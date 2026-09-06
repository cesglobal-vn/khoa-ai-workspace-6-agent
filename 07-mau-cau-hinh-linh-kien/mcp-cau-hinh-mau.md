# Mẫu cấu hình MCP (cắm công cụ & dữ liệu ngoài)

> MCP là cổng cắm chuẩn để agent dùng công cụ ngoài: đọc file trong máy, tra web, đọc Google Drive,
> truy vấn cơ sở dữ liệu... Mỗi công cụ là một "MCP server". Cắm xong, agent gọi được các tool của nó.

## Hai cách cắm MCP

### Cách 1: qua giao diện Claude Desktop (khuyên dùng cho lớp)
1. Mở Claude Desktop, vào phần cài đặt kết nối (Connectors / MCP).
2. Chọn server muốn cắm (ví dụ Google Drive, Filesystem), bấm kết nối.
3. Cấp quyền khi được hỏi (đăng nhập tài khoản tương ứng nếu cần).
4. Quay lại Claude Code, agent đã dùng được các tool của server đó.

### Cách 2: bằng lệnh (cho ai quen thao tác dòng lệnh)
```
claude mcp add <ten-server> -- <lenh-chay-server>
```
Sau khi thêm, kiểm tra bằng:
```
claude mcp list
```

## Sau khi cắm: tool xuất hiện thế nào
Các tool của server hiện ra với tên dạng `mcp__<ten-server>__<ten-tool>`. Bạn không cần nhớ tên;
chỉ cần ra lệnh tự nhiên, ví dụ: "Đọc file doanh-thu.csv trong thư mục dự án và tính tổng doanh thu."

## Ví dụ MCP hay dùng cho khối văn phòng
| MCP server | Dùng để |
|---|---|
| Filesystem | Cho agent đọc/ghi file trong một thư mục cụ thể trên máy |
| Google Drive | Đọc tài liệu, sheet trên Drive |
| Web/Fetch | Tra cứu, đọc nội dung trang web |
| Cơ sở dữ liệu | Truy vấn số liệu từ hệ thống công ty (khi được cấp) |

## Lưu ý an toàn (dạy học viên)
- Chỉ cắm MCP từ nguồn tin cậy. Cấp quyền tối thiểu cần thiết.
- Với dữ liệu nhạy cảm (khách hàng, tài chính), hỏi bộ phận phụ trách trước khi cắm.
- Đọc kỹ khi agent xin quyền ghi/xóa; ưu tiên quyền chỉ đọc khi chỉ cần xem.

---

## Ghi chú giảng dạy
- Nhấn ý: skill dạy agent LÀM GÌ; MCP cho agent CHẠM VÀO CÁI GÌ (file, web, dữ liệu thật).
- Demo trước bằng Filesystem hoặc Google Drive vì trực quan, ai cũng có.
- Thao tác cắm cụ thể chốt theo phiên bản Claude Desktop lớp đang dùng.
