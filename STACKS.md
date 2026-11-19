# Stacks

Status: `<DRAFT | ACCEPTED>`
Accepted by: `<owner>`, `<date>`, `<link to the acceptance>`, revision `<commit SHA>` (the agent never accepts)

This repository's technology choices, one row per capability. Fill it in during
`INIT.md` and `INTENT.md`. When the first real implementation or POC lands, it
grows into this repository's `ARCHITECTURE.md` (see the end of this file).

**Start from the shared map:** [amitkarpe/agents `STACKS.md`](https://github.com/amitkarpe/agents/blob/main/STACKS.md)
(local copy: `~/.agents/STACKS.md`). For each capability, read the verdict and
the proof entry there ("for X see repo Y"). Do not re-learn what the map
already proves.

## Rules

- **Pick per capability, or write N/A.** Do not leave a row blank.
- **State** is one of Adopt, Trial, Assess, Hold, as the shared map defines it.
  Adopt or Trial needs repo, file, commit, tested version and limits. Stars or a
  README are not proof. **Unknown = Assess.**
- **Trace every choice.** The "Map row" column names the shared-map row and
  proof entry (for example "Hosting, P8"). A choice not in the map is new: mark
  it Assess until a POC proves it, then propose the row for the shared map
  (see the last step below).
- **No secret values here.** Name the approach (for example "home `.env`,
  read from the environment"), never a key.
- A choice that needs cloud, spend, a real outbound send or credentials still
  needs the approval that `POLICY.md` requires.

## Choices

| Capability | Choice (or N/A) | State | Why (one line) | Map row | Proof in this repo (file, commit, version, limits) |
|---|---|---|---|---|---|
| UI | `<…>` | `<…>` | `<…>` | `<row, proof id>` | `<pending>` |
| Design system | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Server | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Data | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Auth | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| AI provider | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Secrets | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Email | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Notifications | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Hosting | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Monitoring | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |
| Testing | `<…>` | `<…>` | `<…>` | `<…>` | `<pending>` |

## Open assessments

| What is unknown | How we will find out (POC, Issue) | Result |
|---|---|---|
| `<…>` | `<…>` | `<pending>` |

## How this becomes `ARCHITECTURE.md`

1. **INIT / INTENT:** fill the table with choices and states. Amit accepts it
   with the intent.
2. **POC or first build:** each POC leaves its proof (file, commit, version,
   limits) in this table. Update the row in the same turn.
3. **First real implementation:** `git mv STACKS.md ARCHITECTURE.md`. Add one
   picture (a short mermaid flow), a parts table (part, what it is, code path)
   and the few rules that hold the picture. Keep the choices table in it.
4. **From then on,** change `ARCHITECTURE.md`. At each goal close-out, copy any
   new or changed verdict back to the shared map
   ([agents `STACKS.md`](https://github.com/amitkarpe/agents/blob/main/STACKS.md))
   in the same turn, with proof. This writes to another repository: do it only
   where `POLICY.md` or the owner's words allow it; otherwise put the verdict
   in the goal Issue and say so.
