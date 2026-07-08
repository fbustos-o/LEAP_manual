# Writer Value Rules & Bug Fixes — from first real export review

Reviewed the first generated export `FBO_7_Test_Buildings_20USA_16.02_Residential_...xlsx` (Current Accounts only) against the model JSON. The structure and row-matching are correct (BranchIDs resolve, output is trimmed to written rows, scenario = Current Accounts). But the **values are wrong/empty**, so LEAP would compute zero demand. Fix the four defects below and implement the value formulas exactly.

## Model → LEAP value mapping (authoritative)

Facts about the model JSON (`tree_state[year]`):
- Every node has `calculated_pj` = final energy (PJ). By construction `calculated_pj(child) = weight(child) × calculated_pj(parent)`, and a parent's `calculated_pj` equals the sum of its children's.
- Each device leaf carries one fuel with `efficiency[year]` (fraction; heat pump = 3.0, gas = 0.9, etc.) and `calculated_pj`.

LEAP demand math (Useful Energy, Final-Energy-Intensity-in-Current-Accounts method):
`energy(device) = ActivityChain(end-use) × FinalEnergyIntensity(end-use) × FuelShare(device)`.

**Chosen mapping — "energy in intensity" (exact, robust, no division chains):**

| LEAP row | Level | Value to write (Current Accounts, base-year column) |
|---|---|---|
| `Final Energy Intensity` | end-use | `calculated_pj(end-use)` in **PJ** (units already Petajoule). **← currently NOT written; this is why LEAP shows 0.** |
| `Fuel Share` | device | `calculated_pj(device) / calculated_pj(end-use) × 100` (% Share). Absent/zero-energy device → 0. |
| `Efficiency` | device | `efficiency(base_year) × 100` (% ; heat pump 300, gas 90…). |
| `Activity Level` | end-use | `100` (% Share) — saturation = 1. |
| `Activity Level` | category (Urban/Rural/Others) | `100` (% Share). |

With all Activity Levels = 100 % (chain = 1), `energy(device) = 1 × calculated_pj(end-use) × [calculated_pj(device)/calculated_pj(end-use)] = calculated_pj(device)` — exact at the device level, and category totals fall out as the sum of their end-uses. This reproduction does **not** depend on sibling weights summing to 1, so it is safe even for un-optimized trees.

Worked check (Urban\Space Heating, calculated_pj = 0.2865): FEI = 0.2865; Diesel Heater share = 0.0654/0.2865×100 = 22.83 %, eff = 85; LEAP energy = 1 × 0.2865 × 0.2283 = 0.0654 PJ ✓. Fuel shares sum to 100 %.

Why NOT put the weights into Activity Level: the model's weights are *energy* shares, not activity shares (`calculated_pj = weight × parent`). Mapping the whole weight chain into Activity Level forces a degenerate uniform intensity. The weight's correct LEAP home is **Fuel Share** at the device level (`weight_device ≡ calculated_pj_device/calculated_pj_enduse`); the absolute energy lives in the end-use **Final Energy Intensity**.

## Defects to fix (observed in the first export)

1. **BUG — off-by-one year column (CRITICAL).** All values were written to the **2023** column; Current Accounts base-year data must go in the **base-year column (2022)**. Resolve the target column by matching the integer year in the header row to the model year (base_year → the file's base year), never by positional offset from the first year column.
2. **BUG — Fuel Share = 0 for every device (CRITICAL).** Efficiency wrote correctly but Fuel Share came out 0. Implement `fuel_share = calculated_pj(device) / calculated_pj(end-use) × 100`, where `calculated_pj(end-use)` is the device's parent aggregate (sum of sibling device pj). Guard divide-by-zero (end-use pj = 0 → all shares 0).
3. **BUG — `Final Energy Intensity` rows never written (CRITICAL).** The writer emitted Fuel Share + Efficiency + Activity Level but no FEI. Without the absolute energy anchor LEAP computes 0. Write FEI at each in-scope end-use = `calculated_pj(end-use)` (PJ), Current Accounts base-year column, Method = Interp.
4. **BUG — end-use Activity Level written as 0 with units `Million USD`.** Write `100` with units `% / Share`; do **not** overwrite these rows' Scale/Units with a driver (the USD leak comes from binding every end-use to `gdp_ppp`, the only driver present in this run). Under the "energy in intensity" mapping no absolute driver is needed; leave Scale/Units as the template's `% Share`.

## Scenario years (when the user moves past Current Accounts)

Per the write matrix already in the handoff: devices carry **no** Fuel Share in scenarios — write device `Activity Level` share = `(final_pj_i × eff_i) / Σ_j(final_pj_j × eff_j) × 100` and `Efficiency`; write end-use `Useful Energy Intensity` = `Σ_devices(final_pj × eff) / ActivityChain` (with the flat mapping, ActivityChain = 1 → UEI = Σ(final_pj × eff) at the end-use). Final Energy Intensity is **not** written in scenarios.

## Optional future refinement (physical intensities)

When the model supplies real absolute drivers per end-use (households for Cooking/Water Heating/Lighting/Appliances; floor_area m² for Space Heating/Cooling — this run only had `gdp_ppp`, hence the USD leak), switch to a physical decomposition: end-use Activity Level = absolute driver (Scale = Million, Units = Household/Square Meter on first-region Current Accounts rows), FEI = calculated_pj(end-use) / driver. Until real drivers exist, keep the flat 100 %-share mapping above.
