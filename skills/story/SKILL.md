---
name: story
description: "Refines ONE story from hola/stories/: 2-3 acceptance criteria and a mini implementation plan for approval, written into the story file (State: refined). If it needs more than 3 criteria, proposes splitting it. Writes no code; implementation is /pair's job."
disable-model-invocation: true
---

# Story

We refine a single story, right before building it. You propose and I decide.

## Steps

1. **Read the story** I point to in `hola/stories/` (or the text I paste) and review the current code and `CLAUDE.md` to understand the context. If I pasted it, create `hola/stories/NN-slug.md` first with the next number and `State: proposed`.
2. **Acceptance criteria.** Propose 2–3 in Given/When/Then format. They only describe *what* the user sees or gets, never *how* it's implemented.
3. **If it needs more than 3 criteria, don't bloat it: propose splitting it.** On my approval, set the original to `State: split`, create the new stories in `hola/stories/` (next numbers, `State: proposed`, `Requires:` when needed), and we continue with the first one.
4. **Mini plan.** 5 bullets max, no code or file names. How it cuts through the layers, with the minimum that meets the criteria.
5. **Wait for my approval.** We adjust until I say yes.

## Rules

- **Don't invent requirements.** If information is missing, ask me.
- **The simplest thing that meets the criteria.** No abstractions, layers, configuration or patterns "for the future".
- **Suggest, don't decide.** If a pattern could help (Atomic Design, middleware composition, extracting a component…), mention it under "Suggestions" with its why. Only suggest it if there's a concrete signal in the code (for example, something that already repeats), not in advance.
- **Don't write code.**

## Write

On my approval, append it to the story file and set `State: refined`. `/pair` reads the file as input.

```markdown
## Acceptance criteria
- Given <context>, when <action>, then <result>.
- ...

## Plan
- ...

## Out of scope
- <what's left out of this story, so it doesn't sneak in>

## Suggestions (your call)
- <optional>
```
