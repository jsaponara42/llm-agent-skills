# Skill Anatomy: How Skills Are Structured

This document explains the architecture and components of an LLM agent skill.

## What Is a Skill?

A **skill** is a reusable, well-defined capability that an LLM agent can invoke to accomplish a specific task. It's the bridge between an LLM's reasoning abilities and concrete actions.

### Characteristics of a Skill
- **Focused**: Does one thing well
- **Documented**: Clear specs and examples
- **Robust**: Handles errors gracefully
- **Composable**: Works with other skills
- **Observable**: Logging and metrics
- **Tested**: Reliable and predictable
- **Maintainable**: Clean code, clear structure

---

## Skill Components

### 1. Specification Document (SKILL.md)

**Purpose**: Defines what the skill does, how it works, and when to use it.

**Key Sections**:
```
├─ Overview (Purpose, Category, Status)
├─ Problem Statement (What problem does it solve?)
├─ Specification (Inputs, Outputs, Dependencies)
├─ Use Cases (When and why to use it)
├─ Implementation Approach (How it works)
├─ Examples (Real usage scenarios)
├─ Edge Cases & Limitations (What it doesn't do)
└─ Integration (How it works with other skills)
```

**Audience**: Everyone - helps understand the skill before using it.

### 2. Implementation Code

**Purpose**: The actual code that executes the skill.

**Typical Structure**:
```python
# src/skill_name.py

import logging
from dataclasses import dataclass
from typing import List, Dict

logger = logging.getLogger(__name__)

@dataclass
class InputType:
    """Structure of input data."""
    field1: str
    field2: int

@dataclass
class OutputType:
    """Structure of output data."""
    result: str
    metadata: Dict

class SkillName:
    """Implements the skill with all necessary methods."""
    
    def __init__(self, config: Config = None):
        """Initialize skill with optional configuration."""
        self.config = config or default_config()
    
    def execute(self, input_data: InputType) -> OutputType:
        """Main entry point for the skill."""
        logger.info("Starting skill execution")
        
        # Validate inputs
        self._validate(input_data)
        
        # Process
        result = self._process(input_data)
        
        # Format and return
        return self._format_output(result)
    
    def _validate(self, input_data: InputType) -> None:
        """Validate input before processing."""
        if not input_data.field1:
            raise ValueError("field1 is required")
    
    def _process(self, input_data: InputType) -> Dict:
        """Core logic of the skill."""
        logger.debug(f"Processing {input_data}")
        return {}
    
    def _format_output(self, result: Dict) -> OutputType:
        """Format result for output."""
        return OutputType(result=str(result))

# Module-level function for quick access
def execute(input_data: InputType) -> OutputType:
    """Quick way to use the skill."""
    skill = SkillName()
    return skill.execute(input_data)
```

**Key Attributes**:
- Clear input/output types
- Explicit error handling
- Logging at appropriate levels
- Documented methods
- Testable components

### 3. Tests

**Purpose**: Ensure the skill works as expected.

**Test Structure**:
```python
# tests/test_skill_name.py

import pytest
from src.skill_name import SkillName, InputType, OutputType

class TestSkillName:
    
    @pytest.fixture
    def skill(self):
        """Create skill instance for tests."""
        return SkillName()
    
    @pytest.fixture
    def valid_input(self):
        """Provide valid test input."""
        return InputType(field1="test", field2=42)
    
    def test_valid_input(self, skill, valid_input):
        """Test with valid input."""
        output = skill.execute(valid_input)
        assert output.result is not None
    
    def test_invalid_input(self, skill):
        """Test error handling."""
        invalid = InputType(field1="", field2=-1)
        with pytest.raises(ValueError):
            skill.execute(invalid)
    
    def test_edge_case_large_input(self, skill):
        """Test with large input."""
        large_input = InputType(field1="x" * 1000000, field2=999999)
        output = skill.execute(large_input)
        assert output is not None
```

**Coverage**:
- Happy path (valid input → expected output)
- Error cases (invalid input → error)
- Edge cases (boundary conditions)
- Performance (if critical)

### 4. Examples

**Purpose**: Show how to use the skill in real scenarios.

**Example Files**:
```python
# examples/basic_usage.py
"""
Basic example of using the skill.
"""

from src.skill_name import SkillName, InputType

# Create skill instance
skill = SkillName()

# Prepare input
input_data = InputType(field1="example", field2=100)

# Execute
output = skill.execute(input_data)

# Use results
print(f"Result: {output.result}")
print(f"Metadata: {output.metadata}")
```

```python
# examples/advanced_usage.py
"""
Advanced examples showing configuration and integration.
"""

from src.skill_name import SkillName, InputType, Config

# Custom configuration
config = Config(
    option1="value",
    option2=42
)

skill = SkillName(config=config)

# Use with different inputs
for i in range(10):
    input_data = InputType(field1=f"item_{i}", field2=i)
    output = skill.execute(input_data)
    print(output)
```

### 5. Documentation

**Purpose**: Help users understand and use the skill.

**README.md**:
```markdown
# Skill Name

One sentence describing what this does.

## Why Use This?

Problem it solves and when you'd need it.

## Quick Start

```python
from skill import execute

result = execute(input_data)
```

## Configuration

Document all config options:
- `option1`: Description (default: value)
- `option2`: Description (default: value)

## Examples

Real-world usage examples.

## Limitations

What this skill doesn't do.

## API Reference

See [API.md](docs/API.md)
```

**API.md**:
- Full function/class documentation
- Parameter types and constraints
- Return value structure
- Possible errors
- Code examples

---

## Skill Lifecycle

### Phase 1: Idea
```
↓ In SKILL_IDEAS.md
```

### Phase 2: Specification
```
↓ Create detailed spec (SKILL.md)
↓ Define inputs/outputs
↓ Outline implementation approach
```

### Phase 3: Implementation
```
↓ Write code (src/)
↓ Write tests (tests/)
↓ Write examples (examples/)
↓ Create documentation (docs/)
```

### Phase 4: Testing & QA
```
↓ Ensure all tests pass
↓ Manual testing
↓ Edge case verification
↓ Performance validation
```

### Phase 5: Release
```
↓ Update SKILL_IDEAS.md (mark Complete)
↓ Create versioned release
↓ Update repository README
↓ Announce to users
```

### Phase 6: Maintenance
```
↓ Monitor usage and feedback
↓ Fix bugs promptly
↓ Improve documentation based on questions
↓ Plan future enhancements
```

---

## Skill Dependencies

### Internal Dependencies
Skills can depend on other skills.

**Example**:
```python
from skills.data_analysis.validator import DataValidator

class DataCleaner:
    def __init__(self):
        self.validator = DataValidator()
    
    def clean(self, data):
        # First validate
        report = self.validator.validate(data)
        
        # Then clean based on report
        return self._apply_fixes(data, report)
```

### External Dependencies
Document clearly.

```python
# requirements.txt
pandas>=1.0.0
numpy>=1.18.0
scikit-learn>=0.24.0

# In SKILL.md:
## Dependencies
- pandas: For data manipulation
- numpy: For numerical operations
- scikit-learn: For machine learning models
```

---

## Configuration Pattern

### Default Configuration
```python
from dataclasses import dataclass

@dataclass
class Config:
    """Configuration for the skill."""
    
    # Data validation
    strict_mode: bool = False
    """If True, fail on any error. If False, continue with warnings."""
    
    # Processing
    max_iterations: int = 100
    """Maximum iterations in algorithms."""
    
    # Output
    verbose: bool = False
    """If True, print debug information."""
    
    def validate(self):
        """Ensure configuration is valid."""
        if self.max_iterations < 1:
            raise ValueError("max_iterations must be >= 1")

def default_config() -> Config:
    """Return default configuration."""
    return Config()
```

### Usage
```python
# Use defaults
skill = SkillName()

# Customize
config = Config(
    strict_mode=True,
    max_iterations=500
)
skill = SkillName(config=config)
```

---

## Logging Pattern

```python
import logging

logger = logging.getLogger(__name__)

def execute(data):
    logger.debug("Starting execution with data: %s", data)
    
    try:
        result = process(data)
        logger.info("Successfully processed %d items", len(result))
        return result
    except ValueError as e:
        logger.warning("Invalid data format: %s", e)
        raise
    except Exception as e:
        logger.error("Unexpected error: %s", e, exc_info=True)
        raise
```

**Log Levels**:
- **DEBUG**: Detailed info for debugging
- **INFO**: Successful operations and milestones
- **WARNING**: Something unexpected but handled
- **ERROR**: Something went wrong
- **CRITICAL**: System-level failures

---

## Error Handling Pattern

```python
class SkillError(Exception):
    """Base error for this skill."""
    def __init__(self, message: str, details: Dict = None):
        super().__init__(message)
        self.details = details or {}

class ValidationError(SkillError):
    """Input validation failed."""
    pass

class ProcessingError(SkillError):
    """Something went wrong during processing."""
    pass

def execute(data):
    # Validate
    if not data:
        raise ValidationError("Input data is empty")
    
    # Process with error handling
    try:
        result = complex_operation(data)
    except SomeLibraryError as e:
        raise ProcessingError(
            f"Operation failed: {e}",
            details={"original_error": str(e)}
        )
    
    return result
```

---

## Type Hints

Use type hints throughout for clarity.

```python
from typing import List, Dict, Optional, Callable, Union

def skill_function(
    required_param: str,
    optional_param: Optional[int] = None,
    items: List[str] = None,
    callback: Callable[[str], None] = None
) -> Dict[str, Union[int, str]]:
    """Function with complete type hints."""
    pass
```

---

## Documentation Checklist

For each skill, ensure:
- [ ] README.md exists and is clear
- [ ] SKILL.md is complete
- [ ] All functions have docstrings
- [ ] Examples are correct and runnable
- [ ] Configuration options documented
- [ ] Error cases documented
- [ ] Limitations stated clearly
- [ ] Integration points shown
- [ ] Version history tracked

---

## Directory Structure Recap

```
skills/[category]/[skill-name]/
├── README.md                      # Quick start
├── SKILL.md                       # Full specification
├── pyproject.toml or setup.py    # Installation config
├── requirements.txt              # Dependencies
├── src/
│   ├── __init__.py
│   ├── [skill_name].py           # Main implementation
│   ├── [skill_name]_config.py    # Configuration
│   └── errors.py                 # Custom errors
├── tests/
│   ├── __init__.py
│   ├── test_[skill_name].py      # Main tests
│   ├── test_edge_cases.py        # Edge case tests
│   ├── test_integration.py       # Integration tests
│   └── fixtures/
│       ├── valid_data.json
│       ├── invalid_data.json
│       └── edge_cases.json
├── examples/
│   ├── basic_usage.py
│   ├── advanced_usage.py
│   └── integration_example.py
└── docs/
    ├── API.md                    # API reference
    ├── TROUBLESHOOTING.md        # Known issues
    └── FAQ.md                    # Common questions
```

---

## Summary

A well-structured skill:
1. **Specification**: Clear SKILL.md defining everything
2. **Implementation**: Clean, tested code
3. **Documentation**: README + API docs + examples
4. **Tests**: Comprehensive coverage
5. **Examples**: Real-world usage
6. **Logging**: Observable behavior
7. **Errors**: Handled gracefully
8. **Composability**: Works with other skills

Following this anatomy makes skills maintainable, understandable, and reusable.

---

**Last Updated**: 2026-03-12
