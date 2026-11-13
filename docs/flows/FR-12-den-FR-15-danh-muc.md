# FLOW-006 Quản lý danh mục cá nhân

[SRS FR-12 đến FR-15](../SRS/SRS_EduVault.docx) · [TASK-011](../../roadmap/02-tasks.md#task-011) · [Bản nháp API danh mục](../api/categories.md)

- Giáo viên mở danh mục và thấy dữ liệu trong kho của mình. Khi tạo hoặc sửa, gửi tên và mô tả tùy chọn. Sau khi lưu thành công, ứng dụng làm mới danh sách.
- Khi xóa, ứng dụng yêu cầu xác nhận và nêu tác động đến tài liệu. Backend kiểm tra quyền và xử lý các tài liệu liên quan theo quy tắc đã duyệt.
- Kiểm thử theo AT-09 và AT-10. Kiểm tra tên trống, tên trùng, danh mục ngoài kho, hủy xóa và xóa danh mục đang có tài liệu. Quy tắc nghiệp vụ chờ TBD-04.
