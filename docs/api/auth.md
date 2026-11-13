# API-001 Tài khoản và phiên

**Trạng thái hợp đồng — Bản nháp chờ duyệt.** [TASK-006](../../roadmap/02-tasks.md#task-006) · [FLOW-002](../flows/FR-01-den-FR-03-xac-thuc.md)

1. **Đăng ký FR-01**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Họ tên, email, mật khẩu. Chốt cách kiểm tra xác nhận mật khẩu giữa hai phía.
   - **Kết quả và lỗi cần quy định** — Tạo tài khoản, báo trường không hợp lệ, email trùng hoặc lỗi máy chủ.

2. **Đăng nhập FR-02**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Email, mật khẩu.
   - **Kết quả và lỗi cần quy định** — Cấp thông tin phiên khi hợp lệ, từ chối thông tin sai.

3. **Đăng xuất FR-03**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Thông tin phiên cần kết thúc.
   - **Kết quả và lỗi cần quy định** — Phiên đã thu hồi bị từ chối khi dùng lại.

TBD-05 và TBD-11 — Chốt phương thức HTTP, đường dẫn, lược đồ request/response, mã lỗi, cách truyền phiên, hết hạn và thu hồi.
