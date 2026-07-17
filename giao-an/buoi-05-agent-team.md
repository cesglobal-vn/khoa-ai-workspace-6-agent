# Giáo án Buổi 05: Agent Team - điều khiển đội agent chạy song song

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối demo/thực hành có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

## Thông tin buổi
- **Buổi:** 05 / 6
- **Khái niệm chính:** Agent Team
- **Loại:** Nâng cao
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop
- [ ] Mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/`
- [ ] File demo cần dùng:
  - `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/thi-truong/boi-canh-thi-truong.md`
  - `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/doi-thu/doi-thu-canh-tranh.md`
  - `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/so-lieu/so-lieu-ban-hang.csv`
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/agent-team-mau.md`
- [ ] Kiểm tra thư mục demo có đủ 3 thư mục con: `thi-truong/`, `doi-thu/`, `so-lieu/`

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu agent team là gì: một việc lớn chia cho nhiều agent làm cùng lúc, một lead ghép kết quả.
2. Nắm 4 nguyên tắc: chia việc độc lập, phân vùng file, chạy song song, lead tổng hợp và kiểm mâu thuẫn.
3. Viết được prompt giao lead chia một việc thành nhiều phần cho các agent chạy song song.
4. Biết khi nào KHÔNG nên chạy song song (việc phụ thuộc nhau, phải làm tuần tự).
5. Tự chia một việc thật của mình cho 2-3 agent và nhận về một bản tổng hợp.

## Kết quả cầm về (deliverable)
- Một lần chạy agent team trên thư mục demo `du-an-ra-mat-san-pham/`: 3 agent chạy song song, lead ghép thành 1 bản tóm tắt chung.
- Một prompt chia việc song song viết cho công việc thật của học viên (kèm sơ đồ team ai làm phần nào).

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Agent team** là nhiều agent cùng làm một công việc lớn. Bạn (qua Claude Code) đóng vai lead: chia việc thành các phần độc lập, giao mỗi phần cho một agent, các agent chạy song song, rồi bạn ghép kết quả lại.
- Liên hệ đời thực: giống trưởng nhóm giao việc cho 3 nhân viên làm cùng lúc, xong gom lại thành một báo cáo.
- **4 nguyên tắc:**
  1. Chia việc độc lập: mỗi agent làm một phần không đụng phần của agent khác.
  2. Phân vùng file: mỗi agent chỉ đọc và sửa thư mục của mình, tránh giẫm chân nhau.
  3. Chạy song song: giao tất cả cùng lúc để rút ngắn thời gian.
  4. Lead tổng hợp: khi các agent xong, lead gom kết quả, kiểm số liệu có khớp không, xuất bản cuối.
- **Hai mức:** mức 1 là giao nhiều việc song song trong một phiên (dùng cho lớp); mức 2 là team nhiều phiên có lead và teammate riêng (chỉ giới thiệu, ai cần thì học thêm sau khóa).
- **Nối buổi 4:** mỗi agent trong team có thể là một subagent chuyên trách đã học ở buổi 4 (ví dụ agent phân tích số liệu, agent nghiên cứu). Buổi 5 học cách cho nhiều agent như vậy chạy cùng lúc.
- **Lưu ý quan trọng:** việc nào các phần phụ thuộc nhau (phần sau cần kết quả phần trước) thì KHÔNG chia song song, phải làm lần lượt.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn GV:** "Chào cả lớp. Buổi 4 mình đã tạo được subagent, tức là agent con chuyên một việc, có vai trò và công cụ riêng. Hôm nay mình lên một bậc nữa: cho nhiều agent cùng chạy một lúc, mỗi agent lo một phần, rồi mình ghép lại. Đây gọi là agent team."
- Recap buổi 4: subagent là agent chuyên trách một việc (ví dụ Report, Research). Mỗi agent trong team hôm nay có thể chính là một subagent như vậy.
- Nêu mục tiêu buổi: học xong tự chia được một việc thật cho 2-3 agent chạy song song và nhận về bản tổng hợp.
- **Câu hỏi mở màn:** "Ở công ty, khi có một việc gấp và to, anh chị hay làm một mình hay chia cho vài người làm song song rồi gom lại? Agent team đúng là kiểu chia việc đó, nhưng người làm là AI."

### [00:15-00:35] Lý thuyết ngắn: agent team + sơ đồ
- **Lời dẫn GV:** "Ý tưởng rất đơn giản. Một việc lớn, ví dụ chuẩn bị tài liệu ra mắt sản phẩm, gồm nhiều phần không dính nhau: tìm hiểu thị trường, so sánh đối thủ, phân tích số liệu bán hàng. Ba phần này làm độc lập được, nên giao cho 3 agent chạy cùng lúc sẽ nhanh gấp mấy lần."

**Sơ đồ team (vẽ lên bảng hoặc chiếu):**
```
                 BẠN (lead qua Claude Code)
                 │  chia việc + phân vùng file
     ┌───────────┼───────────┐
     ▼           ▼           ▼
  Agent 1     Agent 2     Agent 3     (chạy song song, mỗi agent 1 thư mục)
 thi-truong/  doi-thu/    so-lieu/
     └───────────┼───────────┘
                 ▼
        Lead tổng hợp + kiểm mâu thuẫn + xuất bản cuối
```

- Giảng 4 nguyên tắc, mỗi nguyên tắc kèm 1 câu đời thực:
  1. **Chia việc độc lập:** như chia 3 phần báo cáo cho 3 người, không ai chờ ai.
  2. **Phân vùng file:** dặn rõ mỗi agent chỉ đọc thư mục của mình. Giống mỗi nhân viên chỉ mở đúng ngăn tài liệu của họ, tránh sửa nhầm file người khác.
  3. **Chạy song song:** bấm giao cả 3 cùng lúc thay vì làm xong cái này mới tới cái kia.
  4. **Lead tổng hợp:** trưởng nhóm gom 3 phần, đọc lại xem số liệu có khớp không rồi mới chốt.
- Nói rõ ranh giới mức 1 và mức 2: "Lớp mình dùng mức 1, tức giao nhiều việc song song trong một phiên. Mức 2 là team nhiều phiên có lead riêng và teammate riêng nhắn tin cho nhau, cái đó nâng cao, hôm nay chỉ giới thiệu để anh chị biết là có."
- **Câu hỏi tương tác:** "Cho tôi một ví dụ việc ở công ty anh chị mà chia song song được, và một ví dụ phải làm tuần tự vì phần sau cần kết quả phần trước."

### [00:35-01:00] Demo giảng viên: chạy team 3 agent trên dự án ra mắt sản phẩm

**Bước 1: Cho lớp xem cấu trúc thư mục dự án**
- **Lời dẫn GV:** "Trước khi giao việc, mình xem thư mục dự án đã. Nó có 3 thư mục con, mỗi thư mục là phần việc của một agent. Đây chính là cách phân vùng file: mỗi agent một thư mục."
- **Prompt gõ vào Claude Code:**
  ```
  Liệt kê cấu trúc thư mục du-an-ra-mat-san-pham/ cho tôi xem có những thư mục con nào và mỗi thư mục có file gì.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/`
- **Kết quả mong đợi:** Claude liệt kê 3 thư mục con `thi-truong/` (có `boi-canh-thi-truong.md`), `doi-thu/` (có `doi-thu-canh-tranh.md`), `so-lieu/` (có `so-lieu-ban-hang.csv`). GV chỉ vào và nói: mỗi thư mục sẽ giao cho một agent.

**Bước 2: Giao lead chia 3 phần cho 3 agent chạy song song**
- **Lời dẫn GV:** "Giờ mình giao cho Claude Code làm lead: chia việc thành 3 phần, mỗi agent một thư mục, chạy song song, xong ghép lại. Anh chị chú ý câu quan trọng nhất là dòng dặn mỗi agent chỉ đọc thư mục của mình."
- **Prompt gõ vào Claude Code (prompt demo chính, bám `mau-cau-hinh/agent-team-mau.md`):**
  ```
  Tôi có một dự án chuẩn bị ra mắt sản phẩm trong thư mục du-an-ra-mat-san-pham/.
  Hãy chia thành 3 phần độc lập và giao cho 3 agent chạy SONG SONG:
  - Agent 1: chỉ đọc thư mục thi-truong/ và tóm tắt bối cảnh thị trường (nhu cầu khách, xu hướng, cơ hội cho bản mới).
  - Agent 2: chỉ đọc thư mục doi-thu/ và lập bảng so sánh các đối thủ (giá, điểm mạnh, điểm yếu) và chỉ ra khoảng trống thị trường.
  - Agent 3: chỉ đọc thư mục so-lieu/ và phân tích số liệu bán hàng (xu hướng doanh thu, sản phẩm nào tăng nhanh).
  Mỗi agent chỉ đọc đúng thư mục của mình, không đọc thư mục của agent khác.
  Sau khi cả ba xong, hãy tổng hợp thành một bản tóm tắt chung cho tôi, và kiểm xem các phần có mâu thuẫn số liệu nào không.
  ```
- **File demo:** cả 3 thư mục con trong `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/`
- **Kết quả mong đợi:** Claude khởi tạo 3 agent chạy song song, sau đó trả về một bản tổng hợp gồm:
  - Phần thị trường: khách nhỏ chuyển từ sổ tay và Excel sang phần mềm; quan tâm dễ dùng, giá hợp lý, hỗ trợ nhanh, xem báo cáo trên điện thoại; cơ hội cho bản mới là nhấn báo cáo trên điện thoại và hỗ trợ chuyển dữ liệu miễn phí.
  - Phần đối thủ: bảng 3 đối thủ. Đối thủ A giá rẻ (khoảng 30 triệu/năm, ít tính năng); Đối thủ B tầm trung (80-100 triệu/năm, giao diện cũ, cài phức tạp); Đối thủ C cao cấp (trên 200 triệu/năm, đắt, thừa tính năng). Khoảng trống thị trường: gói tầm trung, dễ dùng, có bản điện thoại tốt, giá vừa phải, hỗ trợ chuyển dữ liệu miễn phí.
  - Phần số liệu: doanh thu tăng dần qua 3 tháng; Gói Cao cấp tăng nhanh (480 lên 520 rồi 640 triệu, số đơn 48 lên 52 rồi 64); Gói Tiêu chuẩn tăng nhẹ và ổn định.
  - Lead nhận xét không có mâu thuẫn số liệu, và gợi ý: bản mới "Gói Cao cấp Plus" nên nhắm vào khoảng trống tầm trung, đúng lúc Gói Cao cap đang tăng nhanh.

**Bước 3: Chỉ ra bằng chứng của 4 nguyên tắc trong lần chạy vừa rồi**
- **Lời dẫn GV:** "Mình quay lại xem lần chạy vừa rồi thể hiện 4 nguyên tắc ở đâu. Chia độc lập: 3 phần không dính nhau. Phân vùng file: mỗi agent một thư mục. Song song: cả 3 chạy cùng lúc nên nhanh. Lead tổng hợp: Claude gom lại và kiểm số liệu. Đủ 4."
- **Prompt gõ vào Claude Code:**
  ```
  Cho tôi biết mỗi agent vừa rồi đã đọc những file nào, để tôi kiểm tra là các agent không đọc lấn thư mục của nhau.
  ```
- **File demo:** cùng thư mục trên
- **Kết quả mong đợi:** Claude xác nhận Agent 1 chỉ đọc `thi-truong/boi-canh-thi-truong.md`, Agent 2 chỉ đọc `doi-thu/doi-thu-canh-tranh.md`, Agent 3 chỉ đọc `so-lieu/so-lieu-ban-hang.csv`. Không agent nào đọc lấn. GV chốt: đó là phân vùng file đúng.

### [01:00-01:30] Thực hành 1: học viên chạy lại team trên thư mục demo chung
- **Lời dẫn GV:** "Tới lượt anh chị. Mở thư mục demo giống của tôi, gõ prompt chia 3 agent song song, chạy và đọc bản tổng hợp. Mục tiêu là ai cũng thấy được 3 agent chạy cùng lúc và có một bản gom cuối."
- **Đề bài:** Chạy lại đúng team 3 agent trên thư mục `du-an-ra-mat-san-pham/`, nhận về bản tổng hợp, đối chiếu với kết quả mong đợi ở demo.
- **Prompt gợi ý cho học viên:**
  ```
  Trong thư mục du-an-ra-mat-san-pham/, hãy chia việc cho 3 agent chạy song song:
  - Agent 1 chỉ đọc thi-truong/ tóm tắt bối cảnh thị trường.
  - Agent 2 chỉ đọc doi-thu/ lập bảng so sánh đối thủ và chỉ khoảng trống thị trường.
  - Agent 3 chỉ đọc so-lieu/ phân tích xu hướng doanh thu.
  Mỗi agent chỉ đọc thư mục của mình. Sau đó tổng hợp thành một bản chung và kiểm mâu thuẫn số liệu.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/` (cả 3 thư mục con)
- **Kết quả mong đợi:** học viên nhận bản tổng hợp có đủ 3 phần (thị trường, đối thủ A/B/C, số liệu), nêu được khoảng trống thị trường là gói tầm trung, và thấy Gói Cao cấp đang tăng nhanh. GV đi vòng lớp kiểm: bản có đủ 3 phần và có một câu kiểm mâu thuẫn của lead là đạt.

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2: học viên chia một việc thật của mình cho 2-3 agent
- **Lời dẫn GV:** "Giờ dùng việc thật của anh chị. Chọn một việc to mà có thể tách thành 2-3 phần không dính nhau. Ví dụ: chuẩn bị họp gồm đọc biên bản cũ, tổng hợp số liệu tháng, soạn danh sách việc tồn. Mỗi phần một thư mục, mỗi thư mục một agent."
- **Đề bài:**
  1. Chọn một việc nhiều phần độc lập trong công việc của mình.
  2. Tổ chức file thành các thư mục con, mỗi thư mục là một phần.
  3. Viết prompt giao 2-3 agent chạy song song, dặn mỗi agent chỉ đọc thư mục của mình.
  4. Chạy, để lead tổng hợp, đọc lại bản gom.
- **Prompt gợi ý (học viên thay tên thư mục và mô tả phần việc của mình):**
  ```
  Tôi có việc [tên việc] trong thư mục [tên-thu-muc-cua-toi]/.
  Hãy chia cho [2 hoặc 3] agent chạy SONG SONG:
  - Agent 1: chỉ đọc thư mục [phan-1]/ và [làm gì].
  - Agent 2: chỉ đọc thư mục [phan-2]/ và [làm gì].
  - Agent 3: chỉ đọc thư mục [phan-3]/ và [làm gì].
  Mỗi agent chỉ đọc thư mục của mình. Sau khi xong, tổng hợp thành một bản chung và chỉ ra chỗ nào các phần chưa khớp.
  ```
- **File demo:** dữ liệu công việc thật của học viên (không dùng file demo của khóa).
- **Kết quả mong đợi:** mỗi học viên có một prompt chia việc song song chạy được trên dữ liệu của mình, và nhận về một bản tổng hợp. GV nhắc: nếu học viên chọn nhầm một việc mà phần sau cần kết quả phần trước, hướng dẫn tách lại hoặc chuyển sang làm tuần tự.
- **Câu hỏi tương tác:** "Việc anh chị vừa chọn có thật sự độc lập không? Thử hỏi: nếu Agent 2 chưa xong thì Agent 1 có làm được không? Nếu vẫn làm được thì mới nên chạy song song."

### [02:15-02:35] Chốt & giao bài
- **Lời dẫn GV:** "Tóm lại buổi hôm nay: agent team là một lead chia việc độc lập cho nhiều agent, mỗi agent một thư mục, chạy song song, lead ghép và kiểm mâu thuẫn. Nhớ hai điều: phân vùng file để khỏi giẫm chân nhau, và việc phụ thuộc nhau thì làm tuần tự chứ đừng song song. Buổi 6 mình sẽ ghép skill, MCP và team thành một quy trình thật đầu cuối, đó là bài capstone."
- Tổng kết 4 nguyên tắc và ranh giới mức 1, mức 2.
- Bài về nhà (xem mục Bài tập).
- Xem trước buổi 6: capstone ghép skill + MCP + team.

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Liệt kê cấu trúc thư mục du-an-ra-mat-san-pham/ | `.../du-an-ra-mat-san-pham/` | Thấy 3 thư mục con thi-truong, doi-thu, so-lieu |
| 2 | Chia 3 phần cho 3 agent chạy song song, mỗi agent 1 thư mục, tổng hợp cuối | cả 3 thư mục con | Bản tổng hợp 3 phần + lead kiểm mâu thuẫn |
| 3 | Cho biết mỗi agent đã đọc file nào (kiểm phân vùng) | cả 3 thư mục con | Xác nhận không agent nào đọc lấn thư mục khác |
| 4 | (Thực hành 1) Học viên chạy lại team 3 agent | `.../du-an-ra-mat-san-pham/` | Bản gom đủ 3 phần, nêu khoảng trống tầm trung |
| 5 | (Thực hành 2) Chia việc thật của mình cho 2-3 agent song song | dữ liệu học viên | Prompt chạy được + 1 bản tổng hợp |

## Câu hỏi tương tác gợi ý
- "Cho một ví dụ việc ở công ty chia song song được, và một ví dụ phải làm tuần tự."
- "Trong lần chạy vừa rồi, 4 nguyên tắc thể hiện ở chỗ nào?"
- "Nếu Agent 2 chưa xong mà Agent 1 vẫn làm được thì việc đó có độc lập không?"
- "Vì sao phải dặn mỗi agent chỉ đọc thư mục của mình? Chuyện gì xảy ra nếu không dặn?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Hai agent cùng sửa một file, kết quả đè lên nhau gây xung đột | Phân vùng file rõ: mỗi agent một thư mục riêng, không cho hai agent ghi cùng một file. Nếu cần chung dữ liệu, để một agent đọc rồi lead gom, đừng cho cùng ghi. |
| Việc thực ra phụ thuộc nhau nhưng học viên vẫn chia song song, kết quả sai hoặc thiếu | Kiểm tính độc lập trước: nếu phần sau cần kết quả phần trước thì KHÔNG song song, chuyển sang làm tuần tự từng bước. |
| Số liệu giữa các agent lệch nhau (ví dụ hai agent nói hai con số doanh thu khác nhau) | Đây đúng là việc của lead: dặn lead kiểm mâu thuẫn số liệu trước khi chốt, chỉ ra chỗ lệch và lấy nguồn gốc từ thư mục so-lieu/ làm chuẩn. |
| Agent đọc lấn sang thư mục của agent khác | Viết lại prompt nhấn mạnh "chỉ đọc đúng thư mục của mình, không đọc thư mục khác"; chạy lại và dùng prompt kiểm phân vùng (prompt #3). |
| Học viên chọn việc quá nhỏ, chia ra không đáng | Gợi ý gộp lại làm một agent, hoặc chọn việc lớn hơn có ít nhất 2 phần thật sự tách rời. |

## Bài tập
- **Tại lớp:** chạy xong team 3 agent trên thư mục demo, và viết được 1 prompt chia việc thật của mình cho 2-3 agent song song.
- **Về nhà:** chọn một việc thật khác trong công việc, tổ chức thành các thư mục con theo phần, chạy team song song, lưu lại bản tổng hợp và vẽ sơ đồ team ai làm phần nào. Ghi chú 1 chỗ mà lead phát hiện số liệu chưa khớp (nếu có).

## Tiêu chí hoàn thành buổi
- [ ] Chạy được team 3 agent trên thư mục demo, nhận về 1 bản tổng hợp đủ 3 phần.
- [ ] Chỉ ra được 4 nguyên tắc trong lần chạy đó.
- [ ] Viết được 1 prompt chia việc thật của mình cho 2-3 agent chạy song song, có dặn phân vùng file.
- [ ] Phân biệt được việc nên song song và việc phải làm tuần tự.
