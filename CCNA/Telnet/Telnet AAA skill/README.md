<!--
# h1
## h2
### h3
#### h4
##### h5
###### h6

*in nghiêng*

**bôi đậm**

***vừa in nghiêng vừa bôi đậm***

`inlide code`

```php

echo ("highlight code");

```

[Link test](https://viblo.asia/helps/cach-su-dung-markdown-bxjvZYnwkJZ)

![markdown](https://images.viblo.asia/518eea86-f0bd-45c9-bf38-d5cb119e947d.png)

* mục 3
* mục 2
* mục 1

1. item 1
2. item 2
3. item 3

***
horizonal rules

> text

{@youtube: https://www.youtube.com/watch?v=HndN6P9ke6U}
* Cài đặt nginx bằng câu lệnh sau
```php
dnf -y install nginx
```
*	Cấu hình nginx như sau
```php
vi /etc/nginx/nginx.conf

 Server{
     ...
     server_name www.srv.world;
     ...
 }
 
-->

# TÌM HIỂU VỀ Kỹ thuật AAA hỗ trợ xác thực và phân quyền Telnet trên thiết bị 
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	Kỹ thuật AA hỗ trợ xác thực và***
* AAA là Authentication(xác thực) Authorization(phân quyền) Accounting(kiểm toán). Nó hỗ trợ 3 cái dịch vụ như tên gọi của nó
    * Authentication(Xác thực): chỉ có ai biêt username và password mới được quyền truy cập telnet đến thiết bị.
    * Authorization(phân quyền): các người dùng sẽ được phân quyền và tùy vào quyền của người dùng thì sẽ bị giới hạn các câu lệnh cấu hình.
    * Accounting(kiểm toán): ghi lại nhật ký hoạt động của hệ thống mạng như: User nào đã telnet vào hệ thống, từ lúc nào và trong thời gian bao nhiêu, đã thực hiện những câu lệnh gì

# ***II.	Xác thực Authentication***
* 
```cisco
R1(config)#aaa authentication login localAAA local
R1(config)#username admin password 123456
R1(config)#line vty 0 4
R1(config-line)#login authentication localAAA
```

```cisco
R1(config)#enable secret level 15 tai123
```