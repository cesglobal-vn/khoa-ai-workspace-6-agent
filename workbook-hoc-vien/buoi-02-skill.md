# Workbook Buổi 02: Skill - Đóng gói quy trình lặp lại

> Sổ tay thực hành cho học viên. Làm theo từng bước đánh số. Prompt in trong khối xám là copy dán được ngay.

## Mục tiêu buổi này
Học xong, bạn sẽ:
1. Hiểu skill là gì và vì sao nó tiết kiệm công so với gõ lại chỉ dẫn mỗi lần.
2. Tự tay tạo được 1 skill tên `tom-tat-tai-lieu` trong thư mục dự án của mình.
3. Dùng skill để tóm tắt một hợp đồng: bóc ra số tiền, ngày tháng, hạn chót, điều khoản bất lợi.
4. Nắm quy tắc chống bịa: tài liệu không có thì ghi "không đề cập", không tự đoán.

## Skill là gì (đọc nhanh trước khi làm)
- **Skill là một gói chỉ dẫn cho việc bạn làm đi làm lại.** Viết một lần, dùng mãi. Ví dụ: tóm tắt tài liệu, soạn email, kiểm tra hợp đồng.
- **Về mặt file, skill là một thư mục có một file tên SKILL.md**, đặt tại `.claude/skills/<ten-skill>/SKILL.md` trong thư mục dự án của bạn.
- **Claude tự nạp skill nhờ dòng mô tả (description).** Dòng này ghi rõ "dùng khi nào". Khi bạn nhờ một việc khớp mô tả, Claude tự lấy skill ra dùng. Bạn cũng gọi thẳng bằng tên được.

## Chuẩn bị
- [ ] Máy đã mở Claude Code trên Claude Desktop, đăng nhập tài khoản CES cấp.
- [ ] Mở thư mục dự án đã tạo ở Buổi 1 (có sẵn file CLAUDE.md của bạn).
- [ ] Có bộ file demo của khóa (chứa `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`).
- [ ] **Mang theo 1 tài liệu dài trong công việc thật** của bạn: hợp đồng, biên bản họp, báo cáo, hoặc đề xuất. Dùng ở phần thực hành 2.

---

## PHẦN A: Tạo skill tom-tat-tai-lieu

### Bước 1: Nhờ Claude tạo file skill
Bạn không cần tự tay tạo thư mục hay file. Nhờ Claude làm. Copy prompt dưới, rồi dán nguyên khối nội dung SKILL.md (ở mục "Nội dung SKILL.md để copy" bên dưới) vào chỗ ghi chú.

Prompt mẫu (copy):
```
Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md với nội dung sau:

[dán nguyên khối nội dung SKILL.md ở mục bên dưới vào đây]
```

### Bước 2: Kiểm tra skill đã nằm đúng chỗ
- [ ] Claude báo đã tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md`.
- [ ] Mở thư mục dự án, thấy thư mục `.claude/skills/tom-tat-tai-lieu/` và file SKILL.md bên trong.

Nếu tạo sai chỗ, gõ:
```
Di chuyển file SKILL.md vào đúng đường dẫn .claude/skills/tom-tat-tai-lieu/SKILL.md
```

### Bước 3: Chạy thử skill trên hợp đồng demo
Gõ đúng câu này. Để ý: bạn KHÔNG nhắc gì tới skill, Claude tự nạp nhờ dòng mô tả.
```
Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md
```

Bản tóm tắt đúng phải bóc ra các số liệu sau (đối chiếu):

| Cần bóc ra | Giá trị đúng trong hợp đồng |
|---|---|
| Tổng giá trị | 120.000.000 đồng (đã gồm thuế) |
| Cách thanh toán | 2 đợt 50/50: đợt 1 60 triệu trong 5 ngày sau ký, đợt 2 60 triệu sau nghiệm thu |
| Thời hạn hợp đồng | 12 tháng, tự động gia hạn nếu không có ý kiến trước hạn 30 ngày |
| Phạt chậm thanh toán | 0,05% giá trị chậm trả mỗi ngày |
| Bảo mật | Còn hiệu lực 2 năm sau khi hợp đồng chấm dứt |
| Chấm dứt | Báo trước 30 ngày bằng văn bản |

### Bước 4: Thử quy tắc chống bịa
Hỏi một câu mà hợp đồng KHÔNG nói tới, xem skill có bịa không:
```
Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
```
- Đúng: Claude trả lời đại ý "Hợp đồng có điều khoản bảo mật nhưng không nêu mức phạt bằng tiền. Tài liệu không đề cập."
- Sai: Claude bịa ra một con số. Nếu gặp, xem lại SKILL.md có đủ mục QUY TẮC chưa (Bước chỉnh ở Phần C).

---

## Nội dung SKILL.md để copy
Dán đúng khối này vào chỗ Bước 1 (giữ nguyên cả hai dòng gạch ngang ba dấu và phần đầu name/description):

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

## PHẦN B: Dùng skill với tài liệu công việc thật của bạn

### Bước 5: Đưa tài liệu của bạn vào
- Đặt file tài liệu thật của bạn vào thư mục dự án (hoặc ghi nhớ đường dẫn đầy đủ tới file).

### Bước 6: Nhờ tóm tắt
```
Tóm tắt tài liệu trong [đường-dẫn-tới-file-của-bạn]
```
Nếu Claude không tự dùng skill (làm kiểu chung chung), gọi thẳng tên:
```
Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file-của-bạn]
```

### Bước 7: Đọc lại và kiểm tra
- [ ] Bản tóm tắt có đủ 5 mục không?
- [ ] Các con số, ngày tháng có khớp tài liệu gốc không?
- [ ] Có chỗ nào skill ghi "không đề cập" mà thực ra tài liệu CÓ nói không? (nếu có, chỉ cho Claude chỗ đó rồi hỏi lại)

---

## PHẦN C: Chỉnh dòng description cho hợp nghề của bạn (nâng cao, nếu còn giờ)

### Bước 8: Sửa mô tả cho hẹp đúng việc bạn làm
Dòng `description` càng rõ "dùng khi nào" thì Claude càng tự nạp đúng lúc. Ví dụ nếu bạn hay tóm tắt hợp đồng thuê mặt bằng:
```
Mở file .claude/skills/tom-tat-tai-lieu/SKILL.md, sửa dòng description thành: "Dùng khi cần tóm tắt hợp đồng thuê mặt bằng, bóc ra giá thuê, thời hạn, đặt cọc, điều khoản phạt."
```
Sau khi sửa, thử lại prompt tóm tắt xem Claude còn tự nạp đúng không.

### Bước 9: Thêm mục riêng cho nghề (tùy chọn)
Nếu cần thêm một mục vào bản tóm tắt (ví dụ mục "Bên chịu trách nhiệm"), nhờ Claude:
```
Trong file .claude/skills/tom-tat-tai-lieu/SKILL.md, thêm một mục mới tên "BÊN CHỊU TRÁCH NHIỆM" vào phần cấu trúc xuất ra.
```

---

## Ô ghi chú của bạn

Skill khác gì với gõ lại chỉ dẫn mỗi lần (viết bằng lời của bạn):
```
.......................................................................
.......................................................................
```

Việc lặp lại trong nghề bạn muốn đóng thành skill tiếp theo:
```
.......................................................................
.......................................................................
```

Chỗ skill làm chưa đúng và cách bạn đã sửa:
```
.......................................................................
.......................................................................
```

---

## Bài tập
- **Tại lớp:** Nộp 2 bản tóm tắt: 1 của hợp đồng demo, 1 của tài liệu công việc thật của bạn.
- **Về nhà:** Tạo thêm 1 skill cho một việc lặp lại khác trong nghề (soạn email trả khách, lập kế hoạch tuần, kiểm tra checklist). Viết dòng description rõ "dùng khi nào". Chạy thử 1 lần, chụp kết quả gửi nhóm Zalo.

## Checklist tự đánh giá
- [ ] Tôi có thư mục `.claude/skills/tom-tat-tai-lieu/` với file SKILL.md trong dự án của mình.
- [ ] Tôi chạy được skill trên hợp đồng demo, bản tóm tắt đủ 5 mục.
- [ ] Bản tóm tắt bóc đúng: 120 triệu, chia 2 đợt, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm.
- [ ] Tôi thử được câu hỏi chống bịa và thấy skill trả lời "không đề cập" thay vì đoán bừa.
- [ ] Tôi chạy được skill trên 1 tài liệu công việc thật của mình.
- [ ] Tôi giải thích được vì sao dòng description quan trọng.
