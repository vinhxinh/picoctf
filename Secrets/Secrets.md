Đề bài có cho mình một trang web nhìn không có thông tin gì hữu ích, sử dụng `inspect` để xem qua về các file của trang web.

Ở đây ta tìm được 2 file ban đầu đó là `/secret` và `/vendor`. Vì biết chắc chắn file `vendor` không có gì nên mình sẽ kiểm tra file `/secret`. 

Trong file `secret` có một file `index` chứa một GIF không rõ thông tin và một dòng thông báo: 

> Finally. You almost found me. you are doing well

Kiểm tra `inspect` một lần nữa có thông tin trong file `secret` có thêm một file `/hidden`. Tiếp tục truy cập mình sẽ đến một trang thông tin đăng nhập như sau.

![](https://github.com/vinhxinh/picoctf/blob/main/Secrets/pic1.png?raw=true)

Thử đăng nhập linh tinh và sử dụng một vài tính năng của trang web đều không được. Tiếp tục phải sử dụng `inspect` để tìm thêm thông tin về các file khác tồn tại. Ở file `hidden` này ta còn tìm thấy trong nó còn 1 file `superhidden` nữa. Truy caaph vào ta thấy một dòng thông báo:

> Finally. You found me. But can you see me

Chắc chắn là flag sẽ được giấu trong mấy file html hoặc css, php nên ta `f12` để tìm và mình đã có flag: `picoCTF{succ3ss_@h3n1c@10n_51b260fe}`.
