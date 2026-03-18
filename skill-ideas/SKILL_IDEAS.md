# LLM Agent Skills - Idea Backlog

A living index for brainstorming, evaluating, and tracking skill ideas.

## Fast Idea Workflow (Default)

Use this lightweight flow so idea capture stays easy:

1. Create one file per idea in `skill-ideas/ideas/`
2. Use `skill-ideas/IDEA_TEMPLATE.md`
3. Fill in: Problem, Pain Point, Description, Value Driver
4. Add a link under "Idea Files Index" below

Naming format:

`YYYY-MM-DD-short-kebab-name.md`

Related docs:
- `docs/SKILL_IDEA_PROCESS.md`
- `docs/SKILL_IDEA_FILE_FORMAT.md`
- `skills/skill-idea-describer/SKILL.md`

## Idea Files Index

- [2026-03-18 - Process Transcript SOP Writer](ideas/2026-03-18-process-transcript-sop-writer.md)
- [2026-03-17 - AI & Automation Agency Client Onboarding Skill](ideas/2026-03-17-ai-automation-agency-client-onboarding-skill.md)
- [2026-03-13 - Skill Idea Description Coach](ideas/2026-03-13-skill-idea-description-coach.md)
- [2026-03-13 - Filevine API Automation Skill](ideas/2026-03-13-filevine-api-automation-skill.md)

## How to Use This Document

- **Idea Phase**: Rough concepts go here with basic info
- **Ready for Dev**: Move to `backlog/` when fully scoped
- **In Progress**: Track development in dedicated skill directory
- **Completed**: Link to production skill once shipped

---

## 🌟 Ideas Queue

### Template for New Ideas
```
## [Skill Name]
- **Category**: [Data Analysis/Content/Code/Research/etc]
- **Problem Solved**: What user problem does this solve?
- **Complexity**: Low/Medium/High
- **Priority**: High/Medium/Low
- **Status**: Idea/Backlog/In Progress/Complete
- **Description**: 2-3 sentence overview
- **Key Use Cases**: 
  - Use case 1
  - Use case 2
- **Potential Implementation Approach**: How would this work?
- **Dependencies**: What tools/APIs needed?
- **Notes**: Additional context or blockers
```

---

## Ideas

### Data Analysis Skills

#### Data Validator & Cleaner
- **Category**: Data Analysis
- **Problem Solved**: Identify and fix data quality issues in CSV/JSON files
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Scans tabular data for inconsistencies (missing values, type mismatches, outliers), suggests corrections, generates cleaning report
- **Key Use Cases**:
  - Prepare messy customer data before analysis
  - Validate data imports from external sources
  - Create audit trail of data changes
- **Potential Implementation Approach**: Parse file → detect issues (pandas profiling style) → suggest fixes → apply transformations
- **Dependencies**: pandas, numpy, chardet
- **Notes**: Should handle multiple formats (CSV, JSON, Excel)

#### Time Series Forecaster
- **Category**: Data Analysis
- **Problem Solved**: Predict future values based on historical time series data
- **Complexity**: High
- **Priority**: Medium
- **Status**: Idea
- **Description**: Analyzes time series patterns and generates forecasts with confidence intervals
- **Key Use Cases**:
  - Forecast sales/revenue trends
  - Predict resource needs
  - Anomaly detection in metrics
- **Potential Implementation Approach**: ARIMA, exponential smoothing, or simple trend extrapolation
- **Dependencies**: statsmodels, scikit-learn
- **Notes**: Start with simple linear models before complex algorithms

#### Statistical Test Runner
- **Category**: Data Analysis
- **Problem Solved**: Run appropriate statistical tests to validate hypotheses
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Recommends and executes statistical tests based on data characteristics and research question
- **Key Use Cases**:
  - A/B test analysis
  - Determine if groups are significantly different
  - Validate assumptions before regression
- **Potential Implementation Approach**: Questionnaire to determine test type → run test → interpret results
- **Dependencies**: scipy, statsmodels
- **Notes**: Educational mode to explain test selection rationale

---

### Content Creation Skills

#### Multi-Format Content Converter
- **Category**: Content Creation
- **Problem Solved**: Convert single piece of content into multiple formats/styles
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Takes one content piece (blog post, article, script) and generates versions for different channels
- **Key Use Cases**:
  - Blog post → LinkedIn post, Twitter thread, email, video script
  - Research paper → Executive summary + infographic + tweet
  - Meeting notes → Action items + team email + project update
- **Potential Implementation Approach**: Parse source → extract key points → reformat for each target medium
- **Dependencies**: None (pure LLM)
- **Notes**: Should maintain tone/voice consistency

#### Tone & Style Adjuster
- **Category**: Content Creation
- **Problem Solved**: Rewrite content in a specific tone or style
- **Complexity**: Low
- **Priority**: Medium
- **Status**: Idea
- **Description**: Takes existing text and rewrites it in requested tone (formal, casual, humorous, technical, etc.)
- **Key Use Cases**:
  - Make internal memo more engaging
  - Simplify technical docs for non-experts
  - Add humor to marketing copy
- **Potential Implementation Approach**: Simple prompt engineering with examples
- **Dependencies**: None (pure LLM)
- **Notes**: Could include style library (corporate, startup, academic, etc.)

#### SEO Optimizer
- **Category**: Content Creation
- **Problem Solved**: Optimize content for search engines and readability
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Analyzes content and suggests improvements for SEO (keywords, structure, meta tags, readability)
- **Key Use Cases**:
  - Improve blog post ranking potential
  - Optimize product descriptions
  - Enhance technical documentation discoverability
- **Potential Implementation Approach**: Analyze keyword density → suggest structure → generate meta tags → check readability metrics
- **Dependencies**: Could integrate with SEO APIs
- **Notes**: Educational comments explaining recommendations

---

### Code Generation Skills

#### Code Review & Suggestions
- **Category**: Code Generation
- **Problem Solved**: Review code for bugs, style issues, and improvements
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Analyzes code and provides detailed feedback on correctness, performance, and style
- **Key Use Cases**:
  - Quick code review before commit
  - Identify potential bugs
  - Suggest performance optimizations
  - Enforce coding standards
- **Potential Implementation Approach**: AST parsing + pattern matching + LLM analysis
- **Dependencies**: Language-specific parsers
- **Notes**: Should flag security issues prominently

#### Documentation Generator
- **Category**: Code Generation
- **Problem Solved**: Auto-generate code documentation from source
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Scans code and generates docstrings, README sections, and API docs
- **Key Use Cases**:
  - Generate docstrings for existing code
  - Create API documentation
  - Build README sections
- **Potential Implementation Approach**: AST parsing → extract functions/classes → generate docs → format output
- **Dependencies**: Language-specific AST libraries
- **Notes**: Preserve user-written docs, only fill gaps

#### Database Schema Designer
- **Category**: Code Generation
- **Problem Solved**: Design database schemas from requirements
- **Complexity**: High
- **Priority**: Medium
- **Status**: Idea
- **Description**: Takes requirements and generates normalized database schema with explanations
- **Key Use Cases**:
  - Design schema from business requirements
  - Migrate from one database type to another
  - Optimize existing schema
- **Potential Implementation Approach**: Question user about entities and relationships → suggest schema → generate DDL
- **Dependencies**: None
- **Notes**: Should explain normalization choices

---

### Research Skills

#### Research Paper Summarizer
- **Category**: Research
- **Problem Solved**: Extract key findings from academic papers
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Reads research papers and generates executive summaries with methodology and key findings
- **Key Use Cases**:
  - Quickly digest research papers
  - Extract relevant papers for literature review
  - Understand methodology for replication
- **Potential Implementation Approach**: PDF parsing → section detection → selective summarization
- **Dependencies**: PyPDF2 or similar
- **Notes**: Should preserve citation information

#### Competitive Intelligence Gatherer
- **Category**: Research
- **Problem Solved**: Research competitors and market landscape
- **Complexity**: High
- **Priority**: Medium
- **Status**: Idea
- **Description**: Gathers information about competitors and creates analysis reports
- **Key Use Cases**:
  - Understand competitor positioning
  - Identify market gaps
  - Track competitor product updates
- **Potential Implementation Approach**: Web search + scraping → organize → analyze
- **Dependencies**: Web search API, scraping libraries
- **Notes**: Must respect robots.txt and terms of service

#### FAQ Generator
- **Category**: Research
- **Problem Solved**: Create FAQ from documentation or content
- **Complexity**: Low
- **Priority**: Medium
- **Status**: Idea
- **Description**: Analyzes content and generates likely questions with answers
- **Key Use Cases**:
  - Create FAQ from product docs
  - Build support resource from help articles
  - Anticipate customer questions
- **Potential Implementation Approach**: Analyze content → generate likely questions → create concise answers
- **Dependencies**: None (pure LLM)
- **Notes**: Should solicit real questions from users to validate

---

### Communication Skills

#### Email Template Generator
- **Category**: Communication
- **Problem Solved**: Generate professional email templates for common scenarios
- **Complexity**: Low
- **Priority**: High
- **Status**: Idea
- **Description**: Creates email templates for business scenarios (follow-up, rejection, negotiation, etc.)
- **Key Use Cases**:
  - Draft difficult emails (layoffs, rejections)
  - Professional follow-up templates
  - Negotiation starting points
- **Potential Implementation Approach**: Template library + contextual customization
- **Dependencies**: None
- **Notes**: Include tone guidance (formal, warm, firm, etc.)

#### Meeting Minutes Processor
- **Category**: Communication
- **Problem Solved**: Convert meeting transcripts into structured notes
- **Complexity**: Medium
- **Priority**: High
- **Status**: Idea
- **Description**: Takes meeting transcript/recording and generates agenda, decisions, action items, and next steps
- **Key Use Cases**:
  - Automatically structure meeting notes
  - Extract action items with owners
  - Create internal communication summary
  - Archive decision log
- **Potential Implementation Approach**: Transcription → section detection → extraction → formatting
- **Dependencies**: Optional speech-to-text API
- **Notes**: Should be smart about grouping related items

#### Stakeholder Communication Planner
- **Category**: Communication
- **Problem Solved**: Plan communication strategy for different stakeholders
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Takes a message/update and creates tailored versions for different stakeholder groups
- **Key Use Cases**:
  - Product launch communication across org levels
  - Status updates customized by audience
  - Change management communication
- **Potential Implementation Approach**: Analyze message → identify stakeholders → create versions → suggest channels
- **Dependencies**: None (pure LLM)
- **Notes**: Include timing recommendations

---

### Planning & Project Management Skills

#### Project Roadmap Generator
- **Category**: Planning
- **Problem Solved**: Create prioritized product/project roadmaps
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Takes project requirements and generates structured roadmap with timelines and dependencies
- **Key Use Cases**:
  - Create product roadmap from requirements
  - Break down projects into phases
  - Identify critical path
- **Potential Implementation Approach**: Parse requirements → dependency analysis → scheduling → visualization
- **Dependencies**: Could integrate with project management APIs
- **Notes**: Should handle uncertainty and dependencies

#### OKR Framework Builder
- **Category**: Planning
- **Problem Solved**: Create OKRs (Objectives & Key Results) from business goals
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Helps define clear OKRs with measurable key results
- **Key Use Cases**:
  - Create quarterly OKRs for teams
  - Align company goals top-down
  - Track progress against OKRs
- **Potential Implementation Approach**: Questionnaire about goals → suggest OKRs → review for SMART criteria
- **Dependencies**: None
- **Notes**: Educational - explain why certain OKRs work better

#### Risk Assessment & Mitigation Planner
- **Category**: Planning
- **Problem Solved**: Identify risks and create mitigation strategies
- **Complexity**: Medium
- **Priority**: Medium
- **Status**: Idea
- **Description**: Analyzes projects/plans and identifies potential risks with mitigation approaches
- **Key Use Cases**:
  - Risk assessment before project kickoff
  - Due diligence for investments
  - Contingency planning
- **Potential Implementation Approach**: Ask about project/context → identify risks → assess probability/impact → suggest mitigations
- **Dependencies**: None
- **Notes**: Should prioritize by risk score

---

### Automation & Workflow Skills

#### Task Scheduler & Orchestrator
- **Category**: Automation
- **Problem Solved**: Schedule and orchestrate multi-step workflows
- **Complexity**: High
- **Priority**: Medium
- **Status**: Idea
- **Description**: Creates automation workflows that coordinate multiple skills/tools
- **Key Use Cases**:
  - Weekly report generation (gather data → analyze → format → send)
  - Customer onboarding automation
  - Data pipeline orchestration
- **Potential Implementation Approach**: Workflow definition language → task execution → error handling → logging
- **Dependencies**: Task queue system (Celery, RQ)
- **Notes**: Critical for enterprise use cases

#### Template & Variable Substitution Engine
- **Category**: Automation
- **Problem Solved**: Process templates with dynamic variable substitution
- **Complexity**: Low
- **Priority**: Low
- **Status**: Idea
- **Description**: Manages template libraries and handles variable substitution for documents, emails, etc.
- **Key Use Cases**:
  - Mail merge for bulk communications
  - Generate customized documents
  - Populate config files from templates
- **Potential Implementation Approach**: Template parsing → variable detection → safe substitution
- **Dependencies**: Jinja2 or similar
- **Notes**: Should handle conditional logic in templates

---

## Skill Status Summary

| Category | Total | Idea | Backlog | In Progress | Complete |
|----------|-------|------|---------|-------------|----------|
| Data Analysis | 3 | 3 | - | - | - |
| Content Creation | 3 | 3 | - | - | - |
| Code Generation | 3 | 3 | - | - | - |
| Research | 3 | 3 | - | - | - |
| Communication | 3 | 3 | - | - | - |
| Planning | 3 | 3 | - | - | - |
| Automation | 2 | 2 | - | - | - |
| **TOTAL** | **20** | **20** | **0** | **0** | **0** |

---

## Quick Filters

### High Priority Ideas (Ready to Scope)
- [ ] Data Validator & Cleaner
- [ ] Multi-Format Content Converter
- [ ] Code Review & Suggestions
- [ ] Documentation Generator
- [ ] Research Paper Summarizer
- [ ] Email Template Generator
- [ ] Meeting Minutes Processor

### Good First Skills (Low Complexity)
- [ ] Tone & Style Adjuster
- [ ] FAQ Generator
- [ ] Email Template Generator
- [ ] Template & Variable Substitution Engine

### Enterprise-Ready (High Impact)
- [ ] Task Scheduler & Orchestrator
- [ ] Data Validator & Cleaner
- [ ] Code Review & Suggestions
- [ ] Meeting Minutes Processor

---

## Discussion & Notes

Use this section for ideas that are too rough for their own entry, temporary notes, or cross-skill considerations.

- **Cross-skill opportunity**: Many skills could use a common "quality assessment" layer
- **Infrastructure need**: Building Task Scheduler will unlock several automation skills
- **Integration priority**: Should investigate APIs early for competitive intelligence and research skills

---

Last updated: 2026-03-12
