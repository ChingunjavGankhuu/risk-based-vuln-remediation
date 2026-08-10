# Risk-Based Vulnerability Remediation & Ownership

A practitioner approach for turning a stream of security findings into timely, accountable remediation — by connecting each vulnerability to the affected application, its operational importance, its true exposure and risk, and the team accountable for fixing it.

This is an adaptable approach, not a product or a tool. Every organization runs different technologies, scanners, ticketing systems, and risk tolerances, so nothing here prescribes a specific platform. What it offers is a repeatable decision structure that a security or development team can pick up and adapt to its own environment.

## The problem this addresses

Organizations rarely struggle to find vulnerabilities — scanners produce more findings than any team can act on at once. The harder, more persistent problem is deciding **which findings actually matter**, getting each one to **the team responsible for fixing it**, and **tracking it to completion**. When that connective work is missing, findings pile up unassigned, get routed to the wrong team, or are prioritized purely by a severity score that doesn't reflect real risk.

This approach is a practical way to close that gap in day-to-day work.

## Core Principles

**Exploitability over severity**. A CVSS score is an input, not a verdict. What matters is whether the weakness can actually be exploited in your environment — is it internet-facing, is there a public exploit, and is the vulnerable component genuinely in use and reachable? Findings that can't be reached are de-escalated, so effort goes where the real risk is.

**Every finding has an owner**. Remediation stalls when no one knows who's responsible. Each finding is connected to the specific team accountable for fixing it, with a defined path when ownership is unclear — because a finding no one owns doesn't get fixed.

**Context decides, automation carries**. The value is in the decision structure and risk judgement staying with people; the tools are interchangeable. Automation handles the repetitive parts: matching findings to owners, routing, and tracking.

In practice, that means answering five questions for every significant finding:

1. **What is it, is it real?** — understand and validate the finding; rule out false positives if possible.
2. **What does it affect?** — connect the finding to the specific application, service, or component.
3. **How much does that matter?** — weigh the affected asset's operational importance, its exposure, evidence of active exploitation, and data sensitivity.
4. **Who owns the fix?** — identify the accountable team or individual, with a defined path when ownership is unclear.
5. **Did it actually get fixed?** — assign, track, and confirm remediation or formal risk acceptance.

The approach can be applied at two points in the software lifecycle: before release, reviewing software for weaknesses (see docs/04), and in operation, finding and remediating vulnerabilities in running systems (see docs/01 and /02).

## Repository contents

| File | What it is |
|------|------------|
| [`01-prioritization-rubric.md`](01-prioritization-rubric.md) | Risk-based prioritization decision guide (adapt to your own risk factors and thresholds) |
| [`02-ownership-mapping.md`](02-ownership-mapping.md) | Method for connecting findings to accountable owners (adapt to your org structure) |
| [`03-remediation-workflow.md`](03-remediation-workflow.md) | Assigning, tracking, and closing findings (wire to your already-use tool) |
| [`04-pre-deployment-review-checklist.md`](04-pre-deployment-review-checklist.md) | A pre-release application-security review checklist (fold into your pre-deploy) |
| [`application-inventory-template.md`](application-inventory-template.md) | Minimal application-to-owner inventory |
| [`vulnerability-triage-record-template.md`](vulnerability-triage-record-template.md) | A record for a single triaged finding |

### Useful references

If you want to go deeper on the ideas behind risk-based prioritization, these public resources are worth knowing and being referenced:

- **CISA Known Exploited Vulnerabilities (KEV) Catalog** — a running list of vulnerabilities known to be exploited in the wild; a strong signal for prioritization. (https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
- **NIST Cybersecurity Framework 2.0** — asset inventory (ID.AM), risk assessment (ID.RA), and roles/accountability (GV.RR). (https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf)

(These are background references, not requirements — the approach works with whatever standards and tools your organization already follows.)

## Contributing

Issues and pull requests are welcome. If you adapt this approach in your organization and learn something worth sharing, contributions that improve the general method (without exposing any organization's internal specifics) are appreciated.

## License

Released under the MIT License — see [`LICENSE`](LICENSE). Use, adapt, and redistribute freely.

## Author

Chingunjav (CJ) Gankhuu — information security engineer working in application security and vulnerability management. This guidance is shared as an individual professional contribution to the field — not associated with or endorsed by any employer.
