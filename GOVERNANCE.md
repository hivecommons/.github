# Hive Commons Project Governance

This document describes how the Hive Commons project ("Hive") is governed.
Hive is an AI-agent fleet orchestration system: a hub coordinating hosted
spokes that run coding-agent swarms against GitHub repositories.

This governance is deliberately sized for a small project. Where a rule
depends on the number of maintainers, the rule states how it applies today
(1–3 maintainers) and how it scales as the maintainer body grows.

## Values

- **Openness.** Design, decisions, and roadmaps happen in public — in
  issues, pull requests, and public documents in the project repositories.
- **Human accountability.** Hive's own AI agents contribute code to the
  project. Agents are tooling. Every decision, every merge, and every
  release is the responsibility of a named human.
- **Vendor neutrality.** No single company controls the project (see
  "Vendor Neutrality" below).
- **Earned authority.** Roles are earned through sustained, public
  contribution, per the contributor ladder in [MAINTAINERS.md](MAINTAINERS.md).

## Maintainer Committee

The project is governed by its Maintainers, acting collectively as the
**Maintainer Committee** (the term used by the project's existing
governance record). There are no other governing bodies; if the project
grows to need subproject leads or a steering committee, this document will
be amended first.

The current Maintainers are listed in [MAINTAINERS.md](MAINTAINERS.md),
which also defines how Maintainers are added, removed, and retired
(emeritus).

### Authoritative records and the OWNERS file

Three records describe who the Maintainers are, and they **must agree**:

1. [MAINTAINERS.md](MAINTAINERS.md) in this repository,
2. the root `OWNERS` file (reviewers/approvers used by CI and tooling),
3. while the project lives in the KubeStellar org, the upstream
   Maintainer Committee table in
   [kubestellar/kubestellar GOVERNANCE-HIVE.md](https://github.com/kubestellar/kubestellar/blob/main/GOVERNANCE-HIVE.md),
   which is the authoritative record.

Any drift between these files is a governance bug: it is fixed by PR as
soon as discovered and disclosed in CNCF due-diligence materials. Every
Maintainer lifecycle change is made as a single PR (or coordinated PRs)
updating all applicable records together.

**Migration note.** If the project moves to a neutral org (working name
`hivecommons`), the content of GOVERNANCE-HIVE.md migrates into this
repository, this document and MAINTAINERS.md become the sole
authoritative records, and the upstream pointer — including the
KubeStellar Steering Committee's role in maintainer removal — is retired
in the same change.

Maintainer Committee responsibilities:

- Set and publish the technical direction and roadmap.
- Approve and merge changes to project repositories.
- Cut releases and manage release channels (stable / candidate / edge).
- Enforce the [Code of Conduct](CODE_OF_CONDUCT.md).
- Operate the project's own AI agents and answer for their output
  (see "AI Agents and Automation" below).
- Steward project assets (GitHub org, domains, artifact registries,
  signing keys) on behalf of the community, not any employer.

## Decision Making

### Lazy consensus (the default)

Most decisions are made by **lazy consensus**: a proposal (normally a pull
request or issue) is adopted if no Maintainer objects within **72 hours**
for routine changes, or **7 calendar days** for significant changes
(new features, deprecations, dependency or process changes). Silence is
consent. Any Maintainer may object and convert the decision to a vote.

Routine code review and merge follows the rules in
[CONTRIBUTING.md](CONTRIBUTING.md) and does not require a waiting period
beyond review itself.

### Maintainer lifecycle decisions

Consistent with existing practice, **adding a Maintainer** (or Reviewer)
is not a formal vote: an existing Maintainer nominates, the Committee
confirms by **lazy consensus (7 days)**, and the change lands as a PR
updating all the maintainer records listed above (MAINTAINERS.md, OWNERS,
and — while it remains authoritative — GOVERNANCE-HIVE.md). Ladder
advancement requests are reviewed by the Committee at least **monthly**.
Removal for cause is a supermajority vote (below).

### Votes

When lazy consensus fails, or for the decisions listed below, the
Maintainer Committee votes. Votes are held in public (issue or PR comment
thread) unless the subject is a security embargo or a Code of Conduct
matter, and remain open for at least **7 calendar days** or until the
outcome is mathematically settled.

- **Simple majority** of all current Maintainers: technical disputes,
  release/branch policy, adopting or archiving a repository in the org.
- **Two-thirds (2/3) supermajority** of all current Maintainers:
  - amendments to this governance document,
  - removing a Maintainer for cause,
  - breaking changes to the hub↔spoke protocol or other published
    compatibility guarantees,
  - license changes,
  - Code of Conduct enforcement decisions against a Maintainer
    (the subject does not vote).

With today's 3-member Committee, a 2/3 supermajority means 2 of 3, and
removal for cause means both of the other two Maintainers. Supermajority
decisions are preceded by a community comment period of at least
**one week**, matching existing practice, unless urgency (e.g. an active
security incident) requires otherwise — in which case the rationale is
published afterward. **Contingency:** if the Committee ever falls below
3 members, supermajority items additionally require a **14-day** public
comment period until the Committee is back to 3 or more.

**Employer cap.** No single employer may control a majority of Maintainer
votes; if one employer's Maintainers ever exceed half of the Committee,
their collective vote is proportionally reduced to half. This binds
immediately: the current Committee spans three distinct affiliations
(IBM, Universal Blue, independent), which satisfies the cap, and future
maintainer additions are evaluated against it.

## AI Agents and Automation

Hive develops AI-agent orchestration, and the project uses its own agents
("dogfooding") to author pull requests via the **hive-bot** GitHub App.
Agent contributions are a feature of the project, and they are governed
explicitly:

1. **Agents are tooling, not members.** An AI agent, bot account, or
   GitHub App cannot hold any role on the contributor ladder, cannot be a
   Maintainer, cannot vote, cannot sponsor a promotion, and its activity
   does not count toward any person's promotion criteria.
2. **Every agent has a responsible human.** Each agent identity that
   contributes to project repositories must be registered (in
   MAINTAINERS.md or a linked registry) with a named Maintainer who
   operates it and is accountable for its output.
3. **Every merge has an accountable human.** No agent-authored change is
   merged without review and explicit approval by a human Maintainer or
   Reviewer, and the merging human is accountable for the change exactly
   as if they had written it. Auto-merge automation may only act on
   approvals already given by humans.
4. **Attribution and DCO.** Agent-authored commits are labeled as such
   (see [CONTRIBUTING.md](CONTRIBUTING.md)); the DCO sign-off is made by
   the responsible human, who thereby certifies the contribution under
   the DCO on the agent's behalf.
5. **Review-power limits.** Agent reviews (including any future automated
   "reviewer lane") are advisory. They never satisfy a required-approval
   rule by themselves.

Violations of these rules by an agent are treated as violations by its
responsible human.

## Vendor Neutrality

Hive is intended to be a vendor-neutral project under the CNCF:

- Project assets (the GitHub org, DNS, artifact registries, trademarks,
  signing keys) are held for the project, and upon CNCF acceptance are
  transferred to or controlled per CNCF policy.
- Maintainership is personal, not corporate: roles attach to individuals
  and survive employer changes.
- The project does not require any proprietary product or single vendor's
  service to build, test, or run its releases, and roadmap decisions are
  made in public regardless of any maintainer's employer interests.

## Code of Conduct

The project follows the CNCF Code of Conduct; see
[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). The Maintainer Committee handles
reports as described there. Conduct decisions concerning a Maintainer
require a 2/3 supermajority of the other Maintainers.

## Security

Security disclosure, response SLOs, and the project's audit and
key-rotation commitments are defined in [SECURITY.md](SECURITY.md).

## Amendments

This document is amended by pull request. An amendment requires a
**2/3 supermajority** vote of the Maintainer Committee, preceded by the
comment period described under "Votes" (one week; 14 days if the
Committee is below 3 members). The PR description must summarize the
change and link the vote thread. While GOVERNANCE-HIVE.md remains the
authoritative upstream record, amendments that touch the Maintainer
roster or Committee structure are proposed against both documents
together.
