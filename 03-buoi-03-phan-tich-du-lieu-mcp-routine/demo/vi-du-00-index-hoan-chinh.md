# Ví dụ: file 00-index.md hoàn chỉnh

> Đây là ĐÁP ÁN cho thư mục `phong-kinh-doanh-mau`. Giảng viên dùng để đối chiếu khi học viên chạy lệnh nhờ agent tự dựng index. Nội dung khối dưới chính là file `00-index.md` đặt ở gốc thư mục đó.

```markdown
# Index thư mục phòng Kinh doanh

> Mỗi file một dòng. Cập nhật khi thêm hoặc bớt file.

## 01-khach-hang/
| File | Nội dung |
|---|---|
| `minh-long.md` | Công ty TNHH Minh Long, ngành Sản xuất, ông Nguyễn Minh Long Giám đốc. Đang dùng gói Cao cấp, hợp đồng 120 triệu ký 10/6/2026, đang tư vấn mở rộng thêm 10 người dùng |
| `hai-nam.md` | Cửa hàng Hải Nam, ngành Bán lẻ, chị Trần Thị Nam chủ cửa hàng. Khách cũ từ 2025, đã hủy đơn 120 triệu tháng 3/2026 do đổi ý cấu hình, cần chăm sóc lại |
| `an-phat.md` | Công ty An Phát, ngành Dịch vụ, anh Lê An Trưởng phòng Hành chính. Đơn DH003 trị giá 120 triệu quá hạn thanh toán, đã nhắc 2 lần ngày 15/3 và 22/3, cần nhắc lần 3 |

## 02-bao-gia/
| File | Nội dung |
|---|---|
| `bao-gia-an-phat-2027.md` | Báo giá gói Cao cấp cho An Phát ngày 05/01/2027: 120 triệu đã gồm thuế, 20 người dùng, đào tạo 2 buổi, hiệu lực 30 ngày |

## 03-hop-dong/
| File | Nội dung |
|---|---|
| `hd-minh-long-2026.md` | Hợp đồng số 2026/HĐDV-ML với Minh Long, 120 triệu đã gồm thuế, chia 2 đợt 50/50, ký 10/6/2026, thời hạn 12 tháng, tự động gia hạn, phạt chậm 0,05 phần trăm mỗi ngày |

## 04-so-lieu/
| File | Nội dung |
|---|---|
| `doanh-thu-quy.csv` | Doanh thu tháng 01 tới 03, 2 khu vực Hà Nội và TP HCM, 2 sản phẩm Tiêu chuẩn và Cao cấp, 12 dòng, tổng 2.870 triệu |
| `don-hang.csv` | 10 đơn hàng tháng 3/2026 kèm trạng thái: 6 đã thanh toán, 3 chờ thanh toán tổng 275 triệu, 1 đơn hủy 120 triệu |

## 05-bao-cao/
| File | Nội dung |
|---|---|
| `README.md` | Ghi chú thư mục lưu kết quả agent tạo ra, quy ước đặt tên `[loai]-[thang]-[nam].md` |
```

## Ghi chú cho giảng viên
- Lệnh học viên chạy để tạo index: "Đọc toàn bộ thư mục này và tạo file 00-index.md liệt kê mỗi file một dòng: tên file và một câu mô tả nội dung. Nhóm theo thư mục con, trình bày dạng bảng."
- Điểm đối chiếu: đủ 8 file, đủ 5 nhóm, mô tả có số liệu cụ thể chứ không chung chung.
- Nếu học viên ra index thiếu file hoặc mô tả mơ hồ, cho chạy lại kèm câu: "Ghi rõ số tiền và trạng thái trong phần mô tả."
