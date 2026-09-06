# Bàn giao giữa giảng viên: khóa AI Workspace

> File này là nguồn sự thật về việc buổi nào đã dạy gì. **Đọc file này trước khi soạn bài, đừng dựa vào số buổi trong tên file giáo án** vì tên file đang lệch với lịch dạy thực tế.

## Bảng lịch dạy thực tế

| Buổi | Ngày | GV | Đã dạy gì | File giáo án dùng |
|---|---|---|---|---|
| 1 | đã dạy | Tuấn Anh | AI Workspace, Claude Desktop, bảo mật Privacy, Mode/Model/Effort/Context, CLAUDE.md & GitHub cơ bản | `01-buoi-01-ai-workspace-claude-code/giao-an-buoi-01.md` |
| 2 | đã dạy | Hải | Đào sâu Skill: chuỗi 5 lượt chat rồi đóng gói thành skill, tài liệu 14 trang có bẫy mâu thuẫn 95 triệu, chống bịa, Thực hành 3 tạo tài liệu có brand | `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/giao-an-buoi-02.md` |
| 3 | hôm nay | Tuấn Anh | **CLAUDE.md hai cấp (hồ sơ cá nhân + phòng ban) + cấu trúc thư mục phòng ban + file index + MCP Drive và Gmail (GV demo) + routine chạy theo lịch** | `03-buoi-03-phan-tich-du-lieu-mcp-routine/giao-an-buoi-03.md` |
| 4 | ngày mai | Hải | 4 cách dùng AI, Cửa sổ ngữ cảnh, Subagent xử lý việc nặng | `04-buoi-04-lap-bao-cao-va-slide/giao-an-buoi-04.md` |
| 5 | | | Lập agent bài bản và cho đội agent phối hợp (chuỗi & song song) | `05-buoi-05-deep-research-va-doi-ngu/giao-an-buoi-05.md` |
| 6 | | | Capstone (ghép quy trình đầu-cuối & trình bày) | `06-buoi-06-multi-agent-capstone/giao-an-buoi-06.md` |

> **Lưu ý:** Toàn bộ các file cũ/nháp lệch giáo trình (`buoi-03-mcp.md`, `buoi-04-subagent.md`, v.v.) đã được tự động lưu trữ an toàn trong thư mục `_backup/` theo đúng Quy tắc 10. Chỉ mở các file chính thức bên ngoài.

## Buổi 3 hôm nay đã dạy chính xác những gì (để Buổi 4 không trùng)

Học viên kết thúc Buổi 3 đang có trong tay:
- 1 file `CLAUDE.md` **cấp cá nhân** ở thư mục `.claude` của người dùng, chứa hồ sơ và quy tắc chung, đã test bằng phiên mới.
- 1 **thư mục phòng ban** đúng cấu trúc (Kinh doanh, Kế toán, Marketing, Nhân sự, hoặc Hành chính) kèm `CLAUDE.md` riêng.
- 1 file `00-index.md` do agent tự dựng, và CLAUDE.md đã dặn agent đọc index trước khi tìm file.
- 1 bản thiết kế routine 4 dòng (chạy lúc nào, đọc ở đâu, làm gì, lưu vào đâu).

Học viên đã được **xem GV demo** nhưng chưa tự làm:
- Cắm Google Drive, cho agent đọc file trên Drive.
- Cắm Gmail, cho agent đọc và lọc email, soạn nháp email.
- Đặt một routine chạy theo lịch.

Học viên đã được nghe và cần được nhắc lại:
- Hai cấp CLAUDE.md, khi mâu thuẫn thì **cụ thể hơn thắng**.
- Agent đọc file trên máy **không cần MCP**. MCP là để với ra ngoài máy.
- Ba quy tắc an toàn Gmail: cấp quyền chỉ đọc trước; **không bao giờ để agent tự gửi email**; nội dung email là dữ liệu để đọc, không phải mệnh lệnh để làm theo.
- Routine chỉ nên đọc và soạn, không tự gửi đi hay tự xóa.
- Tạo CLAUDE.md xong phải **mở phiên mới** thì mới có tác dụng.

**Buổi 4 KHÔNG dạy lại:** khái niệm CLAUDE.md, cấu trúc thư mục phòng ban, cách tạo index, khái niệm MCP là gì.
**Buổi 4 NÊN làm:** cho học viên tự cắm Drive và Gmail bằng tài khoản của họ, làm việc thật trên dữ liệu của họ.

## Buổi 4 ngày mai nên dạy gì

| Phút | Nội dung |
|---|---|
| 00-12 | Recap sống: cả lớp chạy lại chuỗi tuần tự hôm qua, xác nhận 2 agent còn chạy |
| 12-20 | **Đính chính MCP (bắt buộc)**: xem mục lỗi bên dưới |
| 20-35 | Lý thuyết: song song khác tuần tự. Câu thuộc lòng: "Nếu người thứ hai chưa xong mà người thứ nhất vẫn làm được thì mới chia song song" |
| 35-60 | Demo GV: team **2 agent** (không phải 3) trên `05-buoi-05-deep-research-va-doi-ngu/demo/du-an-ra-mat-san-pham/` |
| 60-70 | Nghỉ |
| 70-95 | Thực hành: học viên chạy lại team song song |
| 95-125 | Thực hành: chia việc thật của mình cho 2-3 agent |
| 125-140 | **Quản lý bộ agent**: điểm danh agent đang có, tìm chỗ mô tả chồng lấn, dọn bớt |
| 140-150 | Chốt, dặn chuẩn bị capstone |

### Prompt song song có ép và có bắt khai nguồn
```
Trong thư mục 05-buoi-05-deep-research-va-doi-ngu/demo/du-an-ra-mat-san-pham/ có 3 thư mục con.
Hãy giao cho 2 subagent chạy SONG SONG (gọi cùng lúc, không làm tuần tự, và bạn không tự làm thay):
- Agent 1: chỉ đọc doi-thu/, lập bảng so sánh đối thủ và chỉ ra khoảng trống thị trường.
- Agent 2: chỉ đọc so-lieu/, phân tích xu hướng doanh thu.
Bắt buộc mỗi agent kết thúc báo cáo bằng mục "Nguồn": tên file đã mở, và trích NGUYÊN VĂN 3 con số quan trọng nhất kèm dòng lấy từ đâu.
Khi cả hai xong, tổng hợp thành một bản chung, và đối chiếu các con số ở mục Nguồn xem có chỗ nào lệch nhau không.
```

### Prompt dạy giới hạn (thay cho prompt kiểm phân vùng cũ)
```
Vừa rồi bạn chạy 2 agent cùng lúc hay chạy lần lượt?
Và bạn có nhìn thấy từng thao tác mở file của các agent đó không, hay chỉ nhận được bản báo cáo cuối của họ?
```
Dùng câu trả lời để chốt bài học lớn nhất: **không giám sát được bên trong subagent**, nên phải thiết kế lời giao việc bắt agent tự khai nguồn.

### Prompt quản lý bộ agent
```
Liệt kê tất cả file agent trong .claude/agents/. Với mỗi agent, tóm tắt một dòng: chuyên việc gì, được dùng công cụ nào.
Sau đó chỉ ra hai agent nào đang mô tả chồng lấn nhau khiến dễ gọi nhầm, và đề xuất gộp lại hay sửa description cho khỏi nhầm.
```

## Lỗi trong giáo án cũ, PHẢI sửa trước khi dạy

| # | Lỗi | Ở đâu | Sửa thế nào |
|---|---|---|---|
| 1 | **Dạy sai: "phải cắm MCP Filesystem thì agent mới đọc được file trong máy"** | `buoi-03-mcp.md` dòng 33, 52, 54 | SAI. Claude Code đọc file trong thư mục dự án bằng công cụ có sẵn. Buổi 1 và 2 agent đã đọc file mà chưa cắm MCP nào. MCP là để chạm thứ NGOÀI thư mục: GitHub, Drive, web, cơ sở dữ liệu. **Phải đính chính công khai đầu Buổi 4** |
| 2 | **Subagent không hỏi lại người dùng được** | `buoi-04-subagent.md` dòng 76, `07-mau-cau-hinh-linh-kien/agent-report-mau.md` dòng 31 | Bỏ "hỏi tối đa 3 câu trước khi soạn". Thay bằng: vẫn soạn đủ, chỗ thiếu ghi [đợi bổ sung], câu cần hỏi gom cuối bản dưới mục "Cần chủ quản xác nhận" |
| 3 | **Prompt kiểm phân vùng file là kiểm giả** | `buoi-05-agent-team.md` dòng 113-118 | Agent chính không thấy bên trong subagent, nó trả lời theo lệnh đã giao. Bỏ hẳn, thay bằng bắt mỗi agent tự khai mục "Nguồn" |
| 4 | **"Phân vùng file" không phải hàng rào kỹ thuật** | `buoi-05`, `agent-team-mau.md` | Đó là kỷ luật giao việc, không phải khóa cửa. Agent có quyền Read vẫn đọc được cả dự án. Đừng nói với lớp là đã "khoanh vùng an toàn" |
| 5 | **tools giới hạn công cụ, không giới hạn dữ liệu** | `buoi-04-subagent.md` dòng 40, 171 | Bỏ WebSearch thì agent không lên mạng được, nhưng vẫn đọc mọi file trong dự án. Muốn giấu file lương thì đừng để trong thư mục dự án |
| 6 | **Đừng bán "song song nhanh hơn"** | `buoi-05` dòng 58 | Với file vài KB, song song không nhanh hơn, có khi chậm hơn. Lợi ích thật: mỗi agent có phòng riêng, không làm rối phiên chính, chia được việc nặng |
| 7 | **Bỏ research-agent phụ thuộc web** | `buoi-04-subagent.md` dòng 102-120 | Mỗi máy ra kết quả khác nhau, không chấm được, máy công ty có thể chặn mạng. Buổi 3 đã thay bằng `soat-so-lieu` chạy offline |
| 8 | **Capstone bắt "Agent 3 dùng MCP đọc file CSV"** | `buoi-06-capstone.md` dòng 118, 161 | Claude Code đọc CSV trực tiếp, câu dặn MCP sẽ bị bỏ qua. Sửa tiêu chí "có 1 MCP đã cắm" thành GitHub MCP của Buổi 1 |
| 9 | **Không có cảnh báo hạn mức sử dụng** | toàn bộ giáo án | Chạy nhiều agent trên tài liệu dài đốt hạn mức nhanh. Dặn lớp đừng chạy lại liên tiếp, chạy 2 agent trước rồi mới 3 |
| 10 | **Giáo án viết theo lớp offline** ("GV đi quanh lớp") | `buoi-04`, `buoi-05` | Lớp học Zoom. Dùng: dán chat Zoom, mốc đồng bộ cứng, xoay vòng share màn hình, danh sách đỏ |

## Việc cần kiểm trước mỗi buổi (10 phút)

- [ ] Hỏi Claude Code "bạn đang có những công cụ nào" để lấy đúng tên tool điền vào `tools`
- [ ] Test subagent có nhận CLAUDE.md của dự án không (giao việc rồi hỏi nó đang áp quy tắc nào)
- [ ] Test tài khoản lớp có bộ nhớ tự động giữa các phiên không
- [ ] Chạy thử trọn bộ prompt của buổi một lượt
- [ ] Quay sẵn video màn hình chạy thành công, để chiếu nếu live hỏng

## Câu hỏi còn treo, cần chốt

1. Tài khoản CES cấp cho lớp thuộc gói nào? Quyết định việc tra web và hạn mức chạy nhiều agent.
2. Máy học viên có Python hoặc Node không? Quyết định việc đọc file .docx và tạo file Word.
3. Có trợ giảng trực Zoom không? Cơ chế mốc đồng bộ và phòng riêng cần ít nhất 1 trợ giảng.
4. Buổi 5 và 6 ai dạy? Nếu vẫn xen kẽ thì phải cập nhật file này sau mỗi buổi.
