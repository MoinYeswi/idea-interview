---
name: idea-interview
description: Use at the start of ANY new project, build, or idea when the goal, scope, or approach isn't fully clear. Interviews the user one short question at a time before any work begins, then suggests 2-3 directions and gets a plan approved. Covers anything, not just code, including apps, websites, artifacts, writing, business ideas, and plans. Use it whenever the user says things like "I want to make", "help me build", "I have an idea", "thinking about starting", or "can you create", or gives a rough or vague request, even if they never ask for questions or brainstorming. Skip it when the request is small and fully specified, such as a quick fix, a factual question, or a task with every detail given, and when the user asks to write an AI prompt or to plan one specific UI screen or feature.
---

# Idea Interview

Turn a rough idea into an agreed plan before any work starts. A rough idea hides choices the user hasn't made yet. Building on guesses costs far more of their time than a few quick questions do.

## First, check whether an interview is needed

- **Small and clear:** skip this skill and do the task.
- **Anything else:** run the three steps below, scaled to the size of the task.

Before asking anything, read what you already have: the user's message, shared files, and project context. Never ask for something you can already tell.

## Step 1: Interview

How to ask:

- Ask one question per message, then wait. Several questions at once get partial answers.
- Keep it short and plain, with no jargon.
- Offer lettered options wherever you can, so the user can reply with one letter. Use 2-4 realistic options and end with "or something else". Ask an open question when options would only be guesses.
- Only ask if the answer would change what gets made. If it wouldn't, choose a sensible default and list it in the plan.
- If the user says "not sure" or "you pick", choose a default, say what it is, and move on.

What to cover, in whatever order feels natural, skipping anything already known:

- **What:** what they want to make
- **Why:** the reason behind it, or the problem it solves
- **Who:** who it's for
- **Done:** what finished looks like
- **Priorities:** must-haves vs nice-to-haves
- **Constraints:** time, budget, tools, skill level
- **References:** examples they like

Stop as soon as you have enough to act on. A good test: could you describe what you'd make and expect the user to agree? As a rough guide, a small task needs 1-3 questions, a medium one 3-5, and a large one up to about 8. If the user says "just go" or seems tired of questions, stop and list your assumptions in the plan.

## Step 2: Suggest directions

Offer 2-3 real directions, each with a short trade-off, then say which one you recommend and why. Tie the reason to what the user told you.

```
A. [Direction]: [what it is]. Trade-off: [what you gain and give up].
B. [Direction]: [what it is]. Trade-off: [what you gain and give up].
C. [Direction]: [what it is]. Trade-off: [what you gain and give up].

I'd go with B, because [reason based on their answers].
```

Leave out any filler option added only to reach three. If the user picks a direction or mixes two, go with that.

## Step 3: Summarize and get approval

End with a short plan, using only the lines that apply:

```
Plan
- Making: [what]
- For: [who, and why it matters]
- Done when: [what finished looks like]
- Must-have: [list]
- Nice-to-have, if time allows: [list]
- Constraints: [time, budget, tools, skill level]
- Direction: [the chosen direction]
- Assumptions: [defaults you chose]

Good to start, or should I change anything?
```

Wait for a clear yes. If the user asks for changes, update the plan and ask again. Do no work before approval: no drafts, code, or files. Changing a plan takes seconds, while redoing finished work doesn't.

## Keep everything in the chat

Don't write design docs, save plan files, or commit anything unless the user asks. The plan lives in the conversation.

Ask every question as a normal chat message. This skill needs no special tools, so it works the same in any Claude app.

## Working with other skills

Run this interview first, then pass the approved plan to whichever skill fits the work, so the user isn't asked the same thing twice.

Step aside when the user names a specific skill or command, or asks to skip the questions.

If a skill for it is available, leave these two kinds of request to that skill, because its questions fit the work better:

- Writing a prompt for an AI tool
- Planning one specific UI screen or feature

## Example

User: I want to start a newsletter

Claude: What's it mainly about?
A. Your work or industry
B. A hobby or personal interest
C. A business you run
Or something else.

User: B, specialty coffee

Claude: Who do you most want reading it?
A. Beginners who want better coffee at home
B. Serious hobbyists
C. Cafe owners and baristas
Or something else.

The interview continues until there's enough to act on, then Claude suggests directions and shares the plan for approval.
