# ADR 006: Agent Documentation Access

## Status
Accepted

## Context
Agents need consistent access to architectural decisions and product context to make informed decisions. We need to ensure all agents can both create ADRs and access product documentation.

## Decision
We will implement universal documentation access patterns:

1. ADR Creation
   - All agents can create ADRs
   - ADRs stored in central /ai-docs/adr directory
   - Consistent ADR format across agents
   - ADR numbering managed by system

2. Product Context Access
   - All agents pull from /ai-docs/product
   - Product documentation as shared context
   - Consistent access patterns
   - Read-only for most operations

3. File Structure
```
ai-docs/
├── adr/          # All agents can write
│   └── ADR-*.md  # Numbered sequentially
├── product/      # All agents can read
│   ├── vision.md
│   ├── requirements.md
│   └── critical-path.md
└── agents/       # Agent-specific outputs
    └── [agent-name]/
```

4. Access Patterns
   - Common module for documentation access
   - Standardized ADR creation
   - Product context loading
   - File path management

## Consequences

### Positive
- Consistent decision documentation
- Shared understanding of product context
- Clear file organization
- Standardized access patterns

### Negative
- Need for ADR coordination
- Potential for conflicting decisions
- Increased file access overhead
- More complex file management

## Alternatives Considered

### Agent-Specific ADR Directories
- Separate ADR directories per agent
- Rejected for consistency

### Duplicated Product Context
- Each agent maintains own copy
- Rejected for maintainability

### Dynamic Documentation Access
- On-demand file access
- Rejected for complexity

## Implementation Notes
- Implement common documentation access module
- Add ADR creation utilities
- Create product context loaders
- Manage file paths centrally