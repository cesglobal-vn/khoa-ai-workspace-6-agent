# Workbook Buổi 05: Agent Team - chia một việc lớn cho nhiều agent chạy song song

> Tài liệu để học viên tự làm theo trong và sau buổi học. Làm lần lượt từng bước có đánh số.
> Không cần biết lập trình. Ra lệnh bằng tiếng Việt trong Claude Code trên Claude Desktop.

## 1. Mục tiêu của bạn sau buổi này
1. Hiểu agent team: một việc lớn chia cho nhiều agent làm cùng lúc, một lead ghép kết quả.
2. Chạy được team 3 agent trên thư mục demo `du-an-ra-mat-san-pham/`.
3. Tự chia một việc thật của mình cho 2-3 agent chạy song song và nhận về một bản tổng hợp.
4. Biết khi nào KHÔNG nên chạy song song (việc phụ thuộc nhau thì làm tuần tự).

## 2. Bạn cần nhớ (4 nguyên tắc)
1. **Chia việc độc lập:** mỗi agent làm một phần không đụng phần agent khác.
2. **Phân vùng file:** mỗi agent chỉ đọc và sửa thư mục của mình, tránh giẫm chân nhau.
3. **Chạy song song:** giao tất cả cùng lúc để rút ngắn thời gian.
4. **Lead tổng hợp:** khi các agent xong, lead gom kết quả, kiểm số liệu có khớp không, rồi chốt.

> Nối buổi 4: mỗi agent trong team có thể là một subagent chuyên trách bạn đã học (agent phân tích số liệu, agent nghiên cứu). Buổi 5 là cho nhiều agent như vậy chạy cùng lúc.

## 3. Chuẩn bị
- [ ] Mở Claude Code trên Claude Desktop.
- [ ] Tải và mở thư mục demo `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/`, kiểm có 3 thư mục con: `thi-truong/`, `doi-thu/`, `so-lieu/`.
- [ ] Chọn sẵn 1 việc thật của bạn có nhiều phần độc lập để dùng ở phần thực hành 2. Gợi ý cách chọn:
  - Việc chuẩn bị họp: đọc biên bản cũ / tổng hợp số liệu tháng / soạn danh sách việc tồn.
  - Việc làm hồ sơ khách: tóm tắt nhu cầu khách / so sánh các gói / soạn báo giá nháp.
  - Cách kiểm nhanh một việc có độc lập không: hỏi "nếu phần 2 chưa xong thì phần 1 có làm được không?". Nếu vẫn làm được thì độc lập, chia song song được.

---

## 4. Thao tác từng bước (phần A: chạy trên thư mục demo)

**Bước 1. Xem cấu trúc thư mục dự án.** Gõ vào Claude Code:
```
Liệt kê cấu trúc thư mục du-an-ra-mat-san-pham/ cho tôi xem có những thư mục con nào và mỗi thư mục có file gì.
```
Bạn phải thấy 3 thư mục con: `thi-truong/`, `doi-thu/`, `so-lieu/`. Mỗi thư mục sẽ giao cho một agent.

**Bước 2. Giao lead chia 3 phần cho 3 agent chạy song song.** Gõ vào Claude Code:
```
Tôi có một dự án chuẩn bị ra mắt sản phẩm trong thư mục du-an-ra-mat-san-pham/.
Hãy chia thành 3 phần độc lập và giao cho 3 agent chạy SONG SONG:
- Agent 1: chỉ đọc thư mục thi-truong/ và tóm tắt bối cảnh thị trường.
- Agent 2: chỉ đọc thư mục doi-thu/ và lập bảng so sánh các đối thủ và chỉ ra khoảng trống thị trường.
- Agent 3: chỉ đọc thư mục so-lieu/ và phân tích số liệu bán hàng.
Mỗi agent chỉ đọc đúng thư mục của mình, không đọc thư mục của agent khác.
Sau khi cả ba xong, hãy tổng hợp thành một bản chung cho tôi và kiểm xem có mâu thuẫn số liệu nào không.
```

**Bước 3. Đọc bản tổng hợp và đối chiếu.** Bản gom cuối phải có đủ 3 phần:
- Thị trường: khách nhỏ chuyển từ sổ tay và Excel sang phần mềm; quan tâm dễ dùng, giá hợp lý, hỗ trợ nhanh, xem báo cáo trên điện thoại.
- Đối thủ: bảng 3 đối thủ A (giá rẻ), B (tầm trung), C (cao cấp); khoảng trống thị trường là gói tầm trung, dễ dùng, có bản điện thoại tốt.
- Số liệu: doanh thu tăng dần 3 tháng, Gói Cao cấp tăng nhanh hơn Gói Tiêu chuẩn.

**Bước 4. Kiểm phân vùng file.** Gõ vào Claude Code:
```
Cho tôi biết mỗi agent vừa rồi đã đọc những file nào, để tôi kiểm là các agent không đọc lấn thư mục của nhau.
```
Kết quả đúng: Agent 1 chỉ đọc `thi-truong/`, Agent 2 chỉ đọc `doi-thu/`, Agent 3 chỉ đọc `so-lieu/`.

---

## 5. Thao tác từng bước (phần B: việc thật của bạn)

**Bước 5. Chọn việc và tách phần.** Viết ra 2-3 phần độc lập của việc bạn chọn:

| Phần | Nội dung phần này làm gì | Tên thư mục |
|---|---|---|
| Phần 1 | | |
| Phần 2 | | |
| Phần 3 (nếu có) | | |

**Bước 6. Tổ chức file theo phần.** Tạo thư mục dự án, bên trong tạo mỗi phần một thư mục con, bỏ đúng file của phần đó vào. Ví dụ: `hop-tuan/bien-ban/`, `hop-tuan/so-lieu/`, `hop-tuan/viec-ton/`.

**Bước 7. Viết prompt chia việc song song.** Điền vào mẫu rồi gõ vào Claude Code:
```
Tôi có việc [tên việc] trong thư mục [tên-thu-muc-cua-toi]/.
Hãy chia cho [2 hoặc 3] agent chạy SONG SONG:
- Agent 1: chỉ đọc thư mục [phan-1]/ và [làm gì].
- Agent 2: chỉ đọc thư mục [phan-2]/ và [làm gì].
- Agent 3: chỉ đọc thư mục [phan-3]/ và [làm gì].
Mỗi agent chỉ đọc thư mục của mình. Sau khi xong, tổng hợp thành một bản chung và chỉ ra chỗ nào các phần chưa khớp.
```

**Bước 8. Chạy, để lead tổng hợp, đọc lại bản gom.** Kiểm 2 điều: các agent có đọc lấn thư mục nhau không; lead có kiểm mâu thuẫn số liệu chưa.

---

## 6. Prompt mẫu để copy nhanh (trích từ mẫu cấu hình agent-team)

Chia việc song song trên dự án ra mắt sản phẩm:
```
Tôi có một dự án ra mắt sản phẩm. Hãy chia thành các phần độc lập và giao cho nhiều agent chạy SONG SONG:
- Agent 1: đọc thư mục "thi-truong/" và tóm tắt bối cảnh thị trường.
- Agent 2: đọc "doi-thu/" và lập bảng so sánh đối thủ.
- Agent 3: đọc "so-lieu/" và phân tích số liệu bán hàng.
Mỗi agent chỉ đọc thư mục của mình. Sau khi cả ba xong, tổng hợp thành một bản tóm tắt chung cho tôi.
```

Câu dặn phân vùng file (luôn thêm vào cuối prompt):
```
Mỗi agent chỉ đọc và sửa thư mục của mình, không đụng thư mục của agent khác.
```

Câu dặn lead kiểm mâu thuẫn (luôn thêm khi cần gom số liệu):
```
Khi tổng hợp, hãy kiểm số liệu giữa các phần có khớp nhau không và chỉ ra chỗ lệch nếu có.
```

---

## 7. Sơ đồ team của bạn (điền vào)

Vẽ lại sơ đồ cho việc thật của bạn: ghi tên thư mục mỗi agent phụ trách và phần việc.
```
                 BẠN (lead qua Claude Code)
                 │  chia việc + phân vùng file
     ┌───────────┼───────────┐
     ▼           ▼           ▼
  Agent 1     Agent 2     Agent 3
  [____/]     [____/]     [____/]      (điền tên thư mục)
  làm: ___    làm: ___    làm: ___     (điền phần việc)
     └───────────┼───────────┘
                 ▼
        Lead tổng hợp + kiểm mâu thuẫn + xuất bản cuối
```

## 8. Ô ghi chú
- Việc mình chọn để chia team: ____________________________________________
- Việc này độc lập không? (nếu phần 2 chưa xong, phần 1 vẫn làm được không?): ______
- Chỗ lead phát hiện số liệu chưa khớp (nếu có): __________________________
- Điều mình còn thắc mắc: __________________________________________________

## 9. Bài tập
- **Tại lớp:** chạy xong team 3 agent trên thư mục demo và viết 1 prompt chia việc thật của mình cho 2-3 agent song song.
- **Về nhà:** chọn một việc thật khác, tổ chức thành các thư mục con theo phần, chạy team song song, lưu bản tổng hợp và vẽ sơ đồ team ai làm phần nào.

## 10. Checklist tự đánh giá
- [ ] Mình hiểu agent team là 1 lead chia việc cho nhiều agent, chạy song song, lead ghép lại.
- [ ] Mình đọc thuộc 4 nguyên tắc (độc lập, phân vùng file, song song, lead tổng hợp).
- [ ] Mình chạy được team 3 agent trên thư mục demo và nhận bản tổng hợp đủ 3 phần.
- [ ] Mình kiểm được các agent không đọc lấn thư mục của nhau.
- [ ] Mình viết được 1 prompt chia việc thật của mình cho 2-3 agent song song, có câu dặn phân vùng file.
- [ ] Mình phân biệt được việc nên chạy song song và việc phải làm tuần tự.
