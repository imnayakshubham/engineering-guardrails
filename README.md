# engineering-guardrails

An [Agent Skill](https://github.com/anthropics/skills) (the open `SKILL.md` standard) that enforces engineering discipline across the dev lifecycle — pattern preservation, minimalism (KISS/YAGNI/DRY/SOLID), security review, and context efficiency — to produce the smallest correct, secure, maintainable solution that follows the existing codebase.

It works with any agent that supports the standard — **Claude Code, Cursor, Codex**, and more.

## Install

Install with the open [`skills`](https://github.com/vercel-labs/skills) CLI:

```bash
npx skills add imnayakshubham/engineering-guardrails
```

Add `-g` to install globally (for all your projects) instead of just the current one:

```bash
npx skills add imnayakshubham/engineering-guardrails -g
```

The CLI auto-detects whichever agents you have installed and places the skill in the right folder for each (`.claude/skills/`, `.cursor/skills/`, `.codex/skills/`, …). The skill then loads automatically when the agent detects it's relevant — no extra configuration needed.

## Repo structure

```text
.
├── README.md
└── skills/
    └── engineering-guardrails/
        ├── SKILL.md
        └── references/
            └── checklists.md
```

The skill lives in `skills/engineering-guardrails/` with a `SKILL.md` whose `name:` frontmatter matches the folder name. Heavy reference material is kept in `references/` and loaded by the agent only when needed (progressive disclosure).
