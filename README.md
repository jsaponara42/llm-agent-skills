# LLM Agent Skills Repository

A centralized home for creating, storing, and iterating on LLM agent skills and skill ideas.

## Repository Structure

```
llm-agent-skills/
├── README.md                 # This file
├── CONTRIBUTING.md          # Guidelines for adding new skills
├── skills/                            # Reusable skill folders
│   ├── skill-creator/                # Imported Anthropic skill creator
│   ├── skill-idea-describer/         # Idea-writing helper skill
│   └── [your-skill]/
├── skill-ideas/                       # One-file-per-idea workspace
│   ├── SKILL_IDEAS.md                # Master index and queue
│   ├── IDEA_TEMPLATE.md              # Fast plain-language template
│   └── ideas/                        # Individual idea markdown files
│       └── YYYY-MM-DD-idea-name.md
├── templates/              # Starter templates for new skills
│   ├── SKILL_TEMPLATE.md   # Standard skill structure
│   └── IMPLEMENTATION_CHECKLIST.md
└── docs/                   # Documentation
    ├── SKILL_IDEA_PROCESS.md      # Fast process for capturing ideas
    └── SKILL_IDEA_FILE_FORMAT.md  # Required idea file structure
```

## Quick Start

### 1. Capture a Skill Idea Fast
1. Copy `skill-ideas/IDEA_TEMPLATE.md`
2. Save as `skill-ideas/ideas/YYYY-MM-DD-short-kebab-name.md`
3. Fill in: Problem, Pain Point, Description, Value Driver
4. Link it from `skill-ideas/SKILL_IDEAS.md`

### 2. Improve an Idea
Use `skills/skill-idea-describer/SKILL.md` when you want to refine rough notes into a high-quality idea description quickly.

### 3. Develop a New Skill
1. Copy `templates/SKILL_TEMPLATE.md` to your skill directory
2. Follow the implementation checklist in `templates/IMPLEMENTATION_CHECKLIST.md`
3. Submit a PR or move to production when ready

## Idea Capture Principles

- Keep ideas short and plain-language first
- One idea per markdown file
- Start rough, refine later
- Optimize for speed and consistency

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on adding skills, naming conventions, and quality standards.

## Related Docs

- `docs/SKILL_IDEA_PROCESS.md`
- `docs/SKILL_IDEA_FILE_FORMAT.md`
- `skill-ideas/SKILL_IDEAS.md`
- `skills/skill-idea-describer/SKILL.md`

## Getting Help

- Check docs in the `docs/` folder
- Review existing idea files in `skill-ideas/ideas/`
- Open an issue for questions or suggestions

---

Last updated: 2026-03-13
