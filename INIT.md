# Initialization

Status: NOT_INITIALIZED

Use this file only for first-time repository setup or when Amit explicitly asks to reinitialize the project. When initialization is done, move this file to `docs/archive/INIT.md`.

## First-Intent Bootstrap

A new meaningful repository starts with one durable project intent before significant implementation.

Follow the start ritual in the Amit core (`AGENTS.md`, section 2): a short intent interview, then discovery and inventory, then deep interview rounds with question cards (3–4 questions per card, several rounds, "🎤 I'll say it by voice" as the last option on each), then a deep plan with pictures for Amit to approve. Inspect repository and runtime truth before asking. Challenge an assumption only when it could change scope, architecture, safety, acceptance, or reproducibility.

Cover these areas only as needed:

1. What problem, product, learning goal, or operational outcome does this repository own?
2. Who will use, operate, review, or benefit from it?
3. What does success look like, including the first useful demo or milestone?
4. What already exists: code, repository, runtime, AWS resources, Docker environment, manual process, or prior proof?
5. What is in scope and explicitly out of scope?
6. What constraints matter: PERSONAL/WORK, environment, cost, time, technology, data, publication, security, or approvals?
7. What assumptions or open questions could materially change the direction?
8. What evidence would prove the result works repeatedly?
9. What mutation, rollback, cleanup, or retention boundaries matter?

Preserve the originator's words where they carry useful nuance. Distinguish verified facts from assumptions.

## Research / Discovery Gate

Before finalizing intent, ask whether unresolved uncertainty could materially change the desired outcome, constraints, architecture, or acceptance.

- **Research** is outside-in: current capabilities, official patterns, alternatives, constraints, and reusable solutions.
- **Discovery** is inside-out: actual repository/runtime/environment truth such as topology, versions, configuration, integrations, and dependencies.
- Do only the minimum useful investigation.
- Feed findings back into the intent; do not create a parallel authority source.
- Skip this gate when the technology and current state are already sufficiently known.
- Do not create mandatory research/discovery files; preserve only findings with continuing value.

## Record And Accept Intent

Write the project intent in the root `INTENT.md` (the template is there). Use `intent/README.md` for the interview protocol and the status rules. Change-level intent later goes in the owning Issue or `intent/<change>/`.

Then:

1. restate the proposed intent to the originator;
2. let the originator correct missing or wrong assumptions;
3. keep the record `DRAFT` until explicit originator acceptance exists;
4. only after that acceptance, record `Status: ACCEPTED` and the evidence/link for the acceptance.

An agent cannot self-approve intent. Intent acceptance confirms the desired outcome and boundaries; it does **not** authorize cloud, PROD, IAM, network, destructive, sensitive-data, or other mutation.

Read-only inspection, Research / Discovery, and repository-initialization documentation may occur before intent acceptance. Significant implementation waits for the accepted intent.

## Initialize Repository Contracts

After the first intent is accepted, update only the files that need project-specific truth:

Required:

- `README.md` — purpose and start-here guidance
- `INTENT.md` — the accepted project intent
- `POLICY.md` — authority: allowed with no approval, needs the owner's word, not allowed (with enforcers), stop gates. Replace every `<placeholder>`; a minimal file is fine. A "Text only" rule still binds and marks an enforcement gap
- `SPEC.md` — requirements, milestones, proof
- `GOALS.md` — the first approved goal, its plan and open questions

When needed:

- `ENV.md` — project runtime, tool and cloud dependencies
- `CONTEXT.md` — current state for restart, when work runs across many sessions

Keep `AGENTS.md` and `CLAUDE.md` as they are, apart from repository-specific rules. Future direction goes in GitHub Issues and `GOALS.md`, not a roadmap file.

Adopt the agent identity standard of [amitkarpe/agents `IDENTITY.md`](https://github.com/amitkarpe/agents/blob/main/IDENTITY.md): add the one line from its "Adopt it" section to `AGENTS.md` in this first PR (link it; do not copy the file).

Derive a change-specific spec or plan only when the proportional artifact rules in `docs/AI_NATIVE_SDLC.md` require them.

Then set this file to `Status: INITIALIZED` and move it to `docs/archive/INIT.md` in the same PR.

Do not repeat this bootstrap for normal future work. Meaningful later changes use the Intent Gate in `AGENTS.md`; tiny/local fixes may use the owning Issue/PR when they satisfy the skip rule.
