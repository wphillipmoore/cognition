# Development Workflow v1.0

**Status:** Normative  
**Normative Language:** MUST, MUST NOT, SHOULD, SHOULD NOT, MAY are interpreted per RFC 2119

## Purpose
Define a minimal, durable workflow for making changes in this repository.
This repository is documentation-only, but it is managed like source code: all changes go through feature branches and pull requests.

## Core Rules
- Documentation-first: read relevant docs before acting; no trial-and-error discovery.
- No direct changes to eternal branches (`develop`, `release`, `main`).
- All work happens on short-lived branches and is merged via PRs.
- Never reuse old branch names.

## Start of Session (Required)
1. Check the current branch:
   ```bash
   git branch --show-current
   ```
2. If on `develop`, immediately create a feature branch:
   ```bash
   git checkout -b feature/<descriptive-name>
   ```
3. If already on a feature/bugfix/hotfix branch, continue.

## Branch Naming
Only the following prefixes are allowed:
- `feature/*` for new docs, refactors, or structural changes
- `bugfix/*` for non-urgent corrections
- `hotfix/*` for production-blocking issues only

## Work and Commit
- Keep changes scoped and explicit.
- Use conventional commits:
  ```
  <type>: <short description>

  <optional detailed description>

  <footer with co-authorship and generation info>
  ```
  Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

## Checkpoint: Before Creating a PR
When the change is ready, STOP and ask:

```
Create PR?
```

Only proceed after explicit approval.

## Checkpoint: Before Finalizing a PR
After creating the PR, STOP and ask:

```
Finalize PR?
```

Finalization means:
1. Squash-merge the PR and delete the remote branch
2. Update local `develop`

Proceed only after explicit approval.

## Critical: Avoid Heredoc for Multi-Line Messages
Heredoc commands for multi-line commit or PR messages fail in this environment.
Use a temporary file instead.

Example:
```bash
cat > /tmp/commit-msg.txt << 'EOF'
docs: update development workflow

Describe the change here.
EOF

git commit -F /tmp/commit-msg.txt
rm /tmp/commit-msg.txt

cat > /tmp/pr-body.txt << 'EOF'
## Summary
- ...

## Testing
- ...
EOF

gh pr create --base develop --title "..." --body-file /tmp/pr-body.txt
rm /tmp/pr-body.txt
```
