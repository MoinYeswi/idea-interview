---
name: model-router
description: Use for any work beyond a single quick action, including small tasks, multi-step work, and approved plans, especially right after idea-interview. Assigns each task to the cheapest Claude model that can do it well, with Haiku for small or mechanical work, Sonnet for everyday work, Opus for UI design and hard judgment, and Fable, if the user has it, for the hardest long-running tasks. Use it whenever the user wants to save tokens, cut cost, pick a model, or delegate work to subagents, even if they don't mention routing. Skip it only for a single quick action, such as one command or a one-line edit.
---

# Model Router

Give each step the cheapest model that can do it well. Most work doesn't need the strongest model, but hard decisions made by a weak model cost more to fix than they saved.

## Step 1: Size up the work

Split the work into steps. If an approved plan exists, use its steps.

Give each step a tier:

| Tier | Good for | Examples |
|---|---|---|
| Haiku | Small or mechanical work with an obvious right answer | Finding files, renaming, formatting, extracting data, summarizing logs, small text changes |
| Sonnet | Everyday work, and the default when unsure | Writing features, fixing bugs with a clear cause, tests, refactors, drafting |
| Opus | UI design and hard judgment, where a wrong call is costly | Designing screens or layouts, architecture, unclear bugs, security review, trade-offs across many files |
| Fable | The hardest, longest tasks, when Opus has failed or clearly won't be enough | Large migrations, deep multi-stage investigations |

Fable is optional. Use it only if the user has said it's available to them. Otherwise Opus is the top tier.

Choose by the kind of work, not by how large the task looks. Renaming something across 200 files is still a Haiku task, and a small UI change is still an Opus task. Small tasks get a tier too.

If this page's model names are out of date, keep the same idea and use the current models at each level.

## Step 2: Route every task

Route every task, however small, so cheap work doesn't run on an expensive model. Keeping a task because it looks easy is the mistake this skill exists to prevent: a Sonnet session still hands small work down to Haiku, and hands UI design up to Opus.

- If its tier differs from the main model, delegate it to a subagent on that tier.
- If its tier matches the main model, do it in the main conversation, unless it reads or produces a lot of text, such as wide searches, logs, or test output. Then delegate it so only a summary comes back.

The one exception is a single quick action, such as one command or a one-line edit. Do that directly, because the brief and the result would cost more than the action.

A subagent starts with no memory of the conversation, so if a task depends on what was discussed, put what it needs in the brief.

Run independent tasks at the same time only when they don't touch the same files.

## Step 3: Write a tight brief

Every word of a brief is paid for, and a vague brief wastes more through retries. Each brief should state:

- The goal, in one sentence
- The exact files or area to work in
- What done looks like
- What to send back, and how short it should be

Set the model on each subagent call. If no model is set, the subagent normally runs on the main model and nothing is saved.

## Step 4: Check and escalate

Check each result before relying on it, preferably by running a test or command rather than rereading everything.

If a step fails or the result looks unsure, retry it once, one tier up. If it fails again, stop and tell the user what happened instead of climbing further.

## Choosing the main model

The main conversation usually uses more tokens than any single subagent, so its model matters most. At the start of large work, say which model suits the session:

- Mostly routine work: Sonnet
- Hard planning, then routine building: Opus for the plan, then Sonnet to build
- Mostly hard decisions: Opus

Suggest this at the start. Changing models partway through can lose cached context, which can cost more than it saves.

If the app can't run subagents or change models by itself, do the work in the conversation and tell the user which model to select.

## Reporting

Before starting, show the routing in a short list, one line per step: the step, its tier, and whether it's delegated. If the user approved a plan, continue without asking again.

When finished, say which model did what. Don't quote savings unless they were actually measured.

## Working with other skills

Run this after idea-interview, once the plan is approved. If another skill is already running the delegation, only choose the model for each step.

## Example

Plan: add a settings page.

```
1. Find how existing pages are built: Haiku, delegated
2. Design the page layout: Opus, delegated
3. Build the page: Sonnet, main conversation
4. Write and run the tests: Sonnet, delegated
5. Update old links to the new page: Haiku, delegated
```
