---
name: process-transcript-sop-writer
description: Convert process transcripts or rough workflow descriptions into clear, beginner-friendly standard operating procedures (SOPs). Use whenever the user shares steps involving tools, programs, files, folders, handoffs, triggers, or automations and wants documentation others can follow without technical knowledge. Always ask focused follow-up questions for missing context before finalizing.
---

# Process Transcript SOP Writer

Turn a raw process description into a complete, easy-to-follow SOP for non-technical readers.

## When to use this skill

Use this skill when the user asks for any of the following:
- "Turn this transcript into an SOP"
- "Document my automation process"
- "Write step-by-step instructions for my team"
- "Map how these tools/files/folders connect"
- "Create a process guide from this workflow description"

## When not to use this skill

Do not use this skill when:
- The user asks for code implementation instead of documentation
- The user only wants a short summary (not an SOP)
- The user asks for legal/compliance policy authoring beyond the process details provided

## Inputs

### Required
- A transcript, voice-to-text dump, notes, or written description of the process

### Strongly recommended
- Tool names and account/platform names
- File and folder names/locations
- Trigger events (what starts the process)
- Input/output artifacts for each stage
- Owner or role responsible for each step
- Error and exception handling behavior

### Assumptions
- Audience has low technical knowledge
- The SOP should prioritize clarity, safety, and repeatability

## Output contract

If required context is complete, output a full SOP using this structure:

```markdown
# [Process Name] - Standard Operating Procedure

## 1) Purpose (Plain Language)
## 2) Who This Is For
## 3) Tools and Access Required
## 4) Files and Folders Used
## 5) Before You Start Checklist
## 6) Step-by-Step Procedure
## 7) How the Pieces Connect (System Flow)
## 8) Quality Checks and Success Criteria
## 9) Common Issues and Fixes
## 10) Critical Dependencies and Change Warnings
## 11) Change Log and Ownership
```

If context is missing, do **not** finalize the SOP. Instead output:

```markdown
## Missing Information Needed Before SOP Can Be Finalized
- [Specific missing item]

## Clarifying Questions
1. ...
2. ...
3. ...
```

## Workflow

1. Read the process transcript and extract all explicit steps, tools, files, folders, inputs, outputs, owners, and dependencies.
2. Compare extracted details against `references/intake-checklist.md`.
3. Identify missing required context.
4. If key context is missing, ask concise clarifying questions and pause finalization.
5. If context is sufficient, draft the SOP using simple language:
   - Short sentences
   - Define technical terms in plain English
   - Include concrete examples where helpful
6. In **How the Pieces Connect (System Flow)**, explain how each tool/file/folder passes work to the next step.
7. In **Critical Dependencies and Change Warnings**, explicitly list items that should not be changed casually, why changes can break automation, and what to do before any change.
8. Review for readability and completeness, then deliver the final SOP.

## Quality bar

Before finalizing, verify:
- The SOP can be followed by a non-technical reader without guessing.
- Every step includes action, owner/role (if known), and expected result.
- Tool/file/folder handoffs are explicit.
- Missing context is surfaced as questions (not hidden assumptions).
- The dependency warning section is present and specific.

## Edge cases

- Transcript is messy, repetitive, or out of order: normalize into ordered steps and note assumptions.
- Multiple versions of the same tool/process are mentioned: ask which version is current.
- Paths, file names, or credentials are vague: request exact names/locations before finalization.
- Critical dependencies are implied but not explicit: ask targeted dependency questions.
- User asks for very technical output: keep core SOP plain-language, then add an optional technical appendix only if requested.

## Reference files

- `references/intake-checklist.md`: Read before finalizing to validate missing context and required SOP sections.

## Test prompts

```json
{
  "skill_name": "process-transcript-sop-writer",
  "evals": [
    {
      "id": 1,
      "prompt": "Turn this transcript into an SOP for my non-technical operations assistant. Make sure it includes what not to change: [transcript content here]",
      "expected_output": "Returns either a full plain-language SOP with critical dependency warnings or asks clear missing-context questions first.",
      "files": [],
      "expectations": []
    },
    {
      "id": 2,
      "prompt": "I use Zapier, Google Drive folders, and Airtable. Here is the process transcript. Document exactly how data flows and where handoffs happen.",
      "expected_output": "Produces a step-by-step SOP with a dedicated system-flow section and explicit file/folder usage.",
      "files": [],
      "expectations": []
    },
    {
      "id": 3,
      "prompt": "Write the SOP from this rough voice transcript, but keep it understandable for someone with no technical background.",
      "expected_output": "Produces beginner-friendly SOP language and surfaces missing items through clarifying questions when needed.",
      "files": [],
      "expectations": []
    }
  ]
}
```
