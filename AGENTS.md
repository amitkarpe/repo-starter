# AGENTS.md

## Read Order

1. `AGENTS.md`
2. `CONTEXT.md`
3. `INIT.md` only when repository initialization is incomplete
4. `ENV.md` when runtime, cloud, host, or tool facts matter
5. `SPEC.md` before implementation, mutation, deployment, cleanup, or trusted-contract changes

## Rules

- Follow KISS: optimize for one useful outcome, not the smallest possible task.
- Preserve existing work. Do not revert unrelated changes or use destructive Git actions without authority.
- Keep durable code, decisions, and reports in Git. Never commit secrets, credentials, authentication state, or copied repositories.
- Keep `CONTEXT.md` current-only. It is the restart index, not project history.
- Update `CONTEXT.md` when repository identity, current truth, active Issue/PR, blocker, or next action materially changes.
- Move completed/history detail to Git history, closed Issues/PRs, or `docs/history/` when the repository uses one.
- `SPEC.md` is the repository execution contract. Proceed inside an ACTIVE approved scope and stop on a genuine safety, scope, authorization, repository-identity, access, or validation failure.
- Prefer one cohesive PR with related phases/tasks over micro-PRs. Small isolated fixes may remain small.
- When the current objective is known, short continuation such as `go`, `g`, `.`, `Y`, or `yes` means execute/continue it within existing authority unless Amit explicitly selected plan/review/discussion mode.
- Before cross-repo mutation, confirm the target repository matches `CONTEXT.md` and the owning Issue/PR.

## Chat Restart Rule

Chat sessions are temporary working context; GitHub is durable project truth.

Before abandoning a long chat or after a major milestone, ensure `CONTEXT.md` and the active Issue/PR reflect the current state. A fresh ChatGPT session should normally be able to continue with:

`@GitHub Read AGENTS.md, CONTEXT.md, active Issue/PR and continue.`

Do not create `BOOTSTRAP.md`, transcript summaries, or handoff files when the same state is already represented by `CONTEXT.md` plus the active Issue/PR.

## Global Guidance

When available, use `~/.agent/CORE.md` as the shared machine-wide operating contract and `~/.agent/HOST.md` for active host facts. Tool homes such as `~/.codex/` remain tool-specific adapters/runtime state.

Agent OS is reusable guidance, never automatic project authority. Current user instruction plus this repository's `AGENTS.md`, `SPEC.md`, owning Issue/PR, and project context take precedence.
