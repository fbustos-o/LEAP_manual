# Functional Specification — LEAP ⇄ Multinode Round-Trip Integration

**Version:** 0.9 (draft for review)
**Date:** 2026-07-02
**Applies to:** Multinode Energy Modeler v10 (`back-end/core`, `back-end/api`) and LEAP 2024 areas using the Buildings demand skeleton.
**Companion assets:** `ESTO_codes_to_LEAP_names.xlsx` (fuel & flow dictionary), `Test_LEAP.xlsx` (reference contract workbook, Area `FBO_6_Test_Building`).

---

## 1. Purpose and scope

This specification defines two new capabilities in the Multinode Energy Modeler and the conventions both sides must follow so that demand data can travel **LEAP → Multinode → LEAP** without loss of linkage:

1. **Template Importer** — ingest a LEAP *Export to Excel* workbook (the "contract workbook"), reconstruct the demand tree, and bind every Multinode node to its LEAP row identifiers.
2. **Value Writer** — write balanced results (base year + projected years) back into the *same* workbook, preserving all linkage columns, so LEAP's *Import from Excel* applies them by ID.

A third, semi-manual channel — **Structure Channel** (LEAP's *Create Branches from Excel*) — is specified for creating the device/fuel layer and any structural additions.

Out of scope: LEAP-side automation via the LEAP API; Transformation branches; cost data.

---

## 2. Core principles (non-negotiable)

| # | Principle |
|---|-----------|
| P1 | **LEAP owns the structure.** Multinode never invents branches in the value channel; every branch must exist in LEAP first. |
| P2 | **Match by ID, never by name.** Row identity = (`BranchID`, `VariableID`, `ScenarioID`, `RegionID`), columns A–D of the contract workbook. |
| P3 | **The contract workbook is round-trip property.** Multinode reads it, fills year cells, and re-emits it. Columns A–D, the blank spacer column, and the trailing `#N/A` column are preserved byte-for-byte. |
| P4 | **IDs are area-specific.** A values file may only be imported into the *same LEAP area* whose export produced it. Cloned areas mint different IDs. |
| P5 | **Names cross the boundary only through the dictionary** (`ESTO_codes_to_LEAP_names.xlsx`): ESTO product codes ⇄ LEAP fuel names; ESTO flow codes ⇄ LEAP branch names. |
| P6 | **All persistent artifacts, code identifiers, logs, and file contents are in professional English.** |

---

## 3. The contract workbook (input format, as observed)

Single sheet named `Export`.

**Row layout**
- Row 1: metadata — `Area:` in col E, area name in col F, `Ver:` in col G, version number in col H.
- Row 2: blank.
- Row 3: header row.
- Rows 4…N: data rows, one per (branch, variable, scenario, region).

**Column layout** — *must be discovered by header text on row 3, never by fixed index* (LEAP layouts vary with year range and level count):

| Header | Notes |
|---|---|
| `BranchID`, `VariableID`, `ScenarioID`, `RegionID` | Linkage keys. `BranchID` column is hidden in Excel. Read-only. |
| `Branch Path` | Backslash-delimited, e.g. `Demand\Buildings\Residencial\Urban\Space Heating`. |
| `Variable` | E.g. `Total Activity`, `Activity Level`, `Final Energy Intensity`, `Useful Energy Intensity`, `Load Shape`, and (after the device layer exists) `Fuel Share`, `Efficiency`. |
| `Scenario` | `Current Accounts` (ScenarioID 1) or `Reference Scenario` (ScenarioID 2 in the reference area). Do not hardcode IDs; read them per file. |
| `Region` | Region display name. |
| `Scale`, `Units`, `Per...` | Unit metadata. Writable only for Current Accounts rows of the first region (LEAP ignores unit edits elsewhere). |
| `Method` | Interpolation label consumed by LEAP on import: `Interp`, `Step`, or `Smooth`. |
| Year columns | One column per year, header is the integer year (reference file: 2022…2060). |
| (blank spacer) | Unnamed column after the last year. Preserve. |
| `Level 1` … `Level 8...` | Branch name split per level. Used for parsing convenience only; not authoritative. |
| trailing unnamed column | Contains `#N/A` formulas. Preserve. |

**Variable pattern per branch type (Useful Energy methodology):**

| Branch type | Variables present |
|---|---|
| Category (e.g. `Residencial`, `Urban`, `Rural`) | `Total Activity`, `Activity Level` (Share %) |
| End-use, Category-with-Energy-Intensity, useful-energy enabled (e.g. `Space Heating`) | `Total Activity`, `Activity Level` (absolute driver), `Final Energy Intensity` (CA only), `Useful Energy Intensity`, `Load Shape` |
| Device/fuel technology leaf (exists only after Structure Channel runs) | `Fuel Share`, `Efficiency` (+ activity share variables as configured) |

**Scenario × variable write matrix (the key business rule):**

| Variable | Current Accounts | Reference Scenario |
|---|---|---|
| `Final Energy Intensity` | ✅ base year value (2022) | ❌ not present — do not write |
| `Useful Energy Intensity` | derived by LEAP — leave untouched | ✅ milestone years |
| `Activity Level` / `Total Activity` | ✅ base year | ✅ milestone years |
| `Fuel Share` (device rows) | ✅ base year | ❌ not present — write `Activity Level` (share) instead |
| `Activity Level` share (device rows) | derived by LEAP | ✅ milestone years: act_share_i ∝ final_i × eff_i (normalized per end-use) |
| `Efficiency` (device rows) | ✅ base year | ✅ milestone years |
| `Load Shape` | leave untouched | leave untouched |

---

## 4. Module A — Template Importer

### 4.1 Placement
`back-end/core/leap_importer.py` (new), exposed via `POST /leap/import-template` in `api/routers.py`; multipart upload of one `.xlsx`. Response and state extensions defined in `api/schemas.py`.

### 4.2 Processing pipeline
1. **Validate workbook**: sheet `Export` exists; row 3 contains the mandatory headers (`BranchID`, `VariableID`, `ScenarioID`, `RegionID`, `Branch Path`, `Variable`, `Scenario`, `Method`, ≥1 integer year header). Reject otherwise with a structured error listing missing headers.
2. **Read metadata**: area name (row 1), year span (first/last year headers), scenario list with their IDs, region list with their IDs.
3. **Economy binding check** (see §7-D2): compare the area name against the economy selected in the Multinode session using the convention `<economy>_<anything>` (e.g. `20USA_Buildings`). Mismatch ⇒ warning requiring explicit user confirmation, not a hard failure.
4. **Scope filter**: keep only rows whose `Branch Path` starts with the demand root mapped from the selected sector flow via the dictionary (e.g. `16.02 Residential` → path prefix configured per area, default `Demand\Buildings\Residencial`; `16.01 Commercial and public services` → `Demand\Buildings\Services`). The prefix mapping must be editable in the UI because LEAP branch names may be localized (`Residencial` vs `Residential`).
5. **Rebuild tree**: split `Branch Path`; create/merge Multinode nodes level by level. Classify each branch (category / end-use / device) from its variable pattern (§3).
6. **Bind linkage metadata**: for every node store `leap_binding = { branch_id, rows: [{variable, scenario_id, region_id, row_index, method, scale, units}] }`. Multinode's internal state (telemetry/save files) must persist this binding.
7. **Driver detection**: read the `Units` of each end-use `Activity Level` row and map to Multinode macro-drivers (`Household` → `households`, `Square Meter` → `floor_area`; extensible lookup table). Conflicts with an existing `macro_driver_link` are reported, not silently overwritten.
8. **Unit audit**: every `Final Energy Intensity` / `Useful Energy Intensity` row **that the writer targets** (end-use level) must be `Petajoule`; device-leaf FEI placeholder rows (created by LEAP in GJ) are ignored. Any other unit (e.g. `Gigajoule`) ⇒ blocking finding in the reconciliation report: fix in LEAP and re-export (per project decision, units are corrected on the LEAP side, not converted silently).
9. **Reconciliation report** (returned to the UI):
   - branches in scope with no Multinode counterpart (new to Multinode) — will be adopted;
   - Multinode nodes with no LEAP branch — routed to the Structure Channel backlog (§6);
   - device leaves with fuels not found in the dictionary — blocking;
   - fuels with non-zero ESTO targets for the session economy/flow not covered by any bound leaf — blocking (target-fuel coverage check);
   - unit findings, driver conflicts, scenario list.
10. **Keep the original workbook** (bytes) attached to the session; the Value Writer re-opens *this* file, never regenerates it.

### 4.3 Failure modes
- Missing/duplicated headers, no rows in scope, unknown fuel names, tampered ID columns (non-integer values) ⇒ structured errors, import aborted, nothing persisted.

---

## 5. Module B — Value Writer

### 5.1 Placement
Refactor `back-end/core/leap_exporter.py` from "generate new workbook" to "fill the ingested workbook". Endpoint: `POST /leap/export-values` returning the filled `.xlsx`.

### 5.2 What gets written where

For each bound node and each (variable, scenario) row, per the write matrix in §3:

**Current Accounts (base year column only, e.g. 2022):**
- End-use `Final Energy Intensity`: total final energy of the end-use (sum of its device `calculated_pj`) ÷ end-use activity, in PJ per driver unit. If the activity is dimensionless/1, write total PJ.
- End-use `Activity Level` / `Total Activity`: driver value from `macro_drivers` (households, floor_area).
- Category `Activity Level` (shares): Urban/Rural weights (×100, `%`).
- Device `Fuel Share`: share of the end-use final energy per device (×100).
- Device `Efficiency`: device efficiency (×100; heat pumps may legitimately exceed 100).

**Reference Scenario (milestone year columns):**
- End-use `Useful Energy Intensity`: Σ_devices (device final energy × device efficiency) ÷ end-use activity, per milestone year. This is the conversion final→useful that Multinode must perform; LEAP will re-derive final energy from shares and efficiencies.
- `Activity Level` / `Total Activity`, category shares, device `Fuel Share` and `Efficiency`: milestone-year values.
- `Method` cell: ensure `Interp`.

### 5.3 Year-cell policy
- Write **milestone years only** (base year in CA; 2035, 2050, and the horizon value per §7-D1 in REF).
- **Clear (empty) all other year cells** in rows being written: the reference export contains explicit `0` in every REF year; if left, LEAP would import a series pinned to zero instead of interpolating.
- Never write into year columns of rows the matrix marks "leave untouched".
- Precision: round to 6 significant digits; write numbers, not strings.

### 5.4 Integrity rules
- Cells outside (written rows × year/Method columns) are never modified. Columns A–D, spacer, `#N/A` column, hidden-column state, and row order are preserved.
- Rows may be *skipped* (LEAP tolerates deleted/foreign rows) but Multinode does not delete rows; it simply leaves them unwritten.
- Output filename: `<area>_<economy>_<sector-code>_<scenario>_<timestamp>.xlsx`.
- A dry-run mode returns the list of (row, column, old value, new value) without producing the file — used by the UI for a review screen.

---

## 6. Structure Channel — device layer and structural additions

*Used at first setup (to create the device/fuel leaves under each end-use) and whenever the diff engine finds structure that LEAP lacks.*

1. **Diff detection**: after any import (Module A), Multinode computes `structure_backlog` = nodes/fuels present in the Multinode tree but absent in LEAP bindings.
2. **Generator**: produce one *Create Branches from Excel* table per parent end-use branch, with rows = device names and columns:
   - `Fuel` — LEAP fuel name from the dictionary (mandatory; enables LEAP's automatic fuel association);
   - `Efficiency [%]` — base-year efficiency;
   - `Fuel Share [%]` — base-year fuel share;
   - optional `Tags`.
   Column headers carry units in square brackets (LEAP's unit-recognition convention).
3. **Operator procedure (manual, documented in-app):** in LEAP, right-click the end-use branch → *Create Branches from Excel* → select the named range → map columns → finish. Repeat per end-use listed by the backlog screen.
4. **Re-mint IDs**: after structural changes, the operator re-runs *Export to Excel* and uploads the new workbook (Module A). Only then can Module B write device-level values for scenario years. (Create Branches itself seeds Current Accounts.)
5. **Idempotency**: the backlog screen must show what already exists in LEAP so re-running the procedure never proposes duplicates. Removing a fuel from an economy = write `Fuel Share = 0`; the branch remains.
6. **Fuels master list**: if a dictionary fuel does not exist in LEAP's Fuels database, it must be added once manually in LEAP (`General: Fuels`, Add). The dictionary is the authoritative name source; the importer validates against it (§4.2-9).

---

## 7. Resolved decisions

**D1 — Horizon year 2060.** LEAP's `Interp` applies **zero growth after the last data point** (values are *not* extrapolated). With milestones only at 2035/2050, the 2050–2060 decade would be flat at the 2050 value.
*Decision:* Multinode produces an explicit **2060 value**. Default rule = extend each end-use's 2035→2050 trend (same driver-linked growth) with a per-run toggle `hold constant after 2050`; the user may override 2060 values before export. Rationale: silent flat-lining misstates the final decade; an explicit value keeps the choice visible and auditable.

**D2 — Economy ↔ area/region binding.** Region *names* cannot be changed through the data import (imports match by `RegionID`; names live in LEAP's Regions screen, where renaming is a one-click manual edit). The "generic buildings file" therefore works as follows:
- The generic artifact is a **template LEAP area** (the skeleton), not a spreadsheet: one copy of the area per economy (LEAP *Save As*), named `<economy>_Buildings` (e.g. `20USA_Buildings`).
- Because IDs are area-specific (P4), **each economy's copy exports its own contract workbook**; a workbook from one economy's area must never be imported into another's. The importer enforces this via the area name in row 1 + a fingerprint (hash of the sorted `BranchID` set) stored with the session.
- Renaming `Region 1` to the economy code inside each copy is recommended for traceability but optional; the binding is carried by the area name.

**D3 — Language.** All artifacts (spec, code, UI labels, logs, workbook contents) in professional English.

**D4 — Units.** PJ everywhere for energy variables; deviations are fixed in LEAP (e.g. `Others_Unspecified` currently in GJ) and re-exported. The importer blocks on non-PJ energy rows.

---

## 8. Validation — closing the loop (Phase 7 hook)

After importing values into LEAP, the operator re-exports the workbook and uploads it to `POST /leap/verify-roundtrip`. Multinode compares, per fuel and per milestone year, LEAP's implied final energy against ESTO targets (`active_fuels`) and reports deviations. Acceptance: ≤ 1–3 % per fuel (same tolerance as the SLSQP objective). Deviations above tolerance list the offending branches.

---

## 9. Open items

1. Exact per-driver units for `Useful Energy Intensity` denominators (PJ per million households vs PJ per household) — fix after the first device-layer export shows LEAP's chosen denominator.
2. Whether `Load Shape` will ever be populated from Multinode (currently: never written).
3. Services sector skeleton (`16.01`) — replicate the Residential pattern once validated.
4. Handling of multi-region areas (more than one region per area) — deferred; current design assumes one region per economy area.
