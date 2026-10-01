# AI-Native SDLC v1

Status: PROPOSED  
Applies to: repositories created from `repo-starter`

## Principle

Use the AI-native lifecycle:

```text
Intent -> Spec -> Plan -> Code -> Tests/Evals -> PR/Review -> Deploy -> Observe -> New Intent
```

Human input should stay focused on outcome, constraints, approval boundaries, and meaningful review. AI should derive detailed requirements, implementation plans, code, tests, documentation, and evidence. Keep the process proportional: artifacts exist to improve correctness, safety, reproducibility, and continuation — not to create ceremony.

## Ten Contracts

1. **Purpose** — `README.md` states why the repository exists, who it serves, and its important non-goals.
2. **Intent** — meaningful work starts from the originator's problem, desired outcome, constraints, assumptions, and open questions.
3. **Specification** — AI converts approved intent into reviewable requirements, interfaces, environment assumptions, safety boundaries, and acceptance criteria.
4. **Plan** — before significant implementation, define the change sequence, dependencies, validation, failure handling, rollback, and retained state.
5. **Git is complete** — runtime work on EC2, Docker, AWS, local hosts, or other systems is not complete until the code, IaC, configuration, scripts, and instructions needed to reproduce it are committed.
6. **Deterministic execution** — AI may reason probabilistically, but repeatable build, deploy, validation, remediation, cleanup, and promotion paths should graduate into repo-owned scripts, IaC, CI/CD, or provider-native automation.
7. **Tests and CI** — prove the smallest meaningful acceptance surface, including representative negative/failure cases. CI proves repeatability of the revision; test count is not the objective.
8. **Safety and authority** — identity, repository, account, environment, target, permissions, mutation boundary, approval, cost, rollback, and cleanup must be explicit where relevant. Read first, change second; fail closed on uncertainty.
9. **Evidence** — "done" requires revision + relevant tests + runtime/provider readback when state matters + acceptance result + cleanup/retention state. A successful command alone is not proof of the desired outcome.
10. **Learning** — every meaningful escaped failure asks: "What permanent check would have prevented this?" Add the regression locally first; promote repeated cross-repo lessons to `repo-starter`, Agent OS, or a reusable skill.

## Artifact Rule

Artifacts are selected by risk and complexity, not by task size alone.

| Work type | `intent.md` | change `spec.md` | `plan.md` |
|---|---|---|---|
| Tiny/local fix | Optional | Optional | Optional |
| Meaningful feature or milestone | **Required** | Required when requirements/interfaces/acceptance need durable review | Required when sequence, dependencies, rollback, or multiple implementation steps matter |
| High-risk work: AWS/PROD/IAM/network/security/data/destructive/material-cost/trust-boundary | **Required** | **Required** | **Required** when multi-step, rollback-sensitive, operationally complex, or dependent on external state |

### Exact skip rule

A tiny/local fix may use the owning GitHub Issue/PR as both intent and plan when all of the following are true:

- one bounded outcome;
- no new trust/security boundary;
- no PROD, IAM, network, destructive, sensitive-data, or material-cost change;
- no material architecture/design decision;
- implementation and rollback are obvious;
- acceptance can be expressed directly in the Issue/PR.

Do not create empty `intent.md`, `spec.md`, or `plan.md` files merely to satisfy a template.

If an artifact is skipped, the owning Issue/PR must still preserve the information needed to execute and review the work safely.

## Change Artifact Layout

For meaningful work, use:

```text
intent/<change>/
  intent.md
  spec.md      # when required
  plan.md      # when required
```

`intent.md` preserves the originator's intent; AI may structure it, but must not silently replace the desired outcome.

The change-specific `spec.md` defines what must be true for that change. It does **not** replace the root `SPEC.md`, which remains the repository-level execution, authority, and safety contract.

The change-specific `plan.md` defines how the approved specification will be implemented and proven. It is not a second roadmap.

## Default Execution Loop

```text
Amit / originator brain dump
  -> capture intent
  -> AI derives specification
  -> human reviews outcome + boundaries
  -> AI derives implementation plan
  -> code / IaC / configuration
  -> focused tests and CI
  -> deploy or runtime validation when relevant
  -> provider/readback evidence
  -> PR review
  -> cleanup / retained-state record
  -> escaped failure becomes a regression or reusable rule
  -> next intent
```

GitHub Issue/PR remains the normal workflow, authority, coordination, and evidence plane. Context loading stays event-driven: use the owning Issue/PR, current HEAD/diff, and only the governing files relevant to the task.

## References

- https://claude.com/blog/the-ai-native-sdlc-playbook
- https://academy.claude.com/courses/ai-native-sdlc-playbook
- https://academy.claude.com/courses/ai-native-sdlc-playbook/capture-intent
- https://academy.claude.com/courses/ai-native-sdlc-playbook/requirements-and-design
- https://academy.claude.com/courses/ai-native-sdlc-playbook/plan-mode
