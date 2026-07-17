# Workbook Buổi 05: Deep Research Agent (Agent nghiên cứu thị trường & đối thủ)

> Sổ tay thực hành của học viên. Làm theo từng bước, điền vào ô ghi chú.

## Mục tiêu buổi này
Kết thúc buổi, bạn có:
1. 1 Deep Research Agent riêng, chạy được.
2. 1 khung câu hỏi nghiên cứu cho thị trường/đối thủ thật của bạn.
3. 1 báo cáo nghiên cứu nháp có bảng so sánh đối thủ và mục "điểm cần kiểm chứng".
4. Biết cách bắt AI khi nó bịa số liệu hoặc bịa nguồn.

## Chuẩn bị trước khi vào lớp
- [ ] Tài khoản AI đã đăng nhập sẵn (bản tạo được project/agent).
- [ ] **Chọn 1 thị trường HOẶC 1 đối thủ thật bạn cần tìm hiểu.** Gợi ý: đối thủ trực tiếp của công ty bạn, hoặc một sản phẩm/dịch vụ bạn đang cân nhắc làm. Chọn cái gần công việc nhất.
- [ ] Nếu công cụ của lớp có tính năng duyệt web/tìm kiếm: biết cách bật nó (GV hướng dẫn).

**Chủ đề thật của tôi hôm nay là:**
```
(viết vào đây, ví dụ: "Thị trường phần mềm kế toán cho doanh nghiệp nhỏ tại Việt Nam" hoặc "Đối thủ ABC của công ty tôi")
_______________________________________________
```

---

## Ba loại thông tin phải phân biệt (nhớ kỹ, đây là kỹ năng chính của buổi)

| Loại | Nghĩa | Xử lý |
|---|---|---|
| **Dữ kiện có nguồn** | Con số/sự việc lấy từ 1 nguồn cụ thể, mở link kiểm được | Tin, nhưng vẫn nên tự mở nguồn nếu quan trọng |
| **Suy luận của AI** | AI tự suy ra, hợp lý nhưng chưa được kiểm chứng | Ghi rõ là suy luận, không dùng như sự thật |
| **Chỗ chưa chắc** | AI không có dữ liệu, đang đoán | Ghi "cần kiểm chứng", tự tra trước khi dùng |

Nguyên tắc vàng: **AI có thể bịa số liệu và bịa nguồn rất trơn tru. Số nào quan trọng thì tự mở ra kiểm, đừng tin ngay.**

---

## Thao tác từng bước

### Bước 1: Dựng Deep Research Agent
1. Tạo agent/project mới, đặt tên "Deep Research Agent".
2. Copy nguyên khối system prompt (ở cuối workbook này) dán vào phần hướng dẫn của agent.
3. Điền 3 ô: [Họ tên] / [chức danh] / [ngành] của bạn.
4. Nếu công cụ có duyệt web/tìm kiếm: bật lên.

**Ô ghi chú (agent đặt tên gì, đã bật web chưa):**
```
_______________________________________________
```

### Bước 2: Lập khung câu hỏi nghiên cứu
Đừng hỏi chủ đề lớn kiểu "thị trường này thế nào". Bẻ thành 4-6 câu hỏi con cụ thể, mỗi câu trả lời được riêng.

Mẫu câu lệnh copy:
```
Tôi cần nghiên cứu: [chủ đề thật của bạn].
Mục tiêu: [để ra quyết định gì, ví dụ: có nên mở sản phẩm này không].
Khu vực: [ví dụ: Hà Nội]. Mốc thời gian: [ví dụ: 2024-2025].
Trước khi trả lời, hãy lập khung câu hỏi nghiên cứu: chia chủ đề trên
thành 4-6 câu hỏi con cụ thể cần trả lời. Chỉ liệt kê câu hỏi con, chưa trả lời vội.
```

**Ô ghi chú - khung câu hỏi con của tôi:**
```
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
4. _______________________________________________
5. _______________________________________________
6. _______________________________________________
```

### Bước 3: Cho agent chạy research
Mẫu câu lệnh copy:
```
Tốt. Bây giờ trả lời lần lượt từng câu hỏi con ở trên.
Với mỗi thông tin, ghi rõ: đây là DỮ KIỆN có nguồn (kèm link nếu có),
hay SUY LUẬN của bạn, hay chỗ CHƯA CHẮC cần tôi kiểm chứng.
KHÔNG bịa số liệu, KHÔNG bịa nguồn. Không chắc thì ghi "cần kiểm chứng".
Trả về theo đúng 6 mục định dạng báo cáo nghiên cứu.
```

Nếu cần bảng so sánh đối thủ, thêm:
```
Làm thêm 1 bảng so sánh 2-3 đối thủ chính, các cột:
sản phẩm | giá | điểm mạnh | điểm yếu | định vị.
```

### Bước 4: Kiểm chứng thông tin (quan trọng nhất)
Đọc báo cáo agent trả về, làm 3 việc:

**A. Bắt AI ghi rõ nguồn.** Với số liệu quan trọng, hỏi thẳng:
```
Con số/thông tin "[dán lại chỗ nghi ngờ]" bạn lấy từ nguồn nào?
Nếu không có nguồn cụ thể, hãy ghi rõ đây là ước lượng cần kiểm chứng.
```

**B. Tự mở link kiểm.** Nếu agent trích link: mở ra xem link có thật không, nội dung có đúng như agent nói không. Link chết hoặc không khớp = dấu hiệu nguồn bịa.

**C. Đối chiếu nguồn thứ hai.** Số liệu quan trọng thì tra thêm 1 nguồn khác (tìm ngoài) xem có khớp không.

**Ô ghi chú - kết quả kiểm chứng:**
| Thông tin kiểm | Loại (dữ kiện/suy luận/chưa chắc) | Nguồn có thật? | Kết luận |
|---|---|---|---|
| | | | |
| | | | |
| | | | |

### Bước 5: Tổng hợp báo cáo hoàn chỉnh
Yêu cầu agent chỉnh lại theo 6 mục chuẩn, hạ mọi số bịa xuống "cần kiểm chứng":
```
Hãy hoàn thiện báo cáo theo đúng 6 mục:
1. Tóm tắt điều hành (5-7 dòng)
2. Khung câu hỏi nghiên cứu
3. Phát hiện chính (theo từng câu hỏi con, có nguồn)
4. Bảng so sánh đối thủ
5. Insight & khuyến nghị
6. Nguồn tham khảo / điểm cần kiểm chứng thêm
Các số liệu tôi chưa kiểm chứng được, để nguyên trong mục 6 chứ đừng đưa lên phần khẳng định.
```

---

## Bảng so sánh đối thủ (điền tay để tự nắm, đối chiếu với bản agent làm)

| Đối thủ | Sản phẩm | Giá | Điểm mạnh | Điểm yếu | Định vị |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

**Khoảng trống thị trường tôi nhìn ra từ bảng này:**
```
_______________________________________________
```

---

## System prompt: COPY nguyên khối này vào agent

```
Bạn là Deep Research Agent, trợ lý nghiên cứu cho [Họ tên], làm [chức danh] trong lĩnh vực [ngành].

NHIỆM VỤ
Khi tôi giao một chủ đề nghiên cứu, bạn:
1. Làm rõ phạm vi: hỏi tôi mục tiêu nghiên cứu để làm gì, thị trường/khu vực nào, mốc thời gian.
2. Lập khung nghiên cứu: chia chủ đề thành các câu hỏi con cần trả lời.
3. Thu thập & tổng hợp: với mỗi câu hỏi con, tổng hợp thông tin, nêu rõ nguồn (nếu có công cụ tìm web thì trích link; nếu không, ghi rõ đây là kiến thức nền cần tôi kiểm chứng).
4. Phân tích đối thủ (khi cần): bảng so sánh sản phẩm/giá/điểm mạnh-yếu/định vị.
5. Kết luận: nêu insight chính, cơ hội, rủi ro, và khuyến nghị hành động.

ĐỊNH DẠNG BÁO CÁO NGHIÊN CỨU
1. TÓM TẮT ĐIỀU HÀNH (5-7 dòng, đọc là nắm)
2. KHUNG CÂU HỎI NGHIÊN CỨU
3. PHÁT HIỆN CHÍNH (theo từng câu hỏi con, có nguồn)
4. BẢNG SO SÁNH ĐỐI THỦ (nếu có)
5. INSIGHT & KHUYẾN NGHỊ
6. NGUỒN THAM KHẢO / ĐIỂM CẦN KIỂM CHỨNG THÊM

QUY TẮC (rất quan trọng với nghiên cứu)
- Phân biệt rõ: đâu là DỮ KIỆN có nguồn, đâu là SUY LUẬN của bạn, đâu là chỗ CHƯA CHẮC.
- KHÔNG bịa số liệu thị trường, KHÔNG bịa nguồn. Không chắc thì ghi "cần kiểm chứng".
- Nêu ngày/tính thời sự của thông tin khi liên quan.
- Trung lập, đa chiều: nêu cả điểm mạnh lẫn điểm yếu.

BỐI CẢNH: tôi thường nghiên cứu để [ra quyết định kinh doanh / viết đề xuất / hiểu khách hàng ...]
```

---

## Bài tập

### Tại lớp
- [ ] Dựng xong Deep Research Agent.
- [ ] Lập khung câu hỏi nghiên cứu (4-6 câu hỏi con) cho chủ đề thật.
- [ ] Chạy ra báo cáo theo 6 mục, có 1 bảng so sánh đối thủ.
- [ ] Đánh dấu trong báo cáo: đâu là dữ kiện, suy luận, chưa chắc.

### Về nhà
- [ ] Tự mở và kiểm chứng ít nhất 2 số liệu/nguồn trong báo cáo. Ghi lại cái nào đúng, cái nào sai/không có nguồn.
- [ ] Chỉnh lại báo cáo sau kiểm chứng (hạ số bịa xuống "cần kiểm chứng", bổ sung nguồn thật).
- [ ] Nghĩ trước 1 dự án công việc thật cho buổi 6 (research xong đẩy sang Report Agent viết đề xuất).

**Ô ghi chú bài về nhà - tôi đã kiểm chứng được gì:**
```
_______________________________________________
_______________________________________________
```

---

## Checklist tự đánh giá
- [ ] Tôi bẻ được 1 chủ đề lớn thành các câu hỏi con cụ thể.
- [ ] Tôi phân biệt được dữ kiện / suy luận / chỗ chưa chắc trong 1 báo cáo.
- [ ] Tôi biết ít nhất 1 cách bắt AI khi nó bịa số liệu.
- [ ] Tôi biết cách kiểm 1 nguồn/link có thật hay không.
- [ ] Tôi có bảng so sánh đối thủ đủ 5 cột.
- [ ] Tôi hiểu vì sao research xong lại đẩy sang Report Agent để viết đề xuất.
