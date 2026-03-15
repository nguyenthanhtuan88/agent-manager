---
name: task-decomposer
description: >
  Phân rã task phức tạp thành các sub-task nhỏ, xác định dependency graph
  và thứ tự thực thi tối ưu.
tags: [decomposition, planning, analysis]
---

# 🧩 Skill: Task Decomposer

## Mục đích
Nhận một task phức tạp từ người dùng và phân rã thành các sub-task có thể giao cho agent con.

## Quy trình

### Bước 1: Phân tích yêu cầu
- Đọc kỹ yêu cầu người dùng
- Xác định: domain nào? output mong đợi là gì? constraints?
- Ước lượng độ phức tạp: đơn giản (1 agent) / trung bình (2-3 agent) / phức tạp (4+ agent)

### Bước 2: Phân rã
- Tách thành sub-tasks **độc lập tối đa** (maximize parallelism)
- Mỗi sub-task phải có:
  - `id`: định danh duy nhất (T1, T2, ...)
  - `description`: mô tả ngắn gọn
  - `depends_on`: danh sách task phải hoàn thành trước ([] nếu độc lập)
  - `suggested_agent`: agent phù hợp nhất
  - `suggested_skill`: skill cụ thể cần dùng
  - `expected_output`: output mong đợi

### Bước 3: Xây dependency graph
- Vẽ thứ tự thực thi dưới dạng text graph:
```
T1 (Research) ──┐
T2 (Research) ──┤──→ T4 (Synthesize) ──→ T5 (Review)
T3 (Draw)    ──┘
```

### Bước 4: Output
Ghi kế hoạch vào `workspace/task-plan.md` theo template:
```markdown
## Task Plan: [Tên task]
### Sub-tasks
| ID | Description | Depends On | Agent | Skill | Expected Output |
|----|-------------|------------|-------|-------|-----------------|
| T1 | ... | [] | ... | ... | ... |

### Execution Graph
[graph ở đây]

### Estimated Parallel Rounds
Round 1: T1, T2, T3 (parallel)
Round 2: T4 (depends on T1, T2, T3)
Round 3: T5 (depends on T4)
```

## Lưu ý
- Nếu task quá đơn giản (1 agent đủ xử lý), KHÔNG cần phân rã — giao thẳng cho agent
- Ưu tiên song song hóa — càng nhiều task chạy cùng lúc càng tốt
- Mỗi sub-task nên ATOMIC — đủ nhỏ để 1 agent hoàn thành trong 1 lần gọi
