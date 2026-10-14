# AGENTS.md

## Agent Entry And Read Contract

`AGENTS.md` is the universal agent entry point. Use it to decide what else must be loaded; do not treat every repository file as mandatory context.

### Cold start / recovery

Use this order when the agent has no reliable current context, is recovering from stale/contradictory state, or governing context materially changed:

1. `AGENTS.md`
2. `INIT.md` when the repository is new, initialization may be incomplete, or the project purpose is not yet settled
3. the owning GitHub Issue/PR when active work exists
4. `CONTEXT.md` only when restart/current-state recovery is needed
5. `SPEC.md` when implementation, mutation, deployment, cleanup, authority, or safety boundaries matter
6. `ENV.md` when runtime, cloud, host, profile, or tool facts matter
7. `CHATGPT.md` when ChatGPT/Codex adapter or repository-binding details matter

If `INIT.md` says `NOT_INITIALIZED`, complete the first-intent bootstrap before significant implementation.

For Codex Cloud development-environment onboarding or recovery, read `ENV.md` and [the repository-owned setup guide](docs/CLOUD_SETUP.md) when relevant. Verify the task's intended repository, the managed environment's selected repository when observable, and the mounted checkout **before** project setup; a Git remote alone does not prove the managed binding. Follow adopted project-required readiness commands, not optional examples; report unconfigured and failed prerequisites without bypassing `INIT.md`'s intent gate.

### Intent Gate

For meaningful new work, do not jump from a vague request directly into implementation.

Use `intent/README.md` and the AI-native SDLC contract to:

1. inspect existing repository/runtime truth first;
2. ask only unresolved material questions, normally one question at a time;
3. use Research / Discovery only when uncertainty could materially change the intent;
4. challenge assumptions only when they affect scope, architecture, safety, acceptance, or reproducibility;
5. restate the proposed intent so the originator can correct it;
6. record explicit originator acceptance before deriving the governed Spec / Plan or starting significant implementation.

The agent may draft and structure intent, but it cannot self-approve it. Recording `Status: ACCEPTED` is allowed only when explicit originator acceptance exists in the owning conversation or GitHub record. Intent acceptance does not grant cloud, PROD, IAM, network, destructive, sensitive-data, or other mutation authority.

Tiny/local fixes that satisfy the skip rule in `AI_NATIVE_SDLC.md` may use the owning Issue/PR directly and skip a separate intent file or interview.

### Autonomous execution after intent acceptance

For an already **ACCEPTED** intent or a sufficiently bounded authorized Issue/Spec,
continue the **whole approved goal**, not one conversational step. A short
`go`, `yes`, or equivalent means execute the remaining in-scope work through
implementation, focused validation, one cohesive PR, and normal safe merge
where required checks and repository rules allow it. Do not request repeated
permission for routine engineering decisions, minor fixes, or a continuation
already authorized. A message receipt is not proof that a persistent worker or
native Codex Goal is running: verify execution state when continuity matters.

When an external tool seems unavailable, first inspect the task-relevant host
guidance (for example `~/.agent/HOST.md`, `GIT.md`, `GITLAB.md`, `AWS.md`)
and verify existing `gh`/`glab`/`aws` CLI availability, authentication,
target identity and permission. Missing MCP does not mean missing CLI.
**Capability is not authority:** an authenticated broad GitHub token is not
permission to store it as a persistent GitLab mirror credential or bypass the
active environment's mutation contract.

When blocked by a problem that previously worked, do **one targeted recovery**
from the owning Issue/PR and current Git state, then a relevant indexed
historical evidence/agent-memory record or prior-session summary. Verify old
facts against the present provider before acting. Promote proven non-secret
connection procedures to the owning runbook; do not dump session transcripts,
create duplicate memory manuals, or repeatedly rescan unchanged context.

Escalate **one concrete external decision** only after completing safe,
independently useful work. Credential/secret changes, unauthorized PROD,
destructive action, public exposure, widened IAM/architecture, material cost,
and unsafe uncertain execution remain real stop gates. An accepted intent never
silently approves such mutations.

### Warm continuation

Prefer the smallest current delta:

```text
owning Issue/PR
-> latest relevant authorized comment/delta
-> current HEAD/diff
-> only changed or relevant governing files
```

Do not reread all root context files before every PR, handoff, or continuation.

## Rules

- Follow KISS: optimize for one useful outcome, not the smallest possible task.
- For meaningful new work, before treating intent as ready, check whether external technology uncertainty or current repository/runtime/environment uncertainty could materially change the outcome, constraints, architecture, or acceptance. Use brief **Research** for outside-in uncertainty and **Discovery** for inside-out current-state uncertainty. Skip this gate when the work is bounded and sufficiently known. Findings refine the owning intent/Issue; no separate research/discovery artifact is required unless it has continuing value.
- Preserve existing work. Do not revert unrelated changes or use destructive Git actions without authority.
- Keep durable code, decisions, and reports in Git. Never commit secrets, credentials, authentication state, or copied repositories.
- Keep `CONTEXT.md` current-only. It is a recovery index, not project history.
- Update `CONTEXT.md` only when repository identity, current truth, active Issue/PR, blocker, or next action must be preserved for recovery.
- Move completed/history detail to Git history, closed Issues/PRs, or `docs/history/` when the repository uses one.
- Use `SPEC.md` as the repository execution/authority contract when the work needs one. Proceed inside an ACTIVE approved scope and stop on a genuine safety, scope, authorization, repository-identity, access, or validation failure.
- Prefer one cohesive PR with related phases/tasks over micro-PRs. Small isolated fixes may remain small.
- At PR/Issue closeout, inspect secondary Git worktrees and remove only completed, clean, unused checkouts with merged/preserved work and no active X/rollback dependency. Use native `git worktree remove` (no force/`rm -rf`); preserve dirty, active, unmerged or uncertain work. Batch safe cleanup when useful. Remote branches and cloud resources are separate authority. [Canonical Agent OS default](https://github.com/amitkarpe/agent-os/blob/main/AGENTS.md#portfolio-economy-defaults).
- When context is materially stale, incomplete, contradictory, or unsafe to reuse, rebuild it from current repository/GitHub truth instead of relying on old conversation memory.
- The Connector Safety Gate referenced in `CHATGPT.md` is mandatory for connector/platform actions.
- When the current objective is known, short continuation such as `go`, `g`, `.`, `Y`, or `yes` means execute/continue it within existing authority unless Amit explicitly selected plan/review/discussion mode.
- Before cross-repo mutation, apply the repository-binding guard in `CHATGPT.md`.

## Global Guidance

When available, use `~/.agent/CORE.md` as the shared machine-wide operating contract and `~/.agent/HOST.md` for active host facts. Tool homes such as `~/.codex/` remain tool-specific adapters/runtime state.

Agent OS is reusable guidance, never automatic project authority. Current user instruction plus this repository's local rules, applicable `SPEC.md`, owning Issue/PR, and project context take precedence.

## Portfolio Economy Defaults

Testing and runner economy follow the canonical [Agent OS Portfolio Economy Defaults](https://github.com/amitkarpe/agent-os/blob/main/AGENTS.md#portfolio-economy-defaults).

Keep the full reusable rule there. Add repository-specific exceptions here only when this repository genuinely needs them.
