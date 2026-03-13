---
name: skill-idea-describer
description: Turn rough skill ideas into clear, useful skill idea writeups fast. Use when the user is brainstorming a new skill and wants plain-language framing such as problem, pain point, description, and value driver, then save it as a single markdown file.
---

# Skill Idea Describer

This skill helps capture and improve skill ideas quickly without heavy process.

## When to use this skill

Use this skill when the user says things like:
- "I have a rough skill idea"
- "Help me brainstorm a skill"
- "Can you clean up this idea so I can build it later"
- "I just want to write down the problem/pain/value quickly"

Do not use this skill for full skill implementation or code generation.

## Core workflow

1. Capture a raw idea in plain language.
2. Normalize it into four core fields.
3. Ask only the minimum clarifying questions needed.
4. Produce a short markdown idea file.
5. Offer one fast iteration pass to improve clarity.

Keep this lightweight. Avoid long interviews unless the user asks for depth.

## Repository save requirement

Always save idea files in this repository (`llm-agent-skills`), under the `skill-ideas` folder.

- Primary target: `skill-ideas/ideas/`
- Repository name: `llm-agent-skills`
- Do not save idea files outside this repo unless the user explicitly asks.
- After creating a new idea file, add or update a link in `skill-ideas/SKILL_IDEAS.md`.

If write access is unavailable, return the exact file path and full markdown content the user should place in `skill-ideas/ideas/`.

## Required fields

Always produce these four fields:
- Problem
- Pain Point
- Description
- Value Driver

Optional fields:
- Users
- Current workaround
- Success signal
- Scope boundaries

## Output format

ALWAYS use this template for the final idea writeup:

```markdown
# [Idea Name]

## Problem
[What is broken or missing?]

## Pain Point
[Why this hurts today.]

## Description
[What the skill should do in plain language.]

## Value Driver
[Why this is worth building now.]

## Optional Notes
- Users: [who benefits]
- Current workaround: [what happens today]
- Success signal: [how we know it worked]
- Scope boundaries: [what not to do]
```

## File conventions

When saving an idea file, use this path and naming style:
- Path: `skill-ideas/ideas/`
- Filename: `YYYY-MM-DD-short-kebab-name.md`

Examples:
- `skill-ideas/ideas/2026-03-13-client-onboarding-checklist.md`
- `skill-ideas/ideas/2026-03-13-ticket-triage-assistant.md`

Also update `skill-ideas/SKILL_IDEAS.md` with a link to the new file.

## Question strategy

Ask at most 3 short follow-up questions before drafting.

If details are missing, prefer drafting with assumptions and clearly label them.

## Quality bar

Before finalizing, verify:
- The problem is specific, not generic.
- The pain point describes a real friction.
- The description states behavior and boundaries.
- The value driver is concrete (time, quality, risk, revenue, etc.).

## Fast iteration mode

If user says "make it better" or similar:
1. Keep the same structure.
2. Tighten wording.
3. Add one concrete example.
4. Keep total length short.
