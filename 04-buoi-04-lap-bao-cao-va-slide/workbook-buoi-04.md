# Workbook Buổi 04: Hoàn Thiện Slide, Connectors, Routine & Subagent Chuẩn Anthropic

> **Sổ tay thực hành dành cho Học viên Khóa AI Workspace (CES Global).**
> Cẩm nang thực hành dựa trên tài liệu nghiên cứu chính thức của Anthropic (*Building Effective Agents*).

---

## 1. Bản Đồ Năng Lực Buổi 04

Sau buổi học này, bạn sẽ nắm trọn vẹn:
1. **MCP `chatgpt-image-mcp`**: Tự động vẽ ảnh infographic, sơ đồ quy trình tiếng Việt sắc nét nhúng thẳng vào Slide và Báo cáo.
2. **Bản chất Connectors & MCP**: Hiểu rõ khi nào cần MCP (ra ngoài máy) và khi nào không cần (đọc file trong máy), cùng **3 luật thép bảo mật** (chỉ đọc, không cho AI tự gửi, chống Injection).
3. **Routine**: "Hẹn giờ nồi cơm điện" cho Agent — Khung 4 câu hỏi tự động hóa tác vụ định kỳ mỗi sáng thứ Hai.
4. **Giải mã Subagent chuẩn Anthropic**:
   - Hiểu **Ranh giới Context (Context Boundary)**: Subagent có context hoàn toàn mới, cách ly 100% với phiên chính.
   - Nắm vững ẩn dụ **"Trưởng phòng & Tờ giấy giao việc"**: Kênh duy nhất sang Subagent là đoạn prompt giao việc; chiều ngược lại chỉ có kết quả cuối cùng được nộp về.
   - Nhớ **2 giới hạn cứng**: Subagent không thể đẻ subagent khác; Subagent không thể hỏi lại người dùng giữa chừng.
   - Thuộc lòng **quy tắc ngón tay cái**: *"Đi tìm X rồi báo tôi đáp án"* $\rightarrow$ Giao Subagent. Việc cần trao đổi qua lại hoặc duyệt sửa file $\rightarrow$ Giữ ở Agent chính.

---

## 2. Bảng Phân Biệt: Khi Nào Dùng Subagent vs Giữ Ở Agent Chính

| Tiêu chí | DÙNG SUBAGENT | GIỮ Ở AGENT CHÍNH |
|---|---|---|
| **Bản chất công việc** | Tìm kiếm rộng, điều tra, đọc quét, tóm tắt dữ liệu thô | Cần trao đổi qua lại, nhiều bước phụ thuộc nhau |
| **Đặc điểm dữ liệu** | **Output lớn nhưng kết luận nhỏ** (đọc 20 file chỉ lấy 1 bảng) | Cần cập nhật bối cảnh liên tục |
| **Tương tác người dùng** | Độc lập 100%, không cần hỏi lại người dùng | Cần bạn ra quyết định giữa chừng |
| **Quyền hạn thao tác** | Chỉ đọc, phân tích, trích xuất (Read-only) | Thao tác sửa file thực tế, chạy code cần bạn phê duyệt |
| **Mục đích then chốt** | **Chống ô nhiễm Context (Context Pollution)** cho phiên chính | Giữ mạch hội thoại thông suốt |

---

## 3. Quy Tắc Ngón Tay Cái Của Anthropic (Học Thuộc Lòng)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ "Nếu mô tả được việc là: 'ĐI TÌM X RỒI BÁO TÔI ĐÁP ÁN' ──> DÙNG SUBAGENT.   │
│  Không cần sửa gì, không cần quyết định giữa chừng.                         │
│  Việc gắn chặt, cần lặp lại, cần duyệt sửa ─────────────> AGENT CHÍNH."     │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## PHẦN B: Thực Hành Từng Bước (Copy dán vào Claude Code)

### Bước 1: Kiểm tra công cụ tạo ảnh MCP Image
```text
Kiểm tra giúp tôi công cụ tạo ảnh chatgpt-image đã sẵn sàng hoạt động chưa?
```

### Bước 2: Tạo Infographic sơ đồ quy trình chèn Slide
```text
Sử dụng công cụ chatgpt-image để tạo cho tôi một hình ảnh đồ họa infographic chuyên nghiệp minh họa: "Quy trình 4 bước chăm sóc khách hàng và thu hồi công nợ chuẩn B2B":
- Bước 1: Tư vấn giải pháp & Ký kết hợp đồng
- Bước 2: Bàn giao phần mềm & Nghiệm thu đợt 1
- Bước 3: Đối soát công nợ & Gửi thông báo thanh toán
- Bước 4: Chăm sóc sau bán & Mở rộng gói dịch vụ

Yêu cầu phong cách: Đồ họa vector phẳng hiện đại, nền trắng sạch sẽ, tông màu xanh dương công nghệ cao cấp, các nhãn chữ tiếng Việt hiển thị rõ ràng, sắc nét có dấu.
Tỉ lệ ảnh 16:9. Lưu ảnh vào thư mục 05-bao-cao/ theo đúng Super Rule tự động đánh số thứ tự tuần tự (ví dụ: 03_so-do-quy-trinh-b2b.png).
```

### Bước 3: Chèn ảnh vào slide thuyết trình đã làm ở Buổi 3
```text
Hãy chèn hình ảnh vừa tạo vào slide cuối cùng của file bài thuyết trình trong thư mục báo cáo.
```

### Bước 4: Soạn nháp email an toàn theo Luật "Chỉ Đọc & Không Tự Gửi"
```text
Dựa trên thông tin công nợ trong demo/md/so-lieu-ban-hang-thang.md:
Khách hàng Công ty An Phát đang có đơn hàng chờ thanh toán kéo dài.
Hãy soạn giúp tôi một bản nháp email chuyên nghiệp gửi chị Kế toán trưởng bên An Phát:
- Mục đích: Nhắc nhở lịch đối soát và đề nghị hoàn tất thanh toán trước ngày 05/04.
- Văn phong: Nhã nhặn, tôn trọng quan hệ đối tác, rõ ràng thời hạn.
- Ký tên: [Họ và tên của bạn] - Phòng Kinh doanh.

LƯU Ý BẢO MẬT: CHỈ xuất bản nháp ra màn hình để tôi duyệt. Tuyệt đối KHÔNG tự ý gửi email hay tương tác với hệ thống gửi thư.
```

### Bước 5: Cài đặt Routine tự động hóa 4 câu hỏi
```text
Hãy thiết lập cho tôi một Routine tự động hóa theo đúng khung 4 câu hỏi:
1. Lịch chạy: Vào lúc 08:00 sáng thứ Hai hàng tuần.
2. Nguồn dữ liệu: Đọc file demo/md/so-lieu-ban-hang-thang.md (hoặc demo/pdf/so-lieu-ban-hang-thang-3.pdf).
3. Xử lý: Lọc các đơn hàng chờ thanh toán và khách hủy đơn, tính tổng doanh thu và tỷ lệ tăng trưởng so với tháng trước.
4. Đầu ra: Lưu thành file markdown trong thư mục 05-bao-cao/ theo đúng quy tắc đánh số tự động của Global CLAUDE.md.
Ràng buộc an toàn: Chỉ đọc và lưu báo cáo nội bộ, không gửi email, không chỉnh sửa file nguồn.
```

### Bước 6: Gọi Subagent quét 5 hồ sơ CV (Áp dụng "Tờ giấy giao việc")
```text
Dùng một subagent đọc toàn bộ 5 file hồ sơ ứng viên trong thư mục demo/pdf/01-ung-vien/ (hoặc demo/md/01-ung-vien/).
Yêu cầu subagent:
1. Đánh giá từng ứng viên dựa trên tiêu chí tuyển dụng: Vị trí Nhân viên giao vận Hà Nội (cần người trực tiếp đi xe máy giao hàng nội thành, cẩn thận, có kinh nghiệm thực địa, mức lương dưới 12 triệu).
2. Trả về đúng 1 bảng tổng hợp gồm các cột: Tên ứng viên, Năm sinh, Kinh nghiệm chính, Mức lương kỳ vọng, Đánh giá (Phù hợp / Không phù hợp) và Lý do ngắn gọn.
3. Đề xuất chọn ra 2 ứng viên sáng giá nhất để mời phỏng vấn vòng 1.

QUY TẮC BẮT BUỘC: Chỉ trả về bảng tổng hợp và đề xuất ngắn gọn. Tuyệt đối không đổ nguyên văn nội dung từng file CV vào cuộc trò chuyện chính.
```
> 💡 *Mẹo thực hành:* Bạn có thể chỉ định đọc 5 file `.pdf` (`demo/pdf/01-ung-vien/*.pdf`) hoặc 5 file `.md` (`demo/md/01-ung-vien/*.md`). Thư mục đã phân tách rạch ròi 2 định dạng `demo/pdf/` và `demo/md/` để bạn dễ dàng thực hành cả 2 kịch bản!

### Bước 7: Agent chính xuất Báo cáo kinh doanh chuẩn công sở
```text
Dựa trên số liệu bán hàng trong demo/md/so-lieu-ban-hang-thang.md (hoặc demo/pdf/so-lieu-ban-hang-thang-3.pdf) và kết quả sàng lọc ứng viên giao vận vừa rồi, hãy soạn Báo cáo Kết quả Kinh doanh Tháng 3 gửi chị Lan Trưởng phòng:
- Cấu trúc: Tiêu đề trang trọng, Tóm tắt điều hành (3 chỉ số chính), Chi tiết doanh thu theo thị trường & sản phẩm, Cảnh báo công nợ (An Phát, Đại Tín, Hải Nam), và Kế hoạch hành động tháng 4 (đẩy mạnh Gói Cao cấp, phương án phỏng vấn 2 ứng viên Nam và Hùng).
- Văn phong công sở trang trọng, KHÔNG DÙNG EMOJI, số liệu trích dẫn chính xác 100%.
- Lưu file vào thư mục 05-bao-cao/ theo đúng Super Rule tự động đánh số thứ tự tuần tự (ví dụ: 04_bao-cao-kinh-doanh-thang-3.md).
```

---

## 4. Checklist Hoàn Thành Buổi 04

- [ ] Sinh được 1 ảnh Infographic tiếng Việt bằng MCP Image và nhúng vào Slide.
- [ ] Nắm vững 3 luật thép bảo mật dữ liệu ngoài.
- [ ] Thiết lập thành công ít nhất 1 Routine tự động hóa 4 câu hỏi.
- [ ] Giải thích được ranh giới context cô lập của Subagent và 2 giới hạn cứng.
- [ ] Soạn được 1 prompt giao việc chuẩn cho Subagent quét 5 file thô mà không làm chật bàn chính.
- [ ] Agent chính xuất được Báo cáo quản trị kết quả kinh doanh hoàn chỉnh.
