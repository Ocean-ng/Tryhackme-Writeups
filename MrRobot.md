Đầu tiên ta sẽ chuẩn bị một máy ảo kali linux kết nối vpn của tryhackme để vào địa chỉ trong phòng Mr Robot CTF.

![image](https://github.com/user-attachments/assets/9c07b9ee-d2d6-4b98-814a-4afa3dd56c60)

Trên đây là hình ảnh đầu tiên khi kết nối với địa chỉ web. Theo như thói quen thì ta sẽ tò mò về những câu lệnh mr robot đưa ra. Nên là sẽ nhập từng câu lệnh để xem có thông tin gì. Sau khi xem là những đoạn video về phim Mr Robot với nhân vật chính là Elliot Alderson.
Tiếp theo ta sẽ sử dụng nmap để quét xem có những cổng nào đang mở

![image](https://github.com/user-attachments/assets/94ab8d8e-0021-49af-ab9b-06b219473e06)

Có thể thấy trên hình chỉ có ssh, http và https nên ta sẽ sử dụng gobuster để xem những trang đang ẩn

![image](https://github.com/user-attachments/assets/2e8cb77c-5b6c-416f-b864-c7ac4c36598a)

Ta chú ý hơn với những trang có status 200, thông thường các địa chỉ url sẽ nằm trong sitemap và robots.txt

![image](https://github.com/user-attachments/assets/8f956451-8cbe-43a8-b3ad-b6c3ab66c890)

![image](https://github.com/user-attachments/assets/36a36737-418e-4fe2-89e9-e50c4338fea1)

Ta thấy được 2 file mà mr robot không muốn ta biết. 

![image](https://github.com/user-attachments/assets/a8718800-16ec-4cdd-8848-32673e442d51)

Vậy là ta đã tìm được key1 : 073403c8a58a1f80d943455fb30724b9

![image](https://github.com/user-attachments/assets/42e6c2f1-3695-4825-978d-79213d2b05bf)

Quay lại với file fsocity.dic, đây là một file rất dài và nhiều từ lặp lại nên để tấn công bruteforce thì sẽ rất mất thời gian và tài nguyên nên ta sẽ sắp xếp và xóa những kí tự trùng lặp file này với câu lệnh: sort fsocity.dic | uniq > list.txt . (tải file về máy bằng lệnh wget)

![image](https://github.com/user-attachments/assets/accb2e07-78b7-4d0d-93a6-0cab4ee14b58)

file đã nhẹ đi bớt, ta sẽ lọc những từ khóa có liên quan tới phim mr robot và những tên mang đặc quyền cao nhất như là mrrobot, admin, elliot, Alderson. (không phân biệt viết hoa viết thường)

![image](https://github.com/user-attachments/assets/8820e360-8c77-404c-b8b4-019d44b0c0e5)

![image](https://github.com/user-attachments/assets/e833101e-e31c-42b7-8f31-0c6d0eda374d)

lúc đầu khi quét bằng gobuster thì ta thấy được trang đăng nhập vào wordpress, với danh sách này thì ta sẽ thử điền username hợp lệ trước. Bạn có thấy sự khác biệt gì ở đây không? Đúng như vậy, ta đã điền username được đăng kí và bây giờ chỉ cần tìm mật khẩu.

![image](https://github.com/user-attachments/assets/fac3fb22-877b-4c00-a858-4866fa268d99)

Sử dụng tool wpscan để tìm lỗ hổng wordpress: wpscan --url http://ip-address -U Elliot -P list.txt. Vậy trên hình ảnh này thì ta thấy được username và password hợp lệ ER28-0652

![image](https://github.com/user-attachments/assets/e05a5385-e3e6-4c41-8995-be23901ca26b)

Sau một lục lọi trang web thì tìm được lỗ hổng upload file (không dùng upload media file vì file php không hợp lệ và nếu muốn bypass thì mất thêm thời gian và upload media file lạ sẽ bị admin dễ phát hiện). 

![image](https://github.com/user-attachments/assets/73ca5d62-0c12-49c0-a614-f50ec0b222f1)

Ta sử dụng kĩ thuật gọi là web shell upload và server của wordpress đc viết bằng php nên sẽ sử dụng code php để tấn công. Kĩ thuật web shell upload sẽ sử dụng reverse shell để làm server tự động gửi kết nối tới client mà không bị tường lửa chặn. (Trong kali linux có sẵn code reverse shell)

![image](https://github.com/user-attachments/assets/61a9f4df-7c4e-4023-815d-83b0624fe633)

Thay đổi ip bằng ip client kali linux, đổi cổng lớn hơn 1024 để tránh các dịch vụ được đăng kí riêng. Xóa hết code trong 404.php và copy code php reverse shell vào 404.php rồi nhấn update file. Sau đó chạy tool netcat: nc -lvnp 1025

![image](https://github.com/user-attachments/assets/79e1174b-e525-4114-92ec-0332b1a7e47e)

Sau đó kết nối trang không tồn tại để server cho 404.php chạy. Sử dụng địa chỉ url: http://10.82.188.192/wp-content/themes/twentyfifteen/404.php 
P/s: cấu hình web nào thì ghi ra web đó - ở đây ta sử dụng web twentyfifteen

![image](https://github.com/user-attachments/assets/dfb6ad9f-6c4e-4dc8-8fa3-a72a2eb864b5)

![image](https://github.com/user-attachments/assets/aae7b54f-7113-48d6-afac-a39dcf0fb323)

Vậy là ta đã kết nối được với server, tiếp theo sẽ sử dụng các lệnh như là ls -la, cd để xem thư mục và chuyển thư mục

![image](https://github.com/user-attachments/assets/7528c390-3c85-4344-a82f-61370b38162a)

file key-2-of-3.txt do robot sở hữu mới có thể đọc được nên quay ngược lại file password.raw-md5 để giải mã bằng web online 
password của robot là abcdefghijklmnopqrstuvwxyz. Sau đó quay lại sử dụng su robot để đăng nhập

![image](https://github.com/user-attachments/assets/dc8f3ecb-e0bc-4650-93cc-bf99116649e5)

![image](https://github.com/user-attachments/assets/cfaa3d40-b572-4327-a551-46864ccde946)

do thường dumbshell của netcat sẽ không cho phép thực hiện lệnh sudo nên ta nâng cấp lên Text terminal để dễ dàng làm bài dùng lệnh: python -c 'import pty; pty.spawn("/bin/bash")'

![image](https://github.com/user-attachments/assets/1e414b95-0dbb-4aab-9537-d58d17bebce8)

Vậy là ta đã tìm được key2: 822c73956184f694993bede3eb39f959

![image](https://github.com/user-attachments/assets/38bb255c-e43d-44f8-bc54-d74662b6f751)

Sau khi tìm hiểu vài thư mục thì mình nghĩ nên chuyển sang vai trò root để đọc và truy cập được tất cả các file, folder. Nhưng lại không có quyền được đăng nhập. Vậy để chạy dưới quyền root thì ta sẽ sử dụng kỹ thuật SUID (Set User ID) để mạo danh root. Sử dụng lệnh: find / -perm -u=s -type f 2>/dev/null

![image](https://github.com/user-attachments/assets/ac4bc1eb-0a55-4c6f-8a9d-6f7eb9159733)

Có các file như là passwd, sudo, su nhưng chỉ làm được một việc của nó chứ không cho chạy lung tung. Đối với nmap, tìm hiểu được rằng ở phiên bản cũ thì nhà phát triển đã thêm interactive mode. Khi mà scan bằng nmap thì người ta đa số sẽ dùng root, nên khi ta là user thường kết nối vào nmap (interactive mode) thì cũng sẽ hưởng quyền của root luôn. (tham khảo https://gtfobins.org/ để tìm những command giúp leo thang đặc quyền)

![image](https://github.com/user-attachments/assets/662bea50-05ba-430f-bd02-321105c3ddbe)

Sử dụng lệnh: /usr/local/bin/nmap –interactive để mở nmap. Sử dụng !sh để nmap mở terminal root
 
Vậy là ta đã tìm được key3: 04787ddef27c3dee1ee161b21670b4e4
