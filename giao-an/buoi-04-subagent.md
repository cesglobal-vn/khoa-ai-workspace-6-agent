# Giáo án Buổi 04: Subagent - Tạo agent chuyên trách

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

## Thông tin buổi
- **Buổi:** 04 / 6
- **Khái niệm chính:** Subagent (agent con chuyên trách)
- **Loại:** Thực chiến
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đứng trong thư mục dự án của khóa
- [ ] Mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-04/`
- [ ] File demo cần dùng: `so-lieu-ban-hang-thang.md`, `yeu-cau-nghien-cuu.md`
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/agent-report-mau.md`, `mau-cau-hinh/agent-research-mau.md`
- [ ] Kiểm tra thư mục `.claude/agents/` đã tồn tại chưa; nếu chưa, để Claude tự tạo khi lưu file agent đầu tiên
- [ ] Xóa sẵn các file agent cũ trong `.claude/agents/` để lớp thấy quá trình tạo mới từ đầu

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu subagent là gì: một agent con chỉ lo một việc, có vai trò riêng, chỉ dẫn riêng, và bộ công cụ (tools) được khoanh vùng riêng.
2. Đọc và viết được file định nghĩa agent trong `.claude/agents/<ten>.md`: phần đầu YAML (name, description, tools) và phần thân chỉ dẫn.
3. Tự tay tạo report-agent, giao việc, nhận về một báo cáo hoàn chỉnh không bịa số.
4. Tự tay tạo research-agent, giao một đề bài nghiên cứu, nhận về báo cáo có tóm tắt điều hành và bảng so sánh đối thủ.
5. Tạo được 1 subagent cho chính công việc lặp lại của nghề mình.

## Kết quả cầm về (deliverable)
- Ít nhất 2 file agent chạy được trong `.claude/agents/` (report-agent + research-agent hoặc report-agent + 1 agent nghề của học viên).
- 1 báo cáo bán hàng do report-agent soạn từ file số liệu thô.
- 1 báo cáo nghiên cứu thị trường do research-agent soạn từ đề bài.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Subagent là gì:** ở 3 buổi trước, học viên nói chuyện với một Claude Code duy nhất, kiêm hết mọi việc. Subagent là cách tách một việc cụ thể ra cho một "nhân viên chuyên trách". Ví dụ: một agent chỉ chuyên viết báo cáo, một agent chỉ chuyên nghiên cứu. Mỗi agent có tính cách và giới hạn riêng do mình đặt.
- **Định nghĩa bằng một file:** không cần lập trình. Chỉ cần tạo một file văn bản trong thư mục `.claude/agents/`, đặt tên ví dụ `report-agent.md`. File gồm 2 phần: phần đầu là mấy dòng khai báo giữa hai dấu `---` (gọi là YAML), phần sau là lời dặn agent làm gì.
- **Ba dòng khai báo quan trọng:**
  - `name`: tên gọi của agent, để mình gọi đích danh.
  - `description`: mô tả agent này chuyên việc gì. Dòng này quyết định khi nào Claude Code (đóng vai lead, tức người điều phối) tự động gọi agent ra làm. Mô tả càng rõ, gọi càng đúng.
  - `tools`: danh sách công cụ agent được phép dùng, ví dụ Read (đọc file), Write (ghi file), WebSearch (tra web). Không liệt kê thì agent không có quyền đó. Đây là cách khoanh vùng cho an toàn: agent viết báo cáo thì không cần quyền lên mạng.
- **Nối với 3 buổi trước:** Buổi 1 làm quen agent (Claude Code). Buổi 2 đóng gói quy trình lặp lại thành skill. Buổi 3 cắm công cụ ngoài bằng MCP. Buổi 4 này: tạo nhiều agent chuyên trách. Buổi 5 sẽ cho nhiều agent chạy song song thành một đội.

---

## Timeline chi tiết (theo phút)

Mỗi mục demo/thực hành trình bày theo khối 4 dòng.

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn GV:** "Ba buổi vừa rồi mình dạy một Claude Code làm mọi việc. Hôm nay mình tách việc ra: mỗi việc giao cho một agent con chuyên trách. Cuối buổi mỗi người có ít nhất hai nhân viên AI riêng: một chuyên viết báo cáo, một chuyên nghiên cứu."
- Recap nhanh buổi 1-3 bằng 3 câu hỏi mở:
  - Buổi 1: agent khác chat thường ở điểm nào? (Trả lời gợi ý: tự làm nhiều bước, đọc sửa file thật, nhớ bối cảnh.)
  - Buổi 2: skill để làm gì? (Đóng gói quy trình lặp lại.)
  - Buổi 3: MCP để làm gì? (Cắm công cụ và dữ liệu ngoài.)
- Nêu mục tiêu buổi hôm nay: hiểu subagent, viết được file agent, tạo report-agent + research-agent, và tạo 1 agent cho nghề của mình.

### [00:15-00:35] Lý thuyết ngắn: subagent và cấu trúc file agent
- **Lời dẫn GV:** "Hình dung mình là trưởng phòng. Thay vì tự làm hết, mình tuyển hai nhân viên. Mỗi nhân viên có một bản mô tả công việc dán trên bàn: tên, chuyên việc gì, được dùng công cụ nào. File agent chính là bản mô tả công việc đó."
- Nội dung trình chiếu, mở file mẫu `mau-cau-hinh/agent-report-mau.md` cho lớp nhìn cấu trúc thật:
  - Giải thích khối YAML giữa hai dấu `---`: `name`, `description`, `tools`.
  - Nhấn 3 ý: **description quyết định khi nào lead gọi agent**; **tools khoanh vùng cho an toàn**; **phần thân là lời dặn agent làm gì và giữ quy tắc gì** (ví dụ không bịa số, không emoji).
  - Chỉ ra dòng `tools: Read, Write, Grep, Glob` của report-agent: chỉ đọc ghi tìm file, cố tình không cho lên mạng. So với research-agent có thêm `WebSearch, WebFetch` vì cần tra ngoài.
- **Câu hỏi tương tác:** "Nếu mình để description mập mờ kiểu 'agent xử lý văn bản', theo các anh chị lead sẽ dễ gọi đúng hay dễ gọi nhầm?" (Dẫn tới ý: description phải nêu rõ loại việc và khi nào dùng.)

### [00:35-01:00] Demo giảng viên: tạo report-agent và chạy trên số liệu thật
> Trình bày mỗi bước demo theo mẫu 4 dòng.

**Bước 1: Tạo file định nghĩa report-agent**
- **Lời dẫn GV:** "Mình không tự gõ file. Mình tả cho Claude Code, nó tạo hộ. Nhìn lên màn hình, mình yêu cầu tạo một agent chuyên viết báo cáo."
- **Prompt gõ vào Claude Code:**
  ```
  Tạo file .claude/agents/report-agent.md để định nghĩa một subagent chuyên soạn văn bản công việc.
  Yêu cầu:
  - Phần đầu YAML có name là report-agent, description nói rõ agent chuyên soạn báo cáo, đề xuất, email, dàn ý slide từ số liệu hoặc ý thô, dùng khi cần biến dữ liệu thành văn bản công sở hoàn chỉnh.
  - tools chỉ gồm: Read, Write, Grep, Glob.
  - Phần thân dặn: tiếng Việt chuẩn công sở, không emoji trong báo cáo và email, không bịa số, chỗ thiếu để [đợi bổ sung], thiếu thông tin cốt lõi thì hỏi tối đa 3 câu trước khi soạn.
  Tạo xong đọc lại nội dung file cho tôi xem.
  ```
- **File demo:** dùng nội dung mẫu ở `mau-cau-hinh/agent-report-mau.md` để đối chiếu file agent vừa tạo.
- **Kết quả mong đợi:** Claude Code tạo file `.claude/agents/report-agent.md`. Mở ra thấy khối YAML có đúng 3 khóa `name`, `description`, `tools` (đúng 4 công cụ Read, Write, Grep, Glob, không có công cụ web), và phần thân có các quy tắc không bịa số, không emoji. Nếu Claude thêm công cụ lạ (ví dụ WebSearch), GV chỉ ra và yêu cầu bỏ.

**Bước 2: Giao việc cho report-agent chạy trên file số liệu**
- **Lời dẫn GV:** "Có nhân viên rồi thì giao việc. Mình đưa file ghi chú bán hàng thô, nhờ đúng report-agent soạn thành báo cáo tháng."
- **Prompt gõ vào Claude Code:**
  ```
  Nhờ report-agent soạn báo cáo bán hàng tháng 3 dựa trên số liệu trong file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md.
  Báo cáo cần có các mục: kết quả tháng 3, số liệu chính, vướng mắc, kế hoạch tháng 4.
  Không được bịa thêm con số nào ngoài file.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md`
- **Kết quả mong đợi:** report-agent trả về báo cáo có 4 mục rõ ràng. Số liệu đúng như file: doanh thu tháng 3 khoảng 1.085 triệu, tháng 2 khoảng 915 triệu, TP HCM tốt hơn Hà Nội, Gói Cao cấp tăng nhanh. Nêu đúng vướng mắc (đơn chờ thanh toán An Phát và Đại Tín, đơn hủy Hải Nam, thiếu nhân sự giao hàng Hà Nội) và kế hoạch tháng 4 (đẩy Gói Cao cấp ở TP HCM, chăm lại khách hủy, tuyển 1 nhân sự giao hàng). Không có emoji, không có con số nào ngoài file. GV mở file gốc so từng số để chứng minh agent không bịa.

**Bước 3: Chỉ ra vai trò của description**
- **Lời dẫn GV:** "Để ý là mình gọi 'nhờ report-agent'. Nhưng nếu mình chỉ nói 'soạn giúp báo cáo' mà không gọi tên, lead vẫn tự chọn agent nhờ dòng description. Mình thử."
- **Prompt gõ vào Claude Code:**
  ```
  Từ file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md, hãy soạn giúp một báo cáo bán hàng tháng 3 hoàn chỉnh theo văn phong công sở.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md`
- **Kết quả mong đợi:** lead tự nhận ra đây là việc soạn văn bản công sở nên gọi report-agent (nhờ dòng description khớp). GV chốt: description viết rõ thì lead gọi đúng agent mà không cần mình gọi tên.

### [01:00-01:30] Thực hành 1: học viên tạo research-agent và chạy đề bài nghiên cứu
- **Lời dẫn GV:** "Đến lượt anh chị. Lần này tạo một nhân viên khác: chuyên nghiên cứu thị trường. Khác report-agent ở chỗ nó được phép lên mạng tra thông tin, nên tools có thêm công cụ web."
- **Đề bài:** mỗi học viên tạo file `.claude/agents/research-agent.md` rồi giao đề bài nghiên cứu trong file demo cho agent chạy.
- **Prompt gợi ý cho học viên (bước tạo agent):**
  ```
  Tạo file .claude/agents/research-agent.md để định nghĩa một subagent chuyên nghiên cứu thị trường và phân tích đối thủ.
  Yêu cầu:
  - YAML: name là research-agent, description nói rõ agent chuyên nghiên cứu thị trường, phân tích đối thủ, tổng hợp đa nguồn thành báo cáo có cấu trúc và trích nguồn, dùng khi cần tìm hiểu một chủ đề trước khi ra quyết định.
  - tools gồm: Read, Write, Grep, Glob, WebSearch, WebFetch.
  - Phần thân dặn: chia chủ đề thành câu hỏi con, mỗi câu trả lời nêu nguồn; nếu phân tích đối thủ thì làm bảng so sánh; báo cáo theo cấu trúc tóm tắt điều hành, phát hiện chính, bảng so sánh đối thủ, insight và khuyến nghị, phần nguồn và điểm cần kiểm chứng; tách rõ dữ kiện có nguồn với suy luận; không bịa số liệu và không bịa nguồn.
  Tạo xong đọc lại file cho tôi xem.
  ```
- **Prompt gợi ý cho học viên (bước giao việc):**
  ```
  Nhờ research-agent làm theo yêu cầu trong file tai-lieu-phat/demo/buoi-04/yeu-cau-nghien-cuu.md.
  Trả về báo cáo có tóm tắt điều hành, bảng so sánh đối thủ, và tách rõ chỗ nào là dữ kiện chỗ nào cần kiểm chứng thêm.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-04/yeu-cau-nghien-cuu.md` (đối chiếu mẫu ở `mau-cau-hinh/agent-research-mau.md`)
- **Kết quả mong đợi:** research-agent trả về báo cáo có phần TÓM TẮT ĐIỀU HÀNH (5 tới 7 dòng), có BẢNG SO SÁNH 3 tới 4 đối thủ (cột sản phẩm, giá, điểm mạnh, điểm yếu, định vị), phần khuyến nghị điểm khác biệt để cạnh tranh, và phần cuối tách rõ đâu là dữ kiện đâu là điểm "cần kiểm chứng". Con số thị trường nào không chắc phải được ghi "cần kiểm chứng" thay vì khẳng định chắc. GV đi quanh lớp kiểm tra 3 điểm: có bảng so sánh chưa, có phần cần kiểm chứng chưa, tools có đủ công cụ web chưa.

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2: tạo 1 subagent cho nghề của học viên
- **Lời dẫn GV:** "Hai agent vừa rồi là ví dụ chung. Giờ mình làm agent cho đúng việc của mình. Nghĩ một việc anh chị làm đi làm lại hàng tuần, có công thức: trả lời tin nhắn khách theo mẫu, soạn lịch đăng bài, chốt đơn, dựng đề bài chấm. Mình biến việc đó thành một agent chuyên trách."
- **Đề bài:** mỗi học viên chọn một việc lặp lại của nghề mình, tạo một file agent mới trong `.claude/agents/`, rồi giao một việc mẫu để kiểm tra agent chạy đúng.
- **Prompt gợi ý (bước tạo, học viên điền chỗ trong ngoặc):**
  ```
  Tạo file .claude/agents/[ten-agent].md định nghĩa một subagent chuyên [việc lặp lại của tôi].
  Yêu cầu:
  - YAML: name là [ten-agent]; description nêu rõ agent chuyên [việc gì] và dùng khi nào; tools chỉ gồm các công cụ thật sự cần (nếu chỉ đọc và ghi file thì để Read, Write, Grep, Glob; cần tra web mới thêm WebSearch, WebFetch).
  - Phần thân: mô tả vai trò, các bước agent nên làm, định dạng đầu ra mong muốn, và quy tắc bắt buộc (ví dụ không bịa số, không emoji, thiếu thông tin thì hỏi trước).
  Tạo xong đọc lại file cho tôi xem.
  ```
- **Prompt gợi ý (bước giao việc mẫu):**
  ```
  Nhờ [ten-agent] xử lý việc sau: [dán một tình huống thật hoặc một file dữ liệu của tôi].
  ```
- **Kết quả mong đợi:** mỗi học viên có thêm 1 file agent trong `.claude/agents/` với description rõ ràng và tools khoanh đúng phạm vi, chạy thử ra kết quả dùng được cho công việc thật. GV nhắc: nếu lead không tự gọi đúng agent, sửa lại dòng description cho cụ thể hơn.

### [02:15-02:35] Chốt & giao bài
- **Lời dẫn GV:** "Hôm nay mình đi từ một Claude Code kiêm hết sang việc tách ra nhiều nhân viên chuyên trách. Một điểm cần nhớ: sức mạnh nằm ở dòng description (để lead gọi đúng) và dòng tools (để khoanh vùng an toàn). Buổi sau mình cho hai nhân viên này làm cùng lúc: research xong đưa thẳng cho report viết đề xuất."
- Tổng kết 3 ý: subagent là agent con chuyên một việc; định nghĩa bằng file trong `.claude/agents/` có YAML và thân; description và tools là hai dòng quan trọng nhất.
- Demo ghép nhanh (nếu còn thời gian): giao chuỗi "research-agent nghiên cứu theo yeu-cau-nghien-cuu.md, xong đưa kết quả cho report-agent viết thành một bản đề xuất đẩy Gói Cao cấp".
- Bài về nhà và xem trước buổi 5 (Agent Team: một lead chia việc cho nhiều agent chạy song song).

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Tạo file `.claude/agents/report-agent.md` với YAML name/description/tools (Read, Write, Grep, Glob) và thân dặn không bịa số, không emoji | `mau-cau-hinh/agent-report-mau.md` (đối chiếu) | File agent đúng cấu trúc, tools không có công cụ web |
| 2 | Nhờ report-agent soạn báo cáo bán hàng tháng 3 từ file số liệu | `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md` | Báo cáo 4 mục (kết quả, số liệu, vướng mắc, kế hoạch), số đúng file, không emoji, không bịa |
| 3 | Soạn giúp báo cáo bán hàng (không gọi tên agent) | `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md` | Lead tự gọi report-agent nhờ description khớp |
| 4 | Tạo file `.claude/agents/research-agent.md`, tools có thêm WebSearch, WebFetch | `mau-cau-hinh/agent-research-mau.md` (đối chiếu) | File agent có công cụ web, thân yêu cầu tách dữ kiện với suy luận |
| 5 | Nhờ research-agent làm theo `yeu-cau-nghien-cuu.md` | `tai-lieu-phat/demo/buoi-04/yeu-cau-nghien-cuu.md` | Báo cáo có tóm tắt điều hành, bảng so sánh đối thủ, phần cần kiểm chứng |
| 6 | Tạo 1 agent cho nghề của học viên rồi giao việc mẫu | Dữ liệu thật của học viên | Agent mới chạy ra kết quả dùng được, description rõ, tools đúng phạm vi |
| 7 | Ghép chuỗi: research-agent nghiên cứu, đưa kết quả cho report-agent viết đề xuất | 2 file demo buổi 04 | 1 bản đề xuất hoàn chỉnh dựa trên kết quả nghiên cứu |

## Câu hỏi tương tác gợi ý
- "Một Claude Code làm hết mọi việc có được không? Vậy tại sao mình lại tách ra nhiều agent?" (Dẫn tới: mỗi agent chuyên sâu hơn, giữ quy tắc riêng, an toàn hơn nhờ khoanh tools.)
- "Trong ba dòng name, description, tools, dòng nào quyết định khi nào lead tự gọi agent?" (Đáp: description.)
- "Agent viết báo cáo có cần quyền lên mạng không? Nếu cho quyền đó thì rủi ro gì?" (Dẫn tới: chỉ cấp tools thật sự cần.)
- "Làm sao biết agent có bịa số không?" (Đáp: mở file gốc so từng số; agent tốt phải ghi [đợi bổ sung] hoặc 'cần kiểm chứng' thay vì bịa.)

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Description mờ (ví dụ chỉ ghi "xử lý văn bản") nên lead không gọi đúng agent, hoặc gọi nhầm agent khác | Sửa description cho cụ thể: nêu rõ loại việc (báo cáo, đề xuất, email) và cụm "dùng khi nào". Sau đó thử lại prompt không gọi tên để kiểm tra lead có chọn đúng không. |
| Agent bịa số liệu không có trong file | Kiểm tra phần thân agent có quy tắc "không bịa số, chỗ thiếu để [đợi bổ sung]" chưa. Bổ sung câu này. Khi giao việc, thêm dòng "không được thêm con số nào ngoài file". Mở file gốc so lại từng số. |
| tools cấp quá rộng (agent báo cáo lại có WebSearch, WebFetch) | Bỏ bớt công cụ không cần trong dòng tools. Nguyên tắc: chỉ cấp công cụ thật sự dùng. Agent chỉ đọc ghi file thì để Read, Write, Grep, Glob. |
| Lỡ quên thư mục `.claude/agents/` chưa có | Bảo Claude Code tạo thư mục khi lưu file agent đầu tiên; hoặc nhờ "tạo thư mục .claude/agents/ nếu chưa có rồi lưu file". |
| Agent trả kết quả dài dòng, thừa lời chào hỏi | Thêm vào thân agent: "trả kết quả gọn, sẵn sàng dùng, không thêm lời rào đón". |
| research-agent không có phần "cần kiểm chứng", khẳng định chắc số liệu thị trường | Nhắc lại quy tắc tách dữ kiện với suy luận trong thân agent; giao lại và yêu cầu ghi rõ chỗ chưa chắc là "cần kiểm chứng". |

## Bài tập
- **Tại lớp:** tạo xong report-agent + research-agent, chạy ra 1 báo cáo bán hàng và 1 báo cáo nghiên cứu từ hai file demo. Tạo thêm 1 agent cho nghề của mình và chạy thử 1 việc mẫu.
- **Về nhà:** chỉnh dòng description của agent nghề mình cho thật rõ, rồi thử 3 lần giao việc không gọi tên agent, kiểm tra lead có tự gọi đúng không. Viết lại 2 câu: agent của mình chuyên việc gì, và mình đã khoanh tools thế nào cho an toàn. Xem trước khái niệm Agent Team của buổi 5.

## Tiêu chí hoàn thành buổi
- [ ] Có ít nhất 2 file agent chạy được trong `.claude/agents/` (report-agent + research-agent).
- [ ] report-agent soạn được báo cáo bán hàng đúng số liệu file, có đủ 4 mục, không emoji, không bịa số.
- [ ] research-agent soạn được báo cáo nghiên cứu có tóm tắt điều hành, bảng so sánh đối thủ, và phần cần kiểm chứng.
- [ ] Tạo được 1 agent cho công việc thật của bản thân, description rõ và tools khoanh đúng phạm vi.
- [ ] Học viên giải thích được: vì sao description quyết định lead gọi agent, và vì sao tools là cách khoanh vùng an toàn.
