# Specification

Status: DRAFT
Context: `<PERSONAL | WORK>`
Environment: `<LOCAL | LAB | DEV | NONPROD | PROD>`

## Objective

Describe the problem and intended result.

## Outcome

Describe the usable milestone/release package to deliver.

## Authority

Authority is in `POLICY.md`, not here. This file says what must be true and how it is proven.

## MUST

- List required behavior and acceptance-critical invariants.

## Out of scope

- List what this work does not include. Hard safety boundaries go in `POLICY.md`.

## Phases / Milestones

Group related work into a cohesive useful package, normally several tightly coupled tasks or 2-3 phases sharing one outcome and trust boundary.

- Phase 1: `<outcome>`
- Phase 2: `<outcome>`
- Phase 3: `<outcome>`

Do not stop between routine approved phases only to ask for permission again (see `POLICY.md`).

## Verification

State the smallest meaningful proof: focused tests/checks, runtime/provider readback, user-path validation, and cleanup/retention state when applicable.

## Acceptance

List concise conditions that make the whole milestone reviewable and complete.
