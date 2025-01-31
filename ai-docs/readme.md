# Agentic Software Planning System

> Testing out a software architecture prompt to build one of itself in agent form.... `ai-docs` was the result of 7 step-by-step choices of ~10  questions. This prompt is sick. <https://github.com/eighteyes/dev-prompts/>

## Overview
A LangChain-based system that uses specialized agents to create software delivery plans through structured dialogue with users. The system processes initial project context, manages questions and answers through agent interactions, and produces a comprehensive set of markdown documents outlining the software delivery plan.

## Key Features
- Specialized agents for different planning aspects
- Structured question-answer workflow
- Markdown-based documentation
- External input support
- Inter-agent communication

## Directory Structure
```
docs/
├── adr/                    # Architecture Decision Records
├── product/               # Product documentation
│   ├── vision.md         # Product vision
│   ├── requirements.md   # System requirements
│   └── critical-path.md  # Critical path and priorities
├── activeQuestions.md    # Current phase questions
└── readme.md            # This file
```

## Workflow 
1. System receives initial project context  
2. Agents add questions to q.md
3. User answers questions
4. Agents process answers and generate documentation
5. Process repeats through different planning phases
6. Final delivery review and validation

## Agents & Files
- Discovery Agent: Initial context and requirements -  docs/product/ [ vision, user-stories, critical path, requirements ].md
- Architecture Agent: Technical decisions and structure - stack.md, models.md
- Logic Agent: Component flows and patterns - patterns.md
- Systems Agent: Component integration - patterns.md
- API Agent: Interface documentation (if needed) - api.md
- UI/UX Agent: Interface planning (if needed) - ui.md
- Project Management Agent: Planning and milestones - plan.md
- Delivery Agent: Final review and validation - readme.md

## Usage
```bash
# Run with initial context
command [options] <input>

# Run with external documentation
command --input ./external-doc.md <input>
```

## Development Status
- Discovery Phase: Complete
- Architecture Phase: In Progress
- Remaining Phases: Pending

## Key Decisions
- Sequential primary workflow with independent operation capability
- Centralized question management in q.md
- Agent-specific file outputs
- Markdown-based documentation
- Simple notation format for Q&A

See ADRs in `/adr` directory for detailed decision records.