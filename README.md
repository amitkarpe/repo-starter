# <Project Name>

One sentence explaining the problem this repository solves.

## Start Here

For agents, `AGENTS.md` is the single entry point (Claude Code reaches it through `CLAUDE.md`). It carries a copy of the Amit core, so every agent, including cloud agents, knows how Amit works.

| File | Job | Needed |
|---|---|---|
| `README.md` | What this is, for people | Always |
| `AGENTS.md` | Agent entry: the Amit core, read order, rules | Always |
| `CLAUDE.md` | One line: `@AGENTS.md`, so Claude Code loads it | Always |
| `INTENT.md` | Why and what, accepted by the owner | Always |
| `POLICY.md` | The one authority source: allowed, needs the owner's word, not allowed, stop gates | Always |
| `SPEC.md` | Requirements and proof | Always |
| `GOALS.md` | The live goal, plan, questions for the owner, progress | Always |
| `ENV.md` | Runtime, tool and cloud facts | When needed |
| `CONTEXT.md` | Current state for restart across many sessions | When needed |
| `INIT.md` | One-time setup; moves to `docs/archive/` when done | New repos only |
| `intent/` | Change-level intent records | When a change needs one |
| `docs/` | Lifecycle (`docs/AI_NATIVE_SDLC.md`), cloud setup, runbooks, `docs/archive/` | On a trigger |

For optional laptop-free deployment of a Codex Cloud app, see [Cloud-first quickstart](docs/CLOUD_FIRST_QUICKSTART.md). It is a reference workflow, not an extra approval or bootstrap gate.

Cloudflare is an opt-in path: [six-file static starter](examples/cloudflare-static/README.md),
[owner onboarding and new-project checklist](docs/CLOUDFLARE_WORKERS_ONBOARDING.md),
and [release evidence / recovery receipt](docs/DEPLOYMENT_EVIDENCE.md). The template
provisions nothing and carries no provider credentials or active root deployment config.
Complete `INIT.md` first; the owner's `<app-name>.amitk.life` convention is optional
for other owners. Use native Git Builds only after the one owner integration gate.

Do not use this README as a second copy of the agent bootstrap policy.

## Template Model

One fact has one home. Authority lives only in `POLICY.md`; requirements in `SPEC.md`; the why in `INTENT.md`; the live work in `GOALS.md`. Files that are no longer used move to `docs/archive/`; nothing useful is deleted.

The Amit core is written once, in Amit's private dotfiles (`~/.config/agent/CORE.md`), and loads at every launch on his machines. `AGENTS.md` holds its public copy (between the `AMIT-CORE` markers) for cloud agents; refresh that block from `CORE.public.md` when the core changes.

Historical detail belongs in Git history, closed Issues/PRs, or `docs/history/` when needed — not in `CONTEXT.md`.

Reusable cross-project policy belongs in the canonical `amitkarpe/agents` repository, read locally from `~/.agents/` (kept current at session start), and should normally be referenced rather than recopied here. Machine-specific facts belong in the active `~/.config/agent/HOST.md` when available.

Preserve useful local knowledge. Context-loading economy means reading the right file at the right time, not deleting information.
