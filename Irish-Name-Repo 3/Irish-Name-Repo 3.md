# Irish-Name-Repo 3 

---

Bài này khác so với 2 bài trước, khi ta thử inject bằng cả 2 cách ban đầu đều không cho ra kết quả gì mà trả về giá trị HTTP error 500. Giờ chúng ta chỉ có một ô để điền mật khẩu. Ở đây mình thử vào `inspect` như thông thường kiểm tra. Ta có thấy một vài điểm đặc biệt như sau:

![](pic1)

Ở đây không chỉ tồn tại 1 input password như thông thường mà nó còn một input được ẩn đi đó chính là `debug` với giá trị ban đầu được gán là `0`. Việc tiếp theo mình có thể nghĩ tới đó là vẫn tiếp tục inject bằng câu query thông thường `' or 1=1 --` và chuyển đổi giá trị của `debug` sang '1`.

![](pic2)

Ở đây trang web có trả về cho mình đoạn `password` sau khi được truyền giá trị vào và cấu trúc của nó. Có một điểm lưu ý ở cấu trúc là khi truyền vào mình có truyền giá trị là `or` mà sau khi bị filter trở thành `be`. Mình thử thay `password=abcdefgh` để xem có gì xảy ra không thì nó bị chuyển thành chuỗi `nopqrstu`. Vậy mình có thể kết luận đây là mật mã Ceasar. Nó đã bị thay thế bằng các kí tự sau nó. Cuối cùng mình vẫn sử dụng cú pháp inject như ban đầu nhưng thay `or` thành `be` và kết quả là: `' be 1=1 --`.

![](pic3)

Cuối cùng flag là: `picoCTF{3v3n_m0r3_SQL_4424e7af}`.
