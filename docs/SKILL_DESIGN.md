# Skill Design Best Practices

Principles and patterns for designing high-quality, maintainable LLM agent skills.

## Core Design Principles

### 1. Single Responsibility
Each skill should do ONE thing well.

**✅ Good**:
- Data Validator: Validates and reports on data quality issues
- Code Reviewer: Reviews code for bugs and style issues
- Email Generator: Creates email templates for common scenarios

**❌ Bad**:
- Universal Tool: Does data validation, code review, AND email generation
- Everything Processor: Handles any kind of input and produces output

### 2. Clear Input/Output Contract
Explicit about what goes in and what comes out.

**Specification**:
```python
def skill_function(input_data: InputType) -> OutputType:
    """
    Clear description of what this does.
    
    Args:
        input_data: Exact specification of input format
        
    Returns:
        Exact specification of output format
        
    Raises:
        SpecificError: When and why this error occurs
    """
```

**Example**:
```python
def validate_data(csv_path: str) -> ValidationReport:
    """
    Validates CSV data quality.
    
    Args:
        csv_path: Path to CSV file to validate
        
    Returns:
        ValidationReport with issues found, severity, and suggestions
        
    Raises:
        FileNotFoundError: If file doesn't exist
        ValueError: If file is not valid CSV format
    """
```

### 3. Composability
Skills should work well together.

**Design for Composition**:
- Use standard formats (JSON, CSV, plain text) not custom proprietary formats
- Document dependencies clearly
- Make output of one skill compatible with input of another
- Avoid hardcoded paths or environment dependencies

**Example Chain**:
```
Data File 
  → Data Validator 
  → Data Cleaner 
  → Data Analyzer 
  → Report Generator
```

### 4. Graceful Degradation
Handle errors without catastrophic failure.

**Error Handling Levels**:
1. **Validation**: Reject invalid inputs immediately with clear message
2. **Warnings**: Continue with partial results, warn user
3. **Failure**: Can't proceed, provide useful error message
4. **Logging**: Log everything for debugging

**Example**:
```python
def analyze_data(data):
    # Level 1: Validation
    if not data:
        raise ValueError("Data cannot be empty")
    
    # Level 2: Warnings
    if has_missing_values(data):
        logger.warning("Data has missing values, using imputation")
        data = impute_missing(data)
    
    # Level 3: Core logic
    try:
        results = perform_analysis(data)
    except AnalysisError as e:
        logger.error(f"Analysis failed: {e}")
        raise
    
    return results
```

### 5. Observability
Design for understanding behavior and debugging.

**Logging Strategy**:
```python
logger.debug("Starting validation with 5000 rows")
logger.info("Found 47 rows with missing values")
logger.warning("3 columns have >50% missing data")
logger.error("Cannot proceed without timestamp column")
```

**Metrics to Track**:
- Time to execute
- Success vs. failure rate
- Common error patterns
- Resource usage

### 6. Testability
Easy to test = fewer bugs.

**Design for Testing**:
- Pure functions preferred (same input → same output)
- Inject dependencies, don't hard-code them
- Provide test fixtures/examples
- Mock external calls (APIs, files, etc.)
- Test edge cases and error paths

**Example**:
```python
# Good: Testable
def format_output(data, formatter=None):
    formatter = formatter or JSONFormatter()
    return formatter.format(data)

# Bad: Hard to test
def format_output(data):
    formatter = JSONFormatter(config_from_env())
    return formatter.format(data)
```

---

## Skill Structure Patterns

### Pattern 1: Validation → Processing → Formatting
Most common pattern.

```
1. Validate Inputs
   ├─ Type checking
   ├─ Range checking
   └─ Format checking
2. Process Core Logic
   ├─ Transform data
   ├─ Apply business logic
   └─ Handle edge cases
3. Format & Return
   ├─ Structure output
   ├─ Add metadata
   └─ Return in expected format
```

### Pattern 2: Analyze → Suggest → Apply
For improvement/optimization skills.

```
1. Analyze Current State
   ├─ Gather metrics
   ├─ Identify issues
   └─ Score severity
2. Generate Suggestions
   ├─ Brainstorm fixes
   ├─ Rank by impact
   └─ Estimate effort
3. Apply & Report
   ├─ Apply changes (optional)
   ├─ Generate report
   └─ Show before/after
```

### Pattern 3: Query → Gather → Synthesize
For research/analysis skills.

```
1. Parse Query/Requirements
   ├─ Understand what's needed
   ├─ Set search parameters
   └─ Define success criteria
2. Gather Information
   ├─ Search/fetch data
   ├─ Deduplicate
   └─ Filter relevant
3. Synthesize Results
   ├─ Organize findings
   ├─ Generate summary
   └─ Provide citations
```

---

## API Design Patterns

### Simple: Single Function
For straightforward skills.

```python
def validate_data(data_path: str) -> ValidationReport:
    """Validate CSV file and return report."""
    pass
```

### Moderate: Class with Methods
For skills with state or multiple operations.

```python
class DataValidator:
    def __init__(self, config: Config):
        self.config = config
    
    def validate(self, data_path: str) -> ValidationReport:
        """Validate data."""
        pass
    
    def fix(self, data_path: str, report: ValidationReport) -> str:
        """Fix issues in data based on report."""
        pass
    
    def report(self, report: ValidationReport) -> str:
        """Generate human-readable report."""
        pass
```

### Complex: Builder Pattern
For skills with many options.

```python
analyzer = (AnalysisBuilder()
    .with_input_file('data.csv')
    .with_method('clustering')
    .with_k_clusters(5)
    .with_output_format('json')
    .build())

results = analyzer.execute()
```

---

## Configuration Management

### Keep It Simple
```python
# Good: Sensible defaults
def clean_data(data, remove_nulls=True, remove_duplicates=True):
    pass

# Better: Config object
config = CleaningConfig(
    remove_nulls=True,
    remove_duplicates=True,
    threshold=0.95
)
cleaned = clean_data(data, config)
```

### Validation
```python
@dataclass
class Config:
    threshold: float  # 0-1
    
    def __post_init__(self):
        if not 0 <= self.threshold <= 1:
            raise ValueError("threshold must be between 0 and 1")
```

### Documentation
Every config option should document:
- What it does
- Valid values/range
- Default value
- Impact/side effects

---

## Error Handling Philosophy

### Error Hierarchy
```python
class SkillError(Exception):
    """Base error for this skill."""
    pass

class ValidationError(SkillError):
    """Input validation failed."""
    pass

class ProcessingError(SkillError):
    """Something went wrong during processing."""
    pass
```

### Error Messages
Make them useful!

**❌ Bad**:
```
Error: Failed
```

**✅ Good**:
```
ValidationError: Column 'timestamp' is required but missing. 
Found columns: ['id', 'value', 'date']. 
See docs for required schema.
```

### Recover or Fail Fast
```python
# Good: Recovers what it can
def analyze_batch(files):
    results = []
    errors = []
    
    for file in files:
        try:
            results.append(analyze_file(file))
        except AnalysisError as e:
            errors.append((file, str(e)))
            logger.warning(f"Skipped {file}: {e}")
    
    return AnalysisResults(successful=results, failed=errors)

# Also good: Fails clearly if critical path
def critical_operation(data):
    if not data:
        raise ValueError("Data is required")
    
    return process(data)
```

---

## Testing Strategy

### Test Categories

**Unit Tests**: Individual functions
```python
def test_validate_empty_data():
    with pytest.raises(ValueError):
        validate_data(empty_data)

def test_validate_valid_data():
    report = validate_data(valid_data)
    assert report.is_valid
```

**Integration Tests**: Multiple components together
```python
def test_end_to_end_validation():
    raw_data = load_test_file('messy.csv')
    validator = DataValidator()
    report = validator.validate(raw_data)
    cleaned = validator.fix(raw_data, report)
    assert cleaned.is_valid
```

**Edge Case Tests**: Boundaries and special scenarios
```python
def test_very_large_file():
    # Can handle 1GB file
    pass

def test_unicode_handling():
    # Handles emoji, Chinese characters, etc.
    pass

def test_all_missing_values():
    # Doesn't crash when all data is missing
    pass
```

### Coverage Goals
- Aim for 80%+ code coverage
- 100% coverage of critical paths
- 100% coverage of error handling

### Test Fixtures
Provide realistic test data.

```python
@pytest.fixture
def valid_data():
    return {
        'rows': 100,
        'columns': ['id', 'name', 'value'],
        'sample': [...]
    }

@pytest.fixture
def edge_case_data():
    return {
        'rows': 1000000,
        'missing_rate': 0.5,
        'unicode': True
    }
```

---

## Documentation Requirements

### Skill README
- What it does (one sentence)
- Why someone would use it
- Quick start example
- Configuration options
- Limitations and edge cases
- Links to full docs

### Docstrings
```python
def skill_function(input_data: InputType, config: Config) -> OutputType:
    """
    One-line summary.
    
    Longer description explaining what this does, when to use it,
    and any important behaviors.
    
    Args:
        input_data: Description with example
        config: Description of config options
        
    Returns:
        Description of return value structure
        
    Raises:
        ValidationError: When inputs are invalid
        ProcessingError: When processing fails
        
    Examples:
        >>> result = skill_function(data, default_config())
        >>> result.success
        True
        
    Note:
        Important behavior or gotcha
    """
```

### API Documentation
Include:
- Function/class descriptions
- Parameter types and ranges
- Return value structure
- Possible errors
- Real examples
- Edge cases

---

## Performance Considerations

### Memory Efficiency
```python
# Bad: Loads entire file into memory
def process_file(path):
    data = load_entire_file(path)  # 10GB → memory
    return analyze(data)

# Good: Process in chunks
def process_file(path):
    for chunk in read_in_chunks(path, size=10000):
        yield analyze(chunk)
```

### Time Complexity
Document expected performance:
```python
def find_duplicates(data: List[str]) -> List[List[str]]:
    """
    Find duplicate entries in data.
    
    Time Complexity: O(n log n) due to sorting
    Space Complexity: O(n) for storing duplicates
    
    With 1 million items: ~2 seconds
    """
```

### Caching
When appropriate, cache expensive operations.
```python
from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_operation(param):
    # This result is cached
    return result
```

---

## Version Management

### Semantic Versioning
- `1.0.0` = Major.Minor.Patch
- Major: Breaking changes
- Minor: New features, backward compatible
- Patch: Bug fixes

### Deprecation Strategy
```python
import warnings

def old_function(data):
    warnings.warn(
        "old_function is deprecated, use new_function instead",
        DeprecationWarning,
        stacklevel=2
    )
    return new_function(data)
```

---

## Reusability Checklist

Before shipping a skill, ensure:
- [ ] Works with standard formats (JSON, CSV, plain text)
- [ ] No hard-coded paths or credentials
- [ ] Configurable without code changes
- [ ] Clear error messages
- [ ] Documented with examples
- [ ] Composable with other skills
- [ ] Tested thoroughly
- [ ] Performance characterized
- [ ] Dependencies documented
- [ ] Failure modes handled gracefully

---

## Red Flags

🚩 **Avoid**:
- Skills that do too many unrelated things
- Unclear input/output contracts
- No error handling
- "Magic" behavior that's hard to predict
- Tightly coupled to other systems
- No tests or documentation
- Hardcoded configuration
- Silent failures
- Dependencies on specific user setup

---

## Real-World Examples

Check the `skills/` directory for examples of well-designed skills across different categories.

---

**Last Updated**: 2026-03-12
