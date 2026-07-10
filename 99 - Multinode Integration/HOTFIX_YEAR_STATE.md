# Hotfix — Year-keyed state: false infeasibility + Projections Dashboard staleness

**To:** v11 coding agent. Two defects, one theme: code paths that ignore the active year's slice of the year-keyed state. Fix A (backend) first, then B (frontend). Output the User Verification Checklist and stop.

## A — Feasibility pre-check reports EVERYTHING infeasible (backend, blocking)

**Observed:** running optimization after the last fixes returns
`Infeasible: fuel targets > 0 with no available capacity: [07.06 Kerosene (target 8.553482 …), … 17 Electricity (target 5430.907386 …)] — all leaves max_weight=0`
listing **all nine fuels** with **base-year target values**, while the user confirms every `max_weight` in the tree is 1. A pre-check that finds zero capacity for every fuel at once is examining the wrong tree.

**Check these candidate causes in order (at least one is present):**
1. **Wrong tree object passed to the pre-check.** The check must receive the **year slice** (`year_tree = tree[year]`), not the multi-year dict `{"base_year": {...}, "2035": {...}}`. Traversing the outer dict finds no `fuels` anywhere → every fuel appears uncovered. Verify the call site in `/scenarios/{id}/optimize` and in the stateless path.
2. **Default bound treated as 0.** Patterns like `float(node.get("max_weight") or 0)` or `.get("max_weight", 0)` turn a *missing* key into 0 (unreachable). The default for a missing/None `max_weight` is **1.0** (`b = 1.0 if raw is None else float(raw)`); same for fuel-level `max_weight`. Note `or` also mangles legitimate `0.0` on min bounds — use explicit None checks.
3. **Reachability tested on current `weight` instead of bounds.** The pre-check must ask "could this leaf carry energy?" → ancestors and leaf `max_weight > 0` — never the current weight (which can legitimately be 0 before optimization).
4. **Targets taken from the wrong year.** The listed targets are the base-year ESTO values; the pre-check must use the same `active_fuels[year]` list that the optimization run uses.

**Tests (regression gate):**
- Year slice where every node/fuel `max_weight` = 1 and 9 fuel targets > 0 → pre-check passes (no exception).
- Same tree with ONE fuel's only leaf capped at `max_weight = 0` → exactly that fuel listed, others pass.
- Missing `max_weight` keys on some nodes → still feasible (default 1.0).
- Pre-check on a 2035 run uses `active_fuels["2035"]` values, not base (assert on the message content with distinct targets).

## B — Projections Dashboard and fuel bars ignore the active year (frontend)

**Observed (screenshot, active tab = 2035 after a +10 % projection):** the left TOP-DOWN MACRO TARGET panel already shows ΔPJ = 12,709.76, but the dashboard cards still show Bottom-Up = 11,554.33 and **Top-Down Target = 11,554.33** (base value), and the Fuel Target Tracking bars keep full width even though their ΔPJ inputs updated (bar fill uses a stale denominator).

**Required behavior — one render path keyed on the active year:**
1. Implement (or finish) `renderProjectionsDashboard(yearKey)` that derives EVERYTHING from the year slice:
   - `target = macro_drivers[yearKey].target_total ?? .total` (object-or-scalar safe);
   - `bottomUp = recomputed tree energy of tree_state[yearKey]` (same routine the canvas uses);
   - `imbalance = bottomUp − target`;
   - fuel bars: for each fuel in `active_fuels[yearKey]`: `calc = Σ calculated_pj of that fuel in tree_state[yearKey]`, `target_f = value`, bar width = `clamp(calc/target_f × 100, 0, 100)`, label `calc / target_f PJ`, color by deviation band (≤1 % green, ≤3 % amber, else red).
2. Call it from **every mutation point**: year-tab switch; Δ% / ΔPJ edits in the TOP-DOWN MACRO TARGET panel; per-fuel Δ% / ΔPJ edits in the tracking cards; Balance completion; SLSQP completion; Add/Remove Projection. Remove any values cached at first render.
3. The Δ%/ΔPJ editors must write to `macro_drivers[state.activeYear]` and `active_fuels[state.activeYear]` (never base) — and the two inputs stay consistent (editing Δ% recomputes ΔPJ and vice versa, both against the BASE-year reference value).
4. Title/badge the dashboard with the active year ("Projections Dashboard — 2035") so staleness is visually impossible to miss.
5. `markUnsaved()` after these edits (they must ride the Compile auto-save).

**Manual test additions for `tests/MANUAL_UI.md`:** the checklist below.

## User Verification Checklist (output this, then stop)

1. `pytest -q` green; feasibility tests included (state counts).
2. Base year: Balance + SLSQP converge exactly as before (no false infeasible).
3. Switch to 2035 (copy of base), set Δ% = 10 in TOP-DOWN MACRO TARGET:
   - Top-Down Target card updates to 12,709.76 **immediately**;
   - fuel bars re-scale (≈ 91 % fill: base calc vs new target), labels show `calc / new-target`;
   - dashboard title shows "— 2035".
4. Run SLSQP on 2035 → converges; Bottom-Up card updates to ≈ 12,709; Solver Imbalance ≈ 0; bars go green.
5. Switch back to 2022 (Base) → all cards and bars instantly show base numbers again; switch to 2035 → 2035 numbers return (no leakage either way).
6. Deliberately cap one fuel's leaves at max_weight = 0 in 2035 with a positive target → optimization returns the infeasibility message naming ONLY that fuel.
