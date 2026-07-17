# Mẫu CLAUDE.md (bộ nhớ & chỉ dẫn cho thư mục dự án)

> CLAUDE.md là file Claude Code tự đọc mỗi khi mở thư mục dự án. Đặt ở gốc thư mục.
> Nó cho agent biết: bạn là ai, thư mục này để làm gì, quy tắc làm việc. Nhờ đó không phải dặn lại mỗi lần.

Tạo file tên `CLAUDE.md` ở gốc thư mục dự án, dán nội dung dưới rồi sửa phần trong [ngoặc].

---

```markdown
# CLAUDE.md

## Tôi là ai
- Tên: [Họ tên]
- Vai trò: [chức danh, ví dụ: nhân viên kinh doanh]
- Công ty/lĩnh vực: [...]

## Thư mục này để làm gì
[Ví dụ: nơi tôi để tài liệu, dữ liệu bán hàng, và nhờ agent xử lý báo cáo hằng tuần.]

## Quy tắc khi làm việc với tôi
- Trả lời bằng tiếng Việt, ngắn gọn, dễ hiểu.
- Trước khi sửa hay xóa file, hỏi tôi xác nhận.
- Không bịa số liệu. Thiếu thông tin thì hỏi tôi.
- Văn bản gửi đi (email, báo cáo): văn phong công sở, không dùng emoji.

## Định dạng đầu ra tôi hay cần
[Ví dụ: báo cáo tuần, email khách hàng, bảng tổng hợp số liệu.]

## Cấu trúc thư mục
- `tai-lieu/` : tài liệu cần đọc
- `du-lieu/`  : file Excel/CSV
- `ket-qua/`  : nơi agent lưu output
```

---

## Ghi chú giảng dạy
- Nhấn: CLAUDE.md là "trí nhớ dài hạn" của agent về bạn và dự án.
- Càng ghi rõ vai trò + quy tắc, agent càng làm đúng ngay từ lần đầu.
- Buổi sau (skill, subagent, team) đều dựa trên thói quen tổ chức thư mục này.
