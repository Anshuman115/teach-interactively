# Teach Interactively

A lightweight question-and-answer teaching skill for AI coding agents. Ask it to explain a concept from your own repo, your architecture, a library you are evaluating, or an error whose cause you want to understand. It gives you the mental model first, ties it to your real files, and checks your understanding with short, realistic questions instead of a lecture.

Author: Anshuman Tripathy ([@Anshuman115](https://github.com/Anshuman115)).

## What it does

- Answers a concept question in the first paragraph, then goes deeper only if you want it. A factual question gets the answer, not an exercise.
- Builds the mental model before the details, and keeps one concept in flight at a time.
- Uses your project, config, logs, or error as the example. It does not invent environment details.
- Adapts to your answers and skips what you have already shown you understand.
- On an error, works from expected vs observed behaviour to a single read-only diagnostic, and explains what each possible result would mean before proposing a fix.

It does not run commands, edit files, deploy, or change infrastructure without permission, and it never asks for secrets, only redacted output.

For multi-session learning, ask it to keep notes. It only claims remembered progress when those notes or the conversation are in context.

## Install

### Plugin marketplace

```bash
claude plugin marketplace add Anshuman115/teach-interactively
claude plugin install teach-interactively@teach-interactively
```

### Symlink into a skill root

Symlinks keep one copy in this repository and make every agent read it.

```bash
git clone git@github.com:Anshuman115/teach-interactively.git
ln -s "$PWD/teach-interactively/skills/teach-interactively" ~/.agents/skills/teach-interactively
```

`~/.agents/skills` is the cross-runtime alias that omp, Codex, Copilot CLI and Gemini CLI read. Claude Code also reads `~/.claude/skills`, and omp reads `~/.omp/agent/skills`.

### Copy

```bash
cp -R skills/teach-interactively ~/.agents/skills/
```

### No skill support

Add `skills/teach-interactively/SKILL.md` to the agent's project instructions, or ask it to read that file before the lesson.

## Usage

```text
Use teach-interactively to explain [concept]. Use my real project where possible,
explain the mental model first, keep it concise, and give me one practical example.
```

```text
Teach me how this error works; don't just fix it.
Help me understand this code.
Use my learning style for this.
```

Short form:

```text
Use teach-interactively for this.
```

One exchange:

```text
You: teach-interactively, why does the webhook handler see no tenant?
It:  Goal: you will be able to name the layer that drops the tenant.
     Model: the request carries tenant metadata, the consumer resolves it from
     config, and anything unresolved falls back to the default database.
     Question: given that, which of the two is more likely to be empty?
You: the config lookup
It:  Right. The line to check is `No tenant could be resolved`. If it appears
     before the first query, the metadata arrived intact and the lookup is the gap.
```

## Layout

```text
.claude-plugin/marketplace.json   plugin marketplace entry
.claude-plugin/plugin.json        plugin metadata
skills/teach-interactively/SKILL.md
```

## Licence

MIT
