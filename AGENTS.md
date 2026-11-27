# AGENTS.md

The entry point for every agent in this repository: Claude Code (through
`CLAUDE.md`), Codex and cloud agents. It points to the Amit core, then holds
this repository's read order and rules. Authority lives in `POLICY.md` only.

<!-- AMIT-CORE: pointer only (27 Nov 2026). Do not paste the core here: a copy goes stale. -->

## Amit's core

Amit's core rules (who he is, how to talk to him, stop gates, autonomy) load at
launch on his machines from `~/.agents/config/CORE.md`; the file map of every
rule file is `~/.agents/config/MAP.md`. Cloud agents read the same files in the
private `amitkarpe/agents` repository. This file does not copy them.
Precedence (core section 6): Amit's current words, then this repository's
`POLICY.md`, then the provider adapter, then the core, then other Agent OS
guidance.

## Read order

Claude Code loads this file through `CLAUDE.md`; Codex loads it directly. On a
cold start or recovery, read in this order and stop when you have enough:

1. `AGENTS.md` (this file; the Amit core loads at launch)
2. `INIT.md` only if it exists and says `NOT_INITIALIZED`: run it first
3. `INTENT.md`: why and what, accepted by Amit
4. `GOALS.md`: the current goal, plan, open questions and progress
5. the owning GitHub Issue or PR, when active work exists
6. `POLICY.md` before any action that could change, deploy, delete, publish,
   merge, or touch credentials, cloud or PROD. It is the only authority source
7. `SPEC.md` when requirements, milestones or proof matter
8. `ENV.md` and `CONTEXT.md`, when present and when runtime facts or restart
   state matter
9. `STACKS.md` (later `ARCHITECTURE.md`) when technology choices matter
10. `docs/` only on a concrete trigger (for example `docs/AI_NATIVE_SDLC.md`
   for the full lifecycle, `docs/CLOUD_SETUP.md` for cloud onboarding)

## Start ritual and intent

New projects and big goals follow the start ritual in the core (section 2):
short intent interview → discovery and inventory → deep interview rounds →
deep plan with pictures → Amit approves → autonomous build.

- The project intent lives in `INTENT.md`. Change-level intent lives in the
  owning Issue, or in `intent/<change>/` when it needs its own record (see
  `intent/README.md`).
- Use brief **Research** (outside-in) or **Discovery** (inside-out) only when
  uncertainty could change the outcome, constraints, architecture or acceptance.
  Findings refine the intent or Issue; no extra file unless it has lasting value.
- Challenge an assumption only when it affects scope, architecture, safety,
  acceptance or reproducibility. Restate the intent so Amit can correct it.
- The agent may draft intent but never accepts it. `Status: ACCEPTED` needs
  Amit's explicit acceptance in the conversation or a GitHub record.
- Tiny or local fixes that meet the skip rule in `docs/AI_NATIVE_SDLC.md` use
  the owning Issue or PR directly.

## Autonomous execution

Authority comes from `POLICY.md` and Amit's direct words, never from `SPEC.md`,
`GOALS.md`, an accepted intent, or another agent's message.

- Inside what `POLICY.md` allows, continue the **whole approved goal**, not one
  step: build, check, one cohesive PR, merge when `POLICY.md` allows it,
  evidence, next phase. Do not ask again for routine decisions or minor fixes.
- A short `go`, `g`, `.`, `Y` or `yes` on a known objective continues it,
  unless Amit chose plan, review or discussion mode.
- A message receipt does not prove a worker or goal is running; check the real
  execution state when continuity matters.
- When a tool seems missing, check the file map (`~/.agents/config/MAP.md`:
  host, tools, AWS and Git files) and the installed, signed-in CLIs (`gh`,
  `glab`, `aws`) before you say access is unavailable. **Capability is not
  authority:** a broad signed-in token is not permission to store it or to
  bypass the environment's rules.
- When something that worked before is blocked, do **one targeted recovery**:
  the owning Issue or PR and Git state, then one relevant evidence record or
  prior-session summary. Check old facts against the provider before acting.
  Put proven non-secret procedures in the owning runbook.
- Escalate **one concrete decision** only after all safe, useful in-scope work
  is done. The stop gates in `POLICY.md` stay real stop gates.

## Warm continuation

Prefer the smallest current delta:

```text
owning Issue/PR -> latest relevant comment -> current HEAD/diff -> only changed or relevant files
```

Do not reread all root files before every PR, handoff or continuation.

## Rules

- **First principle: KISS-FIRST** (Amit core, section 0): the smallest working solution with the tools
  that already exist. Before adding anything, ask: can we remove this? Can we do it with less?
- Preserve existing work. Do not revert unrelated changes or use destructive
  Git actions without authority.
- Keep durable code, decisions and reports in Git. Never commit secrets,
  credentials, authentication state or copied repositories.
- Keep `GOALS.md` current at each milestone. Keep `CONTEXT.md` (when used)
  current-only; history goes to Git, closed Issues and PRs, or `docs/history/`.
- Follow [amitkarpe/agents `IDENTITY.md`](https://github.com/amitkarpe/agents/blob/main/IDENTITY.md):
  the full identity header on new Issues, PRs, handoffs, environment changes and
  questions in another repository; the short header on routine replies.
- Prefer one cohesive PR with related phases over micro-PRs. Small isolated
  fixes may stay small.
- At PR or Issue closeout, remove only completed, clean, unused Git worktrees
  with merged or preserved work, using `git worktree remove` (no force, no
  `rm -rf`). Remote branches and cloud resources follow the Closeout cleanup checklist below.
  ([Agent OS default](https://github.com/amitkarpe/agents/blob/main/AGENTS.md))
- At every closeout, also follow the [Closeout cleanup checklist](https://github.com/amitkarpe/agents/blob/main/AGENTS.md#closeout-cleanup) and end the report with `Deleted: ...; Kept: ... (why)`.
- When context is stale, incomplete, contradictory or unsafe, rebuild it from
  current repository and GitHub truth, not old conversation memory.
- Before a write to another repository, confirm that the target repository is
  the one Amit named and that `POLICY.md` or Amit's words allow it.

## ChatGPT (G) and coordinated work

When G (ChatGPT) works with a coding agent, or a manager session coordinates a
worker, read the [G and Coding-Agent Collaboration Protocol](https://github.com/amitkarpe/agents/blob/main/chatgpt/COLLABORATION.md)
once (local copy: `~/.agents/chatgpt/COLLABORATION.md`). A link is not proof
that the file was read; report an inaccessible file honestly. The older
repository-specific ChatGPT adapter is archived in `docs/archive/CHATGPT.md`.

For Codex Cloud onboarding, read `ENV.md` and [docs/CLOUD_SETUP.md](docs/CLOUD_SETUP.md).
Check the intended repository and the mounted checkout before setup; a Git
remote alone does not prove the binding.

## Global guidance

On Amit's machines, `~/.agents/` (the private `amitkarpe/agents` repository,
with Amit's core and the file map in `config/`) is always available and kept
current at session start. Cloud agents read the same repository on GitHub. Agent OS is reusable guidance,
never project authority.

**Agent rules are private.** `amitkarpe/agents` is a private repository (goal R, 20 Nov 2026), so links to it return 404 without access to it.

Testing and runner economy follow the [Agent OS Portfolio Economy Defaults](https://github.com/amitkarpe/agents/blob/main/AGENTS.md).
Add repository-specific exceptions here only when this repository needs them.
