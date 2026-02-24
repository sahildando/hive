# Contributing to Hive

This guide complements the root-level [`CONTRIBUTING.md`](../CONTRIBUTING.md) with an end-to-end workflow for new contributors.

## 1) Fork and clone

```bash
git clone https://github.com/<your-org-or-user>/hive.git
cd hive
```

## 2) Set up local environment

```bash
./quickstart.sh
```

## 3) Create a branch

Use a descriptive branch name:

```bash
git checkout -b docs/improve-project-documentation
```

## 4) Commit convention (Conventional Commits)

Use Conventional Commits in the form:

```text
<type>(<scope>): <summary>
```

Examples:

- `docs(architecture): add graph executor overview`
- `docs(tools): add guide for creating new tools`
- `fix(runtime): handle missing stream metadata`

## 5) Run checks before pushing

From repository root:

```bash
make check
make test
```

## 6) Pull request expectations

A good PR includes:

- Clear summary of what changed and why
- Test/check evidence (commands and outcomes)
- Scope-limited changes (avoid unrelated edits)
- Updated docs for behavior/configuration changes

## 7) Review and iteration

- Address reviewer feedback promptly
- Keep discussion in PR comments for traceability
- Prefer follow-up commits over force-push while review is active

## Issue Assignment

If an issue is already assigned, coordinate in comments before opening overlapping work.
If not assigned, leave a short note that you are taking it to reduce duplicated effort.
