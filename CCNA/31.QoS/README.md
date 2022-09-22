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

# TÌM HIỂU VỀ QoS
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. QoS là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/31.QoS/README.md#iqos-l%C3%A0-g%C3%AC)
# [II. Traffic Shaping và Traffic Policing](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/31.QoS/README.md#iitraffic-shaping-v%C3%A0-traffic-policing)
# [III. Cấu hình Traffic Shaping và Traffic Policing](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/31.QoS/README.md#iiic%E1%BA%A5u-h%C3%ACnh-traffic-shaping-v%C3%A0-traffic-policing)
***
# ***I.	QoS là gì***
* QoS là viết tắt của Quality of Service. Đây là 1 phương thức điều khiển mức độ ưu tiên traffic của hệ thống mạng. Đơn giản là nó tryền tín hiệu đi với thời gian trễ tối thiểu và cung cấp lưu lượng băng thông cho những ứng dụng truyền thông đa phương tiện
* QoS hoạt động trên tất cả các tầng mạng khác nhau của hệ thống mạng. Đối với mỗi tầng mạng thì nó thực hiện 1 chức năng khác nhau.
* Nó chỉ hoạt động khi có hiện tượng nghẽn cổ chai. 
# ***II.	Traffic Shaping và Traffic Policing***
* Traffic Shaping(TS) và Traffic Policing(TP) là 1 phần quan trọng của QoS. Chúng dùng để đo tốc độ đường truyền hoặc nhận dữ liệu. 
* TS là công cụ điều hòa lưu lượng, giúp gói tin được gửi theo đúng tốc độ đã cấu hình và không vượt ra khỏi tốc độ đã được định nghĩa. Để đảm bảo tốc độ được định nghĩa TS sẽ làm giảm tốc độ của các gói tin bằng cách đưa chúng vào hàng đợi điều hòa sau đó gửi gói tin đi theo đúng tốc độ định nghĩa.
* TP là công cụ không chế lưu lượng. Nó sẽ đo tốc độ của gói tinvaof và ra 1 cổng của Router. Nếu tốc độ vượt quá tốc độ đã được định nghĩa  thì Router sẽ loại bỏ đủ số lượng gói tin sao cho tốc độ không bị vượt qua hoặc Router cũng có thể đánh dấu các gói tin sao cho các gói tin này có thể loại bỏ về sau. Ví dụ tốc độ được định nghĩa là X thì nếu tốc độ được gửi đi là 10X thì TP hủy các gói tin đó

![](https://user-images.githubusercontent.com/52046920/191641783-86091043-3949-4eb1-9e5d-40947fc80563.png)

# ***III.	Cấu hình Traffic Shaping và Traffic Policing***

![](https://user-images.githubusercontent.com/52046920/191644357-30c60219-99e6-4b63-95c7-f74b26d96ebc.png)
* Cấu hình Policing bằng câu lệnh
```cisco
///Tạo accesslist các IP cần bị giới hạn băng thông
Router(config)#access-list 100 permit ip any any 

Router(config)#class-map match-any QT
Router(config-cmap)#match access-group 100
Router(config-cmap)#exit

Router(config)#policy-map LBW
Router(config-pmap)#class QT
Router(config-pmap-c)#police 2048000 conform-action transmit exceed-action drop
/// lưu lượng tính theo bit/s


///Chọn interface áp dụng Policing
Router(config)#interface e0/0
Router(config-if)#service-policy output LBW
```

* Cấu hình Shaping bằng câu lệnh
```cisco
///Tạo accesslist các IP cần bị giới hạn băng thông
Router(config)#access-list 100 permit ip any any 

Router(config)#class-map match-any QT
Router(config-cmap)#match access-group 100
Router(config-cmap)#exit

Router(config)#policy-map LBW
Router(config-pmap)#class QT
Router(config-pmap-c)#shape average 1048000

///Chọn interface áp dụng Shaping
Router(config)#interface e0/0
Router(config-if)#service-policy output LBW

```
* Các Swich hỗ trợ 2 phương thức Shaping và Policing cũng có thể được cấu hình như trên
* Các thiết bị VPC1 và VPC2 sẽ bị giới hạn băng thông ở 2Mb/s
