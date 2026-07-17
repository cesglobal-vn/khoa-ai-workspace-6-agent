# Giáo án Buổi 02: Skill - Đóng gói quy trình lặp lại

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

## Thông tin buổi
- **Buổi:** 02 / 6
- **Khái niệm chính:** Skill
- **Loại:** Thực chiến
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đã đăng nhập tài khoản CES cấp
- [ ] Mở sẵn thư mục dự án đã tạo ở Buổi 1 (có sẵn file CLAUDE.md của học viên)
- [ ] Mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-02/`
- [ ] File demo cần dùng: `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/skill-tom-tat-tai-lieu.md` (mở sẵn để copy nội dung SKILL.md)
- [ ] Chuẩn bị 1 tài liệu dài của riêng GV để làm ví dụ thực hành 2 (biên bản họp hoặc báo cáo)
- [ ] Kiểm tra: gõ thử prompt tạo skill 1 lần trước giờ lên lớp để chắc thao tác chạy trơn

## Mục tiêu buổi (học xong học viên làm được gì)
1. Nói được skill là gì và khác gì với việc gõ lại chỉ dẫn mỗi lần.
2. Biết skill là 1 thư mục chứa file SKILL.md, đặt đúng chỗ trong dự án.
3. Tự tay tạo skill "tom-tat-tai-lieu" trong dự án của mình.
4. Dùng skill để tóm tắt hợp đồng: bóc ra số tiền, ngày tháng, hạn chót, điều khoản bất lợi.
5. Hiểu quy tắc chống bịa: thông tin không có trong tài liệu thì ghi "không đề cập", không suy đoán.

## Kết quả cầm về (deliverable)
- 1 skill `tom-tat-tai-lieu` nằm trong thư mục dự án của học viên, chạy được.
- 1 bản tóm tắt hợp đồng demo do skill sinh ra (đủ 5 mục: tóm tắt nhanh, ý chính, số liệu, lưu ý, quy tắc).
- 1 bản tóm tắt tài liệu công việc thật của học viên.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Skill là gói chỉ dẫn cho một việc bạn làm đi làm lại.** Ví dụ: tóm tắt tài liệu, soạn email, kiểm tra hợp đồng. Thay vì mỗi lần lại gõ lại một loạt chỉ dẫn dài, bạn viết chỉ dẫn đó một lần vào skill, rồi dùng lại mãi.
- **Claude tự nạp skill khi gặp việc phù hợp.** Mỗi skill có một dòng mô tả (description) ghi rõ "dùng khi nào". Khi bạn nhờ một việc khớp với dòng mô tả đó, Claude tự lấy skill ra dùng. Bạn cũng gọi thẳng skill bằng tên được.
- **Skill là một thư mục chứa một file tên SKILL.md.** Đặt tại `.claude/skills/<ten-skill>/SKILL.md` trong thư mục dự án. Ví dụ: `.claude/skills/tom-tat-tai-lieu/SKILL.md`. Không phải cài đặt gì, chỉ là file văn bản.
- **Quy tắc quan trọng nhất khi tóm tắt: chống bịa.** Bắt AI chỉ dùng thông tin có thật trong tài liệu. Chỗ nào tài liệu không nói thì ghi "Tài liệu không đề cập", tuyệt đối không tự đoán ra con số hay điều khoản.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap buổi 1
- **Lời dẫn GV:** "Chào cả lớp. Buổi trước mình đã cài Claude Code, tạo thư mục dự án và viết file CLAUDE.md để agent nhớ bối cảnh công việc của mình. Hôm nay mình lên một nấc: dạy agent một quy trình để nó làm chuẩn mỗi lần, không phải nhắc lại. Cái đó gọi là skill."
- Recap buổi 1 (hỏi nhanh cả lớp, 3 câu):
  - Claude Code khác chat thường ở điểm nào? (tự làm nhiều bước, đọc/sửa file thật, nhớ bối cảnh)
  - File CLAUDE.md dùng để làm gì? (ghi bối cảnh dự án để agent tự đọc mỗi lần)
  - Thư mục dự án của bạn đang ở đâu trên máy? (kiểm tra cả lớp còn mở được)
- Nêu mục tiêu buổi hôm nay: tạo được 1 skill và dùng nó tóm tắt một hợp đồng.
- **Lời dẫn GV chốt mở đầu:** "Cuối buổi, mỗi người có một skill riêng chạy được, và một bản tóm tắt hợp đồng do chính skill của mình làm ra."

### [00:15-00:35] Lý thuyết ngắn: Skill là gì
- **Lời dẫn GV:** "Hình dung skill giống một tờ quy trình dán trên tường. Ai vào làm việc đó cũng theo đúng tờ quy trình, ra kết quả giống nhau. Skill là tờ quy trình đó, nhưng cho AI."
- Nội dung trình bày (giữ đơn giản, có thể vẽ lên bảng):
  1. **Vì sao cần skill.** Việc lặp lại mà mỗi lần gõ lại chỉ dẫn thì mất công và dễ quên bước. Skill viết một lần, dùng mãi, luôn đủ bước.
  2. **Skill nằm ở đâu.** Là một thư mục trong dự án: `.claude/skills/<ten-skill>/`. Trong đó có một file `SKILL.md`. Tên thư mục chính là tên skill.
  3. **Bên trong SKILL.md có gì.** Phần đầu ghi `name` (tên) và `description` (mô tả dùng khi nào). Phần thân là các bước chỉ dẫn cho AI làm.
  4. **Claude tự nạp nhờ dòng description.** Đây là điểm mấu chốt. Dòng mô tả viết càng rõ "dùng khi nào" thì Claude càng biết lúc nào lôi skill ra dùng. Nếu mô tả mờ, Claude không tự nạp, khi đó phải gọi thẳng tên skill.
- **Câu hỏi tương tác:** "Trong công việc của bạn, có việc nào tuần nào cũng làm, bước nào cũng giống nhau không? Kể một cái." (gọi 2-3 học viên, ghi lên bảng để cuối buổi họ tự làm skill cho việc đó)

### [00:35-01:00] Demo giảng viên: tạo skill và chạy trên hợp đồng
> GV làm mẫu trên màn hình chia sẻ. Học viên xem, chưa gõ theo.

**Bước 1: Tạo file SKILL.md cho skill tóm tắt tài liệu**
- **Lời dẫn GV:** "Mình sẽ nhờ Claude tạo giúp cái thư mục skill và file SKILL.md, không cần tự tay tạo file. Mình đọc nội dung skill cho nó ghi vào."
- **Prompt gõ vào Claude Code:**
  ```
  Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md với nội dung sau:

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
- **File demo:** không cần file demo cho bước này (đang tạo file cấu hình). Nội dung lấy từ `mau-cau-hinh/skill-tom-tat-tai-lieu.md`.
- **Kết quả mong đợi:** Claude báo đã tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md`. GV mở thư mục dự án cho lớp thấy thư mục `.claude/skills/tom-tat-tai-lieu/` vừa hiện ra và file SKILL.md có nội dung đúng như trên. GV nhấn: "Xong. Skill đã nằm trong dự án. Từ giờ nó dùng lại được mãi."

**Bước 2: Chạy skill để tóm tắt hợp đồng demo**
- **Lời dẫn GV:** "Giờ mình đưa một hợp đồng thật vào và chỉ cần nói tóm tắt. Để ý: mình không nhắc gì tới skill cả. Nhờ dòng description, Claude tự nhận ra đây là việc tóm tắt tài liệu và tự nạp skill mình vừa tạo."
- **Prompt gõ vào Claude Code:**
  ```
  Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- **Kết quả mong đợi:** Claude trả về bản tóm tắt đúng 5 mục của skill. Nội dung bóc ra phải khớp hợp đồng thật:
  - **Số liệu:** tổng giá trị **120.000.000 đồng** (đã gồm thuế), chia **2 đợt 50/50** (đợt 1 60 triệu trong 5 ngày sau ký, đợt 2 60 triệu sau nghiệm thu); bản quyền tối đa **20 người dùng**; đào tạo **2 buổi**.
  - **Ngày tháng, hạn chót:** ký ngày **10/6/2026**; cài đặt xong trong **15 ngày**; đào tạo trong **30 ngày**; thời hạn **12 tháng, tự động gia hạn** nếu không có ý kiến trước khi hết hạn 30 ngày.
  - **Điểm lưu ý / rủi ro:** **phạt chậm thanh toán 0,05%/ngày**; điều khoản **bảo mật còn hiệu lực 2 năm** sau khi chấm dứt; chấm dứt phải **báo trước 30 ngày**; nếu Bên B giao trễ quá 20 ngày, Bên A được chấm dứt và hoàn tiền phần chưa thực hiện.
- **Lời dẫn GV chốt demo:** "Để ý dòng đầu Claude thường báo nó đang dùng skill tom-tat-tai-lieu. Đó là bằng chứng skill tự nạp. Và mọi con số nó lấy đều có thật trong hợp đồng, không tự chế ra."

**Bước 3: Thử quy tắc chống bịa (điểm nhấn của buổi)**
- **Lời dẫn GV:** "Giờ mình thử một câu hỏi mà hợp đồng KHÔNG hề nói tới, xem skill có bịa không."
- **Prompt gõ vào Claude Code:**
  ```
  Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- **Kết quả mong đợi:** Claude trả lời đại ý "Hợp đồng có điều khoản bảo mật (Điều 6) nhưng KHÔNG nêu mức phạt bằng tiền cho việc tiết lộ. Tài liệu không đề cập con số này." Không được bịa ra một số tiền. GV nhấn: "Đây là lý do có mục QUY TẮC trong skill. Với hợp đồng và số liệu, thà nói không có còn hơn đoán sai."

### [01:00-01:30] Thực hành 1: học viên tự tạo skill và chạy trên hợp đồng demo
- **Lời dẫn GV:** "Đến lượt cả lớp. Làm đúng 2 việc mình vừa demo: một, tạo skill; hai, tóm tắt hợp đồng. Ai xong giơ tay, mình qua xem kết quả."
- **Đề bài:**
  1. Tạo skill `tom-tat-tai-lieu` trong thư mục dự án của mình.
  2. Chạy skill trên hợp đồng demo.
  3. Kiểm tra bản tóm tắt có bóc đúng: 120 triệu, chia 2 đợt, thời hạn 12 tháng, phạt chậm 0,05%/ngày, bảo mật 2 năm.
- **Prompt gợi ý cho học viên (tạo skill):**
  ```
  Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md. Nội dung tôi dán ngay dưới đây:
  [dán nguyên khối nội dung SKILL.md từ workbook]
  ```
- **Prompt gợi ý cho học viên (chạy skill):**
  ```
  Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- **Kết quả mong đợi:** Mỗi học viên có thư mục `.claude/skills/tom-tat-tai-lieu/` và một bản tóm tắt hợp đồng đủ 5 mục, các số liệu khớp hợp đồng thật. GV đi một vòng xác nhận từng máy, sửa nhanh các lỗi hay gặp (xem bảng tình huống bên dưới).

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2: dùng skill với tài liệu công việc thật của học viên
- **Lời dẫn GV:** "Skill của bạn đã chạy tốt với hợp đồng mẫu. Giờ mới là phần đáng tiền: đưa một tài liệu thật trong công việc của bạn vào. Cùng một skill đó, không phải tạo lại."
- **Đề bài:**
  1. Lấy 1 tài liệu dài trong công việc thật (hợp đồng, biên bản họp, báo cáo, đề xuất) đã chuẩn bị.
  2. Đặt nó vào thư mục dự án (hoặc chỉ cho Claude đường dẫn tới file).
  3. Nhờ tóm tắt bằng đúng skill vừa tạo.
  4. Đọc lại bản tóm tắt: kiểm tra số liệu có đúng không, có chỗ nào skill ghi "không đề cập" mà thực ra tài liệu có nói không.
- **Prompt gợi ý:**
  ```
  Tóm tắt tài liệu trong [đường-dẫn-tới-file-của-bạn]
  ```
  Nếu Claude không tự dùng skill, gọi thẳng tên:
  ```
  Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file]
  ```
- **File demo:** tài liệu riêng của từng học viên (không dùng file demo chung).
- **Kết quả mong đợi:** Mỗi học viên có bản tóm tắt tài liệu công việc của mình, đủ cấu trúc 5 mục. GV nhắc: nếu thấy mục nào chưa hợp với nghề của mình (ví dụ cần thêm mục "Bên chịu trách nhiệm"), có thể sửa phần thân SKILL.md, đó chính là cách skill lớn dần theo nhu cầu.
- **Mở rộng cho ai làm nhanh:** chỉnh dòng `description` cho hẹp đúng nghề (ví dụ "Dùng khi tóm tắt hợp đồng thuê mặt bằng") rồi thử lại xem Claude còn tự nạp đúng không.

### [02:15-02:35] Chốt & giao bài
- **Lời dẫn GV:** "Tóm lại hôm nay: skill là gói chỉ dẫn cho việc lặp lại, để trong `.claude/skills/`, Claude tự nạp nhờ dòng mô tả. Bạn đã có một skill chạy được và hai bản tóm tắt. Skill này còn dùng dài dài về sau."
- Tổng kết 3 ý cần nhớ:
  1. Skill = 1 thư mục + 1 file SKILL.md.
  2. Dòng `description` quyết định Claude có tự nạp đúng lúc không.
  3. Quy tắc chống bịa: không có trong tài liệu thì nói không có.
- **Bài về nhà:** tạo thêm 1 skill cho một việc lặp lại khác trong nghề của mình (soạn email trả lời khách, lập kế hoạch tuần, kiểm tra checklist). Chạy thử 1 lần, chụp kết quả gửi vào nhóm Zalo.
- **Xem trước buổi sau:** "Buổi 3 mình học MCP: cách cắm thêm công cụ và dữ liệu ngoài cho agent, để nó đọc được cả file Excel, web, Google Drive. Nhớ mang theo 1 file Excel hoặc CSV công việc của bạn."

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | `Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md với nội dung sau: [nội dung]` | (không) | Tạo được thư mục skill + file SKILL.md đúng nội dung |
| 2 | `Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md` | `hop-dong-dich-vu-mau.md` | Bản tóm tắt 5 mục, bóc đúng 120 triệu, 2 đợt 50/50, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm |
| 3 | `Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?` | `hop-dong-dich-vu-mau.md` | Trả lời "Tài liệu không đề cập", không bịa ra số tiền |
| 4 | `Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file]` | tài liệu HV | Bản tóm tắt 5 mục cho tài liệu thật của học viên |

## Câu hỏi tương tác gợi ý
- "Việc nào trong công việc bạn tuần nào cũng làm, bước nào cũng giống? Cái đó đóng gói thành skill được không?"
- "Theo bạn, vì sao dòng description lại quan trọng đến vậy?" (vì Claude dựa vào đó để tự nạp đúng skill)
- "Nếu hợp đồng không nói mức phạt, skill nên trả lời thế nào?" (ghi không đề cập, không đoán)
- "Skill khác gì với việc mỗi lần bạn gõ lại một loạt chỉ dẫn dài?" (viết một lần, dùng mãi, luôn đủ bước)

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Học viên nhờ tóm tắt nhưng Claude không tự dùng skill (làm kiểu chung chung) | Dòng description mờ hoặc câu nhờ chưa khớp. Bảo học viên gọi thẳng: "Dùng skill tom-tat-tai-lieu để tóm tắt...". Sau đó sửa description cho rõ hơn phần "dùng khi nào". |
| Claude bịa ra một con số hoặc điều khoản không có trong hợp đồng | Nhắc lại mục QUY TẮC. Kiểm tra SKILL.md có đủ dòng "Chỉ dùng thông tin có trong tài liệu... KHÔNG suy đoán" không. Nếu thiếu thì thêm vào. Cho học viên hỏi lại câu bịa đó để đối chiếu. |
| Tạo file sai chỗ (không nằm trong `.claude/skills/`) | Nhờ Claude: "Di chuyển file SKILL.md vào đúng đường dẫn .claude/skills/tom-tat-tai-lieu/SKILL.md". Kiểm tra lại thư mục. |
| Đặt tên thư mục skill có dấu cách hoặc chữ hoa | Đổi về chữ thường, nối bằng dấu gạch nối: `tom-tat-tai-lieu`. Nhờ Claude đổi tên giúp. |
| Bản tóm tắt thiếu mục (ví dụ thiếu mục số liệu) | Thường do phần thân SKILL.md bị dán thiếu. Mở SKILL.md đối chiếu với mẫu, dán lại cho đủ 5 mục. |
| Claude báo không tìm thấy file hợp đồng | Sai đường dẫn. Kiểm tra file có nằm trong thư mục dự án không, gõ lại đúng đường dẫn `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`. |

## Bài tập
- **Tại lớp:** Tạo skill `tom-tat-tai-lieu`, chạy trên hợp đồng demo, rồi chạy trên 1 tài liệu công việc thật của mình. Nộp 2 bản tóm tắt.
- **Về nhà:** Tạo thêm 1 skill cho một việc lặp lại khác trong nghề của mình. Viết dòng description rõ "dùng khi nào". Chạy thử 1 lần, chụp kết quả gửi nhóm Zalo.

## Tiêu chí hoàn thành buổi
- [ ] Có thư mục `.claude/skills/tom-tat-tai-lieu/` với file SKILL.md đúng nội dung trong dự án của học viên.
- [ ] Chạy skill trên hợp đồng demo, bản tóm tắt đủ 5 mục và bóc đúng các số liệu chính (120 triệu, 2 đợt, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm).
- [ ] Chạy được skill trên 1 tài liệu công việc thật của học viên.
- [ ] Học viên giải thích được vai trò dòng description và quy tắc chống bịa.
