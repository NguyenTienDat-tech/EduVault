## Mục lục

1. [Tiến độ hiện tại](#tiến-độ-hiện-tại)
2. [Các file trong roadmap](#các-file-trong-roadmap)
3. [Cập nhật Roadmap](#cập-nhật-roadmap)



## Tiến độ hiện tại
1. **Nền móng** — Đã có project Android, Spring Boot và cấu hình MySQL local. Docker Compose đọc được cấu hình. [TASK-001](02-tasks.md#task-001) còn chờ xác nhận MySQL chạy và truy vấn thành công.
2. **Kiểm tra tự động** — Đã có workflow build Backend. [TASK-005](02-tasks.md#task-005) còn cần kết quả GitHub Actions và kiểm thử tích hợp từ bản clone sạch.
3. **Chuẩn bị MVP** — Đã lập checklist cho 19 yêu cầu chức năng, có 7 luồng nghiệp vụ và 4 bản nháp API. Có thể rà soát hợp đồng Auth và danh sách kho ở [TASK-006](02-tasks.md#task-006) song song với M0.




## Các file trong roadmap
1. **[01 Tiến độ](01-progress.md)** — Xem bằng chứng triển khai và kiểm tra theo module
2. **[02 Danh sách task](02-tasks.md)** — Tra trạng thái, tiêu chí nghiệm thu và phụ thuộc của từng task
3. **[03 Ưu tiên](03-priorities.md)** — Xem việc cần làm tiếp và nguyên nhân bị chặn
4. **[04 Tính năng](04-features.md)** — Nối yêu cầu, flow, API và task
5. **[05 Hoàn thành](05-completed.md)** — Tra nhật ký nghiệm thu theo ngày hoặc mốc



## Cập nhật Roadmap
Trước khi code, đọc AGENTS.md, trang này, task được giao, SRS và flow liên quan. Kiểm tra phụ thuộc và quyết định còn TBD. Sau khi làm, chạy kiểm tra phù hợp, ghi bằng chứng và cập nhật trạng thái ở [02 Danh sách task](02-tasks.md). Sau đó cập nhật phần tổng hợp và nhật ký nếu có kết quả mới. Khi nghiệp vụ thay đổi, cập nhật SRS hoặc Flow theo yêu cầu thay đổi đã được xác nhận.

Giữ nguyên mã FR và NFR trong SRS. Gán mã FLOW và API khi có tài liệu để trỏ tới. Mỗi TASK có một mục cố định trong danh sách task. FEATURE dùng để nhóm các FR liên quan. Liên kết có dạng `02-tasks.md#task-001` và `04-features.md#feature-003`.
