# Stage 9 Completion Handoff — Canonical Fixture and Contract Deltas

**To:** v11 coding agent
**Context:** the definitive LEAP template `Test_LEAP_v3_Buildings.xlsx` (Area `FBO_7_Test_Buildings`) has been validated: 374/374 device leaves, full year columns 2022–2060, PJ units at all end-use rows. It replaces all assumptions made from the v2 fixture. Apply the deltas below, finish Stage 9, output the updated User Verification Checklist, and STOP — do not start Stage 10 until the user reports green light.

## 1. Fixture swap
- Copy `Test_LEAP_v3_Buildings.xlsx` into `back-end/tests/fixtures/`.
- Remove the `@pytest.mark.skipif` guards on device-level writer tests; point them at this file.
- Keep `Test_LEAP_v2.xlsx` as a parser-only fixture (different area `FBO_6_Test_Building`; values must never cross areas).

## 2. Contract deltas the code MUST reflect (verified facts from the v3 file)

1. **Scenarios:** `Current Accounts` (ID 1), `Reference` (ID 2 — renamed, no longer "Reference Scenario"), `Target` (ID 3, new). Parser reads scenario names/IDs from the file — never hardcode. The writer targets ONE user-selected scenario (session setting, default `Reference`); rows of other scenarios are never written.
2. **Regions:** the file contains TWO regions — `United States` (RegionID 1) and `Region 1` (RegionID 2, empty spare). All importer/writer operations must key rows by `RegionID` and operate ONLY on the session's selected region (default = RegionID 1). Rows of any other region are preserved untouched. Add a region selector to the session state (schema + UI dropdown populated from the parsed file).
3. **Device-leaf variable pattern (write matrix, supersedes the original plan wording):**
   - Current Accounts: write `Fuel Share` (% of end-use final energy, ×100) and `Efficiency` (×100). Ignore the device-level `Final Energy Intensity` placeholder rows (LEAP creates them in Gigajoule; never write, never unit-audit them).
   - Scenario years: devices carry NO `Fuel Share` rows. Write `Activity Level` (share %) instead: `act_share_i = (final_pj_i × eff_i) / Σ_j (final_pj_j × eff_j) × 100` normalized within each end-use, plus `Efficiency` per milestone year. Absent fuels: act share 0, efficiency kept at default.
4. **Unit audit scope:** `Petajoule` is enforced ONLY on rows the writer targets (end-use `Final Energy Intensity` / `Useful Energy Intensity`). Confirmed: all end-use rows in v3 are PJ; the 748 GJ device placeholders must not block anything.
5. **Whole-area exports:** the file has ~30,000 rows including Transformation and Resources branches. The branch-path scope filter must discard them efficiently; parsing must stay well under a few seconds. Unknown variables (`Demand Cost`, `Total Final Energy Consumption`, `Total Activity` on leaves, `IPCC GWP Values`, etc.) are ignored via the variable whitelist.

6. **Output trimming (NEW rule — replaces "preserve row order" on the OUTPUT file):** the exported workbook returned to the user contains ONLY the rows the writer actually wrote (header rows 1–3 and each written row's columns A–D preserved verbatim). All unwritten rows — `Target` scenario, non-selected regions, `Load Shape`, result/cost variables, out-of-scope branches — are removed from the output copy. Rationale: LEAP's import processes every remaining contiguous row; stale exported rows (e.g. `Target` rows carrying explicit 0s, or old values in unwritten variables) would otherwise be re-imported and could pin the Target scenario to zero or overwrite LEAP-side edits. LEAP explicitly supports row deletion ("You can safely delete rows... LEAP simply imports any remaining contiguous rows"). The in-memory template keeps all rows (it remains the binding source); trimming happens only when producing the output bytes.

## 3. Tests to add before declaring Stage 9 complete
- Activity-share conversion: for a synthetic end-use with known finals and efficiencies, written scenario `Activity Level` shares sum to 100 (±1e-6) and match hand-computed values.
- Region isolation: filling values for RegionID 1 leaves every RegionID 2 cell byte-identical.
- Scenario dynamism: writer resolves the target scenario by name from the parsed file (test with `Reference`), and refuses an unknown scenario name with a clear error.
- Preservation test re-run against v3 (374 leaves, 3 scenarios, 2 regions, 39 year columns), amended for trimming: every row present in the output was written by the writer; its A–D cells are byte-identical to the input; no `Target` or non-selected-region row survives in the output.
- Trimming safety: output row count == number of written rows; importing-side sanity = header row 3 intact and rows contiguous from row 4.

## 4. Updated Stage 9 User Verification Checklist (output this when done)
- `pytest tests/test_leap_writer.py -q` green, including the previously skipped device-level tests (state expected test count).
- `pytest -q` full suite green.
- Manual: import `Test_LEAP_v3_Buildings.xlsx` in a `20USA`/2022/`16.02 Residential` session → reconciliation shows 138 Residential leaves bound (Services out of scope), region selector shows United States/Region 1 → dry-run export lists only expected cells → downloaded workbook opens in Excel with IDs/columns intact.

## 5. After green light only: Stage 10 notes
- `verify-roundtrip` compares per-fuel final energy for the SELECTED region and scenario only, against session ESTO targets (≤3% acceptance, 1–3% warning band).
- README operator workflow must mention: one LEAP area per economy, region selection, scenario selection (default Reference; `Target` reserved for future policy runs), and the maintenance rule for new ESTO fuels (coverage check will flag; add leaf under Others_Unspecified; re-export).
