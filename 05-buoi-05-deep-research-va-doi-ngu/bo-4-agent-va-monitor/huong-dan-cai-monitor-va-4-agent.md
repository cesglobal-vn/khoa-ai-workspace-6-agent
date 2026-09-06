# Hướng dẫn cài Claude Agent Monitor và tạo 4 agent

> Công cụ theo dõi để nhìn thấy subagent của Claude Code đang chạy. Rất hợp sau khi học agent và subagent.
> Repo: https://github.com/vuhai2002/claude-agent-monitor

## Phần 1: Monitor là gì và để làm gì

Claude Desktop không cho thấy bên trong subagent đang làm gì. Monitor này mở một bảng theo dõi ở trình duyệt (localhost) cho thấy: agent nào đang chạy, đang gọi công cụ gì, dùng bao nhiêu token, mấy lượt, có lỗi không, và khi nào xong.

Nhờ nó, lớp thấy tận mắt điều đã học: subagent chạy ở cửa sổ riêng, agent chính chỉ nhận kết quả cuối.

## Phần 2: Cài đặt (Windows)

1. **Kiểm tra có Node.js chưa.** Mở PowerShell gõ `node -v`. Nếu ra số phiên bản là có. Nếu báo lỗi, tải Node.js tại nodejs.org, cài bản LTS, rồi thử lại.
2. **Tải công cụ về.** Vào trang repo, bấm nút Code màu xanh, chọn Download ZIP. Giải nén ra một thư mục.
3. **Chạy.** Vào thư mục vừa giải nén, bấm đúp file `start-monitor.bat`. Một cửa sổ đen hiện lên và trình duyệt tự mở.
4. **Xem bảng.** Trình duyệt mở ở `http://localhost:4478`. Nếu không tự mở, gõ địa chỉ đó vào trình duyệt.
5. **Tắt.** Đóng cửa sổ đen là dừng.

> Ghi chú an toàn: bảng này chỉ chạy trên máy của bạn (127.0.0.1), không ai ngoài mạng vào được. Không cần lo lộ dữ liệu.

Nếu máy nào chưa có Node.js hoặc chưa cài kịp, ghép cặp xem chung máy bạn bên cạnh, cài sau ở nhà.

## Phần 3: Tạo 4 agent

Bốn agent mẫu nằm cùng thư mục này. Chép mỗi file vào `.claude/agents/` trong thư mục dự án của bạn. Nhanh nhất là nhờ Claude Code tạo giúp bằng các prompt dưới.

### Agent 1: agent-soan-bao-cao (có quyền ghi file)
```
Tạo file .claude/agents/agent-soan-bao-cao.md với nội dung y hệt file mẫu agent-soan-bao-cao.md tôi đưa: chuyên soạn báo cáo, đề xuất, email từ số liệu thô. tools gồm Read, Write, Grep, Glob. Quy tắc: tiếng Việt công sở, không emoji, không bịa số.
```

### Agent 2: agent-ra-soat-khach (chỉ đọc, không ghi)
```
Tạo file .claude/agents/agent-ra-soat-khach.md: chuyên đọc hồ sơ khách và chỉ ra khách cần hành động. tools chỉ gồm Read, Grep, Glob, KHÔNG có Write. Chỉ báo cáo, không sửa file.
```

### Agent 3: agent-tom-tat-tai-lieu (chỉ đọc)
```
Tạo file .claude/agents/agent-tom-tat-tai-lieu.md: chuyên tóm tắt tài liệu dài theo cấu trúc tóm tắt nhanh, ý chính, số liệu và hạn chót, điểm lưu ý. tools gồm Read, Grep, Glob. Chỉ dùng thông tin trong tài liệu, không có thì ghi "tài liệu không đề cập".
```

### Agent 4: agent-nghien-cuu-thi-truong (có tra web)
```
Tạo file .claude/agents/agent-nghien-cuu-thi-truong.md: chuyên nghiên cứu thị trường và đối thủ, tổng hợp có trích nguồn. tools gồm Read, Write, WebSearch, WebFetch, Grep, Glob. Tách rõ dữ kiện có nguồn với suy luận, không bịa số liệu, không bịa nguồn.
```

> Sau khi tạo hoặc sửa agent, phải MỞ PHIÊN MỚI thì Claude mới nạp.

## Phần 4: Chạy 4 agent để xem trên monitor

Mở phiên mới, mở sẵn bảng monitor ở trình duyệt, rồi gõ lệnh dưới. Vừa gõ vừa nhìn bảng, sẽ thấy các agent lần lượt sáng lên.

### Cách A: chạy lần lượt từng agent
```
1. Nhờ agent-ra-soat-khach đọc thư mục 05-buoi-05-deep-research-va-doi-ngu/demo/word và chỉ ra khách cần hành động.
2. Nhờ agent-tom-tat-tai-lieu tóm tắt file hợp đồng trong 05-buoi-05-deep-research-va-doi-ngu/demo/pdf.
3. Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3 từ 04-buoi-04-lap-bao-cao-va-slide/demo/so-lieu-ban-hang-thang.md.
4. Nhờ agent-nghien-cuu-thi-truong tìm hiểu nhanh xu hướng phần mềm quản lý bán hàng cho doanh nghiệp nhỏ.
```

### Cách B: chạy nhiều agent cùng lúc để bảng sáng nhiều dòng
```
Giao SONG SONG cho các agent, gọi cùng lúc, không tự làm thay:
- agent-ra-soat-khach: rà thư mục 03-buoi-03-phan-tich-du-lieu-mcp-routine/demo/phong-kinh-doanh-mau/01-khach-hang.
- agent-tom-tat-tai-lieu: tóm tắt hợp đồng trong 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/hop-dong-dich-vu-mau.md.
- agent-soan-bao-cao: soạn báo cáo tháng 3 từ 04-buoi-04-lap-bao-cao-va-slide/demo/so-lieu-ban-hang-thang.md.
Mỗi agent kết thúc bằng mục Nguồn. Xong gom lại thành một bản chung.
```

Trên bảng monitor sẽ thấy nhiều agent chạy song song, mỗi cái có token và công cụ riêng. Đây là bằng chứng tận mắt cho bài học "mỗi subagent chạy ở cửa sổ ngữ cảnh riêng".

## Bốn agent này lo việc gì

| Agent | Chuyên việc | Có ghi file không |
|---|---|---|
| agent-soan-bao-cao | Soạn báo cáo, đề xuất, email | Có (Write) |
| agent-ra-soat-khach | Rà hồ sơ khách, chỉ ra việc cần làm | Không, chỉ đọc |
| agent-tom-tat-tai-lieu | Tóm tắt tài liệu dài | Không, chỉ đọc |
| agent-nghien-cuu-thi-truong | Nghiên cứu thị trường, đối thủ, có tra web | Có (Write) |

Hai agent chỉ đọc (không Write) là ví dụ khoanh công cụ cho an toàn: người rà soát và người tóm tắt thì không cần cầm bút sửa file.
