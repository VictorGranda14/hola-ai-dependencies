---
name: backlog
description: Turns a software idea or a discussed feature into a backlog of short, vertical user stories, each carrying its dependencies on other stories. No acceptance criteria or implementation; that's /story's job.
disable-model-invocation: false
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
- **Few stories.** 15–20 max. I'd rather add than cut.
- **One line per story.** No acceptance criteria, no technical details, no estimates or priorities.
- The first story is the smallest one usable end to end (walking skeleton).

## Dependencies

- **A dependency is hard.** Story B `Requires: #A` only when B cannot be built or used without A existing. "Would be nicer to build first" is not a dependency. Don't invent dependencies, same as requirements.
- A story can require several: `Requires: #1, #3`.
- **Numbering is a valid build order.** A story never requires a story with a higher number.
- **No cycles.** If two stories need each other, they are sliced wrong; propose merging or re-slicing them.
- Story #1 requires nothing. Prefer shallow chains; if a story requires many others, check whether it's too big.
- When the backlog is adjusted (a story added, removed, split or merged), re-check dependencies and say which `Requires` changed. Never silently leave a `Requires` pointing at a removed story.

## Output format

```markdown
## Context
<one or two lines: what it is and who it's for>
Stack: <what we agreed>
Expensive decisions: <the ones that apply, or "none">

## Backlog
1. As a <actor>, I want <action>, so that <benefit>.
2. As a <actor>, I want <action>, so that <benefit>. Requires: #1

## Dependencies
Ready to start: #<stories with no pending requirement>
Most depended on: #<story> (unblocks #<n>, #<m>)
```

Add `Requires: #N` only when a story makes no sense without another (see Dependencies). "Most depended on" is the story that unblocks the most others.

When done, offer to save the context and stack in `CLAUDE.md` (or `AGENTS.md`). The stories go to my tracker; don't save them to files unless I ask.
