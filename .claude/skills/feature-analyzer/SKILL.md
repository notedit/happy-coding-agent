---
name: feature-analyzer
description: "Turn ideas into fully formed designs and specs through natural collaborative dialogue. Use when planning new features, designing architecture, or making significant changes to the codebase."
---

# Feature Analyzer

Help turn ideas into fully formed designs and specs through natural collaborative dialogue. Start by understanding the current project context, then ask questions one at a time to refine the idea. Once you understand what you're building, present the design in small sections (200-300 words), checking after each section whether it looks right so far.  using ultrathink. 

## The Process

### Understanding the idea

- Check out the current project state first (files, docs, recent commits)
- Ask questions one at a time to refine the idea
- Prefer multiple choice questions when possible, but open-ended is fine too
- Only one question per message - if a topic needs more exploration, break it into multiple questions
- Focus on understanding: purpose, constraints, success criteria

### Exploring approaches

- Propose 2-3 different approaches with trade-offs
- Present options conversationally with your recommendation and reasoning
- Lead with your recommended option and explain why

### Presenting the design

- Once you believe you understand what you're building, present the design
- Break it into sections of 300-500 words
- Ask after each section whether it looks right so far
- Cover: architecture, components, data flow, error handling, testing
- Be ready to go back and clarify if something doesn't make sense

## After the Design

### Documentation

- Write the validated design to `docs/designs/YYYY-MM-DD-<topic>-design.md`
- Commit the design document to git

### Implementation Tasks

After presenting the design, generate an implementation task list using markdown checkboxes:

```markdown
## Implementation Tasks

- [ ] **Task Title** `priority:1` `phase:model`
  - files: file1.py, file2.py
  - [ ] Acceptance criterion 1
  - [ ] Acceptance criterion 2

- [ ] **Another Task** `priority:2` `phase:api` `deps:Task Title`
  - files: api.py
  - [ ] Criterion 1
  - [ ] Criterion 2
```

**Task Format:**
- `- [ ]` checkbox with **bold title**
- Inline attributes: `priority:N` `phase:X` `deps:A,B`
- Indented `- files:` line with comma-separated paths
- Indented `- [ ]` checkboxes for acceptance criteria

**Task Generation Guidelines:**
- Break the design into atomic, implementable tasks
- Order tasks by dependency (foundations first)
- Use clear, action-oriented titles ("Create X", "Implement Y", "Add Z")
- Each task should be completable independently
- Include test tasks for each major component
- Phases: `model` → `api` → `ui` → `test` → `docs`

### Implementation (if continuing)

- Ask: "设计已完成，要开始实现吗？"
- If user says "开始实现" / "Yes" / "start implementation":
  - Invoke `/feature-pipeline <design-file-path>`
  - Or directly start executing tasks from the design document

## Key Principles

- **One question at a time** - Don't overwhelm with multiple questions
- **Multiple choice preferred** - Easier to answer than open-ended when possible
- **YAGNI ruthlessly** - Remove unnecessary features from all designs
- **Explore alternatives** - Always propose 2-3 approaches before settling
- **Incremental validation** - Present design in sections, validate each
- **Be flexible** - Go back and clarify when something doesn't make sense
