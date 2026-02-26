Identity, Authentication, Authorisation, and Accountability (IAAA) -> đây là lỗ hổng liên quan tới nhận diện, xác thực, ủy quyền, và giải trình.
Ví dụ:
+ Nhận diện: tài khoản duy nhất đại diện cho cá nhân hoặc là dịch vụ
+ Xác thực: chứng minh (password, OTP, key)
+ Ủy quyền: những gì mà cá nhân đó được phép làm
+ Giải trình: ghi chép lại và thông báo what, when, where

A01: Broken Access Control; máy chủ cho phép người dùng sử dụng quyền truy cập trái phép. Đây được xem là leo thang đặc quyền theo chiều ngang (cùng vai trò nhưng lại xem được thông tin của user khác) do ứng dụng quá tin tưởng vào người dùng
<img width="1230" height="1151" alt="image" src="https://github.com/user-attachments/assets/76a6c140-5ab9-48d8-9a4a-6d0294c8f44c" />
<img width="1230" height="1149" alt="image" src="https://github.com/user-attachments/assets/676ec3ec-694e-4ebb-909c-711c143be3cc" />
Trên đây là hai bức ảnh, bức đầu tiên với id=5 sau đó mình đã thay đổi id=7 và tìm được flag

A07: Authentication Failures; lỗi xác thực xảy ra khi dev code web mắc lỗi bảo mật như là mật khẩu yếu/dễ đoán (bị leak); lỗi logic đăng nhập, đăng kí (không phân biệt chữ hoa với chữ thường); tên người dùng được liệt kê hoặc dòng trạng thái cho thấy tên người dùng tồn tại; cookie bị đánh cắp
<img width="1232" height="856" alt="image" src="https://github.com/user-attachments/assets/1d800969-a812-463a-afb3-8d9cde5c8443" />
<img width="1242" height="756" alt="image" src="https://github.com/user-attachments/assets/1d323aa3-4636-4fe3-be19-e7ab8d55b27b" />
<img width="1233" height="1091" alt="image" src="https://github.com/user-attachments/assets/48e4d3e1-dd12-44de-90f4-32c2341e6d48" />
Trên đây là lỗi logic không phân biệt hoa thường nên dễ đăng kí trùng với tài khoản mặc định của web admin

A09: Logging & Alerting Failures; ứng dụng không được ghi log lại dẫn tới thiếu các sự kiện xác thực





