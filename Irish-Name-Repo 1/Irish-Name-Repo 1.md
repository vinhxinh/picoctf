# Irish-Name-Repo 1
--- 

Đề bài cho ta một đường dẫn đến một trang web khá cơ bản. Như thường lệ mình vẫn sẽ vào `Inspect` để kiểm tra các đường dẫn file cơ bản xem có gặp phải file ẩn không và `Cookies`. 

Trang web có 3 danh mục cơ bản:
- Menu
- About
- Admin Login

Kiểm tra qua Menu thì không có gì hữu ích cả.

TIếp theo mình kiểm tra đến About. Ở đây có đoạn hội thoại khá thú vị về client và admin web. Thông tin ta có thể dùng được ở đây là web sử dụng SQL là database.

Điều cuối cùng ta có thể khai thác đó là phần `Admin Login` page. Tài khoản thì chúng ta không chắc có phải là admin hay không. Nhưng mật khẩu thì ta có thể sử dụng thể SQL injection cơ bản để bypass. Bởi vì khi check tài khoản mật khẩu được nhập vào, SQL database sẽ check theo cú pháp sau: 

```sql

SELECT username, password FROM users WHERE username = '$username' AND password = '$password';

``` 

Ta sẽ hướng đến cách inject vào password bằng cách chọn username = `admin` và password = `' OR 1=1 --`, khi đó lệnh kiểm tra của SQL database có dạng sau:

```sql 

SELECT username, password FROM users WHERE username = '$username' AND password = '' OR 1=1 --;

```

Khi đó dòng kiểm tra password sẽ bị để trống và nó chỉ kiểm tra phần logic 1=1 luôn luôn đúng sau nó, vậy ta đã có thể thực hiện `SQL injection`. Flag sẽ là: `picoCTF{s0m3_SQL_fb3fe2ad}`.Ngoài ra ta còn có thể thực hiện ngay từ phần username bằng username = admin` -- để truy cập k cần qua mật khẩu.
