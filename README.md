# idea-interview

A Claude skill that stops Claude from building on guesses. When you start something with only a rough idea, Claude interviews you first, one short question at a time, and you agree on a plan before any work begins.

It works for anything, not just code: apps, websites, writing, business ideas, and plans.

## How it works

1. **Interview:** Claude asks one short question at a time, with lettered options wherever it can, so you can reply with a single letter.
2. **Directions:** Claude suggests 2-3 ways forward with their trade-offs, and says which one it recommends and why.
3. **Plan:** Claude sums up the plan and waits for your yes before starting.

Small, clear tasks skip the interview, and everything stays in the chat. No design docs or files are created unless you ask.

## Example

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

## Install

### Claude Code

```bash
git clone https://github.com/MoinYeswi/idea-interview.git
cp -r idea-interview/idea-interview ~/.claude/skills/
```

To make it fire more reliably, add this line to `~/.claude/CLAUDE.md`:

```text
At the start of any new project, build, or idea where the goal, scope, or approach isn't fully clear, use the idea-interview skill before doing any work.
```

### Claude app

1. Download this repo and unzip it.
2. Zip the inner `idea-interview` folder, so that `SKILL.md` sits directly inside that folder.
3. Upload the zip under **Settings > Capabilities > Skills**.

## Credits

Inspired by the brainstorming skill in [Superpowers](https://github.com/obra/superpowers).

## License

[MIT](LICENSE)
