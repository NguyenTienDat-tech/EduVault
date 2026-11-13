# FLOW-007 Tìm kiếm lọc và sắp xếp kho

[SRS FR-17 đến FR-19](../SRS/SRS_EduVault.docx) · [Luồng xem kho](FR-07-xem-kho-tai-lieu.md) · [TASK-013](../../roadmap/02-tasks.md#task-013) · [Bản nháp API tài liệu](../api/documents.md)

- Giáo viên nhập từ khóa, đổi bộ lọc hoặc thứ tự. Backend áp dụng tất cả điều kiện trong kho hiện tại trước khi phân trang.
- Xóa từ khóa giữ các điều kiện còn lại. Xóa toàn bộ điều kiện trở về danh sách mặc định. Khi không có kết quả, ứng dụng cho thay đổi điều kiện. Khi lỗi tải, có thể thử lại.
- Kiểm thử theo AT-11. Dùng nhiều trang, giá trị đồng hạng và hai tài khoản. Trường tìm kiếm, xử lý dấu, bộ lọc và mặc định chờ TBD-10.
