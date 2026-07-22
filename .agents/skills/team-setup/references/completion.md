# Completion and resume states

Use this reference before pausing, handing off, or declaring setup complete.

Choose exactly one state in this order:

1. `operational` when every operational condition is verified.
2. `model_ready_partial` when the model is reviewable but a measurement or other declared prerequisite prevents a valid OKR or operational Project.
3. `model_ready` only when every Model ready gate, including required Concept publication, is satisfied.
4. `waiting_for_human` when an earlier gate is blocked by a human-only action.
5. `in_progress` when the agent can continue safely.

Record a human action separately under Waiting for human even when the selected milestone is `model_ready_partial`. The milestone states model completeness; the waiting field states who must act next.

## State definitions

### in_progress

The agent can continue safely without new human authority or external state.

### waiting_for_human

A blocking Ask, Concept publication, sensitive Entity mutation, member assignment, or other human-only action is outstanding.

Before stopping:

- update `PROJECT.md` current phase and Waiting for human;
- identify the exact resource or action;
- state why it blocks and what remains non-blocking;
- tell the human how to resume the agent after acting.

### model_ready_partial

The Team model and intended outcome are reviewable, but a measurement bootstrap Project or another explicit prerequisite prevents a valid OKR or operational Project.

### model_ready

Confirmed Entity state, intended outcome, problem choice, a valid OKR definition, and Project candidates are reviewable by the sponsor. Every Direction / Guardrail Concept that materially shapes or constrains that OKR is published; auxiliary proposals may remain pending as non-blocking work.

### operational

All conditions hold:

- required normal Entities are registered and reread;
- blocking sensitive Entity actions are verified;
- Direction / Guardrail Concepts that materially shape or constrain the OKR are published;
- a valid draft OKR exists with 2–5 KRs;
- the first Project exists with target KR and solution hypothesis;
- required human members are present;
- the first session brief and verification point are ready;
- remaining work is explicitly non-blocking.

## Canonical verification

Never infer completion from prior tool responses or checklist text. Reread the relevant Company, Concept, OKR, Project, Ask, and membership state.

## Handoff

Use `templates/setup-handoff.md`. Link to canonical resources rather than copying Registry content. Separate:

- achieved milestone;
- registered and published state;
- pending review;
- human actions;
- measurement or data prerequisites;
- next Project action and responsible party.

Close the setup Project only when the sponsor accepts the milestone and no setup-specific blocking action remains.
