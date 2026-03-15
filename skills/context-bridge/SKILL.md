---
name: context-bridge
description: >
  Chuyển đổi và truyền context giữa các agent khi output của agent A
  là input cho agent B. Đảm bảo format tương thích.
tags: [context, bridge, transform, handoff]
---

# 🌉 Skill: Context Bridge

## Mục đích
Khi output của Agent A cần trở thành input cho Agent B, Context Bridge đảm bảo:
1. Format tương thích
2. Thông tin đầy đủ
3. Context không bị mất

## Tình huống cần Context Bridge

### Case 1: Research → Content Creation
```
Research_Trend_Agent (output: research notes)
  ↓ [Bridge: extract key findings, format as outline]
template_content_agent (input: structured outline)
```

### Case 2: Image Analysis → TikZ Drawing
```
TikZ-Drawing-Agent/image-analyzer (output: analysis JSON)
  ↓ [Bridge: translate analysis to drawing specs]
TikZ-Drawing-Agent/tikz-code-generator (input: drawing specification)
```

### Case 3: Research → Academic Writing
```
Science_Scholar_Agent (output: paper concepts)
  ↓ [Bridge: structure as academic framework]
Academic-Writing-Agent (input: structured text for processing)
```

### Case 4: Education Design → Content
```
EE_Edu_Innovator_Agent (output: curriculum design)
  ↓ [Bridge: convert to document template]
template_content_agent (input: structured template data)
```

## Quy trình Bridge

### Bước 1: Phân tích Output nguồn
- Đọc output từ Agent A
- Xác định format: markdown, JSON, plain text, code, file path
- Trích xuất key information

### Bước 2: Xác định Input target
- Đọc SKILL.md của Agent B
- Xác định format input mong đợi
- Mapping fields: output_field → input_field

### Bước 3: Transform
- Chuyển đổi format nếu cần
- Bổ sung context thiếu (từ task plan gốc)
- Validate: bridge output khớp với Agent B expectations

### Bước 4: Handoff
- Ghi bridge output vào `workspace/bridge-T[source]-T[target].md`
- Cung cấp cho Agent B cùng với instructions

## Transform Templates

### Research → Outline
```markdown
## Research Summary for Content Creation
### Key Findings
[extracted from research output]
### Suggested Structure
[derived from findings]
### Supporting Data
[tables, references from research]
```

### Analysis → Specification
```markdown
## Drawing Specification
### Components
[extracted from analysis]
### Layout
[derived from analysis]
### Style
[inferred or specified by user]
```

## Lưu ý
- Bridge nên MINIMAL — chỉ transform đủ, không thêm nội dung mới
- Luôn giữ nguyên attribution (info này từ agent nào)
- Nếu format không rõ → hỏi user thay vì đoán
