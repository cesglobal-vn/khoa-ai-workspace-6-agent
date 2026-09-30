# Workbook Buổi 06: Thuê Ê-kíp Media — Một Câu Lệnh Ra Video Trailer Quảng Cáo

> **Sổ tay thực hành dành cho Học viên Khóa AI Workspace (CES Global)**  
> Dùng file này trong suốt buổi học để copy nhanh các câu lệnh thực hành (10 bước) và ghi chép.

---

## 1. Bản Đồ Năng Lực Buổi 06

Sau buổi học hôm nay, bạn sẽ làm chủ:
1. **Khái niệm Ê-kíp Media tự động:** `/brag` là quyển công thức của cả một ê-kíp (biên kịch, dựng hình, làm nhạc, viết caption).
2. **Quy tắc an toàn công ty:** Cài đặt skill cấp thư mục dự án và bắt Claude thẩm định skill trước khi cài (chống bẫy câu lệnh ẩn).
3. **Một câu lệnh ra video:** Tự động tạo kịch bản phân cảnh, video `.mp4`, ảnh bìa `.jpg` và caption `.txt`.
4. **Đạo diễn bằng lời thường:** Đổi 7 phong cách tông cảm xúc và chuyển đổi kích thước video dọc cho TikTok/Reels.
5. **Kỹ thuật sửa cục bộ:** Chỉ đạo ê-kíp quay lại đúng 1 cảnh chưa ưng ý mà không cần làm lại từ đầu.
6. **Ứng dụng thực tế:** Tự động tạo video trailer từ chính website doanh nghiệp của bạn.

---

## 2. Toàn Bộ 10 Bước Thực Hành (Copy Dán Vào Claude Code)

### Phần A. Thuê ê-kíp về công ty

#### Bước 1: Lấy 5 sản phẩm mẫu
```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```

#### Bước 2: Thử làm khi chưa có ê-kíp
```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```

#### Bước 3: Cài skill ê-kíp làm trailer
```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```

---

### Phần B. Một câu lệnh ra một video

#### Bước 4: Video đầu tiên
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```

#### Bước 5: So sánh trước và sau
```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```

---

### Phần C. Đạo diễn bằng lời

#### Bước 6: Đổi tông phong cách
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```

#### Bước 7: Dựng bản dọc cho TikTok / Reels
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```

---

### Phần D. Quay lại một cảnh

#### Bước 8: Sửa riêng cảnh mở đầu
```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```

#### Bước 9: Viết 3 caption tiếng Việt đa kênh
```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```

---

### Phần E. Sản phẩm thật và giới hạn

#### Bước 10: Video cho website của bạn
```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```

---

## 3. Ghi Chú & Lưu Ý Quan Trọng
- **4 thứ nhận về trong thư mục `brag-output/`:**
  1. `brag-plan.md`: Kịch bản chi tiết.
  2. `brag.mp4`: Video trailer hoàn chỉnh.
  3. `brag.jpg`: Ảnh bìa đại diện.
  4. `share-copy.txt`: Caption mạng xã hội.
- **Giới hạn cần nhớ:** Video bám sát nội dung web, web sơ sài thì video sơ sài. Tuyệt đối không chạy trên thư mục chứa dữ liệu mật hoặc danh sách khách hàng.
