# Workbook Buổi 02: Document Agent (Người đọc tài liệu của bạn)

> Sổ tay thực hành cho học viên. Làm theo từng bước, điền vào các ô ghi chú. Cuối buổi bạn sẽ có một "nhân viên AI" chuyên đọc tài liệu dài.

## Buổi này bạn sẽ làm được gì
- Dựng một Document Agent trong workspace của bạn: một agent chỉ chuyên đọc tài liệu.
- Đưa file dài (hợp đồng, biên bản, báo cáo, bài viết) cho AI đọc hộ và tóm tắt.
- Xin tóm tắt nhiều mức: bản 3 câu để lướt nhanh, bản 1 trang để hiểu kỹ.
- Bóc ra số liệu, ngày tháng, hạn chót trong tài liệu chỉ bằng một câu lệnh.
- Biết cách hỏi nối tiếp để đào sâu đúng chỗ bạn quan tâm.
- Nhận ra khi AI "bịa" (ảo giác) và biết cách chặn.

## Chuẩn bị trước khi vào lớp
- [ ] Workspace + Orchestrator đã dựng xong ở Buổi 1 (nếu chưa xong, báo giảng viên đầu giờ).
- [ ] Tải file demo chung mà CES gửi qua Zalo về máy.
- [ ] Mang theo **tài liệu dài công việc thật của bạn**: 1 hợp đồng, 1 biên bản họp, hoặc 1 báo cáo nhiều trang (dạng PDF hoặc Word có chữ thật, không phải ảnh chụp).
- [ ] Đăng nhập sẵn tài khoản AI, ngồi máy tính để thao tác theo.

---

## Phần A: Khái niệm nhanh (đọc 2 phút)

- **Document Agent** là một nhân viên AI chỉ làm một việc: đọc tài liệu. Bạn đưa file, nó tóm tắt, chỉ ra ý quan trọng, trả lời câu hỏi dựa trên file đó.
- **Upload file** = đưa file lên cho AI đọc trực tiếp, thay vì copy từng đoạn dán vào.
- **Hỏi nối tiếp** = xin tóm tắt tổng thể trước, rồi hỏi sâu từng mục sau. Giống bóc củ hành, lớp ngoài trước.
- **Ảo giác (AI bịa)** = AI trả lời trôi chảy nhưng nội dung không có thật trong file. Nguy hiểm nhất với hợp đồng và số liệu. Quy tắc vàng: bắt agent "không có trong tài liệu thì nói không có".

---

## Phần B: Thao tác từng bước

### Bước 1: Tạo Document Agent
1. Mở workspace bạn đã dựng ở Buổi 1.
2. Bấm nút tạo **project / custom agent mới**.
3. Đặt tên: `Document Agent`.

### Bước 2: Dán system prompt
4. Mở phần **Instructions / System prompt** của agent.
5. Copy toàn bộ khối system prompt ở Phần E cuối workbook này (hoặc từ file `system-prompts/02-document-agent.md`).
6. Dán vào ô Instructions.
7. Điền tên bạn vào chỗ `[Họ tên]`. Ở dòng cuối, chọn văn phong bạn muốn: `trang trọng`, `thân thiện`, hay `ngắn gọn`.
8. **Lưu** agent lại.

### Bước 3: Upload tài liệu
9. Mở khung chat của Document Agent vừa tạo.
10. Bấm nút **upload file** (thường là hình cái kẹp giấy hoặc dấu cộng).
11. Chọn file demo chung (hoặc kéo thả file vào khung chat). Chờ file nạp xong.

### Bước 4: Ra lệnh tóm tắt nhiều mức
12. Gõ lệnh xin bản ngắn nhất (xem câu mẫu ở Phần C).
13. Gõ tiếp lệnh xin bản dài hơn để so sánh.

### Bước 5: Bóc tách số liệu
14. Gõ lệnh xin liệt kê ngày tháng, số tiền, hạn chót trong file.

### Bước 6: Hỏi nối tiếp
15. Chọn 1 mục quan trọng trong bản tóm tắt.
16. Hỏi sâu về đúng mục đó bằng 2-3 câu liên tiếp.

### Bước 7: Kiểm tra ảo giác
17. Cố tình hỏi một câu mà bạn biết chắc file KHÔNG có đáp án.
18. Xem agent trả lời "Tài liệu không đề cập" (đúng) hay bịa ra một câu (sai). Nếu nó bịa, thêm vào lệnh: "Chỉ trả lời dựa trên tài liệu, phần nào không có thì nói không có."

---

## Phần C: Câu lệnh mẫu (gõ thử ngay)

Tóm tắt nhiều mức:
```
Tóm tắt tài liệu này trong đúng 3 câu.
```
```
Giờ tóm tắt lại thành 1 trang, chia theo từng mục.
```

Trích ý chính:
```
Liệt kê các ý quan trọng nhất của tài liệu dạng gạch đầu dòng, kèm vị trí (mục/trang) nếu có.
```

Bóc tách số liệu / ngày / hạn chót:
```
Liệt kê tất cả ngày tháng, số tiền và hạn chót có trong tài liệu này, sắp theo thứ tự thời gian.
```

Hỏi nối tiếp (đào sâu 1 mục):
```
Điều khoản thanh toán trong tài liệu nói gì? Trích nguyên văn câu quan trọng nhất, đặt trong ngoặc kép.
```

Trích rủi ro / điểm cần lưu ý:
```
Chỉ ra các điểm cần lưu ý, rủi ro, hoặc hạn chót trong tài liệu này. Nếu không có, nói rõ là không có.
```

Câu hỏi kiểm tra ảo giác (thay bằng thông tin bạn biết file không có):
```
Số điện thoại của bên A ghi trong tài liệu là gì?
```

So sánh nhiều tài liệu (dùng khi upload từ 2 file):
```
So sánh hai tài liệu này: điểm giống, điểm khác, và có chỗ nào mâu thuẫn không?
```

---

## Phần D: Ô ghi chú (điền trong lúc thực hành)

**Tên tài liệu công việc mình dùng hôm nay:**
```
.......................................................................
```

**Bản tóm tắt 3 câu agent trả về (chép lại hoặc nhận xét):**
```
.......................................................................
.......................................................................
```

**Số liệu / ngày / hạn chót agent bóc ra được:**
```
.......................................................................
.......................................................................
```

**Câu hỏi nối tiếp mình đã hỏi và câu trả lời đáng chú ý:**
```
.......................................................................
.......................................................................
```

**Lần agent suýt bịa (ảo giác) và cách mình phát hiện:**
```
.......................................................................
.......................................................................
```

**Văn phong mình đã chọn cho agent:**  trang trọng / thân thiện / ngắn gọn  (khoanh 1)

---

## Phần E: System prompt để COPY

> Dán khối này vào ô Instructions của Document Agent. Sửa chỗ trong `[ngoặc vuông]`.

```
Bạn là Document Agent: trợ lý đọc và xử lý tài liệu cho [Họ tên].

NHIỆM VỤ
Khi tôi đưa một tài liệu (hoặc dán nội dung dài), bạn giúp tôi:
- Tóm tắt: nêu ý chính theo độ dài tôi yêu cầu (3 câu / 1 đoạn / 1 trang).
- Trích ý: liệt kê các điểm quan trọng dạng gạch đầu dòng, kèm vị trí (mục/trang) nếu có.
- Trả lời câu hỏi: chỉ dựa trên nội dung tài liệu, không tự bịa.
- Bóc tách: lấy ra số liệu, ngày tháng, tên riêng, cam kết, hạn chót khi tôi cần.
- So sánh: nếu có nhiều tài liệu, chỉ ra điểm giống/khác/mâu thuẫn.

ĐỊNH DẠNG TRẢ LỜI MẶC ĐỊNH
1. TÓM TẮT NHANH (3-5 gạch đầu dòng)
2. Ý CHÍNH CHI TIẾT (theo mục)
3. ĐIỂM CẦN LƯU Ý / RỦI RO / HẠN CHÓT (nếu có)
4. CÂU HỎI GỢI Ý tôi nên hỏi tiếp

QUY TẮC
- Tiếng Việt, rõ ràng, đi thẳng vào nội dung.
- Nếu tài liệu không có thông tin tôi hỏi, nói rõ "Tài liệu không đề cập", KHÔNG suy đoán.
- Trích dẫn nguyên văn khi tôi cần bằng chứng, đặt trong ngoặc kép.
- Giữ trung thực với tài liệu: không thêm quan điểm ngoài nội dung trừ khi tôi yêu cầu.

VĂN PHONG ĐẦU RA: [trang trọng / thân thiện / ngắn gọn]
```

---

## Phần F: Bài tập

### Tại lớp
- [ ] Dựng xong Document Agent và upload được file demo chung.
- [ ] Xin được 2 mức tóm tắt khác nhau trên cùng file (3 câu và 1 trang).
- [ ] Bóc được số liệu / ngày / hạn chót từ file.
- [ ] Hỏi bẫy ảo giác 1 câu file không có, xác nhận agent nói "không đề cập".
- [ ] Áp Document Agent vào 1 tài liệu công việc thật của mình và hỏi nối tiếp 2-3 câu.

### Về nhà
- [ ] Cho agent tóm tắt và trích điểm cần lưu ý của 2 tài liệu công việc khác nhau.
- [ ] Thử so sánh 2 tài liệu liên quan (ví dụ hợp đồng bản cũ và bản mới): hỏi khác nhau chỗ nào, có mâu thuẫn không.
- [ ] Ghi lại 1 lần agent suýt bịa nội dung và cách bạn phát hiện, mang chia sẻ đầu Buổi 3.
- [ ] Chuẩn bị 1 file Excel/CSV công việc thật cho Buổi 3 (Data Analysis Agent).

---

## Phần G: Checklist tự đánh giá

- [ ] Mình tự dựng lại được Document Agent mà không cần xem hướng dẫn.
- [ ] Mình biết upload file và xin tóm tắt ở mức mình cần.
- [ ] Mình biết dùng kỹ thuật hỏi nối tiếp: tóm tắt trước, đào sâu sau.
- [ ] Mình hiểu ảo giác là gì và biết một cách chặn.
- [ ] Mình luôn nhớ kiểm tra lại file gốc với thông tin quan trọng (hợp đồng, số tiền, hạn chót).
- [ ] Agent của mình đã lưu lại, sẵn sàng dùng cho công việc thật.

> Mẹo: từ hôm nay, mỗi lần nhận tài liệu dài, đừng đọc từ trang một. Đưa cho Document Agent, xin tóm tắt, rồi hỏi sâu chỗ bạn cần. Nhưng với hợp đồng và số liệu, luôn mở file gốc kiểm tra lại điểm quan trọng.
