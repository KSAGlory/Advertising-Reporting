# Roadmap

[Back to the project](../README.md)

The accepted Meta/HubSpot configuration is complete and scheduled. The work below describes conditions for later additions, not an announced release schedule or enabled functionality.

## Maintain the accepted configuration

| Area | Maintenance objective |
| --- | --- |
| Weekly operation | Review real execution and export results when maintenance is requested. |
| Meta access | Renew before the privately recorded expiry and verify a successful read afterward. |
| Google access | Investigate renewal or connector failures if they occur; retain approved scope. |
| Reporting evidence | Keep the private handoff current after authorised changes. |
| Isolation | Preserve unrelated workflows, credentials, and infrastructure. |

## Connect real Google assets when available

| Integration | Prerequisite | Acceptance needed |
| --- | --- | --- |
| GA4 | A real website/app property and data stream, plus approved read access. | Collect actual metrics, verify period/timezone interpretation, and check visible source status. |
| Google Ads | A real customer ID and approved API/OAuth access. | Verify account metadata, real campaign responses, currency, dates, and incomplete-data behavior. |
| Google Tag Manager | A real container for the owner's website and approved read access. | Verify the expected container; test website installation and event delivery separately if those claims are needed. |

No placeholder assets should be created to make an unconnected integration appear complete. Access and setup changes require the owner's real assets and approval.

## Possible future improvements

- Collect subsequent advertising pages with bounded requests and completeness checks.
- Add historical storage with explicit retention and rerun behavior.
- Define and verify a real Meta conversion action before reporting conversion totals or CPA.
- Add separately scoped notification delivery if the owner requests it.
- Evaluate the optional AI summary only with an explicit owner decision and validation of its data handling and output.

These are options, not commitments. Contact-to-lead qualification, deals/revenue mapping, and commercial copies are separate future scope. No public workflow package or hosted service is announced.
