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

# TÌM HIỂU VỀ CDP
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
# ***I.	CDP là gì***
* CDP(Cisco Discovery Protocol)là một giao thức phát hiện các thiết bị láng giềng có trên Cisco router.

![](https://user-images.githubusercontent.com/52046920/182113706-167e0a6b-1493-4385-a866-8ea86eae30d1.png)
* Trong 1 hệ thống mạng nếu mà người quan trị quên vẽ lại sơ đồ mạng thì có thể dựa vào giao thức này để phát hiện các của 1 thiết bị cisco đang kết nối với thiết bị nào và vẽ lại hệ thống mạng.
```cisco
Switch>show cdp neighbors
```

![](https://user-images.githubusercontent.com/52046920/182113562-d6df8c7b-de94-4ad0-a16a-eba994f970ce.png)
* Sử dụng câu lệnh sau còn có thể biết thêm được IP của thiết bị được kết nối với cổng của thiết bị cisco người đùng đang đứng tại đó kiểm tra. Và ta còn có thể biết được thêm thông tin về tên của hệ điều hành cảu thiết bị kết nối kia
```cisco
Switch>show cdp neighbors detail
```

![](https://user-images.githubusercontent.com/52046920/182113572-a983c1cb-07b5-4081-baba-ad4477f3b4f4.png)
* Từ thông tin trên ta xác định được thiết bị kết nối với cổng fas0/1 của switch là 1 router có tên là cisco ISR4300 và sử dụng cổng gig 0/0/0 để kết nối với switch và cổng này có IP là 192.168.1.1. Hệ điều hành mà router này đang sử dụng là Cisco IOS XE Software, Version 03.13.04.S - Extended Support Release-Cisco IOS Software, ISR Software (X86_64_LINUX_IOSD-UNIVERSALK9-M), Version 15.5(3)S5, RELEASE SOFTWARE (fc2)
* Các thiết bị có thể nhận biết được nhau do giao thức CDP tự động kích hoạt trên các dòng sản phẩm nhà Cisco vật nên nó sẽ không có tác dụng với các dòng sản phẩm của công ty khác sản xuất. Cứ định kỳ cứ 60 giây 1 lần các thiết bị cisco sẽ gửi bản tin CDP cho nhau. CDP sẽ chứa các thông tin liên quan đến thiết bị gửi nó. Khi các thiết bị cisco nhận được bản tin CDP từ các thiết bị cisco láng giềng nó sẽ lưu trữ nó trong vòng 180 giây(holdtme).
* Tại các máy tính ta có thể bắt được các gói tin CDP và từ đó có thể nắm được sơ đồ mạng của 1 hệ thống. Điều này dẫn đến các nguy cơ về bảo mật như lộ sơ đồ mạng dẫn đến việc tăng khả năng bị tấn công. Lúc này ta sẽ tắt các giao thức CDP đến các cổng bằng câu lệnh như sau.
```cisco
Switch(config)# interface fastEthernet 0/2
Switch(config-if)# no cdp enable
```
* Nếu muốn vô hiệu cdp hóa 1 dải các cổng thì thực hiện câu lệnh sau
```cisco
Switch(config)# interface range fastEthernet 0/2-3, fastEthernet 0/5            \\\Tắt cdp từ port 0/2 đến 0/3 và port 0/5
Switch(config-if)# no cdp enable
```
* Nếu muốn tắt giao thức CDP trên toàn bộ thiết bị thì thực hiện câu lệnh. Lúc đó nó sẽ không xử lý các bản tin CDP từ các thiết bị khác cũng như gửi các bản tin CDP cho các thiết bị xung quanh
```cisco
Switch(config)# no cdp run
```