khi quét cổng thì sẽ ra port 21 và 22 nên mình sẽ dùng ftp để lấy thông tin và tìm được flag user

<img width="2559" height="1250" alt="image" src="https://github.com/user-attachments/assets/22fdd75d-fbe5-453d-b346-6c2449de07a6" />

<img width="2557" height="1061" alt="image" src="https://github.com/user-attachments/assets/1470b24b-9d7f-4be7-818c-e3ee09c06db1" />

trong đó nếu đọc kĩ bạn sẽ tìm được thư mục notread và tìm được 2 file 

<img width="1672" height="260" alt="image" src="https://github.com/user-attachments/assets/e917b051-b01e-4e9c-9990-3ad1a2bc55ad" />

để đọc được thông tin trong file gpg thì ta sẽ bẻ khóa file asc để tìm được passphrase bằng gpgjohn 

<img width="2557" height="1215" alt="image" src="https://github.com/user-attachments/assets/3a539789-155a-4506-a1b6-8bfed30eb89b" />

sau đó import khóa gpg vào rồi decrypt

<img width="2557" height="1002" alt="image" src="https://github.com/user-attachments/assets/c369f7e5-d99e-490e-9fec-14c753b0a73d" />
<img width="2559" height="1182" alt="image" src="https://github.com/user-attachments/assets/5407811f-69ef-4d53-8ce1-ab9ea068f493" />

vào trang hashcat thì bạn sẽ tìm được phương pháp mã hóa là 

<img width="1872" height="57" alt="image" src="https://github.com/user-attachments/assets/4d9d6085-04ee-4c46-8409-caacd85f5e9a" />

sau đó sẽ tìm được mật khẩu của user root rồi ssh lên

<img width="2559" height="267" alt="image" src="https://github.com/user-attachments/assets/1fda3beb-a8a4-4106-8258-c2cbd84ad71d" />

vậy là đã tìm được flag 

<img width="2559" height="253" alt="image" src="https://github.com/user-attachments/assets/3c9aa676-80fc-4ecc-b640-de9ffa65a488" />













