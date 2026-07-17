# Workbook Buổi 04 - Report Agent (Agent soạn báo cáo & văn bản)

> Sổ tay làm theo cho học viên. Bám sát giáo viên, điền trực tiếp vào các ô ghi chú.

## Buổi này bạn sẽ làm được gì
1. Dựng Report Agent riêng: một agent viết văn bản công việc theo giọng công ty bạn.
2. Soạn 4 loại văn bản từ ý/số liệu thô: báo cáo, đề xuất, email, dàn ý slide.
3. Nối số liệu từ agent buổi 3 (Data Analysis) thành báo cáo hoàn chỉnh.
4. Áp đúng 3 quy tắc CES: email không emoji, văn phong công sở, không bịa số.

## Chuẩn bị trước khi vào lớp
- [ ] Tài khoản AI đã đăng nhập, tạo sẵn 1 project trống.
- [ ] Mang theo **1 việc soạn thảo thật** đang phải làm: 1 báo cáo, 1 email, hoặc 1 đề xuất (kèm số liệu hoặc ý thô).
- [ ] Nếu đã làm buổi 3: mở sẵn 1 output số liệu từ Data Analysis Agent để thử nối.
- [ ] Nhớ 2-3 câu mô tả văn phong công ty mình (xưng hô, trang trọng hay thân thiện, chữ ký).

---

## Phần 1 - Bốn khung văn bản (học thuộc bố cục)

| Loại | Bố cục theo thứ tự | Dùng khi |
|---|---|---|
| Báo cáo | Mở đầu (kỳ) → Nội dung chính → Kết quả (số liệu) → Vướng mắc → Đề xuất/Kế hoạch | Báo cáo tuần/tháng/dự án cho sếp |
| Đề xuất | Bối cảnh → Vấn đề → Giải pháp → Lợi ích → Chi phí → Kế hoạch | Xin duyệt ý tưởng, ngân sách |
| Email | Tiêu đề → Lời chào → Thân (1 ý chính) → Đề nghị/hành động → Lời kết + chữ ký | Gửi sếp, khách, đồng nghiệp, đối tác |
| Dàn ý slide | Từng slide: tiêu đề + 3-5 gạch ý + gợi ý hình/biểu đồ | Chuẩn bị thuyết trình nhanh |

**3 quy tắc CES bắt buộc (kiểm tra mọi output):**
1. Email gửi đi KHÔNG emoji.
2. Văn phong chuyên nghiệp công sở, câu rõ, không sáo rỗng.
3. KHÔNG bịa số. Chỗ thiếu để `[đợi bổ sung]`, bạn tự điền sau.

---

## Phần 2 - Thao tác từng bước

### A. Dựng Report Agent (làm 1 lần)
1. Tạo project/agent mới, đặt tên "Report Agent".
2. Copy khối system prompt ở **Phần 5** của workbook này, dán vào phần chỉ dẫn của agent.
3. Điền các chỗ trong ngoặc vuông: `[Họ tên]`, `[chức danh]`, `[công ty]`.
4. Chọn văn phong mặc định (trang trọng / thân thiện chuyên nghiệp / ngắn gọn) và người nhận thường gặp (sếp / khách hàng / đồng nghiệp / đối tác).
5. Dán 2-3 câu mô tả văn phong công ty bạn vào phần bối cảnh. Lưu lại.

### B. Soạn 1 báo cáo từ số liệu
1. Chuẩn bị số liệu thô (gạch đầu dòng hoặc bảng đơn giản).
2. Gõ lệnh: "Soạn báo cáo tuần từ số liệu này." Dán số liệu bên dưới.
3. Nếu agent hỏi lại (đối tượng nhận, mục đích), trả lời gọn.
4. Đọc kỹ output: bố cục đúng khung chưa, số liệu có khớp số bạn đưa không, chỗ thiếu có để `[đợi bổ sung]` không.
5. Tinh chỉnh nếu cần: "Rút gọn còn nửa trang" / "Trang trọng hơn" / "Mỗi ý một gạch đầu dòng."

### C. Soạn 1 email công việc
1. Đưa vài ý rời cần nói.
2. Gõ: "Soạn email [mục đích] gửi [người nhận], văn phong công sở, không dùng emoji."
3. Kiểm tra: tiêu đề rõ, một ý chính, có lời chào và chữ ký, KHÔNG emoji.

### D. Soạn đề xuất hoặc dàn ý slide (khi cần)
1. Đề xuất: gõ "Soạn đề xuất về [chủ đề]." Đưa bối cảnh và vấn đề. Agent theo khung bối cảnh → vấn đề → giải pháp → lợi ích → chi phí → kế hoạch.
2. Dàn ý slide: gõ "Lập dàn ý slide cho [chủ đề], mỗi slide 3-5 gạch ý, gợi ý hình/biểu đồ."

### E. Nối số liệu buổi 3 sang buổi 4
1. Mở output số liệu đã phân tích từ Data Analysis Agent (buổi 3).
2. Copy phần con số và kết luận gọn (không copy cả bảng thô dài).
3. Dán vào Report Agent, gõ: "Đây là số liệu đã phân tích, viết thành báo cáo tuần."
4. Kiểm tra số trong báo cáo khớp đúng số buổi 3 đưa qua.

---

## Phần 3 - Mẫu câu lệnh để copy

```
Soạn báo cáo tuần từ số liệu dưới đây. Văn phong công sở. Chỉ dùng số tôi cung cấp, chỗ nào thiếu để [đợi bổ sung], không tự bịa số.
[dán số liệu]
```

```
Soạn email báo cáo tiến độ gửi sếp. Văn phong chuyên nghiệp, KHÔNG dùng emoji. Ý cần nói:
[dán các ý rời]
```

```
Soạn đề xuất về [chủ đề]. Theo khung: bối cảnh, vấn đề, giải pháp, lợi ích, chi phí, kế hoạch triển khai.
[dán thông tin có]
```

```
Lập dàn ý slide cho buổi thuyết trình [chủ đề]. Mỗi slide gồm tiêu đề + 3-5 gạch ý + gợi ý hình hoặc biểu đồ.
```

```
Rút gọn bản trên còn nửa trang, giữ đủ số liệu, bỏ câu sáo rỗng.
```

```
Bỏ hết emoji, viết lại theo văn phong công sở chuyên nghiệp.
```

---

## Phần 4 - Ví dụ: input thô đến output hoàn chỉnh

### Input thô (bạn đưa cho agent)
```
Báo cáo tuần phòng kinh doanh:
- Gọi 120 khách, hẹn gặp 18
- Chốt 5 hợp đồng, doanh thu 240 triệu
- Vướng: 3 khách chờ duyệt ngân sách bên họ
- Tuần tới: đẩy nhóm khách đã hẹn gặp
- Số khách mới thu về: chưa tổng hợp xong
```

### Output hoàn chỉnh (agent trả về, không emoji)
```
BÁO CÁO CÔNG VIỆC TUẦN - PHÒNG KINH DOANH

Kỳ báo cáo: [đợi bổ sung ngày]

1. Nội dung chính đã thực hiện
- Gọi tiếp cận 120 khách hàng, đặt lịch hẹn gặp 18 khách.
- Tập trung nhóm khách có nhu cầu rõ để đẩy nhanh vòng chốt.

2. Kết quả
- Chốt 5 hợp đồng.
- Doanh thu tuần: 240 triệu đồng.
- Số khách hàng mới thu về: [đợi bổ sung].

3. Vướng mắc
- 3 khách hàng đang chờ duyệt ngân sách nội bộ bên phía họ, chưa thể chốt trong tuần.

4. Kế hoạch tuần tới
- Ưu tiên chăm sóc nhóm 18 khách đã hẹn gặp để chuyển sang giai đoạn chốt.
- Theo dõi tiến độ duyệt ngân sách của 3 khách đang chờ.

Trân trọng,
[Họ tên] - [Chức danh]
```

Điểm cần chú ý ở output: bố cục đúng khung báo cáo; mọi số khớp đúng số bạn đưa; chỗ thiếu (kỳ báo cáo, số khách mới) để `[đợi bổ sung]` chứ agent không tự bịa; không có một emoji nào.

---

## Phần 5 - System prompt Report Agent (copy nguyên khối)

```
Bạn là Report Agent - trợ lý soạn thảo văn bản công việc cho [Họ tên], làm [chức danh] tại [công ty].

NHIỆM VỤ
Từ dữ liệu/ý thô tôi đưa, bạn soạn ra bản hoàn chỉnh cho một trong các loại:
- BÁO CÁO (tuần/tháng/dự án): mở đầu, nội dung chính, kết quả, vướng mắc, đề xuất.
- ĐỀ XUẤT / PROPOSAL: bối cảnh, vấn đề, giải pháp, lợi ích, chi phí, kế hoạch.
- EMAIL: tiêu đề và thân email đúng văn phong, có lời chào và lời kết phù hợp.
- DÀN Ý SLIDE: liệt kê từng slide (tiêu đề và 3-5 gạch ý), gợi ý hình hoặc biểu đồ.

QUY TRÌNH
1. Nếu thiếu thông tin cốt lõi (đối tượng nhận, mục đích, số liệu), hỏi tôi tối đa 3 câu trước.
2. Soạn bản đầy đủ theo cấu trúc loại văn bản.
3. Kết thúc, hỏi tôi có muốn: rút gọn / trang trọng hơn / thêm số liệu / đổi văn phong.

QUY TẮC
- Tiếng Việt chuẩn công sở. KHÔNG dùng emoji trong email và báo cáo trang trọng.
- KHÔNG bịa số liệu, chỉ dùng số tôi cung cấp; chỗ thiếu để [đợi bổ sung].
- Câu rõ ràng, tránh sáo rỗng. Ưu tiên gạch đầu dòng cho báo cáo.
- Giữ nhất quán tên riêng, chức danh, đơn vị tôi đã nêu.

VĂN PHONG MẶC ĐỊNH: [trang trọng / thân thiện chuyên nghiệp / ngắn gọn]
NGƯỜI NHẬN THƯỜNG LÀ: [sếp / khách hàng / đồng nghiệp / đối tác]
```

Sau khi dán, nhớ thay hết chỗ trong ngoặc vuông bằng thông tin thật của bạn.

---

## Phần 6 - Ô ghi chú (điền tại lớp)

**Văn phong công ty tôi (2-3 câu):**
```
_______________________________________________
_______________________________________________
```

**Loại văn bản tôi viết nhiều nhất và hay vướng ở đâu:**
```
_______________________________________________
```

**Lệnh hiệu quả nhất tôi tìm ra hôm nay:**
```
_______________________________________________
```

**Chỗ agent hay bịa số / sai giọng và cách tôi sửa:**
```
_______________________________________________
```

---

## Phần 7 - Bài tập

**Tại lớp:**
- [ ] Dựng xong Report Agent (đã điền tên, chức danh, công ty, văn phong).
- [ ] Soạn tối thiểu 2 văn bản hoàn chỉnh từ dữ liệu thật: 1 báo cáo (hoặc đề xuất) + 1 email.
- [ ] Kiểm tra đạt 3 quy tắc CES.

**Về nhà:**
- [ ] Nạp văn phong công ty thật vào agent và lưu lại.
- [ ] Soạn 1 báo cáo tuần thật, rà không có số bịa (chỗ thiếu để `[đợi bổ sung]`).
- [ ] Soạn 1 email công việc thật gửi sếp hoặc đối tác, rà kỹ không còn emoji.
- [ ] (Nếu có agent buổi 3) Thử nối: Data Agent ra số, đưa sang Report Agent viết báo cáo.

---

## Phần 8 - Checklist tự đánh giá

- [ ] Tôi dựng được Report Agent chạy được ngay.
- [ ] Tôi biết chọn đúng 1 trong 4 khung văn bản theo mục đích.
- [ ] Văn bản tôi soạn đúng bố cục khung.
- [ ] Email của tôi không có emoji, giọng chuyên nghiệp công sở.
- [ ] Không có số nào bị bịa; chỗ thiếu tôi để `[đợi bổ sung]`.
- [ ] Tôi đã nạp văn phong công ty vào bối cảnh agent.
- [ ] Tôi thử được (ít nhất 1 lần) nối số liệu buổi 3 thành báo cáo buổi 4.
