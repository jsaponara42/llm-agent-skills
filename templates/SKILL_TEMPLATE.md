# Skill Template: [Skill Name]

> **Copy this file as a starting point for new skills. Replace [Skill Name] and fill in all sections.**

## Overview

### Purpose
One sentence describing what this skill does and the problem it solves.

### Category
[Data Analysis / Content Creation / Code Generation / Research / Communication / Planning / Automation]

### Complexity
[Low / Medium / High]

### Status
[Idea / Backlog / In Progress / Complete]

---

## Problem Statement

### The Problem
Describe the specific problem this skill solves. Who needs it? Why does it matter?

### Success Criteria
What does success look like? List 3-5 measurable outcomes.
- Criterion 1
- Criterion 2
- Criterion 3

---

## Skill Specification

### Inputs
Describe what data/parameters the skill accepts.

**Example Input**:
```
{
  "input_type": "description of input",
  "format": "format specification",
  "example": "sample data"
}
```

### Outputs
Describe what the skill produces.

**Example Output**:
```
{
  "result_type": "description",
  "format": "format specification",
  "example": "sample output"
}
```

### Dependencies
- **Required Libraries**: List any external dependencies
- **Required Tools/APIs**: List any external services or APIs
- **System Requirements**: Memory, compute, etc.

---

## Use Cases

### Primary Use Cases
1. **Use Case 1**: Brief description
   - Scenario: When would someone use this?
   - Value: What benefit do they get?
   - Expected Input/Output: Quick example

2. **Use Case 2**: Brief description
   - Scenario: 
   - Value: 
   - Expected Input/Output: 

### Secondary Use Cases
Additional use cases that are possible but not primary focus.

---

## Implementation Approach

### High-Level Algorithm
Describe the step-by-step approach to implementing this skill.

1. Step 1: Description
2. Step 2: Description
3. Step 3: Description
4. (Continue as needed)

### Key Components
- **Component 1**: Purpose and responsibility
- **Component 2**: Purpose and responsibility
- **Component 3**: Purpose and responsibility

### Architecture Diagram
```
[Provide ASCII diagram showing how components interact]

Input
  ↓
[Parse/Validate]
  ↓
[Process Core Logic]
  ↓
[Format Output]
  ↓
Output
```

---

## Examples

### Example 1: [Scenario Name]

**Input**:
```
[example input data]
```

**Process**:
[Brief explanation of what happens]

**Output**:
```
[example output data]
```

### Example 2: [Scenario Name]

**Input**:
```
[example input data]
```

**Process**:
[Brief explanation of what happens]

**Output**:
```
[example output data]
```

---

## Edge Cases & Limitations

### Known Edge Cases
- **Edge Case 1**: Describe edge case and how it's handled
- **Edge Case 2**: Describe edge case and how it's handled
- **Edge Case 3**: Describe edge case and how it's handled

### Limitations
- **Limitation 1**: What this skill does NOT do
- **Limitation 2**: Known constraints or restrictions
- **Limitation 3**: Scope boundaries

### Failure Modes
- **Scenario**: When skill fails and how it fails gracefully
- **Recovery**: How to recover from common failures
- **User Impact**: What users experience when something goes wrong

---

## Quality Assurance

### Test Cases
- [ ] Test Case 1: [Description]
- [ ] Test Case 2: [Description]
- [ ] Test Case 3: [Description]
- [ ] Edge case handling
- [ ] Error handling
- [ ] Performance under load

### Performance Metrics
- **Latency**: Target response time
- **Throughput**: Items processed per unit time
- **Accuracy**: Expected accuracy rate (if applicable)

### Validation Checklist
- [ ] Inputs validated properly
- [ ] Outputs match specification
- [ ] Error handling works
- [ ] Documentation complete
- [ ] Examples run successfully
- [ ] Edge cases handled

---

## Integration

### Dependencies on Other Skills
Does this skill depend on or compose with other skills?
- Skill A: How it's used
- Skill B: How it's used

### Integration Points
How would this skill be called from other systems?

```python
# Example usage
from skills import [skill_name]

result = [skill_name].execute(
    input_param1=value1,
    input_param2=value2
)
```

### Configuration
What configuration options should be available?
- `config_option_1`: Description and default value
- `config_option_2`: Description and default value

---

## Development Notes

### Implementation Considerations
- What are the trickiest parts to implement?
- Any libraries or approaches to prioritize?
- Known gotchas or tricky interactions?

### Future Enhancements
- [ ] Enhancement 1: Description
- [ ] Enhancement 2: Description
- [ ] Enhancement 3: Description

### Open Questions
- Question 1: Description
- Question 2: Description

---

## Status History

| Date | Status | Notes |
|------|--------|-------|
| YYYY-MM-DD | Idea | Initial concept created |
| YYYY-MM-DD | Backlog | Scoped and ready for implementation |
| YYYY-MM-DD | In Progress | Development started |
| YYYY-MM-DD | Complete | Initial version shipped |

---

## Resources & References

### Related Documentation
- Link or reference to related docs

### Similar Solutions
- External tool/skill 1: How it differs
- External tool/skill 2: How it differs

### References
- Link 1: Citation or reference
- Link 2: Citation or reference

---

## Author Notes

Add any additional context, rationale, or notes here.

---

**Last Updated**: YYYY-MM-DD  
**Author**: [Your Name]  
**Version**: 1.0
