# FR-07 Xem kho tài liệu

## Mục tiêu và điều kiện
Giáo viên đã đăng nhập mở tab Kho tài liệu để xem các tệp thuộc kho của mình.



## Luồng chính
1. Giáo viên mở tab Kho tài liệu. Android hiển thị trạng thái đang tải.
2. Android yêu cầu trang đầu. Backend xác thực phiên và truy vấn
   tài liệu của tài khoản hiện tại.
3. Android hiển thị tên, định dạng, dung lượng, ngày tải lên và danh mục.
4. Khi còn dữ liệu, giáo viên bấm Tải thêm. Android nối trang mới
   vào danh sách đang hiển thị.



## Trường hợp khác
- Kho trống. Hiển thị thông báo và nút Tải lên.
- Lỗi tải trang đầu. Hiển thị nút Thử lại.
- Lỗi tải thêm. Giữ danh sách hiện có và cho phép thử tải lại trang đó.
- Phiên hết hạn. Yêu cầu đăng nhập lại.



## Tiêu chí nghiệm thu
- Cho tài khoản có nhiều trang tài liệu, khi bấm Tải thêm,
  danh sách nối thêm kết quả mà không lặp bản ghi.
- Cho hai tài khoản A và B có tài liệu riêng, khi A mở kho,
  API chỉ trả tài liệu thuộc A.
- Cho tài khoản chưa có tài liệu, khi mở kho,
  màn hình hiển thị trạng thái trống và nút Tải lên.



## Cần chốt
- Đường dẫn API, cách phân trang và thứ tự mặc định.
  Khi đã chốt, ghi chi tiết trong `docs/api/`.