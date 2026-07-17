# Workbook Buổi 06: Multi-Agent System + Capstone

> Buổi cuối khóa. Bạn không tạo agent mới. Bạn ghép cả 5 agent đã có thành 1 dây chuyền, dùng nó giải một việc thật của mình, rồi trình bày.

## Mục tiêu buổi này
Học xong buổi này, bạn:
1. Nâng cấp được Orchestrator để nó điều phối cả 5 agent chạy nhiều bước.
2. Thiết kế được dây chuyền cho 1 quy trình công việc thật của bạn.
3. Chạy được dây chuyền đó ra kết quả cuối hoàn chỉnh.
4. Biết tự rà mâu thuẫn và sửa khi 1 bước ra kết quả sai.
5. Trình bày được capstone: 1 lệnh tổng thay cho nhiều bước làm tay.

---

## Chuẩn bị trước khi vào buổi (làm ở nhà)
Chọn sẵn **1 quy trình công việc THẬT của bạn** để làm capstone. Tiêu chí chọn:
- Việc **nhiều bước** (ít nhất 3 bước).
- Việc **hay lặp lại** (tuần nào, tháng nào cũng làm).
- Việc bạn **có sẵn dữ liệu** để đưa vào (tài liệu, file Excel, hoặc chủ đề cần nghiên cứu).

Viết 1 dòng mô tả việc đó vào đây:

> Quy trình tôi chọn làm capstone: ________________________________________

Mang theo bộ file liên quan: tài liệu dài, file số liệu, email mẫu (tùy việc của bạn).

Gợi ý vài quy trình hay chọn:
- Sale: nghiên cứu khách hàng → đọc hồ sơ nhu cầu → phân tích lịch sử mua → viết đề xuất gửi khách.
- Kế toán: đọc chứng từ → tổng hợp số liệu → phân tích chênh lệch → viết báo cáo tháng.
- Marketing: nghiên cứu thị trường/đối thủ → tổng hợp số liệu chiến dịch → viết báo cáo + đề xuất kế hoạch.
- Quản lý: gom báo cáo các bộ phận → phân tích số → viết bản tổng hợp cho sếp.

---

## Phần 1: Thiết kế workflow của riêng bạn

Trước khi chạy, hãy vẽ dây chuyền trên giấy. Điền bảng sau. Mỗi dòng là 1 bước.

| Bước | Việc cần làm | Giao agent nào | Đầu vào (cần gì) | Đầu ra mong đợi |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |

**Nhắc chọn agent cho đúng:**
- **Deep Research Agent**: nghiên cứu thị trường, đối thủ, tổng hợp nhiều nguồn ngoài.
- **Document Agent**: đọc, tóm tắt, trích ý từ tài liệu dài của bạn.
- **Data Analysis Agent**: phân tích Excel/CSV, tính toán, tìm xu hướng, gợi ý biểu đồ.
- **Report Agent**: viết báo cáo, đề xuất, email, dàn ý slide.
- **Orchestrator**: trưởng nhóm: ra kế hoạch, chia việc, gom kết quả, rà mâu thuẫn.

**Quy tắc thứ tự:** bước sau chỉ chạy được khi đã có đầu ra bước trước làm nguyên liệu. Thường: nghiên cứu và đọc tài liệu trước, phân tích số ở giữa, viết báo cáo sau cùng. Nhưng thứ tự tùy bài của bạn.

Vẽ nhanh sơ đồ dây chuyền của bạn (điền tên agent vào ô):

```
Yêu cầu tổng: "____________________________________"
        │
   [1] __________________  → (đầu ra: ______________)
        ▼
   [2] __________________  → (đầu ra: ______________)
        ▼
   [3] __________________  → (đầu ra: ______________)
        ▼
   [4] __________________  → (đầu ra: ______________)
        ▼
   Orchestrator → rà mâu thuẫn, xuất bản cuối
```

---

## Phần 2: Thao tác từng bước chạy dây chuyền

1. Mở Orchestrator bạn đã dựng từ buổi 1. Vào phần Instructions / System prompt.
2. **Dán đè** toàn bộ system prompt nâng cấp ở Phần 3 bên dưới. Điền phần bối cảnh của bạn. Lưu lại.
3. Gõ **yêu cầu tổng** bằng 1 câu (chính là dòng bạn viết ở sơ đồ trên).
4. Đọc **kế hoạch các bước** Orchestrator trả về. Kiểm: đúng thứ tự chưa, đủ agent chưa, đầu ra mỗi bước có hợp lý không. Nếu ổn thì duyệt, chưa ổn thì bảo nó sửa.
5. Chạy dây chuyền:
   - **Nếu công cụ hỗ trợ agent tự gọi agent (full-auto):** để nó chạy hết, bạn theo dõi từng bước.
   - **Nếu chạy tay có điều phối:** làm lần lượt. Chạy bước 1, **copy nguyên khối kết quả**, dán sang agent bước 2 làm đầu vào. Cứ thế đến hết.
6. Đến bước cuối, yêu cầu Orchestrator **rà mâu thuẫn:** "Soi lại toàn bộ, số liệu giữa các bước có khớp không, có chỗ nào mâu thuẫn hay thiếu không."
7. Sửa chỗ lệch (xem Phần 5 nếu gặp lỗi), rồi lấy **output cuối hoàn chỉnh**.

**Mẹo khi chuyền kết quả:** copy nguyên cả khối, đừng copy nửa chừng. Thiếu nguyên liệu thì bước sau sẽ hỏi lại hoặc bịa.

---

## Phần 3: System prompt Orchestrator nâng cấp (COPY dán đè bản buổi 1)

```
Bạn là Orchestrator điều phối một QUY TRÌNH NHIỀU BƯỚC cho [Họ tên].

Khi tôi giao một yêu cầu lớn, bạn thiết kế và chạy quy trình:
1. Phân rã yêu cầu thành các bước, gán mỗi bước cho đúng agent:
   Research → Document → Data → Report (thứ tự tùy bài toán).
2. Với mỗi bước, nêu rõ: đầu vào cần gì, giao agent nào, đầu ra mong đợi.
3. Sau mỗi bước, TÓM TẮT kết quả và kiểm tra trước khi chuyển bước sau.
4. Ở bước cuối, tổng hợp toàn bộ thành một sản phẩm hoàn chỉnh.
5. Tự rà: các số liệu có nhất quán giữa các bước không? Có chỗ nào mâu thuẫn/thiếu?

QUY TẮC
- Luôn cho tôi thấy KẾ HOẠCH các bước trước khi chạy, để tôi duyệt.
- Chạy tuần tự, chuyền kết quả bước trước làm đầu vào bước sau.
- Không bịa dữ liệu ở bất kỳ bước nào; chỗ thiếu thì dừng hỏi tôi.
- Đầu ra cuối: gọn, đúng định dạng tôi cần, sẵn sàng dùng.

Kết mỗi lượt bằng: trạng thái quy trình (đang ở bước mấy) + việc tôi cần làm tiếp.
```

Nhớ điền [Họ tên] và giữ nguyên phần bối cảnh bạn đã điền từ buổi 1 (công việc chính, loại việc lặp lại, định dạng đầu ra hay cần, văn phong).

---

## Phần 4: Rubric tự đánh giá capstone

Tự chấm dây chuyền của bạn. Đạt cả 5 ô là hoàn thành capstone.

- [ ] **Chọn đúng bài.** Quy trình thật, nhiều bước, hay lặp lại.
- [ ] **Kế hoạch rõ.** Có bảng bước - agent - đầu vào - đầu ra đầy đủ.
- [ ] **Chạy được.** Dây chuyền ra output cuối hoàn chỉnh (không dở dang giữa chừng).
- [ ] **Đã rà mâu thuẫn.** Đã soi số liệu giữa các bước, xử lý nếu có chỗ lệch.
- [ ] **Trình bày được.** Nói được: bài toán, cách ghép agent, kết quả, tiết kiệm được gì.

Điểm cộng (không bắt buộc):
- [ ] Chạy được bản full-auto (1 lệnh tổng ra hết).
- [ ] Lưu lại thành file "quy trình chuẩn" để tái dùng.

---

## Phần 5: Gặp lỗi thì làm gì

| Bạn gặp | Bạn làm |
|---|---|
| Số ở bước này khác số ở bước kia | Đừng lấy kết quả đi dùng vội. Hỏi Orchestrator hai số đến từ nguồn nào. Ưu tiên số từ dữ liệu thật của bạn (file Excel) hơn số nghiên cứu ngoài. Không rõ thì ghi "cần kiểm tra lại". |
| 1 bước ra kết quả sai, các bước sau sai theo | Đừng sửa ở bước cuối. Quay lại đúng bước bị sai, sửa đầu vào hoặc bảo làm lại bước đó, rồi chạy lại từ đó xuống. Vá ở gốc, không vá ở ngọn. |
| Bài quá to, không kịp trong buổi | Cắt nhỏ. Chọn 1 lát gọn (1 tuần, 1 sản phẩm) chạy trọn dây chuyền, phần còn lại làm ở nhà. |
| Công cụ không cho agent tự gọi agent | Chạy tay: Orchestrator ra kế hoạch, bạn copy kết quả bước trước dán sang bước sau. Kết quả như nhau. |
| Nó tự chạy hết, không cho duyệt kế hoạch | Thêm câu "cho tôi xem kế hoạch trước khi chạy" vào yêu cầu. Kiểm lại đã dán đúng system prompt nâng cấp chưa. |
| Bước sau hỏi lại thông tin đã có ở bước trước | Bạn copy chưa đủ. Copy lại nguyên khối kết quả bước trước. |

---

## Phần 6: Gợi ý ý tưởng workflow theo nghề

Chọn hoặc lấy cảm hứng để dựng capstone.

**Sale**
- Chốt khách mới: Research (tìm hiểu công ty khách) → Document (đọc hồ sơ nhu cầu khách gửi) → Report (viết đề xuất + email chào).
- Báo cáo pipeline tuần: Data (phân tích danh sách deal) → Report (viết tổng hợp cho trưởng phòng).

**Kế toán**
- Báo cáo tài chính tháng: Document (đọc chứng từ, ghi chú) → Data (tổng hợp + phân tích chênh lệch) → Report (viết báo cáo tháng).
- Giải trình số liệu: Data (soi khoản bất thường) → Report (viết bản giải trình).

**Marketing**
- Đánh giá chiến dịch: Research (thị trường + đối thủ) → Data (số liệu chiến dịch) → Report (báo cáo + đề xuất kế hoạch sau).
- Nghiên cứu ra brief nội dung: Research (xu hướng chủ đề) → Report (dàn ý content tháng).

**Quản lý / trưởng nhóm**
- Bản tổng hợp cho sếp: Document (gom báo cáo các bộ phận) → Data (phân tích số chung) → Report (viết bản tổng hợp).
- Chuẩn bị họp: Research + Document → Report (dàn ý slide + điểm cần chốt).

**Chủ doanh nghiệp nhỏ**
- Nhìn lại tháng: Data (số bán hàng, chi phí) → Research (so với thị trường) → Report (báo cáo + việc cần làm tháng sau).
- Ra quyết định mở sản phẩm mới: Research (nhu cầu + đối thủ) → Data (số nội bộ) → Report (đề xuất có/không kèm lý do).

---

## Phần 7: Checklist "tôi đã có gì sau cả khóa"

Tick từng ô. Đủ hết là bạn đã hoàn thành khóa.

- [ ] **Orchestrator (nâng cấp)**: trưởng nhóm điều phối cả dây chuyền.
- [ ] **Document Agent**: đọc, tóm tắt, trích ý tài liệu dài.
- [ ] **Data Analysis Agent**: phân tích Excel/CSV, tìm xu hướng, gợi ý biểu đồ.
- [ ] **Report Agent**: viết báo cáo, đề xuất, email, dàn ý slide.
- [ ] **Deep Research Agent**: nghiên cứu thị trường, đối thủ, tổng hợp nhiều nguồn.
- [ ] **Hệ Multi-Agent**: 1 dây chuyền ghép cả 5 agent chạy end-to-end.
- [ ] **Bộ system prompt chuẩn** cho từng agent, copy dùng lại được.
- [ ] **1 capstone** giải đúng việc thật của tôi, đã trình bày.

> Từ nay, mỗi việc lặp lại chỉ còn 1 lệnh tổng thay vì làm thủ công nhiều bước. Đó là thứ bạn giữ lại sau khóa. Mỗi tuần chọn thêm 1 việc để đóng gói thành agent, kỹ năng sẽ mạnh dần.
