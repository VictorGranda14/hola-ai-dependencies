---
name: story
description: Takes ONE user story from the backlog, checks its dependencies first, adds 2-3 acceptance criteria and proposes a mini implementation plan for approval. Writes no code; implementation is /pair's job.
disable-model-invocation: false
---

# Story

We refine a single story, right before building it. You propose and I decide.

## Steps

1. **Read the story** I give you (pasted text, GitHub issue, Jira ticket, etc.) and review the current code and `CLAUDE.md` to understand the context. Also read its `Requires: #N` and check each required story is done (look at the current code, the tracker info I gave you, or ask me). If one isn't done, **stop and say so before writing criteria** and recommend refining the dependency first. Continue only if I explicitly say so, and then record that the work assumes the missing piece (and how).
2. **Acceptance criteria.** Propose 2–3 in Given/When/Then format. They only describe *what* the user sees or gets, never *how* it's implemented.
3. **If it needs more than 3 criteria, don't bloat it: propose splitting it.** Deliver the new stories in backlog format (`As a…, I want…, so that…`) for me to add to the tracker, and we continue with the first one. The new stories carry their own `Requires` (typically the later pieces require the first), and you say which existing backlog stories that required the original now require which piece.
4. **Mini plan.** 5 bullets max, no code or file names. How it cuts through the layers, with the minimum that meets the criteria.
5. **Wait for my approval.** We adjust until I say yes.

## Rules

- **Don't invent requirements.** If information is missing, ask me.
- **The simplest thing that meets the criteria.** No abstractions, layers, configuration or patterns "for the future".
- **Suggest, don't decide.** If a pattern could help (Atomic Design, middleware composition, extracting a component…), mention it under "Suggestions" with its why. Only suggest it if there's a concrete signal in the code (for example, something that already repeats), not in advance.
- **Don't absorb dependencies silently.** If refinement reveals a dependency the backlog doesn't list (on another story, or on something not in the backlog at all), flag it and propose the `Requires` line or a new story in backlog format.
- **Don't write code.**

## Output format

A block ready to paste into the issue. `/pair` uses it as input.

```markdown
## Story
As a <actor>, I want <action>, so that <benefit>.

## Dependencies
- Requires: #N <short title> — ✅ done | ⚠️ pending (<what's assumed>)
- Unblocks: #M, #K

## Acceptance criteria
- [ ] Given <context>, when <action>, then <result>.
- [ ] ...

## Plan
- ...

## Out of scope
- <what's left out of this story, so it doesn't sneak in>

## Suggestions (your call)
- <optional>
```

Use `Requires: none` when it has none. `Unblocks` lists the backlog stories that require this one, if known.
