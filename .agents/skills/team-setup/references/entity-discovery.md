# Entity discovery

Use this reference for Scope and Entities. Read the projected `aachat-company` skill before Registry operations; its current enum and mutation contract are authoritative.

## Establish scope

Confirm:

- setup root and whether the target is a company, business, product, or team subtree;
- included and excluded areas;
- setup sponsor who can confirm facts and make tradeoffs;
- Registry steward who is a Team Owner / Admin and can publish Concepts and manage `person`, `partner`, and `agreement`;
- source material the sponsor authorizes the agent to read.

Start with the Company root overview, then focus only on relevant subtrees. Do not fetch the whole Registry by default.

## Find candidates

Look for stable components of the Team, not every noun in a document. Exclude tasks, campaigns, KPIs, responsibilities, relationships, and temporary work unless they independently qualify as a supported Entity kind.

For each candidate verify:

| Field | Test |
|---|---|
| Name | Is this the formal or durable identifying name? |
| Kind | Does exactly one supported kind express what it is? |
| Status | Does `planned / current / retired` describe company composition rather than work progress? |
| Parent | Is this the one primary structural parent, not ownership, use, dependency, or responsibility? |
| Evidence | Can the sponsor or an authorized source confirm existence and classification? |
| Existing match | Is the same stable identity already present under another name? |

Do not invent a kind or encode missing relations into names and hierarchy. Prefer no parent over a false parent.

## Confirm in small batches

Group ambiguous candidates by one shared fork. Show confirmed facts and ask only what changes registration.

Allow the sponsor to choose `decide later`. Keep that candidate unregistered and record it as non-blocking unless a later link or OKR requires it.

## Register and verify

- Register supported non-sensitive Entities with stable nonces.
- Never mutate `person`, `partner`, or `agreement`. Ask a human to use the management surface.
- An Ask answer is not proof that the human mutation occurred. Reread Company state.
- Reread the affected subtree after every batch and check duplicates, active children under retired parents, and wrong hierarchy.
- Link `realizes` only to published Concepts and only when the Entity structurally realizes that shared meaning.

## Output

Create a verified inventory only after rereading canonical state. Keep unresolved guesses out of it. Classify each outstanding human action as blocking or non-blocking.
