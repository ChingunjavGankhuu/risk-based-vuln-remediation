# Remediation Workflow

A repeatable path from a validated, prioritized, owned finding to a confirmed fix or a formal risk acceptance. This is intentionally tool-agnostic — map each step onto whatever scanning and ticketing systems you already run.

## The loop

```
Detect → Validate → Attribute → Prioritize → Assign → Track → Confirm → (Close | Accept)
```

1. **Detect.** A finding arrives from any source — a scanner, a runtime analysis tool, a pre-deployment review, a report.
2. **Validate.** Confirm it is real and not a false positive; capture enough detail to act.
3. **Attribute.** Connect it to the affected application/component and its owner (`docs/02`).
4. **Prioritize.** Assign a priority tier and target window (`docs/01`).
5. **Assign.** Create a work item for the accountable owner, carrying the context and the "why."
6. **Track.** Keep the item visible and monitored until it moves; make status legible to owners and leadership.
7. **Confirm.** Verify the fix actually resolves the finding (re-test / re-scan where possible).
8. **Close or Accept.** Close on confirmed remediation, or formally accept the risk with rationale, compensating controls, and a re-review date.

## What "good" looks like

- **Every open finding has a named owner and a target date.** No ownerless, dateless items.
- **Priority is explained, not just asserted.** The owner can see *why* something is P1.
- **Status is shared.** Owners, security, and leadership work from one view of what's open, overdue, and closed.
- **Closure is verified, not assumed.** A finding is closed when it's confirmed fixed, not when someone says they fixed it.
- **Measurement drives improvement.** Track a small set of meaningful measures over time (see below).

## Measures worth tracking

Keep the set small and decision-relevant. Examples:
- Open findings by priority tier and by age.
- Time-to-remediate against target windows, by tier.
- Overdue findings (past target) by owning team.
- Coverage — proportion of applications with known ownership and active scanning.
- Recurrence — the same class of weakness reappearing (a signal to fix root causes, not just instances).

## The role of automation

Automate the mechanical, repeatable parts — attributing findings to owners, creating and updating work items, preserving risk context, flagging overdue items, and producing status views. Keep validation, prioritization judgment, and risk acceptance with qualified people. Automation should give decision-makers more complete and timely information, not make the risk decisions for them.

## Integrating with existing systems

You almost certainly already have a scanner and a ticketing system. The workflow above does not replace them — it defines the *decisions and hand-offs* that run on top of them. Wire detection sources to create work items, and make the priority tier and owner explicit fields so they can be filtered, tracked, and measured.
