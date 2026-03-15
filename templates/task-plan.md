# 📋 Task Plan Template

> Sử dụng template này khi Task Decomposer phân rã task.

## Task: [TÊN TASK]
- **Requested by:** User
- **Date:** [YYYY-MM-DD]
- **Complexity:** Simple / Medium / Complex
- **Strategy:** Single-agent / Multi-agent parallel / Multi-agent sequential / Hybrid

---

## Sub-tasks

| ID | Description | Depends On | Agent | Skill Path | Expected Output | Status |
|----|-------------|------------|-------|------------|-----------------|--------|
| T1 | [mô tả] | [] | [agent_name] | `../[agent]/skills/[skill]/SKILL.md` | [output type] | ⏳ |
| T2 | [mô tả] | [T1] | [agent_name] | `../[agent]/skills/[skill]/SKILL.md` | [output type] | ⏳ |
| T3 | [mô tả] | [] | [agent_name] | `../[agent]/skills/[skill]/SKILL.md` | [output type] | ⏳ |

**Status legend:** ⏳ Pending | 🔄 In Progress | ✅ Done | ❌ Failed | ⏭️ Skipped

---

## Execution Graph

```
T1 ──┐
     ├──→ T4 ──→ T5
T2 ──┘
T3 ────────────→ T5
```

---

## Execution Rounds

| Round | Tasks (parallel) | Dependencies met? |
|-------|------------------|-------------------|
| 1 | T1, T2, T3 | ✅ (no deps) |
| 2 | T4 | ✅ (T1, T2 done) |
| 3 | T5 | ✅ (T3, T4 done) |

---

## Context Bridges Required

| Source → Target | Transform needed |
|-----------------|------------------|
| T1 → T4 | [mô tả transform] |
| T3 → T5 | [mô tả transform] |

---

## Notes
- [Ghi chú đặc biệt, constraints, user preferences]
