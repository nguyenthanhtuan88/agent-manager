---
name: quality-controller
description: >
  Kiểm soát chất lượng output từ các agent con — review tính chính xác,
  nhất quán, đầy đủ trước khi giao cho người dùng.
tags: [quality, review, validation, checking]
---

# ✅ Skill: Quality Controller

## Mục đích
Đảm bảo output cuối cùng đạt chất lượng trước khi giao cho người dùng.

## Checklist chất lượng

### 1. Completeness (Đầy đủ)
- [ ] Tất cả sub-task trong task plan đã được thực hiện?
- [ ] Không thiếu phần nào trong output so với yêu cầu ban đầu?
- [ ] Output có đủ chi tiết hay quá sơ sài?

### 2. Accuracy (Chính xác)
- [ ] Thông tin có đúng không? (cross-check giữa các agent)
- [ ] Code (nếu có) có compile/run được không?
- [ ] Tham chiếu, đường dẫn file có chính xác không?

### 3. Consistency (Nhất quán)
- [ ] Terminology thống nhất giữa các phần?
- [ ] Style/format đồng nhất?
- [ ] Không có mâu thuẫn giữa output của các agent khác nhau?

### 4. Relevance (Liên quan)
- [ ] Output trả lời đúng câu hỏi/yêu cầu của user?
- [ ] Không có nội dung thừa, lạc đề?

### 5. Usability (Sử dụng được)
- [ ] User có thể sử dụng output ngay hay cần thêm bước?
- [ ] File paths, links hoạt động?
- [ ] Format phù hợp (markdown, docx, pdf...)?

## Quy trình review

### Quick Review (task đơn giản)
1. Đọc output → check completeness → giao user
2. Thời gian: < 1 phút

### Standard Review (task trung bình)
1. Check completeness
2. Cross-check consistency giữa các phần
3. Verify accuracy of key claims
4. Giao user với confidence score

### Deep Review (task phức tạp/quan trọng)
1. Full checklist ở trên
2. Nếu phát hiện lỗi → gửi lại agent tương ứng để fix
3. Re-review sau khi fix
4. Giao user kèm quality report

## Quality Report Format
```markdown
## Quality Report
- **Review level:** Quick / Standard / Deep
- **Completeness:** ✅ / ⚠️ / ❌
- **Accuracy:** ✅ / ⚠️ / ❌
- **Consistency:** ✅ / ⚠️ / ❌
- **Issues found:** [mô tả nếu có]
- **Actions taken:** [fix đã thực hiện nếu có]
```

## Lưu ý
- Nếu quality < 70% → KHÔNG giao cho user, gửi lại để fix
- Log tất cả issues vào `workspace/execution-log.md`
- Khi re-route task để fix → dùng Agent Router skill
