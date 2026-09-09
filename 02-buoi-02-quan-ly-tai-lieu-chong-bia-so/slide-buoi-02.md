# BỘ SLIDE BÀI GIẢNG BUỔI 02: SKILL – ĐÓNG GÓI QUY TRÌNH LẶP LẠI & CHỐNG BỊA SỐ LIỆU

> **Đơn vị đào tạo:** CES Global — Trung tâm Đào tạo & Ứng dụng Công nghệ  
> **Chương trình:** Khóa AI Workspace — Làm chủ 6 AI Agent với Claude Code  
> **Buổi học:** 02 / 6 | **Khái niệm chính:** Skill & Kỷ luật Chống Bịa Số Liệu  
> **Thời lượng:** 150 phút (2,5 giờ) | Live Zoom & VIP LMS  
> **Quy chuẩn hiển thị:** Mỗi cặp dấu ngăn cách `---` tương ứng với 01 slide trình chiếu độc lập. Phần `[Ghi chú Giảng viên]` cung cấp lời dẫn thoại trực tiếp và prompt chính xác để giảng viên đứng lớp.

---

## Slide 01: Slide Tiêu Đề

# KHÓA HỌC: AI WORKSPACE
## Làm Chủ 6 AI Agent Thực Chiến Với Claude Code

### BUỔI 02: SKILL – ĐÓNG GÓI QUY TRÌNH LẶP LẠI & CHỐNG BỊA SỐ LIỆU (AGENT QUẢN LÝ TÀI LIỆU)

- **Đơn vị tổ chức:** CES Global — AI Technology & Training Center
- **Website đào tạo:** https://nhanvienai.cesglobal.com.vn
- **Thời lượng:** 150 phút (20:00 – 22:30)
- **Phương châm:** *"Từ chat đi chat lại 5 lần sang đóng gói 1 Skill dùng mãi mãi"*

[Ghi chú Giảng viên]: Chào mừng học viên đến với Buổi 02. Nhắc lại Buổi 1 đã có CLAUDE.md để AI nhớ bối cảnh. Hôm nay lớp mình lên một bậc cao hơn: dạy agent một quy trình để nó làm chuẩn mỗi lần, không phải nhắc lại. Cái đó gọi là Skill.

---

## Slide 02: Mục Tiêu & 6 Chuẩn Đầu Ra Buổi 02

### Học xong buổi hôm nay, bạn sẽ làm chủ:

1. **Bản chất Skill:** Hiểu rõ Skill là tờ quy trình SOP cho AI, viết 1 lần dùng mãi mãi.
2. **Nguồn gốc Skill:** Nhìn thấy Skill sinh ra từ đâu: làm tay 5 lượt chat rồi gói lại, không phải chép mẫu có sẵn.
3. **Cấu trúc vật lý:** Nắm vững cấu trúc thư mục `.claude/skills/<ten-skill>/SKILL.md`.
4. **Cơ chế tự nạp (Auto-load):** Hiểu vì sao dòng `description` quyết định AI tự lấy đúng skill ra dùng.
5. **Kỷ luật chống bịa số:** Ép AI chỉ trích xuất thông tin có thật; không có thì ghi "Tài liệu không đề cập", tuyệt đối không suy đoán.
6. **Sản phẩm cầm về (Deliverables):** Tự tạo skill `tom-tat-tai-lieu` chạy được trên máy, tóm tắt hợp đồng demo và tài liệu công việc thật.

[Ghi chú Giảng viên]: Điểm qua 6 chuẩn đầu ra cụ thể. Nhấn mạnh cuối buổi mỗi người sẽ có 1 skill riêng chạy được và 2 bản tóm tắt thực chiến.

---

## Slide 03: Nỗi Đau Chat Thông Thường vs Sức Mạnh Đóng Gói Skill

### Chatbot thông thường (Nghĩ gì gõ nấy):
- **Lặp lại chỉ dẫn mệt mỏi:** Tuần nào cũng tóm tắt báo cáo hay hợp đồng, mỗi lần lại phải gõ lại một tràng yêu cầu dài.
- **Hỏi 5 câu mới ra đủ ý:** Lần đầu ra chung chung, lần 2 bắt chia phần, lần 3 đòi số liệu, lần 4 mới soi mâu thuẫn.
- **Kết quả hên xui, không ổn định:** Hôm nay hỏi kiểu này ra kiểu này, mai hỏi kiểu khác ra kiểu khác; đồng nghiệp hỏi ra kết quả lệch nhau.
- **Ảo giác & tự bịa số liệu:** AI hay tự điền số hoặc suy đoán khi tài liệu thiếu dữ liệu $\rightarrow$ cực kỳ nguy hiểm trong hợp đồng và tài chính.

### Hệ thống Skill trong Claude Code:
- **Viết 1 lần, dùng mãi mãi:** Đóng gói toàn bộ tiêu chuẩn thành một tờ quy trình chuẩn cho AI.
- **1 câu lệnh ra trọn vẹn kết quả:** Không cần nhắc lại cấu trúc, AI tự xuất đủ 5 phần cố định.
- **Chuẩn hóa toàn doanh nghiệp:** Bất kỳ ai trong team gọi skill đều nhận được kết quả cùng một chuẩn chất lượng.
- **Kỷ luật chống bịa số 100%:** Ép AI chỉ dùng dữ liệu có thật, bảo vệ an toàn pháp lý cho người dùng.

[Ghi chú Giảng viên]: Đánh thẳng vào nỗi đau của dân văn phòng: copy-paste mỏi tay và kết quả AI không đáng tin. Skill sinh ra để giải quyết triệt để vấn đề này.

---

## Slide 04: Bản Chất Cốt Lõi: Skill Sinh Ra Từ Đâu?

### Skill KHÔNG PHẢI là một file mẫu tải trên mạng về chép!

> *"Hình dung skill giống một tờ quy trình SOP dán trên tường. Ai vào làm việc đó cũng theo đúng tờ quy trình, ra kết quả giống nhau. Skill là tờ quy trình đó, nhưng viết cho AI."*

### Vòng lặp hình thành một Skill:
1. **Làm bằng tay (Manual Iterations):** Tự chat với AI qua 3 – 5 lượt để nắn kết quả theo đúng ý mình.
2. **Nhận diện sự lặp lại (Pattern Recognition):** Phát hiện ra những chỉ dẫn nào mình liên tục phải nhắc lại cho AI.
3. **Đóng gói quy trình (Packaging):** Gom toàn bộ các yêu cầu đó vào 1 file `SKILL.md` để lần sau AI tự động áp dụng.

[Ghi chú Giảng viên]: Nhấn mạnh thông điệp: "Lát nữa tôi không đưa sẵn file mẫu cho cả lớp chép. Tôi sẽ làm việc bằng tay trước, rồi cả lớp xem tờ quy trình đó tự hình thành thế nào."

---

## Slide 05: Vị Trí Lưu Trữ & Cấu Trúc Thư Mục Skill

### Cây thư mục chuẩn hóa trong Workspace:

```
my-workspace/
├── CLAUDE.md                                # Hiến pháp bối cảnh dự án
├── .claude/
│   └── skills/                              # Kho chứa các Skill của bạn
│       └── tom-tat-tai-lieu/                # Thư mục mang tên Skill
│           └── SKILL.md                     # File quy trình duy nhất
└── demo/
    ├── bao-cao-tong-ket-nam-2026.docx
    └── hop-dong-dich-vu-mau.md
```

### Quy tắc bất biến khi tạo Skill:
- Nằm trong thư mục: `.claude/skills/<ten-skill>/`
- Tên file BẮT BUỘC là: `SKILL.md` (viết hoa chữ SKILL)
- Tên thư mục dùng chữ thường, không dấu, nối bằng gạch ngang: `tom-tat-tai-lieu`

[Ghi chú Giảng viên]: Giải thích giải phẫu thư mục. Không cần cài đặt phần mềm phức tạp, skill đơn giản chỉ là 1 thư mục chứa 1 file văn bản đặt đúng chỗ.

---

## Slide 06: Trái Tim Của Skill: Dòng `description` & Cơ Chế Tự Nạp

### Giải phẫu phần đầu file `SKILL.md`:

```yaml
---
name: tom-tat-tai-lieu
description: Dùng khi cần tóm tắt tài liệu, báo cáo, hợp đồng, văn bản dài. Tự động bóc tách số liệu, hạn chót, phát hiện rủi ro và tuân thủ kỷ luật chống bịa số.
---
```

### Dòng `description` quyết định tất cả:
- **Cơ chế Tự nạp (Auto-load):** Khi bạn yêu cầu *"Tóm tắt báo cáo này"*, Claude tự đọc dòng mô tả của mọi skill trong thư mục và tự lấy skill phù hợp nhất ra dùng.
- **Mô tả rõ "Dùng khi nào":** Mô tả càng cụ thể tình huống kích hoạt thì AI càng nạp chính xác.
- **Hai cách kích hoạt:**
  - *Cách 1 (Tự động):* Gõ tự nhiên theo đúng ngữ cảnh trong `description`.
  - *Cách 2 (Chỉ định):* Gọi thẳng tên: `Dùng skill tom-tat-tai-lieu để...`

[Ghi chú Giảng viên]: Đặt câu hỏi tương tác: "Nếu bạn viết description mờ nhạt như 'Skill tóm tắt' thì chuyện gì xảy ra?" $\rightarrow$ Claude sẽ không biết khi nào nên lôi ra dùng.

---

## Slide 07: Kỷ Luật Chống Bịa Số Liệu (Anti-Hallucination)

### Nỗi sợ lớn nhất của dân văn phòng & quản lý:
> *"AI trả lời nghe rất mượt, nhưng con số và điều khoản thì do nó... tự bịa ra!"*

### 3 Nguyên tắc "Sắt Đá" Chống Bịa trong Skill:
1. **Chỉ dùng thông tin có thật:** 100% dữ liệu phải được trích xuất trực tiếp từ văn bản người dùng cung cấp.
2. **Kỷ luật "Tài liệu không đề cập":** Chỗ nào văn bản không nói tới $\rightarrow$ BẮT BUỘC ghi rõ: *"Tài liệu không đề cập"*. Tuyệt đối KHÔNG suy đoán hay tự bổ sung số liệu!
3. **Trích dẫn nguyên văn bằng chứng:** Những điều khoản quan trọng, rủi ro pháp lý phải đặt trong ngoặc kép `"..."`.

[Ghi chú Giảng viên]: Nhấn mạnh: Với hợp đồng và số liệu kinh doanh, thà để AI nói "không có" còn hơn để nó đoán sai và dẫn tới quyết định sai lầm.

---

## Slide 08: Tài Liệu Demo 14 Trang: Báo Cáo Tổng Kết Năm 2026

### Thử thách thực tế trước giờ họp:
- **Tài liệu:** `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bao-cao-tong-ket-nam-2026.docx`
- **Quy mô:** 14 trang, 9 phần La Mã, 4 bảng số liệu chi tiết, 2 phụ lục hợp đồng & công nợ.
- **Bối cảnh:** Bạn có đúng 10 phút trước giờ họp Hội đồng Quản trị để nắm toàn bộ bức tranh tài chính và các bẫy rủi ro!

### Hành trình Demo của Giảng viên:
- Đi qua chuỗi 5 lượt chat thực tế để học viên nhìn thấy nỗi đau.
- Đóng gói 5 lượt chat thành 1 skill hoàn chỉnh.
- Kiểm chứng trên tài liệu khác với đúng 1 câu lệnh!

[Ghi chú Giảng viên]: Mở file Word trên màn hình, cuộn cho học viên thấy độ dày thật 14 trang. Đặt câu hỏi: "Ai đọc hết và nắm trọn vẹn số liệu trong 10 phút?"

---

## Slide 09: Demo GV Lượt 1 & Lượt 2: Từ Tóm Tắt Hời Hợt Đến Ép Bố Cục

### Lượt 1: Tóm tắt thông thường (Nghĩ gì gõ nấy)
```text
Tóm tắt giúp tôi báo cáo trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bao-cao-tong-ket-nam-2026.docx
```
- **Kết quả:** Chung chung, vài gạch đầu dòng ("doanh thu tăng, có khó khăn"). Chưa dùng được mang đi họp!

### Lượt 2: Ép liệt kê theo từng phần
```text
Chưa đủ. Liệt kê lại theo từng phần của báo cáo, mỗi phần vài ý chính.
```
- **Kết quả:** Bóc theo 9 phần La Mã từ I đến IX. Đầy đủ hơn nhưng còn dài và chưa nổi bật số liệu.
- $\rightarrow$ *Sau này trở thành mục:* **`Ý CHÍNH CHI TIẾT`** trong Skill.

[Ghi chú Giảng viên]: Ghi lên bảng: "Lượt 2 -> sau này thành mục Ý CHÍNH CHI TIẾT". Giải thích cho học viên vì sao phải hỏi lượt thứ 2.

---

## Slide 10: Demo GV Lượt 3: Bóc Số Liệu & Phát Hiện Hạn Chót Ẩn

### Lượt 3: Bóc sạch số liệu và hạn chót
```text
Bóc ra mọi con số, mốc thời gian, cam kết quan trọng trong tài liệu.
```

### Kết quả AI bóc tách được:
- **Số liệu tài chính:** Doanh thu năm, Lợi nhuận trước thuế (1.885 triệu), Sau thuế (1.508 triệu), Công nợ (1.240 triệu - quá hạn 275 triệu).
- **Mốc thời gian rải rác:** 20/01/2027, 31/01/2027, 15/02/2027, 31/03/2027...
- **Điểm "đáng tiền":** Bắt được mốc **`28/02/2027`** chôn sâu ở Phụ lục 2 trang 13 (thân bài không hề nhắc tới!).
- $\rightarrow$ *Sau này trở thành mục:* **`SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT`** trong Skill.

[Ghi chú Giảng viên]: Soi kỹ mốc 28/02/2027. Nhấn mạnh: Ngay cả AI cũng phải được dặn kỹ mới moi ra chỗ chôn sâu. Lát nữa mình dặn nó 1 lần trong Skill rồi thôi.

---

## Slide 11: Demo GV Lượt 4: Soi Lỗi Vênh Số 95 Triệu (Khoảnh Khắc WOW)

### Lượt 4: Soi mâu thuẫn, điều khoản bất lợi, chỗ mập mờ
```text
Trong báo cáo này có điều khoản nào bất lợi, chỗ nào mâu thuẫn, hoặc chỗ nào mập mờ không?
```

### 3 Phát hiện gây "chấn động" trong báo cáo 14 trang:
1. **Mâu thuẫn số liệu 95 TRIỆU:** Mục II.1 ghi tổng doanh thu **12.450 triệu**, nhưng các bảng cộng lại và Phụ lục 1 đều ra **12.545 triệu**! Lệch đúng 95 triệu!
2. **Bẫy hợp đồng tự động gia hạn:** Hợp đồng Đại Tín (1.845 triệu) sẽ tự động gia hạn thêm 12 tháng nếu Công ty không gửi văn bản từ chối trước **28/02/2027**!
3. **Rủi ro tập trung:** 3 khách hàng lớn chiếm 42,3% doanh thu; nợ quá hạn chiếm 22,2%.
- $\rightarrow$ *Sau này trở thành mục:* **`ĐIỂM CẦN LƯU Ý / RỦI RO`** trong Skill.

[Ghi chú Giảng viên]: DỪNG LẠI Ở ĐÂY. Nhấn mạnh: "Cả lớp nhìn con số vênh 95 triệu. Đọc tay 14 trang có ai phát hiện được không? Đây mới là chỗ AI đỡ việc thật sự!"

---

## Slide 12: Demo GV Lượt 5: Chặn Suy Đoán & Chốt Tóm Tắt Nhanh

### Lượt 5: Chặn suy đoán và rút gọn gửi sếp
```text
Trong những gì bạn vừa trả lời, có chỗ nào bạn tự suy đoán mà tài liệu không nói không? Từ giờ chỉ dùng thông tin có trong tài liệu, chỗ nào tài liệu không nói thì ghi "Tài liệu không đề cập", không được đoán. Rút lại giúp tôi 3 tới 5 gạch đầu dòng quan trọng nhất để tôi gửi sếp.
```

### Kết quả mong đợi:
- AI tự rà soát và thừa nhận chỗ nào là suy luận chủ quan của nó.
- Cô đọng 3 – 5 gạch đầu dòng chiến lược nhất gửi sếp.
- Thiết lập quy tắc "Tài liệu không đề cập" đối với ngân sách marketing 2027.
- $\rightarrow$ *Sau này trở thành mục:* **`QUY TẮC`** và **`TÓM TẮT NHANH`**.

[Ghi chú Giảng viên]: Ghi lên bảng: "Lượt 5 -> mục QUY TẮC + TÓM TẮT NHANH". Nhắc lại: Báo cáo có 5 lượt hỏi, tuần sau làm lại mất tiếp 5 lượt nữa nếu không đóng gói.

---

## Slide 13: Đóng Gói 5 Lượt Chat Thành File `SKILL.md`

### Lệnh đóng gói toàn bộ quy trình:
```text
Tôi thấy kết quả ổn rồi, giờ hãy đóng gói lại thành skill tóm tắt tài liệu cho tôi, để sau này tôi không phải chat nhiều nữa mà bạn vẫn đưa ra kết quả tốt. Sau này tôi muốn khi bảo bạn "Tóm tắt tài liệu abc" thì bạn sẽ tự động kích hoạt skill này cho tôi.

Khi tôi đưa vào một tài liệu nào đó, làm theo các bước:
1. Đọc toàn bộ tài liệu.
2. Xuất ra đúng cấu trúc sau:
- TÓM TẮT NHANH (3 tới 5 gạch đầu dòng ý chính nhất)
- Ý CHÍNH CHI TIẾT (Liệt kê theo từng mục/phần của tài liệu)
- SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT (Bóc ra mọi con số, mốc thời gian, cam kết quan trọng)
- ĐIỂM CẦN LƯU Ý / RỦI RO (Nếu có điều khoản bất lợi, mâu thuẫn, hoặc chỗ mập mờ)
- QUY TẮC: Chỉ dùng thông tin có trong tài liệu. Không có thì ghi "Tài liệu không đề cập", KHÔNG suy đoán. Trích nguyên văn khi cần bằng chứng, đặt trong ngoặc kép. Trả lời bằng tiếng Việt, rõ ràng.
```

[Ghi chú Giảng viên]: Chiếu file `.claude/skills/tom-tat-tai-lieu/SKILL.md` vừa được tạo. Chỉ từng mục đối chiếu với 5 dòng đã ghi trên bảng từ đầu buổi.

---

## Slide 14: Chuẩn Bố Cục 5 Mục Của Skill `tom-tat-tai-lieu`

### Bộ khung tóm tắt tài liệu tiêu chuẩn doanh nghiệp:

1. **TÓM TẮT NHANH:** 3 – 5 gạch đầu dòng cốt lõi nhất, đọc trong 30 giây là nắm toàn cảnh.
2. **Ý CHÍNH CHI TIẾT:** Cấu trúc theo từng phần/mục của văn bản gốc, không bỏ sót nội dung.
3. **SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT:** Toàn bộ con số tài chính, tỷ lệ %, deadline, cam kết thời gian.
4. **ĐIỂM CẦN LƯU Ý / RỦI RO:** Chỗ vênh số liệu, điều khoản phạt, gia hạn tự động, rủi ro công nợ, điểm mập mờ.
5. **QUY TẮC CHỐNG BỊA:** "Tài liệu không đề cập" khi thiếu tin; trích nguyên văn bằng chứng trong ngoặc kép.

[Ghi chú Giảng viên]: Nhấn mạnh: Cấu trúc 5 mục này có thể áp dụng cho mọi loại văn bản: hợp đồng kinh tế, báo cáo tài chính, tờ trình dự án, biên bản họp.

---

## Slide 15: Kiểm Chứng Sức Mạnh: 5 Lượt Chat vs 1 Câu Lệnh Duy Nhất

### Thử nghiệm trên tài liệu hoàn toàn mới: Hợp đồng dịch vụ mẫu
```text
Tóm tắt hợp đồng trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md
```

### Điều kỳ diệu xảy ra:
- Bạn chỉ gõ đúng **1 CÂU DUY NHẤT**, không nhắc gì tới từ "skill"!
- Claude tự động báo: `Using skill tom-tat-tai-lieu...` nhờ dòng `description`.
- Trả về ngay lập tức bản tóm tắt chuẩn chỉnh đủ **5 MỤC**.
- **So sánh:** Báo cáo 14 trang mất **5 lượt chat** $\rightarrow$ Hợp đồng mới chỉ mất **1 câu lệnh**!

[Ghi chú Giảng viên]: Đây là khoảnh khắc chốt hạ giá trị của buổi học. Cho học viên thấy sự khác biệt giữa làm tay và tự động hóa bằng Skill.

---

## Slide 16: Thử Thách Bẫy Chống Bịa Trên Hợp Đồng Mẫu

### Thử hỏi một câu mà văn bản KHÔNG HỀ NÓI TỚI:
```text
Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
```

### Phản xạ chuẩn của AI có kỷ luật:
> *"Hợp đồng có điều khoản bảo mật thông tin (Điều 6) nhưng **KHÔNG quy định mức phạt bằng tiền** cho hành vi tiết lộ bí mật. **Tài liệu không đề cập** con số này."*

- **Thành công:** AI không hề bịa ra con số 50 triệu hay 100 triệu!
- **Nguyên nhân:** Mục `QUY TẮC` trong `SKILL.md` đã thiết lập rào chắn bảo vệ dữ liệu.

[Ghi chú Giảng viên]: Nhấn mạnh: Nếu dùng chatbot thông thường không có skill, AI rất dễ đoán mò mức phạt theo thông lệ thị trường $\rightarrow$ gây hiểu lầm nghiêm trọng.

---

## Slide 17: Thực Hành 1: Tự Tạo Skill & Chạy Hợp Đồng Demo (25 Phút)

### Đề bài thực hành tại lớp (25 Phút):
1. **Bước 1:** Dùng prompt mẫu để tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md` trong dự án của bạn.
2. **Bước 2:** Chạy lệnh tóm tắt file `hop-dong-dich-vu-mau.md` (không nhắc tên skill, xem Claude có tự nạp không).
3. **Bước 3:** Đối chiếu kết quả bóc tách với bảng đáp án chuẩn.

```text
Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md theo đúng quy chuẩn đã học.
```

```text
Tóm tắt hợp đồng trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md
```

[Ghi chú Giảng viên]: Bật đồng hồ đếm ngược 25 phút. Giảng viên và trợ giảng đi hỗ trợ từng học viên kiểm tra xem skill đã tạo đúng thư mục chưa.

---

## Slide 18: Bảng Đối Chiếu Số Liệu Bóc Tách Hợp Đồng Chuẩn

### Bảng đáp án để học viên tự chấm điểm kết quả:

| Hạng mục cần bóc tách | Giá trị chuẩn xác trong hợp đồng | Đạt / Chưa đạt |
|---|---|:---:|
| **Tổng giá trị hợp đồng** | **120.000.000 đồng** (đã bao gồm thuế VAT) | [ ] |
| **Tiến độ thanh toán** | Chia **2 đợt 50/50** (Đợt 1: 60 tr sau 5 ngày; Đợt 2: 60 tr sau nghiệm thu) | [ ] |
| **Quy mô bản quyền & Đào tạo** | Tối đa **20 người dùng**; Tổ chức **2 buổi đào tạo** | [ ] |
| **Thời hạn & Gia hạn** | **12 tháng**; Tự động gia hạn nếu không từ chối trước **30 ngày** | [ ] |
| **Chế tài phạt chậm trả** | **0,05% / ngày** trên số tiền chậm thanh toán | [ ] |
| **Thời hạn bảo mật** | Còn hiệu lực **2 năm** sau khi hợp đồng chấm dứt | [ ] |
| **Điều kiện chấm dứt** | Báo trước **30 ngày**; Nếu Bên B trễ quá **20 ngày** $\rightarrow$ Bên A được hủy & hoàn tiền | [ ] |

[Ghi chú Giảng viên]: Chiếu bảng này lên màn hình lớn để học viên tự rà soát bản tóm tắt của mình.

---

## Slide 19: Thực Hành 2: Áp Dụng Skill Vào Tài Liệu Công Việc Thật

### Đưa tài liệu thật của bạn vào thực chiến:
1. Lấy 1 tài liệu dài trong công việc hàng ngày (Hợp đồng, Biên bản họp, Báo cáo, Đề xuất dự án).
2. Copy file vào thư mục dự án của bạn (hoặc cung cấp đường dẫn file).
3. Ra lệnh tóm tắt bằng câu lệnh tự nhiên:
   ```text
   Tóm tắt tài liệu trong [đường-dẫn-tới-file-của-bạn]
   ```
4. Kiểm tra xem bản tóm tắt có đủ 5 mục không, các số liệu và hạn chót có chính xác không.

### Mở rộng cho học viên:
- Bạn có thể sửa nội dung `SKILL.md` để thêm các mục riêng theo ngành nghề (Ví dụ: Kế toán cần thêm mục *Tài khoản ngân hàng*, Pháp chế cần thêm *Cơ quan tài phán*).

[Ghi chú Giảng viên]: Khuyến khích học viên thử nghiệm trên tài liệu thật của chính họ. Đây là lúc học viên cảm nhận rõ nhất giá trị của khóa học.

---

## Slide 20: [Nâng Cao] Thực Hành 3: Quy Trình Tạo Tài Liệu Chuẩn Brand CES

### Đóng gói quy trình tạo tài liệu Word có thương hiệu:
- **Lượt 1 (Tra cứu):**
  ```text
  Tìm hiểu và gửi tôi báo cáo về xu hướng phát triển AI trong năm 2026. Trả kết quả ra file md
  ```
- **Lượt 2 (Dựng Word chuẩn nhận diện thương hiệu):**
  ```text
  Tổng hợp nội dung báo cáo vừa rồi thành 1 file docx. Dùng bộ nhận diện CES Global: chèn logo 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/logo-ces.png vào header mỗi trang; tone màu theo 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/bo-nhan-dien-ces.md (tiêu đề navy 1B3285, điểm nhấn teal 009898 và vàng C47F0A, cảnh báo đỏ C0392B). Chữ tiếng Việt phải đủ dấu, không lỗi phông: dùng phông Unicode (Arial hoặc Times New Roman) và lưu chuỗi UTF-8.
  ```
- **Lượt 3 (Đóng gói Skill):**
  ```text
  Tôi thấy file này đẹp rồi, bây giờ hãy tạo cho tôi skill đóng gói tài liệu đẹp và đúng tone màu như trên, sau này khi tôi nói tạo tài liệu theo chuẩn CES Global thì hãy áp dụng skill này cho tôi. Đóng gói thành skill và lưu vào folder skill tại workspace hiện tại nhé.
  ```

[Ghi chú Giảng viên]: Phần nâng cao dành cho lớp hoàn thành sớm hoặc giảng viên demo nhanh. Minh họa rằng Skill đóng gói được BẤT KỲ quy trình nào chứ không riêng tóm tắt.

---

## Slide 21: Bảng Tra Nhanh Prompt & Xử Lý Sự Cố (Troubleshooting)

### Prompt tra nhanh cốt lõi:
- Tạo skill: `Tạo cho tôi file .claude/skills/tom-tat-tai-lieu/SKILL.md...`
- Tóm tắt tự nạp: `Tóm tắt hợp đồng trong [đường-dẫn-file]`
- Gọi đích danh: `Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file]`
- Thử chống bịa: `Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật là bao nhiêu tiền?`

### Xử lý các tình huống thường gặp:
- **Claude không tự nạp skill:** Sửa dòng `description` cho rõ hơn, hoặc tạm thời gọi đích danh tên skill.
- **AI vẫn tự đoán số liệu:** Kiểm tra lại mục `QUY TẮC` trong file `SKILL.md` xem có đủ yêu cầu "Tài liệu không đề cập" chưa.
- **Tạo sai thư mục:** Yêu cầu Claude di chuyển file vào đúng `.claude/skills/<ten-skill>/SKILL.md`.
- **Tên thư mục có dấu cách/chữ hoa:** Đổi lại thành chữ thường gạch ngang `tom-tat-tai-lieu`.

[Ghi chú Giảng viên]: Chiếu bảng tra nhanh để học viên chụp lại màn hình làm tài liệu tham khảo khi về nhà.

---

## Slide 22: Tổng Kết Buổi 02 & Teaser Buổi 03

### 3 Chân lý cốt lõi cần nhớ hôm nay:
1. **Skill = 1 thư mục + 1 file `SKILL.md`:** Đơn giản, gọn nhẹ, không cần cài đặt phức tạp.
2. **Dòng `description` là linh hồn:** Quyết định AI có tự động nạp đúng việc cần làm hay không.
3. **Kỷ luật chống bịa số:** Không có trong văn bản thì kiên quyết nói "không có", tuyệt đối không suy đoán!

### Bài tập về nhà:
- Tạo thêm **1 Skill riêng** cho công việc lặp lại hàng ngày của bạn (Soạn email báo giá, lập kế hoạch tuần, duyệt checklist nghiệm thu).
- Chạy thử 1 lần, chụp màn hình kết quả gửi vào nhóm Zalo lớp.

### Chuẩn bị cho Buổi 03: Agent Phân Tích Dữ Liệu & Routine Tự Động
> *"Buổi sau mình học MCP: Cách cắm thêm giác quan cho AI để đọc dữ liệu Excel, Google Drive, Gmail và thiết lập Routine tự động chạy định kỳ. Nhớ mang theo 1 file Excel/CSV số liệu công việc của bạn!"*

[Ghi chú Giảng viên]: Khen ngợi học viên đã hoàn thành buổi học xuất sắc. Nhắc nhở nộp bài tập và hẹn gặp lại ở Buổi 03 lúc 20:00 tối Thứ Ba / Thứ Sáu tới!
