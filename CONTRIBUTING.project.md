# Contributing to TheKrush Projects

Thank you for taking an interest in **TheKrush**.

This file is shared across multiple repositories under the `TheKrush` umbrella:
stock tools, bots, libraries, and supporting infrastructure.
Each repo may have its own README or docs with project-specific details — always
read those first.

---

## 🧭 Where to Start

- **New idea or feature request?**
  Open an issue in the target repo and describe:
  - What problem you’re solving
  - How you imagine it working
  - Any related tools or workflows

- **Bug fix or small improvement?**
  Check existing issues first. If nothing matches, open a new issue with:
  - Steps to reproduce
  - Expected vs actual behavior
  - Logs, screenshots, or error messages if available

- **Docs or README improvements?**
  You can usually open a PR directly. If you’re changing behavior or APIs,
  please link or create an issue.

---

## 🧱 Types of Repositories

TheKrush hosts several kinds of projects. Common clusters include:

- **Stock & analysis tools** – Python pipelines, scripts, and helpers
- **Bots & automation** – Discord bots, schedulers, GitHub Actions helpers
- **Libraries & shared code** – Reusable C#, Python, or shell utilities
- **Infra & glue** – Scripts that connect VMs, runners, and services together

For each repo:

- Look at the **README** for setup and build instructions.
- Check for a **`/docs`** folder or wiki if it exists.
- Follow any repo-specific contribution notes there.

---

## 📝 How to Contribute

1. **Fork or branch from `main`**
   - For external contributors, fork the repo.
   - For collaborators, create a feature branch from `main`.

2. **Create or link an issue**
   - Reference an existing issue if one already tracks your change.
   - Otherwise, open a new issue and outline what you plan to do.

3. **Make focused, readable commits**
   - Group related changes together.
   - Use clear messages that explain *why*, not just *what*, you changed.
   - If your repo uses commit tags (e.g. `[skip ci]`, `[publish]`, `[publish-zip]`),
     follow any conventions noted in the README.

4. **Add tests where appropriate**
   - For code changes, add or update unit/integration tests if the project has them.
   - For scripts or workflows, consider adding small checks or validation steps.

5. **Open a Pull Request**
   - Clearly describe the change and link the relevant issue.
   - Call out anything that might affect:
     - CI workflows
     - GitHub Actions
     - VM / runner scripts
     - Other repos in the ecosystem (if you know of any)

6. **Respond to review**
   - Keep the conversation constructive.
   - It’s okay to push follow-up commits; try to keep them tidy.

---

## ⚖️ Code of Conduct

All contributions must follow the
[Lost Minions / TheKrush Code of Conduct](./CODE_OF_CONDUCT.md).

Be respectful, patient, and collaborative — whether you’re editing a small
Python script or a core workflow used across many repositories.

---

## 🔒 Security & Vulnerabilities

If you discover a security issue:

- **Do not** open a public issue.
- Report privately via [GitHub Security Advisories](../../security/advisories) or email:
  **security@lostminions.org**

Please include as much detail as you can:
- A clear description of the problem
- Steps or scripts to reproduce
- Any potential impact you’re aware of

We’ll coordinate fixes here and in any related downstream projects.

---

## 💡 Need Help?

If you’re unsure about anything:

- Whether a change belongs in this repo or a different one
- How a script, workflow, or bot is supposed to behave
- What impact a change might have on other projects

Open a **“Question”** issue in the relevant repo with as much context as you can.
It’s always better to ask early than to guess and fight the automation later.
