# Tiến độ EduVault

## 1. Tình trạng task
1. **Đang làm** — [TASK-005](02-tasks.md#task-005) đã có workflow build Backend. Còn cần kết quả GitHub Actions và kiểm thử tích hợp từ bản clone sạch.
2. **Đang bị chặn** — [TASK-001](02-tasks.md#task-001) chờ xác minh MySQL chạy được. [TASK-007](02-tasks.md#task-007) chờ hợp đồng Auth và chính sách phiên. [TASK-008](02-tasks.md#task-008) chờ xác thực và hợp đồng phân trang để tích hợp kho cá nhân.
3. **Có thể chuẩn bị song song** — Dùng hai bản nháp API để rà soát Auth và kho cá nhân trong [TASK-006](02-tasks.md#task-006).



## 2. Tiến độ theo phần
1. **Frontend Android** — Có Kotlin, Compose và Gradle Wrapper. [MainActivity](../frontend/app/src/main/java/com/example/eduvault/MainActivity.kt) vẫn hiển thị màn mẫu. Bước tiếp theo là kết nối API kiểm tra qua ViewModel và repository trong [TASK-004](02-tasks.md#task-004). Thiết bị và phiên bản Android hỗ trợ chờ TBD-01.
2. **Backend Spring Boot** — Có Maven Wrapper, Java 21 và các dependency Web MVC, Actuator, JDBC, MySQL và Flyway trong [pom.xml](../backend/pom.xml). [TASK-002](02-tasks.md#task-002) sẽ nối datasource và chạy migration. [TASK-003](02-tasks.md#task-003) sẽ kiểm tra API đọc dữ liệu thật.
3. **MySQL và Infrastructure** — [compose.yaml](../infra/compose.yaml) khai báo MySQL 8.4, cổng local 3307 và healthcheck. [.env.example](../infra/.env.example) chứa giá trị mẫu và [.gitignore](../.gitignore) có quy tắc bỏ qua `infra/.env`. [application.properties](../backend/src/main/resources/application.properties) mới có tên ứng dụng, chưa có datasource hoặc migration SQL trong repo.
4. **File Storage** — SRS quy định lưu tệp gốc riêng và lưu metadata trong MySQL. Phương án lưu trữ đang chờ chốt trong [TASK-010](02-tasks.md#task-010).
5. **GitHub Actions** — [ci.yml](../.github/workflows/ci.yml) chạy Maven package với `-DskipTests` khi push hoặc mở PR. Cần ghi nhận kết quả build và chạy kiểm thử tích hợp theo [TASK-005](02-tasks.md#task-005).
6. **Tài liệu MVP** — Đã đối chiếu [SRS](../docs/SRS/SRS_EduVault.docx) và [Đặc tả chức năng](<../docs/SRS/Đặc tả chức năng.docx>). Đã chia đủ 19 yêu cầu chức năng thành checklist Backend, Android và kiểm thử. [Danh mục tính năng](04-features.md) liên kết đến 7 luồng nghiệp vụ và 4 bản nháp API chờ duyệt.



## 3. Bằng chứng và lần kiểm tra tiếp theo
1. `docker compose --env-file infra/.env -f infra/compose.yaml config --quiet` trả mã 0 trong lần rà soát này.
2. `docker compose --env-file infra/.env -f infra/compose.yaml ps` báo Windows không tìm thấy kênh kết nối tới Docker Engine. Cần kiểm tra lại khi Engine sẵn sàng để xác nhận container `healthy` và chạy truy vấn bằng `eduvault_app`.
3. Repo có test mẫu Backend và Android. Chưa ghi nhận kết quả nghiệm thu MySQL → Spring Boot → Android hoặc kết quả GitHub Actions đạt. Ghi lệnh, kết quả kiểm thử và link run vào task tương ứng khi có bằng chứng.
