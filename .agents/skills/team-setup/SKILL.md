---
name: team-setup
description: Guide an aachat Team from initial scope and fact-based Company Entity discovery through human Asks, Concept proposals, draft OKRs, first Projects, and operational handoff. Use when setting up a new Team, onboarding an existing organization into aachat, rebuilding an incomplete Company Map, or resuming a team setup Project that is waiting for answers, Concept publication, measurements, or human-only actions.
---

# Team Setup

Build the smallest complete Team model that lets humans and agents make the next decision and start the first Project. Preserve facts, human decisions, and uncertainty in their proper aachat surfaces.

## Start or resume

0. Confirm that the session belongs to a setup Project. If no setup Project exists, do not mutate Team Registries; ask the human to start the Team Setup Discover template or explicitly choose a Project to hold the setup lifecycle.
1. Read the current Project's `PROJECT.md`.
2. Read the projected `aachat-session` contract before creating or editing any shared document.
3. Read existing open and answered Project Asks before creating another one.
4. Read the current Company, Concept, OKR, and Project state only where it can change the next action.
5. Determine the current phase from Registry state, not from checked boxes alone.
6. Continue the earliest blocking phase. Do not redo completed mutations.

If `PROJECT.md` does not yet identify the setup root, scope, exclusions, setup sponsor, and Registry steward who is a Team Owner / Admin capable of Concept publication and sensitive Entity operations, begin at Scope.

## Core loop

Run the same loop inside every phase:

```text
inspect → form a small candidate set → surface unresolved decisions → Ask if needed
        → apply confirmed mutations → reread canonical state → update handoff
```

Do not treat Ask as a single early phase. Distinguish blocking decisions from non-blocking backlog.

## Phase router

| Phase | Read | Gate |
|---|---|---|
| Scope | `references/entity-discovery.md` | Target root, scope, exclusions, sponsor, and Team Owner / Admin Registry steward are known |
| Entities | `references/entity-discovery.md` and projected `aachat-company` | Confirmed normal Entities are registered and reread; human-only actions are classified |
| Concepts | `references/concept-modeling.md` and projected `aachat-concepts` | Required proposals exist; Direction / Guardrail Concepts that materially shape or constrain the OKR are published |
| Outcomes | `references/okr-and-projects.md` and projected `aachat-okr` | A valid draft OKR exists, or a measurement bootstrap Project and resume condition exist |
| Initiatives | `references/okr-and-projects.md` | A human chose the first solution bet and its target KR is explicit |
| Bootstrap | `references/completion.md` | Project docs, human member action, first session brief, and handoff are ready |

Read the referenced file completely before acting in that phase. Read projected `aachat-ask` before creating or waiting on an Ask.

## Ask and pause

- Use Project Ask for decisions that outlive the current turn.
- Ask only after showing confirmed context, the unresolved fork, a recommendation when justified, and what happens after each answer.
- Allow `unknown / decide later` when it is a legitimate non-blocking outcome.
- Put only actions that stop the current gate under `Waiting for human (blocking)`; keep deferred reviews and follow-ups in `Non-blocking follow-up` without changing the setup to `waiting_for_human`.
- Project Ask answers do not automatically restart a session. Before stopping, update `PROJECT.md` with the Ask and tell the human to answer it and send the agent `回答したので続けて`.
- On resume, read the answer and canonical Registry state. Do not rely on remembered transcript context.

Use bounded Session Ask only when an answer is expected in the current turn and waiting is genuinely useful. Do not poll tightly.

## Lifecycle gates

- A Concept proposal is pending, not canonical. Never report it as published.
- Add Entity `realizes` and OKR Concept links only after the Concept has current published content.
- Block on publication only when the pending Direction / Guardrail materially changes or constrains the OKR or Project choice. Do not require `guidance_strength = governing`; carry auxiliary pending findings as explicit non-blocking work.
- A draft OKR still requires 2–5 fully defined KRs with baseline and target. If measurement is unavailable, create a measurement bootstrap Project first and mark the setup `model_ready_partial`.
- The agent may create a Project but does not claim that human member assignment, Concept publication, or sensitive Entity registration occurred. Reread after the human acts.

## Storage

- Keep canonical Entity, Concept, and OKR data in their Registries.
- Keep questions and answers in Project Asks.
- Keep project-specific decisions, verified inventories, and handoff in shared documents.
- Do not persist speculative candidate tables as settled shared documents.
- Use `templates/entity-inventory.md` only after facts are confirmed.
- Use `templates/setup-handoff.md` at Model ready and update it at Operational.

## Finish

Read `references/completion.md`. Report one of these states:

- `in_progress`
- `waiting_for_human`
- `model_ready_partial`
- `model_ready`
- `operational`

Never collapse waiting, pending, draft, or partial states into complete.
