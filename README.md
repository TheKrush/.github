[![Sync Hub](https://img.shields.io/badge/GitHub-Sync%20Hub-4169E1?style=for-the-badge&logo=github)](https://github.com/TheKrush/.github)

# TheKrush — Super Admin Hub

This repository is a **private control plane**, not a normal project.

It exists for one purpose:

> **Act as the central sync hub for my organizations and personal repos.**

From here, shared workflows, scripts, and admin tools are pushed out to:

- Org hubs like `LostMinions/.github`, `LostMinionsGames/.github`, `ThePortalRealm/.github`
- Selected personal repos under `TheKrush/*`

There are no public issue trackers, community links, or project listings here — those live in the individual orgs and repos.

---

## 🔧 What This Repo Does

This repo is the **source of truth** for cross-repo configuration:

- Shared **GitHub Actions workflows**
- Shared **composite actions**
- Shared **admin scripts** (`/admin`)
- Shared **tools** (CLI helpers, utilities)
- A small amount of shared **governance boilerplate** (CODE_OF_CONDUCT, SECURITY, etc.)

The hub drives sync in two layers:

1. **User hub → org/user hubs**
   - `TheKrush/.github` runs `github-user-sync` workflows.
   - It reads `admin/repos.json` to discover targets.
   - For each target, it clones the repo, syncs the relevant areas, and pushes a commit.

2. **Org hubs → member repos**
   - Each org’s `.github` repo (e.g. `LostMinions/.github`) runs its own `github-org-sync` workflow.
   - When the hub receives updates from here, that workflow fans those changes out to the org’s other repos.

Flow in practice:

> `TheKrush/.github` → `LostMinions/.github` / `LostMinionsGames/.github` / `ThePortalRealm/.github` → their org repos.

---

## 🏗 Repo Layout (Internal)

Key directories:

- `/.github/actions/`
  Shared composite GitHub Actions (build, publish, sync, validation, cleanup).

- `/.github/workflows/`
  Central workflows, including:
  - `github-user-sync.yml` – main user-hub sync workflow
  - `github-user-sync-weekly.yml` – scheduled fan-out
  - Other shared CI/CD templates consumed by org hubs

- `/admin/`
  The sync “engine”:
  - `repos.json` – list of target repos and flags
  - `manifest.json` – excludes, deprecated entries, and per-area rules
  - `sync-*.sh` – per-area sync scripts (actions, workflows, templates, labels, tools, admin, etc.)
  - `logs/*.log` – run logs per repo and per sync

- `/tools/`
  Helper binaries and scripts used by the sync layer (e.g. `jq`, helper PowerShell scripts).

This repo is designed to be **script-first**: humans edit manifests and templates, scripts handle the rest.

---

## 🚦 How Sync Works (Maintainer Notes)

### 1. Triggering sync

Sync is triggered by:

- Changes to workflows, actions, admin scripts, or tools in this repo (push to `main`/`master`)
- Manual runs of:
  - `🔄 GitHub User Sync`
  - `🔄 GitHub User Sync - Weekly` (scheduled)

The main workflow:

- Checks that it’s running in a **user-owned `.github` repo** (this one).
- Uses the `GH_TOKEN` secret to authenticate.
- Runs `admin/sync-core.sh`, which:
  - Reads `admin/repos.json`
  - Detects repo type (org `.github`, user repo, normal org repo)
  - Runs the appropriate `sync-*.sh` steps per target

### 2. Safety behavior

The sync scripts are designed to be **idempotent and reversible**:

- All changes are committed in the target repo — normal Git history applies.
- If something goes wrong, revert in the target repo (or here), then re-run sync.
- The admin sync script:
  - Skips sensitive files (e.g. `repos.json`, `labels.json`, `issue-types.json`, `logs/*`)
  - Only removes items marked as deprecated in `manifest.json`

Because everything is version controlled on both sides, this hub can be safely “loud” — mistakes are fixed with `git revert`.

---

## 🧩 Adding or Changing Targets

> Internal reference – for the future me who forgets.

1. **Edit `admin/repos.json`** in this repo:
   - Add or update entries for:
     - Org `.github` hubs
     - Personal repos that should receive shared configuration

2. **Commit & push** to `main`/`master`:
   - This will:
     - Run `github-user-sync` here
     - Push updates into the listed targets
     - Let org hubs fan those updates out via their own workflows

3. **Check logs**:
   - See `admin/logs/*.log` in this repo for a per-repo sync summary.
   - Each run also uploads logs as workflow artifacts.

---

## 🔒 Secrets & Permissions

This repo uses a single high-trust token:

- **`GH_TOKEN` (repo secret)**
  - Used by sync workflows to clone and push to:
    - Target org `.github` repos
    - Selected personal / org repos
  - Must have scopes appropriate for:
    - `repo` (private + public)
    - `admin:org` if modifying org settings or protected areas

Handle this token as the “master key” for automation across all connected repos.

---

## 📎 Contributions & Issues

This repo is **not** a general contribution target.

- File issues and PRs in the **actual project repos** (bots, sites, libraries, etc.)
- Use this hub only for:
  - Sync logic
  - Shared actions
  - Admin scripts

---

> 🧠 **Reminder:** This repo is the _brain_, not the body.
> Treat changes here as infrastructure — one commit can update dozens of downstream repos by design.
> That’s the power, and the responsibility.
