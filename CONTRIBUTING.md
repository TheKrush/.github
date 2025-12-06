# Contributing to TheKrush

Thank you for taking an interest in **TheKrush**.

This repository is **not** a general project space. It is a **super admin hub** used to manage:

- Shared GitHub Actions workflows
- Shared composite actions
- Shared admin scripts (`/admin`)
- Shared tools and sync configuration

Changes here can affect **multiple organizations and personal repositories** at once.

---

## 🧭 Where to Contribute

Most feature work, bug fixes, and content updates should be made in the **actual project repos** (bots, sites, libraries, games, etc.), not here.

Use this hub only when you are:

- Updating **shared workflows** or **composite actions**
- Adjusting **sync logic** in `/admin/`
- Changing **global templates** that should flow into multiple repos

If you’re unsure whether something belongs here or in a specific repo:

> Open an issue or discussion in the target project repo first, then link back here if a hub change is required.

---

## 🧱 What Lives Here

Key areas you may touch:

| Area                        | Purpose                                      |
|-----------------------------|----------------------------------------------|
| `.github/workflows/`        | Shared CI/CD and sync workflows              |
| `.github/actions/`          | Composite actions used across many repos    |
| `admin/`                    | Sync engine scripts, manifests, repo lists  |
| `tools/`                    | Helper binaries and scripts                  |

Changes here are **infrastructure-level** and should be treated like editing a control panel that fans out settings to many systems.

---

## 📝 Submitting Changes

1. **Create or reference an issue**
   - Prefer issues in the **project repo** that needs the behavior.
   - If the change is purely infra (sync behavior, workflows), open an issue here.

2. **Branch from `main`**
   - Use clear branch names, e.g. `feat/update-sync-workflows`, `fix/admin-manifest`.

3. **Make focused commits**
   - Keep changes small and logical.
   - Describe *why* you’re changing workflows or sync rules, not just *what* you changed.

4. **Open a Pull Request**
   - Explain which orgs/repos are impacted (e.g., `LostMinions/.github`, `LostMinionsGames/.github`, `ThePortalRealm/.github`, specific `TheKrush/*` repos).
   - Note if any follow-up runs of sync workflows are required.

---

## ⚖️ Code of Conduct

All contributions to this hub and downstream projects must follow the
[Lost Minions Code of Conduct](./CODE_OF_CONDUCT.md).

Even though this is an infra repo, the same expectations for respect and professionalism apply.

---

## 🔒 Security & Vulnerabilities

Because this hub can push changes into many repos, vulnerabilities here are **high impact**.

If you discover a security issue:

- Do **not** open a public issue.
- Report privately via [GitHub Security Advisories](../../security/advisories) or email:
  **security@lostminions.org**

We’ll coordinate fixes here and in any affected downstream repositories.

---

## 💡 Need Help?

If you’re trying to figure out:

- Whether a change belongs here or in a specific project repo
- How the sync system (`admin/`, `github-user-sync`, `github-org-sync`) works
- What impact a workflow change might have

Open a **“Question”** issue in this repo with as much context as possible.
This hub is meant to make managing the ecosystem easier—not more confusing.
