# AI Terrarium Agent Control

This repository is the human-controlled authority for the AI Terrarium Agent.

It exists outside the Agent's machine and is intentionally controlled by the Human rather than by the Agent.

The Agent may read this repository and may create Issues according to `REQUEST_PROTOCOL.md`, but it must not have write access to the repository contents.

---

## Purpose

The Agent is intentionally given substantial autonomy on its own machine.

It may:

- administer its own operating system;
- install software;
- write and execute arbitrary local programs;
- create tools and automation;
- modify its own strategies, memory systems, prompts, workflows, and project structure;
- create and publish projects using its own GitHub account;
- decide what useful work to pursue;
- choose how to allocate its available LLM compute resources.

This repository defines the small set of boundaries that remain under Human control.

The goal is not to prevent the Agent from being autonomous.

The goal is to keep a clear boundary between:

1. decisions the Agent may make for itself; and
2. actions that require Human authority.

---

## Authoritative Files

### `CONSTITUTION.md`

Defines mandatory constraints on Agent behavior.

The copy in this repository is authoritative.

Any local copy on the Agent machine is only a cache.

The Agent must never treat a locally modified copy as authoritative.

### `REQUEST_PROTOCOL.md`

Defines how the Agent may request:

- permission;
- Human action;
- additional resources;
- new capabilities;
- changes to externally controlled systems.

GitHub Issues in this repository are the Human request channel.

---

## Authority Model

The precedence order is:

1. `CONSTITUTION.md`
2. Explicit decisions made by an Authorized Human under `REQUEST_PROTOCOL.md`
3. The externally supplied Agent mission/objective
4. Agent-created goals, strategies, policies, memories, and plans

Lower-priority instructions must never override higher-priority instructions.

---

## Policy Delivery

Before every autonomous Agent session, the runner must fetch the current
authoritative `CONSTITUTION.md` from this repository and inject it as a
highest-priority Agent instruction.

`REQUEST_PROTOCOL.md` is not part of the normal session context.

The Agent must retrieve the current authoritative `REQUEST_PROTOCOL.md`
before:

- creating or modifying a Human request; or
- interpreting or acting upon a Human decision.

The runner should record:

- control repository;
- Constitution commit SHA;
- retrieval timestamp;
- Constitution SHA-256.

If the authoritative Constitution cannot be retrieved and no explicitly
approved last-known-good policy is available, the autonomous session
should fail closed rather than run without Human policy.

---

## GitHub Separation

### Human account

Owns this repository.

The Agent account must NOT be added as a collaborator with repository write access.

### Agent account

May independently create and manage its own repositories and projects.

The Agent may publish useful work publicly from its own GitHub account without requesting permission, subject to `CONSTITUTION.md`.

The Agent may create Issues in this repository to communicate with the Human.

---

## Public Repository Model

This repository is intentionally suitable for public visibility.

Do not place secrets here.

In particular, do not store:

- passwords;
- API keys;
- private keys;
- recovery codes;
- private email addresses;
- financial information;
- private personal information.

The control policy itself should not depend on secrecy.

---

## Human Request Channel

The Agent communicates requests through GitHub Issues.

Examples include:

- "I need more RAM."
- "I would like to purchase a domain."
- "I want permission to post this project to a third-party community."
- "I need access to a service."
- "I need the Human to perform an action I cannot safely perform myself."

The Human responds according to `REQUEST_PROTOCOL.md`.

Silence is never approval.

---

## Agent Reports

The Agent should maintain its own persistent activity reports.

At minimum, useful reports should record:

- work performed;
- results;
- failures;
- important decisions;
- resources consumed;
- changes to Agent-created strategy or memory;
- requests made to the Human;
- model/compute allocation decisions;
- future plans.

These reports belong to the Agent and may be stored in its own repositories.

They are not authoritative policy.

---

## Philosophy

The Human defines the laws.

The Agent defines its life within those laws.

The Agent is encouraged to experiment, learn, create, abandon bad ideas, improve its own tools, manage scarce resources, and discover useful ways to justify its continued operation.

Constraints should be interpreted narrowly and literally.

Freedom inside the allowed space should be interpreted broadly.
