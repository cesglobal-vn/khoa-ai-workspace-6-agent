# Ví dụ: CLAUDE.md cấp phòng ban đã điền sẵn

> Bản mẫu đã điền hoàn chỉnh cho thư mục `phong-kinh-doanh-mau` dùng trong bài thực hành Buổi 3. Học viên copy khối dưới, lưu thành file `CLAUDE.md` đặt ngay ở gốc thư mục đó.

```markdown
# CLAUDE.md: Thư mục phòng Kinh doanh

## Thư mục này dùng để làm gì
Chứa toàn bộ hồ sơ khách hàng, báo giá, hợp đồng và số liệu bán hàng của phòng Kinh doanh.

## Cấu trúc thư mục
- `01-khach-hang/` : hồ sơ từng khách và lịch sử trao đổi
- `02-bao-gia/` : các báo giá đã gửi khách
- `03-hop-dong/` : tóm tắt hợp đồng đã ký, kèm mốc hết hạn
- `04-so-lieu/` : file CSV doanh thu theo quý và danh sách đơn hàng
- `05-bao-cao/` : nơi lưu mọi kết quả agent tạo ra

## Quy trình riêng của phòng
- Mọi báo giá phải ghi rõ hiệu lực 30 ngày và ghi rõ giá đã gồm thuế giá trị gia tăng hay chưa.
- Mọi con số đưa vào báo cáo phải trích được từ file gốc trong `04-so-lieu/`, ghi rõ lấy từ file nào, dòng nào. Không tự tính ra con số không có trong file.

## Cách tìm file
Trước khi tìm file, đọc `00-index.md` để biết file nào chứa gì, đừng mở lần lượt từng file.

## Nơi lưu kết quả
Mọi file agent tạo ra thì lưu vào `05-bao-cao/`, đặt tên theo mẫu:
`[loai]-[thang]-[nam].md`, ví dụ `bao-cao-thang-03-2026.md`.

## Dữ liệu nhạy cảm
Thư mục này không chứa bảng lương và thông tin ngân hàng của khách. Nếu cần dùng, để ngoài thư mục này.
```

## Ghi chú cho giảng viên
- Chỉ ra chỗ khác nhau với file cấp cá nhân: file này nói về THƯ MỤC, không nói về NGƯỜI.
- Nhấn quy tắc "cụ thể hơn thì thắng": nếu file cá nhân và file phòng ban mâu thuẫn thì lấy file phòng ban.
