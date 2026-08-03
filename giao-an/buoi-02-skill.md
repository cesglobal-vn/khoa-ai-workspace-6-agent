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
- [ ] File demo cần dùng:
  - `tai-lieu-phat/demo/buoi-02/bao-cao-tong-ket-nam-2026.docx` (14 trang, dùng cho phần demo GV)
  - `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md` (dùng cho thực hành học viên)
- [ ] Mở sẵn bản `.docx` bằng Word và **chiếu số trang lên cho lớp nhìn thấy độ dày thật** trước khi chạy prompt đầu tiên. Hiệu ứng "14 trang này ai đọc hết trong 10 phút" là điểm mở màn của buổi
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/skill-tom-tat-tai-lieu.md` (KHÔNG chiếu cho lớp ở phần demo, chỉ dùng để đối chiếu cuối buổi hoặc cấp cho học viên bị tụt lại)
- [ ] Chuẩn bị 1 tài liệu dài của riêng GV để làm ví dụ thực hành 2 (biên bản họp hoặc báo cáo)
- [ ] **Chạy thử trọn chuỗi 5 lượt chat + prompt đóng gói ít nhất 1 lần trước giờ lên lớp.** Đây là buổi mà GV phải quen tay, vì kết quả từng lượt phụ thuộc câu hỏi trước đó
- [ ] Ghi sẵn ra giấy 3 con số để đối chiếu nhanh khi agent trả kết quả: tổng doanh thu **12.545** (bảng và phụ lục) so với **12.450** (mục II.1), và mốc **28/02/2027** nằm ở Phụ lục 2 trang 13

## Mục tiêu buổi (học xong học viên làm được gì)
1. Nói được skill là gì và khác gì với việc gõ lại chỉ dẫn mỗi lần.
2. **Hiểu skill sinh ra từ đâu:** làm tay vài lượt, thấy mình lặp lại chỉ dẫn nào thì gói chỉ dẫn đó lại. Không phải chép một file mẫu có sẵn.
3. Biết skill là 1 thư mục chứa file SKILL.md, đặt đúng chỗ trong dự án.
4. Tự tay tạo skill "tom-tat-tai-lieu" trong dự án của mình.
5. Dùng skill để tóm tắt hợp đồng: bóc ra số tiền, ngày tháng, hạn chót, điều khoản bất lợi.
6. Hiểu quy tắc chống bịa: thông tin không có trong tài liệu thì ghi "không đề cập", không suy đoán.

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

> **Ghi chú phân bổ thời gian:** khối demo được kéo dài lên 38 phút vì phải diễn trọn
> 5 lượt chat rồi mới đóng gói. Phần lý thuyết rút ngắn tương ứng, vì chính khối demo
> đã dạy khái niệm skill bằng trải nghiệm rồi. Tổng vẫn đúng 150 phút.

### [00:00-00:12] Mở đầu & recap buổi 1
- **Lời dẫn GV:** "Chào cả lớp. Buổi trước mình đã cài Claude Code, tạo thư mục dự án và viết file CLAUDE.md để agent nhớ bối cảnh công việc của mình. Hôm nay mình lên một nấc: dạy agent một quy trình để nó làm chuẩn mỗi lần, không phải nhắc lại. Cái đó gọi là skill."
- Recap buổi 1 (hỏi nhanh cả lớp, 3 câu):
  - Claude Code khác chat thường ở điểm nào? (tự làm nhiều bước, đọc/sửa file thật, nhớ bối cảnh)
  - File CLAUDE.md dùng để làm gì? (ghi bối cảnh dự án để agent tự đọc mỗi lần)
  - Thư mục dự án của bạn đang ở đâu trên máy? (kiểm tra cả lớp còn mở được)
- Nêu mục tiêu buổi hôm nay: tạo được 1 skill và dùng nó tóm tắt một hợp đồng.
- **Lời dẫn GV chốt mở đầu:** "Cuối buổi, mỗi người có một skill riêng chạy được, và một bản tóm tắt hợp đồng do chính skill của mình làm ra."

### [00:12-00:27] Lý thuyết ngắn: Skill là gì
> Giữ ngắn, nói vừa đủ để lớp có cái khung. Phần "vì sao cần skill" sẽ tự sáng ra ở
> khối demo ngay sau đây, đừng giảng kỹ ở đây kẻo trùng và cháy giờ.

- **Lời dẫn GV:** "Hình dung skill giống một tờ quy trình dán trên tường. Ai vào làm việc đó cũng theo đúng tờ quy trình, ra kết quả giống nhau. Skill là tờ quy trình đó, nhưng cho AI. Lát nữa tôi sẽ không đưa sẵn tờ quy trình cho cả lớp chép. Tôi sẽ làm việc bằng tay trước, rồi cả lớp xem tờ quy trình đó tự hình thành thế nào."
- Nội dung trình bày (giữ đơn giản, có thể vẽ lên bảng):
  1. **Vì sao cần skill.** Việc lặp lại mà mỗi lần gõ lại chỉ dẫn thì mất công và dễ quên bước. Skill viết một lần, dùng mãi, luôn đủ bước.
  2. **Skill nằm ở đâu.** Là một thư mục trong dự án: `.claude/skills/<ten-skill>/`. Trong đó có một file `SKILL.md`. Tên thư mục chính là tên skill.
  3. **Bên trong SKILL.md có gì.** Phần đầu ghi `name` (tên) và `description` (mô tả dùng khi nào). Phần thân là các bước chỉ dẫn cho AI làm.
  4. **Claude tự nạp nhờ dòng description.** Đây là điểm mấu chốt. Dòng mô tả viết càng rõ "dùng khi nào" thì Claude càng biết lúc nào lôi skill ra dùng. Nếu mô tả mờ, Claude không tự nạp, khi đó phải gọi thẳng tên skill.
- **Câu hỏi tương tác:** "Trong công việc của bạn, có việc nào tuần nào cũng làm, bước nào cũng giống nhau không? Kể một cái." (gọi 2-3 học viên, ghi lên bảng để cuối buổi họ tự làm skill cho việc đó)

### [00:27-01:05] Demo giảng viên: từ chat nhiều lượt tới một skill
> GV làm mẫu trên màn hình chia sẻ. Học viên xem, chưa gõ theo.
>
> **Ý đồ của khối này (GV đọc kỹ trước khi lên lớp):** KHÔNG đưa sẵn nội dung SKILL.md
> cho lớp chép. Để lớp NHÌN THẤY GV phải hỏi đi hỏi lại 5 lượt mới ra bản tóm tắt dùng
> được, rồi mới đóng gói chỗ đó lại thành skill. Mỗi lượt chat sẽ biến thành đúng một
> mục trong SKILL.md. Học viên hiểu vì sao có từng mục, thay vì chép một file mẫu rơi
> từ trên trời xuống. Đây là điểm khác biệt lớn nhất của buổi này, đừng rút gọn.

**Bước 1 (Lượt 1): Tóm tắt kiểu thông thường để lớp thấy nó chưa đủ**
- **Lời dẫn GV:** "Tôi có một báo cáo tổng kết năm dài 14 trang. Cả lớp nhìn số trang ở góc màn hình. Trong 10 phút trước giờ họp, không ai đọc hết được cái này. Giờ tôi nhờ AI tóm tắt theo cách bình thường nhất, tức là nghĩ gì gõ nấy."
- **Prompt gõ vào Claude Code:**
  ```
  Tóm tắt giúp tôi báo cáo trong tai-lieu-phat/demo/buoi-02/bao-cao-tong-ket-nam-2026.docx
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/bao-cao-tong-ket-nam-2026.docx`
- **Kết quả mong đợi:** Claude trả về một bản tóm tắt chung chung, thường vài đoạn hoặc dăm gạch đầu dòng: doanh thu tăng, Gói Cao cấp bán tốt, có khó khăn về nhân sự và công nợ. Đọc thì xuôi tai. Nhưng nó KHÔNG bóc đủ số liệu, KHÔNG gom hạn chót, và gần như chắc chắn KHÔNG phát hiện con số bị lệch trong báo cáo.
- **Lời dẫn GV chốt bước:** "Nghe thì ổn đúng không? Nhưng nếu tôi mang đúng bản này đi họp, sếp hỏi tổng doanh thu bao nhiêu, hạn nào sắp tới, tôi vẫn phải mở lại 14 trang. Nó chưa dùng được. Nên tôi hỏi tiếp."

**Bước 2 (Lượt 2): Ép liệt kê theo từng phần**
- **Lời dẫn GV:** "Vấn đề thứ nhất là nó gộp hết vào một cục. Tôi muốn theo đúng bố cục báo cáo."
- **Prompt gõ vào Claude Code:**
  ```
  Chưa đủ. Liệt kê lại theo từng phần của báo cáo, mỗi phần vài ý chính.
  ```
- **File demo:** dùng tiếp tài liệu ở Bước 1 (không cần nạp lại)
- **Kết quả mong đợi:** Claude liệt kê theo 9 phần La Mã của báo cáo (từ I. Đặc điểm tình hình tới IX. Kiến nghị, đề xuất), mỗi phần vài gạch đầu dòng. Giờ đã đầy đủ nhưng còn dài và chưa nổi số.
- **Ghi chú GV:** viết lên bảng: "Lượt 2 -> sau này thành mục **Ý CHÍNH CHI TIẾT**".

**Bước 3 (Lượt 3): Bóc số liệu và hạn chót**
- **Lời dẫn GV:** "Thứ hai, cái sếp hỏi luôn là con số và deadline. Tôi bắt nó bóc riêng ra."
- **Prompt gõ vào Claude Code:**
  ```
  Bóc ra mọi con số, mốc thời gian, cam kết quan trọng trong tài liệu.
  ```
- **File demo:** dùng tiếp tài liệu ở Bước 1
- **Kết quả mong đợi:** Claude liệt kê được các con số chính (doanh thu năm, lợi nhuận trước thuế 1.885 triệu, lợi nhuận sau thuế 1.508 triệu, công nợ phải thu 1.240 triệu trong đó quá hạn 275 triệu, chi phí marketing 485 triệu, nhân sự từ 34 lên 41 người) và các mốc thời gian nằm rải trong bài: 20/01/2027, 31/01/2027, 15/02/2027, 31/3/2027, quý II/2027, 30/6/2027.
- **Lời dẫn GV (điểm cần soi):** kiểm xem agent có nhặt được mốc **28/02/2027** hay không. Mốc này nằm sâu ở Phụ lục 2 trang 13, thân báo cáo không hề nhắc. Nếu agent bỏ sót, đây là dịp tốt để nói: "Ngay cả AI cũng phải được dặn kỹ mới moi ra chỗ chôn sâu. Lát nữa mình sẽ dặn nó một lần rồi thôi." Nếu agent nhặt được, nhấn mạnh: "Cả lớp đọc 14 trang trong 10 phút có ai thấy dòng này không?"
- **Ghi chú GV:** viết lên bảng: "Lượt 3 -> mục **SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT**".

**Bước 4 (Lượt 4): Hỏi chỗ bất lợi, mâu thuẫn, mập mờ (lượt quan trọng nhất)**
- **Lời dẫn GV:** "Thứ ba, và đây là thứ đáng tiền nhất. Tôi không chỉ muốn biết báo cáo nói gì, tôi muốn biết chỗ nào có vấn đề."
- **Prompt gõ vào Claude Code:**
  ```
  Trong báo cáo này có điều khoản nào bất lợi, chỗ nào mâu thuẫn, hoặc chỗ nào mập mờ không?
  ```
- **File demo:** dùng tiếp tài liệu ở Bước 1
- **Kết quả mong đợi:** đây là lượt agent phải bắt được các điểm sau:
  - **Mâu thuẫn số liệu:** mục II.1 ghi tổng doanh thu **12.450 triệu**, nhưng bảng theo quý, bảng theo sản phẩm, bảng theo khu vực và Phụ lục 1 đều cộng ra **12.545 triệu**. Lệch **95 triệu**. Thêm một dấu hiệu nữa: tỷ lệ "tăng 14,2%" ghi trong bài lại đúng với 12.545 chứ không đúng với 12.450.
  - **Điều khoản bất lợi:** hợp đồng Đại Tín (1.845 triệu, Phụ lục 2) **tự động gia hạn thêm 12 tháng** nếu Công ty không gửi văn bản từ chối trước **28/02/2027**.
  - **Rủi ro:** ba khách hàng lớn nhất chiếm **42,3%** doanh thu; nợ quá hạn **275 triệu** chiếm 22,2% công nợ phải thu; tăng trưởng chậm dần từ 9,8% quý II xuống 1,1% quý IV.
  - **Chỗ mập mờ:** ngân sách marketing 2027 được nhắc tới nhưng không nêu con số; mức thưởng vượt chỉ tiêu chỉ ghi "theo Quy chế thưởng hiện hành".
- **Lời dẫn GV chốt bước (đây là khoảnh khắc phải dừng lại):** "Cả lớp để ý con số này. Báo cáo tự nói vênh nhau 95 triệu. Tôi đọc tay 14 trang, thú thật là tôi không bắt được. Đây mới là chỗ AI đỡ việc thật sự, chứ không phải chỗ nó viết văn hay."
- **Ghi chú GV:** viết lên bảng: "Lượt 4 -> mục **ĐIỂM CẦN LƯU Ý / RỦI RO**".

**Bước 5 (Lượt 5): Chặn suy đoán và rút gọn**
- **Lời dẫn GV:** "Còn một chuyện phải xử lý. AI hay có tật thấy thiếu thì tự điền vào cho trơn. Với báo cáo và hợp đồng thì đó là tai họa. Tôi hỏi thẳng nó."
- **Prompt gõ vào Claude Code:**
  ```
  Trong những gì bạn vừa trả lời, có chỗ nào bạn tự suy đoán mà tài liệu không nói không? Từ giờ chỉ dùng thông tin có trong tài liệu, chỗ nào tài liệu không nói thì ghi "Tài liệu không đề cập", không được đoán. Rút lại giúp tôi 3 tới 5 gạch đầu dòng quan trọng nhất để tôi gửi sếp.
  ```
- **File demo:** dùng tiếp tài liệu ở Bước 1
- **Kết quả mong đợi:** Claude tự rà lại, chỉ ra chỗ nào là suy luận của nó chứ không phải tài liệu nói (ví dụ nhận định về nguyên nhân tăng trưởng chậm), và trả về 3 tới 5 gạch đầu dòng cô đọng. Nếu GV hỏi thêm "ngân sách marketing 2027 là bao nhiêu", agent phải trả lời tài liệu không đề cập, không được bịa ra con số.
- **Ghi chú GV:** viết lên bảng: "Lượt 5 -> mục **QUY TẮC** + mục **TÓM TẮT NHANH**".

**Bước 6: Đóng gói 5 lượt chat vừa rồi thành một skill**
- **Lời dẫn GV (dẫn vào bằng nỗi đau, đọc chậm):** "Xong. Giờ tôi có bản tóm tắt dùng được. Nhưng nhìn lại xem tôi vừa mất mấy lượt: năm lượt. Tuần sau có báo cáo khác, tôi lại mất năm lượt nữa, và chắc gì đã hỏi đúng thứ tự như hôm nay. Cả phòng tôi năm người, mỗi người hỏi một kiểu, ra năm bản khác nhau. Đó chính là lý do phải đóng gói. Tôi bảo nó gói toàn bộ cách làm này lại thành một skill."
- **Chỉ lên bảng trước khi gõ:** 5 dòng vừa ghi (Lượt 2 tới Lượt 5) chính là 5 mục sắp xuất hiện trong SKILL.md. Nhấn: "Tôi không bịa ra cấu trúc này. Nó là đúng những gì tôi vừa phải hỏi."
- **Prompt gõ vào Claude Code:**
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
- **File demo:** không cần file demo cho bước này (đang tạo file cấu hình). GV giữ `mau-cau-hinh/skill-tom-tat-tai-lieu.md` bên cạnh để đối chiếu, nhưng KHÔNG chiếu lên trước khi lớp thấy skill tự sinh ra.
- **Kết quả mong đợi:** Claude báo đã tạo file `.claude/skills/tom-tat-tai-lieu/SKILL.md`. GV mở file cho lớp xem và chỉ từng mục, đối chiếu với 5 dòng đã ghi trên bảng: mục TÓM TẮT NHANH ứng với Lượt 5, Ý CHÍNH CHI TIẾT ứng với Lượt 2, SỐ LIỆU NGÀY THÁNG HẠN CHÓT ứng với Lượt 3, ĐIỂM CẦN LƯU Ý ứng với Lượt 4, QUY TẮC ứng với Lượt 5.
- **Lời dẫn GV chốt bước:** "Nhìn kỹ file này. Nó không phải mẫu tôi tải ở đâu về. Nó là biên bản của 5 lượt tôi vừa phải hỏi, được ghi lại một lần để khỏi phải hỏi nữa. Skill của các anh chị sau này cũng sinh ra đúng kiểu đó: cứ làm tay vài lần, thấy mình lặp lại chỉ dẫn nào thì gói chỉ dẫn đó lại."

**Bước 7: Chạy skill trên một tài liệu KHÁC để chứng minh nó tái dùng được**
- **Lời dẫn GV:** "Thử xem nó có thật sự dùng lại được không. Tôi đưa vào một hợp đồng, tức là loại tài liệu hoàn toàn khác báo cáo lúc nãy. Và để ý: tôi chỉ gõ đúng một câu, không nhắc gì tới skill. Nhờ dòng description, Claude tự nhận ra đây là việc tóm tắt tài liệu và tự nạp skill vừa tạo."
- **Prompt gõ vào Claude Code:**
  ```
  Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- **Kết quả mong đợi:** Claude trả về bản tóm tắt đúng 5 mục của skill. Nội dung bóc ra phải khớp hợp đồng thật:
  - **Số liệu:** tổng giá trị **120.000.000 đồng** (đã gồm thuế), chia **2 đợt 50/50** (đợt 1 60 triệu trong 5 ngày sau ký, đợt 2 60 triệu sau nghiệm thu); bản quyền tối đa **20 người dùng**; đào tạo **2 buổi**.
  - **Ngày tháng, hạn chót:** ký ngày **10/6/2026**; cài đặt xong trong **15 ngày**; đào tạo trong **30 ngày**; thời hạn **12 tháng, tự động gia hạn** nếu không có ý kiến trước khi hết hạn 30 ngày.
  - **Điểm lưu ý / rủi ro:** **phạt chậm thanh toán 0,05%/ngày**; điều khoản **bảo mật còn hiệu lực 2 năm** sau khi chấm dứt; chấm dứt phải **báo trước 30 ngày**; nếu Bên B giao trễ quá 20 ngày, Bên A được chấm dứt và hoàn tiền phần chưa thực hiện.
- **Lời dẫn GV chốt demo (so sánh 5 lượt với 1 lượt):** "Để ý dòng đầu Claude thường báo nó đang dùng skill tom-tat-tai-lieu. Đó là bằng chứng skill tự nạp. Và quan trọng hơn: với báo cáo lúc nãy tôi mất 5 lượt mới ra đủ 5 mục. Với hợp đồng này tôi gõ 1 câu, ra ngay đủ 5 mục. Đó là toàn bộ giá trị của skill."

**Bước 8: Thử quy tắc chống bịa (điểm nhấn của buổi)**
- **Lời dẫn GV:** "Giờ mình thử một câu hỏi mà hợp đồng KHÔNG hề nói tới, xem skill có bịa không."
- **Prompt gõ vào Claude Code:**
  ```
  Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md`
- **Kết quả mong đợi:** Claude trả lời đại ý "Hợp đồng có điều khoản bảo mật (Điều 6) nhưng KHÔNG nêu mức phạt bằng tiền cho việc tiết lộ. Tài liệu không đề cập con số này." Không được bịa ra một số tiền. GV nhấn: "Đây là lý do có mục QUY TẮC trong skill. Với hợp đồng và số liệu, thà nói không có còn hơn đoán sai."

### [01:05-01:32] Thực hành 1: học viên tự tạo skill và chạy trên hợp đồng demo
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

### [01:32-01:42] Nghỉ giải lao

### [01:42-02:15] Thực hành 2: dùng skill với tài liệu công việc thật của học viên
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

### [Nâng cao] Thực hành 3: Từ nghiên cứu tới tài liệu có thương hiệu, rồi đóng gói thành skill
> **Ghi chú thời lượng (đọc trước khi xếp lịch):** buổi chuẩn 150 phút đã kín tới phần Chốt.
> Thực hành 3 là phần NÂNG CAO, KHÔNG nhồi vào 150 phút. Chọn 1 trong 3 cách: (a) lớp mạnh và
> còn giờ thì GV demo nhanh rồi cho làm tại lớp; (b) GV chỉ demo, học viên làm nốt ở nhà;
> (c) tách thành một buổi phụ. Ưu tiên giữ trọn các phần nền phía trên, đừng để Thực hành 3
> làm cháy giờ.
>
> **Ý đồ:** lặp lại đúng bài học của buổi (làm việc qua chat rồi ĐÓNG GÓI thành skill), nhưng
> nâng một bậc. Ở phần đầu buổi, skill chỉ để tóm tắt. Ở đây, học viên đóng gói cả một quy
> trình tạo tài liệu có thương hiệu công ty, dùng lại cho mọi báo cáo sau này. Chuỗi vẫn là
> 3 lượt chat rồi đóng gói, giống hệt cấu trúc đã dạy, nên học viên thấy skill là công cụ
> gói được BẤT KỲ quy trình nào, không riêng tóm tắt.

**Chuẩn bị thêm cho Thực hành 3:**
- Máy học viên: Claude Code phải chạy được script tạo file Word (môi trường có Python hoặc Node kèm thư viện tạo docx). Nếu máy chưa có, để phần Lượt 2 ở dạng GV demo, học viên xem và làm ở nhà.
- Cần mạng: Lượt 1 tra web thật.
- Logo CES: `tai-lieu-phat/demo/buoi-02/logo-ces.png`
- Bộ nhận diện CES: `tai-lieu-phat/demo/buoi-02/bo-nhan-dien-ces.md` (navy 1B3285, đỏ C0392B, teal 009898, vàng C47F0A).

**Lượt 1: Bảo agent tự đi tìm thông tin và xuất ra file**
- **Lời dẫn GV:** "Bài đầu buổi mình đóng gói việc tóm tắt. Giờ mình đóng gói một việc oách hơn: tạo hẳn một bộ tài liệu có thương hiệu công ty. Bắt đầu bằng việc bảo agent tự đi tra thông tin đã, chứ không phải mình dán sẵn."
- **Prompt gõ vào Claude Code:**
  ```
  Tìm hiểu và gửi tôi báo cáo về xu hướng phát triển AI trong năm 2026. Trả kết quả ra file md
  ```
- **File demo:** không có. Agent tra web và tự tạo file `.md` mới trong thư mục dự án.
- **Kết quả mong đợi:** agent tra web rồi tạo một file `.md` (ví dụ `bao-cao-xu-huong-ai-2026.md`). **Vì tra web thật nên nội dung mỗi lần mỗi khác, GV chấm theo CẤU TRÚC chứ không theo nội dung cố định:** file có tiêu đề, nhiều mục lớn (ví dụ mô hình nền tảng, agent AI, đa phương thức, chi phí suy luận, quy định pháp lý), mỗi mục vài gạch đầu dòng, và có phần nguồn tham khảo. GV nhắc lớp: kiểm lại nguồn, đây đúng là bước "tự đi tìm thông tin" chứ không phải bịa.

**Lượt 2: Đóng nội dung thành tài liệu có thương hiệu (logo + tone màu)**
- **Lời dẫn GV:** "Có nội dung rồi. Mình không muốn một file Word trắng đen nhạt nhẽo. Mình muốn nó ra đúng màu thương hiệu công ty và có logo. Để ý mình dặn kỹ chuyện tiếng Việt đủ dấu, vì tạo Word bằng máy rất hay bị lỗi phông."
- **Prompt gốc (kiểu học viên hay gõ tự nhiên, giữ nguyên để lớp thấy cách nói đời thường vẫn chạy được):**
  ```
  Tôi thấy nội dung khá chi tiết rồi, bây giờ hãy tổng hợp và tạo cho tôi 1 file docx cho nội dung trên. Sử dụng tone màu của logo công ty của tôi, trong file docx phải có logo kèm theo luôn. Lưu ý file docx phải chuẩn tiếng Việt và không bị lỗi dấu. Trong file docx phải kèm theo logo luôn nhé.
  ```
- **Prompt cho lớp (bản chỉ rõ đường dẫn để chạy được ngay, GV chiếu bản này cho học viên copy):**
  ```
  Tổng hợp nội dung báo cáo vừa rồi thành 1 file docx. Dùng bộ nhận diện CES Global: chèn logo tai-lieu-phat/demo/buoi-02/logo-ces.png vào header mỗi trang; tone màu theo tai-lieu-phat/demo/buoi-02/bo-nhan-dien-ces.md (tiêu đề navy 1B3285, điểm nhấn teal 009898 và vàng C47F0A, cảnh báo đỏ C0392B). Chữ tiếng Việt phải đủ dấu, không lỗi phông: dùng phông Unicode (Arial hoặc Times New Roman) và lưu chuỗi UTF-8.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-02/logo-ces.png` và `tai-lieu-phat/demo/buoi-02/bo-nhan-dien-ces.md`; nội dung lấy từ file `.md` ở Lượt 1.
- **Kết quả mong đợi:** agent viết một script tạo file `.docx`, mở ra thấy: logo CES ở header mỗi trang, tiêu đề màu navy, điểm nhấn teal/vàng, và **tiếng Việt đủ dấu, không có ô vuông hay dấu hỏi thay cho chữ có dấu**. GV mở file kiểm 3 thứ: logo có hiện không, màu có đúng thương hiệu không, chữ có lỗi dấu không.
- **Lời dẫn GV (nhấn chuyện lỗi dấu):** "Vì sao mình phải dặn 'không lỗi dấu'? Vì khi tạo Word bằng script, nếu ghi file sai mã hoặc chọn phông không có tiếng Việt thì chữ có dấu ra thành dấu hỏi hoặc ô vuông. Đây là lỗi kinh điển. Dặn trước một câu là tránh được."

**Lượt 3: Đóng gói cả quy trình thành một skill dùng lại**
- **Lời dẫn GV:** "Lại đúng khoảnh khắc quen thuộc của cả buổi hôm nay. Mình vừa làm qua ba lượt: tra tin, dựng tài liệu, chỉnh màu thương hiệu. Tuần sau có nội dung khác mình lại phải làm lại từ đầu. Nên mình đóng gói cả quy trình này thành một skill, y như lúc đầu buổi mình đóng gói việc tóm tắt."
- **Prompt gõ vào Claude Code:**
  ```
  Tôi thấy file này đẹp rồi, bây giờ hãy tạo cho tôi skill đóng gói tài liệu đẹp và đúng tone màu như trên, sau này khi tôi nói tạo tài liệu theo chuẩn CES Global thì hãy áp dụng skill này cho tôi. Đóng gói thành skill và lưu vào folder skill tại workspace hiện tại nhé.
  ```
- **File demo:** dùng lại kết quả Lượt 1 và Lượt 2 (không cần file mới).
- **Kết quả mong đợi:** agent tạo file skill trong `.claude/skills/` của thư mục dự án (ví dụ `.claude/skills/tao-tai-lieu-ces/SKILL.md`), với: dòng `description` ghi rõ "dùng khi cần tạo tài liệu theo chuẩn CES Global"; phần thân ghi lại quy trình (đường dẫn logo, bộ màu navy/teal/vàng/đỏ, phông Unicode đủ dấu, các bước dựng docx). GV kiểm chứng skill tự nạp: gõ một câu mới như "Tạo tài liệu theo chuẩn CES Global cho nội dung ABC" và xem agent có tự dùng skill vừa tạo không.
- **Lời dẫn GV chốt Thực hành 3:** "Nhìn lại cả buổi: hai lần mình đều làm cùng một việc. Làm tay qua vài lượt cho ra kết quả ưng ý, rồi đóng gói chỗ đó thành skill. Lần đầu là skill tóm tắt, lần này là skill tạo tài liệu có thương hiệu. Đó là cách anh chị biến mọi việc lặp lại của mình thành skill."

**Tình huống hay gặp riêng của Thực hành 3:**

| Tình huống | Cách xử lý |
|---|---|
| Lượt 1 agent không tra web được (không có mạng, hoặc tài khoản chưa bật web) | Kiểm mạng và quyền tra web của Claude Code. Nếu lớp không có mạng ổn định, GV chỉ demo Lượt 1 trên máy mình, học viên bắt đầu từ Lượt 2 với nội dung GV chia sẻ. |
| Lượt 2 chữ tiếng Việt ra ô vuông hoặc dấu hỏi | Lỗi phông hoặc mã ký tự. Bảo agent: "Chữ tiếng Việt đang bị lỗi dấu. Dùng phông Arial hoặc Times New Roman và lưu file bằng mã UTF-8, tạo lại giúp tôi." |
| Lượt 2 logo không hiện trong file | Sai đường dẫn logo hoặc agent quên chèn. Nhắc: "Chèn logo tai-lieu-phat/demo/buoi-02/logo-ces.png vào header mỗi trang." Kiểm file logo có nằm đúng chỗ không. |
| Máy học viên không tạo được docx (thiếu thư viện) | Để Lượt 2 ở dạng GV demo. Học viên ghi lại quy trình, làm ở nhà khi máy đủ điều kiện. Không để cả lớp kẹt ở đây. |
| Lượt 3 skill tạo ra nhưng description mờ, lần sau không tự nạp | Sửa description cho rõ cụm "dùng khi nào": "Dùng khi cần tạo tài liệu Word theo chuẩn thương hiệu CES Global (logo, tone màu navy/teal/vàng)." |
| Học viên hỏi vì sao không dùng luôn skill có sẵn của công ty | Giải thích: đây là bài tập để học viên tự tay đóng gói, hiểu skill từ bên trong. Trong thực tế công ty có thể phát skill chuẩn dùng chung. |

### [02:15-02:30] Chốt & giao bài
- **Lời dẫn GV:** "Tóm lại hôm nay: skill là gói chỉ dẫn cho việc lặp lại, để trong `.claude/skills/`, Claude tự nạp nhờ dòng mô tả. Bạn đã có một skill chạy được và hai bản tóm tắt. Skill này còn dùng dài dài về sau."
- Tổng kết 3 ý cần nhớ:
  1. Skill = 1 thư mục + 1 file SKILL.md.
  2. Dòng `description` quyết định Claude có tự nạp đúng lúc không.
  3. Quy tắc chống bịa: không có trong tài liệu thì nói không có.
- **Bài về nhà:** tạo thêm 1 skill cho một việc lặp lại khác trong nghề của mình (soạn email trả lời khách, lập kế hoạch tuần, kiểm tra checklist). Chạy thử 1 lần, chụp kết quả gửi vào nhóm Zalo.
- **Xem trước buổi sau:** "Buổi 3 mình học MCP: cách cắm thêm công cụ và dữ liệu ngoài cho agent, để nó đọc được cả file Excel, web, Google Drive. Nhớ mang theo 1 file Excel hoặc CSV công việc của bạn."

---

## Bảng prompt tổng hợp của buổi (tra nhanh)

**Chuỗi 5 lượt chat trong demo GV (gõ lần lượt, mỗi lượt dựa trên lượt trước):**

| Lượt | Prompt | Sau này thành mục nào trong SKILL.md |
|---|---|---|
| 1 | `Tóm tắt giúp tôi báo cáo trong tai-lieu-phat/demo/buoi-02/bao-cao-tong-ket-nam-2026.docx` | (chưa thành mục nào, đây là lượt để lớp thấy chưa đủ) |
| 2 | `Chưa đủ. Liệt kê lại theo từng phần của báo cáo, mỗi phần vài ý chính.` | Ý CHÍNH CHI TIẾT |
| 3 | `Bóc ra mọi con số, mốc thời gian, cam kết quan trọng trong tài liệu.` | SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT |
| 4 | `Trong báo cáo này có điều khoản nào bất lợi, chỗ nào mâu thuẫn, hoặc chỗ nào mập mờ không?` | ĐIỂM CẦN LƯU Ý / RỦI RO |
| 5 | `Trong những gì bạn vừa trả lời, có chỗ nào bạn tự suy đoán mà tài liệu không nói không? ... Rút lại giúp tôi 3 tới 5 gạch đầu dòng quan trọng nhất` | QUY TẮC + TÓM TẮT NHANH |

**Các prompt còn lại của buổi:**

| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 6 | Prompt đóng gói: `Tôi thấy kết quả ổn rồi, giờ hãy đóng gói lại thành skill tóm tắt tài liệu cho tôi...` (xem Bước 6) | (không) | Tạo được `.claude/skills/tom-tat-tai-lieu/SKILL.md`, 5 mục khớp 5 lượt chat vừa rồi |
| 7 | `Tóm tắt hợp đồng trong tai-lieu-phat/demo/buoi-02/hop-dong-dich-vu-mau.md` | `hop-dong-dich-vu-mau.md` | Chỉ 1 lượt ra đủ 5 mục; bóc đúng 120 triệu, 2 đợt 50/50, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm |
| 8 | `Trong hợp đồng này, mức phạt nếu Bên A tiết lộ bí mật ra ngoài là bao nhiêu tiền?` | `hop-dong-dich-vu-mau.md` | Trả lời "Tài liệu không đề cập", không bịa ra số tiền |
| 9 | `Dùng skill tom-tat-tai-lieu để tóm tắt tài liệu trong [đường-dẫn-file]` | tài liệu HV | Bản tóm tắt 5 mục cho tài liệu thật của học viên |

**Thực hành 3 - nâng cao (chuỗi 3 lượt: nghiên cứu -> tài liệu có brand -> đóng gói skill):**

| Lượt | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| TH3-1 | `Tìm hiểu và gửi tôi báo cáo về xu hướng phát triển AI trong năm 2026. Trả kết quả ra file md` | (agent tra web) | File `.md` có cấu trúc nhiều mục + nguồn; chấm theo cấu trúc vì nội dung web mỗi lần khác |
| TH3-2 | `Tổng hợp nội dung báo cáo vừa rồi thành 1 file docx... logo tai-lieu-phat/demo/buoi-02/logo-ces.png... tone màu bo-nhan-dien-ces.md... tiếng Việt đủ dấu, UTF-8` | `logo-ces.png`, `bo-nhan-dien-ces.md` | File docx có logo header, màu navy/teal/vàng, tiếng Việt đủ dấu, không ô vuông |
| TH3-3 | `Tạo cho tôi skill đóng gói tài liệu đẹp và đúng tone màu như trên... khi tôi nói tạo tài liệu theo chuẩn CES Global thì áp dụng skill này... lưu vào folder skill tại workspace` | (kết quả TH3-1, TH3-2) | Skill `.claude/skills/tao-tai-lieu-ces/` với description "chuẩn CES Global", tự nạp khi gọi |

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

**Riêng cho khối demo 5 lượt chat (Bước 1 tới Bước 6):**

| Tình huống | Cách xử lý |
|---|---|
| Lượt 1 agent đã trả về quá tốt, gần đủ 5 mục luôn, làm mất kịch tính "chưa đủ" | Đừng cố dìm nó. Chuyển hướng lời dẫn: "Lần này nó đoán trúng ý tôi. Nhưng lần sau tài liệu khác, tôi lại phải cầu may. Và đồng nghiệp tôi hỏi kiểu khác thì ra kiểu khác." Vẫn chạy tiếp các lượt 2-5 để lấy đủ 5 mục cho SKILL.md. Nỗi đau chuyển từ "AI làm dở" sang "kết quả không ổn định, không lặp lại được" - vẫn dẫn tới cùng kết luận. |
| Lượt 4 agent KHÔNG bắt được mâu thuẫn 12.450 với 12.545 | Hỏi ép thêm một câu: "Cộng lại bảng doanh thu theo quý xem có đúng bằng con số tổng ghi ở mục II.1 không?" Agent sẽ ra ngay. Đây lại là bài học tốt hơn: chỉ dẫn càng cụ thể thì kết quả càng chắc, và đó đúng là lý do phải viết chỉ dẫn đó vào skill. |
| Agent trả lời lượt sau mà quên mất bối cảnh lượt trước | Nhắc lại tài liệu trong câu hỏi: "Vẫn trong báo cáo tổng kết năm 2026 đó, ...". Nếu phiên quá dài thì mở phiên mới và nạp lại tài liệu, chấp nhận mất vài lượt. |
| Prompt đóng gói ở Bước 6 sinh ra SKILL.md thiếu mục hoặc đặt sai chỗ | Bảo thẳng: "Thiếu mục SỐ LIỆU, NGÀY THÁNG, HẠN CHÓT. Bổ sung vào SKILL.md giúp tôi." Hoặc "Đặt lại file vào đúng .claude/skills/tom-tat-tai-lieu/SKILL.md". Đây cũng là dịp cho lớp thấy skill sửa được, không phải viết một phát ăn ngay. |
| Học viên gõ theo ngay từ lượt 1 nên lớp loạn nhịp, mỗi máy một kết quả | Nói rõ ngay đầu khối demo: "Khối này cả lớp XEM thôi, chưa gõ. Đến Thực hành 1 mới tới lượt anh chị." Ai lỡ gõ rồi thì cứ để, lát vào thực hành làm lại từ đầu. |
| Cháy giờ, diễn 5 lượt xong đã hết 45 phút | Cắt Bước 2 (lượt liệt kê theo từng phần) vì đây là lượt ít kịch tính nhất, gộp vào lời dẫn: "tôi còn phải hỏi thêm một lượt nữa bắt nó liệt kê theo từng phần". Giữ bằng được Bước 4 (mâu thuẫn) và Bước 6 (đóng gói), đó là hai bước mang toàn bộ giá trị của buổi. |

## Bài tập
- **Tại lớp:** Tạo skill `tom-tat-tai-lieu`, chạy trên hợp đồng demo, rồi chạy trên 1 tài liệu công việc thật của mình. Nộp 2 bản tóm tắt.
- **Về nhà:** Tạo thêm 1 skill cho một việc lặp lại khác trong nghề của mình. Viết dòng description rõ "dùng khi nào". Chạy thử 1 lần, chụp kết quả gửi nhóm Zalo.

## Tiêu chí hoàn thành buổi
- [ ] Có thư mục `.claude/skills/tom-tat-tai-lieu/` với file SKILL.md đúng nội dung trong dự án của học viên.
- [ ] Chạy skill trên hợp đồng demo, bản tóm tắt đủ 5 mục và bóc đúng các số liệu chính (120 triệu, 2 đợt, 12 tháng, phạt 0,05%/ngày, bảo mật 2 năm).
- [ ] Chạy được skill trên 1 tài liệu công việc thật của học viên.
- [ ] Học viên giải thích được vai trò dòng description và quy tắc chống bịa.
