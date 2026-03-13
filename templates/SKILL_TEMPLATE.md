---
name: your-skill-name
description: Describe what this skill does and when the assistant should use it. Include both capability and trigger context.
license: Optional. Add if you include a LICENSE.txt file.
compatibility: Optional. Required tools or environment constraints.
---

# Your Skill Name

Copy this file into a skill folder and replace all placeholder content.

## Purpose

State the user outcome this skill is designed to produce.

## When To Use This Skill

List the situations and user phrasing that should trigger the skill.

- Trigger example 1
- Trigger example 2
- Trigger example 3

## When Not To Use This Skill

List adjacent cases that should not trigger this skill.

- Non-trigger example 1
- Non-trigger example 2

## Inputs

Define what the skill expects from the user.

- Required inputs
- Optional inputs
- Assumptions

## Output Contract

Define what the final output must contain.

Use this format when output shape matters:

```markdown
# [Title]
## [Section 1]
## [Section 2]
## [Section 3]
```

## Workflow

Use imperative steps with explicit sequencing.

1. Validate input and constraints.
2. Choose approach based on user intent.
3. Perform the core task.
4. Check output quality against requirements.
5. Return final output in the required format.

## Quality Bar

Define objective checks before completion.

- Check 1
- Check 2
- Check 3

## Edge Cases

Document tricky scenarios and expected handling.

- Edge case 1 and handling
- Edge case 2 and handling

## Reference Files

If this skill has additional files, tell the model when to read each one.

- `references/domain-a.md`: Read when request is in domain A.
- `references/domain-b.md`: Read when request is in domain B.
- `scripts/transform.py`: Run for deterministic transforms.

## Test Prompts

Start with 2-3 realistic prompts and expand later.

```json
{
  "skill_name": "your-skill-name",
  "evals": [
    {
      "id": 1,
      "prompt": "Realistic user request",
      "expected_output": "Concrete success condition",
      "files": [],
      "expectations": []
    }
  ]
}
```

## Notes For Maintainers

- Keep SKILL.md concise and action-oriented.
- Move large, detailed guidance to `references/`.
- Keep examples realistic, not toy prompts.
