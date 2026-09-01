---
name: scaffold-docs
description: Scaffold or backfill a project's required documentation set (README, AGENTS, PRD, ARCHITECTURE, DECISIONS, specs) from scratch. Use when the user asks to create/initialize project docs, start a new project's documentation, set up the docs folder, or fill in a missing doc that the global standard requires.
---

# Scaffold Docs

Generate or backfill a project's minimum documentation skeleton according to the global "Project Documentation Minimum Structure (mandatory)" standard defined in `~/.claude/CLAUDE.md`.

## When to use (triggers)

- The user says "initialize docs / scaffold project docs / set up the docs skeleton / scaffold docs / backfill docs".
- The user starts a new project and needs README, AGENTS, PRD, ARCHITECTURE, DECISIONS, and specs laid out at once.
- The user finds a required doc missing and wants it filled in.

## Global constraints (from CLAUDE.md)

- Any project's documentation writing/update MUST satisfy this minimum structure.
- Each document has a clear, non-overlapping responsibility.
- README and AGENTS must NOT carry implementation details.

## Steps

1. Identify the project root and existing files (use `ls` / read the directory) to avoid overwriting docs that already exist.
2. If a file already exists, do NOT rewrite it wholesale; only append the missing required sections while preserving its original content.
3. Generate missing files from the templates below, filling in REAL, specific content — do not leave a blank template for the owner to guess.
4. Note on language: the language of the generated docs is determined by the user's conversation context — not locked to English. The skeleton below uses English headings for portability.
5. After finishing, list the created/updated files and briefly state each one's responsibility so the owner can verify.

## File templates

### README.md

```
# <Project Name>

<One sentence describing what this project is>

## What is this?
- Positioning:
- Core problem solved:

## Why does it exist?
- Background / motivation:

## How to install and run?
- Requirements:
- Install steps:
- Run / start:

## Current status
- Stage: prototype / in development / stable / maintenance
- Known limitations:

## Core tech
- Languages / frameworks / key dependencies:

> Note: README does not carry the project's full documentation duty; details live in docs/.
```

### AGENTS.md

```
# AGENTS.md

<One-sentence intro to help the Agent locate the project quickly>

## Overview
- What this project is:

## Boundaries and scope
- In scope:
- Non-Goals (explicitly out of scope):

## Agent operating guide
- How to understand this project:
- Global rules / conventions:

## Directory cheat-sheet
- <path> — <responsibility>
```

### docs/PRD.md

```
# PRD — <Product / Feature Name>

## Product goals
- Goals to achieve:

## Users and usage scenarios
- Target users:
- Typical scenarios:

## Core problem
- Key problem to solve:

## Features and their meaning
| Feature | What it solves | Why it's needed |
|---------|----------------|-----------------|
|         |                |                 |

## Relationships between features
-

## Scope and Non-Goals
- In scope:
- Out of scope:

> PRD focuses on behavior and value, not code implementation.
```

### docs/ARCHITECTURE.md

```
# ARCHITECTURE — <System Name>

## System overview
- Overall structure (ASCII diagram welcome):

## Core modules
| Module | Responsibility |
|--------|----------------|
|        |                |

## Module relationships
-

## Data flow
-

## External systems
-

## Important technical boundaries
-

> ARCHITECTURE describes the stable structure, not every code change.
```

### docs/DECISIONS.md

```
# DECISIONS

## ADR-<number>: <Decision Title>
- Date:
- Status: accepted / alternative / deprecated
- Context (what problem was encountered):
- Options considered:
- Decision:
- Why this one:
- Why not the others:
- Consequences:
- When to revisit:
```

### docs/specs/module-*.md

```
# Spec — <Module Name>

## What to build
- Goal:

## Behavior
- Expected behavior:

## Input / Output
- Input:
- Output:

## Constraints
-

## Boundary conditions
-

## Acceptance criteria
- [ ]

## Done definition
- How to tell it's complete:
```

## Acceptance criteria

- [ ] README / AGENTS / PRD / ARCHITECTURE / DECISIONS all exist and are non-empty.
- [ ] specs/ is filled in gradually as concrete modules are raised (do not invent modules; add them when the owner specifies one).
- [ ] Responsibilities do not overlap; README and AGENTS contain no implementation details.
- [ ] Content is based on the project's real information, not pure placeholders.

## Boundaries

- Do not substitute for product/technical decisions: if critical information is missing, ask the owner before filling in — do not fabricate facts.
- Do not write concrete code implementation outside of PRD or ARCHITECTURE.
