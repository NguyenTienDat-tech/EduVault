# Danh sách task

## Mục lục
1. [TASK-001 — Dựng MySQL local](#task-001)
2. [TASK-002 — Nối Spring Boot với MySQL và Flyway](#task-002)
3. [TASK-003 — Tạo API kiểm tra đọc dữ liệu thật](#task-003)
4. [TASK-004 — Gọi API kiểm tra từ Android theo MVVM](#task-004)
5. [TASK-005 — Xác minh CI và chạy từ bản clone sạch](#task-005)
6. [TASK-006 — Chốt hợp đồng Auth và danh sách kho cá nhân](#task-006)
7. [TASK-007 — Triển khai tài khoản và phiên](#task-007)
8. [TASK-008 — Triển khai danh sách kho cá nhân](#task-008)
9. [TASK-009 — Triển khai chi tiết, chỉnh sửa metadata và gán danh mục](#task-009)
10. [TASK-010 — Triển khai tải lên, tải xuống và xóa tệp](#task-010)
11. [TASK-011 — Triển khai danh mục cá nhân](#task-011)
12. [TASK-012 — Triển khai hồ sơ giáo viên](#task-012)
13. [TASK-013 — Triển khai tìm kiếm, lọc và sắp xếp](#task-013)
14. [TASK-014 — Nghiệm thu MVP](#task-014)



## Quy ước trạng thái
1. **Not Started** — Chưa bắt đầu thực hiện
2. **In Progress** — Đã bắt đầu và đang triển khai
3. **Blocked** — Chưa thể tiếp tục vì có trở ngại cụ thể được ghi trong task
4. **Done** — Đã đạt tiêu chí nghiệm thu và có bằng chứng

P0 là việc cần để nghiệm thu nền móng. P1 thuộc phạm vi MVP sau M0. Các mục FR bên dưới task dùng để chia việc và kiểm thử. Hợp đồng API có nhãn bản nháp chờ duyệt. TBD là nội dung chưa chốt. Link SRS trỏ đến tài liệu Word, mã FR/NFR chỉ vị trí cần đối chiếu.



## TASK-001
**Dựng MySQL local** · M0 · Infrastructure / Database · P0 · Blocked
- Tham chiếu: [SRS NFR-15](../docs/SRS/SRS_EduVault.docx). Flow và API nghiệp vụ không áp dụng.
- Phụ thuộc: Docker Engine hoạt động và PowerShell có quyền truy cập Docker Engine.
- Đã xác minh ngày 12/11/2026: `docker compose --env-file infra/.env -f infra/compose.yaml config --quiet` trả mã 0. `git check-ignore -v -- infra/.env` xác nhận file local được bỏ qua. `.env.example` có giá trị mẫu.
- Lý do bị chặn: Docker Desktop báo Engine running, nhưng Docker CLI của Codex bị từ chối truy cập Engine. Chạy `docker compose --env-file infra/.env -f infra/compose.yaml up -d --wait` từ PowerShell của máy phát triển, sau đó kiểm tra trạng thái và truy vấn bằng `eduvault_app`.
- Nghiệm thu: Compose khởi động MySQL và báo healthy. Tài khoản ứng dụng chạy được truy vấn kiểm tra. `git check-ignore infra/.env` xác nhận file local được bỏ qua, còn `.env.example` dùng giá trị mẫu.



## TASK-002
**Nối Spring Boot với MySQL và Flyway** · M0 · Backend / Database · P0 · Not Started
- Tham chiếu: [SRS Chương 6 và NFR-15](../docs/SRS/SRS_EduVault.docx). Flow và API nghiệp vụ không áp dụng.
- Phụ thuộc: [TASK-001](#task-001).
- Nghiệm thu: Backend khởi động với biến môi trường local và chạy được migration trên DB sạch. MySQL có lịch sử Flyway và bản ghi mẫu. Các thông tin kết nối nhạy cảm nằm ngoài Git.



## TASK-003
**Tạo API kiểm tra đọc dữ liệu thật** · M0 · Backend · P0 · Not Started
- Tham chiếu: [SRS Chương 5 và 6](../docs/SRS/SRS_EduVault.docx). Flow nghiệp vụ không áp dụng. Hợp đồng endpoint kiểm tra local còn TBD.
- Phụ thuộc: [TASK-002](#task-002).
- Nghiệm thu: Gọi API từ Windows, nhận HTTP 200 và JSON khớp bản ghi MySQL. Ghi lệnh và phản hồi vào bằng chứng task.



## TASK-004
**Gọi API kiểm tra từ Android theo MVVM** · M0 · Frontend · P0 · Not Started
- Tham chiếu: [SRS Chương 5 và NFR-12](../docs/SRS/SRS_EduVault.docx). Flow nghiệp vụ không áp dụng. API dùng hợp đồng kiểm tra từ [TASK-003](#task-003).
- Phụ thuộc: [TASK-003](#task-003).
- Nghiệm thu: Emulator hiện dữ liệu lấy qua ViewModel và repository. Khi Backend tạm dừng, màn hình báo lỗi. Sau khi Backend chạy lại, Thử lại đọc được dữ liệu.



## TASK-005
**Xác minh CI và chạy từ bản clone sạch** · M0 · Infrastructure / Frontend / Backend · P0 · In Progress
- Tham chiếu: [Cấu hình Backend CI](../.github/workflows/ci.yml). Flow nghiệp vụ không áp dụng. Kiểm tra API theo [TASK-003](#task-003).
- Phụ thuộc: Có thể kiểm tra build Backend ngay. Phần nghiệm thu tích hợp phụ thuộc [TASK-001](#task-001) đến [TASK-004](#task-004).
- Hiện trạng: Workflow build Backend đã được thêm vào repo. Chưa ghi nhận run CI đã đạt.
- Nghiệm thu: Có link run CI build Backend đạt, có kết quả kiểm thử Backend với datasource MySQL, và người khác làm theo hướng dẫn để chạy được luồng tích hợp từ bản clone sạch. Ghi rõ phần kiểm tra tự động và phần kiểm tra thủ công.



## TASK-006
**Chốt hợp đồng Auth và danh sách kho cá nhân** · M1 · API / Frontend / Backend · P1 · Not Started
- Tham chiếu: [SRS FR-01 đến FR-03, FR-07, NFR-01 và NFR-06](../docs/SRS/SRS_EduVault.docx), [FLOW-001 – FR-07](../docs/flows/FR-07-xem-kho-tai-lieu.md).
- Phụ thuộc: SRS và [đặc tả chức năng](<../docs/SRS/Đặc tả chức năng.docx>). Có thể làm song song với M0.
- Nghiệm thu: Có tài liệu trong `docs/api/` ghi đường dẫn, request/response, trạng thái lỗi và phân trang. Các điểm chưa chốt về phiên, tìm kiếm mặc định và hợp đồng được đối chiếu với TBD-05, TBD-10, TBD-11 trong SRS.



### Chốt hợp đồng trước khi tích hợp
- [ ] Auth — Chốt chính sách mật khẩu, vòng đời phiên, cách đăng xuất và lỗi xác thực. Đối chiếu TBD-05 và TBD-11 với [bản nháp Auth](../docs/api/auth.md).
- [ ] Kho — Chốt trường trả về, cách tải trang tiếp theo, thứ tự mặc định và quy tắc đồng hạng. Đối chiếu TBD-10 và TBD-11 với [bản nháp API tài liệu](../docs/api/documents.md).
- [ ] Android và Backend — Duyệt ví dụ request/response thành công và lỗi cho hai nhóm API trước khi bắt đầu tích hợp.



## TASK-007
**Triển khai tài khoản và phiên** · M1 · Frontend / Backend · P1 · Blocked
- Tham chiếu: [SRS FR-01 đến FR-03 và NFR-01 đến NFR-03](../docs/SRS/SRS_EduVault.docx), [đặc tả chức năng mục 3.1–3.2](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-002](../docs/flows/FR-01-den-FR-03-xac-thuc.md) · [API-001 bản nháp](../docs/api/auth.md).
- Phụ thuộc: [TASK-005](#task-005) và [TASK-006](#task-006).
- Lý do bị chặn: Hợp đồng Auth và chính sách phiên ở TBD-05/TBD-11 chưa được xác nhận.
- Nghiệm thu: Luồng đăng ký, đăng nhập và đăng xuất chạy theo đặc tả đã duyệt. Kiểm tra phiên hết hạn hoặc bị thu hồi và các trường hợp lỗi liên quan.



### FR-01 Đăng ký tài khoản
- [ ] Backend — Kiểm tra trường bắt buộc, email hợp lệ và duy nhất, lưu mật khẩu dạng băm có salt.
- [ ] Android — Làm biểu mẫu họ tên, email, mật khẩu và xác nhận mật khẩu. Hiển thị lỗi trường và kết quả đăng ký.
- [ ] Kiểm thử — AT-01. Thử email sai định dạng, email trùng và mật khẩu xác nhận không khớp. Đăng ký hợp lệ tạo đúng một tài khoản.



### FR-02 Đăng nhập
- [ ] Backend — Xác thực thông tin và cấp phiên theo TBD-05, dùng cơ chế phiên thống nhất cho các API bảo vệ.
- [ ] Android — Làm màn đăng nhập, bảo vệ thông tin phiên trên thiết bị và điều hướng sau đăng nhập.
- [ ] Kiểm thử — AT-02, NFR-02 và NFR-03. Thông tin sai bị từ chối. Phiên hết hạn yêu cầu xác thực lại.



### FR-03 Đăng xuất
- [ ] Backend — Kết thúc hoặc thu hồi phiên theo chính sách đã duyệt.
- [ ] Android — Xóa phiên trên thiết bị, trở về màn đăng nhập và xử lý trường hợp mất mạng theo TBD-05.
- [ ] Kiểm thử — AT-02. Kiểm tra mở lại màn cần phiên, dùng lại phiên đã thu hồi và đăng xuất khi mất mạng.



## TASK-008
**Triển khai danh sách kho cá nhân** · M2 · Frontend / Backend · P1 · Blocked
- Tham chiếu: [SRS FR-07, NFR-01, NFR-06 và AT-05](../docs/SRS/SRS_EduVault.docx), [FLOW-001 – FR-07](../docs/flows/FR-07-xem-kho-tai-lieu.md).
- Tài liệu triển khai: [FLOW-001](../docs/flows/FR-07-xem-kho-tai-lieu.md) · [API-003 bản nháp](../docs/api/documents.md).
- Phụ thuộc: [TASK-006](#task-006) và [TASK-007](#task-007).
- Lý do bị chặn: Chưa có API danh sách đã chốt và phiên xác thực để kiểm tra cách ly kho khi tích hợp thật.
- Nghiệm thu: Hiển thị tải, dữ liệu, kho trống và lỗi. Tải thêm trang đúng thứ tự, không lặp bản ghi. Hai tài khoản thử chỉ thấy tài liệu của mình.



### FR-07 Xem kho tài liệu cá nhân
- [ ] Backend — Trả metadata theo tài khoản đang xác thực, phân trang với thứ tự ổn định.
- [ ] Android — Hiển thị danh sách, kho trống, lỗi, hết phiên và Tải thêm theo FLOW-001.
- [ ] Kiểm thử — AT-05, NFR-01 và NFR-06. Thử hai tài khoản, kho trống, lỗi trang đầu và lỗi tải thêm. Dữ liệu ổn định qua các trang không lặp bản ghi.



## TASK-009
**Triển khai chi tiết, chỉnh sửa metadata và gán danh mục** · M3 · Frontend / Backend · P1 · Not Started
- Tham chiếu: [SRS FR-08, FR-09, FR-16](../docs/SRS/SRS_EduVault.docx), [đặc tả chức năng mục 3.5–3.6](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-005](../docs/flows/FR-08-FR-09-FR-16-chi-tiet-tai-lieu.md) · [API-003 bản nháp](../docs/api/documents.md).
- Phụ thuộc: [TASK-008](#task-008). Phần gán danh mục dùng dữ liệu từ [TASK-011](#task-011).
- Nghiệm thu: Chủ sở hữu xem và cập nhật được metadata đã cho phép. Backend từ chối tài liệu hoặc danh mục ngoài kho. Tệp gốc giữ nguyên khi sửa metadata.



### FR-08 Xem chi tiết tài liệu
- [ ] Backend — Trả metadata chi tiết sau khi kiểm tra quyền sở hữu.
- [ ] Android — Mở chi tiết từ danh sách, hiện dữ liệu và trạng thái không khả dụng.
- [ ] Kiểm thử — AT-05. Thử tài liệu đã xóa, không tồn tại và ngoài kho. Các trường hợp đó không trả metadata.



### FR-09 Chỉnh sửa thông tin tài liệu
- [ ] Backend — Kiểm tra quyền và lưu tên, mô tả theo phạm vi đã duyệt.
- [ ] Android — Điền sẵn metadata, hiển thị lỗi và làm mới chi tiết sau khi lưu.
- [ ] Kiểm thử — AT-06. Thử tên trống. So sánh tệp tải xuống trước và sau khi sửa metadata.



### FR-16 Gán tài liệu vào danh mục
- [ ] Backend — Kiểm tra tài liệu và danh mục thuộc cùng kho, lưu quan hệ theo TBD-04.
- [ ] Android — Dùng danh sách từ [TASK-011](#task-011) và cập nhật danh mục trên chi tiết.
- [ ] Kiểm thử — AT-10. Thử gán hợp lệ, danh mục ngoài kho và danh mục vừa bị xóa.



## TASK-010
**Triển khai tải lên, tải xuống và xóa tệp** · M3 · Backend / Frontend / File Storage · P1 · Not Started
- Tham chiếu: [SRS FR-06, FR-10, FR-11, NFR-04, NFR-08 đến NFR-10](../docs/SRS/SRS_EduVault.docx), [đặc tả chức năng mục 3.4, 3.7–3.8](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-004](../docs/flows/FR-06-FR-10-FR-11-quan-ly-tep.md) · [API-003 bản nháp](../docs/api/documents.md).
- Phụ thuộc: [TASK-007](#task-007), [TASK-008](#task-008) và các quyết định TBD-02, TBD-03, TBD-06. Xem [SRS mục 5.3 và 6.3](../docs/SRS/SRS_EduVault.docx) để đối chiếu yêu cầu lưu trữ.
- Nghiệm thu: Tệp gốc nằm trong File Storage, metadata trong MySQL. Tải xuống đúng nội dung và đúng quyền. Thử lỗi truyền tệp, xử lý gửi lại và xác nhận xóa theo chính sách đã duyệt.



### FR-06 Tải tài liệu lên
- [ ] Backend — Chốt File Storage, định dạng và hạn mức theo TBD-02/TBD-03. Ghi tệp và metadata, xử lý dữ liệu sót và gửi lại theo NFR-09/NFR-10.
- [ ] Android — Làm trình chọn tệp, form metadata và trạng thái truyền tệp ngoài luồng giao diện.
- [ ] Kiểm thử — AT-04. Thử sai định dạng, vượt hạn mức, lỗi MySQL/File Storage và gửi lại sau mất phản hồi. Chỉ tài liệu ghi đầy đủ xuất hiện trong kho.



### FR-11 Tải tài liệu xuống
- [ ] Backend — Kiểm tra phiên và chủ sở hữu trước khi đọc tệp từ File Storage.
- [ ] Android — Hiển thị tiến trình và chỉ báo thành công khi lưu đủ nội dung.
- [ ] Kiểm thử — AT-08. So sánh nội dung bản tải với bản gốc. Thử tài liệu ngoài kho, mất mạng và thiếu dung lượng.



### FR-10 Xóa tài liệu
- [ ] Backend — Áp dụng chính sách TBD-06 cho metadata, quyền tải và dọn tệp. Ghi nhận lỗi cần đối soát.
- [ ] Android — Làm hộp thoại xác nhận có tên tài liệu, cập nhật kho sau khi nhận kết quả.
- [ ] Kiểm thử — AT-07. Thử hủy, xác nhận, lỗi giữa các bước và truy cập lại tài liệu sau khi xóa.



## TASK-011
**Triển khai danh mục cá nhân** · M3 · Frontend / Backend · P1 · Not Started
- Tham chiếu: [SRS FR-12 đến FR-15](../docs/SRS/SRS_EduVault.docx), [đặc tả chức năng mục 3.9–3.10](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-006](../docs/flows/FR-12-den-FR-15-danh-muc.md) · [API-004 bản nháp](../docs/api/categories.md).
- Phụ thuộc: [TASK-007](#task-007) và quyết định TBD-04 về danh mục.
- Nghiệm thu: Giáo viên xem, tạo, sửa và xóa được danh mục của mình. Tài liệu thuộc danh mục đã xóa được xử lý theo chính sách đã duyệt.



### FR-13 Xem danh sách danh mục
- [ ] Backend — Trả danh mục của tài khoản đang xác thực.
- [ ] Android — Hiển thị danh sách, trạng thái trống và lỗi tải.
- [ ] Kiểm thử — AT-09. Danh mục thuộc kho khác không xuất hiện.



### FR-12 Tạo danh mục
- [ ] Backend — Kiểm tra tên bắt buộc và quy tắc trùng tên theo TBD-04.
- [ ] Android — Làm form tạo tên và mô tả tùy chọn, cập nhật danh sách khi lưu thành công.
- [ ] Kiểm thử — AT-09. Thử tạo thành công, tên trống và tên trùng theo chính sách.



### FR-14 Chỉnh sửa danh mục
- [ ] Backend — Kiểm tra chủ sở hữu và dữ liệu trước khi lưu.
- [ ] Android — Điền sẵn dữ liệu hiện tại, làm mới danh sách sau khi sửa.
- [ ] Kiểm thử — AT-09. Thử sửa hợp lệ và sửa danh mục không thuộc kho.



### FR-15 Xóa danh mục
- [ ] Backend — Xử lý quan hệ với tài liệu theo TBD-04 sau khi kiểm tra quyền.
- [ ] Android — Hiển thị tác động trong hộp thoại xác nhận, làm mới danh mục và phân loại tài liệu sau khi xóa.
- [ ] Kiểm thử — AT-10. Thử hủy, xóa danh mục trống và xóa danh mục đang có tài liệu theo quy tắc đã duyệt.



## TASK-012
**Triển khai hồ sơ giáo viên** · M3 · Frontend / Backend · P1 · Not Started
- Tham chiếu: [SRS FR-04, FR-05](../docs/SRS/SRS_EduVault.docx), [đặc tả chức năng mục 3.3](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-003](../docs/flows/FR-04-den-FR-05-ho-so.md) · [API-002 bản nháp](../docs/api/profile.md).
- Phụ thuộc: [TASK-007](#task-007) và quyết định về trường được phép sửa tại TBD-05.
- Nghiệm thu: Giáo viên xem đúng hồ sơ của mình, cập nhật được trường đã duyệt, xử lý dữ liệu sai và hiển thị kết quả sau khi lưu.



### FR-04 Xem hồ sơ
- [ ] Backend — Lấy hồ sơ theo phiên hiện tại.
- [ ] Android — Hiển thị các trường được phép công bố và xử lý lỗi tải.
- [ ] Kiểm thử — AT-03. Hai tài khoản lần lượt mở hồ sơ và thấy đúng dữ liệu của mình.



### FR-05 Cập nhật hồ sơ
- [ ] Backend — Xác thực và lưu các trường được phép sửa theo TBD-05.
- [ ] Android — Làm form đã điền sẵn, có Lưu, Hủy và thông báo lỗi theo trường.
- [ ] Kiểm thử — AT-03. Mở lại hồ sơ sau khi lưu. Thử gửi dữ liệu sai hoặc trường chưa được phép sửa.



## TASK-013
**Triển khai tìm kiếm, lọc và sắp xếp** · M3 · Frontend / Backend · P1 · Not Started
- Tham chiếu: [SRS FR-17 đến FR-19 và NFR-06](../docs/SRS/SRS_EduVault.docx), [FLOW-001 – danh sách làm nền](../docs/flows/FR-07-xem-kho-tai-lieu.md), [đặc tả chức năng mục 3.11](<../docs/SRS/Đặc tả chức năng.docx>).
- Tài liệu triển khai: [FLOW-007](../docs/flows/FR-17-den-FR-19-truy-van-kho.md) · [API-003 bản nháp](../docs/api/documents.md).
- Phụ thuộc: [TASK-008](#task-008), danh mục từ [TASK-011](#task-011) và tiêu chí đã duyệt tại TBD-10.
- Nghiệm thu: Tìm, lọc và sắp xếp trên dữ liệu phân trang theo tiêu chí đã chốt. Kiểm tra trạng thái không có kết quả và bảo đảm kết quả thuộc đúng kho.



### FR-17 Tìm kiếm tài liệu
- [ ] Backend — Tìm trong kho cá nhân theo trường và quy tắc tiếng Việt đã duyệt tại TBD-10.
- [ ] Android — Gửi từ khóa, hiển thị lỗi và trạng thái không có kết quả.
- [ ] Kiểm thử — AT-11. Thử từ khóa khớp, không khớp và xóa từ khóa khi còn bộ lọc.



### FR-18 Lọc tài liệu
- [ ] Backend — Áp dụng bộ lọc đã duyệt trước khi phân trang, giới hạn kết quả theo chủ sở hữu.
- [ ] Android — Hiển thị, thay đổi và xóa điều kiện lọc. Bộ lọc danh mục dùng dữ liệu từ [TASK-011](#task-011).
- [ ] Kiểm thử — AT-11. Thử kết hợp từ khóa và bộ lọc, bỏ từng điều kiện và lấy nhiều trang.



### FR-19 Sắp xếp tài liệu
- [ ] Backend — Áp dụng tiêu chí, chiều sắp xếp và cách xử lý đồng hạng theo TBD-10 trước khi phân trang.
- [ ] Android — Cho chọn thứ tự được hỗ trợ và tải lại danh sách khi đổi.
- [ ] Kiểm thử — AT-11 và NFR-06. Dữ liệu nhiều trang có giá trị đồng hạng vẫn cho thứ tự ổn định trên tập dữ liệu giữ nguyên.



## TASK-014
**Nghiệm thu MVP** · M3 · Frontend / Backend / Database / Infrastructure · P1 · Not Started
- Tham chiếu: [SRS Chương 7, AT-01 đến AT-12 và NFR áp dụng](../docs/SRS/SRS_EduVault.docx), [danh mục tính năng và liên kết flow/API](04-features.md#mvp).
- Phụ thuộc: [TASK-005](#task-005) và [TASK-007](#task-007) đến [TASK-013](#task-013). Các tham số ảnh hưởng kiểm thử đã được phê duyệt.
- Nghiệm thu: Các ca nghiệm thu và phép xác minh NFR áp dụng đạt trên bản phát hành kiểm thử. Có kết quả thực tế, môi trường và liên kết bằng chứng. Các lỗi gây truy cập trái quyền, mất dữ liệu hoặc chặn luồng chính đã được sửa và kiểm tra lại.
