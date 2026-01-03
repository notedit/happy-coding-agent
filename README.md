# Happy Coding Agent

A collection of Claude Code skills, commands, and agents for rapid product development.

## Commands

| Command | Description |
|---------|-------------|
| `/feature-analyzer` | Turn ideas into fully formed designs and specs through collaborative dialogue |
| `/feature-pipeline` | Execute implementation tasks from design documents using markdown checkboxes |
| `/analyze-screenshot` | Analyze product screenshots to extract features and generate task lists |
| `/feature-dev` | Guided feature development with codebase understanding and architecture focus |

## Agents

| Agent | Description |
|-------|-------------|
| `code-explorer` | Deeply analyzes codebase features by tracing execution paths, mapping architecture layers, and documenting dependencies |
| `code-architect` | Designs feature architectures by analyzing existing patterns and providing comprehensive implementation blueprints |
| `code-reviewer` | Reviews code for bugs, security vulnerabilities, and quality issues with confidence-based filtering |

## Skills

| Skill | Description |
|-------|-------------|
| `feature-analyzer` | Feature design through incremental Q&A and validation |
| `feature-pipeline` | Execute implementation tasks from design documents |
| `screenshot-analyzer` | Extract features from UI screenshots, generate development checklists |
| `skill-creator` | Guide for creating new skills |

## Project Structure

```
.claude/
├── agents/             # Custom agents
│   ├── code-architect.md
│   ├── code-explorer.md
│   └── code-reviewer.md
├── commands/           # Slash commands
│   ├── feature-analyzer.md
│   ├── feature-pipeline.md
│   ├── analyze-screenshot.md
│   └── feature-dev.md
└── skills/             # Reusable skills
    ├── feature-analyzer/
    ├── feature-pipeline/
    ├── screenshot-analyzer/
    └── skill-creator/
```
