# FLOW-005 Chi tiết chỉnh sửa và phân loại tài liệu

[SRS FR-08, FR-09 và FR-16](../SRS/SRS_EduVault.docx) · [TASK-009](../../roadmap/02-tasks.md#task-009) · [Bản nháp API tài liệu](../api/documents.md)

- Từ kho cá nhân, giáo viên chọn tài liệu. Backend kiểm tra chủ sở hữu trước khi trả metadata.
- Giáo viên mở form đã điền sẵn, sửa tên, mô tả hoặc chọn danh mục cùng kho. Backend kiểm tra và lưu metadata, giữ nội dung tệp gốc.
- Tài liệu đã xóa hoặc ngoài kho không trả metadata. Dữ liệu sai hoặc danh mục không khả dụng bị từ chối. Khi chưa rõ kết quả lưu, tải lại dữ liệu để đối chiếu.
- Kiểm thử theo AT-05, AT-06 và AT-10. Quy tắc gán danh mục chờ TBD-04.
