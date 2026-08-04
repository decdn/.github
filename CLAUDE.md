# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is the **org-level `.github` repo** for the `decdn` GitHub organization (`git@github.com:decdn/.github.git`). It is GitHub's special "community health" repo: files placed here become **defaults for every repo in the `decdn` org that does not ship its own equivalent**.

Currently contains only `profile/README.md` (the org-page README) and this file. Anything added has org-wide blast radius — changes affect `decdn/decdn`, `decdn/finance`, `decdn/website`, `decdn/internal`, and any future repos. Treat additions accordingly.

## What belongs here vs. elsewhere

| Path in this repo | Effect |
|-------------------|--------|
| `profile/README.md` | Renders on the `decdn` GitHub org profile page. |
| `CONTRIBUTING.md`, `SECURITY.md`, `SUPPORT.md`, `CODE_OF_CONDUCT.md`, `FUNDING.yml` | Org-wide defaults. A repo's own copy overrides these. |
| `.github/ISSUE_TEMPLATE/`, `.github/PULL_REQUEST_TEMPLATE.md` | Default issue/PR templates for repos without their own. |
| `workflow-templates/` | Starter workflows offered to org members in the Actions UI (these are *templates*, not workflows that run). |
| `.github/labels/*.yml` | Source of truth for issue labels org-wide. `_core.yml` applies to all repos; each `<repo>.yml` (or `dotgithub.yml` for this repo) is an overlay. |
| `.github/workflows/sync-labels.yml` | Org-management workflow that pushes the composed label manifest to each repo. Not repo-specific CI — runs from here because it operates org-wide. |

**Does not belong here:** repo-specific CI workflows, repo-specific docs, code. Those live in the per-repo `.github/` directory inside `decdn/`, `finance/`, or `website/`.

## Issue labels

To change labels on any repo in the org, edit the relevant file under `.github/labels/` — never edit labels directly in the GitHub UI, they will be reverted on the next sync.

- Cross-cutting labels go in `_core.yml` (applied everywhere).
- Stack/topic labels specific to one repo go in that repo's overlay (`decdn.yml`, `website.yml`, `finance.yml`, `internal.yml`, `dotgithub.yml`).
- The sync workflow runs `EndBug/label-sync@v2` on push to `main` affecting `.github/labels/**`, or manually via the Actions tab (`workflow_dispatch`).
- **Required secret:** `LABEL_SYNC_TOKEN` — a PAT or GitHub App token with `issues:write` and `metadata:read` on all five org repos. `GITHUB_TOKEN` is scoped to this repo only and cannot mutate other repos' labels.
- `delete-other-labels` is currently `false` (additive sync). Flip to `true` only after verifying no important orphan labels remain on any target repo.

## Before adding anything

1. Check whether the per-repo `.github/` directory in `decdn/`, `finance/`, or `website/` already provides the file — a repo-local copy overrides this org-level default and may be intentional.
2. Confirm the change is appropriate for *all three* (and any future) org repos. If it's only right for one, it belongs in that repo, not here.
3. The parent workspace `CLAUDE.md` at `/home/thiras/dev/decdn/CLAUDE.md` is the entry point for understanding the org's repos and their cross-dependencies.
