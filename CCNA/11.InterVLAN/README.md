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

# TÌM HIỂU VỀ INTERVLAN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. InterVLAN là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/11.InterVLAN/README.md#iintervlan-l%C3%A0-g%C3%AC)

## &ensp; [1. Router on a Stick trên Cisco Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/11.InterVLAN/README.md#1router-on-a-stick-tr%C3%AAn-cisco-router)

## &ensp; [2. Giải pháp SVI trên Switch Layer 3](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/11.InterVLAN/README.md#2gi%E1%BA%A3i-ph%C3%A1p-svi-tr%C3%AAn-switch-layer-3)

## &ensp; [3. Cấu hình định tuyến trên Switch Layer 3](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/11.InterVLAN/README.md#3c%E1%BA%A5u-h%C3%ACnh-%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-tr%C3%AAn-switch-layer-3)

# []()
***
# ***I.	InterVLAN là gì***
* Có thể hiểu đơn giản đó là định tuyến cho các Vlan. Là phương pháp giúp các Vlan sử dụng được dịch vụ được cung cấp bởi các Vlan khác bằng cách cung cấp một liên kết trunk duy nhất giữa Switch và Router mà có thể mạng lưu lượng truy cập của nhiều Vlan trong đó và được định tuyến bởi Router.

# ***II.	Các kỹ thuật InterVLAN routing***
## ***1.	Router on a Stick trên Cisco Router***
* Phương pháp sử dụng 1 cổng vật lý của router chia thành các interface logic, hoạt động độc lập gọi là subinterface, các cổng ảo mỗi cổng đóng vai trò là default-gateway cho các VLAN tương ứng. Cổng vật lý sẽ kết nối với switch và được thiết lập là 1 đường trunk
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/183557815-e5a3b2f4-e90b-41c6-9a19-56dc3a502b9d.png)
* Switch

|Port|Sử dụng làm|
|---|---|
|fa0/1|Trunk đến router|
|fa0/2|Vlan10|
|fa0/3|Vlan20|

* PC

|Tên PC|Vlan|IP|Default gateway|
|---|---|---|---|
|PC1|10|10.0.0.2/8|10.0.0.1|
|PC2|20|20.0.0.2/8|20.0.0.1|

* Chia nhỏ cổng giao tiếp thành các cổng ảo bằng câu lệnh
```cisco
R1(config)#interface gig0/0.10
R1(config-subif)#encapsulation dot1q 10         ///chỉ số ở đây ám chỉ Vlan 10 không liên quan đến cổng ảo chia nhỏ nhưng có thể đặt cổng giống để dễ kiểm soát. dot1q có thể thay bằng isl tùy theo nhu cầu cũng như thiết bị và phải đồng nhất router và switch

R1(config-subif)#ip address 10.0.0.1 255.0.0.0

///Tương tự cho Vlan 20
R1(config)#interface gig0/0.20
R1(config-subif)#encapsulation dot1q 20         
R1(config-subif)#ip address 20.0.0.1 255.0.0.0

/// Nếu sử dụng Vlan1 thì câu lệnh như sau do vlan 1 mặc định là native Vlan
R1(config-subif)#encapsulation dot1q native   
```

![](https://user-images.githubusercontent.com/52046920/183557811-dd72d07d-f32b-4b59-aeb3-bcd32d67c485.png)
* Router

|Cổng|IP|
|---|---|
|gig0/0.10|10.0.0.1/8|
|gig0/0.10|20.0.0.1/8|



* Bên phía switch thiết lập Vlan 10 và 20 sau đó mở đường trunk đến router

```cisco
///Thiết lập Vlan
SW1(config)#interface f0/2
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface f0/3
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 20

///Mở đường trunk đến router
SW1(config)#int fa0/1
SW1(config-if)#switchport mode trunk 

```

* Kết quả là ta có thể ping đến Vlan 20 và default gateway 10.0.0.1 và 20.0.0.1

![](https://user-images.githubusercontent.com/52046920/183557809-0598b6c6-3f9c-4e08-88a8-958aa7ae5db8.png)

* Nhược điểm: lưu lượng của các VLAN sẽ dùng chung kết nối trunking, khi đường trunk bị tắc nghẽn sẽ ảnh hưởng đến tất cả các VLAN, đồng thời độ trễ cũng tăng lên do gói tin phải rời khỏi Switch đi vào Router sau đó trở lại Switch.

## ***2.	Giải pháp SVI trên Switch Layer 3***
* Switch Layer 3 có đầy đủ chức năng của Switch Layer 2, bên cạnh đó Switch Layer 3 là những router tốc độ cao nhưng lại không có cổng kết nối WAN.
* Triển khai SVI là việc tạo ra các interface VLAN trên switch layer 3, chúng sẽ là default gateway cho các Vlan tương ứng. 1 cổng SVIs trên switch hoạt động tương đương với 1 cổng router.
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/183562840-cb43e154-1910-42c2-9678-8ef610721741.png)

|Tên PC|Vlan|IP|Default gateway|
|---|---|---|---|
|PC1|10|10.0.0.2/8|10.0.0.1|
|PC2|20|20.0.0.2/8|20.0.0.1|


* Tạo Vlan
```cisco
SW1(config)#interface gig1/0/1
SW1(config-if)#switchport mode access 
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface gig1/0/2
SW1(config-if)#switchport mode access 
SW1(config-if)#switchport access vlan 20

```
* Tạo cổng cho Vlan
```cisco
SW1(config)#interface vlan 10
SW1(config-if)#ip address 10.0.0.1 255.0.0.0
SW1(config-if)#no shut
SW1(config-if)#exit

SW1(config)#interface vlan 20
SW1(config-if)#ip address 20.0.0.1 255.0.0.0
SW1(config-if)#no shut
```
![](https://user-images.githubusercontent.com/52046920/183563368-1f07765b-fa67-4ffe-ac9a-0e36762fdbc8.png)

* Sau khi thiết lập Switch có các thông số như sau
    * Các cổng và Vlan

    |Port|Vlan|
    |---|---|
    |gig1/0/1|Vlan10||
    |gig1/0/2|Vlan20||
    * Cổng ảo được tạo để làm default gateway

    |Port|ip|
    |---|---|
    |vlan10|10.0.0.1/8|
    |vlan20|20.0.0.1/8|

* Bật định tuyến trên Switch layer 3
```
SW1(config)#ip routing 
```

* Kiểm tra bảng định tuyến

![](https://user-images.githubusercontent.com/52046920/183563078-6dff8a04-91f4-4fb4-bf01-0c5306baa9fc.png)

* 2 Vlan đã có thể ping thông được đến nhau

![](https://user-images.githubusercontent.com/52046920/183563077-4285361f-402e-4c5b-be5e-2a5d7c82a9ee.png)

## ***3.	Cấu hình định tuyến trên Switch Layer 3***
* Tương tự với cấu hình định tuyến trên router tuy nhiên cổng của switch layer 3 có thể linh hoạt giữa cổng interface Vlan hoặc cổng giao tiếp vật lý.

* Muốn đặt ip cho 1 cổng giao tiếp trên switch ta thực hiện câu lệnh
```cisco
SW1(config)#interface gig1/0/3
SW1(config-if)#no switchport 
SW1(config-if)#ip address 30.0.0.2 255.0.0.0
```

```cisco
R1(config)#ip route 10.0.0.0 255.0.0.0 30.0.0.2
R1(config)#ip route 20.0.0.0 255.0.0.0 30.0.0.2
R1(config)#ip route 0.0.0.0 0.0.0.0 40.0.0.2
```

* Khi tắt chức năng định tuyến của switch ta phải khai báo thêm 1 thông số là ip default gateway để nó có thể trỏ đến router nơi đã được định tuyến sẵn để đi đến đích. Còn nếu có bảng định tuyến nó sẽ tuân theo bảng định tuyến để có thể đi đến đích

```cisco
SW1(config)#ip default-gateway
```

* Giả sử cho mô hình

![](https://user-images.githubusercontent.com/52046920/183582506-1c4133da-2a9b-4f42-a54f-2140b3b9c60b.png)

* ***PC***

|Tên PC|Vlan|IP|Default gateway|
|---|---|---|---|
|PC1|10|10.0.0.2/8|10.0.0.1|
|PC2|20|20.0.0.2/8|20.0.0.1|
|PC3||50.0.0.2/8|50.0.0.1|

* Sau khi thiết lập ***Switch*** có các thông số như sau
    |Port|Vlan|IP|
    |---|---|---|
    |gig1/0/1|Vlan10||
    |gig1/0/2|Vlan20||
    |gig1/0/3||30.0.0.2|
    |vlan10||10.0.0.1/8|
    |vlan20||20.0.0.1/8|

* ***Router***

|Tên Router|interface|ip|
|---|---|---|
|Router1|gig0/0|30.0.0.1|
||gig0/1|40.0.0.1|
|Router1|gig0/0|40.0.0.2|
||gig0/1|50.0.0.1|


* Tiến hành định tuyến như sau
* Tại Router 1
```cisco

///Cấu hình định tuyến tĩnh cho dữ liệu đi vào các Vlan
R1(config)#ip route 10.0.0.0 255.0.0.0 30.0.0.2
R1(config)#ip route 20.0.0.0 255.0.0.0 30.0.0.2

///Giả sử cấu hình ra ngoài mạng
R1(config)#ip route 0.0.0.0 0.0.0.0 40.0.0.2
```
* Tại Router 2
```cisco
///Giả sử cấu hình ra ngoài mạng
R1(config)#ip route 0.0.0.0 0.0.0.0 40.0.0.1
```

* Tại Switch layer 3
```cisco
SW1(config)#interface gig1/0/3
SW1(config-if)#no switchport 
SW1(config-if)#ip address 30.0.0.2 255.0.0.0
/// Định tuyến cho các gói tin đi ra
SW1(config)#ip route 0.0.0.0 0.0.0.0 30.0.0.1

```

* PC3 và PC1 đã thông với nhau

![](https://user-images.githubusercontent.com/52046920/183581848-35f010a5-2ca5-43d9-8ff1-ae6fc7aae9ac.png)
<!--
## ***3.	Cấu hình DHCP Server trên Switch Layer 3***
