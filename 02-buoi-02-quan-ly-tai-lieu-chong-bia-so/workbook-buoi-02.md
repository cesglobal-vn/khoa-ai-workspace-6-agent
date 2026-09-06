# Workbook Buổi 02: Skill - Đóng gói quy trình lặp lại

> Sổ tay thực hành cho học viên. PHẦN A bạn NHÌN THEO GV demo (chưa gõ). Từ PHẦN B trở đi bạn tự làm. Prompt trong khối xám copy dán được ngay.

## Mục tiêu buổi này
Học xong, bạn sẽ:
1. Hiểu skill là gì và vì sao nó tiết kiệm công so với gõ lại chỉ dẫn mỗi lần.
2. Thấy tận mắt một skill SINH RA từ đâu: làm tay qua 5 lượt chat cho ra kết quả ưng ý, rồi đóng gói chỗ đó lại thành skill. Không phải chép một file mẫu có sẵn.
3. Tự tạo skill `tom-tat-tai-lieu` và chạy trên hợp đồng.
4. Nắm quy tắc chống bịa: tài liệu không có thì ghi "không đề cập", không tự đoán.

## Skill là gì (đọc nhanh trước khi làm)
- **Skill là một gói chỉ dẫn cho việc bạn làm đi làm lại.** Viết một lần, dùng mãi. Ví dụ: tóm tắt tài liệu, soạn email, kiểm tra hợp đồng.
- **Về mặt file, skill là một thư mục có một file tên SKILL.md**, đặt tại `.claude/skills/<ten-skill>/SKILL.md` trong thư mục dự án của bạn.
- **Claude tự nạp skill nhờ dòng mô tả (description).** Dòng này ghi rõ "dùng khi nào". Khi bạn nhờ một việc khớp mô tả, Claude tự lấy skill ra dùng. Bạn cũng gọi thẳng bằng tên được.

## Chuẩn bị
- [ ] Máy đã mở Claude Code trên Claude Desktop, đăng nhập tài khoản CES cấp.
- [ ] Mở thư mục dự án đã tạo ở Buổi 1 (có sẵn file CLAUDE.md của bạn).
- [ ] Có bộ file demo của khóa: báo cáo `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bao-cao-tong-ket-nam-2026.docx` và hợp đồng `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md`.
- [ ] **Mang theo 1 tài liệu dài trong công việc thật** của bạn (hợp đồng, biên bản, báo cáo, đề xuất). Dùng ở PHẦN C.

---

## PHẦN A: Xem GV demo - từ 5 lượt chat tới một skill

> **Phần này bạn CHỈ NHÌN THEO, chưa gõ.** Mục đích: thấy một skill không phải file mẫu tải từ đâu về, mà là biên bản của mấy lượt mình phải hỏi. GV tóm tắt một báo cáo dài 14 trang, phải hỏi đi hỏi lại 5 lượt mới ra bản dùng được, rồi mới đóng gói thành skill. **Mỗi lượt chat biến thành đúng một mục trong skill.**

GV chạy trên file: `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bao-cao-tong-ket-nam-2026.docx`

**Lượt 1 - Tóm tắt kiểu thông thường (để thấy nó chưa đủ):**
```
Tóm tắt giúp tôi báo cáo trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bao-cao-tong-ket-nam-2026.docx
```
Ra bản chung chung: doanh thu tăng, Gói Cao cấp bán tốt, có khó khăn nhân sự. Nghe xuôi tai nhưng chưa bóc đủ số, chưa gom hạn chót. Chưa dùng được.

**Lượt 2 - Ép liệt kê theo từng phần:**
```
Chưa đủ. Liệt kê lại theo từng phần của báo cáo, mỗi phần vài ý chính.
```
Lượt này sau sẽ thành mục **Ý CHÍNH CHI TIẾT**.

**Lượt 3 - Bóc số liệu và hạn chót:**
```
Bóc ra mọi con số, mốc thời gian, cam kết quan trọng trong tài liệu.
```
Lượt này sau sẽ thành mục **SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT**. (Để ý: có mốc 28/02/2027 chôn sâu ở phụ lục, không đọc kỹ là trượt.)

**Lượt 4 - Hỏi chỗ bất lợi, mâu thuẫn, mập mờ (lượt quan trọng nhất):**
```
Trong báo cáo này có điều khoản nào bất lợi, chỗ nào mâu thuẫn, hoặc chỗ nào mập mờ không?
```
Lượt này sau sẽ thành mục **ĐIỂM CẦN LƯU Ý / RỦI RO**. (Đây là chỗ AI bắt được báo cáo tự vênh số: mục II.1 ghi tổng 12.450 triệu, nhưng các bảng cộng ra 12.545 triệu, lệch 95 triệu.)

**Lượt 5 - Chặn suy đoán và rút gọn:**
```
Trong những gì bạn vừa trả lời, có chỗ nào bạn tự suy đoán mà tài liệu không nói không? Từ giờ chỉ dùng thông tin có trong tài liệu, chỗ nào tài liệu không nói thì ghi "Tài liệu không đề cập", không được đoán. Rút lại giúp tôi 3 tới 5 gạch đầu dòng quan trọng nhất để tôi gửi sếp.
```
Lượt này sau sẽ thành mục **QUY TẮC** và mục **TÓM TẮT NHANH**.

**Đóng gói - biến 5 lượt vừa rồi thành một skill:**
```
Tôi thấy kết quả ổn rồi, giờ hãy đóng gói lại thành skill tóm tắt tài liệu cho tôi, để sau này tôi không phải chat nhiều nữa mà bạn vẫn đưa ra kết quả tốt. Sau này tôi muốn khi bảo bạn "Tóm tắt tài liệu abc" thì bạn sẽ tự động kích hoạt skill này cho tôi.

Khi tôi đưa vào một tài liệu nào đó, làm theo các bước:

1. Đọc toàn bộ tài liệu.
2. Xuất ra đúng cấu trúc sau:
- TÓM TẮT NHANH
+ 3 tới 5 gạch đầu dòng ý chính nhất.

- Ý CHÍNH CHI TIẾT
+ Liệt kê theo từng mục/phần của tài liệu.

- SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT
+ Bóc ra mọi con số, mốc thời gian, cam kết quan trọng.

- ĐIỂM CẦN LƯU Ý / RỦI RO
+ Nếu có điều khoản bất lợi, mâu thuẫn, hoặc chỗ mập mờ.

- QUY TẮC
+ Chỉ dùng thông tin có trong tài liệu. Không có thì ghi "Tài liệu không đề cập", KHÔNG suy đoán.
+ Trích nguyên văn khi cần bằng chứng, đặt trong ngoặc kép.
+ Trả lời bằng tiếng Việt, rõ ràng.
```
Claude tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md`. **5 mục trong file đúng bằng 5 lượt bạn vừa xem GV hỏi** - không phải cấu trúc bịa ra.

**Chạy lại trên hợp đồng (chỉ 1 lượt ra đủ 5 mục):**
```
Tóm tắt hợp đồng trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md
```
Báo cáo mất 5 lượt, hợp đồng chỉ 1 lượt. Đó là toàn bộ giá trị của skill.

**Thử chống bịa:**
```
Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
```
Đúng: Claude trả lời đại ý "hợp đồng có điều khoản bảo mật nhưng không nêu mức phạt bằng tiền. Tài liệu không đề cập." Không được bịa ra một con số.

---

## PHẦN B: Thực hành 1 - Bạn tự tạo skill và chạy trên hợp đồng

> Tới lượt bạn. Bạn vừa xem skill sinh ra từ 5 lượt. Giờ để nhanh, dùng luôn bản đã đóng gói đó: dán khối "Nội dung SKILL.md" ở PHỤ LỤC cuối sổ.

### Bước 1: Tạo skill
```
Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md. Nội dung tôi dán ngay dưới đây:
[dán nguyên khối "Nội dung SKILL.md" ở PHỤ LỤC vào đây]
```
- [ ] Claude báo đã tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md`.
- [ ] Mở thư mục dự án, thấy thư mục `.claude/skills/tom-tat-tai-lieu/` và file bên trong.

### Bước 2: Chạy trên hợp đồng (không nhắc skill, xem Claude tự nạp)
```
Tóm tắt hợp đồng trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md
```
Bản tóm tắt đúng phải bóc ra (đối chiếu):

| Cần bóc ra | Giá trị đúng trong hợp đồng |
|---|---|
| Tổng giá trị | 120.000.000 đồng (đã gồm thuế) |
| Cách thanh toán | 2 đợt 50/50: đợt 1 60 triệu trong 5 ngày sau ký, đợt 2 sau nghiệm thu |
| Thời hạn hợp đồng | 12 tháng, tự động gia hạn nếu không có ý kiến trước hạn 30 ngày |
| Phạt chậm thanh toán | 0,05% giá trị chậm trả mỗi ngày |
| Bảo mật | Còn hiệu lực 2 năm sau khi hợp đồng chấm dứt |
| Chấm dứt | Báo trước 30 ngày bằng văn bản |

### Bước 3: Thử quy tắc chống bịa
```
Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
```
- [ ] Claude trả lời đại ý "có điều khoản bảo mật nhưng không nêu mức phạt bằng tiền. Tài liệu không đề cập".
- [ ] Claude KHÔNG bịa ra một con số. Nếu bịa, xem lại khối SKILL.md có đủ mục QUY TẮC chưa.

---

## PHẦN C: Thực hành 2 - Chạy skill trên tài liệu thật của bạn

### Bước 4: Đưa tài liệu của bạn vào
Đặt file tài liệu thật của bạn vào thư mục dự án (hoặc ghi nhớ đường dẫn đầy đủ), rồi:
```
Tóm tắt tài liệu trong [đường-dẫn-tới-file-của-bạn]
```
Nếu Claude không tự dùng skill (làm kiểu chung chung), gọi thẳng tên:
```
Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file-của-bạn]
```
- [ ] Bản tóm tắt có đủ 5 mục.
- [ ] Các con số, ngày tháng khớp tài liệu gốc.
- [ ] Không có chỗ nào skill ghi "không đề cập" mà thực ra tài liệu CÓ nói.

**Mở rộng (nếu còn giờ):** chỉnh dòng description cho hẹp đúng nghề của bạn, rồi thử lại xem Claude còn tự nạp đúng không:
```
Mở file .claude/skills/tom-tat-tai-lieu/SKILL.md, sửa dòng description thành: "Dùng khi cần tóm tắt hợp đồng thuê mặt bằng, bóc ra giá thuê, thời hạn, đặt cọc, điều khoản phạt."
```

---

## PHẦN D: Thực hành 3 (nâng cao) - Tạo tài liệu có thương hiệu rồi đóng gói thành skill

> Phần này lặp lại đúng bài học của buổi (làm qua vài lượt chat rồi đóng gói thành skill), nhưng sản phẩm cuối là một skill tạo tài liệu có thương hiệu CES Global. Cần mạng (Bước 5 tra web) và máy chạy được script tạo Word. Nếu máy chưa đủ điều kiện, xem GV demo rồi làm ở nhà.

Chuẩn bị: logo tại `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/logo-ces.png`, bộ màu tại `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bo-nhan-dien-ces.md`.

### Bước 5: Bảo agent tự tra thông tin và xuất ra file
```
Tìm hiểu và gửi tôi báo cáo về xu hướng phát triển AI trong năm 2026. Trả kết quả ra file md
```
- [ ] Agent tạo được 1 file `.md` nhiều mục, có phần nguồn tham khảo. (Nội dung mỗi lần một khác vì tra web thật, đó là bình thường.)

### Bước 6: Đóng nội dung thành tài liệu có thương hiệu
```
Tổng hợp nội dung báo cáo vừa rồi thành 1 file docx. Dùng bộ nhận diện CES Global: chèn logo 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/logo-ces.png vào header mỗi trang; tone màu theo 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bo-nhan-dien-ces.md (tiêu đề navy 1B3285, điểm nhấn teal 009898 và vàng C47F0A, cảnh báo đỏ C0392B). Chữ tiếng Việt phải đủ dấu, không lỗi phông: dùng phông Unicode (Arial hoặc Times New Roman) và lưu UTF-8.
```
- [ ] File docx có logo ở header mỗi trang.
- [ ] Màu tiêu đề đúng navy, điểm nhấn teal/vàng.
- [ ] Chữ tiếng Việt đủ dấu, không có ô vuông hay dấu hỏi.

### Bước 7: Đóng gói cả quy trình thành skill
```
Tôi thấy file này đẹp rồi, bây giờ hãy tạo cho tôi skill đóng gói tài liệu đẹp và đúng tone màu như trên, sau này khi tôi nói tạo tài liệu theo chuẩn CES Global thì hãy áp dụng skill này cho tôi. Đóng gói thành skill và lưu vào folder skill tại workspace hiện tại nhé.
```
- [ ] Có file skill trong `.claude/skills/` (ví dụ `tao-tai-lieu-ces`).
- [ ] Thử gõ "Tạo tài liệu theo chuẩn CES Global cho nội dung ABC" và agent tự nạp skill vừa tạo.

> Ghi nhớ: hai lần trong buổi bạn đều làm cùng một việc - làm tay qua vài lượt cho ưng ý, rồi đóng gói thành skill. Lần đầu là skill tóm tắt, lần này là skill tạo tài liệu có thương hiệu. Đó là cách biến mọi việc lặp lại thành skill.

---

## PHỤ LỤC: Nội dung SKILL.md để dán nhanh

> Đây là bản skill đã đóng gói ở PHẦN A. Dùng cho PHẦN B Bước 1 khi bạn muốn tạo skill nhanh mà không gõ lại 5 lượt.

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
- **Tại lớp:** Nộp 2 bản tóm tắt - 1 của hợp đồng demo, 1 của tài liệu công việc thật của bạn.
- **Về nhà:** Tạo thêm 1 skill cho một việc lặp lại khác trong nghề (soạn email trả khách, lập kế hoạch tuần, kiểm tra checklist). Viết dòng description rõ "dùng khi nào". Chạy thử 1 lần, chụp kết quả gửi nhóm Zalo.

## Checklist tự đánh giá
- [ ] Tôi hiểu skill sinh ra từ đâu: làm tay vài lượt rồi đóng gói, không phải chép file mẫu.
- [ ] Tôi có thư mục `.claude/skills/tom-tat-tai-lieu/` với file SKILL.md trong dự án của mình.
- [ ] Tôi chạy được skill trên hợp đồng demo, bản tóm tắt đủ 5 mục.
- [ ] Bản tóm tắt bóc đúng: 120 triệu, chia 2 đợt, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm.
- [ ] Tôi thử được câu hỏi chống bịa và thấy skill trả lời "không đề cập" thay vì đoán bừa.
- [ ] Tôi chạy được skill trên 1 tài liệu công việc thật của mình.
- [ ] Tôi giải thích được vì sao dòng description quan trọng.
