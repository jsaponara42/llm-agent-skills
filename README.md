# LLM Agent Skills Repository

A comprehensive collection of reusable skills designed for LLM agents to perform specialized tasks across various domains.

## Repository Structure

```
llm-agent-skills/
├── README.md                 # This file
├── CONTRIBUTING.md          # Guidelines for adding new skills
├── skills/                  # Production-ready skills
│   ├── data-analysis/
│   ├── content-creation/
│   ├── code-generation/
│   ├── research/
│   └── [domain]/
├── skill-ideas/             # Brainstorming and planning
│   ├── SKILL_IDEAS.md      # Master list of skill concepts
│   ├── backlog/            # Skills under consideration
│   └── completed/          # Shipped skills (with links)
├── templates/              # Starter templates for new skills
│   ├── SKILL_TEMPLATE.md   # Standard skill structure
│   └── IMPLEMENTATION_CHECKLIST.md
└── docs/                   # Documentation
    ├── SKILL_DESIGN.md     # Best practices for skill design
    └── SKILL_ANATOMY.md    # How skills are structured
```

## Quick Start

### 1. Explore Existing Skills
Browse the `skills/` directory to see implemented skills and how they're structured.

### 2. Add a New Skill Idea
1. Open `skill-ideas/SKILL_IDEAS.md`
2. Add your idea with description, use cases, and implementation priority
3. Once ready to develop, move details to `skill-ideas/backlog/`

### 3. Develop a New Skill
1. Copy `templates/SKILL_TEMPLATE.md` to your skill directory
2. Follow the implementation checklist in `templates/IMPLEMENTATION_CHECKLIST.md`
3. Submit a PR or move to production when ready

## Skill Categories

- **Data Analysis**: Extract, transform, visualize, and interpret data
- **Content Creation**: Generate, edit, and refine written content
- **Code Generation**: Write, debug, and optimize code
- **Research**: Gather, synthesize, and summarize information
- **Communication**: Draft emails, messages, reports
- **Planning**: Create schedules, roadmaps, and project plans
- **Automation**: Orchestrate multi-step workflows

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on adding skills, naming conventions, and quality standards.

## Skill Anatomy

Each skill includes:
- **Purpose**: Clear description of what the skill does
- **Inputs**: Data/parameters the skill accepts
- **Outputs**: Expected results and formats
- **Dependencies**: Required libraries or tools
- **Examples**: Real-world usage scenarios
- **Edge Cases**: Known limitations and failure modes

## Getting Help

- Check `docs/SKILL_DESIGN.md` for design principles
- Review existing skills in similar domains
- Open an issue for questions or suggestions

---

Last updated: 2026-03-12
