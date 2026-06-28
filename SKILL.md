---
name: guide
description: Interactive guide to all skills and tools available in this project. Explains what each skill does, when to use it, and how to invoke it. Also covers ~/tools repos. Use when the user asks "what can you do?", "what skills are available?", "how do I use X?", or invokes /guide.
---

# Guide

Helps the user understand and use everything available in this project: skills, tools, and when to reach for each.

---

## How to Run This Skill

When invoked, do the following:

1. **Scan for available skills** — list all directories under `.claude/skills/` in the current project. Read each `SKILL.md` to extract name + description.

2. **Scan for installed tools** — check `~/tools/` for directories. For each, read the first 20 lines of its `README.md` to get a one-line summary.

3. **Ask the user what they want**:
   - "Everything" → print the full catalogue below
   - A specific skill or tool name → deep-dive on just that one
   - A task description → recommend the best skill/tool for it

4. **Present the catalogue** in the format below, tailored to what's actually installed (don't show skills/tools that aren't present).

---

## Catalogue Format

### Skills

For each skill found in `.claude/skills/`:

```
## /skill-name
<one-line description>

**When to use:** <1-2 sentences on the trigger>
**Commands:**
  - /skill-name          → <what it does>
  - /skill-name <sub>    → <what it does>
**Key files:** .claude/skills/<name>/SKILL.md
```

### Tools (~/tools)

For each tool found in `~/tools/`:

```
## <tool-name>  (~/tools/<tool-name>)
<one-line description>

**Best for:** <use case>
**How agents use it:** <1-2 sentences with example command or invocation pattern>
**Full docs:** ~/tools/<tool-name>/README.md
```

---

## Deep-Dive Mode

If the user asks about a specific skill or tool, read its full documentation and answer their question directly. Don't just quote the README — synthesize and explain in the context of this project.

---

## Recommend Mode

If the user describes a task (e.g. "I want to run experiments" or "I need to automate a browser"), map it to the best available skill or tool:

| Task type | Recommend |
|-----------|-----------|
| New feature, structured dev | `paul` (plan-apply-unify) |
| Vague idea, new sub-project | `seed` |
| Iterative tuning / experiments | `autoexperiment` |
| UI / frontend component | `frontend-design` |
| GitHub operations | `~/tools/axi` |
| Browser automation | `~/tools/agent-browser-axi` |
| Parallel agent work | `~/tools/firstmate` |
| Library API questions | `~/tools/context7` |
| Exploring unfamiliar codebase | `~/tools/codebase-memory-mcp` |
| Researching web / external sources | `~/tools/agent-reach` |
| UI design consistency across agents | `~/tools/design.md` |
| Test-first development | `tdd` |
| Restructuring existing code | `refactor` |

If nothing matches, say so honestly and suggest the closest option.

---

## Keeping the Guide Current

The guide is **self-assembling** — it reads what's actually installed rather than maintaining a hardcoded list. To add something new to the guide:
- Add a skill → drop it in `.claude/skills/` with a `SKILL.md`
- Add a tool → add it to `tools.yaml` in `project-init` and run `/project-init tools`

No changes needed to this file.
