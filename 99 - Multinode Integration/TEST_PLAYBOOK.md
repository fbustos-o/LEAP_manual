# Test Playbook — Multinode → LEAP round-trip (Current Accounts + Reference multi-year)

Two batches. Batch 1 = build everything from the LEAP v3 Buildings template. Batch 2 = repeat from a saved JSON / DB load to prove both entry paths reach LEAP identically. Check every ✅; if one fails, note the step and (likely cause) from the troubleshooting table.

Reference numbers for 20USA Residential base year (from your model): total residential = **11,554 PJ**; households = **132 M**; floor_area = **22,716.89 M m²**; Urban Space Heating base ≈ **3,984 PJ** → FEI ≈ **0.17538 PJ/M m²**.

---

## Pre-flight (once)

- ✅ Back up the LEAP area `FBO_7_Test_Buildings` before any import (File → Save As a copy).
- ✅ In LEAP, note base year = 2022, end year = 2060, scenario = **Reference** exists.
- ✅ Have the canonical template `Test_LEAP_v3_Buildings.xlsx` at hand.

---

## BATCH 1 — Build from the LEAP template

### Step 1.1 — Load template & bind
- Create project, economy **20USA**, year **2022**, sector **16.02 Residential**; load `Test_LEAP_v3_Buildings.xlsx`.
- ✅ Reconciliation shows **138 Residential leaves bound**, 0 unbound; Services out of scope; region = United States; scenarios Current Accounts / Reference / Target detected.
- ✅ Fuel-coverage check: no blocking findings (all ESTO fuels with target map to a bound leaf).
- ✅ Efficiencies auto-prefilled (spot-check Heat Pump = 300, Natural Gas Stove = 55, Kerosene Lamps = 10).

### Step 1.2 — Base year: link drivers, balance, optimize
- Link drivers: Space Heating & Space Cooling → **floor_area**; Water Heating, Cooking, Lighting, Appliances → **households**.
- Run Balance, then SLSQP.
- ✅ In multinode, base-year total ≈ 11,554 PJ and per-fuel matches ESTO within 1–3 %.
- ✅ Sibling weights sum to 1.0 per parent (normalization pass ran).

### Step 1.3 — Project 2023 (+10 % global, no structural change)
- Add milestone year **2023**; set the macro target / driver growth so total demand is **+10 %** vs 2022, shares unchanged.
- ✅ 2023 total ≈ 12,710 PJ (11,554 × 1.10); per-end-use and per-fuel shares ≈ same % as 2022.
- ✅ Driver values for 2023 are set (households/floor_area for 2023 present, not just gdp).

### Step 1.4 — Project 2060 (electrification + growth)
- Add milestone year **2060**; set some fuels to **0** (e.g. Kerosene/Charcoal in an end-use), raise **Electricity** demand and the global total.
- ✅ Zeroed fuels show weight/`calculated_pj` = 0 in 2060; Electricity share visibly higher than 2022.
- ✅ 2060 total = your chosen higher figure; balance still closes (Others_Unspecified absorbs residual).

### Step 1.5 — Add 2035 (intermediate)
- Add milestone year **2035**; set values between 2023 and 2060.
- ✅ Project now has years [2022, 2023, 2035, 2060]; each has its own balanced `calculated_pj`; removing/re-adding 2035 is clean.

### Step 1.6 — Compile to LEAP & review
- Open Compile Review, target Region = United States, Scenario = **Reference**.
- ✅ Review is scrollable/collapsible; **Year filter** lets you switch 2022/2023/2035/2060.
- ✅ Current Accounts (2022): end-use **Final Energy Intensity** in PJ; device **Fuel Share** sums to 100 % per end-use; **Efficiency** ×100; driver-linked end-uses show Activity Level = driver value (Million, Square Meter / Household).
- ✅ Reference: end-use **Useful Energy Intensity** per year; device **Activity Level** (share) per year; **Efficiency** per year; **no Fuel Share** rows; **2022 column empty in Reference** (anchored from CA).
- ✅ Sanity badges: no "shares ≠ 100 %", no "unit ≠ PJ".
- Download the workbook.

### Step 1.7 — Import into LEAP & verify
- LEAP → Analysis → **Import from Excel** → Import as **Data**, "Values only replace Interp/Step" ON.
- **Current Accounts checks (Analysis view, Scenario = Current Accounts, Region = United States):**
  - ✅ `Demand\Buildings\Residential\Urban\Space Heating`: Final Energy Intensity ≈ 3,984 (if flat) or Activity Level = 22,716.89 (Million m²) + FEI ≈ 0.17538 (if driver-linked).
  - ✅ A device (e.g. Diesel Heater) shows the expected Fuel Share and Efficiency.
  - ✅ Results view → total residential demand ≈ 11,554 PJ; per-fuel ≈ ESTO.
- **Reference checks (Scenario = Reference):**
  - ✅ Pick `…\Space Heating\Electric Heater` → Activity Level tab shows a trajectory 2022→2060 (2022 from CA, then your 2023/2035/2060 points, interpolated between).
  - ✅ Efficiency tab shows the per-year values.
  - ✅ Results view → total demand: 2023 ≈ +10 % vs 2022; 2060 = your higher figure; the zeroed fuels drop to 0; Electricity rises.
  - ✅ Chart the trajectory: smooth interpolation between your milestone years (no zero dips in the in-between years → confirms non-milestone cells were cleared, not written 0).

**Batch 1 pass = Current Accounts correct AND Reference shows the multi-year trajectory in LEAP Results.**

---

## BATCH 2 — Same outcome from a saved JSON / DB load

Goal: prove the model reaches LEAP identically whether structure came from the template, a saved JSON, or the DB.

### Step 2.1 — Load model, then attach template
- New session; **load the saved JSON** (the one with all scenarios) OR load the project from the DB.
- ✅ Compile / Verify are **disabled** with tooltip "Attach a LEAP template first" (no template yet).
- Use **Load LEAP Template** → upload `Test_LEAP_v3_Buildings.xlsx`.
- ✅ Reconciliation binds by branch path: 138 bound, 0 unbound. (If any unbound → it's a name mismatch; see troubleshooting.)

### Step 2.2 — Compile & compare
- Compile Reference; download.
- ✅ The generated workbook is **cell-for-cell equivalent** to Batch 1's (same FEI, Fuel Share, Activity Level, Efficiency per year) — allowing for any values you changed. Quick way: open both, compare Urban Space Heating block.

### Step 2.3 — Import & verify in LEAP
- Import into a fresh copy of the area; repeat the Current Accounts + Reference checks from Step 1.7.
- ✅ Same demand totals and trajectories as Batch 1.

**Batch 2 pass = JSON-load and DB-load produce the same LEAP result as the template-built path.**

---

## Cross-cutting acceptance
- ✅ `verify-roundtrip` (upload the LEAP re-export): per-fuel, per-year deviation ≤ 3 % for 2022/2023/2035/2060.
- ✅ Target scenario in LEAP is untouched after import (output trimming worked).
- ✅ Re-importing the same file twice is idempotent (no doubling, no drift).

## Troubleshooting quick-reference
| Symptom in LEAP / multinode | Likely cause |
|---|---|
| Demand = 0 for an end-use | FEI row not written / driver value = 0 (flat fallback) |
| Fuel shares sum ≠ 100 % | rounding — must normalize against sibling sum, not parent |
| Device trajectory dips to 0 between milestone years | non-milestone year cells not cleared (Method must be Interp, cells empty) |
| Values appear one year off (2023 instead of 2022) | base-year column mapping regression |
| Many "unbound" at reconcile | branch-name mismatch (case/spacing) or wrong sector root prefix |
| Target scenario changed after import | output trimming not applied (Target rows leaked into the file) |
| Driver shows units "USD" everywhere | end-use linked to gdp by default instead of floor_area/households |
| 2060 zeroed fuel still shows energy | weight not actually 0, or normalization forced a uniform split on all-zero siblings |
