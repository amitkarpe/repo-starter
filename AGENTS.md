# AGENTS.md

## Read Order

1. `AGENTS.md`
2. `CONTEXT.md`
3. `SPEC.md` when work changes a trusted contract, release, environment, or
   external system.

## Rules

- Follow KISS: one problem, one happy path, one command, one proof, one result.
- Preserve existing work. Do not revert unrelated changes or use destructive
  Git commands without explicit approval.
- Keep durable code, decisions, and reports in Git. Do not put secrets,
  credentials, large dependencies, or copied repositories in temporary paths.
- Create a temporary directory or worktree only when isolation is needed.
  When the lane is clean and terminal, remove its exact worktree and temporary
  directory; stop and ask if work is active, held, dirty, or unknown.
- Update `CONTEXT.md` when current truth or the next action changes.
- Keep `SPEC.md` small. A worker proceeds inside an approved SPEC and stops on
  a safety, scope, authorization, or evidence failure.

## Global Guidance

When available, use `~/.codex/AGENTS.md` as the machine-wide baseline. For
reusable guidance, load only the relevant Agent OS playbook; local repository
rules and approved SPECs remain authoritative.

