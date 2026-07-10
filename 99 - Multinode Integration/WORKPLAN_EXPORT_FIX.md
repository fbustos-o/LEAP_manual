# Work Plan — Fix LEAP export pipeline, year-specific optimization, and UI reactivity

**To:** v11 coding agent. Apply in order A → B → C → D. File edits only. Output the User Verification Checklist at the end and stop.

## Diagnosed root causes (verified in the current code)

1. **Projections never reach the DB before export.** `handleAddProjection` (app.js ~1808) clones base_year into `state.selectedScenario.tree_state[yearStr]` and only calls `markUnsaved()`. The export endpoint reads the **database** (`db_project.scenarios[0].tree_state`). If the user compiles without pressing DB Save, the DB tree has only `base_year` → `LeapWriter.milestone_years = [2022]` → in Reference the writer's year loops skip everything (base year is excluded from REF), `_clear_non_milestone_years` blanks every column except 2022, and the template's stale 2022 values survive. That is exactly the observed output: one populated 2022 column with wrong values, all projection years empty.
2. **Export may read the wrong scenario row.** `export_leap_values` uses `db_project.scenarios[0]` — ordering is arbitrary when a project has several scenario rows. The endpoint must receive the active `scenario_id`.
3. **Writer macro-driver lookups use the wrong key.** Everywhere the writer does `self.macro_drivers.get(str(self.base_year))` (i.e. `"2022"`), but the dict is keyed `"base_year"`. CA driver values are therefore never found (silent flat fallback).
4. **Driver values are now objects.** Per the D7 UI, drivers are stored as `{value, scale, leap_unit, display_label}`. The writer calls `float(macro[driver_key])` → `TypeError` on any driver-linked branch (uncaught → HTTP 500), and hardcodes `DRIVER_METADATA` instead of using the driver's own scale/unit.
5. **Projection-year optimization uses base-year fuel targets.** `optimize_scenario` (routers ~281) calls `attach_active_fuels` (flat, base-year ESTO) for every year — the code comments admit it. For 2060 the user zeroes fuels and raises totals, so SLSQP chases 2022 per-fuel targets under contradictory bounds → the reported 2060 conflict. Also `target = macro.get("target_total")` reads the TOP level of the year-keyed `macro_drivers` dict → always None unless the payload carries it; and `api.js optimizeScenario` never sends `year`.
6. **Auto-added years contradict the new workflow.** `import-template`/`import-stateless` still auto-create the first and last template years (`years_to_add` → "2023", "2060"). Years must be user-created copies only.
7. **UI staleness.** Balance modal and node deltas render from cached values; on year-tab switch or after editing year targets they keep showing base-year numbers (visual only, but it hides problem #1 from the user).

---

## A — Make the export pipeline trustworthy (highest priority)

**A1. Export/Verify take an explicit scenario and auto-save first.**
- Backend: add `scenario_id: int = Form(...)` to `/leap/export-values` and `/leap/verify-roundtrip`; load that scenario (404 if not in project). Remove all `scenarios[0]` access.
- Frontend: the Compile handler (app.js ~2699) must, before the dry-run and before the download, persist the full current state: `await updateScenario(id, { tree_state, macro_drivers, active_fuels })`. Same in the Verify handler. Show a small "Saving…" state on the button. (Auto-save, not a blocking prompt.)
- `updateScenario` backend (`PUT /scenarios/{id}`) must accept and persist `macro_drivers` and `active_fuels` too (see B1 for the column).

**A2. Fix the writer's year-key access — one helper, used everywhere.**
```python
def _macro_for(self, year: int) -> dict:
    key = "base_year" if year == self.base_year else str(year)
    return self.macro_drivers.get(key, {})
```
Replace every `self.macro_drivers.get(str(self.base_year))` / `.get(str(y))` in `_traverse_and_write`, `_write_macro_variables`, `_get_activity_driver_value`.

**A3. Driver values may be scalars or objects.**
```python
def _driver_value(self, macro: dict, key: str) -> float | None:
    v = macro.get(key)
    if v is None: return None
    return float(v["value"]) if isinstance(v, dict) else float(v)
```
Use it in all driver reads. When writing Scale/Units on driver-linked CA rows, take `scale`/`leap_unit` from the driver object itself when present; keep `DRIVER_METADATA` only as fallback for scalar drivers.

**A4. Stop auto-creating projection years.** In `leap/import-template` and `leap/import-stateless`, build `new_tree = {"base_year": tree_state}` only (delete the `years_to_add` first/last-year logic). Projection years are created exclusively by the user's "Add Projection" (clone of base), per the copy-based workflow.

**A5. Surface the milestone set instead of failing silently.** The dry-run response gains `"milestone_years": [...]` and `"scenario_id"`; the Compile Review modal header shows "Years to write: 2022, 2035, 2060". If the set is only the base year while the project has projection tabs, show a warning banner ("Projections exist in the UI but are not saved — they were saved automatically now" / or a hard error if still divergent).

**A6. Writer tests for the regression:** build a scenarios dict with base+2035+2060, run fill(), assert REF rows carry values in the 2035/2060 columns and the 2022 REF column is EMPTY (not stale); assert a driver-linked end-use with object-style driver writes Activity = value and Scale/Units from the object; assert TypeError can no longer occur (object driver test).

## B — Year-aware balancing & optimization (fixes the 2060 conflict)

**B1. Persist per-year fuel targets.** `Scenario.active_fuels` becomes a stored JSON column (dict keyed `"base_year"|"<year>"` → list of `{fuel_id, value}`), mirrored in `schemas.py`. Migration: if the column is absent/None, generate `{"base_year": <ESTO query>}` on read (backward compatible). `attach_active_fuels(scen, economy, flow, year=None)` fills ONLY missing years from ESTO; it must never overwrite user-edited year entries.
- Frontend already migrates `active_fuels` to a year-keyed dict in `handleAddProjection`; make that the canonical shape everywhere (panel edits write to `active_fuels[activeYear]`).

**B2. Fix `/scenarios/{id}/optimize`.**
- `payload.year` required (400 with clear message if missing); `api.js optimizeScenario(scenarioId, targetTotal, year)` sends `state.activeYear`.
- Resolve `target_total` from `macro_drivers[year]` (`target_total` → `total` fallback), honoring object-or-scalar values; payload override wins.
- Pass `active_fuels[year]` to `optimize_tree_state` — never the base list for a projection year.

**B3. Same discipline in the stateless path.** Wherever the canvas Balance/SLSQP buttons call `optimizeStatelessTree`, confirm they pass `tree_state[activeYear]`, `macro_drivers[activeYear]`, `active_fuels[activeYear]`, and write the result back only into `tree_state[activeYear]`.

**B4. Feasibility pre-check with actionable message.** Before running SLSQP: for every fuel target > 0, verify at least one leaf carrying that fuel has a reachable path (all ancestors `max_weight > 0` and leaf `max_weight > 0`). Collect violations and return `optimization_success=false` with `optimization_message = "Infeasible: fuel targets > 0 with no available capacity: [07.06 Kerosene (target 12.3 PJ, all leaves max_weight=0)] — zero the target or relax a bound."` Also detect the inverse (target 0 but min_weight forces energy). This turns the 2060 "self-conflict" into a precise instruction to the user.

**B5. Tests:** optimize year=2060 with edited fuels uses ONLY the 2060 targets (assert by spying the objective inputs or by result); infeasible case returns the message, does not throw; base year untouched after a 2060 optimize (deep-copy isolation assert).

## C — Frontend reactivity (year switching)

**C1. Single source of truth per year.** One render pipeline keyed on `state.activeYear`: switching tabs re-renders canvas nodes, the Total Energy panel, fuel-delta table, and any open balance modal strictly from `tree_state[activeYear]` + `macro_drivers[activeYear]` + `active_fuels[activeYear]`. Kill any cached copies captured at modal-open time.
**C2. Balance modal recomputes on open and on year switch**, and its title carries the year ("Balance Check — 2060") so a stale view is instantly recognizable. If the modal is open while the user switches year, refresh or close it.
**C3. Node deltas after edits.** Edits in the projections panel (total energy increase, fuel deltas) must trigger the same re-render for the affected year (event → recompute cascaded pj → re-render canvas). Add the year badge to node tooltips for clarity.
**C4. Unsaved-state affordance.** `markUnsaved()` should light a visible "Unsaved changes" pill next to DB Save; Compile auto-saves (A1) and then clears it.

## D — Documentation & handback

- Update walkthrough with "Export pipeline fixes" section.
- Update `tests/MANUAL_UI.md` with the year-switch reactivity checks.

---

## User Verification Checklist (output this, then stop)

1. `pytest -q` green (state total + new counts).
2. Load template → base year balance+optimize → **Add Projection 2035** (edit targets, optimize) → **Add Projection 2060** (zero one fuel, raise electricity+total, optimize):
   - 2060 optimization either converges or returns the explicit infeasibility message naming the conflicting fuels — no silent failure.
   - Switching year tabs updates Total Energy panel, node values and balance modal (title shows the year).
3. Compile → Review modal header lists "Years to write: 2022, 2035, 2060"; REF rows show 2035/2060 values, 2022 column empty in REF; CA rows show base values; driver-linked end-uses show the driver's value/scale/unit from the driver editor.
4. Download → open in Excel: Reference rows have data at 2035/2060 (not only 2022); import into LEAP → trajectories visible in Results for both years.
5. Negative: create a projection, do NOT press DB Save, hit Compile → the export still contains the projection (auto-save proved).
