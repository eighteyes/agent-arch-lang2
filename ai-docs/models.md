# Core Models and Structures

## File Structures

### Question Management (q.md)
```markdown
# Agent Section
## [Agent Name]
1. Question text
   Answer: Response text
2. Question text
   Answer: Response text

## [Next Agent]
...
```

### Prompt Files
```markdown
# [Prompt Name]
metadata:
  agent: [agent name]
  purpose: [brief description]
  version: [version number]

## Context
[Context information]

## Instructions
[Specific instructions]

## Output Format
[Expected output format]
```

## Data Models

### Event System
```python
Event {
  type: str          # Event type identifier
  agent: str         # Source agent name
  timestamp: float   # Event timestamp
  data: dict        # Event payload
  metadata: dict    # Additional context
}
```

### Agent Context
```python
AgentContext {
  name: str         # Agent identifier
  phase: str        # Current phase
  input_files: list # Relevant input files
  output_files: list # Expected output files
  questions: list   # Agent's questions
  answers: dict     # Received answers
}
```

### File Metadata
```python
FileMetadata {
  path: str         # File path
  agent: str        # Creating agent
  phase: str        # Creation phase
  dependencies: list # Required input files
  schema: dict      # Optional structure validation
}
```

## Component Relationships

### Agent Workflow
```
Input -> Discovery -> Architecture -> Logic -> Systems -> [API/UI] -> Project -> Delivery
```

### File Dependencies
```
vision.md <- requirements.md <- critical-path.md
     \            |                    |
      \           v                    v
       +-> stack.md <- models.md <- patterns.md
```

### Event Flow
```
Agent Initialization
      |
Question Generation
      |
Answer Processing
      |
File Generation
      |
Inter-agent Communication
      |
Validation/Review
```

## Validation Rules

### Document Structure
- All files must be valid markdown
- Required metadata sections where specified
- Consistent header hierarchy
- Clear section delineation

### Question Format
- Numbered questions under agent headers
- Clear answer section for each question
- Support for deferred answers
- Cross-references when needed

### Event Handling
- Valid event types
- Required event metadata
- Proper agent attribution
- Error context inclusion

## Documentation Access Models

### ADR Management
```python
ADRContext {
  next_number: int    # Next available ADR number
  adr_directory: str  # Path to ADR directory
  template: str       # ADR template format
  metadata: dict     # ADR tracking information
}
```

### Product Context
```python
ProductContext {
  vision: dict       # Vision document content
  requirements: dict # Requirements content
  critical_path: dict # Critical path content
  metadata: dict     # Context tracking information
}
```

### Documentation Access
```python
DocAccess {
  adr: ADRContext    # ADR management context
  product: ProductContext # Product documentation
  agent_name: str    # Current agent
  permissions: dict  # Access controls
}
```

## Extension Points

### Agent Capabilities
- Custom prompt definitions
- Specialized tools
- Event handlers
- Output formatters
- ADR creation
- Product context access

### File Processing
- Custom markdown extensions
- Metadata processors
- Schema validators
- Format converters