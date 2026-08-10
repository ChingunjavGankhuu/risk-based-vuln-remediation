# Risk-Based Prioritization

Severity scores alone don't tell you how urgently your org should act on a finding. A CVSS rating is an input, not a verdict. This reflects the decision logic I have developed through professional practice for translating vulnerability findings into remediation priority — and, just as importantly, for de-escalating findings that look alarming on paper but can't actually be exploited in your environment.

## The factors I weigh

- **Severity** — is the finding rated **High or Critical**? (CVSS 7.0 - 10.0)
- **Exposure** — is the affected application or service **internet-facing**, or **internal-only**?
- **Exploitability in practice ("in use / reachable")** — this is the factor most teams skip, and it matters most. A finding can be exploitable when *either*:
  - the specific conditions for exploitation are met — the vulnerable function, class, or code path is actually present and reachable in a way that could be exploited; **or**
  - no special conditions are required — the mere presence of the vulnerable component is enough, for example an outdated or known-vulnerable version of a package or library that         carries the risk simply by being in use.
- **Public exploit** — does a known public exploit or proof-of-concept (PoC) exist?

  If neither is true — the vulnerable code isn't present or reachable, and the component isn't in a vulnerable state — the finding **de-escalates**, even at High or Critical severity. A critical CVE that your environment cannot actually trigger is not an emergency.

## Why the "reachable / in use" factor matters so much

A vulnerability can look severe because of its score, but if an attacker can't actually reach or use it in your systems, this approach treats it as lower priority — so effort goes to the findings that pose real risk. Most prioritization goes wrong by treating every High/Critical CVE as urgent, when some of them aren't exploitable in your environment — the vulnerable code path isn't reachable, or the affected feature isn't used. Conversely, don't let "it's just a dependency" fool you: an outdated, known-vulnerable library version can carry real risk by its mere presence, with no special condition required.

## Impact modifier — Data sensitivity

Consider what the affected application or service handles: does it process sensitive data — such as personally identifiable information (PII), financial, health, or confidential business data? A finding on an application that handles sensitive data warrants escalation, because successful exploitation causes greater harm. A finding on an application that handles little or no sensitive data may be de-escalated. Where your organization has a data classification standard, use it to define what counts as sensitive. Data sensitivity adjusts priority up or down; it does not replace the exploitability assessment.

## Tiers

### Immediate
Fix now. A finding is **Immediate** when it is **High or Critical severity**, **exploitable** (reachable or vulnerable-version-present), **internet-facing**, and a **public exploit exists**.

It is also **Immediate** when it is **High or Critical severity**, **exploitable**, and **internet-facing**, **even if no public exploit exists yet** — an exposed, exploitable, high-severity issue is urgent whether or not someone has published a PoC.

### High
Needs quick attention. A finding is High when it's **High or Critical severity**, **exploitable**, but **not internet-facing**. A public exploit is not required at this tier.

Internal-only does **not** mean safe. An insider, an attacker impersonating an employee, or a compromised workstation or account can reach and exploit an internal system. So a reachable High/Critical internal finding is still elevated — just below an internet-facing one.

### Medium
Findings **Medium severity** — regardless of exposure, whether a public exploit exists, or whether the component is in use. These are handled on a planned basis.

### Low
Low severity findings or higher-severity findings where no elevating factors are met. Backlog (address on routine basis) or formally accept.

## Quick reference

| Tiers | Severity | Exploitable (reachable / vulnerable version) | Exposure | Public Exploit (PoC) |
|------|----------|----------------------------------------------|------------------|-----------------|
| **Immediate** | High/Critical | Yes | Yes | Yes or No (exposure + exploitability is enough) |
| **High** | High/Critical | Yes | No | Any |
| **Medium** | Medium | Any | Any | Any |
| **Low** | Low | - | Any | — |


## Risk acceptance

Not everything must be fixed immediately. Lower-tier findings can be formally accepted with a documented rationale, any compensating controls, and a re-review date. You can record these by using the template [`vulnerability-triage-record-template.md`](vulnerability-triage-record-template.md).

## Adapting this

The tiers and factors reflect how I weigh risk; your environment may weigh them differently. Keep whatever rule you adopt written down and applied consistently, so prioritization is defensible and repeatable across reviewers.
