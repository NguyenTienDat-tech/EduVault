# FLOW-004 Tải lên tải xuống và xóa tệp

[SRS FR-06, FR-10 và FR-11](../SRS/SRS_EduVault.docx) · [TASK-010](../../roadmap/02-tasks.md#task-010) · [Bản nháp API tài liệu](../api/documents.md)

- Tải lên. Giáo viên chọn tệp, nhập tên và có thể thêm mô tả hoặc danh mục cùng kho. Backend xác thực, kiểm tra định dạng và hạn mức. Ứng dụng cập nhật kho sau khi File Storage và MySQL ghi thành công.
- Tải xuống. Từ màn chi tiết, giáo viên yêu cầu tải. Backend kiểm tra quyền trước khi đọc File Storage. Ứng dụng chỉ báo thành công khi lưu đủ nội dung.
- Xóa. Ứng dụng hiển thị tên tài liệu để xác nhận. Hủy giữ tài liệu. Khi xác nhận thành công, tài liệu rời kho và không còn tải được. Lỗi giữa các bước cần ghi nhận để đối soát.
- Kiểm thử theo AT-04, AT-07 và AT-08, gồm lỗi mạng, quyền sở hữu, thiếu dung lượng và gửi lại tải lên. Quy tắc định dạng, hạn mức và xóa chờ TBD-02/TBD-03/TBD-06.
