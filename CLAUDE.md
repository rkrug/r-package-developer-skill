# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a **skill distribution repository** — it contains a reusable AI workflow framework (`skills/r-package-developer/`) for R package maintainers. It is not an R package itself. The skill is designed to be synced into R package repositories so AI agents have consistent governance and workflow guidance.

## Key Files

- [`skills/r-package-developer/SKILL.md`](skills/r-package-developer/SKILL.md) — the primary policy document; start here
- [`skills/r-package-developer/references/checklist.md`](skills/r-package-developer/references/checklist.md) — execution gates (pre-impl, sync, validate, merge)
- [`skills/r-package-developer/references/branch-protection-baseline.md`](skills/r-package-developer/references/branch-protection-baseline.md) — branching and PR governance rules
- [`skills/r-package-developer/references/commit-template.md`](skills/r-package-developer/references/commit-template.md) — commit message structure
- [`skills/r-package-developer/references/skill-design-standard.md`](skills/r-package-developer/references/skill-design-standard.md) — rules for editing/extending the skill itself

## Scripts

**`skills/r-package-developer/scripts/sync-from-github.sh`** — downloads the latest skill from GitHub into a target R package repo. Configurable via env vars:
- `RPKG_SKILL_GH_REPO` (default: `rkrug/r-package-developer-skill`)
- `RPKG_SKILL_GH_REF` (default: `main`)
- `RPKG_SKILL_GH_PATH` (default: `skills/r-package-developer`)

**`skills/r-package-developer/scripts/check-ai-docs-template.sh`** — template validation script for AI-readable artifacts (copy into a target R package as `scripts/check-ai-docs.sh`, do not run here).

## Agent Workflow Guidance

### General R Agentic Guidance

- Use `btw` tools **only** for R-specific tasks: checking installed packages, reading R help pages and vignettes, inspecting live R sessions and environments, and searching CRAN
- For reading URLs, strongly prefer the builtin `web_fetch` tool over `btw_tool_web_read_url`
- For file operations (read, write, edit, list, search), strongly prefer the builtin `read`, `write`, `grep`, and `code` tools over their btw equivalents
- For git write operations (commit, branch), strongly prefer the builtin `shell` tool over btw git tools
- If `btw` tools are unavailable, the agent can still function — but package documentation lookups and live session introspection will be limited
- If you cannot access a live R session, ask the user whether they have enabled `btw::btw_mcp_session()` in their current session
- If `btw` is not installed, recommend the user install it: `install.packages("btw")`

### Package Installation

- Use the default configured repos when installing R packages
  - Do not specify repos explicitly in `install.packages()` calls
  - Exception: If `getOption("repos")` returns NULL or "@CRAN@", then repos must be specified
- Always ask the user before installing a package, unless they give explicit permission for the remainder of the session

### R Package Documentation

- When a user requests help with a particular function or method, _always_ consult the help documentation before making suggestions
- If the help documentation is sparse, look for relevant package vignettes
- If you cannot access the help documentation because a package is not installed, ask the user if you can install it on their behalf (using the rules for package installation above)

### Code Suggestions

- When suggesting or inserting code, check whether the necessary packages are available on the user's system (using `btw` tools)

## Architecture

The skill is organized in two tiers:

**Tier 1 — Policy (`SKILL.md`)**: Compact, non-negotiable rules covering maintainer roles, breaking-change documentation, `air` formatting, AI-doc separation, and validation reproducibility.

**Tier 2 — References (`references/`)**: Detailed operational documents that expand on SKILL.md. Never duplicate content between SKILL.md and references; SKILL.md points to references for specifics.

This two-tier structure is enforced by [`skill-design-standard.md`](skills/r-package-developer/references/skill-design-standard.md) — follow it when modifying the skill.

## Branching

Long-lived branches: `main` (stable), `dev` (integration). All changes go through PRs. Branch protection rules are defined in `branch-protection-baseline.md`.
