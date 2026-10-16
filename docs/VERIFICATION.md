# Verification and acceptance

[Back to the project](../README.md)

**Evidence baseline: 16 October 2026.** This page summarises the owner's private handoff evidence. It is a dated account of completed checks, not a live health dashboard. The showcase was prepared without running or changing the reporting automation.

## Completed checks

| Area | Recorded evidence | What it establishes |
| --- | --- | --- |
| Reporting logic | A saved local test result with 25 passes and no failures. | Covered scenarios passed for the tested reporting logic and portable workflow structure. |
| Meta | Successful native API collection, with account timezone/currency checks and permission inspection. | Read access and the tested reporting window worked for the configured account. |
| HubSpot | Successful native contact-count collection. | The configured contact-read path worked; this is not sales or lead qualification evidence. |
| Google Sheets | Repeated successful updates to the same range, all 13 columns read back, and no appended duplicates. | The tested exports wrote the intended current table. |
| Overview tab | Formula error checks and visual review of both Sheet tabs. | The reviewed Sheet presentation and formulas worked at acceptance. |
| Data Studio | Saved dashboard reviewed in viewing mode and after reload; source totals, contact filter, responsive layout, and owner-only sharing checked. | The reviewed dashboard and Sheets connection worked at acceptance. |
| Google production consent | Successful native export after approved production reconnection. | The accepted production authorisation worked with the existing scope. |
| Google renewal | Credential update observed during a successful later report execution, without manual reconnection or a separate credential write. | One automatic token renewal was observed. |
| Weekly activation | Native trigger-mode execution reached the final report and updated the Sheet; temporary test schedule removed. | The clock-triggered path worked, and the final published configuration uses the Monday schedule. |
| Preservation | Other workflow definitions and credential metadata compared during the final activation checks. | Those unrelated records remained unchanged across the recorded operation. |

Earlier setup evidence includes inactive scheduling, Testing-mode OAuth, and incomplete provider connections. Those were intermediate stages, superseded by the later production and weekly-activation records. Test counts from different stages are not added together.

## Local test coverage

The 25 saved checks cover these areas:

- Missing connections and the requirement for credentials and account settings.
- Complete-day periods and Zurich daylight-saving boundaries.
- Malformed, missing, boolean, whitespace-only, and invalid numeric metrics.
- Weighted CTR/CPC/CPA calculations and unavailable ratios with zero denominators.
- Valid empty advertising responses and verified Meta currency during inactivity.
- Advertising pagination, currency separation, and source timezone validation.
- Platform attribution boundaries and avoidance of invented leads or sales.
- Provider authentication failures and safe report errors.
- GA4 required metrics, thresholding, and uncertainty in thresholded empty responses.
- Tag Manager metadata versus actual tracking installation.
- Meta expiry blocking and the seven-day renewal warning.
- Valid portable workflow edges, parsable logic nodes, and disabled provider requests in the portable setup copy.

Synthetic test fixtures are not live account evidence. The portable-copy check does not imply that the published personal workflow is inactive.

## What remains unverified or outside scope

| Area | Current limit |
| --- | --- |
| GA4, Google Ads, Tag Manager | No live account acceptance; real owner assets and access are pending. |
| Regular Monday recurrence | The handoff records the clock-triggered test and final schedule; it does not claim that the first regular Monday run had already occurred. |
| Complete advertising pagination | Later pages are not collected. |
| Historical reporting | Latest is overwritten; no time-series storage is implemented there. |
| Cross-source attribution | No deduplication or mapping of ad conversions to customers or revenue. |
| Alerts | No configured email or messaging notification delivery. |
| Long-term reliability | No uninterrupted uptime, future token-renewal success, or continuous dashboard health guarantee. |
| Disaster recovery | Private recovery copies exist; a full reporting-specific restore drill is not claimed. |
| Commercial use | No multi-customer acceptance, public onboarding, or commercial service readiness claim. |

## Evidence kept privately

The handoff includes the README, weekly activation verification, Google setup state, Google production verification, non-secret live profile, saved local test output, source/export checks, and dashboard UI verification. Native before/after workflow snapshots and the recovery bundle remain private.

This repository publishes a readable summary rather than those raw records. Live identifiers, credential metadata, report values, and private links are intentionally omitted. Later maintenance should update this dated status only after inspecting the relevant current state and recording new evidence.
