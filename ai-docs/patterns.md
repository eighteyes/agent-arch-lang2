# System Patterns

## Event Patterns

### Agent Event Flow
```
[Agent Event Listener] -> [30s Timeout] -> [Processing] -> [Output/Error]
                                            |
                                            v
                                      [User Intervention]
                                      (if needed)
```

### Event Types
1. Initialization Events
   - Agent startup
   - Context loading
   - Resource preparation

2. Processing Events
   - Question generation
   - Answer processing
   - File generation
   - Validation requests

3. Error Events
   - Timeout notifications
   - Validation failures
   - Processing errors
   - Agent concerns

4. Phase Events
   - Phase completion
   - Re-run requests
   - Optional phase activation

## Document Patterns

### Question Management (q.md)
```markdown
# Batch Answers
1. Answer to question 1
2. Answer to question 2
...

# Discovery Agent ⚡
1. Urgent question
2. Regular question

# Architecture Agent 🔄
1. Question needing clarification
...
```

### Cross-References
```markdown
See [Technical Stack](stack.md#components) for details.
Related: [ADR-001](adr/ADR-001-agent-collaboration-model.md)
```

### Metadata Headers
```markdown
---
agent: discovery
phase: initial
dependencies:
  - input.md
  - context.md
validation: required
---
```

## Error Handling Patterns

### User Intervention Points
1. Agent Concerns
   ```
   [Agent A] -> [Concern] -> [Pause] -> [User Input] -> [Resume/Modify]
   ```

2. Processing Failures
   ```
   [Process] -> [Error] -> [Log] -> [User Decision] -> [Retry/Skip]
   ```

3. Validation Issues
   ```
   [Pre-write] -> [Validate] -> [Issues] -> [User Fix] -> [Retry]
   ```

### Timeout Management
```
[Start] -> [30s Timer] -> [Complete/Timeout]
            |
            v
      [User Notification]
```

## Flow Control Patterns

### Phase Management
```
[Phase Start] -> [Need Check] -> [Execute/Skip]
                    |
                    v
              [Optional Phases]
```

### Re-run Requests
```
[Agent] -> [Re-run Request] -> [User Approval] -> [Phase Restart]
```

### Batch Processing
```
[Collect Questions] -> [Batch Section] -> [Process Answers] -> [Distribute]
```

## Validation Patterns

### Document Validation
1. Pre-write Checks
   - Metadata presence
   - Link validity
   - Structure conformance
   - Format compliance

2. Cross-reference Validation
   - Link targets exist
   - Reference validity
   - Dependency check

3. Metadata Validation
   - Required fields
   - Value formats
   - Dependency lists

## Extension Patterns

### Agent Customization
```
[Base Agent] -> [Custom Events] -> [Specialized Behavior]
```

### Document Processing
```
[Input] -> [Parser] -> [Processor] -> [Validator] -> [Output]
```

### Error Handling Extensions
```
[Error] -> [Categorize] -> [Custom Handler] -> [Resolution]
```

## System Integration Patterns

### Common Module Organization
```
common/
├── events/        # Shared event bus
├── utils/         # Common utilities
├── processors/    # Document processors
└── files/         # File operations
```

### Agent Orchestra Pattern
```
[Conductor]
    |
    +---> [Agent Status Tracking]
    |
    +---> [Phase Management]
    |
    +---> [Re-run Coordination]
    |
    +---> [Event Broadcasting]
```

### Document Hub Pattern
```
[Central Hub]
    |
    +---> [/docs/ Directory]
    |          |
    |          +---> [Agent Outputs]
    |          |
    |          +---> [Shared Resources]
    |
    +---> [Access Control]
    |
    +---> [Validation]
```

### Event Nexus Pattern
```
[Event Nexus]
    |
    +---> [Agent Events]
    |
    +---> [System State]
    |
    +---> [Timeouts]
    |
    +---> [User Interaction]
```

### State Management Pattern
```
[Agent State]
    |
    +---> ["Done" Flag]
    |
    +---> [Phase Status]
    |
    +---> [Re-run State]
```

### Resource Coordination
```
[Resource Manager]
    |
    +---> [File Access]
    |
    +---> [Event Distribution]
    |
    +---> [State Updates]
```