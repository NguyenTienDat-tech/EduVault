# FLOW-003 Xem và cập nhật hồ sơ

[SRS FR-04 đến FR-05](../SRS/SRS_EduVault.docx) · [TASK-012](../../roadmap/02-tasks.md#task-012) · [Bản nháp API hồ sơ](../api/profile.md)

- Giáo viên đã đăng nhập mở hồ sơ. Backend lấy dữ liệu theo phiên hiện tại.
- Khi sửa, ứng dụng điền sẵn dữ liệu. Lưu gửi các trường được phép, Hủy đóng form. Sau khi lưu thành công, mở lại thấy dữ liệu mới.
- Dữ liệu sai hiển thị lỗi và giữ dữ liệu đã lưu. Hết phiên yêu cầu đăng nhập lại. Lỗi mạng cho phép thử lại.
- Kiểm thử theo AT-03. Phạm vi trường được sửa chờ TBD-05.
