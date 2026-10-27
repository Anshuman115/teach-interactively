# Teach Interactively

A portable teaching skill for AI coding agents. The agent teaches a topic from your own project, builds the mental model before the details, sets short exercises, and adapts to your answers instead of dumping information.

## Invocation

```text
Use teach-interactively to explain [topic]. Use my real project where possible,
explain the mental model first, keep it concise, and give me one practical example.
```

Short form:

```text
Use teach-interactively for this.
```

Other triggers it is written for:

```text
Teach me how this error works; don't just fix it.
Help me understand this code.
Use my learning style for this.
```

## Install

### Plugin marketplace

```bash
claude plugin marketplace add Anshuman115/teach-interactively
claude plugin install teach-interactively@teach-interactively
```

The repository is private, so the machine needs GitHub credentials that `git` can use.

### Copy or symlink

Copy `skills/teach-interactively/` into any directory your agent scans for skills. On this machine the agent roots are `~/.omp/agent/skills`, `~/.agents/skills`, and `~/.claude/skills`.

```bash
ln -s "$PWD/skills/teach-interactively" ~/.agents/skills/teach-interactively
```

### No skill support

Add `skills/teach-interactively/SKILL.md` to the agent's project instructions, or ask it to read that file before the lesson.

## Scope

The skill grants no file, terminal, or infrastructure access. The agent still needs the relevant context and permissions, and it must ask before running commands, editing files, deploying, or changing infrastructure.

## Licence

MIT
