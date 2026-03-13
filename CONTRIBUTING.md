# Contributing Guidelines

How to contribute ideas, skills, improvements, and feedback to the LLM Agent Skills repository.

## Getting Started

### Before You Start
1. Read the [README.md](README.md) to understand the project
2. Review [docs/SKILL_DESIGN.md](docs/SKILL_DESIGN.md) for design principles
3. Look at existing skills in `skills/` directory for patterns
4. Check [skill-ideas/SKILL_IDEAS.md](skill-ideas/SKILL_IDEAS.md) to see if your idea already exists

### Setting Up Your Environment
```bash
git clone <repo-url>
cd llm-agent-skills
# No special setup needed for idea submissions
# For implementation: see individual skill README files
```

---

## Contributing Types

### 1. Adding Skill Ideas

The lowest friction way to contribute! Got a problem that could use a skill? Add it.

**Process**:
1. Open `skill-ideas/SKILL_IDEAS.md`
2. Find the appropriate category
3. Add your idea using the template format
4. Include:
   - Problem statement
   - Use cases (2-3 examples)
   - Complexity and priority estimate
   - Implementation approach (high-level)
5. Commit with message: `docs: add skill idea - [skill name]`
6. Open a PR

**What makes a good idea**:
- ✅ Solves a specific, real problem
- ✅ Clearly explains who would use it and why
- ✅ Has 2-3 concrete use cases
- ✅ Realistic complexity estimate
- ✅ Brief high-level approach sketched out
- ❌ Too vague or abstract
- ❌ Duplicate of existing skill
- ❌ Missing use cases

### 2. Implementing a Skill

Ready to build something? Here's how to develop a full skill.

**Process**:
1. Start from an idea in SKILL_IDEAS.md
2. Move idea to `skill-ideas/backlog/[skill-name].md` with full spec
3. Create skill directory: `skills/[category]/[skill-name]/`
4. Copy [SKILL_TEMPLATE.md](templates/SKILL_TEMPLATE.md) → `SKILL.md`
5. Implement using [IMPLEMENTATION_CHECKLIST.md](templates/IMPLEMENTATION_CHECKLIST.md)
6. When complete:
   - Update SKILL_IDEAS.md with "Complete" status and link
   - Open PR with new skill
   - Tag as "skill-implementation"

**Directory Structure**:
```
skills/[category]/[skill-name]/
├── README.md                # Quick start guide
├── SKILL.md                 # Full specification (from template)
├── src/
│   └── [skill_name].py      # Main implementation
├── tests/
│   └── test_[skill_name].py # Unit tests
├── examples/
│   └── example_*.py         # Usage examples
└── docs/
    ├── API.md              # API documentation
    └── TROUBLESHOOTING.md  # Known issues
```

**Code Standards**:
- Python: Follow PEP 8
- Functions: Include docstrings with input/output specs
- Tests: Aim for 80%+ coverage
- Documentation: Examples for every major feature
- Errors: Explicit error messages, clear failure modes
- Logging: Debug, info, and error level logs at appropriate points

### 3. Improving Existing Skills

Found a bug? Want to optimize? Have a better approach?

**For Bug Fixes**:
1. Open an issue describing the bug
2. Create a branch: `fix/[issue-number]-[description]`
3. Include test case that reproduces the bug
4. Fix implementation
5. Ensure tests pass
6. Open PR referencing the issue

**For Improvements**:
1. Open an issue describing the improvement
2. Get feedback before major refactoring
3. Create a branch: `improve/[description]`
4. Update tests as needed
5. Update documentation if behavior changes
6. Open PR with benchmarks showing improvements

### 4. Improving Documentation

Documentation is critical! Help make it better.

**Types of doc contributions**:
- Clarifying existing docs
- Adding examples
- Creating troubleshooting guides
- Expanding API documentation
- Creating tutorials

**Process**:
1. Edit docs directly or create new `.md` files
2. Keep writing clear and concise
3. Include code examples where relevant
4. Open PR with message: `docs: [description]`

### 5. Reporting Issues

Found a problem? Let us know!

**Issue Template**:
```markdown
## Problem
[Clear description of the issue]

## Skill/Area Affected
[Which skill or area]

## Steps to Reproduce
[How to reproduce the issue]

## Expected Behavior
[What should happen]

## Actual Behavior
[What actually happens]

## Environment
- OS: [Windows/Mac/Linux]
- Python: [version if applicable]
- Other relevant details

## Possible Solution
[Optional: your thoughts on a fix]
```

---

## Review Process

### Code Review

All PRs go through code review before merging.

**Review Criteria**:
- ✅ Code follows standards in this repo
- ✅ Implementation matches specification
- ✅ Tests provide adequate coverage
- ✅ Documentation is clear and complete
- ✅ No obvious bugs or issues
- ✅ Performance is acceptable
- ✅ Error handling is robust

**What reviewers look for**:
- Edge case handling
- Clear variable/function naming
- Proper error messages
- Test quality and coverage
- Documentation completeness
- Code consistency with codebase

### Getting Your PR Reviewed

1. Use the PR template (if available)
2. Provide clear description of changes
3. Link related issues
4. Request specific reviewers if known
5. Be responsive to feedback
6. Make requested changes in new commits (don't squash until approved)

---

## Naming Conventions

### Skill Names
- Use lowercase, hyphenated names
- Be descriptive but concise
- Examples: `data-validator`, `email-generator`, `code-reviewer`

### Categories
- Standardized categories in `skills/[category]/`
- Current categories:
  - `data-analysis/`
  - `content-creation/`
  - `code-generation/`
  - `research/`
  - `communication/`
  - `planning/`
  - `automation/`

### Branch Names
- Feature: `feature/[skill-name]` or `feature/[description]`
- Fix: `fix/[issue-number]-[description]`
- Doc: `docs/[description]`
- Improvement: `improve/[description]`

### Commit Messages
- Format: `type: message`
- Types: `feat`, `fix`, `docs`, `improve`, `refactor`, `test`
- Examples:
  - `feat: add data validator skill`
  - `fix: handle edge case in time series forecaster`
  - `docs: add examples to email generator`

---

## Communication

### Discussion Channels
- **GitHub Issues**: Bug reports and feature discussions
- **Discussions** (if enabled): General questions and ideas
- **README & docs**: First stop for questions

### Code of Conduct

We want this to be a welcoming community. Please:
- Be respectful of others' ideas and work
- Provide constructive feedback
- Ask questions rather than make assumptions
- Help others when you can
- Report concerning behavior privately to maintainers

---

## FAQ for Contributors

**Q: Can I contribute an idea without building it?**
A: Absolutely! Ideas are valuable. Just add to SKILL_IDEAS.md.

**Q: What if my skill seems too niche?**
A: If it solves a real problem for someone, it's worth considering. Many great ideas start niche.

**Q: Can I contribute multiple skills at once?**
A: Yes, but consider staggering PRs for easier review. One PR per skill is cleaner.

**Q: What if I'm unsure about the design?**
A: Open an issue or discussion to brainstorm. Better to get feedback early.

**Q: Can I refactor an existing skill?**
A: Yes, but please open an issue first to discuss major changes. Start with small improvements.

**Q: How long does PR review take?**
A: Typically 2-5 business days depending on complexity. Ping reviewers if waiting longer.

**Q: What if my PR is rejected?**
A: That's okay! We'll explain why. Consider it feedback for next iteration.

---

## Attribution

### Credit
Contributors are credited in:
- Skill README files
- Git commit history
- Repository contributor list
- Release notes (for major contributions)

### License
By contributing, you agree that your contributions are licensed under the same license as the project.

---

## Resources

- [Skill Design Best Practices](docs/SKILL_DESIGN.md)
- [Skill Anatomy & Structure](docs/SKILL_ANATOMY.md)
- [Skill Template](templates/SKILL_TEMPLATE.md)
- [Implementation Checklist](templates/IMPLEMENTATION_CHECKLIST.md)
- [Existing Skills](skills/) - Examples to learn from

---

## Questions?

- Check existing issues/discussions
- Open a new issue with the `question` label
- Review documentation
- Ask in team channels

Thank you for contributing! 🙏

---

**Last Updated**: 2026-03-12
