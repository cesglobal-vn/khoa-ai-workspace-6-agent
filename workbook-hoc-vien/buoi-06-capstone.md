# Workbook Buổi 06: Capstone, ghép tất cả thành một lệnh

> Đây là buổi cuối. Bạn không học khái niệm mới. Bạn ghép 5 thứ đã học (agent, skill, MCP, subagent, agent team)
> thành một dây chuyền cho một việc công việc THẬT của mình, rồi chạy bằng một lệnh tổng.
> Điền trực tiếp vào workbook này khi làm. Cuối buổi bạn trình bày và nhận chứng nhận.

## Mục tiêu buổi
Học xong buổi này bạn sẽ:
1. Nhìn được bức tranh tổng: 5 khái niệm xếp thành một dây chuyền công việc.
2. Chạy được một quy trình thật đầu-cuối bằng một lệnh tổng.
3. Tự thiết kế quy trình lặp lại của chính mình dưới dạng dây chuyền agent.
4. Xử lý được 3 lỗi hay gặp: số liệu mâu thuẫn, một agent sai kéo bước sau, quy trình quá tham.
5. Trình bày được: mình dùng agent, skill, MCP, subagent, team ở đâu.

## Chuẩn bị trước khi vào phần dựng
- [ ] Chọn sẵn 1 quy trình công việc THẬT của bạn, nhiều bước, làm lặp lại hằng tuần hoặc hằng tháng.
- [ ] Chuẩn bị file dữ liệu cho quy trình đó (tài liệu, ghi chú, file Excel/CSV).
- [ ] Kiểm tra trong thư mục dự án còn đủ: skill tóm tắt (buổi 2), MCP đã cắm (buổi 3), 2 subagent report + research (buổi 4).
- [ ] Nếu chưa nghĩ ra quy trình, xem "5 nhóm nghề gợi ý workflow" ở cuối workbook để lấy ý.

Gợi ý chọn quy trình tốt để làm capstone:
- Có nhiều bước rõ ràng (ít nhất 3 bước).
- Có phần đọc tài liệu và phần đọc số liệu (để dùng cả skill lẫn MCP).
- Kết thúc bằng một văn bản gửi đi (báo cáo, đề xuất, email).
- Bạn phải làm nó lặp lại, nên gói thành một lệnh sẽ tiết kiệm thật.

---

## Phần A: Thiết kế dây chuyền của bạn

### A1. Bảng thiết kế workflow (điền vào)
Mỗi dòng là một bước. Ghi rõ bước đó do agent nào làm, dùng skill hay MCP gì, đầu vào và đầu ra là gì.

| Bước | Agent nào làm | Dùng skill / MCP gì | Đầu vào (thư mục/file) | Đầu ra |
|---|---|---|---|---|
| 1 | Agent 1 | | | |
| 2 | Agent 2 | | | |
| 3 | Agent 3 | | | |
| 4 (gộp) | Report Agent | | kết quả bước 1-2-3 | |
| 5 (gộp) | Report Agent | | kết quả bước 1-2-3 | email/báo cáo gửi đi |

Ví dụ đã điền (đề mẫu ra mắt sản phẩm) để bạn tham khảo:

| Bước | Agent nào làm | Dùng skill / MCP gì | Đầu vào | Đầu ra |
|---|---|---|---|---|
| 1 | Agent Thị trường | Skill tóm tắt tài liệu | `thi-truong/` | Tóm tắt bối cảnh + cơ hội |
| 2 | Agent Đối thủ | (không) | `doi-thu/` | Bảng so sánh đối thủ |
| 3 | Agent Số liệu | MCP đọc file CSV | `so-lieu/so-lieu-ban-hang.csv` | Phân tích doanh thu + xu hướng |
| 4 | Report Agent | (không) | kết quả 1-2-3 | Đề xuất kế hoạch ra mắt |
| 5 | Report Agent | (không) | kết quả 1-2-3 | Email gửi sếp, không emoji |

### A2. Sơ đồ dây chuyền (điền tay)
Điền tên agent và thư mục vào ô trống. Đây là bản đồ để bạn nhìn toàn cảnh trước khi viết lệnh.

```
                     LỆNH TỔNG của tôi
                            │
                     LEAD (Claude Code)
              chia việc + phân vùng thư mục
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
   Agent 1: ________   Agent 2: ________   Agent 3: ________
   đọc: ___________   đọc: ___________    đọc: ___________
   dùng: __________   dùng: __________    dùng: __________
        │                   │                   │
        └───────────────────┼───────────────────┘
                            ▼
                  LEAD kiểm số liệu khớp
                            ▼
                REPORT AGENT (subagent)
        gộp 3 phần -> __________ + __________
                            ▼
              Đầu ra cuối: ________________
```

Đánh dấu chỗ nào BẮT BUỘC tuần tự (không song song): bước gộp (4-5) phải đợi cả 3 agent xong,
vì nó tổng hợp kết quả của cả ba.

---

## Phần B: Chạy dây chuyền từng bước

### B1. Kiểm đồ nghề trước khi chạy
Gõ lệnh này vào Claude Code để chắc mọi thứ sẵn sàng:
```
Liệt kê giúp tôi: các skill đang có trong thư mục này, các subagent đã định nghĩa, và xác nhận MCP đọc file đang chạy được. Rồi đọc thử file dữ liệu của tôi và cho tôi biết có bao nhiêu dòng.
```
- [ ] Agent liệt kê đúng skill tóm tắt tài liệu
- [ ] Agent liệt kê đúng 2 subagent (report, research)
- [ ] MCP đọc file chạy được, đọc đúng số dòng dữ liệu
- [ ] Nếu thiếu thứ nào, dựng lại từ mẫu trước khi đi tiếp

### B2. Bỏ file vào đúng thư mục con
- [ ] Tạo thư mục dự án và các thư mục con cho từng agent (mỗi agent một thư mục riêng).
- [ ] Bỏ file dữ liệu thật vào đúng thư mục con của nó.
- [ ] Kiểm: không có file nào để lẫn giữa hai thư mục (tránh agent giẫm chân nhau).

### B3. Chạy lệnh tổng
- [ ] Viết lệnh tổng theo mẫu ở Phần C.
- [ ] Chạy, xem agent chia việc cho team và ghép lại.
- [ ] Ra đủ các đầu mục mình cần chưa? Ghi lại đầu mục nào còn thiếu: __________

### B4. Kiểm số liệu và soi văn bản gửi đi
Gõ lệnh này để kiểm sau khi chạy:
```
Đối chiếu giúp tôi: các con số trong phần đề xuất và email có khớp với phần phân tích số liệu không? Nếu lệch, chỉ ra chỗ lệch. Đồng thời rà email xem có emoji nào không, nếu có thì bỏ hết.
```
- [ ] Số liệu ở phần cuối khớp với phần phân tích
- [ ] Email/báo cáo gửi đi không có emoji
- [ ] Văn phong công sở, đọc lên nghe được

---

## Phần C: Prompt tổng để copy

### C1. Mẫu lệnh tổng (điền vào chỗ trong ngoặc)
```
Tôi cần [tên bộ kết quả cuối]. Dữ liệu nằm trong thư mục [tên thư mục] gồm các thư mục con: [liệt kê].

Hãy điều phối agent team chạy SONG SONG, mỗi agent chỉ đọc thư mục của mình:
- Agent 1: đọc [thư mục], [việc cần làm], dùng skill [tên skill nếu có].
- Agent 2: đọc [thư mục], [việc cần làm].
- Agent 3: đọc [thư mục], [việc cần làm], dùng MCP đọc file [tên file dữ liệu].

Sau khi cả ba xong, kiểm số liệu khớp nhau, rồi giao cho report-agent gộp thành:
- [Đầu mục 4, ví dụ: một đề xuất / kế hoạch].
- [Đầu mục 5, ví dụ: một email hoặc báo cáo gửi cấp trên, văn phong công sở, KHÔNG emoji].

Xuất đủ các đầu mục, đánh số rõ ràng.
```

### C2. Lệnh tổng đầy đủ cho đề mẫu (chạy được ngay nếu dùng thư mục demo)
```
Tôi cần một bộ tài liệu ra mắt sản phẩm "Gói Cao cấp Plus" hoàn chỉnh. Dữ liệu nằm trong thư mục du-an-ra-mat-san-pham/ gồm 3 thư mục con: thi-truong/, doi-thu/, so-lieu/.

Hãy điều phối một agent team chạy SONG SONG, mỗi agent chỉ đọc thư mục của mình:
- Agent 1: đọc thi-truong/, dùng skill tóm tắt tài liệu để ra bản tóm tắt bối cảnh thị trường và cơ hội.
- Agent 2: đọc doi-thu/, lập bảng so sánh đối thủ và nêu điểm khác biệt của sản phẩm.
- Agent 3: đọc so-lieu/, dùng MCP đọc file CSV để phân tích doanh thu, số đơn và xu hướng theo tháng.

Sau khi cả ba xong, kiểm tra số liệu giữa các phần có khớp nhau không, rồi giao cho report-agent gộp thành:
4. Một đề xuất kế hoạch ra mắt: thông điệp chính, giá đề xuất, kênh bán.
5. Một email ngắn gửi sếp trình bày tóm tắt kế hoạch, văn phong công sở, KHÔNG dùng emoji.

Xuất ra đủ 5 đầu mục, đánh số rõ ràng.
```

---

## Phần D: Rubric tự chấm capstone
Tự tích. Đủ hết là capstone của bạn đạt.

| # | Tiêu chí | Đạt? |
|---|---|---|
| 1 | Quy trình chạy đầu-cuối bằng MỘT lệnh tổng (không dắt từng bước) | [ ] |
| 2 | Ra đủ các đầu mục đã định nghĩa (đề mẫu: đủ 5 đầu mục) | [ ] |
| 3 | Agent team chạy song song, mỗi agent một thư mục riêng | [ ] |
| 4 | Có dùng ít nhất 1 skill trong dây chuyền | [ ] |
| 5 | Có dùng ít nhất 1 MCP để đọc dữ liệu | [ ] |
| 6 | Report agent gộp kết quả thành văn bản hoàn chỉnh | [ ] |
| 7 | Số liệu nhất quán giữa các phần | [ ] |
| 8 | Văn bản gửi đi không emoji, đúng văn phong công sở | [ ] |
| 9 | Tôi chỉ ra được dùng agent / skill / MCP / subagent / team ở đâu | [ ] |

Nếu có ô chưa đạt, ghi lại cần sửa gì: __________________________________

---

## Phần E: 5 nhóm nghề gợi ý workflow
Chưa biết chọn quy trình gì? Lấy ý từ nghề gần bạn nhất.

| Nghề | Quy trình gợi ý (chạy bằng 1 lệnh tổng) |
|---|---|
| **Sale** | Agent 1 đọc hồ sơ khách + ghi chú (skill tóm tắt); Agent 2 đọc lịch sử mua/tương tác; Agent 3 đọc bảng giá + số liệu đơn cũ (MCP đọc CSV). Report agent gộp thành: đề xuất chào giá + email gửi khách (không emoji). |
| **Kế toán** | Agent 1 đọc chứng từ/hóa đơn (skill tóm tắt); Agent 2 đọc ghi chú công nợ; Agent 3 đọc file số liệu thu chi (MCP đọc CSV). Report agent gộp thành: báo cáo thu chi tuần + email nhắc công nợ gửi cấp trên (không emoji). |
| **Marketing** | Agent 1 đọc tài liệu chiến dịch (skill tóm tắt); Agent 2 đọc ghi chú đối thủ/thị trường; Agent 3 đọc số liệu quảng cáo (MCP đọc CSV). Report agent gộp thành: đề xuất kế hoạch nội dung + báo cáo hiệu quả gửi sếp (không emoji). |
| **Quản lý** | Agent 1 đọc báo cáo từng nhân viên (skill tóm tắt); Agent 2 đọc ghi chú vướng mắc/tồn đọng; Agent 3 đọc số liệu tiến độ/KPI (MCP đọc CSV). Report agent gộp thành: báo cáo tuần của phòng + email cập nhật gửi ban giám đốc (không emoji). |
| **Chủ DN nhỏ** | Agent 1 đọc phản hồi khách (skill tóm tắt); Agent 2 đọc ghi chú vận hành/nhân sự; Agent 3 đọc số liệu doanh thu (MCP đọc CSV). Report agent gộp thành: bức tranh tuần của cửa hàng + đề xuất việc cần làm tuần tới. |

---

## Phần F: Checklist "tôi đã có gì sau cả khóa"
Tích lại. Đây là những thứ bạn cầm về, dùng được ngay sau khóa.

- [ ] **Agent:** Claude Code chạy trên máy tôi, có thư mục dự án + CLAUDE.md của riêng tôi (buổi 1).
- [ ] **Skill:** ít nhất 1 skill tự tạo cho một quy trình lặp lại của tôi (buổi 2).
- [ ] **MCP:** ít nhất 1 MCP đã cắm và cho agent đọc dữ liệu ngoài (buổi 3).
- [ ] **Subagent:** 2 agent chuyên trách Report và Research, giao việc được (buổi 4).
- [ ] **Agent Team:** biết cho nhiều agent chạy song song, lead chia việc và ghép kết quả (buổi 5).
- [ ] **Capstone:** 1 quy trình công việc thật chạy đầu-cuối bằng một lệnh tổng, ghép cả 5 thứ trên (buổi 6).

Nói lại được 5 khái niệm bằng lời của mình:
- Agent là: __________________________________
- Skill là: __________________________________
- MCP là: __________________________________
- Subagent là: __________________________________
- Agent Team là: __________________________________

---

## Học gì tiếp theo sau khóa
- Đào sâu agent team nhiều phiên (lead + teammate ở các phiên riêng) cho việc lớn kéo dài.
- Cắm thêm MCP theo nghề: Google Drive, cơ sở dữ liệu công ty, công cụ web, khi được cấp quyền.
- Xây dần một thư viện skill cá nhân cho mọi việc lặp lại.
- Đưa CLAUDE.md và bộ skill vào dùng chung cho cả phòng ban, để cả nhóm cùng một chuẩn.
- Kênh hỗ trợ sau khóa: nhóm Zalo lớp và LMS VIP để hỏi tiếp khi vướng.

> Điều lớn nhất bạn mang về không phải một công cụ, mà một thói quen: mỗi việc lặp lại,
> thay vì làm tay nhiều bước, bạn gói thành một lệnh. Chúc mừng bạn đã hoàn thành khóa.
