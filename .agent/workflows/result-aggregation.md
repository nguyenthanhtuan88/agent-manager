# 🔗 Workflow: Result Aggregation

> Quy trình tổng hợp kết quả khi nhiều agent hoàn thành sub-task.

## Trigger
Tất cả (hoặc phần lớn) sub-task trong task plan đã hoàn thành.

## Quy trình

### Phase 1: Collect
```bash
# Thu thập tất cả output
workspace/T1-output.md
workspace/T2-output.md
workspace/T3-output.md
workspace/bridge-T1-T2.md  (nếu có context bridge)
```

### Phase 2: Classify
Phân loại output theo kiểu nội dung:

| Kiểu | Ví dụ | Aggregation method |
|------|-------|--------------------|
| Research findings | T1: trend data | Merge sections, deduplicate |
| Generated code | T2: TikZ code | Combine as separate files |
| Written content | T3: paper draft | Merge in document order |
| Binary files | T4: PDF output | List references, don't merge |
| Structured data | T5: JSON/YAML | Merge keys, resolve conflicts |

### Phase 3: Merge Strategy

#### Đối với text content
1. Sắp xếp theo document order (intro → body → conclusion)
2. Loại bỏ trùng lặp
3. Thống nhất terminology
4. Thêm transitions giữa các phần từ agent khác nhau

#### Đối với code
1. Tạo project structure hợp lý
2. Resolve import/dependency conflicts
3. Đảm bảo code có thể chạy từ đầu đến cuối

#### Đối với mixed content
1. Tạo main document (markdown)
2. Embed/reference code blocks
3. Link đến binary files
4. Tạo appendix cho data tables

### Phase 4: Generate Output
```
output/
  [task-name]/
    result.md           ← Main document
    sources.md          ← Attribution: phần nào từ agent nào
    appendix/           ← Phụ lục
      figures/          ← Images, TikZ outputs
      data/             ← Tables, datasets
      code/             ← Code files
```

### Phase 5: Generate Execution Report
Sử dụng template `templates/execution-report.md` để tạo báo cáo cuối cùng.

## Edge Cases

| Tình huống | Xử lý |
|-----------|--------|
| 1 agent fail, còn lại OK | Tổng hợp phần OK, note phần thiếu |
| 2 agent trả output mâu thuẫn | Giữ cả hai, đánh dấu [CONFLICT] |
| Output quá lớn | Tạo summary + link đến full output |
| User cần format đặc biệt | Gọi template_content_agent ở cuối |
