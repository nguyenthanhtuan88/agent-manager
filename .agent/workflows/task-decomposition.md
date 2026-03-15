# 🧩 Workflow: Task Decomposition

> Workflow chi tiết cho giai đoạn phân rã task — khi nào nên phân rã, khi nào không.

## Decision Tree

```
User Task
   │
   ├── Chỉ cần 1 skill/1 agent?
   │     YES → Giao thẳng (SKIP decomposition)
   │     NO ↓
   │
   ├── Cần nhiều skill CÙNG 1 agent?
   │     YES → Single-agent pipeline (decompose nhưng 1 agent)
   │     NO ↓
   │
   ├── Cần nhiều agent KHÁC nhau?
   │     YES → Full decomposition (multi-agent)
   │     NO ↓
   │
   └── Không rõ → Auto-Discovery + analyze → quyết định
```

## Patterns phổ biến

### Pattern A: Research → Write → Format
```
T1: Research_Trend_Agent/deep-research → research findings
T2: Academic-Writing-Agent/analyze_text → structured draft (depends: T1)
T3: template_content_agent/official_claude_docx → final docx (depends: T2)
```

### Pattern B: Parallel Research → Synthesize
```
T1: Research_Trend_Agent/apify-trend-analysis → trend data      ┐
T2: Science_Scholar_Agent/ml-paper-writing → paper structure     ├→ T4: Synthesize
T3: EE_Edu_Innovator_Agent/trend-research-advisor → EE insights ┘
```

### Pattern C: Analyze → Draw → Document
```
T1: TikZ-Drawing-Agent/image-analyzer → analysis        ┐
T2: TikZ-Drawing-Agent/tikz-code-generator → TikZ code  ┤ (T2 depends T1)
T3: template_content_agent/official_claude_pdf → report  ┘ (T3 depends T2)
```

### Pattern D: Full Pipeline (Research Paper)
```
Round 1 (parallel):
  T1: Research_Trend_Agent/deep-research
  T2: Science_Scholar_Agent/brainstorming-research-ideas
  T3: Research_Trend_Agent/apify-trend-analysis

Round 2 (sequential):
  T4: Science_Scholar_Agent/ml-paper-writing (depends: T1, T2, T3)

Round 3 (parallel):
  T5: TikZ-Drawing-Agent/tikz-code-generator (depends: T4 - figures)
  T6: Academic-Writing-Agent (depends: T4 - text polish)

Round 4:
  T7: template_content_agent/official_claude_pdf (depends: T5, T6)
```

## Output
Ghi kết quả vào `workspace/task-plan.md` sử dụng template `templates/task-plan.md`.
