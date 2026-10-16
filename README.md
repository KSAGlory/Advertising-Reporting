<h1 align="center">Advertising &amp; Reporting</h1>

<p align="center">A private weekly reporting toolkit for advertising results and new-contact counts.</p>
<p align="center"><strong>Verified metrics. Visible connection status. One private report.</strong></p>

Advertising & Reporting brings Meta advertising results and HubSpot new-contact counts into a private Google Sheet and Google Data Studio dashboard. A scheduled n8n workflow collects the last seven complete days, checks the responses, and updates the same report table each week.

The purpose is to make a personal marketing review easier: see what happened, understand which sources are connected, and distinguish measured inactivity from missing information.

> **Status — 16 October 2026:** Complete and active for the accepted personal configuration: Meta Ads, HubSpot, private Google Sheets export, and a private Data Studio dashboard. Weekly scheduling and a clock-triggered execution passed verification. GA4, Google Ads, and Google Tag Manager await real owner assets and approved access. AI is disabled. This repository is a **public showcase of a private implementation**; source code, workflow exports, account data, and recovery material remain private.

## What it does

| Capability | What it gives the owner |
| --- | --- |
| **Weekly reporting** | A scheduled refresh every Monday at 09:00 Europe/Zurich. |
| **Meta Ads results** | Available campaign spend, impressions, inline link clicks, and calculated ratios. |
| **HubSpot contact counts** | Contacts created during the reporting window, clearly labelled as contacts. |
| **Connection status** | A visible distinction between connected, unconfigured, inactive, partial, and failed sources. |
| **Private Google Sheet** | A readable Overview tab and a stable Latest data table for the dashboard. |
| **Private dashboard** | A source table and a HubSpot contact scorecard, restricted to the owner. |
| **Deterministic calculations** | Metric validation and arithmetic performed by reporting logic, with AI off. |
| **Access-expiry handling** | A report warning near Meta expiry and blocked collection after expiry. |

Provider collection is read-only. The workflow writes its report to Google Sheets; it does not change campaigns, budgets, CRM records, or outreach.

## How it works

```mermaid
flowchart LR
    Schedule[Monday 09:00 Swiss time] --> Workflow[n8n reporting workflow]
    Workflow --> Checks[Check source configuration]
    Checks --> Meta[Read Meta advertising results]
    Checks --> HubSpot[Read HubSpot new-contact count]
    Checks -.-> Pending[GA4 / Google Ads / GTM: deferred]
    Meta --> Validate[Validate metrics and source status]
    HubSpot --> Validate
    Pending -.-> Validate
    Validate --> Report[Build report and source table]
    Report --> Sheet[Private Google Sheet]
    Sheet --> Dashboard[Private Data Studio dashboard]
    Dashboard --> Owner[Owner reviews results]
```

Solid paths describe the accepted reporting configuration. Dotted paths describe deferred integrations and their visible setup status, with no provider collection enabled for them.

The reporting period follows the verified Meta account timezone, recorded as **EET**. The weekly trigger follows **Europe/Zurich** separately. The report excludes the current, incomplete day. Read the [architecture](docs/ARCHITECTURE.md) and [data and metrics guide](docs/DATA-AND-METRICS.md) for the details.

## Connected now, deferred for later

| Source or destination | Verified configuration |
| --- | --- |
| Meta Ads | Connected and tested for reporting. Conversion action intentionally unset until a real goal is chosen. |
| HubSpot | Connected and tested with contact-read access. New contacts are not assumed to be leads or customers. |
| Google Sheets | Private owner-only report; repeat exports overwrite the same Latest range. |
| Google Data Studio | Separately authorised Sheets connector; dashboard and access checked in the browser. |
| Google Analytics 4 | Deferred: no real website/app property is available yet. |
| Google Ads | Deferred: no real Google Ads customer ID is available yet. |
| Google Tag Manager | Deferred: no real website container is available yet. |
| AI summary | Disabled; no AI summary is part of the accepted reporting path. |

## Reporting principles

- **Zero needs evidence.** A successful empty advertising response can establish inactivity; an unavailable connection cannot.
- **Missing metrics stay blank.** Unconfigured conversions and unsupported metrics are not manufactured.
- **Contacts keep their meaning.** Contact creation is separate from lead qualification, sales, and revenue.
- **Ratios use totals.** CTR, CPC, and CPA are calculated from validated summed metrics, rather than averages of campaign percentages.
- **Incomplete data stays visible.** Detected advertising pagination is labelled partial; later pages are not collected yet.
- **Attribution stays separate.** Platform conversions, website key events, and CRM outcomes are not added together as equivalent results.

## What has been verified

The private handoff records **25 passing local tests**, successful live Meta and HubSpot reads, repeated Google Sheets exports with cell readback, and a browser review of the saved dashboard. Google OAuth production reconnection and one automatic token renewal passed. A native clock-triggered n8n execution reached the final report and updated the Sheet; its temporary test schedule was removed before the final Monday schedule was published.

Preservation checks recorded that unrelated workflow definitions and credential metadata remained unchanged. These are dated acceptance results, not continuous service monitoring. No new provider execution was performed to publish this showcase. See [verification](docs/VERIFICATION.md) for the evidence scope and limits.

## Practical boundaries

The Latest worksheet stores **one reporting window**, with one header and five source rows. Each export overwrites `Latest!A1:M6`; historical time series are not stored there. Data Studio can cache results, so its displayed refresh time may differ from the automation's execution time.

Meta access requires renewal. Warnings appear in the report within seven days of its recorded expiry; expired access blocks collection. There is no configured email or messaging alert. The self-hosted server and provider access must remain available for scheduled reporting to work.

This is a single-owner personal setup. Commercial copies, other marketing automation groups, automatic campaign optimisation, and customer outreach are outside the accepted scope.

## Explore the project

| Guide | Contents |
| --- | --- |
| [Capabilities](docs/CAPABILITIES.md) | Connected reporting, deferred source support, destinations, and action boundaries. |
| [Architecture](docs/ARCHITECTURE.md) | Scheduling, configuration checks, collection, validation, export, and dashboard separation. |
| [Data and metrics](docs/DATA-AND-METRICS.md) | Reporting windows, source statuses, metric definitions, formulas, and the 13-column feed. |
| [Privacy and reliability](docs/PRIVACY-AND-RELIABILITY.md) | Access scopes, private data, renewal, failure handling, and maintenance controls. |
| [Verification](docs/VERIFICATION.md) | Local tests, live checks, dated acceptance, and remaining evidence gaps. |
| [Roadmap](docs/ROADMAP.md) | Conditions for connecting real Google assets and possible future improvements. |
| [FAQ](docs/FAQ.md) | Availability, ownership, schedules, history, AI, and common questions. |

## Availability and feedback

This repository offers project information. It does not offer a public dashboard, runnable workflow, hosted reporting service, installation package, or download. The private implementation and report destinations are not accessible through this showcase.

Project questions and documentation corrections are welcome through [GitHub Issues](https://github.com/KSAGlory/Advertising-Reporting/issues). Read [SUPPORT.md](SUPPORT.md) before sharing information and [SECURITY.md](SECURITY.md) for private exposure reports.

## Author and Community

- Author: **KSAGlory**
- Community: [discord.gg/ksahub](https://discord.gg/ksahub)

## License

The implementation remains private and proprietary. No application, source-code, or workflow license is offered through this repository. See [COPYRIGHT.md](COPYRIGHT.md) for the showcase materials.

Referenced platforms, products, and third-party projects retain their respective rights and terms. This is an independent project and does not imply their endorsement.

Copyright © 2026 KSAGlory. All rights reserved.
