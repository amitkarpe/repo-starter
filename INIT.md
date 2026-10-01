# Initialization

Status: NOT_INITIALIZED

Use this file only for first-time repository setup or when Amit explicitly asks to reinitialize the project.

## Short Interview

Ask only what is still unknown, normally 3-7 questions:

1. What problem, product, learning goal, or operational outcome does this repository own?
2. Is the context `PERSONAL` or `WORK`?
3. Which environment applies: `LOCAL`, `LAB`, `DEV`, `NONPROD`, or `PROD`?
4. What runtime, cloud, major tools, profiles, or external services are required?
5. What is the first useful milestone/outcome?
6. What hard boundaries or approval gates matter, if any?
7. Is there enough uncertainty about the external technology/solution space or the current repository/runtime/environment that brief research or discovery could materially change the project intent?

Prefer discovering answers from existing repository/runtime truth before asking Amit.

## Research / Discovery Gate

Use this only when question 7 is materially true:

- **Research** is outside-in: current capabilities, official patterns, alternatives, constraints, and reusable solutions.
- **Discovery** is inside-out: actual repository/runtime/environment truth such as topology, versions, configuration, integrations, and dependencies.
- Do the minimum useful investigation, distinguish verified facts from assumptions, and use the result to refine the project intent before initialization is finalized.
- Skip this gate for bounded work whose technology and current state are already sufficiently known.
- Do not create mandatory research/discovery files; preserve only findings with continuing value.

## Initialize

After the interview, update only the files that need project-specific truth:

- `README.md` — purpose and start-here guidance
- `CONTEXT.md` — repository identity, current truth, active work
- `SPEC.md` — execution authority, scope, milestones, stop gates
- `ENV.md` — project runtime/tool/cloud dependencies
- `ROADMAP.md` — only useful future milestones

Then set this file to:

`Status: INITIALIZED`

Do not repeat the interview on normal future work. Reinitialize only when Amit asks or the repository's fundamental purpose/context changes.
