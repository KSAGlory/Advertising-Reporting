# Data and metrics

[Back to the project](../README.md)

The report keeps each source's status and measurements together. A missing measurement, an authenticated empty response, and a collection error carry different meanings.

## Reporting window

The accepted report covers the previous seven complete days in the verified Meta account timezone, recorded as EET. The current day is excluded. The weekly Monday trigger uses Europe/Zurich independently.

For example, a Monday run normally reports the preceding Monday through Sunday in the report timezone. The row's period dates describe measurement coverage; `generated_at` describes when the report was created. Neither should be replaced by the dashboard's cache-refresh time.

## Source statuses

| Status | Meaning |
| --- | --- |
| `not_connected` | Collection is disabled or approved credentials have not been configured. |
| `needs_configuration` | Required account settings are missing or invalid, or known Meta access has expired. |
| `no_activity` | A successful supported response establishes inactivity for the requested window. |
| `ready` | Valid measurements are available from the requested source. |
| `partial` | Available results have a detected limitation, such as advertising pagination or GA4 thresholding. |
| `error` | Collection or validation failed; the report does not invent replacement totals. |

The overall report status is a summary. Individual source statuses and notes remain necessary for interpretation, especially while some integrations are deliberately deferred.

## Metric definitions

| Measurement | Definition and boundary |
| --- | --- |
| Spend | Reported advertising cost in the verified source currency. |
| Impressions | Provider-reported advertising impressions. |
| Clicks | Provider-specific clicks; Meta uses inline link clicks. |
| Conversions | The selected ad platform's definition; Meta requires an explicitly chosen action type. |
| New contacts | HubSpot contacts created during the reporting window; no automatic qualification or sales inference. |
| Sessions | A GA4 website/app measure; unavailable until a real GA4 property is connected. |
| GA4 key events and revenue | Separate website measures, not equivalents of ad conversions or CRM sales. |
| Tag Manager container metadata | Configuration access, not proof of tag installation or working tracking. |

The internal report can contain fields beyond the dashboard feed, including campaign rows and derived ratios. The 13-column export is a deliberately smaller source-level table.

## Calculations

| Ratio | Calculation |
| --- | --- |
| CTR (%) | Total clicks ÷ total impressions × 100. |
| CPC | Total spend ÷ total clicks. |
| CPA | Total spend ÷ total configured conversions. |

Ratios are rounded to four decimal places. A missing input or zero denominator produces an unavailable ratio. Campaign percentages are not averaged: the report sums the relevant measurements first and calculates the source ratio from those totals.

**Illustrative arithmetic, not account data:** 100 clicks from 10,000 impressions gives a 1% CTR. Spend of 50 with 100 clicks gives a CPC of 0.5 in the source currency. If no conversion action is configured, conversions and CPA remain unavailable even when clicks and spend are known.

Numeric validation rejects malformed, negative, non-finite, boolean, and whitespace-only metric values. Required missing metrics fail validation. Optional unavailable measurements retain their unavailable meaning.

## Currency, attribution, and completeness

Different currencies are not converted or added. Mixed currencies within a source fail validation. Meta's recorded account currency is checked against returned measurements, and timezone differences are surfaced. Google Ads and GA4 have their own response validation for account/property timezone consistency.

Google Ads and Meta conversion totals remain separate because their attribution rules can overlap. GA4 events and HubSpot contacts are also separate. The report makes no cross-platform deduplication, revenue attribution, or return-on-ad-spend claim.

In the accepted Meta/HubSpot configuration, combined advertising spend is unavailable because Google Ads is not connected. Detected partial advertising results are excluded from that combined overview. This showcase does not claim cross-source aggregation has passed live acceptance with two advertising providers.

## Dashboard feed

The Sheet range `Latest!A1:M6` contains one header row followed by five rows: GA4, Google Ads, Meta Ads, HubSpot, and Tag Manager. Unconnected sources keep their row and visible status.

| Column | Field | Meaning |
| --- | --- | --- |
| A | `profile_id` | Non-secret reporting profile key. |
| B | `period_start` | First included calendar date. |
| C | `period_end` | Last included calendar date. |
| D | `source` | Source key identifying the adapter. |
| E | `status` | Source collection/validation status. |
| F | `currency` | Known source currency, otherwise blank. |
| G | `spend` | Available advertising spend. |
| H | `impressions` | Available advertising impressions. |
| I | `clicks` | Available provider-specific clicks. |
| J | `conversions` | Available configured platform conversions. |
| K | `sessions` | Available GA4 sessions. |
| L | `new_contacts` | Available HubSpot new-contact count. |
| M | `generated_at` | Report generation timestamp. |

Unavailable exported measurements are blank. Verified no-activity measurements can be zero. Those representations are intentional and should remain distinct in dashboard formatting.

## Storage limits

Exports overwrite the same range. Re-running avoids appended duplicate rows but replaces the previous window. Latest is not a historical archive, and the dashboard cannot recover a long-term trend from it alone.

Advertising pagination is detected and labelled; subsequent pages are not fetched yet. GA4 thresholding, sampling, or data-loss indicators are handled as partial in local validation tests, but no GA4 account is currently connected. A future high-volume source needs a separate completeness review.
