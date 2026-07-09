# Instruction — Apply AUDIT_v11 fixes (P1 → P2 → P3) in one pass

**To:** v11 coding agent
**Scope:** implement everything below, in order, in a single work session. File edits only — never run installs, servers, or tests. When done, output the **User Verification Checklist** at the end and stop. Do NOT modify the modules the audit marked as correct (template parser core, importer binding/prefill/coverage, CA writer formulas, output trimming, optimizer) except where explicitly told.

---

## P1 — Rewrite `core/leap_verifier.py` so it is the algebraic inverse of `LeapWriter` (CRITICAL)

The current `verify()` is wrong in three ways: (a) it multiplies by the raw end-use Activity Level cell, so flat end-uses (Activity Level = 100 meaning 100 % = ×1) over-count 100×; (b) for scenario years it reads device `Fuel Share`, which does not exist in Reference (the writer stores the split as device `Activity Level`, useful-energy share) — `_get_val`'s CA fallback silently returns the base-year Fuel Share, so projections are never actually validated; (c) it reads only the immediate parent's Activity Level, ignoring the category chain.

Rewrite the energy reconstruction to mirror the writer exactly:

1. **Interpret Activity Level by its Units metadata** (available in `template.records[...]["units"]`):
   - `Share` / `Percent` → fraction = value / 100.
   - absolute units (`Household`, `Square Meter`, …, i.e. driver-linked end-uses) → absolute value.
2. **Walk the full activity chain** from the sector root down to each end-use: `chain = Π (share fractions of category levels) × (end-use Activity Level, fraction or absolute)`. With the current writer all category levels are 100 % ⇒ chain = end-use activity; implement the general product anyway.
3. **Base year (Current Accounts, scenario_id = 1):**
   `device_final_pj = chain(end-use) × FEI(end-use) × FuelShare(device)/100`.
4. **Projection years (target scenario):**
   `device_useful = chain(end-use, year) × UEI(end-use, year) × ActivityShare(device, year)/100`
   `device_final_pj = device_useful / (Efficiency(device, year)/100)` (0 if efficiency ≤ 0).
   Remove the CA fallback in `_get_val` for these variables — a missing scenario value is a finding ("row not written"), not something to silently backfill. Keep the CA fallback ONLY for values LEAP genuinely inherits (Efficiency may fall back to CA if the year cell is empty).
5. Aggregate `device_final_pj` per ESTO fuel via the node's fuels (existing logic OK) and compare to `active_fuels` targets **for the requested year** (the caller must pass the year's own targets when available; keep the current signature but document this).
6. **Tests (`tests/test_leap_verifier.py`) — the regression gate:**
   - Build a small synthetic project (or reuse the JSON fixture), run `LeapWriter.fill()`, feed the produced bytes straight into `LeapVerifier`, and assert **≈0 % deviation for every fuel** in: (i) flat mode, base year; (ii) driver-linked mode, base year; (iii) a projection year with modified shares/efficiencies. These three tests must fail against the OLD verifier logic.
   - Negative test: a scenario-year device row deliberately blanked → verifier reports it as a finding, not silently passing.

## P2 — Robustness fixes

7. **Fingerprint guard on export.** At bind time (`/leap/import-template`, `/projects/{id}/leap-template`, and the stateless path) persist `bound_fingerprint = template.fingerprint` on the project. In `export_leap_values` (and `verify_roundtrip`), recompute the template fingerprint and refuse with HTTP 400 `"Template fingerprint mismatch: the tree was bound against a different LEAP area export. Re-attach the template."` when it differs. Mirror the field in `schemas.py` (rule: models.py ⇄ schemas.py in the same change set).
8. **Structural-consistency check across milestone years.** In `LeapWriter.__init__`, after building `enriched_trees`, walk all years in parallel and assert identical shape: same `node_id` sequence at every path. On mismatch raise `ValueError` naming the year and path (e.g. `"2060: Demand\\...\\Space Heating has 15 children, base year has 16 (first divergence: 'Kerosene Heater')"`). This protects `_get_node_by_path`'s positional lookup from the copy-based year workflow (years are user-created copies that could drift structurally).
9. **Dictionary filename.** Make `LeapDictionary` try `ESTO_codes_to_LEAP_names.xlsx` (underscores — the shipped name) FIRST, then the legacy spaced name, then the fixtures copy; ship the file in `back-end/data/` under the underscore name. Remove the silent dependency on the fixtures fallback.
10. **Internal precision.** In `attach_calculated_energy`, round `calculated_pj` to **6** decimals instead of 4 (display formatting stays wherever the UI rounds). Keep all share computations normalized against the sibling sum. Add a unit test: an end-use whose devices are ~1e-4 PJ yields scenario activity shares summing to 100 ± 1e-6.

## P3 — Cleanup & test hardening

11. **Remove dead code in `leap_writer.py`:** `activity_dict` / `parent_activity_dict` threading in `_traverse_and_write` is computed but never consumed — delete it (and `_get_activity_driver_value`/`_is_dimensionless` if they become unused).
12. **Label the macro no-op:** `_write_macro_variables` targets `Key\Macroeconomic\…` paths absent from the Buildings template. Keep it but add a module-level comment: "Future hook: only active when the LEAP area exposes Key Assumption branches; today macro indicators travel via driver-linked end-use Activity Level."
13. **Harden existing tests to assert values, not just execution:**
    - `test_leap_writer.py`: assert FEI == calculated_pj (or pj/driver), fuel shares sum to 100 per end-use, CA writes only the base-year column, Reference leaves the base-year column empty, Scale/Units written only on driver-linked first-region CA rows.
    - Add missing casuistic tests: **Services 16.01** (deeper path `Services\<BuildingType>\<EndUse>\<Device>`, no Cooking, Other Equipment binds); **two-region isolation** (fixture `Test_LEAP_v3_tworegions.xlsx`: RegionID 2 cells byte-identical after fill); **wrong-area rejection** (bind with v3, attempt export with v2 bytes → HTTP 400 fingerprint error); **idempotent re-attach** (attaching the same template twice yields identical bindings, no duplicates); **uncovered-fuel blocking** (an active fuel with no bound leaf blocks export).
14. Update `walkthrough.md` with a short "Audit fixes" section listing what changed.

---

## User Verification Checklist (output this, then stop)

1. `pytest -q` → full suite green; state the total test count and the count of new tests.
2. `pytest tests/test_leap_verifier.py -q` → green; confirms writer→verifier round-trip ≈0 % in flat, driver-linked, and projection-year cases.
3. Manual (5 min): compile the current project → download → upload the same file to **Verify LEAP Round-Trip** for the base year → every fuel ~0 % deviation, status Pass. Repeat for 2035 → same.
4. Manual negative: try Compile after attaching the OLD v2 template (`FBO_6`) → clear fingerprint-mismatch error, no file produced.
5. Then hand back to the user: the remaining validation is TEST_PLAYBOOK v2 (Batches 1–2), performed by the user in multinode + LEAP.
