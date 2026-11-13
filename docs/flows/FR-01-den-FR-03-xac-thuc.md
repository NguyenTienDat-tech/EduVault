# FLOW-002 Xác thực và kết thúc phiên

[SRS FR-01 đến FR-03](../SRS/SRS_EduVault.docx) · [TASK-007](../../roadmap/02-tasks.md#task-007) · [Bản nháp API Auth](../api/auth.md)

- Đăng ký. Giáo viên nhập họ tên, email, mật khẩu và xác nhận mật khẩu. Backend kiểm tra dữ liệu và tính duy nhất của email. Khi thành công, giáo viên có thể quay lại màn đăng nhập.
- Đăng nhập. Backend xác thực, cấp phiên và ứng dụng mở kho cá nhân. Dữ liệu sai được báo phù hợp. Phiên hết hạn dẫn về xác thực lại.
- Đăng xuất. Ứng dụng yêu cầu Backend kết thúc phiên, dọn phiên trên thiết bị và về màn đăng nhập. Nếu mất mạng, vẫn thoát phiên local. Thu hồi từ xa theo TBD-05.
- Kiểm thử theo AT-01 và AT-02. Chính sách mật khẩu, vòng đời phiên và hợp đồng API chờ TBD-05/TBD-11.
