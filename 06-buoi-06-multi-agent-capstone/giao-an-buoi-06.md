# Outline Buổi 06 (buổi cuối): Capstone, ghép tất cả thành một quy trình công việc thật

> Buổi cuối. Không dạy khái niệm mới. Học viên ghép mọi thứ đã học thành một quy trình đầu-cuối, chạy, rồi trình bày.
> Bản cũ buoi-06-capstone.md có vài chỗ lệch với thực tế đã dạy, bản này thay thế.

## Thông tin buổi
- **Buổi:** 06 / 6 (buổi cuối)
- **Loại:** Capstone
- **Mục tiêu:** mỗi học viên có một quy trình công việc thật chạy được đầu-cuối, ghép nhiều thứ đã học
- **Thời lượng:** 150 phút

---

## PHẦN NỀN: cả khóa đã cho học viên những gì

Chiếu bảng này đầu buổi để lớp thấy trong tay mình đang có cả một bộ đồ nghề:

| Buổi | Học viên có được gì |
|---|---|
| 1 | Skill đầu tiên, kho skill trên GitHub |
| 2 | Biết skill sinh ra từ đâu, biết bắt agent không bịa số |
| 3 | Hồ sơ cá nhân (CLAUDE.md), thư mục theo phòng ban, file index, MCP nối Drive và Gmail, routine chạy theo lịch |
| 4 | MCP tạo slide, hiểu cửa sổ ngữ cảnh, biết dùng subagent cho việc nặng |
| 5 | Lập được agent chuyên trách, cho đội agent phối hợp nối chuỗi và song song |

Capstone hôm nay là **xâu tất cả những thứ trên vào một quy trình thật**.

### Bộ đồ nghề, dùng cái nào cho việc gì (nhắc nhanh)

| Công cụ | Dùng để |
|---|---|
| CLAUDE.md | Đặt quy tắc chung, để agent nhớ bạn là ai |
| Skill | Chuẩn hóa cách làm một việc lặp lại |
| MCP | Chạm ra ngoài máy: Drive, Gmail, tạo slide |
| Agent | Giao hẳn một vai cho một nhân viên AI |
| Đội agent | Nhiều agent làm chung: nối chuỗi hoặc song song |
| Routine | Đặt lịch cho một việc tự chạy |

---

## Timeline

| Khối | Phút | Nội dung |
|---|---|---|
| K0 | 00:00-00:12 | Mở đầu, tổng kết cả khóa |
| K1 | 00:12-00:35 | Capstone là gì + cách thiết kế một quy trình |
| K2 | 00:35-01:05 | Demo GV: chạy một quy trình end-to-end mẫu |
| Nghỉ | 01:05-01:15 | |
| K3 | 01:15-02:00 | Học viên dựng capstone của mình |
| K4 | 02:00-02:22 | Trình bày capstone |
| K5 | 02:22-02:30 | Chốt khóa, chứng nhận, học tiếp |

Mốc cứng: K3 là phần chính, không cắt. K2 nếu cháy thì rút gọn để dồn giờ cho K3.

---

## K0: Mở đầu và tổng kết khóa (12 phút)

**Lời dẫn GV:** "Đây là buổi cuối. Năm buổi qua mỗi buổi mình học một mảnh: skill, CLAUDE.md, MCP, agent, đội agent. Hôm nay không học thêm cái mới, mà xâu tất cả lại thành một quy trình công việc thật của anh chị, cho nó chạy một mạch, rồi mỗi người trình bày cho cả lớp xem."
- Chiếu bảng tổng kết khóa (phần nền).
- Nêu ba việc hôm nay: thiết kế quy trình, dựng và chạy, trình bày.

**PROMPT K0 (kiểm đồ nghề còn đủ):**
```
Liệt kê giúp tôi: các agent trong .claude/agents, các skill trong .claude/skills, và file CLAUDE.md của tôi đang có những quy tắc gì.
```
Kết quả mong đợi: agent, skill, CLAUDE.md của học viên còn đủ. Ai thiếu thì trợ giảng kèm nhanh.

---

## K1: Capstone là gì và cách thiết kế một quy trình (23 phút)

### Phần 1: Capstone là gì (5 phút)
- Chọn một việc thật anh chị làm mỗi tuần hoặc mỗi tháng, gồm nhiều bước. Dùng những thứ đã học để nó chạy gần như tự động.
- Không cần hoành tráng. Một quy trình 3 tới 4 bước là đủ.

### Phần 2: Cách thiết kế, dùng bảng (10 phút)
Trước khi gõ lệnh, vẽ quy trình ra giấy theo bảng này:

| Bước | Làm gì | Dùng công cụ nào | Đầu vào | Đầu ra |
|---|---|---|---|---|
| 1 | ... | agent / skill / MCP | file nào | file hoặc kết quả gì |
| 2 | ... | ... | kết quả bước 1 | ... |
| 3 | ... | ... | ... | ... |

- Nhấn: mỗi bước ghi rõ dùng agent nào hay skill nào, đầu vào lấy ở đâu, đầu ra lưu vào đâu.
- Câu hỏi tự soi: bước nào nối chuỗi (chờ bước trước), bước nào có thể song song.

### Phần 3: Ví dụ mẫu để lớp bắt chước (8 phút)
Chiếu ví dụ "Gói chốt tháng phòng kinh doanh":

| Bước | Làm gì | Công cụ | Đầu vào | Đầu ra |
|---|---|---|---|---|
| 1 | Rà khách cần nhắc thanh toán | agent-ra-soat-khach | thư mục hồ sơ khách | danh sách khách cần nhắc |
| 2 | Soạn báo cáo tháng + email nhắc | agent-soan-bao-cao | kết quả bước 1 + số liệu tháng | báo cáo, email |
| 3 | Tạo slide tổng kết tháng | MCP tạo slide | báo cáo bước 2 | ảnh slide |
| 4 | Đặt lịch tự chạy đầu tháng sau | routine | cả quy trình | lịch đã đặt |

Bước 1 tới 2 là nối chuỗi (bước 2 cần kết quả bước 1). Đây là mạch mẫu, học viên đổi theo nghề mình.

---

## K2: Demo GV chạy quy trình end-to-end mẫu (30 phút)

GV chạy trọn ví dụ trên trước lớp, từng bước, để lớp thấy các mảnh ghép vào nhau.

**Bước 1, PROMPT K2-1:**
```
Nhờ agent-ra-soat-khach đọc thư mục 03-buoi-03-phan-tich-du-lieu-mcp-routine/demo/phong-kinh-doanh-mau/01-khach-hang, chỉ ra khách cần nhắc thanh toán gấp nhất, lưu vào ket-qua/khach-can-nhac.md.
```
Kết quả mong đợi: file khach-can-nhac.md, chỉ ra An Phát.

**Bước 2, PROMPT K2-2:**
```
Làm hai việc từ ket-qua/khach-can-nhac.md và file số liệu 04-buoi-04-lap-bao-cao-va-slide/demo/so-lieu-ban-hang-thang.md:
1. Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3, lưu vào ket-qua/bao-cao-thang-3.md.
2. Nhờ agent-soan-bao-cao soạn email nhắc thanh toán gửi đúng khách trong khach-can-nhac.md, không emoji.
```
Kết quả mong đợi: báo cáo có nguồn số liệu (1.085 triệu, 915 triệu), email nhắc An Phát.

**Bước 3, PROMPT K2-3 (nếu MCP tạo slide sẵn sàng):**
```
Từ ket-qua/bao-cao-thang-3.md, tạo 2 ảnh slide tổng kết tháng: một slide doanh thu, một slide các việc cần theo dõi. Nền trắng, chữ tiếng Việt có dấu, không emoji.
```
Kết quả mong đợi: 2 ảnh slide.

**Bước 4, PROMPT K2-4 (nếu routine sẵn sàng):**
```
Đặt cho tôi việc chạy tự động ngày 1 hằng tháng: chạy lại quy trình rà khách và soạn báo cáo tháng, lưu vào ket-qua. Chỉ soạn và lưu, không gửi email.
```
Kết quả mong đợi: xác nhận đặt lịch.

**Lời dẫn GV chốt demo:** "Cả lớp thấy chưa, mình vừa xâu bốn thứ đã học vào một mạch: agent rà khách, agent soạn thảo, MCP làm slide, routine đặt lịch. Đây chính là capstone. Giờ tới lượt anh chị làm cho việc của mình."

> Nếu MCP slide hoặc routine chưa sẵn sàng, bỏ bước 3 và 4, quy trình vẫn trọn với 2 bước agent nối chuỗi.

---

## Nghỉ giải lao (10 phút)

---

## K3: Học viên dựng capstone của mình (45 phút, phần chính)

### Phần 1: Thiết kế (15 phút)
Mỗi học viên chọn một quy trình thật, điền bảng thiết kế 4 cột ở K1. Trợ giảng đi soát bảng trước khi cho gõ, tránh thiết kế sai từ đầu.
- Gợi ý theo nghề:
  - Kinh doanh: rà khách, soạn báo giá, làm slide chào hàng.
  - Kế toán: rà công nợ, soạn email nhắc, làm bảng tổng hợp.
  - Nhân sự: sàng lọc hồ sơ, soạn thư mời, làm slide onboarding.
  - Marketing: tổng hợp số liệu chiến dịch, soạn báo cáo, làm slide.
- Mốc cứng phút 30 (của giờ): mỗi người dán bảng thiết kế vào chat Zoom.

### Phần 2: Dựng và chạy (30 phút)
Học viên chạy quy trình của mình từng bước, lưu kết quả ra thư mục.
- Bắt buộc: dùng ít nhất 2 thứ đã học (ví dụ agent + đội agent, hoặc agent + MCP).
- Trợ giảng trực breakout hỗ trợ ai tắc.
- Ai xong sớm: thêm một bước (slide, hoặc routine).

---

## K4: Trình bày capstone (22 phút)

- Gọi 5 tới 6 học viên share màn hình 3 phút mỗi người: quy trình của tôi giải việc gì, gồm mấy bước, mỗi bước dùng gì, kết quả ra sao.
- GV nhận xét ngắn mỗi bài theo rubric bên dưới.
- Cả lớp học lẫn nhau, ghi lại ý hay áp được cho mình.

### Rubric chấm capstone (chiếu lên)

| Tiêu chí | Đạt khi |
|---|---|
| Chạy được đầu-cuối | Quy trình cho ra kết quả cuối cùng dùng được |
| Ghép nhiều thứ | Dùng ít nhất 2 thứ đã học (agent, đội agent, skill, MCP, routine) |
| Không bịa số | Kết quả có số liệu đúng nguồn, agent khai được nguồn |
| Giải thích được | Nói được vì sao chọn agent hay skill, bước nào nối chuỗi bước nào song song |
| Áp vào việc thật | Là quy trình dùng được ở công việc thật, không phải ví dụ suông |

Đạt 4 trên 5 tiêu chí là hoàn thành capstone.

---

## K5: Chốt khóa, chứng nhận, học tiếp (8 phút)

**Nhìn lại cả khóa:** từ chỗ dùng AI lẻ tẻ, giờ mỗi anh chị có một workspace riêng: hồ sơ, skill, agent, đội agent, và một quy trình thật chạy được.

**Cấp chứng nhận:** học viên đạt tối thiểu 5 trên 6 buổi và có capstone thì được cấp chứng nhận hoàn thành.

**Học gì tiếp sau khóa:**
- Đưa dần các việc lặp lại khác thành skill và agent.
- Chia sẻ bộ skill và agent cho đồng nghiệp qua GitHub.
- Mỗi tháng rà lại: quy trình nào còn làm tay nhiều thì đóng gói tiếp.

**Bài về nhà cuối:** hoàn thiện capstone của mình, dùng thật một tuần, ghi lại chỗ nào cần chỉnh, gửi Zalo lớp.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt tóm tắt | Khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Liệt kê agent, skill, CLAUDE.md đang có | K0 | Thấy đồ nghề còn đủ |
| K2-1 | agent-ra-soat-khach rà khách, lưu file | K2 | File khách cần nhắc (An Phát) |
| K2-2 | agent-soan-bao-cao soạn báo cáo + email | K2 | Báo cáo có nguồn, email nhắc |
| K2-3 | Tạo 2 slide tổng kết tháng | K2 | 2 ảnh slide |
| K2-4 | Đặt routine chạy đầu tháng | K2 | Xác nhận đặt lịch |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| Học viên chưa còn agent hoặc skill từ buổi trước | Trợ giảng kèm dựng lại nhanh 1 agent để có cái chạy capstone |
| Thiết kế quy trình quá tham, nhiều bước | Cắt còn 2 tới 3 bước cốt lõi, thêm sau nếu còn giờ |
| Bước sau chạy khi bước trước chưa xong | Nhắc nối chuỗi: xong bước 1 mới sang bước 2, chỉ rõ file trung gian |
| Số liệu giữa các bước lệch nhau | Bắt agent khai nguồn, mở file gốc so lại |
| MCP slide hoặc routine chưa chạy được | Bỏ hai bước đó, capstone vẫn trọn với phần agent |
| Cháy giờ phần trình bày | Giảm còn 4 người share, số còn lại nộp file, GV nhận xét sau |

## Ba câu kiểm hiểu cuối khóa
1. "Kể tên các thứ bạn đã ghép trong capstone và mỗi thứ lo phần nào."
2. "Trong quy trình của bạn, bước nào nối chuỗi, bước nào song song, vì sao?"
3. "Việc tiếp theo bạn sẽ đóng gói thành agent hay skill là việc gì?"

## Tiêu chí hoàn thành buổi và khóa
- [ ] Có bảng thiết kế quy trình của riêng mình
- [ ] Chạy được quy trình đầu-cuối, có kết quả cuối dùng được
- [ ] Ghép ít nhất 2 thứ đã học
- [ ] Trình bày được capstone, giải thích lựa chọn
- [ ] Đạt tối thiểu 5 trên 6 buổi để nhận chứng nhận

---

## Câu chưa rõ, cần anh chốt trước khi giãn thành bản chi tiết
1. Ví dụ mẫu K2 giữ bối cảnh phòng kinh doanh, hay đổi sang nhân sự cho khớp buổi trước?
2. Trình bày capstone: gọi mấy người share màn hình, số còn lại nộp file?
3. Có phát chứng nhận ngay tối nay hay sau khi nộp bài về nhà?
