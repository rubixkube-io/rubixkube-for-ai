---
name: knowledge
description: >-
  What RubixKube has recorded about the organization's systems and history: the knowledge
  graph of resources, incidents, RCAs, changes and people. Use when the person asks about a
  service's history, who worked on something, what fails most, or any question whose answer
  is in past incidents rather than live state.
---

## When to use

- "What's the history of the payments service?" / "Has api-gateway failed before?"
- "Who has dealt with the checkout incidents?" / "Which resources fail most?"
- "What do we know about node pool X?"

## Tools

- `search_knowledge(phrase, entity_type?, hops?, limit?)`: find a service, host, resource or
  person by name and see what it connects to. Each hit is the matched node, the nodes around
  it and the relations between them as sentences (`Incident:… AFFECTS Resource:…`).
  `entity_type` narrows to one kind: Service, Resource, Incident, RCA, Change, User.
- `ask_knowledge(question)`: one plain-words question, one short answer from the recorded
  history. Use it for questions across many things; use `search_knowledge` for one thing.
- From an incident, prefer `similar_incidents` and `what_changed` (see the `investigate`
  skill); they already know the incident's resources and fingerprint.

## How to answer

Say what the graph recorded and from when. It starts on 7 Oct 2026 and holds incidents, RCAs,
Tasks, changes, environments and people, not metrics or logs. For the current state of a
source call `environment_snapshot`; for one incident call `get_incident`. If the graph has
nothing, say so and offer `list_incidents`. Do not add to the graph from here; that is done
by RubixKube itself as incidents and RCAs happen.
