# hola-ai

Agent skills for building software with AI **without letting go of the wheel**. Inspired by Extreme Programming: vertical user stories, acceptance criteria, test-first, pair programming, simple design.

The AI splits, proposes and writes code in small steps. You decide.

## The flow

```
/backlog  →  /story  →  /pair  →  /flow done
  what       what exactly   how      verified, done
      ↑          ↑          ↑
      └──────────┴──────────┘
             /board: the state of everything + the next command
```

| Skill | What it does | What it never does |
|---|---|---|
| [`/backlog`](skills/backlog/SKILL.md) | Turns an idea into a short backlog of vertical, one-line user stories, written to `hola/` as one file per story. | Invent requirements, technical stories, estimates. |
| [`/story`](skills/story/SKILL.md) | Takes **one** story, adds 2–3 Given/When/Then acceptance criteria, a mini plan (≤5 bullets) and an explicit "Out of scope", all for your approval; writes it into the story file. | Write code. If it needs more than 3 criteria, it proposes splitting the story. |
| [`/pair`](skills/pair/SKILL.md) | Pair programming: the AI drives, you navigate. One test → red → minimum code → green, then it stops and waits. Progress lives in the story file; it resumes from the first unchecked task. | Commit, edit tests to make them pass, add things you didn't ask for. |
| [`/flow`](skills/flow/SKILL.md) | Moves a story to `done` after verifying tasks, manual criteria and the code review (or its deliberate skip), or moves it backward. | Check boxes itself, refine stories, write code. |
| [`/board`](skills/board/SKILL.md) | Shows every story's state, task progress, and the single next command to run. | Write to a file. |

## Where the workflow lives

The state lives in your project, in `hola/` — one file per story, and the file grows as the story moves:

```
hola/
├── context.md            # what it is, the stack, expensive decisions
└── stories/
    └── 01-first-login.md
```

```markdown
# 01 — As a customer, I can log in, so that I can save my cart.

State: proposed           ← /backlog writes the file
                           ← /story appends criteria + plan + out of scope, sets refined
                           ← /pair appends ## Tasks, sets building, checks boxes as they go green
                           ← /flow sets done after verifying
```

The state has one home: the `State:` line of the story file. Each skill writes only the state it produced; `/board` only reads.

A story that can't be refined whole becomes `State: split` and is replaced by its parts (next numbers). A story may declare `Requires: NN`; `/board` never suggests a story whose requirements are not all `done`.

Each skill's output is the next one's input, written into the story file.

## Principles

- **Don't invent.** Missing information gets asked, not filled in.
- **The simplest thing that works.** No abstractions "for the future".
- **Slice vertically and small.** Stories cross every layer; steps are one test and ~50 lines.
- **Suggest, don't decide.** Patterns, refactors and commits are your call.
- **Explicit checkpoints.** Every phase ends waiting for your approval.

## Install

Copy the skill folders into your Claude Code skills directory:

```bash
git clone https://github.com/nschurmann/hola-ai.git
cp -r hola-ai/skills/* ~/.claude/skills/        # all projects
# or
cp -r hola-ai/skills/* <your-project>/.claude/skills/   # one project
```

The skills are only invoked manually (`/backlog`, `/story`, `/pair`, `/flow`, `/board`), never automatically.

Or ask your agent to install these skills!

---

By Hola Mundo.
