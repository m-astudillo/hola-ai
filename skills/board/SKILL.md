---
name: board
description: "Shows the hola/ board: every story with its state (proposed, refined, building, done), task progress, and the one next command to run. Read-only; it never writes a file."
disable-model-invocation: true
---

# Board

You show where the work is and what comes next. The state is written by the skill that produced it (`/story`, `/pair`, `/flow`); you only read it.

## Read

1. `hola/context.md` — what the project is, the stack, the expensive decisions.
2. Every file in `hola/stories/`, in number order.

If `hola/` doesn't exist, say so and offer to start with `/backlog`.

## Render

Group stories by their `State:` line:

```markdown
## Board
<one line: what it is> | Stack: ...

PROPOSED (2)
  01. As a ..., I want ..., so that ...
  03. ...

REFINED (1)
  02. ...

BUILDING (1)
  05. ... — 3/7 tasks, next: <first unchecked>

DONE (2)
  06. ...
  07. ...

SPLIT (1)
  04. ... (replaced by 08, 09)
```

For `building` stories, count the checkboxes in `## Tasks` and name the first unchecked one.

## Next

End with exactly one suggestion — the smallest useful step. A story whose `Requires:` are not all `done` is not offered:

- A `building` story with unchecked tasks → resume `/pair` on it.
- Else the lowest-numbered `refined` story → `/pair`.
- Else the lowest-numbered `proposed` story → `/story`.
- Else all `done` → the backlog is done; suggest a new feature with `/backlog`.
