# Thứ tự ưu tiên

1. **M0 Nền móng**
   - **Thứ tự triển khai** — [TASK-001](02-tasks.md#task-001) → [TASK-002](02-tasks.md#task-002) → [TASK-003](02-tasks.md#task-003) → [TASK-004](02-tasks.md#task-004). Kiểm tra CI build trong [TASK-005](02-tasks.md#task-005) song song.
   - **Lý do** — Kiểm tra từng đoạn kết nối để khoanh vùng lỗi. Kết thúc M0 bằng chạy lại từ bản clone sạch.



2. **M1 Auth**
   - **Thứ tự triển khai** — [TASK-006](02-tasks.md#task-006) có thể bắt đầu song song với M0, sau đó [TASK-007](02-tasks.md#task-007).
   - **Lý do** — Auth và cách kiểm tra phiên là tiền đề của kho cá nhân.



3. **M2 Kho cá nhân**
   - **Thứ tự triển khai** — [TASK-008](02-tasks.md#task-008).
   - **Lý do** — Kiểm chứng cách ly dữ liệu giữa hai tài khoản trên một luồng trước khi mở rộng.



4. **M3 Hoàn thiện MVP**
   - **Thứ tự triển khai** — Sau M2, triển khai [TASK-009](02-tasks.md#task-009), [TASK-010](02-tasks.md#task-010), [TASK-011](02-tasks.md#task-011), [TASK-012](02-tasks.md#task-012) và [TASK-013](02-tasks.md#task-013) theo phụ thuộc từng task. Chạy [TASK-014](02-tasks.md#task-014) khi các luồng đã sẵn sàng.
   - **Lý do** — Chốt File Storage và chính sách tệp trước khi tích hợp truyền tệp. Làm danh mục trước phần gán FR-16 và lọc theo danh mục. Hồ sơ có thể bắt đầu sau Auth khi đã chốt trường được sửa.



## Việc đang bị chặn
- [TASK-001](02-tasks.md#task-001) cần chạy Compose từ PowerShell có quyền truy cập Docker Engine, rồi xác minh healthcheck và truy vấn MySQL.

- [TASK-007](02-tasks.md#task-007) cần hợp đồng Auth và chính sách phiên đã xác nhận.
- [TASK-008](02-tasks.md#task-008) cần hợp đồng phân trang và luồng xác thực để chạy thử kho của hai tài khoản.

Xem trạng thái và điều kiện gỡ chặn tại từng task. Các tham số cần xác nhận nằm trong [SRS Chương 8](../docs/SRS/SRS_EduVault.docx).
