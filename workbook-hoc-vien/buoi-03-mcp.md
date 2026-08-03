# Workbook Buổi 03: MCP - Cho agent chạm vào dữ liệu thật

> In hoặc mở song song với Claude Code. Làm theo từng bước đánh số. Chỗ nào có ô ghi chú thì viết vào.

## Mục tiêu buổi này (bạn sẽ làm được)
1. Hiểu MCP là cổng cắm để agent đọc file, tra web, mở Google Drive, hỏi cơ sở dữ liệu.
2. Tự cắm 1 MCP qua Claude Desktop và cấp quyền an toàn.
3. Ra lệnh tiếng Việt cho agent đọc file dữ liệu và phân tích: tổng, trung bình, đếm theo nhóm.
4. Biết cách kiểm lại con số quan trọng trước khi dùng.

## Nhắc lại 1 câu từ buổi trước
Buổi 2: skill dạy agent LÀM GÌ. Buổi này: MCP cho agent CHẠM VÀO CÁI GÌ (file, web, Drive, dữ liệu thật). Hai cái ghép với nhau.

## Chuẩn bị (mang theo và mở sẵn)
- [ ] Claude Desktop đã đăng nhập tài khoản CES cấp, mở sẵn Claude Code.
- [ ] 1 file Excel hoặc CSV công việc thật của bạn (doanh thu, đơn hàng, chấm công, danh sách khách...). Nhớ đường dẫn thư mục chứa file.
- [ ] Bộ file demo của khóa đã tải về máy (thư mục `tai-lieu-phat/demo/buoi-03/`).

---

## Phần A: Cắm MCP và đọc file demo (làm theo GV)

### Bước 1: Cắm MCP Filesystem qua Claude Desktop
1. Mở Claude Desktop, vào phần cài đặt kết nối (Connectors / MCP).
2. Chọn server **Filesystem** (cho agent đọc/ghi file trong 1 thư mục).
3. Trỏ nó vào thư mục chứa file demo `buoi-03` (hoặc thư mục chứa dữ liệu bạn muốn agent đọc).
4. Bấm kết nối.

### Bước 2: Cấp quyền an toàn
1. Khi Claude Desktop hỏi cấp quyền, đọc kỹ nó xin truy cập thư mục nào.
2. Chỉ cấp đúng thư mục cần. Nếu nó xin cả ổ đĩa mà bạn chỉ cần 1 thư mục thì thu hẹp lại.
3. Nếu chỉ cần xem (không sửa file), ưu tiên quyền **chỉ đọc**.

### Bước 3: Kiểm tra cổng đã thông
Quay lại Claude Code, gõ prompt sau để xem agent đọc được thư mục chưa:
```
Liệt kê các file trong thư mục demo buoi-03 mà bạn đọc được.
```
Agent phải kể ra 2 file: `doanh-thu-quy.csv` và `don-hang.csv`. Nếu không thấy, quay lại Bước 1, kiểm tra trỏ đúng thư mục và đã cấp quyền chưa.

### Bước 4: Ra lệnh cho agent phân tích doanh-thu-quy.csv
Gõ prompt:
```
Đọc file doanh-thu-quy.csv trong thư mục demo buoi-03. Tính tổng doanh thu
theo khu vực và theo sản phẩm. Chỉ ra xu hướng doanh thu qua 3 tháng.
Gợi ý loại biểu đồ phù hợp. Đơn vị là triệu đồng.
```
Đối chiếu kết quả agent trả với đáp án chuẩn:
- TP HCM = 1.565 triệu, cao hơn Ha Noi = 1.305 triệu.
- Goi Cao cap = 1.640 triệu, cao hơn Goi Tieu chuan = 1.230 triệu.
- Tổng cả quý = 2.870 triệu.
- Xu hướng tăng đều: Tháng 1 = 870, Tháng 2 = 915, Tháng 3 = 1.085 triệu.

Ô ghi chú (kết quả agent của bạn có khớp không):
```
.....................................................................
.....................................................................
```

### Bước 5: Tự kiểm lại 1 con số
Chọn con số quan trọng nhất (ví dụ tổng TP HCM = 1.565). Kiểm lại bằng 1 trong 2 cách:
- Mở file, cộng nhanh cột TP HCM bằng máy tính.
- Hoặc dùng hàm SUM trong Excel.

Ô ghi chú (tôi đã kiểm con số ...., cách kiểm ...., kết quả khớp / lệch):
```
.....................................................................
```

---

## Phần B: Thực hành 1 với don-hang.csv (bạn tự làm)

### Bước 6: Cho agent đếm đơn theo trạng thái
Gõ prompt:
```
Đọc file don-hang.csv trong thư mục demo buoi-03. Cho biết có bao nhiêu đơn
Cho thanh toan và tổng giá trị của các đơn đó. Có bao nhiêu đơn Huy và tổng
giá trị. Đơn vị triệu đồng.
```
Đáp án chuẩn để đối chiếu:
- Cho thanh toan: **3 đơn**, tổng **275 triệu**.
- Huy: **1 đơn**, tổng **120 triệu**.
- (Hỏi thêm nếu muốn: Da thanh toan 6 đơn / 380 triệu. Tổng 10 đơn / 775 triệu.)

### Bước 7: Kiểm tay (file chỉ 10 dòng nên đếm được)
Mở file, đếm số dòng có chữ "Cho thanh toan". Có đúng 3 dòng không?

Ô ghi chú:
```
Số đơn Cho thanh toan tôi đếm tay: ........  Khớp với agent? ........
```

---

## Phần C: Thực hành 2 với dữ liệu công việc của bạn

### Bước 8: Trỏ MCP vào thư mục file của bạn
Nếu file công việc của bạn nằm ở thư mục khác, quay lại Connectors và thêm/đổi Filesystem trỏ vào thư mục đó. Cấp quyền chỉ đọc.

### Bước 9: Ra lệnh cho agent đọc và mô tả file
Gõ prompt (thay tên file cho đúng):
```
Đọc file <ten-file-cua-toi> trong thư mục dự án. Mô tả file có những cột gì
và khoảng bao nhiêu dòng.
```

### Bước 10: Ra lệnh phân tích
Gõ prompt (sửa câu hỏi cho hợp dữ liệu của bạn):
```
Với file <ten-file-cua-toi>, tính giúp tôi: <ví dụ: tổng doanh thu theo tháng /
trung bình mỗi đơn / đếm số khách theo khu vực>. Chỉ ra điểm đáng chú ý và
gợi ý biểu đồ phù hợp. Ghi rõ đơn vị.
```

### Bước 11: Kiểm lại 1 con số của chính bạn
Chọn 1 con số agent đưa ra, kiểm lại bằng hàm SUM hoặc đếm tay trong Excel.

Ô ghi chú (file của tôi, con số agent tính, con số tôi kiểm lại):
```
.....................................................................
.....................................................................
.....................................................................
```

---

## Mẫu câu hỏi phân tích (copy nhanh, đổi tên file cho đúng)
```
Đọc file <ten-file>. Tính tổng <cột số> theo <nhóm>. Đơn vị <triệu/nghìn>.
```
```
Đọc file <ten-file>. Tính giá trị trung bình mỗi <đơn/khách/dòng>.
```
```
Đọc file <ten-file>. Đếm số dòng theo từng <trạng thái/khu vực/loại>.
```
```
Đọc file <ten-file>. So sánh <chỉ số> giữa các tháng, chỉ ra mức tăng giảm.
```
```
Đọc file <ten-file>. Chỉ ra 3 dòng có <giá trị> cao nhất (top 3).
```
```
Trình bày lại kết quả trên thành bảng gọn, ghi rõ đơn vị.
```

## Lưu ý an toàn khi cấp quyền (đọc kỹ)
- Chỉ cắm MCP từ nguồn tin cậy.
- Cấp quyền tối thiểu: chỉ đúng thư mục cần, không cấp cả ổ đĩa nếu không cần.
- Ưu tiên quyền **chỉ đọc** khi bạn chỉ cần xem dữ liệu.
- Đọc kỹ khi agent xin quyền **ghi hoặc xóa**. Không cấp nếu chỉ cần phân tích.
- Dữ liệu nhạy cảm (khách hàng, tài chính, nhân sự): hỏi bộ phận phụ trách trước khi cắm.
- Luôn kiểm lại con số quan trọng trước khi đưa vào báo cáo hay ra quyết định.

## Bài tập về nhà
1. Cắm 1 MCP trên máy nhà, trỏ vào thư mục chứa 1 file dữ liệu công việc thật.
2. Cho agent phân tích file đó: tính 1 con số có ý nghĩa (tổng, trung bình, hoặc đếm theo nhóm), kèm gợi ý biểu đồ.
3. Chụp màn hình kết quả.
4. Ghi 1 dòng: "Tôi đã kiểm lại con số .... bằng cách ...., kết quả khớp / lệch."

## Checklist tự đánh giá (tick khi làm được)
- [ ] Tôi cắm được 1 MCP Filesystem và agent đọc được file qua cổng đó.
- [ ] Agent liệt kê đúng 2 file demo trong thư mục buoi-03.
- [ ] Agent phân tích đúng doanh-thu-quy.csv (số khớp đáp án chuẩn).
- [ ] Agent đếm đúng don-hang.csv (Cho thanh toan 3 đơn/275 triệu, Huy 1 đơn/120 triệu).
- [ ] Tôi cho agent phân tích được 1 file công việc thật của mình.
- [ ] Tôi tự kiểm lại được ít nhất 1 con số quan trọng.
- [ ] Tôi hiểu quy tắc cấp quyền tối thiểu và chỉ đọc khi chỉ cần xem.
