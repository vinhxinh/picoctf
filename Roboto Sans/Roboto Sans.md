Đề bài có cho mình một trang web, kiểm tra các thông tin cơ bản bằng F12 không thấy có thông tin gì dùng được, theo như tền bài mình sẽ kiểm tra đường dẫn trong file `/robots.txt`

File `robots.txt` có một vài thông tin hữu ích như sau:

```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/

```

Có 3 đoạn thông tin được mã hóa rất kì lạ, trong đó dòng số 2 là có dạng base64 nên ta có thể mang ra decode thử, tuy nhiên không tồn tại, vì vậy mình sẽ decode base64 trên 3 dòng tách biệt bằng công cụ [base64decode](https://www.base64decode.org/) và ta đã có được thêm một vài thông tin.

```

flag1.txtjs/myfi
js/myfile.txt
,z谖/u%z8

```

dòng 2 có dạng base64 khi decode từng dòng chung với 2 đoạn mã trên đã tồn tại, cho mình một đường dẫn `js/myfile.txt`. Truy cập đường dẫn tới file đó và mình đã có flag: `picoCTF{Who_D03sN7_L1k5_90B0T5_22ce1f22}`