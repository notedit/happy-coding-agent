# Happy Coding Agent

A collection of Claude Code skills, commands, and agents for rapid product development.

## Installation

### Official Installation (Recommended)

Install directly in Claude Code using the `/plugin` command:

```bash
# From GitHub
/plugin install https://github.com/notedit/happy-coding-agent

# From Marketplace (if published)
/plugin install happy-coding-agent@claude-plugin-directory
```

### Alternative: CLI Tool

```bash
# Install the CLI tool
curl -fsSL https://raw.githubusercontent.com/notedit/happy-coding-agent/main/install.sh | bash

# Or via pip
pip install git+https://github.com/notedit/happy-coding-agent.git

# Initialize in your project
cd your-project
hca init
```

### Team Distribution

Add `.claude/settings.json` to your project for automatic team installation:

```json
{
  "plugins": {
    "sources": [
      { "type": "github", "url": "https://github.com/notedit/happy-coding-agent" }
    ]
  }
}
```

## Usage

### Slash Commands

| Command | Description |
|---------|-------------|
| `/feature-analyzer` | Turn ideas into fully formed designs and specs through collaborative dialogue |
| `/feature-pipeline` | Execute implementation tasks from design documents using markdown checkboxes |
| `/screenshot-analyzer` | Analyze product screenshots to extract features and generate task lists |
| `/feature-dev` | Guided feature development with codebase understanding and architecture focus |

### Example

```bash
# Design a new feature
/feature-analyzer implement user authentication with OAuth2

# Execute tasks from a design document
/feature-pipeline docs/auth-design.md

# Extract features from UI screenshots
/screenshot-analyzer ./screenshots/login-page.png
```

## Components

### Skills

| Skill | Description |
|-------|-------------|
| `feature-design-assistant` | Feature design through incremental Q&A and validation |
| `task-execution-engine` | Execute implementation tasks from design documents |
| `screenshot-feature-extractor` | Multi-agent pipeline for extracting features from UI screenshots |
| `skill-creation-guide` | Guide for creating new skills |

### Agents

#### Code Analysis
| Agent | Description |
|-------|-------------|
| `code-explorer` | Deeply analyzes codebase features by tracing execution paths and mapping architecture |
| `code-architect` | Designs feature architectures by analyzing existing patterns |
| `code-reviewer` | Reviews code for bugs, security vulnerabilities, and quality issues |

#### Screenshot Analysis (Multi-Agent Pipeline)
| Agent | Description |
|-------|-------------|
| `screenshot-ui-analyzer` | Analyzes visual components, layout structure, and design patterns |
| `screenshot-interaction-analyzer` | Analyzes user interaction flows and state transitions |
| `screenshot-business-analyzer` | Extracts business logic and data entities |
| `screenshot-synthesizer` | Synthesizes analysis results into unified feature list |
| `screenshot-reviewer` | Reviews task lists for completeness and quality |

#### Testing
| Agent | Description |
|-------|-------------|
| `test-generator` | Generates comprehensive test cases based on existing patterns |
| `test-runner` | Executes tests, diagnoses failures, and provides fixes |

## Project Structure

```
happy-coding-agent/
├── .claude-plugin/              # Plugin metadata
│   └── plugin.json              # Plugin manifest
│
├── skills/                      # Skills (SKILL.md + resources)
│   ├── feature-design-assistant/
│   ├── task-execution-engine/
│   ├── screenshot-feature-extractor/
│   └── skill-creation-guide/
│
├── commands/                    # Slash commands
│   ├── feature-analyzer.md
│   ├── feature-pipeline.md
│   ├── feature-dev.md
│   └── screenshot-analyzer.md
│
├── agents/                      # Sub-agents
│   ├── code-architect.md
│   ├── code-explorer.md
│   ├── code-reviewer.md
│   ├── screenshot-*.md
│   ├── test-generator.md
│   └── test-runner.md
│
├── cli/                         # CLI tool (alternative installation)
│   └── ...
│
└── docs/                        # Documentation
    └── PLUGIN_ARCHITECTURE_DESIGN.md
```

## CLI Commands

| Command | Description |
|---------|-------------|
| `hca init` | Deploy plugin to current project |
| `hca init --select` | Interactively select components |
| `hca update` | Update from source repository |
| `hca status` | Show deployment status |

## License

MIT
