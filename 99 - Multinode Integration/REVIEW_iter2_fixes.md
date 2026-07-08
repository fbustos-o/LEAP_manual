# Review of 2nd export + Compile-Review modal UX — fixes for the agent

The 2nd Current-Accounts export (`...135521.xlsx`) is **correct**: values in the 2022 base-year column; `Final Energy Intensity` = `calculated_pj` per end-use (PJ); `Fuel Share` = device/end-use share; `Efficiency` ×100; `Activity Level` = 100 % Share (USD leak gone); Method = Interp; non-milestone years cleared; IDs preserved; device FEI placeholders trimmed. Two small items remain.

## Fix 1 — Renormalize Fuel Share within each end-use (robustness)

Observed: `Rural\Lighting` fuel shares summed to **200 %**, `Urban\Lighting` to **0 %**. Root cause is rounding, not logic: the model JSON stores `calculated_pj` rounded to 4 decimals, so two devices at 0.0001 sum to 0.0002 while the end-use reads 0.0001 → each share = 100 %.

Change the device Fuel Share computation to **normalize against the sum of sibling device pj**, not the (independently rounded) end-use pj, and use full-precision internal values:

```
denom = Σ_j calculated_pj(device_j)         # sum over siblings, full precision
fuel_share_i = 0 if denom == 0 else calculated_pj_i / denom * 100
```

This always sums to exactly 100 % (or 0 % when the end-use has no energy), immune to rounding. Apply the same normalization to the scenario-year device `Activity Level` shares (`(pj·eff)/Σ(pj·eff)`). Note: `Final Energy Intensity` at the end-use must still be the end-use's own `calculated_pj` (LEAP multiplies FEI × fuel share, so the absolute stays correct). Add a test: every end-use's written Fuel Shares sum to 100 ± 1e-6 or all-zero.

(No action needed for the huge magnitudes like Rural\Space Cooling = 4988 PJ — those come from an un-optimized test tree, not the writer.)

## Fix 2 — "LEAP Compile Review" modal is unusable; make it a proper reviewer

Current problems (from user): the pre-download review table is cramped, cannot be scrolled through fully, and cannot be closed/reopened without losing the compile; it also does not clearly mirror what lands in the Excel.

Requirements:
1. **Collapsible in place:** add a caret/▸ toggle in the modal header that collapses/expands the review table **without** discarding the compiled result or closing the modal. The `Download` action stays available whether collapsed or expanded. The existing `×` keeps closing the whole modal.
2. **Full scroll:** the results table body must be vertically scrollable with a fixed, always-visible header row and a bounded `max-height` (e.g. 60vh); it must never push the `Cancel`/`Download` buttons off-screen. Horizontal overflow scrolls inside its own container.
3. **Mirror the Excel exactly (verification view):** show one row per cell that will change, with columns: `Branch Path` (the readable path, not just the numeric BranchID — resolve it), `Variable`, `Scenario`, `Region`, `Year`, `Excel Cell` (R#C#), `Old Value`, `New Value`. Group/sort by Branch Path then Variable so a reviewer can scan an end-use and its devices together. Show a top summary line: counts of FEI / Fuel Share / Efficiency / Activity rows and the target Region + Scenario.
4. **Sanity badges (optional but useful):** per end-use, a small badge if its Fuel Shares do not sum to ~100 %, and a global badge if any FEI unit ≠ Petajoule — so the user catches problems before download, not after importing into LEAP.
5. The "Clear" rows (non-milestone years being emptied) are noise for verification — collapse them under a single expandable "N cells cleared" line rather than one row each.

These are `app.js` / `styles.css` changes only; the review data already exists in the dry-run payload.
