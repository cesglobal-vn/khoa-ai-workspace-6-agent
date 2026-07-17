# Workbook Buổi 04: Subagent - Tạo agent chuyên trách

> Sổ tay thực hành cho học viên. Làm theo từng bước đánh số. Chỗ nào có ô ghi chú thì viết vào để nhớ.

## Mục tiêu buổi này
Sau buổi 4, bạn sẽ tự tay:
1. Tạo được một subagent: một agent con chỉ lo một việc, có tên riêng, lời dặn riêng, và bộ công cụ riêng.
2. Hiểu file định nghĩa agent nằm ở đâu và gồm những phần nào.
3. Tạo report-agent để soạn báo cáo và research-agent để nghiên cứu thị trường.
4. Tạo một agent cho đúng một việc lặp lại của nghề bạn.

## Subagent là gì (nhắc nhanh)
- Ba buổi trước bạn nói chuyện với một Claude Code làm mọi việc. Subagent là cách tách một việc ra cho một "nhân viên chuyên trách".
- Bạn định nghĩa agent bằng một file văn bản trong thư mục `.claude/agents/`. Không cần lập trình.
- File agent có 2 phần: phần đầu là mấy dòng khai báo giữa hai dấu `---` (YAML), phần sau là lời dặn agent làm gì.
- Ba dòng khai báo quan trọng:
  - `name`: tên agent, để bạn gọi đích danh.
  - `description`: agent này chuyên việc gì. Dòng này quyết định khi nào Claude Code tự động gọi agent ra làm.
  - `tools`: danh sách công cụ agent được phép dùng. Không cấp thì agent không có quyền đó. Đây là cách khoanh vùng cho an toàn.

## Chuẩn bị trước khi làm
- [ ] Mở Claude Code trên Claude Desktop, đứng trong thư mục dự án của khóa.
- [ ] Nghĩ sẵn 1 việc bạn làm đi làm lại hàng tuần, có công thức rõ, để cuối buổi biến nó thành agent. Ví dụ: trả lời tin nhắn khách theo mẫu, soạn lịch đăng bài, chốt đơn, dựng đề bài chấm, tóm tắt cuộc họp.

Viết việc lặp lại của bạn vào đây:

```
Việc lặp lại của tôi: ...........................................................
Đầu vào thường có: ..............................................................
Kết quả tôi muốn nhận: ..........................................................
```

---

## Phần A: Tạo report-agent và chạy trên số liệu bán hàng

**Bước 1: Tạo file định nghĩa report-agent.** Gõ prompt sau vào Claude Code.
```
Tạo file .claude/agents/report-agent.md để định nghĩa một subagent chuyên soạn văn bản công việc.
Yêu cầu:
- Phần đầu YAML có name là report-agent, description nói rõ agent chuyên soạn báo cáo, đề xuất, email, dàn ý slide từ số liệu hoặc ý thô, dùng khi cần biến dữ liệu thành văn bản công sở hoàn chỉnh.
- tools chỉ gồm: Read, Write, Grep, Glob.
- Phần thân dặn: tiếng Việt chuẩn công sở, không emoji trong báo cáo và email, không bịa số, chỗ thiếu để [đợi bổ sung], thiếu thông tin cốt lõi thì hỏi tối đa 3 câu trước khi soạn.
Tạo xong đọc lại nội dung file cho tôi xem.
```

**Bước 2: Kiểm tra file agent.** Nhìn nội dung Claude đọc lại, tự soát 3 điểm:
- [ ] Có khối YAML giữa hai dấu `---` với đúng 3 khóa: name, description, tools.
- [ ] Dòng tools chỉ có Read, Write, Grep, Glob (không có công cụ web).
- [ ] Phần thân có quy tắc không bịa số và không emoji.

**Bước 3: Giao việc cho report-agent.**
```
Nhờ report-agent soạn báo cáo bán hàng tháng 3 dựa trên số liệu trong file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md.
Báo cáo cần có các mục: kết quả tháng 3, số liệu chính, vướng mắc, kế hoạch tháng 4.
Không được bịa thêm con số nào ngoài file.
```

**Bước 4: Đối chiếu kết quả.** Báo cáo trả về phải:
- [ ] Có 4 mục: kết quả, số liệu chính, vướng mắc, kế hoạch tháng 4.
- [ ] Số đúng file: doanh thu tháng 3 khoảng 1.085 triệu, tháng 2 khoảng 915 triệu, TP HCM tốt hơn Hà Nội.
- [ ] Không có emoji, không có con số nào ngoài file.

Mở file gốc `so-lieu-ban-hang-thang.md` so lại vài con số để chắc agent không bịa.

---

## Phần B: Tạo research-agent và chạy đề bài nghiên cứu

**Bước 5: Tạo file định nghĩa research-agent.** Agent này khác report-agent ở chỗ được phép lên mạng tra, nên tools có thêm công cụ web.
```
Tạo file .claude/agents/research-agent.md để định nghĩa một subagent chuyên nghiên cứu thị trường và phân tích đối thủ.
Yêu cầu:
- YAML: name là research-agent, description nói rõ agent chuyên nghiên cứu thị trường, phân tích đối thủ, tổng hợp đa nguồn thành báo cáo có cấu trúc và trích nguồn, dùng khi cần tìm hiểu một chủ đề trước khi ra quyết định.
- tools gồm: Read, Write, Grep, Glob, WebSearch, WebFetch.
- Phần thân dặn: chia chủ đề thành câu hỏi con, mỗi câu trả lời nêu nguồn; nếu phân tích đối thủ thì làm bảng so sánh; báo cáo theo cấu trúc tóm tắt điều hành, phát hiện chính, bảng so sánh đối thủ, insight và khuyến nghị, phần nguồn và điểm cần kiểm chứng; tách rõ dữ kiện có nguồn với suy luận; không bịa số liệu và không bịa nguồn.
Tạo xong đọc lại file cho tôi xem.
```

**Bước 6: Giao đề bài nghiên cứu.**
```
Nhờ research-agent làm theo yêu cầu trong file tai-lieu-phat/demo/buoi-04/yeu-cau-nghien-cuu.md.
Trả về báo cáo có tóm tắt điều hành, bảng so sánh đối thủ, và tách rõ chỗ nào là dữ kiện chỗ nào cần kiểm chứng thêm.
```

**Bước 7: Đối chiếu kết quả.** Báo cáo trả về phải:
- [ ] Có phần tóm tắt điều hành (5 tới 7 dòng).
- [ ] Có bảng so sánh 3 tới 4 đối thủ (sản phẩm, giá, điểm mạnh, điểm yếu, định vị).
- [ ] Có phần khuyến nghị điểm khác biệt để cạnh tranh.
- [ ] Có phần cuối tách rõ đâu là dữ kiện, đâu là chỗ "cần kiểm chứng".

---

## Phần C: Tạo 1 agent cho nghề của bạn

**Bước 8: Tạo file agent của bạn.** Điền các chỗ trong ngoặc theo việc lặp lại bạn đã ghi ở phần chuẩn bị.
```
Tạo file .claude/agents/[ten-agent].md định nghĩa một subagent chuyên [việc lặp lại của tôi].
Yêu cầu:
- YAML: name là [ten-agent]; description nêu rõ agent chuyên [việc gì] và dùng khi nào; tools chỉ gồm các công cụ thật sự cần (chỉ đọc ghi file thì để Read, Write, Grep, Glob; cần tra web mới thêm WebSearch, WebFetch).
- Phần thân: mô tả vai trò, các bước agent nên làm, định dạng đầu ra mong muốn, và quy tắc bắt buộc (ví dụ không bịa số, không emoji, thiếu thông tin thì hỏi trước).
Tạo xong đọc lại file cho tôi xem.
```

**Bước 9: Giao một việc mẫu để thử.**
```
Nhờ [ten-agent] xử lý việc sau: [dán một tình huống thật hoặc một file dữ liệu của tôi].
```

**Bước 10: Chỉnh dòng description cho lead gọi đúng.** Thử giao lại việc mà không gọi tên agent (chỉ mô tả việc). Nếu Claude Code không tự chọn đúng agent của bạn, sửa dòng description cho cụ thể hơn: nêu rõ loại việc và cụm "dùng khi nào", rồi thử lại.

---

## Hai mẫu agent để copy nhanh

### Mẫu 1: report-agent
```markdown
---
name: report-agent
description: Chuyên soạn báo cáo, đề xuất, email, dàn ý slide từ số liệu/ý thô. Dùng khi cần biến dữ liệu thành văn bản hoàn chỉnh theo văn phong công sở.
tools: Read, Write, Grep, Glob
---

Bạn là Report Agent, chuyên soạn văn bản công việc.

Từ dữ liệu/ý thô được giao, soạn ra bản hoàn chỉnh cho một trong các loại:
- BÁO CÁO (tuần/tháng/dự án): mở đầu, nội dung chính, kết quả, vướng mắc, đề xuất.
- ĐỀ XUẤT: bối cảnh, vấn đề, giải pháp, lợi ích, chi phí, kế hoạch.
- EMAIL: tiêu đề + thân email đúng văn phong, có lời chào/kết.
- DÀN Ý SLIDE: từng slide (tiêu đề + 3 tới 5 gạch ý).

QUY TẮC
- Tiếng Việt chuẩn công sở. KHÔNG dùng emoji trong email và báo cáo.
- KHÔNG bịa số liệu; chỗ thiếu để [đợi bổ sung].
- Nếu thiếu thông tin cốt lõi (người nhận, mục đích), hỏi tối đa 3 câu trước khi soạn.
- Trả kết quả gọn, sẵn sàng dùng.
```

### Mẫu 2: research-agent
```markdown
---
name: research-agent
description: Chuyên nghiên cứu thị trường, phân tích đối thủ, tổng hợp đa nguồn thành báo cáo có cấu trúc và trích nguồn. Dùng khi cần tìm hiểu một chủ đề trước khi ra quyết định.
tools: Read, Write, Grep, Glob, WebSearch, WebFetch
---

Bạn là Research Agent, chuyên nghiên cứu.

Khi được giao một chủ đề:
1. Chia chủ đề thành các câu hỏi con cần trả lời.
2. Với mỗi câu hỏi, tổng hợp thông tin và nêu rõ nguồn (trích link nếu có công cụ web).
3. Nếu là phân tích đối thủ, làm bảng so sánh: sản phẩm, giá, điểm mạnh, điểm yếu, định vị.
4. Kết luận: insight chính, cơ hội, rủi ro, khuyến nghị.

ĐỊNH DẠNG BÁO CÁO
1. TÓM TẮT ĐIỀU HÀNH (5 tới 7 dòng)
2. PHÁT HIỆN CHÍNH (theo từng câu hỏi con, có nguồn)
3. BẢNG SO SÁNH ĐỐI THỦ (nếu có)
4. INSIGHT & KHUYẾN NGHỊ
5. NGUỒN / ĐIỂM CẦN KIỂM CHỨNG THÊM

QUY TẮC
- Tách rõ: đâu là DỮ KIỆN có nguồn, đâu là SUY LUẬN, đâu là chỗ CHƯA CHẮC.
- KHÔNG bịa số liệu thị trường, KHÔNG bịa nguồn. Không chắc thì ghi "cần kiểm chứng".
- Trung lập, nêu cả điểm mạnh lẫn điểm yếu.
```

---

## Ô ghi chú của tôi
Ghi lại điều mình học được, lỗi mình gặp, cách xử lý:

```
Ghi chú 1: ......................................................................
.................................................................................
Ghi chú 2: ......................................................................
.................................................................................
Lỗi tôi gặp và cách sửa: ........................................................
.................................................................................
```

## Bài tập
- **Tại lớp:** hoàn thành Phần A, B, C. Có ít nhất 2 file agent chạy được và 1 agent cho nghề của mình.
- **Về nhà:** chỉnh dòng description của agent nghề mình cho thật rõ. Thử 3 lần giao việc không gọi tên agent, kiểm tra Claude Code có tự gọi đúng agent không. Viết 2 câu: agent của mình chuyên việc gì, và mình đã khoanh tools thế nào cho an toàn.

## Checklist tự đánh giá
- [ ] Tôi hiểu subagent là agent con chuyên một việc, có name, description, tools riêng.
- [ ] Tôi biết file agent nằm trong `.claude/agents/` và gồm phần YAML với phần thân.
- [ ] report-agent của tôi soạn được báo cáo bán hàng đúng số liệu file, đủ 4 mục, không emoji, không bịa số.
- [ ] research-agent của tôi ra báo cáo có tóm tắt điều hành, bảng so sánh đối thủ, và phần cần kiểm chứng.
- [ ] Tôi tạo được 1 agent cho việc thật của mình, description rõ và tools đúng phạm vi.
- [ ] Tôi giải thích được vì sao description quyết định lead gọi agent, và vì sao tools là cách khoanh vùng an toàn.
