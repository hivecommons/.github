# Hive Roadmap

A living document, updated by the maintainers as milestones land.
Direction-setting follows [GOVERNANCE.md](GOVERNANCE.md): items appear
here after discussion in public issues; breaking changes require the
supermajority process.

## v4 — Stable Line (maintenance)

v4 is the default branch and the supported stable line.

- Bug fixes, security fixes, and dependency updates only; no new
  features except low-risk operability improvements.
- Continued hardening from the internal security-audit remediation
  backlog (see [SECURITY.md](SECURITY.md)).
- Supported until: TODO (operator: define an EOL policy relative to the
  first stable v5 release, e.g. "6 months after v5 GA").

## v5 — Next Generation (active development)

- **Reviewer lane.** A dedicated agent lane that reviews (rather than
  authors) changes, producing advisory review output. Per governance,
  reviewer-lane output never satisfies a human-approval requirement.
- **Formal verification of protocol invariants.** Promela/Spin models of
  the hub↔spoke protocol live in `src/formal/`; CI checks the models, and
  protocol changes must update the corresponding model in the same PR.
  Target invariants: TODO (operator: enumerate — e.g. no lost work items,
  no double-claim, pause/resume safety, credential-mint exclusivity).
- **Channel-based release trains.** Three channels — `edge` (every merge),
  `candidate` (periodic promotion), `stable` (promoted after soak) —
  replacing moving tags, with digest-pinned artifacts so deployed
  versions are verifiable. Promotion cadence: TODO.
- Migration path: documented upgrade from v4 hubs/spokes, dual-version
  operation during transition. TODO: compatibility window.

## Future (post-v5) — operator to fill in

Candidate themes, deliberately not committed:

- TODO
- TODO
- TODO

## Non-goals (current)

- TODO (operator: state 1–2 explicit non-goals; incubation reviewers ask.)
