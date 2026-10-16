# Frequently asked questions

[Back to the project](../README.md)

## Is the automation finished?

Yes, for the accepted personal Meta Ads and HubSpot reporting configuration recorded on 16 October 2026. Private Sheet export, the dashboard, production Google access, and weekly activation passed their recorded checks. The three deferred Google sources remain explicitly unconnected.

## Can I install it from this repository?

No. This is a documentation showcase of a private implementation. It contains no runnable workflow, application source, deployment package, public report, or installer.

## Does it manage advertising campaigns?

It reads reporting data. It does not create campaigns, change budgets or bids, edit CRM records, or send outreach. Its routine write destination is the owner's report Sheet.

## Does it need AI?

AI is disabled in the accepted configuration. Metric validation and calculations are deterministic. An optional private summary path is outside the accepted active reporting path.

## Why are some values blank?

A blank means the metric is unavailable or not applicable. A disconnected provider, unset conversion action, or failed collection is not evidence of zero activity. Verified inactivity can produce actual zeros for supported measurements.

## Are new contacts leads or customers?

The report counts contacts created in HubSpot. Qualification, customer status, sales, and attributed revenue require separate definitions and evidence.

## Why are scheduling and reporting in different timezones?

Scheduling follows Swiss time for the owner's weekly routine. Measurement dates follow the verified Meta account timezone so daily totals align with that source. The current incomplete day is excluded.

## Does it store history?

The dashboard feed stores only the latest window. `Latest!A1:M6` is overwritten on each export. Long-term charts would require a separate history design.

## Does a successful run guarantee the dashboard is current?

No. Collection, export, and dashboard display are separate stages. Data Studio uses its own connector and may cache results. A successful Sheet export is not continuous verification of the dashboard.

## Does my computer have to stay open?

The scheduled workflow runs on the self-hosted server. The owner's computer and browser do not have to stay open. Server availability, network access, provider permission, and API availability still matter.

## Will it notify the owner when access expires?

Meta expiry warnings appear in the report within seven days of the recorded expiry. Expired access blocks collection. No email or messaging alert is configured, so the owner must review the report or request maintenance.

## Is the report public?

No. The Sheet and dashboard were checked as owner-only. Public Google OAuth app-information pages are separate from the private report. This showcase does not disclose private report links or real report values.

## Are all five data sources connected?

No. Meta and HubSpot are connected. GA4, Google Ads, and Tag Manager await actual owner assets and approved access. Their adapter logic and local tests do not establish live connections.

## Is it a commercial service or part of another assistant?

It is the owner's personal Advertising & Reporting workflow, the first personal marketing automation group. Other groups and other automations are outside this showcase. Commercial copies are deferred.

## Is it free to run?

The repository does not offer a public service or pricing plan. Hosting and provider account costs are separate from viewing this documentation. No ongoing cost or provider-usage allowance is promised here.

## Where can I ask a question?

Use [GitHub Issues](https://github.com/KSAGlory/Advertising-Reporting/issues) for project questions or documentation corrections. Follow [SUPPORT.md](../SUPPORT.md) and keep private access information out of public posts.
