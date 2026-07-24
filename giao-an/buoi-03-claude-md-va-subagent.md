# Giáo án Buổi 03: CLAUDE.md, bộ nhớ dự án và nhân viên AI chuyên trách

> Bản này thay cho `buoi-03-mcp.md` và `buoi-04-subagent.md` theo lịch dạy thực tế.
> Mỗi bước demo/thực hành có đủ 4 thành phần: LỜI DẪN GV, PROMPT, FILE DEMO, KẾT QUẢ MONG ĐỢI.

## Thông tin buổi
- **Buổi:** 03 / 6 (theo lịch dạy thực tế)
- **Khái niệm chính:** CLAUDE.md (bộ nhớ dự án) + Subagent (nhân viên chuyên trách) + nối chuỗi 2 agent
- **KHÔNG dạy hôm nay:** chạy song song nhiều agent (để Buổi 4)
- **Thời lượng:** 150 phút

## Lớp đang ở đâu (đọc kỹ trước khi soạn bài)
- Buổi 1 đã dạy: skill (tạo `tom-tat-tai-lieu`), MCP ở mức khái niệm, repo GitHub + token + GitHub MCP, và tạo `report-agent` trong 14 phút (quá nhanh, coi như chưa hiểu).
- Buổi 2 đã dạy: đào sâu skill, chuỗi 5 lượt chat rồi đóng gói, chống bịa.
- **Lỗ hổng phải lấp hôm nay:** CLAUDE.md và bộ nhớ. Buổi 2 lỡ hỏi lớp "CLAUDE.md dùng để làm gì" trong khi chưa ai dạy.

## Chuẩn bị của giảng viên

### Kiểm 10 phút trước giờ lên lớp (bắt buộc, tránh chết demo)
- [ ] Hỏi Claude Code: "bạn đang có những công cụ nào" để lấy đúng tên tool điền vào `tools`
- [ ] Test: giao việc cho một subagent rồi hỏi nó đang áp quy tắc nào, xem subagent có nhận CLAUDE.md của dự án không
- [ ] Test xem tài khoản lớp có bộ nhớ tự động giữa các phiên không. Nếu không có thì bỏ hẳn phần đó, chỉ dạy CLAUDE.md
- [ ] Chạy thử trọn P1 tới P7 một lượt

### Chuẩn bị thường lệ
- [ ] Mở sẵn thư mục dự án của khóa, có `.claude/agents/report-agent.md` từ Buổi 1
- [ ] File demo: `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md`, `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- [ ] Mẫu: `mau-cau-hinh/claude-md-mau.md`, `mau-cau-hinh/agent-report-mau.md`
- [ ] **KHÔNG xóa** file agent cũ của học viên. Hôm nay sửa agent cũ, không tạo lại từ đầu
- [ ] Gửi Zalo lớp trước buổi: "nhớ mở đúng thư mục dự án của buổi trước"

## Mục tiêu buổi
1. Tạo được `CLAUDE.md` cho thư mục dự án và **chứng minh được** agent có đọc nó.
2. Phân biệt được 3 chỗ đặt chỉ dẫn: CLAUDE.md, skill, agent. Nói được cái nào đặt ở đâu.
3. Hiểu subagent khác skill ở đâu: skill là đưa thêm tài liệu cho người đang làm, subagent là giao cho người khác làm.
4. Sửa được `report-agent` cho chuẩn và biết cách kiểm chứng agent thật sự chạy.
5. Tạo được agent thứ hai `soat-so-lieu` và nối chuỗi 2 agent chạy tuần tự.

## Kết quả cầm về
- 1 file `CLAUDE.md` ở gốc thư mục dự án, đã test bằng phiên mới.
- `report-agent` đã sửa chuẩn + 1 báo cáo có mục liệt kê nguồn số liệu.
- 1 agent `soat-so-lieu` chạy được (không có quyền Write).
- 1 lần chạy nối chuỗi: report-agent soạn xong, soat-so-lieu đối chiếu.

## Khái niệm cốt lõi (ngôn ngữ đời thường)

Workspace của bạn là một công ty thu nhỏ:

| | Là gì | Nằm ở đâu | Nạp lúc nào |
|---|---|---|---|
| **CLAUDE.md** | Nội quy dán ở cửa phòng, ai vào cũng đọc | Gốc thư mục dự án | Tự đọc **khi mở phiên mới** |
| **Skill** | Quyển quy trình để trong tủ, gặp đúng việc thì rút ra | `.claude/skills/<ten>/SKILL.md` | Nạp thêm vào cuộc trò chuyện đang chạy |
| **Subagent** | **Đổi người làm.** Phiếu giao việc đưa cho nhân viên phòng khác | `.claude/agents/<ten>.md` | Khi được giao việc |
| **MCP** | Thẻ ra vào kho (GitHub, Drive, web) | Cài trong Claude Desktop | Luôn sẵn sau khi cắm |

**Câu chốt bắt buộc nói ra:** "Skill là đưa thêm tài liệu cho người đang làm. Subagent là giao cho người khác làm."

**Ba điều về subagent phải nói rõ, nếu không lớp hiểu sai:**
1. Subagent **không nghe** cuộc trò chuyện của bạn. Giao việc phải viết đủ như viết email cho người lạ, kèm đường dẫn file.
2. Subagent **không hỏi lại bạn được**. Nó ngồi phòng khác, không gọi điện ra được.
3. Bạn **không nhìn thấy** bên trong subagent làm gì. Chỉ nhận bản báo cáo cuối. Nên phải bắt nó tự khai nguồn.

---

## Timeline chi tiết

### [00:00-00:10] Mở đầu: bản đồ khóa và kiểm tra đầu giờ

- **Lời dẫn GV:** "Chào cả lớp. Hai buổi vừa rồi cả lớp đã có hai thứ trong tay: một là skill, tức quy trình đóng gói sẵn để agent làm đúng chuẩn mỗi lần; hai là kho skill trên GitHub. Hôm nay mình lên một nấc mới. Mình sẽ dạy agent nhớ anh chị là ai để khỏi phải dặn lại mỗi lần, rồi tuyển cho anh chị nhân viên AI chuyên trách đầu tiên và cho hai nhân viên đó làm nối tiếp nhau."
- **Chiếu bảng bản đồ khóa 3 dòng:**

| Buổi | Đã có gì trong tay |
|---|---|
| Buổi 1 | Skill `tom-tat-tai-lieu`, kho skill trên GitHub, agent `report-agent` đầu tiên |
| Buổi 2 | Biết skill sinh ra từ đâu, biết bắt agent không bịa số |
| **Hôm nay** | **Bộ nhớ dự án (CLAUDE.md) + nhân viên chuyên trách + cho 2 nhân viên làm nối tiếp** |

- **Kiểm nhanh đầu giờ (2 phút):** ai còn mở được thư mục dự án, ai còn thấy skill `tom-tat-tai-lieu`, ai còn file `report-agent`. Ai mất thì trợ giảng kèm riêng, không để cả lớp chờ.

> Ghi chú GV: mở đầu bằng thứ lớp đã làm được, không nhắc lại chuyện buổi trước lệch nhau. Nếu có học viên tự hỏi về CLAUDE.md, xử lý theo bảng tình huống cuối giáo án.

### [00:10-00:32] CLAUDE.md: nỗi đau trước, giải pháp sau

**Bước 1: Cho lớp thấy nỗi đau (chưa có CLAUDE.md)**
- **Lời dẫn GV:** "Tôi nhờ nó soạn một email khách hàng. Cả lớp để ý văn phong và xem có emoji không."
- **Prompt:**
  ```
  Viết giúp tôi email nhắc khách An Phát thanh toán, dựa trên tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- **Kết quả mong đợi:** email ra được nhưng văn phong chung chung, có thể có emoji, xưng hô chưa đúng kiểu công ty. GV dặn lại vài câu cho đúng ý.
- **Lời dẫn GV chốt bước:** "Giờ tôi tắt phiên này, mở phiên mới, nhờ lại việc tương tự. Cả lớp đoán xem nó có nhớ mấy điều tôi vừa dặn không." Mở phiên mới, chạy lại, nó quên sạch. "Mỗi lần lại dặn lại. Cả phòng tôi năm người, mỗi người dặn một kiểu."

**Bước 2: Tạo CLAUDE.md**
- **Lời dẫn GV:** "Chỗ nào mình lặp lại thì gói lại, đúng bài anh Hải dạy buổi trước. Nhưng lần này không gói thành skill, vì đây không phải một việc cụ thể, đây là nội quy áp cho MỌI việc. Nội quy thì dán ở cửa."
- **Prompt:**
  ```
  Tạo file CLAUDE.md ở gốc thư mục dự án này, ngắn gọn, gồm:
  - Tôi là ai: [họ tên], [chức danh], công ty [tên], lĩnh vực [ngành].
  - Thư mục này dùng để: [một câu].
  - Quy tắc bắt buộc: trả lời tiếng Việt; văn bản gửi ra ngoài dùng văn phong công sở và KHÔNG dùng emoji; không được tạo ra con số không có trong file nguồn, thiếu thì ghi [đợi bổ sung]; trước khi sửa hoặc xóa file có sẵn thì hỏi tôi.
  - Cấu trúc thư mục: liệt kê các thư mục con hiện có và mỗi thư mục dùng làm gì.
  - Đầu ra tôi hay cần: [báo cáo tuần / email khách / bảng tổng hợp].
  Giữ file dưới 40 dòng.
  ```
- **File demo:** mẫu đối chiếu `mau-cau-hinh/claude-md-mau.md`
- **Kết quả mong đợi:** file `CLAUDE.md` ở gốc thư mục, dưới 40 dòng, đủ 5 mục.

**Bước 3: Phép thử (BẮT BUỘC mở phiên mới)**
- **Lời dẫn GV (ghi đỏ, đừng quên):** "Chú ý chỗ này, đây là chỗ hay hỏng nhất. CLAUDE.md chỉ được đọc khi MỞ PHIÊN MỚI. Nếu anh chị tạo file xong rồi hỏi tiếp trong phiên cũ thì sẽ không thấy khác gì và tưởng mình làm sai."
- **Prompt:** mở phiên mới, chạy lại y nguyên prompt ở Bước 1.
- **Kết quả mong đợi:** email lần này đúng văn phong công sở, không emoji, xưng hô đúng, không cần dặn lại câu nào. GV chiếu 2 kết quả cạnh nhau.
- **Prompt kiểm thêm:**
  ```
  Bạn đang áp những quy tắc nào của tôi? Liệt kê lại, và cho biết bạn đọc chúng từ file nào.
  ```
- **Kết quả mong đợi:** agent kể lại đúng các quy tắc và nói rõ đọc từ `CLAUDE.md`.

**Thực hành ngay tại chỗ (trong khối này):** mỗi học viên tạo CLAUDE.md cho thư mục mình, mở phiên mới, chạy phép thử. **Mốc cứng: phút 32 cả lớp phải có CLAUDE.md chạy được.** Yêu cầu dán 3 dòng đầu kết quả vào chat Zoom để GV lướt kiểm.

### [00:32-00:42] Ba chỗ đặt chỉ dẫn + bộ nhớ

- **Lời dẫn GV:** "Giờ cả lớp đã có ba loại file đều là file văn bản chứa chỉ dẫn, rất dễ lẫn. Tôi phân cho rõ một lần."
- Chiếu bảng 4 dòng ở mục Khái niệm cốt lõi (CLAUDE.md / Skill / Subagent / MCP).
- **Câu hỏi tình huống, gọi 3 học viên:**
  - "Quy tắc email không dùng emoji đặt ở đâu?" (CLAUDE.md, vì áp cho mọi việc)
  - "Cách tóm tắt một hợp đồng theo 5 mục đặt ở đâu?" (skill, vì là một việc cụ thể)
  - "Người chuyên soạn báo cáo đặt ở đâu?" (agent)
- **Nói về bộ nhớ, giữ ngắn 3 phút:**

| Loại | Ai viết | Sống bao lâu | Kiểm soát được không |
|---|---|---|---|
| CLAUDE.md | **Bạn viết** | Vĩnh viễn, luôn được đọc | Có, mở file sửa bất cứ lúc nào |
| Nhớ trong một phiên | Không ai ghi ra file | Hết phiên là mất | Không |
| Bộ nhớ tự động | Claude tự ghi | Qua nhiều phiên | Rất hạn chế |

- **Câu chốt:** "Đừng trông vào trí nhớ tự động. Cái gì muốn agent nhớ chắc chắn thì viết vào CLAUDE.md."

> Ghi chú GV: nếu tài khoản lớp không có bộ nhớ tự động (đã kiểm trước giờ), bỏ dòng thứ ba, chỉ nói hai dòng đầu. Càng gọn càng tốt.

### [00:42-00:55] Subagent là gì và khác skill chỗ nào

- **Lời dẫn GV:** "Buổi trước anh Hải dạy skill. Hôm nay có một thứ nhìn rất giống skill nhưng khác hẳn về bản chất."
- **Điểm phân biệt duy nhất cần nhớ:** skill là đưa thêm tài liệu cho **người đang làm** (vẫn là Claude đang nói chuyện với bạn). Subagent là **giao cho người khác làm** (một bản Claude khác, ngồi phòng riêng).
- **Ba hệ quả phải nói rõ:** subagent không nghe cuộc trò chuyện của bạn; không hỏi lại bạn được; bạn không nhìn thấy bên trong nó làm gì.
- **Cấu trúc file agent:** phần đầu giữa hai dấu `---` có 3 dòng cần nhớ (`name`, `description`, `tools`), phần sau là lời dặn việc.
  - `description` quyết định khi nào Claude tự gọi agent này ra.
  - `tools` là danh sách công cụ agent được dùng. **Nói rõ giới hạn:** tools chặn công cụ, KHÔNG chặn dữ liệu. Agent có quyền đọc thì vẫn đọc được mọi file trong thư mục dự án. Muốn giấu file lương, hợp đồng thì đừng để file đó trong thư mục dự án.
- **Câu hỏi tương tác:** "Theo cả lớp, agent chuyên soát lỗi số liệu có nên cho quyền sửa file không?" (Không. Người kiểm tra thì không được cầm bút sửa bài.)

### [00:55-01:18] Demo GV: sửa report-agent cho chuẩn

**Bước 1: Mở agent cũ ra sửa (không tạo mới)**
- **Lời dẫn GV:** "Buổi 1 mình đã tạo report-agent rồi, nhưng lúc đó vội, chỉ kịp nhìn thấy file sinh ra. Hôm nay mình mổ xẻ nó và sửa cho chuẩn. Đây cũng là kỹ năng quan trọng hơn cả việc tạo agent: biết sửa agent khi nó làm sai."
- **Prompt (P1):**
  ```
  Mở file .claude/agents/report-agent.md và sửa lại:
  - description: ghi rõ agent chuyên soạn báo cáo, đề xuất, email công việc từ số liệu thô, và ghi rõ "dùng khi cần biến dữ liệu hoặc ý thô thành văn bản công sở hoàn chỉnh".
  - tools: chỉ giữ Read, Write, Grep, Glob.
  - Phần thân: tiếng Việt công sở, không emoji, không được tạo ra con số không có trong nguồn. Nếu thiếu thông tin thì VẪN soạn đầy đủ, chỗ thiếu ghi [đợi bổ sung], và liệt kê các câu cần hỏi ở cuối bản dưới mục "Cần chủ quản xác nhận". Tuyệt đối không dừng lại để hỏi tôi.
  Sửa xong in lại toàn bộ nội dung file cho tôi xem.
  ```
- **File demo:** `.claude/agents/report-agent.md` (đã có từ Buổi 1); mẫu đối chiếu `mau-cau-hinh/agent-report-mau.md`
- **Kết quả mong đợi:** file có 3 dòng khai báo rõ, phần thân có dòng "tuyệt đối không dừng lại để hỏi".
- **Lời dẫn GV chốt bước (điểm dạy quan trọng):** "Cả lớp để ý dòng cuối. Vì sao phải dặn nó đừng hỏi? Vì nhân viên này ngồi phòng khác, không gọi điện ra cho tôi được. Nếu tôi bảo nó hỏi trước khi làm, nó sẽ đứng im hoặc tự đoán bừa. Đây là chỗ khác hẳn với skill."

**Bước 2: Mở phiên mới rồi mới giao việc**
- **Lời dẫn GV (ghi đỏ):** "Sửa file agent xong, phải mở phiên mới thì Claude mới nạp bản mới. Đây là lỗi khiến quá nửa lớp tắc nếu không dặn trước."
- **Prompt (P2):**
  ```
  Nhờ report-agent soạn báo cáo bán hàng tháng 3 từ file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md.
  Bố cục: kết quả tháng 3, số liệu chính, vướng mắc, kế hoạch tháng 4.
  Chỉ dùng con số có trong file. Cuối bản, liệt kê nguyên văn mọi con số đã dùng kèm dòng lấy từ file.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md`
- **Kết quả mong đợi:** báo cáo 4 phần, không emoji, và có mục liệt kê nguồn số liệu: 1.085 triệu (tháng 3), 915 triệu (tháng 2), 2 đơn chờ thanh toán, 1 đơn hủy.
- **Lời dẫn GV:** mở file gốc, so 2 con số bất kỳ trước lớp trong 30 giây. "Đây mới là cách kiểm agent không bịa. Bắt nó khai nguồn, rồi mình soi lại."

**Bước 3: Thí nghiệm agent có tự được gọi không**
- **Lời dẫn GV (nói TRƯỚC khi bấm):** "Bây giờ tôi thử không gọi tên agent, xem Claude có tự giao cho nó không. Có hai khả năng, và cả hai đều bình thường, không phải lỗi."
- **Prompt (P3):**
  ```
  Từ file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md, soạn giúp tôi một báo cáo bán hàng tháng 3 theo văn phong công sở.
  Làm xong, cho tôi biết bạn đã tự làm hay đã giao cho subagent nào.
  ```
- **Kết quả mong đợi:** một trong hai. Nếu giao cho `report-agent`: chứng minh `description` viết đủ rõ. Nếu tự làm: GV dạy luôn "việc nhỏ thì Claude tự làm cho nhanh, muốn chắc thì gọi đích danh, đừng trông vào tự động".

### [01:18-01:28] Nghỉ giải lao
Trợ giảng kèm riêng nhóm chưa xong CLAUDE.md hoặc chưa sửa được agent.

### [01:28-01:52] Thực hành 1: tạo agent thứ hai, chạy offline hoàn toàn

- **Lời dẫn GV:** "Giờ cả lớp tuyển nhân viên thứ hai. Người này chuyên soát lỗi số liệu. Và chú ý, tôi cố tình KHÔNG cho anh ta quyền sửa file."
- **Prompt (P4):**
  ```
  Tạo file .claude/agents/soat-so-lieu.md định nghĩa một subagent chuyên soát lỗi số liệu.
  - name: soat-so-lieu
  - description: Chuyên đối chiếu một bản báo cáo với file dữ liệu gốc để tìm số liệu sai, số liệu bịa, hoặc kết luận không có căn cứ. Dùng khi cần kiểm lại một bản nháp trước khi gửi đi.
  - tools: Read, Grep, Glob
  - Phần thân: nhận vào đường dẫn bản nháp và đường dẫn file gốc. Lập bảng 4 cột: con số trong bản nháp | con số trong file gốc | khớp hay lệch | ghi chú. Sau đó liệt kê những câu khẳng định không tìm thấy căn cứ trong file gốc. Không tự sửa file, chỉ báo cáo.
  Tạo xong in lại nội dung file.
  ```
- **File demo:** không cần
- **Kết quả mong đợi:** file `.claude/agents/soat-so-lieu.md`, dòng `tools` **không có Write**.
- **Lời dẫn GV chốt:** "Vì sao bỏ Write? Vì người kiểm tra mà được sửa bài thì kiểm tra làm gì nữa. Đây là ví dụ khoanh quyền có ý nghĩa thật, không phải khoanh cho vui."
- **Mốc cứng phút 52:** cả lớp dán tên 2 agent đang có vào chat Zoom.

### [01:52-02:20] Thực hành 2: nối chuỗi 2 agent chạy tuần tự

- **Lời dẫn GV:** "Đây là phần hay nhất hôm nay. Mình có hai nhân viên rồi, giờ cho họ làm nối tiếp nhau: người thứ nhất viết báo cáo, người thứ hai soát lại trước khi gửi. Giống hệt quy trình ở công ty."
- **Prompt (P5):**
  ```
  Bước 1: nhờ report-agent soạn báo cáo bán hàng tháng 3 từ tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md, lưu vào ket-qua/bao-cao-thang-3.md.
  Bước 2: sau khi có file đó, nhờ soat-so-lieu đối chiếu ket-qua/bao-cao-thang-3.md với file gốc và trả cho tôi bảng đối chiếu.
  Làm lần lượt, xong bước 1 mới sang bước 2.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md`
- **Kết quả mong đợi:** có file `ket-qua/bao-cao-thang-3.md` mở ra xem được (bằng chứng agent đã chạy thật), và một bảng đối chiếu 4 cột. Nếu report-agent có bịa số nào thì soat-so-lieu bắt được.
- **Lời dẫn GV chốt (đặt nền cho Buổi 4):** "Để ý: bước 2 phải chờ bước 1 xong mới làm được, vì không có báo cáo thì lấy gì mà soát. Đây gọi là chạy tuần tự. Mai anh Hải sẽ dạy kiểu ngược lại: nhiều việc độc lập chạy cùng lúc."

**Phần cho ai làm nhanh:** tạo thêm 1 agent cho đúng việc lặp lại của nghề mình (agent soạn email chào hàng, agent nhắc công nợ, agent làm biên bản họp), rồi nối vào chuỗi.

### [02:20-02:30] Chốt và giao bài

- **Lời dẫn GV:** "Tổng kết ba ý hôm nay."
  1. **CLAUDE.md** là nội quy dán ở cửa, agent tự đọc mỗi khi mở phiên mới. Cái gì muốn nhớ chắc chắn thì viết vào đây.
  2. **Subagent** là đổi người làm, không phải đưa thêm tài liệu. Nó không nghe chuyện của bạn, không hỏi lại được, và bạn không thấy bên trong nó.
  3. **Muốn tin agent thì bắt nó khai nguồn**, rồi mở file gốc soi lại.
- **Bài về nhà:**
  - Bổ sung CLAUDE.md cho đầy đủ hơn (thêm cách xưng hô với khách, mẫu văn bản hay dùng).
  - Tạo 1 agent cho việc lặp lại của nghề mình, chạy thử 1 lần, chụp màn hình gửi Zalo lớp.
- **Báo trước Buổi 4:** chạy nhiều agent **song song** (khác tuần tự hôm nay), cách quản lý bộ agent khi đã có 3-4 con, và đính chính lại phần MCP.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| P0 | Viết email nhắc khách An Phát thanh toán | `demo/buoi-01/bien-ban-hop-mau.md` | Văn phong chung chung, có thể có emoji (đây là nỗi đau) |
| P1 | Sửa `.claude/agents/report-agent.md`: description, tools, không dừng lại hỏi | agent có sẵn | File 3 dòng khai báo rõ, có dòng "không dừng lại để hỏi" |
| P2 | Nhờ report-agent soạn báo cáo tháng 3, cuối bản liệt kê nguyên văn số liệu | `demo/buoi-04/so-lieu-ban-hang-thang.md` | Báo cáo 4 phần + mục nguồn: 1.085 triệu, 915 triệu |
| P3 | Soạn báo cáo (không gọi tên agent), rồi cho biết tự làm hay giao ai | như trên | Một trong hai, cả hai đều dạy được |
| P4 | Tạo `.claude/agents/soat-so-lieu.md`, tools chỉ Read, Grep, Glob | không | File agent không có quyền Write |
| P5 | Nối chuỗi: report-agent soạn, xong soat-so-lieu đối chiếu | như trên | File `ket-qua/bao-cao-thang-3.md` + bảng đối chiếu 4 cột |
| P6 | Bạn đang áp quy tắc nào của tôi, đọc từ file nào? | không | Kể đúng quy tắc, nói rõ đọc từ CLAUDE.md |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| **Tạo CLAUDE.md xong nhưng "không thấy khác gì"** | Chưa mở phiên mới. CLAUDE.md chỉ nạp khi mở phiên mới. Đây là lỗi số một của buổi, dặn trước khi thực hành |
| **Sửa agent xong gọi tên thì Claude không biết agent đó** | Cũng do phiên cũ chưa nạp lại. Mở phiên mới rồi gọi |
| **Không thấy thư mục `.claude` trong File Explorer** | Thư mục ẩn trên Windows. Bật "hiện file ẩn" trong tab View. Dặn trước 2 phút đầu thực hành |
| **Học viên hỏi về CLAUDE.md của buổi trước** | Trả lời gọn, không sa đà: "CLAUDE.md để đúng hôm nay mới hợp, vì hôm nay mình bắt đầu có nhiều agent, cần một chỗ đặt quy tắc chung." Rồi quay lại bài ngay |
| **Agent trả về danh sách câu hỏi thay vì bản báo cáo** | Phần thân agent còn dòng "hỏi trước khi làm". Sửa lại theo P1: vẫn soạn đủ, chỗ thiếu ghi [đợi bổ sung] |
| **P3 Claude tự làm, không gọi agent** | Bình thường, đã báo trước. Dạy luôn: việc nhỏ thì gọi đích danh cho chắc |
| **Đặt tên agent có dấu cách hoặc chữ hoa** | Đổi về chữ thường nối gạch nối: `soat-so-lieu` |
| **Khối YAML đầu file hỏng (thiếu dấu `---`)** | Bảo Claude sửa lại đúng định dạng, đừng để học viên tự sửa tay |
| **Học viên hỏi tools có chặn được agent đọc file lương không** | Trả lời thật: KHÔNG. tools chặn công cụ, không chặn dữ liệu. Muốn giấu thì đừng để file trong thư mục dự án |
| **Học viên chưa có thư mục dự án riêng** | Trợ giảng dựng ngay trong 5 phút đầu. Không có thư mục riêng thì CLAUDE.md vô nghĩa |
| **Cháy giờ** | Cắt theo thứ tự: phần cho người làm nhanh, rồi P3 (thí nghiệm auto), rồi rút bảng phân biệt còn 5 phút. **Tuyệt đối không cắt Thực hành 2 (nối chuỗi)** |

## Cách kiểm học viên qua Zoom (thay cho đi quanh lớp)

| Cách | Làm thế nào |
|---|---|
| **Dán chat Zoom** | Sau mỗi thực hành, cả lớp dán 3 dòng đầu output vào chat. GV lướt 30 giây biết ai chưa ra kết quả |
| **Mốc đồng bộ cứng** | Phút 32 phải có CLAUDE.md chạy được. Phút 52 phải có 2 agent. Ai chưa tới mốc thì trợ giảng vào phòng riêng kèm, không để cả lớp chờ |
| **Xoay vòng share màn hình** | Mỗi buổi gọi 3-4 người share 30 giây, buổi sau gọi người khác |
| **Danh sách đỏ** | Trợ giảng ghi tên ai chưa làm được, kèm 1-1 sau buổi. Ai đỏ 2 buổi liên tiếp thì buổi 5-6 gần như mất |

**Kỳ vọng thực tế:** làm được và giải thích được 40%, làm được nhưng phải copy prompt mẫu 45%, chưa làm được dưới 15%. Đừng kỳ vọng 80% giỏi, sẽ dạy nhanh quá tay.

## Ba câu kiểm hiểu cuối buổi (gọi ngẫu nhiên)
1. "Quy tắc không dùng emoji nên đặt ở CLAUDE.md hay trong file agent? Vì sao?" (CLAUDE.md, vì áp cho mọi việc, đặt trong agent thì phải chép lại nhiều lần)
2. "Skill khác subagent chỗ nào?" (Skill là đưa thêm tài liệu cho người đang làm, subagent là giao cho người khác làm)
3. "Vì sao agent soát số liệu không được cấp quyền Write?" (Người kiểm tra thì không được sửa bài)

Trả lời được 2/3 là nắm được ý chính.

## Tiêu chí hoàn thành buổi
- [ ] Có file `CLAUDE.md` ở gốc thư mục dự án, đã test bằng phiên mới và agent kể lại đúng quy tắc
- [ ] `report-agent` đã sửa chuẩn, có dòng không dừng lại để hỏi
- [ ] Chạy được P2 ra báo cáo có mục liệt kê nguồn số liệu
- [ ] Có agent `soat-so-lieu` với tools không chứa Write
- [ ] Chạy được nối chuỗi P5, mở được file `ket-qua/bao-cao-thang-3.md`
- [ ] Nói lại được: skill là đưa tài liệu, subagent là đổi người làm
