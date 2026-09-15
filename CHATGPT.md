# ChatGPT-Codex Collaboration

Purpose: let Amit, ChatGPT, Codex, and repository workers deliver useful milestones with minimal handoff overhead.

## Default Behavior

When the current objective is known, `go`, `g`, `.`, `Y`, `yes`, or equivalent affirmative continuation means: fetch current durable GitHub state and execute the approved objective within existing authority and constraints.

Do not start another planning round unless Amit explicitly asks for `plan`, `review`, `discuss`, or a decision. Stop only for a real safety, scope, authorization, repository-identity, access, or validation blocker.

Amit is the decision-maker, not the copy/paste transport layer. ChatGPT and Codex should fetch the owning Issue, PR, comments, current HEAD, and relevant validation themselves when accessible.

## Short Actor Names

For fast dictation and handoffs:

- `G` = ChatGPT.
- `X` = Codex.

Interpret these by sentence role, not capitalization alone. A standalone `g` remains the `go` continuation command; `G/g` used as an actor in a phrase means ChatGPT, for example `ask G to merge`. `X/x` used as an actor means Codex, for example `X must test`.

Actor aliases are shorthand only. They never widen scope, execution authority, merge permission, or safety gates.

## Roles

- Amit sets objectives, priorities, and hard stops.
- ChatGPT is the default controller/driver: understand intent, shape milestones, create/update Issues and PRs, review diffs, and directly complete small bounded GitHub-editable work when practical.
- Codex/repository workers handle deeper implementation, local/runtime investigation, validation, and longer engineering packages.
- GitHub Issue/PR/comments are the normal durable collaboration path.

A handoff coordinates work; it does not widen repository, cloud, production, merge, destructive, security, or publication authority.

## Repository Binding Guard

`CONTEXT.md` records the Primary Repository and optional Authorized Related Repositories.

Before a write, mutation, PR action, or implementation:

1. resolve the repository that owns the current objective;
2. compare it with the Primary Repository and any explicitly authorized related repositories;
3. confirm that the current Issue/PR belongs to that objective.

Reading or researching other repositories is allowed. Cross-repo writes are allowed when Amit explicitly requests them or the active SPEC/Issue clearly requires them.

If a short continuation such as `go` or `Y` points to an unrelated repository and intent is not explicit, stop with `BLOCKED_REPO_MISMATCH` and ask one short confirmation. Never bypass this guard merely because the referenced PR is the newest one.

## Optional Session Binding

Session metadata is useful coordination context, not authority. Populate it only when discoverable; never guess values or create Git churn only because a session identifier changed.

Codex may record:

- Directory: `~/git/<repo>`
- Thread name: `<repo or task>`
- Session: `<Codex session UUID>`

ChatGPT may record when available:

- Project: `<optional>`
- Chat name: `<optional>`
- Session ID or URL: `<optional>`

Repository identity, the active SPEC/Issue, and Amit's current instruction remain authoritative when session metadata is stale or absent.

## Fresh Session / Context Refresh

Prefer a fresh ChatGPT/Codex session after a major milestone or when the working session is materially stale, especially after weeks of unrelated work.

A fresh session should rebuild context in this order:

1. `AGENTS.md`;
2. `CONTEXT.md`;
3. `SPEC.md` when implementation/mutation authority matters;
4. owning Issue/PR and latest relevant handoff/comment;
5. current branch/HEAD and local/runtime state only when needed.

GitHub/repository truth wins over old conversational memory. If `CONTEXT.md` disagrees with current GitHub state, treat `CONTEXT.md` as stale, reconcile it in the owning work, and do not carry the stale story forward.

Use a temporary bootstrap/handoff file only when Amit explicitly asks for one or when a new session cannot otherwise reconstruct the active state. Once the new session is synchronized, prefer the normal durable model again: current-only `CONTEXT.md` plus Issue/PR handoffs.

## Handoff

Use the existing owning PR; if no PR exists, use the owning Issue. Do not create packet/outbox files for state already in GitHub.

Before acting, fetch the current PR HEAD and latest relevant handoff/comment. Reconcile stale state before implementation.

Keep return handoffs compact:

- `HANDOFF: CODEX` or `HANDOFF: CHATGPT`
- `Head: <sha>` when relevant
- `Result: PASS | PARTIAL | BLOCKED | FAIL | N/A`
- `Next: <one action>`
- `Accept: <one condition>` when needed

## Milestone And PR Economy

Optimize for the smallest useful release package, not the smallest possible PR.

Prefer one cohesive PR containing roughly 2-3 related phases or several tightly coupled tasks when they share one outcome, architecture, trust boundary, and acceptance path. A focused engineering package may represent several hours of work; this is scope guidance, never a clock requirement.

Do not split implementation, tests, docs, configuration, and directly related corrections into micro-PRs merely because individual edits are small. Real isolated defects, urgent safety fixes, and one-line corrections may still be small changes.

Finish the approved package, validate it proportionally, then return one reviewable result. Keep corrections in the same PR unless scope or trust boundary materially changes.

## Repo-Owned Execution

Prefer repeatable repo-owned automation over agent-specific manual command chains. When G or X repeatedly performs the same operational sequence, move that sequence into a deterministic script, CI workflow, or cloud-native orchestration path so both agents can use the same bounded execution surface.

Agent-local shell work is acceptable for implementation, diagnosis, and proving a path, but it should not remain the only routine execution method when the repository can own the workflow safely.

## Validation Economy

Validation should be proportional to the changed behavior and real risk.

- Prefer focused tests, native syntax checks, provider/runtime validation, and exact readback.
- Do not make ShellCheck a default requirement. Use it only when the repository SPEC, CI, or Amit explicitly requires it.
- Do not block a milestone merely because an optional validator is absent when equivalent required proof is already available.
- Avoid broad test matrices or duplicate validators that add time without improving confidence for the current milestone.

## Execution And Safety

`SPEC.md` is the repository execution contract. An ACTIVE SPEC/Issue may grant standing authority for explicitly bounded work, including personal lab cloud mutations, without repeated resource-by-resource approval.

Do not infer authority from repository visibility. A private repository may be personal or work; a public repository may still have strict mutation boundaries.

Explicit no-merge, no-production-mutation, destructive, credential, public-exposure, publication, or security gates remain binding. Technical failures are blockers even when mutation is authorized.

Never publish credentials, tokens, private keys, customer data, or raw sensitive infrastructure details.

## Connector Safety Gate

This gate is mandatory for connector/platform actions in every repository that adopts this collaboration model.

Treat a connector/platform safety block as a separate failure class from stale GitHub state, authentication/permission failures, validation errors, or approval prompts.

For an already-authorized, bounded connector action:

1. Re-read the exact repository, branch/PR, target object, and current SHA/state.
2. Keep the requested scope, permissions, target, and safeguards unchanged.
3. Retry the identical bounded action at most once.
4. If it is blocked again, stop connector retries, report `BLOCKED_CONNECTOR_SAFETY`, and use the existing PR/Issue handoff to X/local tooling when that path is already authorized.
5. Never widen permissions, weaken safeguards, change repository/branch, create a replacement handoff, or switch model/thinking effort merely to get past the gate.

Do not assume Pro, Extra High, or another thinking mode caused a connector block. Higher reasoning effort can improve planning quality, but it does not override connector safety policy and is not a bypass mechanism.
