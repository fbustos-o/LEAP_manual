# Implementation Plan — Multinode Energy Modeler v11: LEAP Template Round-Trip

## Context

The Multinode Energy Modeler (v10) reconciles bottom-up buildings demand trees against APEC/ESTO top-down balances and exports Excel files for LEAP. The current export cannot be imported into LEAP because LEAP's *Import from Excel* matches rows by hidden internal IDs (columns A–D) that only LEAP can mint, and it cannot create branches. The agreed solution inverts the flow: **LEAP owns the structure**; multinode ingests LEAP's own *Export to Excel* workbook (the "contract workbook"), runs its normal balancing work on top of that structure, and writes values back into the **same workbook**, preserving IDs, so LEAP re-imports them by ID.

v11 is a copy of v10 extended with: (1) a LEAP template pre-load step, (2) a value writer that fills the same workbook, (3) an interactive per-leaf efficiency catalog, (4) macro-driver scale/unit metadata aligned with LEAP, and (5) configurable milestone years including an interactively requested horizon year (2060).

All artifacts, code, UI text, and logs in **professional English** (project decision).

## Execution model (mandatory)

- The agent **only creates and edits files** (code, tests, config, docs). It must **never** run `pip install`, start servers (`uvicorn`, `http.server`), execute `pytest`, or run any part of the application. All runtime verification is performed **locally by the user**.
- Every stage ends with a **User Verification Checklist**: the exact commands the user runs locally and the expected results. The agent proceeds to the next stage **only after the user reports green light** (or reports failures, which the agent then fixes by editing code).
- The agent commits its file changes at the end of each stage with the stage name in the commit message.

## Locked decisions (do not re-litigate)

| # | Decision |
|---|---|
| D1 | Milestone years configurable; default = base year, 2035, 2050 + horizon year (2060) **asked interactively** in the frontend. LEAP's `Interp` does NOT extrapolate past the last point, hence the explicit horizon value. |
| D2 | Region stays generic (`Region 1`) in the template area; the user renames it manually in LEAP after loading data. Economy binding is by LEAP **Area name** prefix (e.g. `20USA_Buildings`) + BranchID-set fingerprint. |
| D3 | English everywhere in artifacts. |
| D4 | Energy units: **Petajoule** for all energy rows; importer blocks on any other energy unit. |
| D5 | **Device layer = predefined superset** in the generic LEAP area (built once, manually, by the user). Fuels without demand in an economy get `Fuel Share = 0`. No Create-Branches generator in v11. |
| D6 | Efficiency lives on **leaf nodes (device/fuel)**, entered interactively in the frontend from a **seeded catalog of typical devices** + a "User defined" option; persisted in the save file; per milestone year. |
| D7 | Macro-driver units: **Scale dropdown** (None, Thousand, Million, Billion) + **Unit dropdown** seeded with LEAP-recognized unit names (Household, Square Meter, USD, ...) extensible via config + **free-text display label** (e.g. `pp`, `m2`) that is UI-only and never written to LEAP. |
| D8 | Methodology in LEAP: Useful Energy analysis. Write matrix: `Final Energy Intensity` → Current Accounts only (base year); `Useful Energy Intensity` → Reference Scenario milestone years; `Fuel Share`/`Efficiency` → both; `Load Shape` → never written. |

## Reference assets (test fixtures — copy into `v11/back-end/tests/fixtures/`)

- `Test_LEAP_v2.xlsx` — real LEAP export, Area `FBO_6_Test_Building`, sheet `Export`, 133 rows, years 2022–2060, scenarios `Current Accounts` (ID 1) / `Reference Scenario` (ID 2), branches down to end-use level under `Demand\Buildings\Residential`.
- `ESTO_codes_to_LEAP_names.xlsx` — sheet `sector_fuel_ESTO_LEAP_names`, columns `category` (products|sectors), `original_label` (ESTO code+name), `leap_name`, `PRODUCT NOT USED IN LEAP` (bool).
- `20USA_2022_16_02_Residential_2050.json` — v10 save file (tree_state per year, macro_drivers, active_fuels) used as the model-state fixture.
- Functional spec: `99 - Multinode Integration/SPEC_LEAP_roundtrip.md` in the `fbustos-o/LEAP_manual` repo (branch `claude/leap-energy-demand-format-6w5v8h`) — authoritative for the contract details below.

## Contract workbook essentials (already reverse-engineered; encode as constants/tests)

- Sheet `Export`. Row 1 metadata: `Area:` label col E, area name col F, `Ver:` col G. Row 3 = headers. Data from row 4.
- **Discover columns by header text, never fixed index**: `BranchID`, `VariableID`, `ScenarioID`, `RegionID`, `Branch Path`, `Variable`, `Scenario`, `Region`, `Scale`, `Units`, `Per...`, `Method`, integer year columns (2022…2060), blank spacer, `Level 1`…`Level 8...`, trailing `#N/A` column.
- Row identity = (`BranchID`,`VariableID`,`ScenarioID`,`RegionID`). Preserve columns A–D, spacer, `#N/A` column, hidden-column state, row order **byte-for-byte**.
- Variable pattern: categories (Residential/Urban/Rural/Others_Unspecified) carry `Total Activity` + `Activity Level` (% Share); end-uses carry those plus `Final Energy Intensity` (CA only), `Useful Energy Intensity`, `Load Shape`; device leaves (after superset exists) will add `Fuel Share`, `Efficiency`.
- Driver detection from `Units` of end-use `Activity Level`: `Household`→`households`, `Square Meter`→`floor_area` (extensible map).
- Year-cell policy on write: write milestone years only; **clear all other year cells in written rows** (the reference file carries explicit `0` in every Reference Scenario year — leaving them pins the series to zero instead of letting `Interp` interpolate); set `Method = Interp`.

## USER PREREQUISITE (manual, in LEAP — before Stage 9 can be end-to-end tested)

**What `Test_LEAP_v3.xlsx` is:** the next *Export to Excel* of the **same area** (`FBO_6_Test_Building`) taken **after** the user manually creates the superset device/fuel leaves under every end-use. It is produced by LEAP, not authored by hand. v2 ends at end-use branches; v3 additionally contains, for every device leaf, `Fuel Share` and `Efficiency` rows (each with its own `BranchID`) in both scenarios — the rows the Value Writer needs as targets and the Stage 9 tests need as fixture.

**Build procedure (in LEAP, same area — never a new area, or all IDs change):**
1. Select an end-use (green Useful Energy category, e.g. `Urban\Space Heating`) → right-click → Add → **Technology** branch (green). Because the parent is useful-energy enabled, LEAP exposes `Efficiency` and `Fuel Share` on the leaf automatically.
2. In the leaf's Properties select its **Fuel** (typing the first letters autocompletes; LEAP offers the fuel name as branch name). Leave data values empty/default — multinode fills them later.
3. Two siblings may share the same fuel (`Electricity` and `Electricity HP` both consume Electricity; they differ by the efficiency multinode writes).
4. Do not rename or move existing branches.
5. Repeat per the superset table below (53 leaves total: 22 × Urban + 22 × Rural + 9 under Others_Unspecified).
6. Export with the **same options as v2**: from `Demand\Buildings`, all scenarios, all variables, multi-year columns, 8 levels, autofilter → save as `Test_LEAP_v3.xlsx`.

Superset table (branch name → LEAP fuel from the dictionary):

| End-use (create under Urban AND Rural) | Leaves (fuel) |
|---|---|
| Space Heating (7) | Electricity→Electricity, Electricity HP→Electricity, Natural Gas→Natural gas, LPG→LPG, Kerosene→Kerosene, Other Biomass→Other biomass, Gas and Diesel Oil→Gas and diesel oil |
| Space Cooling (1) | Electricity HP→Electricity |
| Water Heating (6) | Electricity, Natural Gas, LPG, Kerosene, Gas and Diesel Oil, Solar→Solar nonspecified |
| Cooking (3) | Electricity, Natural Gas, LPG |
| Lighting (1) | Electricity |
| Appliances (4) | Electricity, Natural Gas, LPG, Kerosene |
| Others_Unspecified (9, once) | Gas and Diesel Oil, Natural Gas, Geothermal, Solar→Solar nonspecified, Other Biomass, Biodiesel, Electricity, Kerosene, LPG |

**Quick check on the exported v3:** ~53 new level-6 branch paths; each has `Fuel Share` + `Efficiency` rows in both scenarios; all v2 rows still present. **The user sends v3 for review before handing it to the agent** — it closes spec open item §9-1 (real device-row variable pattern, e.g. the exact Useful Energy Intensity denominator); the plan/spec are corrected if LEAP's actual output differs from the predicted pattern.

Stages 0–8 proceed against v2; Stage 9 tests are written against v3 and marked skipped until the file is provided.

---

## Step-by-step implementation stages (each ends with runnable tests)

### Stage 0 — Bootstrap v11
1. Copy `v10/` → `v11/` verbatim (back-end, front-end, requirements.txt, data/).
2. Create `v11/AGENTS.md` (full content in "Deliverable 0" below) and `v11/PLAN_v11.md` (a copy of this plan). Update titles/version strings to v11; add `pytest` and `httpx` (FastAPI test client) to `requirements.txt`. File edits only — no installs, no execution.
3. **User Verification Checklist (green light for Stage 0):**
   - `cd v11/back-end && pip install -r ../requirements.txt` completes without errors.
   - `python seed_users.py` then `uvicorn main:app --port 8000` boots cleanly.
   - Serve `v11/front-end`, log in, and run one full v10 flow (initialize → check balance → optimize): behaves identically to v10.
   - `pytest -q` runs (empty suite / no collection errors is OK).

### Stage 1 — Test harness and fixtures
1. Create `back-end/tests/` with `conftest.py` (FastAPI TestClient + auth fixture using seeded test user) and `fixtures/` containing the three reference files.
2. Write characterization tests for existing v10 endpoints (initialize/validate/optimize happy paths) so later stages can't silently break v10 behavior.
3. **User Verification Checklist:** `pytest -q` → characterization suite green (agent states the expected number of tests).

### Stage 2 — Dictionary service
1. New `core/leap_dictionary.py`: loads `ESTO_codes_to_LEAP_names.xlsx` (path configurable; ship the fixture copy in `data/`), exposes `esto_to_leap(fuel_or_flow_label)`, `leap_to_esto(name)`, `is_used_in_leap(label)`, and flow-code → demand-root-path mapping (default: `16.02 Residential` → `Demand\Buildings\Residential`, `16.01 Commercial and public services` → `Demand\Buildings\Services`; overridable per session because LEAP branch names may differ).
2. **User Verification Checklist:** `pytest tests/test_dictionary.py -q` green — all 9 residential JSON fuels resolve; flagged `PRODUCT NOT USED IN LEAP` entries resolve but warn; unknown label raises a typed error.

### Stage 3 — Template parser (`core/leap_template.py`)
1. Implement `LeapTemplate.load(bytes)`:
   - validate sheet `Export`, metadata row, mandatory headers; build column map by header text;
   - parse rows into records keyed by (`BranchID`,`VariableID`,`ScenarioID`,`RegionID`), retaining row index, method, scale, units, per, year values;
   - expose `area_name`, `years`, `scenarios` (name→ID), `regions`, `branch_paths`, and `fingerprint` = SHA-256 of sorted BranchID set;
   - classify each branch (category / end-use / device) from its variable pattern;
   - detect drivers from Activity Level units;
   - unit audit: any energy-intensity row not in `Petajoule` → blocking finding.
2. Keep the raw workbook bytes inside the object (single source for the writer).
3. **User Verification Checklist:** `pytest tests/test_leap_template.py -q` green against `Test_LEAP_v2.xlsx` — 16 branch paths found; scenario IDs {1,2}; years 2022–2060; end-use classification correct for all 12 Urban/Rural end-uses; `Others_Unspecified` passes the PJ audit; a deliberately corrupted header fails with a clear error.

### Stage 4 — Import endpoint + tree binding
1. `POST /leap/import-template` (multipart) in `api/routers.py` + schemas: stores template bytes + parse result in session state (SQLite, keyed to user/session like v10 save files).
2. Build/merge the multinode tree from template branch paths (scope-filtered by the session's economy/sector via the dictionary root path). Each node gets `leap_binding = {branch_id, rows:[{variable, scenario_id, region_id, row_index}]}` persisted in the save-file format (backward compatible: old saves without bindings still load).
3. Economy check: area name must start with the session economy code (e.g. `20USA`) else return a warning flag the UI must surface (non-blocking, per D2).
4. Return a **reconciliation report**: branches adopted, multinode-only nodes (no LEAP row — will not be exportable), device leaves missing (expected until superset exists), unit findings, driver conflicts.
5. **User Verification Checklist:** `pytest tests/test_import_endpoint.py -q` green — upload v2 fixture in a `20USA`/`16.02 Residential` session; 12 end-uses bound, report lists zero device bindings, warning on area name (`FBO_6_Test_Building` doesn't start with `20USA`).

### Stage 5 — Frontend pre-load flow
1. Add "Load LEAP Template" to the initialization screen (after economy/year/sector selection): file upload → shows reconciliation report → on confirm, the tree canvas is rebuilt from the template structure (bound nodes visually badged, e.g. a small link icon).
2. Nodes created from the template are **structure-locked** (rename/delete disabled; weights/fuels/values editable). Multinode-only additions remain allowed but are flagged "not exportable to LEAP".
3. **User Verification Checklist:** follow `tests/MANUAL_UI.md` (written by the agent): upload v2, see 2 groups × 6 end-uses + Others_Unspecified, badges present, locked rename verified.

### Stage 6 — Efficiency catalog (interactive, per leaf)
1. `data/device_efficiency_catalog.json`: seeded entries `{device_label, fuel_leap_name, efficiency_pct}` — e.g. Heat pump/Electricity/300, Electric resistance/Electricity/100, Gas boiler/Natural gas/90, LPG heater/LPG/85, Kerosene heater/Kerosene/80, Biomass stove/Other biomass/65, Solar water heater/Solar nonspecified/100 — plus `User defined`.
2. Data model: each leaf fuel entry gains `efficiency` (fraction, default 1.0) **per milestone year** (dict year→value; base-year value used where a year is missing). Persist in save files (backward compatible default 1.0).
3. Frontend: when attaching/editing a fuel on a leaf, show catalog dropdown → picks efficiency; "User defined" enables a numeric box. Editable per milestone year in the projection view.
4. **User Verification Checklist:** `pytest tests/test_efficiency.py -q` green (schema round-trip save/load with efficiencies); UI manual check per `tests/MANUAL_UI.md` addendum.

### Stage 7 — Macro-driver scale/unit metadata (per D7)
1. Extend macro-driver model: `scale` (enum None/Thousand/Million/Billion), `leap_unit` (from `data/leap_units.json`, seeded with Household, Square Meter, USD, Person, Tonne…; user-extensible file), `display_label` (free text, UI-only).
2. Frontend: two dropdowns + one text box in the driver editor panel; driver chips show `value scale unit (label)`.
3. Writer linkage (used in Stage 9): when writing `Activity Level`/`Total Activity` rows for Current Accounts of the first region, set `Scale`/`Units` cells from these fields; **never** write `display_label`. (LEAP only honors unit edits on first-region Current Accounts rows.)
4. **User Verification Checklist:** `pytest tests/test_macro_drivers.py -q` green (schema tests; the Scale/Units write behavior is asserted again in Stage 9); UI manual check of the two dropdowns + label box.

### Stage 8 — Milestone years (per D1)
1. Session setting `milestone_years`: default `[base, 2035, 2050]`; on template import, horizon year = last year column (2060) is proposed and the UI **requires** the user to either enter horizon values interactively (per end-use/driver, with default = extend 2035→2050 trend, toggle "hold constant") or accept the trend default.
2. Balance/optimization loop (existing v10 engine) runs per milestone year — reuse the multi-year telemetry mechanism v10 already has; add the horizon year as one more entry.
3. **User Verification Checklist:** `pytest tests/test_milestone_years.py -q` green — projection state contains all four years; trend-default math verified (linear continuation of 2035→2050 per branch); UI prompts for the horizon year on template import.

### Stage 9 — Value writer (`core/leap_writer.py`, refactor of `leap_exporter.py`)
1. `LeapWriter(template, model_state).fill()` → workbook bytes. Open the **stored original bytes** with openpyxl (keep_vba False, preserve everything else); touch only year cells + `Method` + (per Stage 7) Scale/Units of CA first-region activity rows.
2. Write rules (formulas):
   - CA end-use `Final Energy Intensity` (base year): Σ leaf `calculated_pj` ÷ end-use activity (in driver units); if activity dimensionless → total PJ.
   - CA/REF `Activity Level`: absolute driver values at end-uses; shares ×100 at category levels (Urban/Rural/Others weights).
   - REF end-use `Useful Energy Intensity` (each milestone year incl. horizon): Σ_leaves (final_pj × efficiency) ÷ activity.
   - Device rows (only if bound, i.e. v3 template): `Fuel Share` = leaf share of end-use final energy ×100; `Efficiency` = efficiency ×100; absent-fuel leaves get explicit 0 share.
   - Clear non-milestone year cells in every written row; `Method = Interp`; round to 6 significant digits; write numbers not strings.
3. `POST /leap/export-values` returns the file, named `<area>_<economy>_<sector>_<timestamp>.xlsx`; `?dry_run=true` returns the change list (row, column, old, new) for a UI review screen. Refuse to export if the session fingerprint ≠ template fingerprint (P4: same-area guarantee).
4. Frontend: "Export to LEAP (filled template)" button + dry-run review modal.
5. **User Verification Checklist:**
   - `pytest tests/test_leap_writer.py -q` green:
     - Preservation test: fill v2 fixture with synthetic state → re-open output; columns A–D, spacer, `#N/A` col, row count/order identical to input; only expected cells differ (cell-by-cell walk of both workbooks).
     - Rules test: UEI = Σ(final×eff)/activity against hand-computed values from the JSON fixture; REF zeros cleared; CA untouched outside base year.
     - Device-level tests target `Test_LEAP_v3.xlsx` and are `@pytest.mark.skipif` until the user provides that file.
   - Manual: run a dry-run from the UI and confirm the change list matches expectations; download the filled workbook and open it in Excel.

### Stage 10 — Round-trip verification + docs
1. `POST /leap/verify-roundtrip`: upload a re-export from LEAP after import; compare implied per-fuel final energy vs session ESTO targets (`active_fuels`); report per-fuel deviation; acceptance ≤ 3% (warning band 1–3%).
2. Update v11 README: full operator workflow (template area → Save As per economy → export → multinode → import filled file with *Import as data*, "Values only replace Interp/Step" ON, backup first → rename region → verify).
3. **User Verification Checklist:** full `pytest` suite green; end-to-end manual run per the README workflow with the v2/v3 fixtures; final LEAP-side import check (user, in LEAP).

## Execution notes for the agent

- Work stage by stage **in order**; do not start a stage until the user reports the previous checklist green. If the user reports failures, fix by editing code and hand back an updated checklist.
- File edits only — never run installs, servers, tests, or the app (see Execution model above).
- Commit at every stage with the stage name.
- Never modify v10; all work in `v11/`.
- openpyxl is already a v10 dependency (leap_exporter uses it) — reuse it; do not add pandas-based Excel writing for the round-trip file (it re-serializes and loses layout).
- The v10 modules to study before coding: `core/tree_components.py` (tree model to extend with `leap_binding` + `efficiency`), `core/leap_exporter.py` (to be superseded by `leap_writer.py`), `api/routers.py`/`api/schemas.py` (endpoint patterns), `app.js` (tree rendering + state management for UI stages).
- Keep old save-file compatibility everywhere (v10 telemetry loader precedent exists).

## Verification (end-to-end, all performed by the user locally)

1. `pytest` suite: parser, dictionary, binding, writer preservation/rules, endpoints.
2. Manual: boot v11 → session `20USA`/2022/`16.02 Residential` → upload `Test_LEAP_v2.xlsx` → confirm reconciliation → set efficiencies from catalog → balance + optimize base/2035/2050 → enter 2060 interactively → dry-run review → export filled workbook → verify in Excel that only expected cells changed.
3. In LEAP: import the filled workbook into the test area (as data, backup first), check LEAP results per fuel vs ESTO targets, re-export and run `/leap/verify-roundtrip` (≤3%).

## Out of scope for v11

Create-Branches table generator (superseded by superset decision); LEAP API automation; Services sector tree content (mechanism is sector-agnostic, only the root-path mapping differs); multi-region areas; Load Shape data.

---

## Deliverable 0: `v11/AGENTS.md`

`AGENTS.md` ships as a separate file at the v11 repository root (created in Stage 0, step 2). It merges the project base context (A.P.E.X. compliance) with the execution rules of this plan and governs every stage. This plan is copied into the repository as `PLAN_v11.md` so `AGENTS.md` can reference it.
