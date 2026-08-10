# Application-to-Owner Inventory (Template)

The foundation of routing and prioritization: a current record of what applications/services exist, how important and exposed they are, and who is accountable. Keep it as simple as possible while still answering "who owns this and how much does it matter?"

| Application / Service | Owning Team | Point of Contact | Operational Importance (e.g., High/Med/Low) | Exposure (Internet / Internal / Partner) | Handles Sensitive Data (Y/N) | Notes |
|-----------------------|-------------|------------------|---------------------------------------------|------------------------------------------|------------------------------|-------|
| *Example App A* | *Team X* | *role/alias* | High | Internet | Y | |
| *Example App B* | *Team Y* | *role/alias* | Low | Internal | N | |

## Field notes

- **Operational importance** feeds the prioritization rubric (`docs/01`) — align the tiers you use here with the tiers there.
- **Exposure** and **sensitive data** are prioritization inputs; capturing them once here saves re-deciding per finding.
- **Point of contact** — prefer a role or team alias over an individual name so the record survives staff changes.
- Keep this current on a defined cadence; stale ownership is a leading cause of stalled remediation (see `docs/02`).

> Do not populate this template with any real, confidential, or organization-specific inventory when publishing it. It is a structure to adopt, not a place to store live data.
