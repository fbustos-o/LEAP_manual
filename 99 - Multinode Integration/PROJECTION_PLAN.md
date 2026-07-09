# Implementation Plan — Driver Linking + Multi-Year Scenario Export to LEAP

**Goal:** (1) finish Current Accounts by driving Activity Level from the macro drivers; (2) let multinode hold an arbitrary set of projection years (base + 2023 + a new 2035 + 2060) and export them to LEAP's **Reference** scenario as interpolated trajectories; (3) carry the macro-economic indicators (households, floor_area, gdp) into LEAP as projectable activity.

Work in phases A→E, each with a User Verification Checklist. File edits only; the user runs everything locally and gives the green light before the next phase.

---

## 0. Concepts to get right first (these resolve the user's questions)

**C1 — Multi-column IS the Interp.** The LEAP template is multi-column (one column per year 2022–2060). We do NOT write a literal `Interp(...)` string. We write the milestone values into their year columns and set `Method = Interp`; LEAP then builds exactly `Interp(2022, v, 2023, v, 2035, v, 2060, v)` internally. Same result the user wants, correct mechanism for this template. (Non-milestone year cells stay empty so LEAP interpolates.)

**C2 — Multinode "projection years" → columns of ONE LEAP scenario (Reference).** `base_year` → Current Accounts (2022 column). `2023 / 2035 / 2060` → Reference scenario, columns 2023 / 2035 / 2060. They are time-points of one projection, not separate LEAP scenarios. `Target` (ID 3) stays reserved for a future alternative policy run.

**C3 — The device split variable differs by scenario (verified from the v3 template):**
- Current Accounts: device **Fuel Share** (final-energy share) + Efficiency.
- Reference: devices have **no Fuel Share**; the split is **Activity Level** (useful-energy share) + Efficiency.
So "Electric Heater's evolving share" = Fuel Share(2022 in Current Accounts) + Activity Level(2023, 2035, 2060 in Reference). LEAP stitches these into one time series; the 2022 anchor is implicit from Current Accounts, so REF only needs the projection years.

**C4 — Macro indicators travel as the end-use Activity Level trajectory.** When an end-use is driver-linked, its Activity Level = the absolute driver value per year (households / floor_area / gdp). Projecting the indicator = writing its yearly values into that end-use's Activity Level columns. No separate structure is required in the current template (see Phase D for the optional Key-Assumption refinement).

## Authoritative write matrix (per region, all values in milestone-year columns; Method=Interp; non-milestone cells cleared)

| Branch level | Variable | Current Accounts (2022) | Reference (2023/2035/2060) |
|---|---|---|---|
| Category (Residential/Urban/Rural/Services/…/Others) | Activity Level | 100 (% Share) | 100 (% Share) |
| End-use, driver-linked | Activity Level | driver.value[2022] (Scale+Units from driver) | driver.value[Y] per year |
| End-use, flat (no driver) | Activity Level | 100 (% Share) | 100 (% Share) |
| End-use | Final Energy Intensity | pj(eu)/driver (or pj(eu) if flat) | — (not written) |
| End-use | Useful Energy Intensity | — (LEAP derives) | Σ_dev(pj·eff)[Y] / driver[Y] (or Σ(pj·eff) if flat) |
| Device | Fuel Share | pj_dev/Σsib_pj ×100 | — (not written) |
| Device | Activity Level (share) | — | (pj_dev·eff)/Σsib(pj·eff) ×100 |
| Device | Efficiency | eff[2022] ×100 | eff[Y] ×100 |

Renormalize shares against the sibling sum (never against an independently-rounded parent). Skip a scenario year for a branch only if it has no data for that year.

---

## Phase A — Driver linking (completes Current Accounts)

1. **Data model** (`tree_components.py`, mirror in `schemas.py`): each end-use node gets `macro_driver_link` (string key into `macro_drivers`, or `null`). Backward compatible: missing/null → flat mode.
2. **UI** (`app.js`): on each end-use (category-with-intensity node) a dropdown to pick its driver from the project's macro-driver list (households / floor_area / gdp / custom) or "None (flat 100%)". Persist via the existing project update endpoint. This is the piece that is currently missing (all links are null).
3. **Writer** (`leap_writer.py`) — Current Accounts, per end-use:
   - link present → Activity Level = driver.value (write Scale + Units from the driver's `{scale, leap_unit}` on the first-region CA row only); Final Energy Intensity = pj(eu)/driver.value.
   - link null → Activity Level = 100 % Share; FEI = pj(eu) (today's behavior).
   - Category levels stay 100 % Share in both modes.
4. **Guard:** driver.value = 0 or missing → fall back to flat for that end-use and flag it in the compile report (avoid divide-by-zero).

**User Verification Checklist A:** link Space Heating/Cooling→floor_area and Water Heating/Cooking/Lighting/Appliances→households; compile Current Accounts; confirm in the review that Urban Space Heating shows Activity Level = 22716.89 (Million, Square Meter) and FEI ≈ 0.17538 PJ/M m², and that device Fuel Shares still sum to 100 %. Import into LEAP → Space Heating energy unchanged (≈3984 PJ). `pytest tests/test_leap_writer.py -q` green including a driver-mode test.

## Phase B — Milestone-year management (add 2035, arbitrary years)

1. `milestone_years` on the project = sorted list, default `[base_year, 2023, 2060]`; the frontend can **add/remove** a projection year (user adds 2035). Adding a year clones the current tree structure into `tree_state[year]` for editing/balancing; removing deletes that slice.
2. Every projection year must be an actual **column in the LEAP template** (2022–2060 all exist → any integer in range is fine). Validate on compile: a milestone year absent from the template's year columns is a blocking error.
3. The balance/optimization loop runs per milestone year (reuse the existing multi-year telemetry). Each `tree_state[year]` carries its own weights, `calculated_pj`, and per-year `efficiency[year]`.

**User Verification Checklist B:** add 2035 in the UI; the project now has years [2022, 2023, 2035, 2060]; balancing produces `calculated_pj` for each; `tree_state` keys reflect all four; removing 2035 cleanly reverts.

## Phase C — Reference-scenario multi-year writer

Extend `leap_writer.py` to write the Reference scenario (user-selected; default `Reference`) across all projection years, per the write matrix:

1. For each projection year Y and each in-scope end-use: write **Useful Energy Intensity**[Y] = Σ_devices(pj[Y]·eff[Y]) / (driver[Y] if linked else 1), into column Y.
2. For each device and year Y: write **Activity Level** share[Y] = (pj[Y]·eff[Y]) / Σ_sib(pj[Y]·eff[Y]) ×100, and **Efficiency**[Y] ×100.
3. Driver-linked end-uses: write **Activity Level**[Y] = driver.value[Y] (absolute) into column Y.
4. Category levels: Activity Level = 100 % across years.
5. **Do NOT** write the 2022 column in Reference (LEAP anchors the base year from Current Accounts); write only the projection years, set `Method = Interp`, leave the intermediate years empty so LEAP interpolates. Output trimming still applies (only written rows leave the workbook).

**User Verification Checklist C:** with 2023/2035/2060 balanced, compile Reference; the review shows, e.g., Urban\Space Heating\Electric Heater Activity Level = {2023:x, 2035:y, 2060:z} and Efficiency per year; UEI present at each end-use per year; no Fuel Share rows in Reference; 2022 columns untouched in Reference. Import into LEAP → the device's Activity Level tab shows the interpolated trajectory (2022 from CA, then the points) and Results reproduce the projected energy within tolerance.

## Phase D — Macro-economic indicators across years (import & export)

1. **Per-year driver values.** Extend the macro-driver model so each driver holds a value per milestone year (e.g. `households: {2022:132, 2035:145, 2060:160}`), reusing the D7 scale/unit/label metadata. UI: the driver editor gains a small per-year value grid (only the milestone years). Today only base_year is populated; 2023/2060 have gdp only — the UI must let the user fill households/floor_area for every projection year.
2. **Export (already covered by Phases A/C):** the driver trajectory lands in the driver-linked end-uses' Activity Level columns (2022 in Current Accounts, 2023/2035/2060 in Reference). That is exactly how the macro indicator reaches LEAP and becomes projectable there.
3. **Optional refinement (recommend later, not now):** model each driver once as a LEAP **Key Assumption** branch (`Key\Demand\Households`, …) and have end-use Activity Level reference it. This removes the per-end-use duplication of the driver value. It requires adding Key-Assumption branches to the generic LEAP area and re-exporting the template so they carry IDs; defer until the per-end-use approach is validated.
4. **Import side:** when a project is created from a LEAP template that already contains driver values in Activity Level rows, the importer should read them back into the macro-driver per-year grid so the round-trip is symmetric (best-effort; flag if units differ).

**User Verification Checklist D:** set households 2035=145, 2060=160; compile; the household-linked end-uses show Activity Level = {2022:132, 2023:…, 2035:145, 2060:160}; floor_area similarly; import to LEAP and confirm the Activity Level trajectory and that demand grows with the driver.

## Phase E — Compile Review & Verify for multi-year

1. Compile Review modal: add a **Year** filter and a Scenario filter (Current Accounts / Reference); show one column per milestone year for the selected variable so the user can eyeball the trajectory before download. Keep the collapsible/scrollable behavior already built.
2. Sanity badges extended: per end-use per year, device shares sum to 100 %; driver-linked end-uses show a monotonic/άny driver trajectory hint if a year is missing.
3. `verify-roundtrip`: compare per-fuel final energy for **each milestone year** (not only base year) against the model's ESTO targets for that year; report per-year, per-fuel deviation (≤3 %).

**User Verification Checklist E:** review modal lets you switch year/scenario and shows trajectories; verify-roundtrip reports all milestone years within tolerance.

---

## Worked example (Urban → Space Heating → Electric Heater)

Base year (real): end-use pj = 3984.13, Electric Heater pj = 1191.11, eff = 1.0 → **Fuel Share(CA 2022) = 29.90 %**, Efficiency = 100.
Illustrative projection (once balanced): say pj/eff give useful-energy shares of 33 % (2023), 45 % (2035), 55 % (2060) as electrification rises.
What lands in LEAP for that device:
- Current Accounts: Fuel Share 2022 = 29.90 ; Efficiency 2022 = 100.
- Reference: Activity Level = {2023: 33, 2035: 45, 2060: 55} ; Efficiency = {2023:…, 2035:…, 2060:300 if it becomes a heat pump}. Method = Interp.
LEAP reads column values and interpolates → the device's activity-share time series = Interp(2022, 29.9, 2023, 33, 2035, 45, 2060, 55), exactly the shape the user described (just via columns, not a typed formula). End-use energy over time comes from UEI[Y] × driver[Y]; per-fuel energy from the shares × efficiencies.
