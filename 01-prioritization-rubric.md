# Risk-Based Prioritization

Severity scores alone don't tell you how urgently *your* organization should act on a finding. A CVSS rating is an input, not a verdict. This is the decision logic I use to turn a finding into a priority — and, just as importantly, to *de-escalate* findings that look scary on paper but can't actually be exploited in your environment.

## The factors I weigh

- **Severity** — is the finding rated **High or Critical**? (I work in severity levels, not a specific numeric cutoff.)
- **Public exploit** — does a known public exploit or proof-of-concept (PoC) exist?
- **Exposure** — is the affected application or service **internet-facing**, or internal-only?
- **Exploitability in practice ("in use / reachable")** — this is the factor most teams skip, and it matters most. A finding is genuinely exploitable when *either*:
  - the specific conditions for exploitation are met — the vulnerable function, class, or code path is actually present and reachable in a way that could be exploited; **or**
  - no special conditions are required — the mere presence of the vulnerable component is enough, for example an outdated or known-vulnerable version of a package or library that carries the risk simply by being in use.

  If neither is true — the vulnerable code isn't present or reachable, and the component isn't in a vulnerable state — the finding **de-escalates**, even at High or Critical severity. A critical CVE that your environment cannot actually trigger is not an emergency.

## Priority tiers

### Immediate
Fix now. A finding is **Immediate** when it is **High or Critical severity**, **genuinely exploitable** (reachable or vulnerable-version-present), **internet-facing**, and a **public exploit exists**.

It is also **Immediate** when it is **High or Critical severity**, **genuinely exploitable**, and **internet-facing**, **even if no public exploit exists yet** — an exposed, exploitable, high-severity issue is urgent whether or not someone has published a PoC.

### High
**High or Critical severity**, **genuinely exploitable**, but **not internet-facing**. A public exploit is *not* required at this tier.

Internal-only does **not** mean safe. An insider, an attacker impersonating an employee, or a compromised workstation or account can reach and exploit an internal system. So a reachable High/Critical internal finding is still elevated — just below an internet-facing one.

### Medium
Findings **below High/Critical severity** — regardless of exposure, whether a public exploit exists, or whether the component is in use. These are handled on a planned basis.

### Low
None of the elevating factors are met. Backlog or formally accept.

## Quick reference

| Tier | Severity | Exploitable (reachable / vulnerable version)? | Internet-facing? | Public exploit? |
|------|----------|----------------------------------------------|------------------|-----------------|
| **Immediate** | High/Critical | Yes | Yes | Yes — *or* No (exposure + exploitability is enough) |
| **High** | High/Critical | Yes | No | Optional |
| **Medium** | Below High/Critical | Any | Any | Any |
| **Low** | — | No elevating factors | — | — |

## Why the "reachable / in use" factor matters so much

Most prioritization goes wrong by treating every High/Critical CVE as urgent. In practice, a large share of them aren't exploitable in *your* environment — the vulnerable code path isn't reachable, or the affected feature isn't used. Checking exploitability first lets you spend your limited remediation effort on the findings that can actually hurt you, and confidently de-prioritize the ones that can't. Conversely, don't let "it's just a dependency" fool you: an outdated, known-vulnerable library version can carry real risk by its mere presence, with no special condition required.

## Risk acceptance

Not everything must be fixed immediately. Lower-tier findings can be formally accepted with a documented rationale, any compensating controls, and a re-review date. Record these in the triage record (`templates/vulnerability-triage-record-template.md`).

## Adapting this

The tiers and factors reflect how I weigh risk; your environment may weigh them differently. Keep whatever rule you adopt written down and applied consistently, so prioritization is defensible and repeatable across reviewers.
