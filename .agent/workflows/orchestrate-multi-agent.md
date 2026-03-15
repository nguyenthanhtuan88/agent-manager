# 🎭 Workflow: Orchestrate Multi-Agent

> Quy trình chính khi Manager nhận task từ user và cần điều phối nhiều agent.

## Trigger
User gửi task phức tạp cần >= 2 agent.

## Flow

```
┌─────────────────────────────────────────────────────────────┐
│  USER REQUEST                                                │
└──────────────────────┬──────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 0: Auto-Discovery                                      │
│  Quét agents/ → cập nhật bản đồ agent & skill                │
│  Skill: (built-in AGENT.md protocol)                          │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 1: Task Decomposition                                   │
│  Phân rã task → sub-tasks + dependency graph                  │
│  Skill: skills/task-decomposer/SKILL.md                       │
│  Output: workspace/task-plan.md                               │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 2: Agent Routing                                        │
│  Ánh xạ sub-task → agent + skill                              │
│  Skill: skills/agent-router/SKILL.md                          │
│  Output: routing table trong task-plan.md                     │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 3: Parallel Execution                                   │
│  Chạy agent theo rounds (parallel + sequential)               │
│  Skill: skills/parallel-orchestrator/SKILL.md                 │
│  Bridge: skills/context-bridge/SKILL.md (khi cần)             │
│  Output: workspace/T*-output.md                               │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 4: Result Synthesis                                     │
│  Tổng hợp output từ tất cả agent                              │
│  Skill: skills/result-synthesizer/SKILL.md                    │
│  Output: output/[task-name]/result.md                         │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 5: Quality Check                                        │
│  Review output trước khi giao user                            │
│  Skill: skills/quality-controller/SKILL.md                    │
│  Output: quality report + final result                        │
└──────────────────────┬───────────────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────────────┐
│  DELIVER TO USER                                              │
└──────────────────────────────────────────────────────────────┘
```

## Error Handling
- Nếu Step 0 không tìm agent phù hợp → thông báo user
- Nếu Step 3 agent fail → retry 1 lần, nếu vẫn fail → skip & note
- Nếu Step 5 quality < 70% → quay lại Step 3 với agent khác

## Platform Compatibility

| Step | Copilot | Codex |
|------|---------|-------|
| 0 - Discovery | `list_dir` + `read_file` | `ls` + `cat` |
| 1 - Decompose | Inline analysis | Inline analysis |
| 2 - Route | Read registry files | Read registry files |
| 3 - Execute | `runSubagent` / parallel tool calls | Sequential step execution |
| 4 - Synthesize | Read workspace/ files | Read workspace/ files |
| 5 - Quality | Inline review | Inline review |
