---
name: feature-design-assistant
description: "Turn ideas into fully formed designs and specs through natural collaborative dialogue. Use when planning new features, designing architecture, or making significant changes to the codebase."
---

# Feature Analyzer

Help turn ideas into fully formed designs and specs through natural collaborative dialogue. Use AskUserQuestion to efficiently gather requirements in batches of up to 4 questions at a time.

**Announce at start:** "I'm using the feature-design-assistant skill to design this feature."

## The Process

### Phase 1: Context Discovery

First, check out the current project state (files, docs, recent commits), then use AskUserQuestion to gather initial context:

```
AskUserQuestion with questions:
1. "这个功能要解决什么问题？" (open-ended)
2. "目标用户是谁？" options: ["开发者", "终端用户", "管理员", "API消费者", "其他"] multiSelect: true
3. "有哪些核心需求？" options: ["性能优先", "易用性优先", "安全性优先", "可扩展性优先", "快速交付"] multiSelect: true
4. "有时间或资源限制吗？" options: ["紧急(1-2天)", "正常(1周)", "宽松(2周+)", "无限制"]
```

### Phase 2: Technical Requirements

Based on Phase 1 answers, ask technical questions:

```
AskUserQuestion with questions:
1. "需要哪些技术能力？" options: ["数据持久化", "API接口", "用户界面", "后台任务", "第三方集成", "无特殊要求"] multiSelect: true
2. "数据存储需求？" options: ["数据库", "文件系统", "缓存", "内存", "无需存储"]
3. "需要支持哪些场景？" options: ["高并发", "大数据量", "离线使用", "实时同步", "普通使用"] multiSelect: true
4. "错误处理策略？" options: ["静默重试", "用户提示", "自动回滚", "日志记录", "告警通知"] multiSelect: true
```

### Phase 3: Architecture Exploration

Propose 2-3 different approaches, then ask:

```
AskUserQuestion with questions:
1. "倾向哪种架构方案？" options: ["方案A: [简述]", "方案B: [简述]", "方案C: [简述]", "需要更多信息"]
2. "哪些非功能性需求重要？" options: ["可测试性", "可维护性", "可观测性", "向后兼容", "文档完整"] multiSelect: true
3. "部署和运维考虑？" options: ["容器化", "CI/CD", "监控告警", "蓝绿发布", "无特殊要求"] multiSelect: true
4. "还有其他约束或偏好吗？" (open-ended)
```

### Phase 4: Design Validation

Present design in sections (300-500 words each), after each section ask:

```
AskUserQuestion with questions:
1. "这部分设计是否符合预期？" options: ["完全符合", "基本符合，有小建议", "需要调整", "完全不对"]
2. "需要补充哪些细节？" options: ["更多代码示例", "更详细的数据流", "边界情况处理", "性能考量", "暂时够了"] multiSelect: true
3. "这部分有疑问吗？" (open-ended)
4. "准备好看下一部分了吗？" options: ["继续", "先修改当前部分", "回到上一部分"]
```

## AskUserQuestion Usage Guidelines

- **每次最多 4 个问题** - 工具上限
- **非互斥选项用 multiSelect: true** - 如技术能力、非功能需求等
- **互斥选项不用 multiSelect** - 如架构方案选择、时间限制等
- **保留一个开放式问题** - 捕获遗漏的需求
- **问题要具体** - 避免模糊的选项

## After the Design

### Documentation

- Write the validated design to `docs/designs/YYYY-MM-DD-<topic>-design.md`
- Commit the design document to git

### Implementation Tasks

After presenting the design, generate an implementation task list using markdown checkboxes:

```markdown
## Implementation Tasks

- [ ] **Task Title** `priority:1` `phase:model` `time:15min`
  - files: src/file1.py, tests/test_file1.py
  - [ ] Step 1: Write failing test for X
  - [ ] Step 2: Run test, verify it fails
  - [ ] Step 3: Implement minimal code
  - [ ] Step 4: Run test, verify it passes
  - [ ] Step 5: Commit

- [ ] **Another Task** `priority:2` `phase:api` `deps:Task Title` `time:10min`
  - files: src/api.py
  - [ ] Step 1: Write failing test
  - [ ] Step 2: Implement and verify
  - [ ] Step 3: Commit
```

**Task Format:**
- `- [ ]` checkbox with **bold title**
- Inline attributes: `priority:N` `phase:X` `deps:A,B` `time:Nmin`
- Indented `- files:` line with exact paths (include test files)
- Indented `- [ ]` checkboxes for TDD steps (2-5 min each)

**Task Granularity (TDD Steps):**
- Each step should take 2-5 minutes
- "Write the failing test" - one step
- "Run it to verify it fails" - one step
- "Implement minimal code" - one step
- "Run test to verify it passes" - one step
- "Commit" - one step

**Task Generation Guidelines:**
- Break the design into atomic, implementable tasks
- Order tasks by dependency (foundations first)
- Use clear, action-oriented titles ("Create X", "Implement Y", "Add Z")
- Each task should be completable independently
- Include test tasks for each major component
- Phases: `model` → `api` → `ui` → `test` → `docs`

### Execution Handoff

After saving the design, offer execution choice:

**"设计完成并保存到 `docs/designs/<filename>.md`。两种执行方式：**

**1. 当前会话执行** - 使用 /feature-pipeline 逐任务执行，每个任务后review

**2. 新会话执行** - 在新会话中批量执行，适合大型功能

**选择哪种？"**

**If 当前会话执行 chosen:**
- Invoke `/feature-pipeline <design-file-path>`
- Stay in this session, execute task by task

**If 新会话执行 chosen:**
- Guide user to open new session
- Provide the design file path for reference

## Key Principles

- **Batch questions efficiently** - Use AskUserQuestion with up to 4 related questions per call
- **Use multiSelect wisely** - For non-mutually-exclusive options (e.g., features, requirements)
- **Keep one open-ended question** - Catch edge cases and unexpected requirements
- **YAGNI ruthlessly** - Remove unnecessary features from all designs
- **Explore alternatives** - Always propose 2-3 approaches before settling
- **Incremental validation** - Present design in sections, validate each
- **Be flexible** - Go back and clarify when something doesn't make sense
