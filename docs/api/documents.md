# API-003 Kho và tài liệu

**Trạng thái hợp đồng — Bản nháp chờ duyệt.** [TASK-006](../../roadmap/02-tasks.md#task-006) · [FLOW-001](../flows/FR-07-xem-kho-tai-lieu.md) · [FLOW-004](../flows/FR-06-FR-10-FR-11-quan-ly-tep.md) · [FLOW-005](../flows/FR-08-FR-09-FR-16-chi-tiet-tai-lieu.md) · [FLOW-007](../flows/FR-17-den-FR-19-truy-van-kho.md)

1. **Xem kho FR-07 và truy vấn FR-17 đến FR-19**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Phiên, tham số phân trang và các điều kiện tìm, lọc, sắp xếp đã duyệt.
   - **Kết quả và lỗi cần quy định** — Trang kết quả thuộc kho hiện tại, thông tin để tải thêm, kho trống và lỗi.

2. **Chi tiết FR-08**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Mã tài liệu.
   - **Kết quả và lỗi cần quy định** — Metadata, hoặc lỗi tài liệu không khả dụng.

3. **Sửa và gán FR-09, FR-16**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Mã tài liệu, trường metadata được sửa và lựa chọn danh mục khi áp dụng.
   - **Kết quả và lỗi cần quy định** — Metadata cập nhật, lỗi dữ liệu hoặc đối tượng không khả dụng.

4. **Tải lên FR-06**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Tệp, metadata, thông tin nhận diện thao tác gửi lại theo TBD-11.
   - **Kết quả và lỗi cần quy định** — Tài liệu được ghi đầy đủ, lỗi định dạng, hạn mức hoặc trạng thái cần xác minh.

5. **Xóa FR-10**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Mã tài liệu cần xóa.
   - **Kết quả và lỗi cần quy định** — Kết quả xử lý theo chính sách xóa hoặc lỗi cần đối soát.

6. **Tải xuống FR-11**
   - **Dữ liệu nghiệp vụ cần trao đổi** — Mã tài liệu cần tải.
   - **Kết quả và lỗi cần quy định** — Nội dung tệp đúng quyền, hoặc lỗi nếu tài liệu không khả dụng.

TBD-02, TBD-03, TBD-04, TBD-06, TBD-10 và TBD-11 — Chốt chính sách tệp, danh mục, truy vấn, phương thức HTTP, đường dẫn, định dạng dữ liệu và mã lỗi. Mọi thao tác dùng phiên hợp lệ và quyền sở hữu.
