# Skill Implementation Checklist

Use this checklist for a skill-creator style workflow.

## 1. Scope And Intent

- [ ] Define what the skill enables the assistant to do.
- [ ] Define when the skill should trigger.
- [ ] Define output expectations and quality bar.
- [ ] Capture edge cases and explicit non-goals.

## 2. Draft The Skill

- [ ] Create `skills/<skill-name>/SKILL.md` from `templates/SKILL_TEMPLATE.md`.
- [ ] Add frontmatter with `name` and `description`.
- [ ] Keep the description explicit about trigger context.
- [ ] Write concise, imperative workflow steps.
- [ ] Add references to optional files under `references/`, `scripts/`, and `assets/`.

## 3. Create Initial Evals

- [ ] Create `skills/<skill-name>/evals/evals.json` with 2-3 realistic prompts.
- [ ] Include `expected_output` for each eval.
- [ ] Add `files` entries when prompts depend on specific inputs.
- [ ] Add `expectations` only when they are objectively verifiable.

## 4. Run With-Skill And Baseline

- [ ] Create a workspace directory for run artifacts.
- [ ] Run with-skill outputs for every eval.
- [ ] Run baseline outputs for every eval.
- [ ] Save outputs per eval in stable, consistent directories.
- [ ] Record timing/token metadata for each run.

## 5. Grade And Benchmark

- [ ] Grade each run against expectations.
- [ ] Save `grading.json` per run with `text`, `passed`, and `evidence` fields.
- [ ] Aggregate results into `benchmark.json`.
- [ ] Review pass rate, variance, latency, and token tradeoffs.
- [ ] Flag weak or non-discriminating expectations.

## 6. Human Review Loop

- [ ] Present outputs for qualitative review.
- [ ] Capture feedback in `feedback.json`.
- [ ] Apply improvements to SKILL.md and resources.
- [ ] Re-run evals in a new iteration directory.
- [ ] Repeat until quality targets are met.

## 7. Description Optimization (Optional)

- [ ] Build trigger eval queries (should-trigger and should-not-trigger).
- [ ] Run description optimization loop.
- [ ] Apply improved description to SKILL.md frontmatter.
- [ ] Verify improved trigger precision and recall.

## 8. Validation And Packaging

- [ ] Validate frontmatter and naming conventions.
- [ ] Validate description length and format constraints.
- [ ] Remove unnecessary artifacts from package.
- [ ] Build distributable `.skill` package.
- [ ] Verify package installs and runs correctly.

## 9. Repository Updates

- [ ] Add or update docs for the new skill.
- [ ] Add links in root docs if needed.
- [ ] Commit with a clear message and changelog note.

## Recommended Skill Folder Layout

```text
skills/<skill-name>/
├── SKILL.md
├── LICENSE.txt                 (optional)
├── evals/
│   └── evals.json
├── references/                 (optional)
│   └── schemas.md
├── scripts/                    (optional)
│   └── *.py
└── assets/                     (optional)
    └── *.html
```

**Last Updated**: 2026-03-13
