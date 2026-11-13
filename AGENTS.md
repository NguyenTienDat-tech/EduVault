# Hướng dẫn làm việc với EduVault

## Cấu trúc repo
- `frontend/` chứa ứng dụng Android Kotlin và Compose.
  UI hiển thị trạng thái từ ViewModel. ViewModel lấy dữ liệu qua repository.
- `backend/` chứa REST API Spring Boot. Controller nhận request,
  Service xử lý nghiệp vụ, Repository truy cập MySQL.
- `infra/` chứa cấu hình chạy môi trường local.
- `docs/flows/` mô tả hành vi theo từng mã yêu cầu trong SRS.



## Khi triển khai tính năng
- Đọc luồng nghiệp vụ và hợp đồng API liên quan trước khi sửa.
- Ghi rõ điểm TBD ảnh hưởng đến hành vi để nhóm xác nhận.
- Backend kiểm tra quyền truy cập theo tài khoản đã xác thực.
- Dùng biến môi trường cho thông tin kết nối. Giữ mật khẩu và token ngoài Git.



## Kiểm tra thay đổi trên Windows
- Android, chạy từ `frontend/`: `.\gradlew.bat :app:assembleDebug`
- Backend, chạy từ `backend/`: `.\mvnw.cmd -B -DskipTests package`
- Khi MySQL kiểm thử đã được cấu hình, chạy Backend với `.\mvnw.cmd -B verify`.
- Khi bàn giao, ghi rõ lệnh đã chạy và kết quả.