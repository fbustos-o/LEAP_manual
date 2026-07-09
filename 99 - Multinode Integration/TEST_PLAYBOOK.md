# Test Playbook v2 — Multinode → LEAP round-trip (base year + 2035 + 2060)

Updated to the actual v11 workflow: projection years are **not auto-generated** — each is created as a **copy of the base case**, then projected (targets/drivers edited), **re-balanced and re-optimized** independently. Milestone set for this run: **2022 (base), 2035, 2060**.

Two batches. Batch 1 = build from the LEAP v3 Buildings template. Batch 2 = same outcome from a saved JSON / DB load. Check every ✅; on failure, see the troubleshooting table.

> ⚠️ **Verifier caveat (AUDIT_v11 P1):** until the `verify-roundtrip` rewrite is applied and re-tested, its ≤3 % report is NOT reliable (flat end-uses over-count 100×; scenario splits read the wrong variable). Until then, **LEAP's Results view is the ground truth** for every energy check below.

Reference numbers, 20USA Residential base year: total = **11,554 PJ**; households = **132 M**; floor_area = **22,716.89 M m²**; Urban Space Heating ≈ **3,984 PJ** → FEI ≈ **0.17538 PJ/M m²** when linked to floor_area.

---

## Pre-flight (once)
- ✅ Back up the LEAP area `FBO_7_Test_Buildings` (work on a copy for imports).
- ✅ LEAP: base year 2022, end year 2060, scenario `Reference` present.
- ✅ `Test_LEAP_v3_Buildings.xlsx` at hand.

---

## BATCH 1 — From the LEAP template

### Step 1.1 — Load template & bind
- New project: 20USA / 2022 / 16.02 Residential; load `Test_LEAP_v3_Buildings.xlsx`.
- ✅ Reconciliation: **138 Residential leaves bound**, 0 unbound; Services out of scope; scenarios CA/Reference/Target and region United States detected.
- ✅ Fuel coverage: no blocking findings.
- ✅ Efficiencies prefilled (Heat Pump 300, Natural Gas Stove 55, Kerosene Lamps 10).

### Step 1.2 — Base case (2022): drivers, balance, optimize
- Link drivers: Space Heating & Cooling → **floor_area**; Water Heating, Cooking, Lighting, Appliances → **households**.
- Balance → SLSQP.
- ✅ Total ≈ 11,554 PJ; per-fuel vs ESTO within 1–3 %; sibling weights sum to 1.0.
- ✅ Save (DB and/or Download JSON) — this is the source for Batch 2.

### Step 1.3 — Create 2035 as a COPY of the base case, project it
- Create milestone year **2035** (copy of base case).
- ✅ Immediately after copying: 2035 tree = identical structure and weights to 2022 (spot-check one end-use).
- Project it: set the 2035 macro target (e.g. total +10 %) and the 2035 driver values (households, floor_area); adjust any weight bounds you want to steer (e.g. mild electrification).
- **Re-balance + re-optimize the 2035 slice.**
- ✅ 2035 total = your target; per-fuel residuals within tolerance; weights re-optimized (different from 2022 where you changed bounds).

### Step 1.4 — Create 2060 as a COPY, project deep changes
- Create milestone year **2060** (copy of base case or of 2035 — note which, for reproducibility).
- Project it: **zero out** selected fuels (e.g. Kerosene/Charcoal heaters: max_weight = 0), **raise Electricity** (heat pumps up), raise the global total; set 2060 driver values.
- **Re-balance + re-optimize the 2060 slice.**
- ✅ Zeroed fuels show weight/pj = 0; Electricity share clearly above 2022; total = target; Others_Unspecified absorbs residual.
- ✅ Efficiencies per year where changed (e.g. Heat Pump 2060 > 2022 if you model improvement).

### Step 1.5 — Compile to LEAP & review
- Compile Review: Region = United States, Scenario = **Reference**.
- ✅ Modal scrollable/collapsible; Year filter switches 2022 / 2035 / 2060.
- ✅ Current Accounts (2022): end-use FEI (PJ or PJ/driver-unit); device Fuel Share sums 100 %; Efficiency ×100; driver-linked end-uses show Activity Level = driver value (Million + Household/Square Meter).
- ✅ Reference: UEI per end-use for 2035 & 2060; device Activity Level (useful-energy share) per year; Efficiency per year; **no Fuel Share rows**; **2022 column empty in Reference**.
- ✅ No sanity badges (shares ≠ 100, non-PJ units).
- Download.

### Step 1.6 — Import into LEAP & verify (ground truth)
- LEAP → Analysis → Import from Excel → **as Data**, "Values only replace Interp/Step" ON.
- **Current Accounts:** ✅ Urban Space Heating: Activity = 22,716.89 M m², FEI ≈ 0.17538; a device shows expected Fuel Share/Efficiency; Results total ≈ 11,554 PJ, per-fuel ≈ ESTO.
- **Reference:** ✅ pick a changed device (e.g. Heat Pump in Space Heating) → Activity Level tab shows the trajectory (2022 anchor from CA, then 2035 and 2060 points, smooth interpolation, **no zero dips between milestones**).
- ✅ Results per year: 2035 total = its target; 2060 total = its target; zeroed fuels → 0 by 2060; Electricity rises.
- ✅ `Target` scenario untouched (trimming worked).

**Batch 1 pass = CA exact + 2035/2060 trajectories visible and correct in LEAP Results.**

---

## BATCH 2 — Same outcome from saved JSON / DB

1. New session → load the saved JSON (with base + 2035 + 2060) or load the project from DB.
   - ✅ Compile/Verify disabled with tooltip until a template is attached.
2. Attach `Test_LEAP_v3_Buildings.xlsx` → ✅ 138 bound / 0 unbound (path binding).
3. Compile Reference → ✅ workbook cell-for-cell equivalent to Batch 1's (compare the Urban Space Heating block for 2022/2035/2060).
4. Import into a fresh area copy → ✅ same LEAP results as Batch 1.

---

## Cross-cutting acceptance
- ✅ Re-importing the same file twice into LEAP is idempotent.
- ✅ Compiling against a template from another area (e.g. the old `FBO_6` v2 file) is refused (fingerprint) — run once as a negative test.
- ⚠️ `verify-roundtrip` ≤3 % per fuel per year: only meaningful **after** the AUDIT_v11 P1 fix; then expect ~0 % on a writer-produced file re-uploaded unchanged.

## Troubleshooting
| Symptom | Likely cause |
|---|---|
| 2035/2060 copy differs from base right after creation | copy routine not deep-copying weights/fuels/efficiencies |
| Re-balance of one year changes another year's numbers | tree slices share references (need deep copy per year) |
| Writer error "Milestone year X not present in template columns" | projection year outside 2022–2060 or template mismatch |
| Trajectory dips to 0 between milestones in LEAP | non-milestone cells not cleared / Method not Interp |
| Demand = 0 for an end-use in LEAP | FEI missing or driver value 0 (flat fallback triggered) |
| Fuel shares ≠ 100 % | normalization must be against sibling sum |
| verify-roundtrip fails everything while LEAP Results look right | AUDIT_v11 P1 (verifier bug) — trust LEAP Results |
| Zeroed fuel still shows energy in 2060 | weight not truly 0 (check max_weight=0 honored) or uniform-split fallback on all-zero siblings |
| Values one year off | base-year column mapping regression |
| Many unbound at attach | name mismatch (case/spacing) or wrong sector root prefix |
