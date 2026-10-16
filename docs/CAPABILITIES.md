# Capabilities and boundaries

[Back to the project](../README.md)

This guide describes the accepted personal configuration as recorded on 16 October 2026. A source adapter existing in the private workflow does not establish live account access or verified provider compatibility.

## Meta advertising results

The workflow reads advertising insights for the report's date range. Supported campaign fields include spend, impressions, inline link clicks, and a selected conversion action when explicitly configured. Campaign measurements feed validated source totals and derived ratios.

In the accepted setup, Meta is connected for read-only reporting and its account currency and timezone have been checked. A conversion action is intentionally unset, so conversions and CPA remain unavailable. Profile visits, clicks, or other engagement are not reclassified as leads.

Successful empty insights can establish no advertising activity for that window. They say nothing about activity outside the requested dates. Pagination, currency changes, and timezone differences affect whether totals can be treated as complete.

## HubSpot new contacts

The workflow reads the count of contacts created during the reporting period. It does not create or edit contacts, move deals, change lifecycle stages, or send messages.

The dashboard's contact scorecard is filtered to the HubSpot source. A contact count is a creation count, rather than a count of qualified leads, customers, sales, or attributed acquisitions. Those interpretations would require separately verified definitions and mappings.

## Google Sheets report

The owner-only spreadsheet contains:

| Tab | Purpose |
| --- | --- |
| Overview | A readable summary with formulas and context for reviewing the current report. |
| Latest | The dashboard data feed: a header and five source rows in `A1:M6`. |

The weekly workflow updates the existing Latest range. Repeated exports do not append duplicate rows. This also means Latest is replaced each time; no historical reporting archive is maintained in this table.

## Google Data Studio dashboard

The private dashboard reads the Latest range through its own authorised native Google Sheets connector. It includes a source table, reporting dates, available totals, explanatory notes, and a HubSpot-only contact scorecard. Missing metrics stay blank, and the table avoids a combined summary row that would mix unlike sources.

Owner-only sharing and the saved dashboard were checked in the browser, including after a reload. The n8n export does not continuously verify the dashboard or manage its connector. Data Studio caching can delay visible changes.

## Deferred source adapters

| Adapter | Intended read operation | What remains necessary |
| --- | --- | --- |
| GA4 | Website/app sessions, active users, key events, and available revenue. | A real property and data stream, approved read access, and a live collection check. |
| Google Ads | Campaign spend, impressions, clicks, conversions, and conversion value. | A real customer account, approved API access, OAuth access, and live validation. |
| Tag Manager | Container metadata and confirmation that the expected container is accessible. | A real website container, approved read access, and a live check. |

These sources are disabled and labelled unconnected in the accepted personal report. No placeholder account, property, stream, or container was created. Tag Manager container access would still not establish that tags are installed or that events reach an analytics destination.

## Actions outside this reporting flow

The accepted flow does not change advertising budgets, create campaigns, optimise bids, edit CRM records, qualify contacts, send outreach, or publish reports publicly. AI is disabled. An optional summary path exists privately, but enabling it would be a separate owner decision and validation step.

Commercial deployment and the owner's other automation groups are separate work. This repository describes only personal Advertising & Reporting.
