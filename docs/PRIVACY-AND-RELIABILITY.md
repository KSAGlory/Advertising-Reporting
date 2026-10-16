# Privacy and reliability

[Back to the project](../README.md)

The accepted deployment is personal and owner-only. This public showcase explains its behavior without exposing live account settings, destinations, credential references, report data, or recovery files.

## Access and data flow

| Connection | Accepted access boundary |
| --- | --- |
| Meta | Advertising reads through a dedicated credential restricted to the provider's API host. Verified scopes included `ads_read` and the automatically included `public_profile`; no `ads_management` scope. |
| HubSpot | Contact reads through a dedicated credential restricted to the HubSpot API host and `crm.objects.contacts.read`. |
| Google report writer | Production OAuth with `drive.file` access for app-authorised report files. |
| Data Studio | Separately authorised native Google Sheets connector and owner-only dashboard sharing. |

Credentials are encrypted in n8n. Encryption does not remove the need to protect server access, execution history, backups, and provider accounts. Provider services receive the data necessary for their operations; self-hosting does not make the entire reporting path local.

The private Sheet and dashboard were checked as restricted to their owner. The public app-information pages required for Google OAuth are separate from the private report. They do not publish the report or grant access to it.

## Metric failure behavior

A source authentication failure or malformed response becomes a visible error, rather than a substitute zero. Missing setup stays visibly unconnected or in need of configuration. The reporting logic avoids forwarding detailed provider errors into the human-readable report, while private node output remains the place for technical investigation.

Successful empty activity and unavailable data remain distinct. Detected advertising pagination is partial. Invalid required metrics fail validation. Different attribution definitions are preserved instead of being merged into a single sales figure.

## Credential lifecycle

Meta access has a recorded expiry. The report warns within seven days of that expiry. Once the recorded access is expired or its expiry is invalid, the configuration check prevents a provider request and reports `needs_configuration`.

Meta renewal is a maintenance task; automatic renewal is not implemented. The account-specific expiry date is kept in the private maintenance record.

Google OAuth is in production. Reconnection with the existing `drive.file` scope passed, followed by an observed automatic token renewal during a successful native report execution without manual reconnection. One successful renewal is evidence for that event; permissions can still be revoked and future refreshes can fail.

## Scheduling and owner control

The native n8n Publish/Unpublish control enables or disables automatic reporting. The accepted schedule is Monday at 09:00 Europe/Zurich. It runs on the existing server and does not require the owner's computer, Codex, or browser tabs to remain open.

The server, scheduler, network, provider credentials, and relevant APIs still need to be available. No service-level availability or automatic incident-recovery guarantee is claimed.

Warnings and source failures are visible in the report. No email or messaging notification is configured. There is no separate public status service or background monitor supplied by this repository.

## Maintenance and recovery

The private maintenance process is to inspect current state, back up the owned workflow, make a narrow authorised change, verify actual executions and destination results, then update the local handoff evidence. Unrelated workflows, credentials, and infrastructure are outside scope.

Private recovery material includes workflow snapshots and a recovery bundle. A separate portable workflow copy is deliberately inactive and credential-free; it is not a replacement to import over the live working workflow. None of those files is distributed here.

Preserved files support recovery planning. This reporting showcase does not claim a separately completed full disaster-recovery restore drill.

## Public disclosure boundary

The public repository contains explanatory Markdown, a conceptual Mermaid diagram, and repository presentation files. It omits:

- Source code, workflow exports, private setup scripts, and deployment instructions.
- Passwords, tokens, client secrets, credentials, and credential identifiers.
- Account, portal, customer, property, container, Sheet, dashboard, and live workflow identifiers.
- Actual report values, contact records, private report links, logs, and unredacted screenshots.
- Backup archives, native workflow snapshots, server addresses, and internal topology.

Report a suspected exposure privately as described in [SECURITY.md](../SECURITY.md).
