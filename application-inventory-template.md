# Application-to-Owner Inventory (Sample Template)

The foundation of routing and prioritization: a current record of what applications/services exist, how important and exposed they are, and who is accountable. Keep it as simple as possible while still answering "who owns this and how much does it matter?" Capturing operational importance, data sensitivity, and exposure once here saves re-deciding them for every finding.

| Application / Service | Repo / Codebase | Owning Team | Point of Contact | Operational Importance (High/Med/Low) | Exposure (Internet / Internal / Partner) | Handles Sensitive Data (Y/N) | Notes |
|-----------------------|------|-------------|------------------|---------------------------------------------|------------------------------------------|------------------------------|-------|
| *Example App A* | org/repo-a | *Team X* | *role/alias* | High | Internet | Y | |
| *Example App B* | org/repo-b | *Team Y* | *role/alias* | Low | Internal | N | |

## Field notes

- **Repository / codebase** — the code repository (or repositories) the application is built from. This is the identifier findings are often traced through: a vulnerability report names a component or repo, which maps here to the owning team. Populate it so findings can be routed by repository as well as by application name.
- **Point of contact** — prefer a role or team alias over an individual name so the record survives staff changes.
- **Operational importance** — how critical the application is to operations: the harm if it is disrupted or compromised (for example, a user-facing system many people depend on, or a core service others rely on). Refer to your org standard record or CMDB. The prioritization rubric uses this as an impact factor.
- **Data sensitivity** — whether the application handles sensitive data (PII, financial, health, or confidential). Where your organization has a data classification standard, use it to define what counts. The rubric uses this as an impact factor.
- **Exposure** — whether the application is internet-facing or internal-only. The rubric uses this as a likelihood factor. 

PS: Keep this current on a defined cadence; stale ownership is a leading cause of stalled remediation.

> Do not populate this template with any real, confidential, or organization-specific inventory when publishing it. It is a structure to adopt, not a place to store live data.
