# Contributing to Hive

Thanks for your interest in contributing. This document covers the
mechanics; roles and promotion are in [MAINTAINERS.md](MAINTAINERS.md),
and project rules (including the AI-agent policy) are in
[GOVERNANCE.md](GOVERNANCE.md).

## Ground Rules

- All participation is covered by the [Code of Conduct](CODE_OF_CONDUCT.md).
- All contributions are accepted under the project license
  under Apache-2.0 via pull request — including maintainers'
  own changes. Nobody pushes directly to protected branches.

## DCO: Sign Your Commits (required)

Every commit must carry a Developer Certificate of Origin sign-off:

```
git commit -s -m "your message"
```

This adds a `Signed-off-by: Your Name <you@example.com>` trailer, which
certifies you have the right to submit the work under the project license
(see <https://developercertificate.org>). The DCO check runs as a commit
**status** on every PR and is a hard merge gate. Forgot one? Amend with
`git commit --amend -s` (or rebase with `--signoff`) and force-push your
branch. Maintainers will not bypass a failing DCO check.

## Branches and Targets

- **v4** is the default branch (stable line). Bug fixes target v4 unless
  a maintainer says otherwise.
- **v5** is the next-generation line; feature work generally targets v5.
  If you are unsure, ask in the issue before writing code.
- Work on a feature branch in your fork; keep PRs focused and small — one
  logical change per PR.

## Pull Request Conventions

- Title: imperative and specific ("hub: reject spokes with stale
  advisory clocks"), prefixed with the affected area when practical
  (`hub:`, `spoke:`, `dashboard:`, `docs:`, `protocol:`).
- Link the issue you are fixing with `Fixes #NNN` — one issue per PR.
- Describe **what** changed and **why**; call out compatibility impact
  (protocol, config, API) explicitly.
- Include tests for behavior changes. New code in ported/refactored areas
  needs tests even when the original lacked them.
- No magic numbers — use named constants. Configurable values get env
  vars with sane defaults.
- Do not include internal infrastructure details (cluster names, private
  hostnames) in code, comments, or PR text.

## CI Expectations

- All required checks must be green before merge. Maintainers do not
  merge over a red required check, and contributors should not push
  further work onto a red PR without first understanding the failure.
- If a check fails for a reason unrelated to your change (flake,
  cancelled job), say so in a comment and ask for a re-run rather than
  pushing empty commits.
- Some jobs are informational (not merge gates); the branch protection
  settings on each repository are authoritative about which checks are
  required.

## Review and Merge

- Every PR needs approval from at least **1 Maintainer** (or a Reviewer
  for their area **plus** a Maintainer merge). Substantial changes
  (protocol, security, releases) require **2 Maintainer approvals** —
  feasible today with a 3-member Maintainer Committee (see
  [MAINTAINERS.md](MAINTAINERS.md)).
- Author approval of their own PR never counts.
- Lazy consensus applies: an approved PR with green CI may be merged
  without further waiting, except changes flagged "significant" in
  GOVERNANCE.md, which wait out their comment window.

## AI-Agent-Authored Contributions

Hive's own agents contribute to this project through the **hive-bot**
GitHub App. External contributors may also use AI tooling. The rules:

1. **Label and disclose.** PRs authored by a project agent are opened by
   the bot identity and labeled `agent-authored`. If you used an AI agent
   to generate a substantial portion of your own PR, say so in the PR
   description — it changes how reviewers read it, not whether it is
   welcome.
2. **A human signs.** The DCO sign-off on agent-authored commits is made
   by the agent's responsible human (registered in MAINTAINERS.md), who
   certifies the contribution on the agent's behalf. Anonymous or
   unattributed agent commits will be closed.
3. **A human merges.** Agent-authored PRs get the same (or stricter)
   review as human PRs and are merged only on a human Maintainer's
   approval. Agent-generated review comments are advisory and never
   satisfy an approval requirement.
4. **Agents don't argue.** If a reviewer requests changes on an
   agent-authored PR, the responsible human either drives the agent to
   address them or takes over the PR — review threads are conversations
   between humans.
5. **No credential material.** Agent workflows must never place tokens,
   keys, or other secrets in commits, PR bodies, or logs.

## Finding Something to Work On

- Issues labeled **`good first issue`** are scoped for newcomers and have
  a maintainer willing to shepherd them.
- **`help wanted`** issues are ready for anyone.
- Comment on an issue before starting non-trivial work, and check for
  existing open PRs (including agent-authored ones) so effort is not
  duplicated.
- Questions: open a GitHub Discussion — the [hivecommons-dev list](https://groups.google.com/g/hivecommons-dev), [Discord](https://discord.gg/x5SxvPeVJ), or the [biweekly community meeting](https://hivecommons.dev/meet).
