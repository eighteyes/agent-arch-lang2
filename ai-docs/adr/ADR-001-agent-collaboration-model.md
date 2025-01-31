# ADR 001: Agent Collaboration Model

## Status
Accepted

## Context
The system requires multiple specialized agents to collaborate on creating software delivery plans. We needed to determine how agents would interact, share information, and manage their outputs.

## Decision
We will implement a hybrid collaboration model with the following characteristics:

1. Sequential Primary Flow
   - Agents will primarily execute in a predefined sequence
   - Each agent will have its own independent file outputs
   - Agents will share context through the q.md file

2. Question Management
   - All questions will be managed in a central q.md file
   - Questions will be organized under agent-specific headers
   - Simple notation format will be used for questions/answers

3. Inter-Agent Communication
   - Agents can raise concerns to other agents
   - Concerns can be escalated to users when needed
   - Communication happens through the q.md file

4. File Independence
   - Each agent maintains its own output files
   - Universal access to ADRs and product documentation (see [ADR-006](ADR-006-agent-documentation-access.md))
   - No version control requirements
   - Markdown format for all documents

## Consequences

### Positive
- Clear separation of concerns
- Simple, centralized question management
- Flexible operation modes (sequential or independent)
- Reduced complexity in file management
- Clear communication channels

### Negative
- Each agent's independent file output could lead to redundant information
- Sequential execution may slow down simple tasks
- No built-in conflict detection between agent outputs
- Single q.md file could become unwieldy with many questions

## Alternatives Considered

### Fully Independent Model
- Each agent operates completely independently
- Rejected due to increased complexity and coordination overhead

### Shared State Model
- Agents share a common state/workspace
- Rejected due to potential conflicts and complexity

### Event-Based Communication
- Agents communicate through events
- Rejected in favor of simpler file-based approach

## Implementation Notes
- Implement clear header conventions for q.md
- Ensure agents can parse and update their sections
- Provide mechanism for cross-agent references
- Support external file input via --input flag