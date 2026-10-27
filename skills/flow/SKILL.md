---
name: flow
description: Moves a story's State in hola/ — to done (after verifying tasks and manual criteria) or backward. The skill that gates done and undoes progress.
disable-model-invocation: true
---

# Flow

The state moves forward on its own: `/story` writes `refined`, `/pair` writes `building`. You handle the moves that need a human gate: `done`, and anything backward.

## done

1. All checkboxes in `## Tasks` checked?
2. The criteria marked `manual:` verified together with me?
3. `/code-review` done — or skipped on purpose, my call?

All yes → set `State: done`. Any no → say which one and stop. You never check a box yourself.

## Backward

Any move that undoes progress (`done → building`, `building → proposed`). Ask why first, then set the `State:` line.

You don't refine stories, don't write tests, don't create stories — those are `/story` and `/pair`'s jobs.
