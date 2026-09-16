# Giáo án Buổi 05: Lập Đội Ngũ Multi-Agent, Phối Hợp Nối Chuỗi & Song Song, Đánh Giá Chi Phí Chuẩn Anthropic

> **Mục tiêu chiến lược Buổi 05:**
> 1. **Lập Agent bài bản:** Tự tay tạo 2 Agent chuyên trách (`agent-soan-bao-cao` và `agent-ra-soat-khach`) lưu tại `.claude/agents/*.md`, hiểu sâu sắc cách dùng `tools` để khoanh vùng quyền hạn (Write vs Read-only).
> 2. **Hiểu rõ khi nào nhiều Agent tốt hơn 1 Agent (3 tình huống chuẩn Anthropic):**
>    - (1) Tránh ô nhiễm Context (Context Pollution);
>    - (2) Chạy song song độc lập (Parallelization);
>    - (3) Chuyên môn hóa công cụ (Specialization).
>    - *Cảnh báo từ Anthropic:* Ngoài 3 tình huống này, chi phí điều phối thường vượt lợi ích! Luôn ưu tiên giải pháp đơn giản nhất (KISS).
> 3. **Hai mô hình phối hợp Đội ngũ Agent (Multi-Agent Team):**
>    - Mô hình Nối chuỗi (Tuần tự / Sequential): Agent A ra kết quả làm đầu vào cho Agent B.
>    - Mô hình Chạy song song (Parallel): Nhiều Agent chạy độc lập cùng lúc gom kết quả.
> 4. **Bài toán Chi phí Token & Hiệu quả Đột phá:**
>    - Tỷ lệ tiêu hao token: Chat (1x) $\rightarrow$ Agent đơn (~4x) $\rightarrow$ Multi-agent (~15x).
>    - Benchmark Anthropic: Hệ Multi-Agent (Opus 4 + Sonnet 4) vượt Agent đơn Opus 4 tới **90.2%** trong đánh giá nghiên cứu phức tạp.

---

## Thông tin buổi học
- **Buổi:** 05 / 6 (Theo lộ trình khóa AI Workspace 6 Agent)
- **Thời lượng:** 150 phút (2,5 giờ)
- **Đối tượng:** Khối văn phòng, kinh doanh, nhân sự, kế toán, quản lý (đã nắm chắc Buổi 4 về Subagent và Context Window).
- **Bộ file demo làm việc:** 
  * `04-buoi-04-lap-bao-cao-va-slide/demo/so-lieu-ban-hang-thang.md` (số liệu bán hàng tháng 3 thô).
  * `03-buoi-03-phan-tich-du-lieu-mcp-routine/demo/phong-kinh-doanh-mau/01-khach-hang/` (3 hồ sơ khách: Minh Long, Hải Nam, An Phát).
  * `04-buoi-04-lap-bao-cao-va-slide/demo/yeu-cau-nghien-cuu.md` (đề bài nghiên cứu thị trường).
- **Tài liệu nghiên cứu tham chiếu:**
  * Anthropic Research: *Building Effective Agents* (anthropic.com/engineering/building-effective-agents)
  * Anthropic Engineering: *When to use multi-agent systems* (claude.com/blog/building-multi-agent-systems-when-and-how-to-use-them)

---

## Timeline chi tiết buổi học (150 phút)

| Mốc thời gian | Thời lượng | Khối nội dung | Trọng tâm sư phạm & Sản phẩm đầu ra |
|---|---|---|---|
| **00:00 - 00:10** | 10 phút | **K0: Mở đầu & Bản đồ Buổi 5** | Nối mạch từ Subagent đơn lẻ (Buổi 4) sang bài toán Đội ngũ Multi-Agent. |
| **00:10 - 00:35** | 25 phút | **K1: Khi nào cần Multi-Agent & Bài toán Chi phí** | 3 tình huống Anthropic chỉ ra; chi phí 1x - 4x - 15x; nguyên tắc KISS; khoanh vùng `tools`. |
| **00:35 - 01:05** | 30 phút | **K2: Tự tay tạo 2 Agent chuyên trách** | Lập `agent-soan-bao-cao` (có Write) và `agent-ra-soat-khach` (chỉ Read); giải thích cấu trúc YAML. |
| **01:05 - 01:15** | 10 phút | **Nghỉ giải lao** | Trợ giảng hỗ trợ học viên kiểm tra cú pháp file trong `.claude/agents/`. |
| **01:15 - 01:45** | 30 phút | **K3: Gọi, Test & Thử thách An toàn** | Mở phiên mới, gọi từng agent; test thử thách cấp quyền (agent không có Write không thể sửa file). |
| **01:45 - 02:15** | 30 phút | **K4: Đội ngũ Nối chuỗi (Tuần tự)** | Rà soát khách $\rightarrow$ File trung gian $\rightarrow$ Soạn email nhắc nợ tự động; điều phối dạng dây chuyền. |
| **02:15 - 02:30** | 15 phút | **K5: Đội ngũ Song song & Tổng kết** | Chạy song song 2 việc độc lập; quy tắc ngón tay cái; giao bài tập chuẩn bị Capstone Buổi 6. |

---

## Kịch bản chi tiết từng phần

```
================================================================================
K0: MỞ ĐẦU & BẢN ĐỒ BUỔI 5 (10 PHÚT)
================================================================================
```

### Lời dẫn Giảng viên (Đọc nguyên văn):
> "Chào cả lớp. Ở Buổi 4, chúng ta đã hiểu sâu sắc về ranh giới Context của Subagent đơn lẻ: Subagent giống như một nhân viên thời vụ được giao việc qua một tờ giấy, làm ở phòng riêng để không làm bẩn bàn làm việc chính.
> 
> Nhưng trong thực tế doanh nghiệp, một công việc không chỉ do một người làm. Chúng ta cần cả một **ĐỘI NGŨ AGENT (Multi-Agent Team)** cùng phối hợp: một nhân viên chuyên rà soát số liệu, một nhân viên chuyên viết báo cáo, một nhân viên chuyên nghiên cứu thị trường.
> 
> Tuy nhiên, tài liệu nghiên cứu chính thức của Anthropic cảnh báo rất rõ: **Hệ thống nhiều Agent tốn token gấp 15 lần so với chat thông thường!** Rất nhiều đội kỹ thuật mất hàng tháng trời xây dựng hệ thống multi-agent phức tạp rồi phát hiện chỉ cần 1 prompt tốt cho 1 agent đơn lẻ là xong việc.
> 
> Tối nay, chúng ta sẽ học cách làm của các chuyên gia hàng đầu thế giới:
> 1. Nắm chắc **3 tình huống duy nhất** mà nhiều Agent thực sự vượt trội hơn 1 Agent.
> 2. Tự tay lập trình 2 nhân viên AI biên chế chính thức.
> 3. Điều phối 2 nhân viên này làm việc theo mô hình **Nối chuỗi (dây chuyền)** và **Chạy song song**, tạo ra năng suất vượt trội mà vẫn tối ưu chi phí. Bắt đầu thôi!"

---

```
================================================================================
K1: KHI NÀO CẦN MULTI-AGENT & BÀI TOÁN CHI PHÍ (25 PHÚT)
================================================================================
```

### 1. Ba tình huống duy nhất nhiều Agent tốt hơn một Agent (Theo Anthropic)

Anthropic chỉ ra rằng, hệ thống Multi-Agent chỉ thực sự phát huy tác dụng khi:
1. **Context bị "ô nhiễm" (Context Pollution):** Khi dữ liệu của bước trước quá nhiều rác hoặc chi tiết thừa thãi làm giảm khả năng suy luận chính xác của các bước tiếp theo. Tách sang Agent/Subagent khác giúp context luôn trong sạch.
2. **Công việc có thể chạy song song (Parallelization):** Khi các phần việc hoàn toàn độc lập (ví dụ: nghiên cứu đồng thời 3 đối thủ khác nhau, hoặc rà soát 3 chi nhánh cùng lúc). Chạy song song giúp tiết kiệm thời gian đáng kể.
3. **Chuyên môn hóa (Specialization):** Khi cần giới hạn công cụ hoặc tập trung sâu (ví dụ: Agent kiểm tra chỉ được cấp quyền Đọc - Read-only để đảm bảo an toàn dữ liệu; còn Agent viết báo cáo mới được cấp quyền Ghi - Write).

> ⚠️ **Cảnh báo từ Anthropic:** Ngoài 3 tình huống trên, chi phí điều phối thường vượt quá lợi ích! Luôn tuân thủ nguyên tắc **KISS (Keep It Simple, Stupid)** — chỉ tăng độ phức tạp khi thực sự cần thiết.

### 2. Bài toán Chi phí Token & Hiệu quả Đột phá
- **Mức tiêu hao Token:**
  * Chat thông thường: **1x** token.
  * Agent đơn lẻ (tự chạy vòng lặp tools): **~4x** token.
  * Hệ thống Đội ngũ Multi-Agent: **~15x** token!
- **Khi nào đáng đầu tư chi phí gấp 15 lần?**
  * Khi giá trị nhiệm vụ đủ cao (bài toán nghiên cứu thị trường chiến lược, đối soát tài chính quan trọng, kiểm thử an ninh).
  * **Benchmark Anthropic:** Hệ thống nghiên cứu kết hợp giữa mô hình điều phối Opus 4 và các subagent Sonnet 4 đã **vượt trội hơn Agent đơn Opus 4 tới 90.2%** trong các đánh giá nghiên cứu thông tin phức tạp!

---

```
================================================================================
K2: TỰ TAY TẠO 2 AGENT BIÊN CHẾ CHUYÊN TRÁCH (30 PHÚT)
================================================================================
```

### 1. Cấu trúc file định nghĩa Agent chuẩn trong `.claude/agents/*.md`
File Agent gồm 2 phần:
- **Khối YAML Frontmatter:** Khai báo `name` (tên gọi), `description` (giúp hệ thống nhận diện khi nào kích hoạt), `tools` (khoanh vùng công cụ được phép dùng).
- **Phần thân:** Bản mô tả công việc (JD) chi tiết và các nguyên tắc bất khả xâm phạm.

### 2. Demo GV tạo Agent 1: `agent-soan-bao-cao` (Có quyền `Write`)
- **PROMPT K2-1 (Bản GV dán chạy ngay):**
  ```text
  Tạo cho tôi file .claude/agents/agent-soan-bao-cao.md, một agent chuyên soạn báo cáo và email công việc:
  - name: agent-soan-bao-cao
  - description: Chuyên biến số liệu hoặc ý thô thành báo cáo, đề xuất, email hoàn chỉnh theo văn phong công sở. Dùng khi cần soạn văn bản công việc từ dữ liệu có sẵn.
  - tools: Read, Write, Grep, Glob
  - Phần thân: Bạn là chuyên viên soạn thảo văn bản tại Công ty Cổ phần Công nghệ CES. Nhiệm vụ: Đọc dữ liệu được chỉ định, soạn thảo văn bản theo đúng yêu cầu. Quy tắc: Tiếng Việt chuẩn công sở, TUYỆT ĐỐI KHÔNG DÙNG EMOJI, CHỐNG BỊA SỐ (số liệu phải trích dẫn nguồn, thiếu ghi [Chờ bổ sung]). Nếu thiếu thông tin, vẫn soạn đầy đủ khung và để trống chỗ thiếu, không dừng lại hỏi giữa chừng.
  Tạo xong in lại toàn bộ nội dung file.
  ```

### 3. Demo GV tạo Agent 2: `agent-ra-soat-khach` (Chỉ có quyền `Read`, KHÔNG CÓ `Write`)
- **PROMPT K2-2 (Bản GV dán chạy ngay):**
  ```text
  Tạo cho tôi file .claude/agents/agent-ra-soat-khach.md, một agent chuyên rà soát hồ sơ khách hàng:
  - name: agent-ra-soat-khach
  - description: Chuyên đọc hồ sơ khách hàng và chỉ ra khách nào cần hành động (nhắc thanh toán, chăm sóc lại, chốt gia hạn). Dùng khi cần rà nhanh danh sách khách để không bỏ sót việc.
  - tools: Read, Grep, Glob
  - Phần thân: Bạn là chuyên viên kiểm tra và đối soát khách hàng. Nhiệm vụ: Đọc toàn bộ hồ sơ khách trong thư mục được chỉ định, trả về một bảng tổng hợp: Tên khách, Trạng thái, Việc cần làm, Mức ưu tiên. Quy tắc: Chỉ dùng thông tin có thật trong hồ sơ, không suy đoán. TUYỆT ĐỐI KHÔNG TỰ Ý SỬA HAY TẠO FILE, CHỈ BÁO CÁO KẾT QUẢ.
  Tạo xong in lại toàn bộ nội dung file.
  ```

- **Thao tác quan trọng:** Sau khi tạo xong 2 file, **BẮT BUỘC ĐÓNG PHIÊN VÀ MỞ PHIÊN MỚI** để Claude Code nạp 2 Agent vào hệ thống.

---

```
================================================================================
NGHỈ GIẢI LAO (10 PHÚT) — 01:05 ĐẾN 01:15
================================================================================
```

---

```
================================================================================
K3: GỌI, TEST & THỬ THÁCH AN TOÀN KHOANH VÙNG CÔNG CỤ (30 PHÚT)
================================================================================
```

### 1. Test Agent 1: Soạn Báo cáo bán hàng tháng 3
- **PROMPT K3-1 (Mở phiên mới rồi gọi):**
  ```text
  Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3 từ file 04-buoi-04-lap-bao-cao-va-slide/demo/so-lieu-ban-hang-thang.md. 
  Bố cục gồm: Kết quả tổng quan tháng 3, Số liệu chi tiết theo khu vực, Vướng mắc tồn đọng, Kế hoạch tháng 4. 
  Quy tắc: Không emoji, cuối báo cáo liệt kê rõ các con số đã dùng kèm dòng trích dẫn từ file nguồn.
  ```
- **Kết quả mong đợi:** Báo cáo xuất sắc, không emoji, trích dẫn chuẩn: 1.085 triệu tháng 3, 915 triệu tháng 2, 2 đơn chờ thanh toán, 1 đơn hủy.

### 2. Test Agent 2: Rà soát danh sách khách hàng
- **PROMPT K3-2:**
  ```text
  Nhờ agent-ra-soat-khach đọc toàn bộ các hồ sơ trong 03-buoi-03-phan-tich-du-lieu-mcp-routine/demo/phong-kinh-doanh-mau/01-khach-hang/ và chỉ ra những khách hàng nào cần hành động gấp, xếp theo mức ưu tiên.
  ```
- **Kết quả mong đợi:** Bảng đối soát: An Phát cần nhắc nợ gấp (ưu tiên 1), Hải Nam cần chăm sóc lại sau khi hủy (ưu tiên 2), Minh Long cần chốt gia hạn (ưu tiên 3).

### 3. Thử thách an toàn: Thử bắt Agent làm việc ngoài quyền hạn (Khoảnh khắc đắt giá)
- **PROMPT K3-3:**
  ```text
  Nhờ agent-ra-soat-khach cập nhật file hồ sơ khách An Phát, ghi thêm dòng: "Đã liên hệ nhắc nợ lần 3 ngày hôm nay".
  ```
- **KẾT QUẢ MONG ĐỢI & BÀI HỌC SƯ PHẠM:**
  * Agent báo lỗi hoặc từ chối: *"Tôi không có quyền Write (ghi file), tôi chỉ có quyền Read để rà soát"*.
  * GV chỉ tay lên màn hình: *"Cả lớp thấy sức mạnh của việc khoanh vùng `tools` chưa? Dù anh chị có ra lệnh hay nài nỉ, Agent cũng không thể phá hoại hay sửa file vì hệ thống đã chặn quyền ngay từ file cấu hình. Đây chính là chuẩn mực an toàn thông tin doanh nghiệp!"*

---

```
================================================================================
K4: ĐỘI NGŨ AGENT NỐI CHUỖI (TUẦN TỰ / SEQUENTIAL) (30 PHÚT)
================================================================================
```

### 1. Bản chất mô hình Nối chuỗi (Dây chuyền sản xuất)
- **Quy tắc:** Việc sau **phải chờ** kết quả của việc trước thì làm Nối chuỗi.
- **Kỹ thuật điều phối:** 
  1. Chỉ định rõ thứ tự: *"Làm lần lượt 2 bước, xong bước 1 mới sang bước 2"*.
  2. Bắt buộc có **File trung gian** để Agent A lưu kết quả ra, và Agent B đọc vào.

### 2. Demo GV: Dây chuyền rà soát nợ $\rightarrow$ Soạn email nhắc nợ tự động
- **PROMPT K4-1 (Bản GV dán chạy ngay):**
  ```text
  Làm lần lượt hai bước theo quy trình nối chuỗi, xong bước 1 mới sang bước 2:
  - Bước 1: Nhờ agent-ra-soat-khach đọc thư mục 03-buoi-03-phan-tich-du-lieu-mcp-routine/demo/phong-kinh-doanh-mau/01-khach-hang/, tìm ra khách hàng CẦN NHẮC THANH TOÁN GẤP NHẤT, lưu kết quả vào file ket-qua/khach-can-nhac.md.
  - Bước 2: Sau khi có file đó, nhờ agent-soan-bao-cao đọc file ket-qua/khach-can-nhac.md và soạn một email nhắc thanh toán gửi đúng khách hàng đó, văn phong công sở lịch sự, tôn trọng đối tác, không dùng emoji.
  ```
- **Kết quả mong đợi:** File `ket-qua/khach-can-nhac.md` được tạo ra (chỉ đích danh An Phát), sau đó email gửi An Phát được soạn thảo hoàn chỉnh. Hai Agent phối hợp như 2 nhân viên trong một phòng ban thực thụ!

---

```
================================================================================
K5: ĐỘI NGŨ AGENT CHẠY SONG SONG (PARALLELIZATION) & TỔNG KẾT (15 PHÚT)
================================================================================
```

### 1. Bản chất mô hình Chạy song song
- **Quy tắc:** Các việc **hoàn toàn độc lập**, không phụ thuộc dữ liệu của nhau thì cho chạy song song để tiết kiệm thời gian.
- **PROMPT K5-1 (Demo GV chạy song song):**
  ```text
  Giao SONG SONG hai việc độc lập cùng lúc, không tự làm thay:
  1. agent-ra-soat-khach: Rà soát thư mục 01-khach-hang, chỉ ra khách hàng cần hành động.
  2. agent-soan-bao-cao: Soạn tóm tắt kết quả bán hàng từ demo/so-lieu-ban-hang-thang.md.
  Sau khi cả hai hoàn thành, gom kết quả thành một bản Báo cáo Tổng hợp Tình hình chung.
  ```

### 2. Tổng kết & Câu chốt cốt lõi:
1. **Ba tình huống dùng Multi-Agent:** Tránh ô nhiễm context, cần chạy song song, chuyên môn hóa công cụ an toàn.
2. **Chi phí token:** Đội ngũ Multi-Agent ngốn token gấp 15 lần chat thường; chỉ dùng cho việc có giá trị cao.
3. **Quy tắc phối hợp:** Chờ nhau $\rightarrow$ Nối chuỗi; Độc lập $\rightarrow$ Song song.

### 3. Bài tập về nhà:
- Tự cấu hình 2 Agent riêng theo phòng ban thực tế của bạn (1 Agent chỉ Read, 1 Agent có Write).
- Thiết lập một kịch bản Nối chuỗi giữa 2 Agent đó trên dữ liệu công việc thật của bạn.
- Chuẩn bị dữ liệu cho **Buổi 06 (Capstone Project)**: Đưa toàn bộ Workspace vào vận hành thực tế cuối khóa.

---

## Bảng tra cứu nhanh các Prompt của Buổi 5

| Mã Prompt | Mục đích sử dụng | Vị trí trong bài | Kết quả kiểm định mong đợi |
|---|---|---|---|
| **K2-1** | Tạo `agent-soan-bao-cao` (có quyền `Write`) | [K2: 00:35 - 01:05] | File agent hoàn chỉnh trong `.claude/agents/` |
| **K2-2** | Tạo `agent-ra-soat-khach` (chỉ quyền `Read`) | [K2: 00:35 - 01:05] | File agent chỉ có Read/Grep/Glob, không có Write |
| **K3-1** | Gọi test `agent-soan-bao-cao` | [K3: 01:15 - 01:45] | Xuất báo cáo 4 phần, chuẩn số liệu, không emoji |
| **K3-2** | Gọi test `agent-ra-soat-khach` | [K3: 01:15 - 01:45] | Bảng đối soát 3 khách hàng theo mức ưu tiên |
| **K3-3** | Thử thách an toàn (bắt agent sửa file) | [K3: 01:15 - 01:45] | Agent từ chối sửa file vì không có quyền Write |
| **K4-1** | Nối chuỗi: Rà soát khách $\rightarrow$ Soạn email nhắc | [K4: 01:45 - 02:15] | Tự động sinh file trung gian và email đúng khách |
| **K5-1** | Chạy song song 2 Agent gom kết quả chung | [K5: 02:15 - 02:30] | Hai phần việc chạy độc lập gom vào 1 báo cáo |
