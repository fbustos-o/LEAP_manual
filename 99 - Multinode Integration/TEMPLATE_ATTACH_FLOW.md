# Fix — "Attach LEAP Template" as a first-class step (unblocks Compile for JSON / from-scratch projects)

## Problem

Exporting to LEAP requires a parsed LEAP template (it is the only source of the row IDs the writer fills). Today the template is only attached during initial project creation. Projects that start from a **loaded JSON** or **from scratch** have no template, so:
- `Compile to LEAP` only pops a warning ("no LEAP file loaded") on click — a dead end.
- The user is forced to abuse `Verify LEAP Round-Trip` to upload the Excel, which is the wrong concept (Verify is a post-import check, not a setup step).

## Desired behavior

Make attaching + binding a LEAP template an explicit action available on **any** project at any time, with a reconciliation step, that then unlocks Compile/Verify. Three entry states must be handled cleanly:

| Project origin | Has template? | Compile / Verify |
|---|---|---|
| Created by importing a LEAP template | yes | enabled |
| Loaded from JSON | no → until attached | **disabled with clear reason**, plus a prominent "Load LEAP Template" action |
| New from scratch | no → until attached | same |

`Compile to LEAP` and `Verify LEAP Round-Trip` must be **disabled (greyed, with tooltip "Attach a LEAP template first")** whenever `project.leap_template_parsed` is absent — never a click-time warning.

## Backend

1. **Reuse the existing template parse+bind logic** (the `POST /leap/import-template` path / `LeapTemplate` parser + the reconciliation used at project creation). Expose it as an action that can run against an **existing** project, not only at creation:
   - `POST /projects/{id}/leap-template` (multipart Excel) → parse, bind the project's current tree to the template, persist `leap_template_bytes` + `leap_template_parsed` + per-node `leap_binding` on the project, return the reconciliation report. Idempotent: re-attaching replaces the previous template (warn if the new template's BranchID fingerprint differs from a previously compiled one).
2. **Do not** compute or persist the template inside `Verify`. Verify keeps only its own transient upload for round-trip comparison. Both Compile and Verify read the template already attached to the project.
3. Reconciliation report (returned to the UI) must include, computed by **branch-path binding** (see rules below):
   - bound leaves (count), by sector scope;
   - **multinode nodes with no matching template branch** (these will NOT be exported — the important list for the user);
   - template device leaves with no multinode node (will remain empty in LEAP);
   - fuel-coverage findings (fuels with non-zero ESTO target not covered by any bound leaf);
   - area name / fingerprint / region list / scenario list.

## Branch-path binding rules (the crux of "do the nodes match?")

The saved JSON has `leap_binding = null`, so binding is re-established by matching **branch paths**, not stored IDs:
1. Map the multinode tree root to the template demand root via the session sector (dictionary): `16.02 Residential → Demand\Buildings\Residential`, `16.01 Commercial and public services → Demand\Buildings\Services`. Make this prefix editable in the reconcile UI (LEAP branch names may be localized).
2. For each multinode node, build its full template path = root prefix + the node_id chain, and look it up in the parsed template's path→row index. On match, attach `leap_binding` (BranchID + the variable/scenario/region row map). On miss, mark the node **unbound**.
3. Matching is on the **exact branch path string** (LEAP matches by ID, but we re-derive by path here). Normalize only whitespace; do NOT fuzzy-match — surface mismatches instead so the user fixes names. Common mismatch causes to display helpfully: case/spacing differences ("Natural gas Heater" vs "Natural Gas Heater"), Services depth (`Services\<BuildingType>\<EndUse>\<Device>`), renamed devices.
4. A project is "compilable" when ≥1 leaf is bound and there are no blocking fuel-coverage findings; Compile still exports only bound rows (unbound nodes are skipped, and listed).

## Frontend

1. In the **Model Execution & Export** panel add a **"Load LEAP Template"** action (or repurpose the template step so it is reachable post-creation). Its modal:
   - file picker (Excel), Target Region + Scenario selectors (populated after parse), and a **Run Reconciliation** result view.
   - reconciliation view = a two-column diff: "Bound (N)" and "Unbound / mismatched (M)" with the readable branch paths, plus a fuel-coverage badge. This is the "check that the built nodes match LEAP" the user asked for.
   - a confirm button that persists the attachment and closes; on success, Compile/Verify become enabled.
2. Gate `Compile to LEAP` and `Verify` on `project.leap_template_parsed`; show the tooltip when disabled. Remove the click-time "no file loaded" warning path.
3. After attach, the Compile Review modal (already rebuilt) works unchanged — it now has a template to preview against.

## Acceptance checklist (for the user to verify)

- Load a JSON-only project → Compile and Verify are disabled with a tooltip; a visible "Load LEAP Template" action exists.
- Attach `Test_LEAP_v3_Buildings.xlsx` → reconciliation lists the bound residential leaves and any unbound nodes; fuel coverage OK.
- Compile becomes enabled → Compile Review shows the same values that land in the Excel → download works and imports into LEAP.
- Attaching a template whose branch names differ from the tree surfaces the mismatches (not a silent empty export).
- From-scratch project behaves identically once a tree exists and a template is attached.
