# Workbook Buổi 05: Thuê Trợ Lý Phụ & Lập Cặp Đôi Trợ Lý Deep Research & Đề Xuất

> **Sổ tay thực hành dành cho Học viên Khóa AI Workspace (CES Global)**  
> Dùng file này trong suốt buổi học để copy nhanh các câu lệnh thực hành và ghi chép.

---

## 1. Bản Đồ Năng Lực Buổi 05

Sau buổi học hôm nay, bạn sẽ làm chủ:
1. **Hình ảnh "Một công ty thu nhỏ":**
   - **Agent** là Nhân viên biên chế chính thức.
   - **Subagent** là Trợ lý phụ làm việc ở phòng riêng, không làm bẩn bàn chính.
2. **Kỹ thuật Lập Agent bằng tiếng Việt tự nhiên:**
   - Tuyển Nhân viên 1: `nghien-cuu-doi-thu` (chuyên ra mạng dọ thám đối thủ, chỉ đọc và tra web, không cho sửa file).
   - Tuyển Nhân viên 2: `chuyen-vien-de-xuat` (chuyên ngồi văn phòng nội bộ, đọc dữ liệu và viết kế hoạch tác chiến cho ban giám đốc).
3. **Phân biệt rạch ròi Skill vs Agent:**
   - **Skill** là *Cuốn công thức* (Làm thế nào).
   - **Agent** là *Bản hợp đồng nhân viên* (Ai làm, và được cầm chìa khóa những phòng nào).
   - Ổ khóa công cụ là lá chắn an toàn tối thượng chống website lạ cài bẫy câu lệnh ẩn (*Prompt Injection*).
4. **Hai mô hình phối hợp Đội ngũ:**
   - **Nối chuỗi (Tuần tự):** Việc sau phải chờ việc trước (Agent 1 nghiên cứu $\rightarrow$ bàn giao file $\rightarrow$ Agent 2 viết đề xuất hành động).
   - **Chạy song song:** Các việc độc lập làm cùng lúc (Nghiên cứu thị trường Việt Nam & Quốc tế cùng lúc).

---

## 2. Bảng Đối Chiếu: Skill vs Agent (Học Thuộc Lòng)

| Đặc điểm | Skill | Agent |
|---|---|---|
| **Trả lời câu hỏi** | Làm việc này thế nào? | Ai làm, và được đụng vào những gì? |
| **Nơi lưu trữ** | `.claude/skills/<tên>/SKILL.md` | `.claude/agents/<tên>.md` |
| **Chạy ở đâu** | Ngay tại chỗ người gọi (phiên chính) | Trong phòng riêng, chỉ gửi kết quả về |
| **Giới hạn quyền hạn** | **Không.** Chỉ dặn được bằng lời | **Có.** Ổ khóa công cụ kỹ thuật thật sự |
| **Khi nào nên dùng** | Một việc lặp lại, quy trình cố định | Một vai làm nhiều lần, cần chạy riêng hoặc cần khóa quyền an toàn |

---

## 3. Thực Hành Từng Bước (Copy dán vào Claude Code)

### Bước 1: Tuyển Nhân viên 1 — Trợ lý Nghiên cứu đối thủ (`nghien-cuu-doi-thu`)

Mở Claude Code tại thư mục dự án và dán câu lệnh sau:

```text
Tạo cho tôi một agent mới, đặt tại đường dẫn: ".claude/agents/nghien-cuu-doi-thu.md" ngay trong thư mục làm việc này.

Chỉ cấp cho trợ lý này các công cụ để đọc file, tìm kiếm file và tra cứu thông tin trên web. Tuyệt đối KHÔNG cấp công cụ chỉnh sửa hay tạo file mới.

Trong file ghi hướng dẫn cho trợ lý này: nhiệm vụ là nghiên cứu đối thủ trong ngành của tôi, chỉ đọc và tra cứu thông tin trên mạng, tuyệt đối không chỉnh sửa file của tôi, và luôn trích dẫn rõ nguồn thông tin kèm các con số đối chiếu cụ thể.
```

*Kiểm tra:* Mở `.claude/agents/nghien-cuu-doi-thu.md`, kiểm tra xem công cụ chỉ có đọc/tra web, không có quyền sửa/ghi file.

---

### Bước 2: Tuyển Nhân viên 2 — Chuyên viên Đề xuất chiến lược (`chuyen-vien-de-xuat`)

Dán tiếp câu lệnh sau vào Claude Code:

```text
Tạo tiếp cho tôi một agent thứ hai, đặt tại đường dẫn: ".claude/agents/chuyen-vien-de-xuat.md" ngay trong thư mục làm việc này.

Chỉ cấp cho trợ lý này các công cụ để đọc file và tạo/ghi file mới. Không cần cấp công cụ tra cứu web vì chỉ làm việc trên dữ liệu nội bộ.

Trong file ghi hướng dẫn cho trợ lý này: nhiệm vụ là đọc các báo cáo hoặc dữ liệu phân tích được chỉ định, sau đó đề xuất các giải pháp, kế hoạch hành động cụ thể cho ban giám đốc. Văn phong công sở rõ ràng, sắc sảo, tuyệt đối không dùng emoji.
```

*So sánh:*
- `nghien-cuu-doi-thu`: Có chìa khóa ra web, **không có chìa khóa sửa file** (chống lừa đảo mạng).
- `chuyen-vien-de-xuat`: Có chìa khóa tạo file đề xuất, **không cần ra mạng** (chuyên môn nội bộ).

---

### Bước 3: Phối hợp Nối chuỗi: Cặp bài trùng Nghiên cứu $\rightarrow$ Đề xuất hành động

Dán câu lệnh sau vào Claude Code:

```text
Làm lần lượt hai bước theo quy trình nối chuỗi giữa 2 agent, xong bước 1 mới sang bước 2:

- Bước 1: Nhờ agent nghien-cuu-doi-thu tìm giúp tôi 3 đối thủ lớn trong ngành của tôi và điểm mạnh nhất của họ, lưu bản tóm tắt vào file "ket-qua/nghien-cuu-doi-thu.md".
- Bước 2: Sau khi có file đó, nhờ agent chuyen-vien-de-xuat đọc file "ket-qua/nghien-cuu-doi-thu.md" và soạn cho tôi một bản đề xuất 3 hành động cụ thể để công ty tôi cạnh tranh lại với họ, văn phong công sở chuẩn mực, không dùng emoji.
```

*Quan sát kết quả:*
- Claude đóng vai Sếp điều phối.
- Agent 1 chạy trước trong phòng riêng $\rightarrow$ tạo file trung gian `ket-qua/nghien-cuu-doi-thu.md`.
- Agent 2 tiếp quản đọc file đó $\rightarrow$ xuất bản đề xuất chiến lược hoàn chỉnh.

---

### Bước 4: Phối hợp Chạy song song: Nghiên cứu 2 thị trường cùng lúc

Dán câu lệnh sau vào Claude Code:

```text
Dùng agent nghien-cuu-doi-thu tìm giúp tôi các thương hiệu cùng ngành đang bán chạy trên thị trường.

Chạy song song 2 trợ lý cùng lúc:
- Trợ lý 1: nghiên cứu ở thị trường Việt Nam
- Trợ lý 2: nghiên cứu ở thị trường quốc tế
Mỗi trợ lý làm việc độc lập trong phòng riêng rồi mang bản tóm tắt về cho tôi nhé.
```

*Mẹo nếu máy chỉ chạy 1 con lần lượt:* Gõ thêm:  
`Chạy đồng thời hai trợ lý song song, đừng làm lần lượt.`

---

## 4. Thước Đo 3 Nấc Chọn Đúng Người Cho Đúng Việc

Trước khi giao việc cho Claude, đối chiếu nhanh với 3 nấc:

1. **Mức 1 — Việc thông thường** *(Viết email, tóm tắt 1 file):*  
   $\rightarrow$ Claude chính là đủ. Nói thẳng, không cần gọi ai.
2. **Mức 2 — Việc phụ nặng & Độc lập** *(Khảo sát mạng, đọc hàng chục bài viết):*  
   $\rightarrow$ Giao cho Trợ lý phụ (`subagent`) như `nghien-cuu-doi-thu` làm trong phòng riêng.
3. **Mức 3 — Bài toán lớn chuỗi giá trị** *(Nghiên cứu $\rightarrow$ Phân tích số liệu $\rightarrow$ Báo cáo $\rightarrow$ Slide):*  
   $\rightarrow$ Điều phối chuỗi Agent $\rightarrow$ **Nội dung trọng tâm Buổi 06 (Capstone)**.

---

## 5. Checklist Tổng Kết Buổi 05

Đánh dấu các việc bạn đã làm được tối nay:
- [ ] Đã có đủ 2 file agent trong `.claude/agents/`: `nghien-cuu-doi-thu.md` và `chuyen-vien-de-xuat.md`.
- [ ] Đã chạy thành công chuỗi tuần tự giữa 2 agent: Agent 1 nghiên cứu $\rightarrow$ bàn giao file $\rightarrow$ Agent 2 viết đề xuất hành động.
- [ ] Đã gọi 2 trợ lý phụ chạy song song 2 thị trường cùng lúc.
- [ ] Đã hiểu rõ Skill (công thức) khác Agent (nhân viên có ổ khóa công cụ) ở điểm nào.
- [ ] Đã có sẵn 2 trợ lý thực chiến trong tay, sẵn sàng bước vào **Buổi 06 (Dự án Capstone)**!
