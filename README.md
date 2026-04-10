# R Package Developer Skill

This repository provides a reusable skill for R package development workflows.

## AI Statement
This skill has been build by Codex for usage in Codex, Claude Code, and similar coding agents using a consistent,
reviewable process.

It is therefore optimised by Codex for AI usage.

## Recommended Layout

Use this structure:

- `README.md` (this file, user-facing overview in repo root)
- `skills/r-package-developer/SKILL.md`
- `skills/r-package-developer/references/*`
- `skills/r-package-developer/scripts/*` (optional helpers)

## How To Use

To get all files from the GitHub repository `r-package-developer-skill`:

```bash
# Option 1: download ZIP archive
curl -L -o r-package-developer-skill.zip https://github.com/<org-or-user>/r-package-developer-skill/archive/refs/heads/main.zip
unzip r-package-developer-skill.zip

# Option 2: download tar.gz archive
curl -L -o r-package-developer-skill.tar.gz https://github.com/<org-or-user>/r-package-developer-skill/archive/refs/heads/main.tar.gz
tar -xzf r-package-developer-skill.tar.gz
```

1. Put the skill under `skills/r-package-developer/` in your target repository.
2. Ask your coding agent to read and follow `skills/r-package-developer/SKILL.md`.
3. Request the concrete task (for example, create a package skeleton, implement a feature, or run a release sync).

Example prompt:

```text
Read and follow skills/r-package-developer/SKILL.md, then create a complete R package skeleton in this repository.
```

## What You Should Expect

For scaffold requests, the result should be a usable package baseline, typically including:

- `DESCRIPTION`, `NAMESPACE`
- `R/`, `man/`
- `tests/testthat/`
- `.Rbuildignore`, `.gitignore`
- `README.md`, `NEWS.md`
- `_pkgdown.yml`
- CI workflow files
- starter vignettes/docs

## Governance

- `SKILL.md` is the executable agent policy.
- `references/checklist.md` is the commit/merge execution gate.
- Skill updates are manual and explicit.

## Skill File Index

- <a href="https://rkrug.github.io/r-package-developer-skill/skills/r-package-developer/SKILL.html" target="_blank" rel="noopener noreferrer">skills/r-package-developer/SKILL.md</a>
  - References
  	- <a href="https://rkrug.github.io/r-package-developer-skill/skills/r-package-developer/references/branch-protection-baseline.html" target="_blank" rel="noopener noreferrer">skills/r-package-developer/references/branch-protection-baseline.md</a>
  	- <a href="https://rkrug.github.io/r-package-developer-skill/skills/r-package-developer/references/checklist.html" target="_blank" rel="noopener noreferrer">skills/r-package-developer/references/checklist.md</a>
  	- <a href="https://rkrug.github.io/r-package-developer-skill/skills/r-package-developer/references/commit-template.html" target="_blank" rel="noopener noreferrer">skills/r-package-developer/references/commit-template.md</a>
  	- <a href="https://rkrug.github.io/r-package-developer-skill/skills/r-package-developer/references/skill-design-standard.html" target="_blank" rel="noopener noreferrer">skills/r-package-developer/references/skill-design-standard.md</a>
  	- <a href="https://github.com/rkrug/r-package-developer-skill/blob/main/skills/r-package-developer/references/check-ai-docs-template.sh" target="_blank" rel="noopener noreferrer">skills/r-package-developer/references/check-ai-docs-template.sh</a>
  - Scripts
  	- <a href="https://github.com/rkrug/r-package-developer-skill/blob/main/skills/r-package-developer/scripts/sync-from-github.sh" target="_blank" rel="noopener noreferrer">skills/r-package-developer/scripts/sync-from-github.sh</a>
