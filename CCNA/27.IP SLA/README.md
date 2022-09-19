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

# TÌM HIỂU VỀ IP SLA
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Kỹ thuật IP SLA là gì]()

# [II. Cấu hình IP SLA]()
***
# ***I.	Kỹ thuật IP SLA là gì***
* IP SLA là IP Service level Agreements 

![](https://user-images.githubusercontent.com/52046920/190937283-2abe68ef-ff22-4129-8e87-d99c7244f4b7.png)
* Được kết hợp với static route. Nó định nghĩa cho router sẽ định kỳ gửi ping đến cho router có route trên bảng định tuyến.  


![](https://user-images.githubusercontent.com/52046920/190937284-06ef9efb-9972-4911-861e-e93a5511a960.png)
* Khi có sự cố và router không nhận được bản tin phản hồi sau 1 khoảng thời gian được định nghĩa thì nó sẽ xóa route đó ra khỏi routing table. Nếu đường đi đó được khôi phục thì route đó sẽ lại được khôi phục lại trong route table
* Do vẫn có 1 số Router không được hỗ trợ các định tuyến động vậy nên định tuyến tĩnh vẫn phải được sử dụng.
* Do định tuyến tĩnh không thể tự mình phát hiện được sự cố của các route nên IP SLA có thể giúp ích cho định tuyến tĩnh rất nhiều trong việc xác định sự cố và tránh mất gói tin khi có sự cố

# ***II.	Cấu hình IP SLA***
* Bước 1 ta phải định nghĩa IP SLA bằng câu lệnh 
```cisco
R1(config)#ip sla 2
R1(config-ip-sla)#icmp-echo [ip ping đến định kỳ]
R1(config-ip-sla-echo)#frequency [thời gian cách nhau của mỗi lần thực hiện ping]
R1(config-ip-sla-echo)#timeout [Thời gian chờ giá trị milliseconds]
R1(config-ip-sla-echo)#threshold [số lần chờ cho đến khi đóng route]


/// ví dụ ping định kỳ 3s 1 lần đến ip 10.0.0.1 và sau 2000 milliseconds không có reply thì nhận định route có vấn đề và sau 2 lần thì route sẽ bị xóa
R1(config)#ip sla 2
R1(config-ip-sla)#icmp-echo 10.0.0.1
R1(config-ip-sla-echo)#frequency 3
R1(config-ip-sla-echo)#timeout 2000
R1(config-ip-sla-echo)#threshold 2


///Khởi động
ip sla schedule 2 life forever start-time now

///nhúng dịch vụ vào track
track 1 ipsla 2 reachability

/// gán track vào route
ip route 0.0.0.0 0.0.0.0 10.0.0.1 track 1
```

* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/190939039-39a58f54-3cd2-4468-8208-2f2382bb6564.png)
* Tại R1
```cisco
R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.2
R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.3
R1(config)#ip route 123.0.0.1 255.255.255.255 10.0.0.2
R1(config)#ip route 123.0.0.2 255.255.255.255 10.0.0.3

```
* Bảng định tuyến của R1

![](https://user-images.githubusercontent.com/52046920/190939358-921e7556-08fa-4546-84b2-a8529e99b1aa.png)
* Cấu hình IP SLA cho R1 khi R2 hoặc R3 có lỗi xảy ra mà không đi được ra ngoài mạng thì sẽ xóa route đó đi bằng IP SLA như sau
```cisco
//Thiết lập IP SLA kiểm tra R2
R1(config)#ip sla 1
R1(config-ip-sla)#icmp-echo 123.0.0.1
R1(config-ip-sla-echo)#frequency 5
R1(config-ip-sla-echo)#threshold 5
R1(config-ip-sla-echo)#timeout 2000
R1(config-ip-sla-echo)#exit

///Thiết lập IP SLA kiểm tra R3
R1(config)#ip sla 2
R1(config-ip-sla)#icmp-echo 123.0.0.2
R1(config-ip-sla-echo)#frequency 5
R1(config-ip-sla-echo)#threshold 5
R1(config-ip-sla-echo)#timeout 2000

///Khởi động IP SLA 1 và IP SLA 2
R1(config)#ip sla schedule 1 life forever start-time now
R1(config)#ip sla schedule 2 life forever start-time now

///Gán IP SLA vào track
R1(config)#track 1 ip sla 1 reachability

R1(config)#track 2 ip sla 2 reachability


///Định tuyến lại và gán track vào route
R1(config)#no ip route 0.0.0.0 0.0.0.0 10.0.0.2
R1(config)#no ip route 0.0.0.0 0.0.0.0 10.0.0.3
R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.2 track 1
R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.3 track 2
```

![](https://user-images.githubusercontent.com/52046920/190940768-bdce3587-c912-49cd-bfc8-7606a90dd215.png)
* Tắt Router R2 đi và kiểm tra IP SLA có hoạt động không

![](https://user-images.githubusercontent.com/52046920/190940770-0007ec0b-b0b2-44eb-b5e6-fc80cab5697f.png)

![](https://user-images.githubusercontent.com/52046920/190940766-1d014785-88c7-4e60-8bae-ef503a30a512.png)
* Route đã bị xóa khỏi Routing Table
* Khi khởi động lại R2

![](https://user-images.githubusercontent.com/52046920/190940772-e096f394-a502-487c-9e58-f8792700c63c.png)

* Route đã được khôi phục lại