# Happy Coding Agent

A collection of Claude Code skills, commands, and agents for rapid product development.

## Quick Start

Deploy to any git project with one command:

```bash
# Install the CLI tool
curl -fsSL https://raw.githubusercontent.com/notedit/happy-coding-agent/main/install.sh | bash

# Or via pip
pip install git+https://github.com/notedit/happy-coding-agent.git

# Initialize in your project
cd your-project
hca init
```

### CLI Commands

| Command | Description |
|---------|-------------|
| `hca init` | Deploy .claude configurations to current project |
| `hca init --select` | Interactively select components to deploy |
| `hca update` | Update configurations from source repository |
| `hca status` | Show deployment status and version info |

## Commands

| Command | Description |
|---------|-------------|
| `/feature-analyzer` | Turn ideas into fully formed designs and specs through collaborative dialogue |
| `/feature-pipeline` | Execute implementation tasks from design documents using markdown checkboxes |
| `/screenshot-analyzer` | Analyze product screenshots to extract features and generate task lists |
| `/feature-dev` | Guided feature development with codebase understanding and architecture focus |

## Agents

### Code Analysis Agents

| Agent | Description |
|-------|-------------|
| `code-explorer` | Deeply analyzes codebase features by tracing execution paths, mapping architecture layers, and documenting dependencies |
| `code-architect` | Designs feature architectures by analyzing existing patterns and providing comprehensive implementation blueprints |
| `code-reviewer` | Reviews code for bugs, security vulnerabilities, and quality issues with confidence-based filtering |

### Screenshot Analysis Agents (Multi-Agent Pipeline)

| Agent | Description |
|-------|-------------|
| `screenshot-ui-analyzer` | Analyzes visual components, layout structure, and design patterns |
| `screenshot-interaction-analyzer` | Analyzes user interaction flows, clickable elements, and state transitions |
| `screenshot-business-analyzer` | Extracts business logic, functional modules, and data entities |
| `screenshot-synthesizer` | Synthesizes analysis results into unified feature list and task breakdown |
| `screenshot-reviewer` | Reviews task lists for completeness, consistency, and quality |

### Testing Agents

| Agent | Description |
|-------|-------------|
| `test-generator` | Analyzes code changes and generates comprehensive test cases by understanding existing test patterns and conventions |
| `test-runner` | Executes tests, analyzes results, identifies failures, diagnoses root causes, and provides actionable fixes |

## Skills

| Skill | Description |
|-------|-------------|
| `feature-design-assistant` | 功能设计助手 - Feature design through incremental Q&A and validation |
| `task-execution-engine` | 任务执行引擎 - Execute implementation tasks from design documents |
| `screenshot-feature-extractor` | 截图特征提取器 - Multi-agent pipeline for extracting features from UI screenshots and generating task lists |
| `skill-creation-guide` | 技能创建指南 - Guide for creating new skills |

## Project Structure

```
cli/                                     # CLI tool (hca command)
│   ├── main.py                          # Entry point
│   ├── commands/                        # CLI commands
│   └── core/                            # Core logic
.claude/
├── agents/                              # Custom agents
│   ├── code-architect.md
│   ├── code-explorer.md
│   ├── code-reviewer.md
│   ├── screenshot-ui-analyzer.md        # Multi-agent pipeline
│   ├── screenshot-interaction-analyzer.md
│   ├── screenshot-business-analyzer.md
│   ├── screenshot-synthesizer.md
│   ├── screenshot-reviewer.md
│   ├── test-generator.md
│   └── test-runner.md
├── commands/                            # Slash commands
│   ├── feature-analyzer.md
│   ├── feature-pipeline.md
│   ├── screenshot-analyzer.md
│   └── feature-dev.md
└── skills/                              # Reusable skills
    ├── feature-design-assistant/
    ├── task-execution-engine/
    ├── screenshot-feature-extractor/
    └── skill-creation-guide/
```
