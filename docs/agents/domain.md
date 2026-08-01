# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Before exploring, read these

- **`CONTEXT-MAP.md`** at the repo root if it exists — it points at one `CONTEXT.md` per functional context. Read each one relevant to the topic.
- **`docs/adr/`** — read ADRs that touch the area you're about to work in.
- **Context-specific ADRs** — read the ADR directory referenced by `CONTEXT-MAP.md` for each relevant context.

If any of these files don't exist, **proceed silently**.
Don't flag their absence or suggest creating them upfront.
The `/domain-modeling` skill (reached via `/grill-with-docs` and `/improve-codebase-architecture`) creates them lazily when terms or decisions actually get resolved.

## File structure

This is a multi-context repo, identified by the presence of `CONTEXT-MAP.md` at the root:

```text
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← system-wide decisions
├── models/
│   ├── CONTEXT.md
│   └── docs/adr/                     ← context-specific decisions
├── vector-stores/
│   ├── CONTEXT.md
│   └── docs/adr/
└── mcp/
    ├── CONTEXT.md
    └── docs/adr/
```

The context map may point to other functional areas such as core models, RAG, memory repositories, document readers, auto-configurations, and starters.
Create context documents only when domain terms or decisions for that area need to be recorded.

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, or a test name), use the term as defined in the relevant `CONTEXT.md`.
Don't drift to synonyms the glossary explicitly avoids.

If the concept you need isn't in the glossary yet, that's a signal — either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/domain-modeling`).

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding it:

> _Contradicts ADR-0007 — but worth reopening because…_
