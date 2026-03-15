---
name: result-synthesizer
description: >
  Tổng hợp output từ nhiều agent thành một kết quả thống nhất,
  xử lý conflict và merge nội dung.
tags: [synthesis, merge, aggregation, output]
---

# 🔗 Skill: Result Synthesizer

## Mục đích
Thu thập output từ tất cả sub-task đã hoàn thành và tổng hợp thành kết quả cuối cùng cho người dùng.

## Quy trình

### Bước 1: Thu thập output
- Đọc tất cả file `workspace/T*-output.md`
- Kiểm tra: có bao nhiêu task thành công / thất bại?
- Nếu task quan trọng bị fail → cảnh báo user trước khi tổng hợp

### Bước 2: Phân loại output
Phân loại output theo kiểu:

| Kiểu output | Cách xử lý |
|-------------|-------------|
| Text/Markdown | Merge theo section, loại trùng lặp |
| Code | Organize theo module/file, resolve import conflicts |
| Data/Table | Merge rows/columns, normalize format |
| File (docx/pdf/image) | Liệt kê đường dẫn, không merge nội dung binary |
| Mixed | Xử lý từng phần theo kiểu tương ứng |

### Bước 3: Resolve conflicts
Khi 2 agent output trả về nội dung mâu thuẫn:
1. So sánh nội dung cụ thể
2. Ưu tiên agent chuyên sâu hơn về domain
3. Nếu không rõ → giữ cả hai và đánh dấu `[CONFLICT]` để user quyết định

### Bước 4: Tạo output cuối cùng
Ghi kết quả vào `output/` theo cấu trúc:
```
output/
  [task-name]/
    result.md          # Kết quả chính
    sources.md         # Trích nguồn từ agent nào
    appendix/          # Phụ lục (nếu có)
```

### Bước 5: Tạo Executive Summary
Ở đầu file result.md, luôn có:
```markdown
## Executive Summary
- **Task:** [mô tả task gốc]
- **Agents used:** [danh sách agent]
- **Sub-tasks completed:** X/Y
- **Key findings/deliverables:**
  1. ...
  2. ...
```

## Lưu ý
- KHÔNG bao giờ bỏ sót output từ agent nào — luôn cross-check với task plan
- Ghi rõ nguồn (agent nào, skill nào) cho mỗi phần output
- Nếu user yêu cầu format cụ thể (docx, pdf) → gọi thêm template_content_agent
