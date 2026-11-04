# claude-skills

Two Claude skills that work as a pair:

- **idea-interview** stops Claude from building on guesses. It interviews you first and agrees a plan before any work begins.
- **model-router** then gives each step of that plan to the cheapest Claude model that can do it well.

Each skill also works on its own.

## idea-interview

When you start something with only a rough idea, Claude asks one short question at a time and you agree on a plan. It works for anything, not just code: apps, websites, writing, business ideas, and plans.

1. **Interview:** Claude asks one short question at a time, with lettered options wherever it can, so you can reply with a single letter.
2. **Directions:** Claude suggests 2-3 ways forward with their trade-offs, and says which one it recommends and why.
3. **Plan:** Claude sums up the plan and waits for your yes before starting.

Small, clear tasks skip the interview, and everything stays in the chat. No design docs or files are created unless you ask.

```text
You:    I want to start a newsletter

Claude: What's it mainly about?
        A. Your work or industry
        B. A hobby or personal interest
        C. A business you run
        Or something else.

You:    B, specialty coffee

Claude: Who do you most want reading it?
        A. Beginners who want better coffee at home
        B. Serious hobbyists
        C. Cafe owners and baristas
        Or something else.
```

## model-router

For multi-step work, Claude gives each step a tier:

| Model | Good for |
|---|---|
| Haiku | Mechanical work: finding files, renaming, formatting, summarizing logs |
| Sonnet | Everyday work, and the default when unsure |
| Opus | Hard judgment: architecture, unclear bugs, security review |
| Fable | The hardest, longest tasks |

It also decides whether a step is worth delegating. A subagent starts with no memory of the conversation, so tiny steps stay in the main chat. If a step fails, it retries once, one tier up, and then stops and tells you.

```text
Plan: add a settings page

1. Find how existing pages are built: Haiku, delegated
2. Decide where preferences are stored: Opus, main conversation
3. Build the page: Sonnet, delegated
4. Write and run the tests: Sonnet, delegated
```

Savings depend on your work and haven't been measured here. In apps that can't run subagents, it tells you which model to select instead.

## Install

### Claude Code

```bash
git clone https://github.com/MoinYeswi/claude-skills.git
cp -r claude-skills/idea-interview claude-skills/model-router ~/.claude/skills/
```

To make them fire more reliably, add these lines to `~/.claude/CLAUDE.md`. The second one lets Claude start subagents without asking each time, so leave it out if you'd rather approve that yourself.

```text
At the start of any new project, build, or idea where the goal, scope, or approach isn't fully clear, use the idea-interview skill before doing any work.
For multi-step work, use the model-router skill; following it counts as my permission to delegate routed steps to subagents.
```

### Claude app

1. Download this repo and unzip it.
2. Zip the `idea-interview` folder, so that `SKILL.md` sits directly inside that folder. Do the same for `model-router` if you want it.
3. Upload each zip under **Settings > Capabilities > Skills**.

## Credits

idea-interview was inspired by the brainstorming skill in [Superpowers](https://github.com/obra/superpowers).

## License

[MIT](LICENSE)
