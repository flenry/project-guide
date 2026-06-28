# project-guide

Claude Code skill that shows all available skills and tools in the current project and recommends the right one for a given task.

## Install

```bash
git clone git@github.com:flenry/project-init.git .claude/skills/project-init
git clone git@github.com:flenry/project-guide.git .claude/skills/guide
```

## Usage

```
/guide
```

Ask it anything:
- "What skills are available?" → full catalogue
- "How do I use paul?" → deep-dive on that skill
- "I need to automate a browser" → recommends the right tool

The guide is self-assembling — it reads whatever is actually installed in `.claude/skills/` and `~/tools/` rather than maintaining a hardcoded list.
