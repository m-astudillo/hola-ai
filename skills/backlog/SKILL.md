---
name: backlog
description: Turns a software idea or a discussed feature into a backlog of short, vertical user stories, written to hola/ as one file per story (State: proposed). No acceptance criteria or implementation; that's /story's job.
disable-model-invocation: true
---

# Backlog

Your job is to help me split what I tell you into user stories. I bring the requirements; you order and slice them.

## Conversation

1. Listen to the idea or feature. If something is unclear, ask. One question at a time, with your suggested answer.
2. If it's a new project, let's discuss the stack. Only the stack, not the architecture or implementation.
3. Ask whether any of these expensive-to-change decisions apply. Only ask, don't design them:
   - Multi-tenant or multi-organization
   - Permissions or roles model
   - Offline or sync
   - Multi-language or multi-currency
4. Propose the backlog. I adjust it.

## Rules

- **Don't invent requirements.** Only split what I told you. If you see a gap, ask me; don't fill it.
- **Each story delivers value on its own** and cuts through every layer (data, backend, UI). Never split by layer.
- **No technical stories.** The actor is never the developer or the system. "Set up the database" or "create the user model" are not stories; that infrastructure gets built inside the first story that needs it.
- **Few stories.** 10–15 max. I'd rather add than cut.
- **One line per story.** No acceptance criteria, no technical details, no estimates or priorities.
- The first story is the smallest one usable end to end (walking skeleton).

## Files

When I approve the backlog, write it to `hola/` — one file per story:

- `hola/context.md` — the context (one or two lines), the stack, the expensive decisions.
- `hola/stories/NN-slug.md` — one per story, numbered from 01 in order:

```markdown
# 01 — As a <actor>, I want <action>, so that <benefit>.

State: proposed

Requires: —
```

Add `Requires: NN` (instead of `—`) only when a story makes no sense without another.

If `hola/` already exists, keep it: append new stories with the next numbers, and don't touch existing files.

When done, suggest one line in `CLAUDE.md` (or `AGENTS.md`) pointing to the workflow in `hola/`.
