# Pre-Deployment Application-Security Review Checklist

A generic checklist for reviewing an application or significant change **before** it reaches production, so avoidable weaknesses are caught while they are cheapest to fix. Adapt the items to your environment; treat this as a starting point, not an exhaustive standard.

This supports the prevention side of the approach and aligns with the NIST Secure Software Development Framework (SP 800-218), which emphasizes integrating security across the lifecycle and addressing root causes so weaknesses do not recur.

## Before the review — intake

Gather enough context to make the review meaningful:

- [ ] What the application/service does and who uses it.
- [ ] The technologies and major components/dependencies involved.
- [ ] How users authenticate and how access is authorized.
- [ ] What data it handles, and whether any is sensitive or regulated.
- [ ] How it is exposed (internet-facing, internal, partner-facing).
- [ ] Its operational importance (map to your application inventory tier).
- [ ] The responsible team and point of contact.

## Authentication & authorization

- [ ] Authentication is handled by a vetted mechanism, not custom/ad-hoc.
- [ ] Authorization enforces least privilege; sensitive actions are properly gated.
- [ ] Administrative access is controlled and auditable.
- [ ] Session handling (tokens, expiry, revocation) is sound.

## Data protection

- [ ] Sensitive data is identified and classified.
- [ ] Data is encrypted in transit; sensitive data is encrypted at rest as appropriate.
- [ ] Secrets/credentials are managed securely (not hard-coded or exposed).
- [ ] Logging captures what's needed without logging sensitive data inappropriately.

## Common weakness classes

- [ ] Input handling defends against injection classes (e.g., SQL injection, cross-site scripting) — well-understood, preventable, and still common per CISA/FBI guidance.
- [ ] Output encoding and content handling are appropriate.
- [ ] Dependencies/components are current and free of known-vulnerable versions.
- [ ] Error handling does not leak sensitive detail.

## Exposure & configuration

- [ ] Attack surface is minimized (unused endpoints/features/ports closed).
- [ ] Secure defaults and hardened configuration are in place.
- [ ] External exposure is intentional and justified.

## Monitoring & response readiness

- [ ] Adequate logging/monitoring exists to detect and investigate issues.
- [ ] There is a clear owner for the application post-release.

## After the review — outcomes

- [ ] Findings recorded, each with a priority tier and owner (feed into `docs/01` and `docs/02`).
- [ ] Follow-up items tracked to completion (`docs/03`).
- [ ] Decisions and any accepted risks documented with rationale and a re-review date.

## Notes

- Keep the review a **conversation**, not just a form — the highest-value output is often the questions raised and the shared understanding created between security and the delivery team.
- Right-size the depth to the application's importance and exposure; a high-importance internet-facing service warrants more scrutiny than a low-risk internal tool.
