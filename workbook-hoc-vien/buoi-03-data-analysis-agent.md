# Workbook Buổi 03 - Data Analysis Agent (Agent phân tích dữ liệu)

> Vở thực hành cho học viên. Làm theo từng bước, điền vào ô ghi chú, giữ lại để buổi sau ghép vào Report Agent.

## Mục tiêu buổi này
Sau 150 phút, bạn có:
- 1 Data Analysis Agent tự dựng, đọc được file Excel/CSV của bạn.
- 1 bản phân tích số liệu từ file công việc thật: tổng quan + số liệu chính + xu hướng + gợi ý biểu đồ.
- Thói quen kiểm lại con số quan trọng trước khi tin.

## Chuẩn bị trước khi vào lớp
- [ ] Đăng nhập sẵn tài khoản AI, mở workspace đã dựng ở Buổi 1.
- [ ] **Mang theo 1 file Excel/CSV công việc thật có số liệu** (doanh thu, chi phí, KPI, kho, khảo sát, danh sách đơn hàng... loại nào cũng được).
- [ ] Mở sẵn Excel trên máy để lát nữa kiểm tra con số và vẽ biểu đồ.
- [ ] Nhận file demo chung của lớp từ giảng viên.

> Mẹo: file càng gọn càng tốt. Nếu file của bạn có nhiều sheet, chọn 1 sheet có số liệu rõ ràng nhất để dùng hôm nay.

---

## Phần A - Thao tác từng bước (làm theo thứ tự)

### Bước 1. Tạo agent mới
1. Vào workspace của bạn.
2. Tạo một agent/project mới.
3. Đặt tên: `Data Analysis Agent`.

**Ô ghi chú (tên agent + vị trí bạn lưu):**
```
_______________________________________________
```

### Bước 2. Dán system prompt
1. Mở phần system prompt ở cuối workbook này (Phần D).
2. Copy nguyên khối trong khung.
3. Dán vào phần hướng dẫn/chỉ dẫn của agent.
4. Điền vào 3 chỗ trong ngoặc vuông:
   - `[Họ tên]` → tên bạn
   - `[chức danh]` → công việc của bạn
   - `[doanh thu / chi phí / KPI / khảo sát / kho ...]` → loại số liệu bạn hay dùng

### Bước 3. Upload file và bắt agent hiểu dữ liệu
1. Upload file demo chung (hoặc file của bạn ở Thực hành 2).
2. Gõ câu này:
```
Đọc file này và cho tôi tổng quan dữ liệu: bao nhiêu dòng, bao nhiêu cột, mỗi cột nghĩa gì, có ô trống / dòng trùng / cột sai định dạng không.
```
3. Đọc kỹ phần trả lời. Kiểm nhanh: số dòng/cột agent nói có khớp với file thật không?

**Ô ghi chú (agent báo file có bao nhiêu dòng/cột, có lỗi gì):**
```
_______________________________________________
_______________________________________________
```

### Bước 4. Hỏi phân tích (tính toán)
Gõ lần lượt vài câu (chọn câu phù hợp file của bạn, xem thêm mẫu ở Phần B):
```
Tính tổng và trung bình của cột [tên cột số liệu].
So sánh [kỳ này] với [kỳ trước], tăng hay giảm bao nhiêu phần trăm.
Cho tôi top 5 [khách hàng / sản phẩm / khoản mục] có [số liệu] cao nhất.
```

**Ô ghi chú (2-3 số liệu chính agent tìm ra):**
```
_______________________________________________
_______________________________________________
```

### Bước 5. Xin gợi ý biểu đồ
Gõ:
```
Đề xuất 1 biểu đồ phù hợp để trình bày [nội dung bạn muốn cho thấy]. Nói rõ loại biểu đồ, trục X là gì, trục Y là gì, và biểu đồ đó cho thấy điều gì.
```
Nếu công cụ vẽ được: cho vẽ. Nếu không: mở Excel → chọn dữ liệu → Insert → Chart → chọn đúng loại theo mô tả.

**Ô ghi chú (loại biểu đồ + trục X-Y agent gợi ý):**
```
_______________________________________________
```

### Bước 6. Kiểm lại con số quan trọng (BẮT BUỘC)
1. Chọn 1 con số quan trọng nhất agent vừa đưa (ví dụ tổng doanh thu).
2. Mở Excel, dùng hàm kiểm: `=SUM(vùng dữ liệu)` hoặc `=AVERAGE(...)`.
3. So sánh với số của agent.

**Ô ghi chú (số của agent / số bạn kiểm / khớp hay lệch):**
```
Agent:  _____________   Kiểm tay: _____________   Khớp? ______
```

> Quy tắc vàng: con số nào đưa vào báo cáo, gửi sếp thì phải là con số đã kiểm. AI nhanh nhưng có thể nhầm.

---

## Phần B - Mẫu câu hỏi phân tích (copy rồi sửa cho hợp file của bạn)

**Hiểu dữ liệu:**
```
Đọc file này, mô tả mỗi cột nghĩa là gì và chỉ ra ô trống, dòng trùng, cột sai định dạng.
```

**Tính toán cơ bản:**
```
Tính tổng, trung bình, lớn nhất, nhỏ nhất của cột [tên cột].
Tỷ lệ [nhóm A] trên tổng là bao nhiêu phần trăm?
```

**So sánh theo kỳ:**
```
So sánh doanh thu quý này với quý trước theo từng sản phẩm, cho biết tăng/giảm bao nhiêu phần trăm.
So sánh [tháng này] với [tháng trước], nêu 3 thay đổi đáng chú ý nhất.
```

**Top / bottom, phân nhóm:**
```
Cho tôi 5 khách hàng đóng góp doanh thu nhiều nhất, xếp từ cao xuống thấp.
Nhóm dữ liệu theo [khu vực / sản phẩm / tháng] và tính tổng từng nhóm.
```

**Xu hướng:**
```
Nhìn số liệu theo thời gian, chỉ ra xu hướng tăng/giảm, tháng cao điểm, tháng thấp điểm, có gì bất thường.
```

**Biểu đồ:**
```
Với số liệu này, nên vẽ biểu đồ gì? Nêu loại biểu đồ, trục X, trục Y và ý nghĩa.
```

> Nhớ: câu hỏi càng cụ thể (rõ cột, rõ cách nhóm, rõ mốc so sánh), kết quả càng đúng ý. Tránh câu chung chung như "phân tích file này giúp tôi".

---

## Phần C - Bài tập

### Tại lớp
- [ ] Dựng xong Data Analysis Agent.
- [ ] Chạy trên file công việc thật, xuất 1 bản phân tích đủ 4 phần: tổng quan dữ liệu, số liệu chính, nhận định xu hướng, gợi ý biểu đồ.
- [ ] Kiểm lại 1 con số quan trọng bằng Excel.

### Về nhà
- [ ] Lấy thêm 1 file số liệu khác (khác loại với file ở lớp), chạy qua agent, xuất 1 bản phân tích.
- [ ] Vẽ ít nhất 1 biểu đồ trong Excel theo gợi ý của agent.
- [ ] Chọn 2 con số quan trọng, kiểm lại bằng tay, ghi rõ đúng hay lệch và lệch bao nhiêu.
- [ ] Thêm 1 câu mô tả loại dữ liệu bạn hay dùng vào phần BỐI CẢNH của system prompt để lần sau agent hiểu nhanh hơn.

**Ô ghi chú bài về nhà (file đã chạy, biểu đồ đã vẽ, kết quả kiểm số):**
```
_______________________________________________
_______________________________________________
_______________________________________________
```

---

## Phần D - System prompt để COPY

> Trích từ `system-prompts/03-data-analysis-agent.md`. Copy nguyên khối dưới, dán vào agent, điền 3 chỗ trong ngoặc vuông.

```
Bạn là Data Analysis Agent - trợ lý phân tích số liệu cho [Họ tên], làm [chức danh].

NHIỆM VỤ
Khi tôi đưa một file dữ liệu (Excel/CSV) hoặc bảng số, bạn:
1. Hiểu dữ liệu: mô tả nhanh có bao nhiêu dòng/cột, mỗi cột nghĩa gì, có gì bất thường (ô trống, sai định dạng, trùng lặp).
2. Làm sạch (nếu tôi yêu cầu): chỉ ra và đề xuất cách xử lý dữ liệu lỗi.
3. Phân tích: tính tổng, trung bình, tỷ lệ, tăng trưởng, top/bottom, phân nhóm theo yêu cầu.
4. Tìm xu hướng: chỉ ra điểm tăng/giảm, mùa vụ, bất thường đáng chú ý.
5. Gợi ý biểu đồ: nói rõ nên dùng loại biểu đồ nào (cột/đường/tròn/...), trục X-Y là gì, và mô tả biểu đồ đó cho biết điều gì.

ĐỊNH DẠNG TRẢ LỜI MẶC ĐỊNH
1. TỔNG QUAN DỮ LIỆU (số dòng/cột, chất lượng)
2. KẾT QUẢ PHÂN TÍCH (số liệu chính, dạng bảng gọn)
3. NHẬN ĐỊNH & XU HƯỚNG (3-5 gạch đầu dòng, ngôn ngữ dễ hiểu)
4. BIỂU ĐỒ ĐỀ XUẤT (loại + trục + ý nghĩa)
5. HÀNH ĐỘNG GỢI Ý dựa trên số liệu

QUY TẮC
- Tiếng Việt. Diễn giải số liệu cho người không chuyên hiểu được.
- KHÔNG bịa số. Mọi con số phải lấy từ dữ liệu; nếu tính ra thì nói rõ công thức.
- Nêu giả định nếu phải giả định (ví dụ đơn vị tiền, kỳ báo cáo).
- Cảnh báo khi mẫu dữ liệu quá nhỏ hoặc kết luận chưa chắc chắn.

BỐI CẢNH: dữ liệu của tôi thường là [doanh thu / chi phí / KPI / khảo sát / kho ...]
```

---

## Phần E - Checklist tự đánh giá

- [ ] Tôi dựng được Data Analysis Agent và nó chạy trong workspace của tôi.
- [ ] Tôi upload được file Excel/CSV và agent mô tả đúng số dòng/cột.
- [ ] Agent chỉ ra được ô trống / dòng trùng / cột sai định dạng trong file của tôi.
- [ ] Tôi đặt được ít nhất 3 câu hỏi phân tích cụ thể và hiểu kết quả.
- [ ] Tôi có 1 gợi ý biểu đồ và đã vẽ lại được (trong công cụ hoặc Excel).
- [ ] Tôi kiểm lại 1 con số quan trọng bằng tay và biết nó đúng hay lệch.
- [ ] Tôi giữ lại bản phân tích để buổi sau ghép vào Report Agent.

> Nếu còn ô chưa tích, nhắn giảng viên qua Zalo hoặc xem lại Phần A trước buổi 4.
