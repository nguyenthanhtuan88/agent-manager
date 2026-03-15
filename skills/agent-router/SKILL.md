---
name: agent-router
description: >
  Chọn agent và skill phù hợp nhất cho mỗi sub-task dựa trên agent_registry
  và skill_registry. Hỗ trợ dynamic discovery cho agent mới.
tags: [routing, selection, matching]
---

# 🔀 Skill: Agent Router

## Mục đích
Ánh xạ mỗi sub-task vào đúng agent + skill tối ưu.

## Quy trình

### Bước 1: Dynamic Agent Scan
Trước khi route, phải đảm bảo bản đồ agent up-to-date:
1. Đọc `agent_registry.md` để lấy cache
2. Quét nhanh thư mục `../` để tìm agent mới chưa có trong registry
3. Nếu phát hiện agent mới → ghi nhận vào working memory

### Bước 2: Matching Algorithm
Với mỗi sub-task, đánh giá các agent theo tiêu chí:

| Tiêu chí | Trọng số | Mô tả |
|-----------|----------|--------|
| Skill match | 40% | Agent có skill khớp chính xác với sub-task |
| Domain match | 30% | Agent thuộc domain phù hợp |
| Complexity fit | 20% | Skill phức tạp đúng mức cần thiết |
| Overlap avoidance | 10% | Tránh giao cùng 1 agent quá nhiều task |

### Bước 3: Conflict Resolution
Khi 2+ agent có skill tương tự:
- **Research overlap** (Research_Trend_Agent vs Science_Scholar_Agent): 
  - Trend/brainstorm → Research_Trend_Agent
  - Deep technical/ML → Science_Scholar_Agent
- **Writing overlap** (template_content_agent vs Academic-Writing-Agent):
  - Template/docx/pdf → template_content_agent
  - Academic text analysis → Academic-Writing-Agent
- **Education overlap** (EE_Edu_Innovator_Agent vs others):
  - EE-specific education → EE_Edu_Innovator_Agent

### Bước 4: Output Routing Table
```markdown
| Sub-task | Agent | Skill Path | Reason |
|----------|-------|------------|--------|
| T1 | Research_Trend_Agent | ../Research_Trend_Agent/skills/deep-research/SKILL.md | Best match for trend analysis |
```

## Cách gọi Skill từ Agent con

Sau khi route xong, Manager đọc SKILL.md của agent con bằng relative path:
```
Read: ../[agent-name]/skills/[skill-name]/SKILL.md
→ Follow instructions in that SKILL.md
→ Execute the skill with sub-task context
```

Cách này hoạt động cả Copilot và Codex vì cả hai đều đọc file qua filesystem.

## Lưu ý
- LUÔN quét agent mới trước khi route — không dựa hoàn toàn vào registry cache
- Nếu không tìm thấy agent phù hợp → thông báo user thay vì ép fit
- Log routing decision vào `workspace/execution-log.md`
