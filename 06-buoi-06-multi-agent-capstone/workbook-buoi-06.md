# Workbook Buổi 06: Toàn Cảnh Hệ Sinh Thái Claude, Vòng Lặp Tự Phản Biện & Thuê Ê-kíp Media

> **Sổ tay thực hành dành cho Học viên Khóa AI Workspace (CES Global)**  
> Dùng file này trong suốt buổi học để copy nhanh các câu lệnh thực hành và ghi chép.

---

## 1. Bản Đồ Năng Lực Buổi 06

Sau buổi học hôm nay, bạn sẽ làm chủ:
1. **Bức tranh 4 cấp độ dùng Claude:**
   - Cấp 1 (Web) -> Cấp 2 (Projects) -> Cấp 3 (Desktop + MCP) -> Cấp 4 (Claude Code AI Workspace).
   - Nắm trọn hệ thống "Bộ não 4 tầng": `CLAUDE.md` + Skill + MCP + Agent.
2. **Vũ khí 1 — Vòng lặp phản biện (Maker – Checker):**
   - Tuyển Trưởng phòng thẩm định (`truong-phong-tham-dinh`) với chìa khóa chỉ đọc an toàn.
   - Cho 2 nhân sự tự phản biện, tự sửa lỗi để nâng chất lượng từ 7/10 lên 9.5/10 hoàn toàn tự động.
3. **Vũ khí 2 — Thuê Ê-kíp Media (`/brag`):**
   - 1 câu lệnh xuất ra video trailer `.mp4`, kịch bản phân cảnh, ảnh bìa và caption mạng xã hội.
   - Đạo diễn bằng lời thường: đổi 7 tông cảm xúc, làm bản dọc cho TikTok/Reels, sửa riêng 1 cảnh.
   - Tự động sản xuất video giới thiệu từ chính địa chỉ website của bạn.
4. **3 nguyên tắc vàng:**
   - 5 lần làm tay mới đóng gói; Chia phòng riêng việc nặng; Bắt buộc có khâu kiểm duyệt trước khi duyệt thật.

---

## 2. Toàn Bộ Câu Lệnh Thực Hành (Copy Dán Vào Claude Code)

### Phần A. Toàn Cảnh AI Workspace & Rà Soát Đồ Nghề

#### Câu lệnh A1: Kiểm tra tài sản AI hiện có
```text
Liệt kê ngắn gọn giúp tôi:
1. File CLAUDE.md đang có những quy tắc chính nào?
2. Thư mục .claude/skills/ đang có những skill gì?
3. Thư mục .claude/agents/ đang có những agent nào?
```

---

### Phần B. Vũ Khí 1: Vòng Lặp Tự Phản Biện (Maker – Checker)

#### Bước B1: Tuyển Trưởng phòng thẩm định (khóa quyền sửa file)
```text
Tạo cho tôi một agent mới tại đường dẫn: ".claude/agents/truong-phong-tham-dinh.md" ngay trong thư mục này.

Chỉ cấp cho trợ lý này công cụ đọc và tìm kiếm file trong máy. Tuyệt đối KHÔNG cấp công cụ chỉnh sửa hay tạo file mới.

Nhiệm vụ của Trưởng phòng thẩm định:
1. Đóng vai một Trưởng phòng chiến lược dày dạn kinh nghiệm, cực kỳ khó tính và khắt khe.
2. Khi nhận được một bản kế hoạch hoặc báo cáo từ chuyên viên, hãy soi lỗi dựa trên 3 tiêu chí:
   - Tính xác thực của số liệu: Mọi con số đều phải trích dẫn rõ nguồn, không được nhận định chung chung.
   - Tính thực tế và rủi ro: Kế hoạch có tính đến ngân sách, đối thủ và điểm nghẽn thực thi chưa?
   - Văn phong công sở: Gọn gàng, khúc chiết, không dùng từ sáo rỗng, không biểu cảm thừa.
3. Luôn đưa ra nhận xét theo format:
   - Điểm đạt yêu cầu.
   - Điểm chưa đạt (nêu rõ tối đa 3 điểm yếu cần sửa gấp).
   - Yêu cầu sửa đổi cụ thể cho chuyên viên.
```

#### Bước B2: Kích hoạt Vòng lặp phản biện tự động
```text
Hãy thực hiện quy trình tự phản biện 2 vòng giữa chuyen-vien-de-xuat và truong-phong-tham-dinh:

Vòng 1:
- Nhờ chuyen-vien-de-xuat đọc dữ liệu nghiên cứu sẵn có và soạn một bản Đề xuất chiến lược ra mắt sản phẩm mới, lưu bản nháp vào file "ket-qua/ban-nhap-de-xuat.md".

Vòng 2:
- Nhờ truong-phong-tham-dinh đọc file "ket-qua/ban-nhap-de-xuat.md", đưa ra bản thẩm định khắt khe và chỉ ra các điểm cần sửa, lưu vào file "ket-qua/bien-ban-tham-dinh.md".

Vòng 3 (Chốt bản cuối):
- Nhờ chuyen-vien-de-xuat đọc kỹ "ket-qua/bien-ban-tham-dinh.md", tiếp thu toàn bộ góp ý của Trưởng phòng để chỉnh sửa và xuất bản hoàn chỉnh vào file "ket-qua/de-xuat-hoan-thien.md".
```

#### Bước B3: Đối chiếu chất lượng Trước vs Sau phản biện
```text
Hãy tóm tắt và chỉ ra 3 điểm khác biệt lớn nhất giữa bản nháp đầu tiên ("ket-qua/ban-nhap-de-xuat.md") và bản đã hoàn thiện sau phản biện ("ket-qua/de-xuat-hoan-thien.md").
```

---

### Phần C. Vũ Khí 2: Thuê Ê-kíp Media Ngoại Viện (`/brag`)

#### Bước C1: Lấy 5 sản phẩm mẫu
```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```

#### Bước C2: Thử làm khi chưa có ê-kíp
```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```

#### Bước C3: Cài skill ê-kíp làm trailer
```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```

#### Bước C4: Video đầu tiên với 1 câu lệnh
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```

#### Bước C5: So sánh trước và sau
```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```

#### Bước C6: Đổi tông phong cách
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```

#### Bước C7: Dựng bản dọc cho TikTok / Reels
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```

#### Bước C8: Sửa riêng cảnh mở đầu
```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```

#### Bước C9: Viết 3 caption tiếng Việt đa kênh
```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```

#### Bước C10: Video cho website của bạn
```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```

---

## 3. Ghi Chú & Lưu Ý Quan Trọng
- **Bốn thứ nhận về trong `brag-output/`:**
  1. `brag-plan.md`: Kịch bản chi tiết.
  2. `brag.mp4`: Video trailer hoàn chỉnh.
  3. `brag.jpg`: Ảnh bìa đại diện.
  4. `share-copy.txt`: Caption mạng xã hội.
- **3 nguyên tắc vàng:**
  1. 5 lần làm tay rồi mới đóng gói.
  2. Chia phòng riêng cho việc nặng.
  3. Bắt buộc có khâu kiểm duyệt trước khi đưa người thật phê duyệt.
