# Verification and acceptance

[Back to the project](../README.md)

**Evidence baseline: 16 October 2026, including approved daily/weekly maintenance.** This page summarises the owner's private handoff and maintenance evidence. It is a dated account of completed checks, not a live health dashboard. The original showcase publication did not run the automation; later owner-approved maintenance added and tested daily reporting while preserving weekly reporting.

## Completed checks

| Area | Recorded evidence | What it establishes |
| --- | --- | --- |
| Reporting logic | The 25 existing checks passed again, alongside 9 new daily/weekly checks. | Covered reporting, cadence selection, fixed feed separation, graph validity, and export-response scenarios passed. |
| Meta | Successful native API collection, with account timezone/currency checks and permission inspection. | Read access and the tested reporting window worked for the configured account. |
| HubSpot | Successful native contact-count collection. | The configured contact-read path worked; this is not sales or lead qualification evidence. |
| Google Sheets | Both six-row, 13-column feeds read back; 156 cells matched native execution results. | Daily and weekly exports wrote their intended independent tables. |
| Overview tabs | Weekly formulas and formats preserved; Daily formulas point to Daily; no formula errors. Native overviews reviewed. | The reviewed summaries retain their intended periods and presentation. |
| Data Studio | Separate Daily/Weekly pages reviewed in viewing mode; Daily reloaded; dates, totals, filter, layout, and owner-only sharing checked. | The reviewed pages read the correct feeds without exposing the report publicly. |
| Google production consent | Successful native export after approved production reconnection. | The accepted production authorisation worked with the existing scope. |
| Google renewal | Credential update observed during a successful later report execution, without manual reconnection or a separate credential write. | One automatic token renewal was observed. |
| Daily and weekly activation | Manual and native trigger-mode executions passed for each period; both temporary minute schedules removed. | Both paths worked, and the final published workflow uses daily 09:00 and Monday 09:00 schedules. |
| Preservation | Other workflow definitions, all credential identities, and unrelated credential metadata compared. The report credential renewed automatically. | Unrelated records remained unchanged; the writer's normal token refresh is distinguished from configuration changes. |

Earlier setup evidence includes inactive scheduling, Testing-mode OAuth, and incomplete provider connections. Those were intermediate stages, superseded by the later production and weekly-activation records. Test counts from different stages are not added together.

The 9 new cadence checks cover independent execution profiles, yesterday versus seven-day periods, Swiss daylight-saving dates, preservation of existing provider nodes and weekly scheduling, daily manual/clock routing, rejection of unknown reporting modes, valid workflow connections, unchanged credential references and disabled sources, and rejection of a successful export response for the wrong range or incomplete table dimensions.

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
| Regular scheduled recurrence | Both native clock paths passed controlled tests. The first regular daily and Monday runs had not occurred at this maintenance check. |
| Complete advertising pagination | Later pages are not collected. |
| Historical reporting | Daily and Latest are overwritten independently; neither stores a time series. |
| Cross-source attribution | No deduplication or mapping of ad conversions to customers or revenue. |
| Alerts | No configured email or messaging notification delivery. |
| Long-term reliability | No uninterrupted uptime, future token-renewal success, or continuous dashboard health guarantee. |
| Disaster recovery | Private recovery copies exist; a full reporting-specific restore drill is not claimed. |
| Commercial use | No multi-customer acceptance, public onboarding, or commercial service readiness claim. |

## Evidence kept privately

The handoff includes the README, original weekly activation verification, Google setup and production evidence, non-secret live profile, saved local test output, and source/dashboard checks. Daily/weekly maintenance adds its own execution verification, feed readback, dashboard checks, patch tooling, and native before/after snapshots. These records and the earlier recovery bundle remain private.

This repository publishes a readable summary rather than those raw records. Live identifiers, credential metadata, report values, and private links are intentionally omitted. Later maintenance should update this dated status only after inspecting the relevant current state and recording new evidence.
