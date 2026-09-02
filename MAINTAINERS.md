# Maintainers and Contributor Ladder

This file lists the people who hold roles in the Hive Commons project and
defines how contributors advance through the ladder. Governance rules
(voting, accountability, AI-agent policy) live in
[GOVERNANCE.md](GOVERNANCE.md).

## Current Maintainers

This table must agree with the root `OWNERS` file and, while the project
lives in the KubeStellar org, with the authoritative Maintainer Committee
table in
[kubestellar/kubestellar GOVERNANCE-HIVE.md](https://github.com/kubestellar/kubestellar/blob/main/GOVERNANCE-HIVE.md).
Any drift is a governance bug — fix it by PR immediately (see
GOVERNANCE.md, "Authoritative records and the OWNERS file").

| Name            | GitHub        | Role             | Focus areas                      | Affiliation    |
| --------------- | ------------- | ---------------- | -------------------------------- | -------------- |
| Andy Anderson   | @clubanderson | Chief Maintainer | hub, spokes, dashboard, releases | IBM            |
| James Reilly    | @hanthor      | Maintainer       | TODO                             | Universal Blue |
| Doug Baggett    | @Danathar     | Maintainer       | TODO                             | Independent    |

All three Maintainers are also approvers and reviewers in the root
`OWNERS` file.

The **Chief Maintainer** is the tie-breaker of last resort when a simple
majority vote deadlocks, chairs security response, and is the default CNCF
point of contact. The role confers no extra vote weight and is reassigned
by simple majority vote of the Maintainers.

### Registered agent identities

Per GOVERNANCE.md, every AI agent identity that contributes to project
repositories must be registered here with its responsible human.

| Agent identity            | Kind       | Responsible human |
| ------------------------- | ---------- | ----------------- |
| hive-bot (GitHub App)     | GitHub App | @clubanderson     |

## Current Reviewers

Reviewers who are not Maintainers are listed here; today there are none —
the three Maintainers above serve as the reviewers/approvers of record
(per `OWNERS`).

| Name | GitHub | Areas |
| ---- | ------ | ----- |
| —    | —      | —     |

## Emeritus

| Name | GitHub | Former role |
| ---- | ------ | ----------- |
| —    | —      | —           |

Emeritus members are recognized former Maintainers/Reviewers. They keep no
special access or vote, are credited in release notes on request, and may
be restored to their former role by a simple majority vote of the
Maintainers (without restarting the ladder) if they return within
**12 months** of moving to emeritus; after that, reinstatement follows the
normal promotion process.

## Contributor Ladder

Levels: **Contributor → Organization Member → Reviewer → Maintainer.**
Each level includes the expectations of the levels below it. All criteria
refer to activity in the project's own repositories, visible on GitHub.

> **AI-agent note (applies to every level):** activity performed by an AI
> agent — including agents you operate — does **not** count toward your
> promotion criteria. Only work you personally authored or reviews you
> personally performed counts. Agents themselves cannot hold any ladder
> role.

### 1. Contributor

Anyone who contributes: code, docs, issue reports with reproduction
detail, triage, or review comments. No approval needed. All contributions
must follow [CONTRIBUTING.md](CONTRIBUTING.md) (including DCO sign-off).

### 2. Organization Member

Member of the GitHub org; may be assigned issues and have CI run without
approval.

Requirements (all measurable on GitHub):

- **5+ contributions** merged/accepted (PRs, substantive issue triage, or
  doc changes) over **at least 2 months** of involvement.
- Sponsored by **1 Maintainer** (scaling note: raise to 2 sponsors once
  the project has 5+ Maintainers).
- 2FA enabled; DCO history clean.

Process: open an issue titled "Org membership request: @handle" listing
the qualifying contributions; the sponsor approves; any Maintainer adds
you within 7 days absent objections.

### 3. Reviewer

Trusted to review within one or more areas (e.g. hub, spoke runtime,
dashboard/UI, docs). Reviewer approval satisfies review requirements for
their areas; merging still requires a Maintainer (see CONTRIBUTING.md).

Requirements:

- Org Member for **3+ months**.
- **10+ merged PRs authored** in the area, or **15+ substantive PR
  reviews** in the area (or a mix; a review counts as half a PR).
- Track record of catching real problems in review, cited by the sponsor.
- Sponsored by **1 Maintainer**; confirmed by lazy consensus of the
  Maintainers (7 days).

Process: PR adding yourself to the Reviewers table above, with links to
the qualifying work.

### 4. Maintainer

Full write/merge access, a Maintainer Committee vote, and shared
responsibility for releases, security response, and any agents they
operate.

Requirements:

- Reviewer for **3+ months**.
- **20+ substantive contributions** (authored or reviewed) spanning
  **at least 2 areas** of the project.
- Demonstrated judgment on compatibility and security (e.g. handled a
  deprecation, release, or security-sensitive change).
- Commitment to remain responsive (reviews and security response) on a
  roughly weekly basis.
- Nominated by an existing Maintainer; confirmed by **lazy consensus of
  the Maintainer Committee (7 days)** — any Maintainer may object and
  convert the decision to a simple-majority vote.

Process: the nominating Maintainer opens a PR updating **all maintainer
records together** — this table, the root `OWNERS` file, and (while it
remains authoritative) the upstream GOVERNANCE-HIVE.md table — linking
the nomination thread. Ladder advancement requests are reviewed by the
Committee at least monthly. On approval, the Chief Maintainer grants
org/repo permissions and updates CNCF maintainer lists.

## Inactivity, Stepping Down, and Removal

- **Stepping down:** any role-holder may retire at any time by PR moving
  themselves to Emeritus. Please hand off in-flight work and any
  registered agents.
- **Inactivity:** a Reviewer or Maintainer with **no project activity
  (commits, reviews, issues, votes, or security response) for 6
  consecutive months** will be contacted; absent a response within 30
  days, or by their agreement, they are moved to Emeritus by lazy
  consensus of the remaining Maintainers. Planned leaves announced in
  advance pause this clock for up to 6 months.
- **Removal for cause** (Code of Conduct violation, abuse of access,
  repeated violation of the AI-agent accountability rules): **2/3
  supermajority** of the other Maintainers, per GOVERNANCE.md. While the
  project lives in the KubeStellar org, a majority vote of the
  KubeStellar Steering Committee may also remove a Maintainer (per
  GOVERNANCE-HIVE.md); that path retires on migration to a neutral org.
  Access is revoked immediately upon the vote closing; registered agents
  of a removed Maintainer are suspended until reassigned to another
  responsible human. Removals update all maintainer records (this file,
  `OWNERS`, and the upstream table) in one coordinated change.
