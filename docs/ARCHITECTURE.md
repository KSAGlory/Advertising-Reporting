# Architecture

[Back to the project](../README.md)

The private implementation uses a self-hosted n8n workflow as the coordinator. Provider adapters supply measurements, deterministic logic validates and summarises them, Google Sheets receives the latest source table, and Data Studio presents it through a separate connection.

## Responsibilities

| Layer | Responsibility |
| --- | --- |
| Scheduler | Start the published workflow on Monday at 09:00 Europe/Zurich. |
| Report context | Establish the owner profile, generation timestamp, date range, and report timezone. |
| Configuration checks | Require enabled sources, approved credentials, account identifiers, and valid configuration before collection. |
| Provider adapters | Issue bounded read requests and preserve source-specific meaning. |
| Validation | Check response shape, numeric metrics, currencies, timezones, and known incompleteness signals. |
| Report assembly | Produce source statuses, notes, deterministic totals, ratios, and the flat dashboard table. |
| Sheet export | Overwrite the existing Latest range and inspect the update response. |
| Dashboard | Read the private Sheet and display available measurements and source context. |

## Execution sequence

1. The clock trigger starts the published workflow.
2. Reporting logic calculates seven complete calendar days, excluding the current day.
3. Each source passes through a setup check. Disabled or unconfigured sources produce an explicit status without a provider request.
4. Enabled Meta and HubSpot adapters request the permitted measurements.
5. Responses are normalised and validated. Failures remain attached to their source instead of becoming fabricated metrics.
6. The report is assembled. The accepted path bypasses the optional AI summary because AI is off.
7. Google Sheets receives a header and five source rows in `Latest!A1:M6`.
8. The workflow records export status and its final report. Data Studio reads the Sheet independently through its own connector.

This sequence describes logical responsibilities; it is not a public workflow definition or a deployment recipe.

## Two timezone responsibilities

The trigger uses Europe/Zurich so the owner can expect a consistent Swiss wall-clock time. Source reporting uses the verified Meta account timezone recorded as EET, so date boundaries align with that account's daily results.

The period has an inclusive start date and end date for presentation. Timestamp filtering uses the start boundary through the next midnight after the last included day, with an exclusive upper bound. It is a calendar-day window, rather than an assumption that every day is exactly 24 hours long.

## Authentication boundaries

Meta, HubSpot, and the Google report writer use encrypted credentials managed by n8n. Account configuration and credential selection are separate: a saved account identifier does not grant permission to read it.

The report writer's Google OAuth application uses a separate Cloud project and is in production. Its `drive.file` scope is limited to app-authorised files rather than blanket access to the owner's Drive. Data Studio uses its own separately authorised native Sheets connector; the writer's access does not grant the dashboard's access.

No provider credentials, live account identifiers, private destination URLs, internal service addresses, or deployment configuration are included in this repository.

## Completion and visibility

There are distinct checks for provider collection, Sheet export, and dashboard display. A successful provider response does not by itself establish a successful export. A saved dashboard URL produces the workflow status `configured_link_only`; it is not evidence of dashboard availability.

The export checks the Sheets API update response. Earlier acceptance also read back cells and reviewed formulas and the dashboard. Those stronger acceptance checks are not claimed to run continuously on every schedule.

## Extending the system

Real GA4, Google Ads, or Tag Manager assets can be connected individually after owner approval. Each source needs its own credential/access check, valid account configuration, response validation, and live execution evidence. The same report structure can then describe it without presenting a configured adapter as an accepted connection.

Historical storage, full advertising pagination, or notification delivery would change the accepted behavior and require separate implementation and verification. None is supplied by this documentation repository.

## Template foundations

The private provenance record identifies two public n8n template foundations:

| Template reference | Recorded adaptation |
| --- | --- |
| [n8n workflow 8463](https://n8n.io/workflows/8463) | GA4 HTTP reporting node and period/reporting structure. |
| [n8n workflow 12124](https://n8n.io/workflows/12124) | Weekly trigger and source aggregation/report-table structure. |

The personal workflow adds fixed read-only provider requests, deterministic metric validation, explicit setup statuses, and the accepted private export configuration. Template provenance is not evidence that a deferred provider is connected. No template export or third-party source is redistributed through this showcase; the original projects retain their own terms.
