# Security Policy

Hive orchestrates AI coding agents that hold credentials to act on real
GitHub repositories. We treat the security of the hub, spokes, agent
credential handling, and the hub↔spoke protocol as first-class concerns.

## Reporting a Vulnerability

**Please do not report security vulnerabilities in public issues.**

Report privately via either channel:

1. **GitHub private vulnerability reporting** (preferred):
   use "Report a vulnerability" under the Security tab of the repository
   (TODO: enable on the hivecommons org repos at migration).
2. **Email:** security@hivecommons.dev (advisories are published to hivecommons-security-announce@googlegroups.com)
   (TODO: create this alias; until it exists, use the Chief Maintainer's
   contact in [MAINTAINERS.md](MAINTAINERS.md)).

Include: affected component (hub, spoke, dashboard, GitHub App/proxy,
protocol), version or commit, reproduction steps, and impact as you
understand it. We are especially interested in reports involving agent
credential exposure, cross-tenant/spoke isolation failures, and abuse of
the hive-bot GitHub App's permissions.

We follow coordinated disclosure: we ask reporters to keep details private
until a fix is released, and we will credit reporters in the advisory
unless they prefer otherwise.

## Response SLOs

| Stage                                   | Target                       |
| --------------------------------------- | ---------------------------- |
| Acknowledge report                      | 3 business days              |
| Triage + severity assessment (CVSS)     | 7 calendar days              |
| Fix or documented mitigation — Critical | 30 days from triage          |
| Fix or documented mitigation — High     | 60 days from triage          |
| Fix or documented mitigation — Medium/Low | 90 days from triage        |
| Public advisory (GitHub Security Advisory) | with the fix release      |

These are targets for a small maintainer team, not guarantees; if we will
miss one, we tell the reporter and give a revised date.

## Supported Versions

| Branch / line | Status                  | Security fixes |
| ------------- | ----------------------- | -------------- |
| v4 (default)  | Stable                  | Yes            |
| v5            | Next (in development)   | Yes (on the development branch; no backports guaranteed until first stable v5 release) |
| v3 and older  | End of life             | No             |

Within a supported line, fixes land in the release channels in order:
**edge → candidate → stable** (see [ROADMAP.md](ROADMAP.md)). Critical
fixes may be fast-tracked directly to stable.

## Security Audit and Key-Rotation Program

The project has run internal security audits of its own codebase and
credential handling; on joining the CNCF we formalize that practice as a
public commitment:

- **Periodic audits.** At least **annually**, the maintainers conduct (or
  commission) a security review covering: the hub↔spoke protocol and
  authentication, agent credential issuance and scoping, the GitHub
  App/proxy layer, and the dashboard. Findings are tracked as issues
  (private while exploitable) and a public summary is published when
  remediation completes.
- **Key rotation.** Long-lived credentials operated by the project
  (hub master keys, GitHub App private keys, OIDC client secrets, signing
  keys) are enumerated in an internal register and rotated on a defined
  schedule — at least **annually**, and **immediately** upon suspected
  exposure or the departure of anyone with access.
- **Agent credential hygiene.** Agent-held tokens are scoped to the
  minimum permissions needed, are short-lived where the platform allows,
  and are never committed to any repository. Secrets found in history are
  treated as exposed and rotated.
- **Third-party audit.** The project intends to request a
  CNCF-facilitated third-party security audit as part of the incubation
  process (TODO: operator to confirm timing with TAG Security).

## Advisories

Published advisories appear as GitHub Security Advisories on the affected
repositories. Release notes for security releases reference the advisory
IDs.
