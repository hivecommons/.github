# Hive Roadmap

A living document, updated by the maintainers as milestones land.
Direction-setting follows [GOVERNANCE.md](GOVERNANCE.md): items appear
here after discussion in public issues; breaking changes require the
supermajority process.

## v4 - Stable Line (maintenance)

v4 is the default branch and the supported stable line.

- Bug fixes, security fixes, and dependency updates only; no new
  features except low-risk operability improvements.
- Continued hardening from the internal security-audit remediation
  backlog (see [SECURITY.md](SECURITY.md)).
- Supported until: **6 months after the first stable v5 release (v5
  GA)**; security fixes continue for that full window.

## v5 - Next Generation (active development)

- **Reviewer lane.** A dedicated agent lane that reviews (rather than
  authors) changes, producing advisory review output. Per governance,
  reviewer-lane output never satisfies a human-approval requirement.
- **Formal verification of protocol invariants.** Promela/Spin models of
  the hub↔spoke protocol live in `src/formal/`; CI checks the models, and
  protocol changes must update the corresponding model in the same PR.
  Target invariants: no lost work items, no double-claim of a work
  item, pause/resume safety (no agent work runs while a spoke is
  paused), and credential-mint exclusivity (at most one active
  credential mint per spoke).
- **Channel-based release trains.** Three channels - `edge` (every merge),
  `candidate` (periodic promotion), `stable` (promoted after soak) -
  replacing moving tags, with digest-pinned artifacts so deployed
  versions are verifiable. Promotion cadence: `candidate` promoted weekly; `stable` promoted
  after a 7-day candidate soak with no regressions.
- Migration path: documented upgrade from v4 hubs/spokes, dual-version
  operation during transition. Compatibility window: v5 hubs manage v4 spokes for at least 6 months
  of dual-version operation.

## Future (post-v5) - operator to fill in

Candidate themes, deliberately not committed:

- Hive as the delivery surface for the wider Hive Commons family:
  first-class integrations for pluk, spektacular, rationguard,
  promptargs, and hotshot.
- Per-repository and per-agent cost attribution with budget governance
  (spend caps, alerts, and audit-grade reporting).
- Broader model/provider support with per-agent model policy and
  automatic capability discovery.

## Non-goals (current)

- **Not a general-purpose CI/CD system.** Hive orchestrates AI agents
  around existing forges and CI; it does not replace them.
- **Not a hosted-only product.** The repository stays complete and
  self-hostable; the maintainers’ hosted hub is an operational
  deployment of the open-source code, not a separate product.
