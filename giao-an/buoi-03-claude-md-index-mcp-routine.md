# Giáo án Buổi 03: Hồ sơ cá nhân, cấu trúc phòng ban, index, MCP Drive và Gmail, routine

> Bản này thay cho `buoi-03-claude-md-va-subagent.md`. Subagent đã bỏ khỏi khóa.
> Mỗi bước demo hoặc thực hành có đủ 4 thành phần: LỜI DẪN GV, PROMPT, FILE DEMO, KẾT QUẢ MONG ĐỢI.

## Thông tin buổi
- **Buổi:** 03 / 6 (theo lịch dạy thực tế)
- **Khái niệm chính:** CLAUDE.md hai cấp (profile cá nhân + phòng ban), file index, MCP kết nối Drive và Gmail, routine chạy tự động theo lịch
- **KHÔNG dạy trong khóa này:** subagent, agent team
- **Thời lượng:** 150 phút

## Ý đồ của buổi
Hai buổi đầu học viên đã biết đóng gói việc lặp lại thành skill. Nhưng agent vẫn chưa biết họ là ai, làm phòng ban nào, file để đâu. Buổi này dựng **chỗ làm việc thật**: hồ sơ cá nhân, cấu trúc thư mục theo phòng ban, mục lục để tìm nhanh, rồi nối agent với Drive và Gmail, cuối cùng cho một việc tự chạy theo lịch.

Mạch buổi: **agent biết bạn là ai → biết file để đâu → chạm được dữ liệu thật → tự chạy không cần nhắc**.

## Chuẩn bị của giảng viên

### Kiểm 15 phút trước giờ lên lớp (bắt buộc, tránh chết demo)
- [ ] **Kiểm connector Drive và Gmail** trong Claude Desktop: mở phần kết nối, xem có Google Drive và Gmail không, gói tài khoản lớp có dùng được không. Nếu không có, chuyển sang phương án B ở bảng tình huống
- [ ] **Kiểm tính năng chạy theo lịch (routine)**: xem bản Claude Desktop lớp dùng có đặt lịch chạy tự động được không. Nếu không có, dạy routine ở mức thiết kế trên giấy và hướng dẫn cách tự chạy tay mỗi sáng
- [ ] Đăng nhập sẵn 1 tài khoản Google **phụ, không phải tài khoản công ty**, có sẵn vài file Drive và vài email mẫu để demo
- [ ] Chạy thử trọn P1 tới P8 một lượt
- [ ] Quay sẵn video màn hình phần cắm Drive và Gmail, chiếu khi live hỏng

### Chuẩn bị thường lệ
- [ ] Mở sẵn thư mục dự án của khóa
- [ ] Mẫu mở sẵn: `mau-cau-hinh/claude-md-profile-va-cau-truc-phong-ban.md`
- [ ] File demo: `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`, `tai-lieu-phat/demo/buoi-03/doanh-thu-quy.csv`
- [ ] Gửi Zalo lớp trước buổi: nhớ mở đúng thư mục dự án, và chuẩn bị sẵn tên phòng ban của mình

## Mục tiêu buổi
1. Viết được CLAUDE.md **cấp cá nhân** chứa hồ sơ của mình, áp cho mọi thư mục.
2. Dựng được **cấu trúc thư mục theo phòng ban** của mình và CLAUDE.md riêng cho thư mục đó.
3. Hiểu quy tắc khi hai cấp mâu thuẫn: cụ thể hơn thì thắng.
4. Tạo được **file index** để agent tìm file nhanh, và biết cách nhờ agent tự cập nhật index.
5. Hiểu MCP nối agent với Drive và Gmail làm được gì, và **các quy tắc an toàn bắt buộc** khi cho agent chạm vào email.
6. Thiết kế được một **routine**: một việc chạy tự động theo lịch.

## Kết quả cầm về
- 1 file CLAUDE.md cấp cá nhân, đã test bằng phiên mới.
- 1 thư mục phòng ban đúng cấu trúc, có CLAUDE.md riêng.
- 1 file `00-index.md` do agent tự dựng.
- 1 bản thiết kế routine của riêng mình (chạy được hoặc chạy tay tùy tính năng).

---

## Khái niệm cốt lõi (ngôn ngữ đời thường)

### Hai cấp CLAUDE.md

| Cấp | Đặt ở đâu | Áp cho | Ví như |
|---|---|---|---|
| **Cá nhân** | `C:\Users\<tên máy>\.claude\CLAUDE.md` | Mọi thư mục | Hồ sơ nhân viên phòng nhân sự giữ: bạn là ai, làm phòng nào |
| **Phòng ban** | `CLAUDE.md` ở gốc thư mục công việc | Chỉ thư mục đó | Nội quy riêng dán ở cửa phòng đó |

**Khi hai cấp mâu thuẫn: cụ thể hơn thì thắng.** Nội quy phòng ban đè nội quy công ty.

### File index
Mục lục của thư mục. Mỗi file một dòng mô tả. Agent đọc mục lục trước, biết ngay cần mở file nào, không phải lật từng trang.

### MCP
Thẻ ra vào kho. Buổi 1 đã cắm GitHub. Hôm nay cắm thêm Drive (kho tài liệu) và Gmail (hộp thư).

**Nói rõ để lớp khỏi hiểu sai:** agent đọc file trong thư mục dự án trên máy **không cần MCP**. MCP là để chạm tới thứ **nằm ngoài** máy: Drive, Gmail, web, cơ sở dữ liệu.

### Routine
Một việc được đặt lịch chạy tự động, không cần bạn ngồi gõ. Ví như hẹn giờ máy pha cà phê: sáng dậy là có sẵn.

---

## Timeline chi tiết

### [00:00-00:10] Mở đầu và bản đồ khóa

- **Lời dẫn GV:** "Chào cả lớp. Hai buổi vừa rồi cả lớp đã biết đóng gói việc lặp lại thành skill, và có kho skill trên GitHub. Nhưng để ý một chuyện: agent vẫn chưa biết anh chị là ai, làm phòng ban nào, file để chỗ nào. Mỗi lần vẫn phải dặn lại từ đầu. Hôm nay mình dựng hẳn chỗ làm việc: agent biết anh chị là ai, biết file để đâu, chạm được vào Drive và Gmail, và cuối cùng là tự chạy mà không cần nhắc."

- **Chiếu bảng bản đồ:**

| Buổi | Đã có gì |
|---|---|
| Buổi 1 | Skill `tom-tat-tai-lieu`, kho skill trên GitHub |
| Buổi 2 | Biết skill sinh ra từ đâu, biết bắt agent không bịa số |
| **Hôm nay** | **Hồ sơ cá nhân, thư mục phòng ban, mục lục, nối Drive và Gmail, đặt lịch tự chạy** |

- **Kiểm nhanh 2 phút:** ai còn mở được thư mục dự án. Ai mất thì trợ giảng kèm riêng, không để cả lớp chờ.
- **Câu hỏi tương tác:** "Anh chị đang làm phòng ban nào? Kinh doanh, kế toán, marketing, nhân sự, hay hành chính?" Ghi lên bảng để lát chia nhóm theo phòng ban.

### [00:10-00:32] CLAUDE.md cấp cá nhân: hồ sơ của bạn

**Bước 1: Cho lớp thấy nỗi đau**
- **Lời dẫn GV:** "Tôi nhờ nó soạn một email khách hàng, cả lớp để ý văn phong và xem có emoji không."
- **Prompt (P1):**
  ```
  Viết giúp tôi email nhắc khách An Phát thanh toán, dựa trên tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- **Kết quả mong đợi:** email ra được nhưng văn phong chung chung, có thể có emoji, xưng hô chưa đúng kiểu công ty. GV dặn lại vài câu cho đúng ý, rồi **tắt phiên, mở phiên mới, hỏi lại việc tương tự**, nó quên sạch.
- **Lời dẫn GV chốt bước:** "Mỗi lần lại dặn lại. Chỗ nào mình lặp lại thì gói lại, đúng bài anh Hải dạy buổi trước. Nhưng lần này không gói thành skill, vì đây không phải một việc cụ thể. Đây là hồ sơ về chính tôi, áp cho mọi việc. Hồ sơ thì nộp cho phòng nhân sự giữ."

**Bước 2: Tạo hồ sơ cấp cá nhân**
- **Lời dẫn GV:** "File này đặt ở thư mục cá nhân trên máy, không nằm trong thư mục dự án nào cả. Nghĩa là mở bất cứ thư mục nào agent cũng đọc được."
- **Prompt (P2):**
  ```
  Tạo cho tôi file CLAUDE.md cấp cá nhân, đặt tại thư mục .claude trong thư mục người dùng của tôi. Nội dung gồm:
  - Tôi là ai: [họ tên], [chức danh], phòng [tên phòng ban], công ty [tên], lĩnh vực [ngành].
  - Tôi làm việc với ai: cấp trên xưng hô thế nào, đồng nghiệp, khách hàng gọi ra sao.
  - Quy tắc chung áp cho mọi việc: trả lời tiếng Việt ngắn gọn; văn bản gửi ra ngoài dùng văn phong công sở và KHÔNG dùng emoji; không tạo ra con số không có trong file nguồn, thiếu thì ghi [đợi bổ sung]; trước khi sửa hoặc xóa file có sẵn thì hỏi tôi; đơn vị tiền là đồng Việt Nam, ngày ghi theo kiểu ngày/tháng/năm.
  - Ba việc tôi làm lặp lại nhiều nhất: [liệt kê].
  Giữ file dưới 40 dòng.
  ```
- **File demo:** mẫu đối chiếu `mau-cau-hinh/claude-md-profile-va-cau-truc-phong-ban.md` phần 2
- **Kết quả mong đợi:** file CLAUDE.md ở thư mục `.claude` cá nhân, dưới 40 dòng, đủ 4 mục.
- **Cảnh báo GV phải nói:** "Tuyệt đối không ghi mật khẩu, token, số tài khoản, hay thông tin cá nhân của khách vào file này."

**Bước 3: Phép thử, BẮT BUỘC mở phiên mới**
- **Lời dẫn GV (ghi đỏ):** "Chỗ này hay hỏng nhất. CLAUDE.md chỉ được đọc khi MỞ PHIÊN MỚI. Tạo xong mà hỏi tiếp trong phiên cũ thì không thấy khác gì và tưởng mình làm sai."
- **Prompt (P3):** mở phiên mới, chạy lại y nguyên P1. Sau đó hỏi thêm:
  ```
  Bạn đang áp những quy tắc nào của tôi? Cho biết bạn đọc chúng từ file nào.
  ```
- **Kết quả mong đợi:** email lần này đúng văn phong, không emoji, xưng hô đúng, không cần dặn lại. Agent kể lại đúng quy tắc và nói rõ đọc từ CLAUDE.md cá nhân.

### [00:32-00:52] Thực hành 1: hồ sơ cá nhân + thư mục phòng ban

- **Lời dẫn GV:** "Đến lượt cả lớp. Làm hai việc: một là hồ sơ cá nhân, hai là dựng thư mục cho đúng phòng ban của mình. Tôi chia bảng cấu trúc cho từng phòng, anh chị lấy đúng phòng mình."

**Việc 1:** mỗi người tạo CLAUDE.md cá nhân theo P2, rồi test bằng phiên mới.

**Việc 2:** dựng thư mục phòng ban.
- **Prompt (P4):**
  ```
  Tạo cho tôi cấu trúc thư mục cho phòng [tên phòng ban] tại [đường dẫn thư mục làm việc của tôi], gồm các thư mục con: [dán danh sách theo mẫu phòng ban của bạn].
  Đồng thời tạo file CLAUDE.md ở gốc thư mục đó, ghi rõ: thư mục này dùng để làm gì, cấu trúc từng thư mục con chứa gì, quy trình riêng của phòng tôi là [nêu 1 tới 2 quy trình], và mọi file agent tạo ra thì lưu vào thư mục 05-bao-cao.
  ```
- **File demo:** cấu trúc mẫu 5 phòng ban ở `mau-cau-hinh/claude-md-profile-va-cau-truc-phong-ban.md` phần 3
- **Kết quả mong đợi:** mỗi người có một thư mục phòng ban đúng cấu trúc, kèm CLAUDE.md riêng.
- **Điểm dạy khi lớp làm xong:** "Giờ anh chị có hai cấp. Cấp cá nhân nói anh chị là ai. Cấp phòng ban nói thư mục này làm gì. Khi hai cái mâu thuẫn thì **cụ thể hơn thắng**: nội quy phòng ban đè nội quy công ty."
- **Mốc cứng phút 52:** cả lớp dán tên phòng ban và đường dẫn thư mục vừa tạo vào chat Zoom.

### [00:52-01:12] File index: mục lục cho thư mục

- **Lời dẫn GV:** "Bây giờ giả sử thư mục của anh chị có 40 file. Mỗi lần hỏi, agent phải mở lần lượt từng file để biết file nào chứa gì. Vừa chậm vừa dễ bỏ sót. Giải pháp giống hệt cuốn sách: làm cái mục lục."

**Bước 1: Nhờ agent tự dựng index**
- **Prompt (P5):**
  ```
  Đọc toàn bộ thư mục này và tạo file 00-index.md liệt kê mỗi file một dòng: tên file và một câu mô tả nội dung. Nhóm theo thư mục con, trình bày dạng bảng.
  ```
- **File demo:** thư mục phòng ban vừa dựng, hoặc `tai-lieu-phat/demo/buoi-03/` nếu thư mục học viên còn trống
- **Kết quả mong đợi:** file `00-index.md` dạng bảng, nhóm theo thư mục con, mỗi file một dòng mô tả.

**Bước 2: Dặn agent luôn dùng index**
- **Lời dẫn GV:** "Có mục lục rồi thì phải dặn nó dùng, không thì nó vẫn lật từng trang."
- **Prompt (P6):**
  ```
  Thêm vào file CLAUDE.md của thư mục này một dòng: trước khi tìm file, đọc 00-index.md để biết file nào chứa gì, đừng mở lần lượt từng file.
  ```
- **Kết quả mong đợi:** CLAUDE.md phòng ban có thêm dòng đó.

**Bước 3: Cập nhật index khi thêm file**
- **Prompt (P7):**
  ```
  Tôi vừa thêm mấy file mới. Cập nhật lại 00-index.md giúp tôi, giữ nguyên các dòng cũ còn đúng.
  ```
- **Kết quả mong đợi:** index có thêm dòng mới, dòng cũ giữ nguyên.
- **Lời dẫn GV chốt:** "Mỗi lần thêm file thì nhắc nó cập nhật mục lục. Đây là nề nếp, giống như thêm sách vào tủ thì ghi vào sổ."

### [01:12-01:22] Nghỉ giải lao
Trợ giảng kèm riêng nhóm chưa xong CLAUDE.md hoặc thư mục phòng ban.

### [01:22-01:52] MCP nối Drive và Gmail (GV demo, học viên xem và ghi)

- **Lời dẫn GV mở khối:** "Phần này cả lớp XEM thôi, chưa làm theo. Lý do: cắm Gmail nghĩa là cho agent đọc hộp thư của mình, phải hiểu rõ rồi mới làm, và nên làm ở nhà với tài khoản mình chủ động. Tôi làm mẫu trên tài khoản phụ của tôi, anh chị ghi lại các bước."

**Bước 1: Nhắc lại MCP và đính chính một hiểu nhầm**
- **Lời dẫn GV:** "Buổi 1 mình đã cắm GitHub MCP. Nhắc lại cho rõ một điều quan trọng: agent đọc file trong thư mục trên máy anh chị thì KHÔNG cần MCP, nó đọc thẳng. MCP là để với tay ra ngoài máy: Drive, Gmail, web, cơ sở dữ liệu."

**Bước 2: Cắm Google Drive**
- **Lời dẫn GV:** "Cắm Drive xong, agent đọc được tài liệu trên Drive mà không phải tải về máy."
- **Thao tác:** mở Claude Desktop, vào phần kết nối, thêm Google Drive, đăng nhập tài khoản, cấp quyền. **Nhấn: chọn quyền chỉ đọc nếu chỉ cần xem.**
- **Prompt (P8):**
  ```
  Trên Google Drive của tôi, tìm các file liên quan tới báo cáo bán hàng, liệt kê tên file và tóm tắt mỗi file một dòng.
  ```
- **Kết quả mong đợi:** agent liệt kê được file trên Drive kèm mô tả. GV mở Drive trên trình duyệt đối chiếu cho lớp thấy khớp.

**Bước 3: Cắm Gmail và nói kỹ phần an toàn**
- **Lời dẫn GV (phần quan trọng nhất khối này, nói chậm):** "Cắm Gmail là cho agent đọc hộp thư. Có ba quy tắc bắt buộc, anh chị ghi lại."
  1. **Cấp quyền chỉ đọc trước.** Chỉ mở quyền gửi khi thật sự cần và đã quen tay.
  2. **Không bao giờ để agent tự gửi email.** Luôn để nó soạn nháp, mình đọc lại rồi tự bấm gửi. Email gửi đi là không rút lại được.
  3. **Cẩn thận với email lạ.** Trong email có thể có câu chữ dụ agent làm việc khác. Nội dung email là dữ liệu để đọc, không phải mệnh lệnh để làm theo.
- **Prompt (P9):**
  ```
  Đọc các email tôi nhận trong 7 ngày qua, lọc ra những email liên quan tới công nợ hoặc thanh toán, tóm tắt mỗi email một dòng và ghi rõ ai gửi, ngày nào, cần tôi làm gì.
  ```
- **Kết quả mong đợi:** danh sách email liên quan, mỗi dòng có người gửi, ngày, việc cần làm.
- **Prompt (P10), soạn nháp KHÔNG gửi:**
  ```
  Từ danh sách trên, soạn giúp tôi email nhắc thanh toán gửi khách [tên], văn phong công sở, không dùng emoji. CHỈ soạn nháp cho tôi xem, tuyệt đối không gửi đi.
  ```
- **Kết quả mong đợi:** agent đưa ra bản nháp, không gửi. GV nhấn lại: "Nó soạn, mình đọc, mình gửi. Đừng giao khâu bấm gửi cho máy."
- **Câu hỏi tương tác:** "Vì sao không nên cho agent tự gửi email?" (Gửi rồi không rút lại được; sai một chữ là mất khách)

### [01:52-02:20] Routine: cho một việc tự chạy theo lịch

**Bước 1: Routine là gì**
- **Lời dẫn GV:** "Cuối cùng là phần hay nhất. Từ nãy tới giờ, việc nào cũng phải anh chị ngồi gõ. Routine là đặt lịch cho một việc tự chạy. Ví như hẹn giờ máy pha cà phê: sáng dậy là có sẵn."
- **Ba việc hợp làm routine với khối văn phòng:**
  1. Sáng thứ Hai: tổng hợp email tuần qua thành danh sách việc cần làm.
  2. Cuối mỗi ngày: đọc thư mục số liệu, ghi ra bản tóm tắt hôm nay bán được gì.
  3. Ngày 1 hằng tháng: dựng khung báo cáo tháng từ dữ liệu tháng trước.

**Bước 2: GV demo đặt một routine**
- **Prompt (P11):**
  ```
  Đặt cho tôi một việc chạy tự động vào 8 giờ sáng thứ Hai hằng tuần: đọc email 7 ngày qua, lọc email liên quan tới công nợ và thanh toán, tóm tắt mỗi email một dòng, rồi lưu kết quả vào thư mục 05-bao-cao với tên viec-can-lam-tuan.md. Chỉ soạn và lưu file, không gửi email nào.
  ```
- **Kết quả mong đợi:** hệ thống xác nhận đã đặt lịch. GV mở danh sách lịch đã đặt cho lớp xem.
- **Nếu bản đang dùng chưa có tính năng đặt lịch:** chuyển sang cách chạy tay có nề nếp, xem bảng tình huống. Bài học vẫn nguyên giá trị.

**Bước 3: Học viên thiết kế routine của mình**
- **Lời dẫn GV:** "Anh chị viết ra một routine cho công việc của mình theo đúng bốn câu hỏi này."
- **Khung thiết kế routine, chiếu lên bảng:**

| Câu hỏi | Trả lời của bạn |
|---|---|
| Chạy lúc nào | [8h sáng thứ Hai / cuối mỗi ngày / ngày 1 hằng tháng] |
| Đọc dữ liệu ở đâu | [thư mục nào / Drive / Gmail] |
| Làm gì với dữ liệu đó | [tóm tắt / lọc / dựng bảng] |
| Lưu kết quả vào đâu | [tên thư mục và tên file] |

- **Kết quả mong đợi:** mỗi học viên có một bản thiết kế routine 4 dòng, và ai máy chạy được thì đặt luôn.
- **Quy tắc an toàn phải nhắc:** "Routine chỉ nên **đọc và soạn**, đừng để nó tự gửi đi hay tự xóa. Việc chạy lúc mình không ngồi đó thì càng phải giới hạn chặt."

### [02:20-02:30] Chốt và giao bài

- **Lời dẫn GV, chốt bốn ý:**
  1. **Hồ sơ cá nhân** đặt ở thư mục `.claude` cá nhân, áp cho mọi thư mục. Nói agent biết bạn là ai.
  2. **CLAUDE.md phòng ban** đặt ở gốc thư mục công việc. Khi mâu thuẫn thì cụ thể hơn thắng.
  3. **Index** là mục lục, giúp agent tìm nhanh. Thêm file thì nhớ cập nhật.
  4. **MCP** đưa agent ra ngoài máy: Drive, Gmail. Nhưng **không bao giờ để agent tự gửi email**.
- **Bài về nhà:**
  - Hoàn thiện CLAUDE.md cá nhân và CLAUDE.md phòng ban.
  - Dựng đủ cấu trúc thư mục phòng ban, bỏ file công việc thật vào, chạy lại lệnh tạo index.
  - Ai muốn: cắm Drive ở nhà theo các bước đã ghi, dùng tài khoản mình chủ động. Gmail thì cấp quyền chỉ đọc.
  - Viết bản thiết kế routine của mình, gửi Zalo lớp.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| P1 | Viết email nhắc khách An Phát thanh toán | `demo/buoi-01/bien-ban-hop-mau.md` | Văn phong chung chung, có thể có emoji (đây là nỗi đau) |
| P2 | Tạo CLAUDE.md cấp cá nhân ở thư mục `.claude`, gồm hồ sơ + quy tắc chung | mẫu phần 2 | File dưới 40 dòng, đủ 4 mục |
| P3 | Mở phiên mới, chạy lại P1; rồi hỏi "bạn đang áp quy tắc nào, đọc từ file nào" | như P1 | Email đúng văn phong, agent kể đúng nguồn quy tắc |
| P4 | Tạo cấu trúc thư mục phòng ban + CLAUDE.md riêng | mẫu phần 3 | Thư mục đúng cấu trúc, có CLAUDE.md |
| P5 | Đọc cả thư mục, tạo `00-index.md` dạng bảng, nhóm theo thư mục con | thư mục vừa dựng | File index mỗi dòng một file |
| P6 | Thêm dòng vào CLAUDE.md: trước khi tìm file thì đọc `00-index.md` | CLAUDE.md phòng ban | Có thêm dòng đó |
| P7 | Cập nhật lại `00-index.md`, giữ nguyên dòng cũ còn đúng | index đã có | Index có dòng mới |
| P8 | Tìm file liên quan báo cáo bán hàng trên Drive, tóm tắt mỗi file một dòng | Drive tài khoản GV | Danh sách file khớp với Drive thật |
| P9 | Đọc email 7 ngày qua, lọc email công nợ, ghi rõ ai gửi, ngày nào, cần làm gì | Gmail tài khoản GV | Danh sách email có người gửi, ngày, việc cần làm |
| P10 | Soạn nháp email nhắc thanh toán, **tuyệt đối không gửi** | như P9 | Bản nháp, không gửi đi |
| P11 | Đặt việc chạy tự động 8h sáng thứ Hai: tổng hợp email công nợ, lưu ra file | lịch của GV | Xác nhận đã đặt lịch |

## Câu hỏi tương tác gợi ý
- "Anh chị làm phòng ban nào? Thư mục phòng đó nên có mấy ngăn?"
- "Hồ sơ cá nhân với nội quy phòng ban mâu thuẫn thì nghe cái nào?" (cụ thể hơn thắng)
- "Vì sao cần mục lục khi thư mục có 40 file?"
- "Agent đọc file trên máy có cần MCP không?" (Không. MCP là để với ra ngoài máy)
- "Vì sao không nên cho agent tự gửi email?" (Gửi rồi không rút lại được)
- "Routine nên được phép làm gì và không được phép làm gì?" (Đọc và soạn thì được, gửi đi và xóa thì không)

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| **Tạo CLAUDE.md xong nhưng "không thấy khác gì"** | Chưa mở phiên mới. CLAUDE.md chỉ nạp khi mở phiên mới. Dặn trước khi thực hành |
| **Không thấy thư mục `.claude`** | Thư mục ẩn. Trên Windows bật "hiện file ẩn" ở tab View. Hoặc nhờ chính agent mở file đó ra cho xem |
| **Không biết thư mục người dùng của mình ở đâu** | Nhờ agent: "cho tôi biết đường dẫn thư mục người dùng của tôi và tạo file ở đó" |
| **Hai cấp CLAUDE.md đá nhau, agent làm sai ý** | Dịp tốt để dạy: cụ thể hơn thắng. Sửa cấp phòng ban cho rõ hơn |
| **Không có connector Drive hoặc Gmail trong bản đang dùng** | Phương án B: demo bằng GitHub MCP đã cắm buổi 1, vẫn dạy đủ ý "MCP là để với ra ngoài máy". Phần Drive và Gmail chuyển thành hướng dẫn làm ở nhà |
| **Cắm Drive hoặc Gmail bị lỗi đăng nhập giữa buổi** | Chiếu video đã quay sẵn. Đừng để cả lớp ngồi chờ GV loay hoay |
| **Học viên đòi cắm Gmail công ty ngay tại lớp** | Khuyên để về nhà làm, và cấp quyền chỉ đọc. Tại lớp đang vừa học vừa lóng ngóng, dễ cấp nhầm quyền |
| **Agent đề nghị gửi email luôn** | Dừng lại, lấy làm ví dụ dạy: luôn để nó soạn nháp, mình đọc rồi tự bấm gửi |
| **Bản đang dùng chưa đặt lịch tự chạy được** | Dạy routine ở mức thiết kế 4 dòng, rồi hướng dẫn cách chạy tay có nề nếp: lưu sẵn câu lệnh vào một file, sáng thứ Hai mở ra dán chạy. Bài học không mất |
| **Index dựng ra sai hoặc thiếu file** | Nhờ agent làm lại và nói rõ: "đọc cả thư mục con, đừng bỏ sót file nào" |
| **Cháy giờ** | Cắt theo thứ tự: bước cập nhật index P7, rồi rút phần Drive còn 5 phút chỉ nói ý. **Không cắt** phần quy tắc an toàn Gmail và phần thiết kế routine |

## Cách kiểm học viên qua Zoom

| Cách | Làm thế nào |
|---|---|
| **Dán chat Zoom** | Sau mỗi thực hành, cả lớp dán 3 dòng đầu kết quả vào chat. GV lướt 30 giây biết ai chưa ra |
| **Mốc đồng bộ cứng** | Phút 32 phải có CLAUDE.md cá nhân chạy được. Phút 52 phải có thư mục phòng ban. Phút 72 phải có file index |
| **Xoay vòng share màn hình** | Mỗi buổi gọi 3-4 người share 30 giây |
| **Danh sách đỏ** | Trợ giảng ghi tên ai chưa làm được, kèm 1-1 sau buổi |

**Kỳ vọng thực tế:** làm được và giải thích được 40%, làm được nhưng phải copy prompt mẫu 45%, chưa làm được dưới 15%.

## Ba câu kiểm hiểu cuối buổi
1. "Hồ sơ cá nhân đặt ở đâu, và nó áp cho mấy thư mục?" (Thư mục `.claude` cá nhân, áp cho mọi thư mục)
2. "Agent đọc file trên máy có cần MCP không?" (Không. MCP để với ra ngoài máy: Drive, Gmail, web)
3. "Routine được phép làm gì, không được phép làm gì?" (Đọc và soạn thì được. Tự gửi đi hay tự xóa thì không)

## Tiêu chí hoàn thành buổi
- [ ] Có CLAUDE.md cấp cá nhân, đã test bằng phiên mới, agent kể lại đúng quy tắc
- [ ] Có thư mục phòng ban đúng cấu trúc, kèm CLAUDE.md riêng
- [ ] Có file `00-index.md` do agent dựng, và CLAUDE.md đã dặn agent dùng index
- [ ] Nói lại được: agent đọc file trên máy không cần MCP
- [ ] Nói lại được 3 quy tắc an toàn khi cắm Gmail
- [ ] Có bản thiết kế routine 4 dòng của riêng mình
