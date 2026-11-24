# Neutron-2 CDR verification dashboard

A single-page dashboard that checks the Neutron-2 (N2) CDR budgets against the mission requirements and shows pass or fail for each check. Open `index.html` in a browser, or view it on GitHub Pages at https://hsfl.github.io/n2-cdr/ once Pages is enabled. It needs no build step or server, and all data is embedded in the file.

Current version: v1.2 (snapshot pulled 23 Nov 2026). The budget workbooks and RVM v4.0 are unchanged since 18 Sep 2026.

## What the page shows

- **Verdict and ledger.** A headline count of passing and failing checks, and a ledger of 15 checks grouped by budget:
  - Mass (M1, M3): 6 kg limit, from the Simplified Mass Budget only, and the 2 kg payload allocation.
  - Power (P1–P4): 80 Wh battery (UNP12-62), 30% safe-mode trigger (OPS-010), 15-minute collection window.
  - Link (L1–L3): 6 dB margin at 10° elevation (UNP12-90).
  - Data (D1–D4): downlink volume and 4 GB storage.
  - Pointing (G1–G2): 36° payload pointing (ADCS-001) and 2° ground tracking (ADCS-003).
- **What-if inputs.** Mass margin, bit rates, S-band pointing loss and ADCS error can be changed to see which checks flip. Reset returns to the CDR values.
- **Arcadia trace map.** Draft operational, system, logical and physical layers (Pre-Phase A to Phase C, following the SmallSat 2025 MBSE poster). Selecting a check or a node highlights what it traces to. A Capella export in JSON can be loaded to replace the draft layers.
- **SysML v2 export.** Generates textual SysML v2 from the current check values, with copy and download. The export validates with the OpenSysML tool in strict mode.
- **Flags.** Cross-budget inconsistencies and mismatches between a budget and the requirement it supports.
- **Reviewer findings.** Open items from the UNP CDR compiled feedback, with the 4 Dec 2026 resubmission deadline.
- **RVM progress.** Verification status by subsystem from the Requirements Verification Matrix: 184 requirements below Tier 1, with FSW-007 retired per the v5.0 FSW tab draft.

## Data sources

- N2.PM.System Budgets v3.0 (SOURCE), Simplified Mass Budget only
- N2.PM.System Budgets v2.1 (link, data, storage, pointing)
- N2.PM.Power Budget v2.0 (STK-based energy balance)
- N2.PM.Requirements Verification Matrix v4.0, plus the FSW tab of the v5.0 draft
- UNP CDR compiled feedback and the Spacecraft 2/3 CDR deck

The values are a snapshot copied into the `D` object in `index.html`. The page does not read the workbooks live, so it must be updated when the budgets change.

## Caveats

- The workbooks have not been revised since the reviewer findings, so the checks still reflect the September numbers.
- The Arcadia layers are drafts built from the MBSE thesis, the RVM and the budgets. They are not read from the Capella model.
- The full RVM v5.0 was not available, so v4.0 is the baseline for every tab except FSW.
