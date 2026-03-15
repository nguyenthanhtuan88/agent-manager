---
name: parallel-orchestrator
description: >
  Điều phối thực thi song song nhiều agent, quản lý dependency,
  xử lý lỗi và retry.
tags: [orchestration, parallel, execution, coordination]
---

# ⚡ Skill: Parallel Orchestrator

## Mục đích
Thực thi kế hoạch từ Task Decomposer — điều phối nhiều agent chạy đồng thời theo dependency graph.

## Chiến lược thực thi

### Mode 1: Full Parallel
Khi tất cả sub-task độc lập → chạy hết cùng lúc.
```
Round 1: [T1, T2, T3, T4] → tất cả song song
```

### Mode 2: Sequential Pipeline
Khi mỗi task phụ thuộc task trước → chạy lần lượt.
```
Round 1: T1
Round 2: T2 (input = T1.output)
Round 3: T3 (input = T2.output)
```

### Mode 3: Hybrid (mặc định)
Kết hợp cả hai — maximizeparallelism trong ràng buộc dependency.
```
Round 1: [T1, T2] → parallel (independent)
Round 2: [T3] → sequential (depends on T1)
Round 3: [T4] → sequential (depends on T2, T3)
```

## Quy trình thực thi

### Bước 1: Đọc Task Plan
- Đọc `workspace/task-plan.md`
- Parse dependency graph
- Tính toán execution rounds

### Bước 2: Execute Round-by-Round
Với mỗi round:
1. Xác định các task có thể chạy (dependencies đã hoàn thành)
2. Với mỗi task trong round:
   - Đọc SKILL.md của agent được assign
   - Cung cấp context (input data + output từ task trước nếu có)
   - Gọi skill và thu thập output
3. Lưu output mỗi task vào `workspace/T[id]-output.md`
4. Đánh dấu task hoàn thành

### Bước 3: Xử lý lỗi
- Nếu 1 task fail → kiểm tra có task nào phụ thuộc không
- Nếu có task phụ thuộc → pause chain đó, tiếp tục các chain khác
- Thông báo user về task fail và đề xuất retry hoặc skip

### Bước 4: Log execution
Ghi vào `workspace/execution-log.md`:
```markdown
## Execution: [timestamp]
| Round | Tasks | Status | Duration |
|-------|-------|--------|----------|
| 1 | T1, T2 | ✅ Done | ~2 min |
| 2 | T3 | ✅ Done | ~1 min |
| 3 | T4 | ❌ Failed | - |
```

## Trên Copilot vs Codex

| Platform | Cách thực hiện song song |
|----------|-------------------------|
| **Copilot** | Sử dụng `runSubagent` hoặc parallel tool calls để chạy nhiều task cùng lúc |
| **Codex** | Sử dụng multi-step execution, mỗi step xử lý 1 round |

## Lưu ý
- Tối đa 4 agent song song (configurable trong `agent_config.yaml`)
- Luôn ghi output trung gian → phục hồi được nếu bị gián đoạn
- Không retry quá 2 lần cho cùng 1 task
