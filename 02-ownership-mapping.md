# Connecting Findings to Accountable Owners

A finding that no one owns doesn't get fixed. In my experience, the single biggest reason remediation stalls isn't technical difficulty — it's that the finding never reaches the person accountable for it, or reaches the wrong one. Reliable ownership information is the foundation that makes prioritization and remediation actually work.

## How to connect a finding to its owner

1. **Read what the finding gives you.** Detection tools — whether they use an agent inside your systems or are fed your system, application, and host data — surface a finding with details. The title and affected-asset fields usually contain identifying information: an application or service name, a repository, a host.

2. **Extract the identifier.** Parse or pull that identifying information out of the finding.

3. **Look it up in your inventory.** Take the identifier to your inventory of applications and owners, search for the match, and get the responsible team and point of contact. Many organizations maintain this in a configuration management database (CMDB) that lists applications and their owners; ideally you have one.

4. **Route it to the owner** with the context they need — what the finding is, its priority and why, and what's expected.

## When ownership is unknown

Not every finding maps cleanly, and not every organization has a complete inventory. When ownership isn't clear:

- Escalate — ask your manager or team lead.
- Investigate — look for the closest match, or find someone who can point you to whoever owns the affected system.
- Follow the chain — often the fastest path is one person who knows who *actually* owns it.

Define a default holder so nothing sits ownerless while you track down the real owner.

## Keeping ownership current

Ownership drifts as teams reorganize and applications are retired or handed off. Ways I keep it usable:

- Reach out to the previous owner when a mapping is stale.
- Refer to a maintained individual team-leadership or team-directory documentations when the inventory is incomplete.
- Where a CMDB exists, keep it as the source of truth and refresh (document) it on a defined cadence.

Be honest that this is often a known pain point — inventories are rarely perfect, and staleness is a constant.

## Automating the process with AI

Mapping a finding to its owner by hand is repetitive and involves juggling several sources at once — the finding's details, the code repositories, team membership, and a team directory. It's exactly the kind of many-tabs, error-prone lookup worth automating.

The main approach I developed to solve the ownership problem:

- create an agentic workspace that maps ownership to each vulnerability for you
- connect your ownership sources (such as a CMDB, application inventory, and team directory) to an AI agent approved by your organization
- connect your scanning tools to the agent so it has the vulnerability details
- have the agent resolve each finding to the affected component's owning team and point of contact
- keep the judgment (validation, prioritization, resolving disputes) with people, and let automation handle the mechanical matching and routing

*(The specific integrations, tools, and automation methods will depend on your environment. Adopt it as a general approach.)*

## Common failure modes to design against

- **Orphaned findings** — nothing maps to vulnerability.
- **Stale ownership** — the mapped team no longer owns the asset. 
- **Shared components** — a vulnerable shared library affects many application (who owns the fix).
- **Ambiguous boundaries** — two teams each think the other owns it.
