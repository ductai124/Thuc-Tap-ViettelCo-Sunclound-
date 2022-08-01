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

# TÌM HIỂU VỀ LLDP
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
# ***I.	LLDP là gì***
* LLDP(Link Layer Discovery Protocol) là giao thức phát hiện thiết bị láng giềng trên các thiết bị mạng. Khác với CDP chỉ chạy trên các dòng sản phẩm của cisco và được mặc định bật thì LLDP lại có thể chạy trên được nhiều các loại thiết bị của các hãng sản xuất khác nhau và muốn sử dụng phải kích hoạt nó lên.

![](https://user-images.githubusercontent.com/52046920/182113706-167e0a6b-1493-4385-a866-8ea86eae30d1.png)
* Kích hoạt LLDP bằng câu lệnh
```cisco
\\\Bật giao thức LLDP trên tất cả các cổng
Switch(config)# lldp run

\\\Bật giao thức LLDP trên từng cổng
Switch(config)# interface FastEthernet 0/2
Switch(config-if)# lldp enable          
```
* Để kiểm tra các nút láng giếng ta sử dụng câu lệnh
```cisco
Switch# show lldp neighbors
```

![](https://user-images.githubusercontent.com/52046920/182120925-ce7c75a2-6ed0-45eb-9d90-364aaef2156d.png)
* Toàn bộ các thiết bị trong mạng đều phải bật giao thức LLDP nếu muốn có thể nhận được các bản tin LLDP của nhau. Nếu không bật chúng sẽ không nhận được bản tin LLDP của nhau
![](https://user-images.githubusercontent.com/52046920/182120931-1a2b14aa-d615-42f5-a96f-4a3b87994fe2.png) 