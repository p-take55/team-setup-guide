# Concept modeling

Use this reference for Concepts. Read the projected `aachat-concepts` skill before reading or proposing; it owns the current kinds, semantic axes, sources, similarity gate, relations, and review lifecycle.

## Discover meaning through three channels

Use all relevant channels without demanding all three for every Concept:

- Declared intent: what an authorized human chooses for the Team now.
- Revealed practice: priorities exposed by real choices, sacrifices, exceptions, and investment.
- Observed reality: problems and learning from customers, metrics, incidents, and experiments.

Ask humans directly when current intent is missing. Do not turn kind names into a questionnaire. Useful direct questions include the desired change, current focus and deliberate exclusions, tradeoff priority, non-negotiable constraints, and important uncertain beliefs.

## Reconstruct implicit judgment

When history matters, reconstruct decision episodes:

```text
situation → real options → choice → sacrifice → stated reason → outcome → authority → source
```

Do not invent an unstated reason. Across episodes, look for repeated tensions and form a candidate judgment model:

```text
In [context], prefer [choice] over [alternative] because [reason].
This does not apply when [boundary].
```

Stress-test it with the opposite choice, other episodes, counterevidence, scope boundaries, and authority. Ask the human about unresolved contradictions rather than asking them to select a Concept kind.

## Balance coverage and restraint

After discovery, check that relevant meaning is understood across:

- Direction: why the Team exists, its promise, direction, and goals;
- Guardrails: principles, policies, and consequential decisions;
- Learning: problems, questions, hypotheses, findings, and important metrics;
- Response: ideas and concrete solution candidates.

This is a coverage check, not a one-Concept-per-kind quota. Explain each important gap as covered by an existing Concept, needing a proposal, waiting for a human, or irrelevant to this setup.

Merge candidates with the same decision value. Keep Project-local details in project docs. Prefer an existing Concept, change proposal, or meaningful link over a duplicate new Concept.

## Classify only after meaning is clear

The projected `aachat-concepts` contract is authoritative for the current enum and semantic axes. Use these kind meanings after discovery:

| Area | Kind | Meaning |
|---|---|---|
| Direction | `purpose` | Why the Team exists |
| Direction | `value_proposition` | Who is promised what distinctive value |
| Direction | `strategy` | A choice of focus and deliberate exclusion for an outcome |
| Direction | `goal` | A reusable desired state or direction, without the OKR measurement contract |
| Guardrails | `principle` | A judgment heuristic used when values or options conflict |
| Guardrails | `policy` | An explicit rule or non-negotiable constraint |
| Guardrails | `decision` | A consequential choice an authorized human has adopted |
| Learning | `metric` | A measurement dimension the Team repeatedly watches |
| Learning | `problem` | An evidence-backed problem worth solving |
| Learning | `question` | An unresolved Team-wide question worth carrying across Projects |
| Learning | `hypothesis` | A falsifiable but unverified belief |
| Learning | `finding` | An evidence-backed observation or learning |
| Response | `idea` | An unevaluated possibility |
| Response | `solution` | A concrete response candidate to a problem |

A `principle` guides tradeoffs while a `policy` sets a rule. A `problem` is established enough to own; an unverified explanation remains a `hypothesis`. A `finding` reports supported observation, while a `decision` records human choice. A Project Ask is not a `question` Concept unless the question itself must persist Team-wide. An `idea` becomes a `solution` only when it is framed as a concrete response to a problem. Do not duplicate an OKR's period, baseline, target, owner, or Check-ins as a `goal` or `metric` Concept.

## Propose correctly

- Choose kind only after the meaning is stable.
- Choose scope, abstraction, horizon, guidance, and maturity independently.
- A direct human declaration may supply the meaning through a `human_decision` source, but the mutation also requires a Project-scoped source such as the current session.
- Preserve observation uncertainty; do not promote a hypothesis to a finding.
- Follow the similarity response instead of forcing creation.

## Publication gate

Proposal creation yields pending review. Block the Outcomes phase when an unpublished Direction or Guardrail materially changes the OKR's meaning or constraints, regardless of its `guidance_strength`. Auxiliary pending Concepts may remain non-blocking. Concept publication is a human action; route it to the named Team Owner / Admin Registry steward and reread the published revision afterward.

Add Entity `realizes` and OKR Concept links only after publication. On resume, reread the Concept and review state before linking.
