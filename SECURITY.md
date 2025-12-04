# 🛡️ Security Policy

This repository is the **super admin hub** that drives shared workflows, scripts, and automation across multiple organizations and personal repositories.

Because changes here can affect many downstream projects, security reports related to this repo and its automation are treated as **high priority**.

---

## Supported Scope

| Area / Version                          | Supported |
|----------------------------------------|-----------|
| Latest `main` of `TheKrush/.github`    | ✅ |
| Active org hubs (`*.github` repos)     | ✅ |
| Downstream project repos               | ⚠️ Handled via their respective repos, case-by-case |
| Archived / deprecated projects         | ❌ No longer supported |

This policy primarily covers:

- Workflows, actions, and scripts in `TheKrush/.github`
- Sync logic that pushes configuration into:
  - `LostMinions/.github`
  - `LostMinionsGames/.github`
  - `ThePortalRealm/.github`
  - Selected `TheKrush/*` repositories

If your report involves a specific **application repo** (bot, site, library), you can still contact us here — we’ll route it to the right place.

---

## Reporting a Vulnerability

If you discover a vulnerability, especially one that could:

- Expose **secrets**,
- Compromise **automation** (e.g., CI/CD or sync behavior),
- Allow unauthorized changes to **downstream repos**,

please **do not open a public issue**.

Instead, report privately via:

- **GitHub Security Advisories**, or
- Email: **security@lostminions.org**

---

## Our Response

For valid security reports, we aim to:

- Acknowledge your report within **72 hours**
- Provide a status update or request for clarification within **7 days**
- Coordinate fixes in this hub and any affected downstream repos
- Credit responsible disclosures in release notes or security notes (if you’d like attribution)

Thank you for helping keep this automation layer — and everything it touches — safe.
