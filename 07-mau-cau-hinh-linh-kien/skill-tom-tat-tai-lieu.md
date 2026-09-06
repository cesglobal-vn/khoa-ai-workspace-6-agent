# Mẫu SKILL.md (skill tự tạo: tóm tắt tài liệu)

> Skill là một gói chỉ dẫn cho một quy trình lặp lại. Claude Code tự nạp skill khi gặp việc phù hợp
> (nhờ dòng mô tả), hoặc bạn gọi thẳng bằng tên. Mỗi skill là một thư mục chứa file `SKILL.md`.

## Cách tạo
1. Trong thư mục dự án, tạo đường dẫn: `.claude/skills/tom-tat-tai-lieu/SKILL.md`
2. Dán nội dung dưới vào file đó.
3. Từ nay khi bạn nhờ "tóm tắt tài liệu này", Claude tự dùng skill để làm đúng chuẩn mỗi lần.

---

```markdown
---
name: tom-tat-tai-lieu
description: Dùng khi cần đọc và tóm tắt một tài liệu dài (hợp đồng, biên bản, báo cáo) theo chuẩn công ty. Trích ý chính, số liệu, hạn chót.
---

# Kỹ năng: Tóm tắt tài liệu

Khi người dùng đưa một tài liệu dài, làm theo các bước:

1. Đọc toàn bộ tài liệu.
2. Xuất ra đúng cấu trúc sau:

## TÓM TẮT NHANH
- 3 tới 5 gạch đầu dòng ý chính nhất.

## Ý CHÍNH CHI TIẾT
- Liệt kê theo từng mục/phần của tài liệu.

## SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT
- Bóc ra mọi con số, mốc thời gian, cam kết quan trọng.

## ĐIỂM CẦN LƯU Ý / RỦI RO
- Nếu có điều khoản bất lợi, mâu thuẫn, hoặc chỗ mập mờ.

## QUY TẮC
- Chỉ dùng thông tin có trong tài liệu. Không có thì ghi "Tài liệu không đề cập", KHÔNG suy đoán.
- Trích nguyên văn khi cần bằng chứng, đặt trong ngoặc kép.
- Trả lời bằng tiếng Việt, rõ ràng.
```

---

## Ghi chú giảng dạy
- Điểm mấu chốt của skill là dòng `description`: viết rõ "dùng khi nào" để Claude tự nạp đúng lúc.
- Học viên đổi phần thân để tạo skill cho nghề mình: soạn email, kiểm tra hợp đồng, lên kế hoạch tuần.
- Skill dùng lại được mãi, khác với việc gõ lại chỉ dẫn mỗi lần.
