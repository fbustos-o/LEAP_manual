# Code Audit — Multinode v11 (LEAP round-trip)

Scope reviewed: `core/leap_writer.py`, `leap_template.py`, `leap_importer.py`, `leap_verifier.py`, `optimization_engine.py`, `leap_dictionary.py`, `api/routers.py`. Overall the contract is well implemented: template parsing (header-based, fingerprint, classification, PJ audit), path binding, efficiency prefill, coverage check, output trimming, and the CA writer all look correct and match the agreed spec. The items below are ordered by severity. **The writer (what LEAP consumes) is in good shape; the main correctness problem is in the verifier (the QA gate).**

## P1 — Correctness: the LEAP Verifier is wrong (fix before trusting `verify-roundtrip`)

`leap_verifier.py` reconstructs implied energy differently from how the writer wrote it, so its ≤3 % pass/fail is unreliable. Three concrete defects:

1. **Share-based Activity Level is over-counted 100×.** `verify()` does `device_pj = activity * intensity * (share/100)` with `activity` read verbatim from the end-use Activity Level cell. In flat mode that cell = **100** (meaning 100 % = ×1 in LEAP), so the result is 100× too large; every flat end-use reports "Fail". It happens to be correct only for driver-linked end-uses (absolute activity × per-unit intensity cancel). Fix: interpret Activity Level by its **Units** — if `Share`/`Percent`, multiply by value/100 (a fraction), not the raw value; if absolute (Household/Square Meter/…), use as-is. Better: walk the full activity chain from the sector root exactly like LEAP (product of category share-fractions × the absolute driver where present), instead of reading only the immediate parent's Activity Level (line ~75).

2. **Wrong variable for the scenario device split.** For non-CA years the verifier reads **Fuel Share** (`_get_val(node_branch_id, "Fuel Share", scenario_id, year)`), but the Reference scenario has **no Fuel Share** rows — the writer stores the projected split as device **Activity Level** (useful-energy share). `_get_val` then silently falls back to the CA Fuel Share, so projected splits are never actually validated. Fix: in scenario years read the device **Activity Level** share and treat `intensity` as **Useful Energy Intensity**: `device_useful = activity_enduse_driver × UEI × (device_activity_share/100)`, then `device_final = device_useful / (eff/100)`. This must mirror the writer's formulas in `leap_writer.py` lines ~322–342 and ~358–382.

3. **Only the immediate parent is read, not the chain.** `activity = _get_val(parent_branch_id, "Activity Level", …)` ignores category-level Activity Levels above the end-use. Harmless while all categories are 100 %, but breaks if category shares ever differ. Fold this into the chain-walk from fix #1.

**Action:** rewrite `verify()` so its math is the algebraic inverse of `LeapWriter`, and add a test that a workbook produced by `LeapWriter` verifies at 0 % deviation for **both** a flat and a driver-linked project, across base year and a projection year. Until fixed, treat **LEAP's own Results view as ground truth**, not this endpoint.

## P2 — Robustness & contract gaps

4. **No fingerprint guard on export.** `export_leap_values` writes into `db_project.leap_template_bytes` without checking that the tree's bindings were made against that same template (P4 in the spec). Re-attaching rebinds, so the common path is safe, but add an explicit guard: store the fingerprint at bind time and, on export, if `template.fingerprint != project.bound_fingerprint`, refuse with a clear 400. Cheap insurance against writing A's row indices into B's area.

5. **Per-year structural drift not guarded.** `LeapWriter._traverse_and_write` walks the **base-year** tree and fetches projection-year nodes by positional path (`_get_node_by_path(enriched_trees[y], path_indices)`). If any projection-year tree has a different shape (a branch added/removed in one year only), this misaligns silently or `IndexError`s. Add a structural-consistency check across `milestone_years` at writer init (same node_id at each path) and fail with a clear message if they diverge.

6. **Dictionary default filename mismatch.** `LeapDictionary` defaults to `"ESTO codes to LEAP names.xlsx"` (spaces) then falls back to `ESTO_codes_to_LEAP_names.xlsx` and to the fixtures copy. The shipped `data/` file should match the primary name, or make the loader glob both spellings first; today it silently relies on the fallback, which will break if the fixture is absent in prod.

7. **Rounding at 4 dp propagates to shares.** `attach_calculated_energy` rounds `calculated_pj` to 4 decimals. Fuel Share is safely renormalized against the sibling sum, but device **useful-energy shares** and **UEI** in scenarios are computed from the rounded pj, so near-zero end-uses (e.g. Lighting ≈ 1e-4) can carry visible share error. Raise the internal precision to ~6 dp (round only for display), and keep the sibling-sum normalization everywhere.

## P3 — Dead code / clarity / tests

8. **Dead `activity_dict` in the writer.** `_traverse_and_write` computes `activity_dict` per year and threads it through recursion, but no write path consumes it (writes use driver value / 100 / shares). Remove it or wire it in; as-is it's confusing and invites future bugs.

9. **`_write_macro_variables` targets `Key\Macroeconomic\…` paths that don't exist** in the Buildings-scoped template, so it's currently a no-op. That's fine (macro indicators correctly ride in the end-use Activity Level per Phase D), but label it explicitly as the future Key-Assumption hook so no one assumes drivers are exported there today.

10. **Strengthen test assertions, not just execution.** Ensure `test_leap_writer.py` asserts the *values* (FEI = calculated_pj; fuel shares sum to 100; CA in the base-year column only; Reference leaves 2022 empty) and that `test_leap_verifier.py` will fail if P1 regresses (round-trip of a writer-produced file = 0 % deviation). Add the untested casuistics: Services 16.01 (deeper path, no Cooking, Other Equipment), two-region isolation, wrong-area fingerprint rejection, idempotent re-attach, uncovered-fuel blocking.

## What is correct (no action)
- Template parser: header-driven column map, mandatory-header check, fingerprint, branch classification, PJ audit scoped to end-uses only. ✔
- Importer: path binding with sector-root prefix, device→fuel via dictionary, efficiency auto-prefill with fallback, target-fuel coverage check, unbound reporting. ✔
- CA writer: FEI = calculated_pj (or /driver), Fuel Share normalized against siblings, Efficiency ×100, Activity 100 % flat or driver value with Scale/Units on first-region CA only, non-milestone cells cleared, Method=Interp. ✔
- Output trimming (grouped reverse row deletion) and dry-run change list. ✔
- Optimizer: normalized routing, robust bounds parsing, strict post-normalization, pinned-fuel diagnostics. ✔
