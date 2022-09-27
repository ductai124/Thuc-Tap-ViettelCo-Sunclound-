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

# TÌM HIỂU VỀ CÁC THÀNH PHẦN CỦA MÁY CHỦ
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Máy chủ là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#im%C3%A1y-ch%E1%BB%A7-l%C3%A0-g%C3%AC)
# [II. Các thành phần chính của máy chủ](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#iic%C3%A1c-th%C3%A0nh-ph%E1%BA%A7n-ch%C3%ADnh-c%E1%BB%A7a-m%C3%A1y-ch%E1%BB%A7)
## &ensp; [1. Mainboard](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#1-mainboard)
## &ensp; [2. CPU](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#2-cpu)
## &ensp; [3. RAM](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#3-ram)
## &ensp; [4. Storage](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#4-storage)
## &ensp; [5. Card Raid](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#5-card-raid)
## &ensp; [6. PSU](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#6-psu)
## &ensp; [7. Chassis](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#7-chassis)
## &ensp; [8. I/O(Input/Output)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#8-ioinputoutput)
## &ensp; [9. OS](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#9-os)
## &ensp; [10. Applications](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/2.Server%20components/README.md#10-applications)
***
# ***I.	Máy chủ là gì***
* Máy chủ - Server là một hệ thống máy tính được thiết kế đáp ứng được thời gian hoạt động lâu dài và có khả năng chịu tải cao trước các yêu cầu truy xuất, cập nhật dữ liệu liên tục từ các máy tính khác nhau trên mạng.
* Máy chủ có:
    * Hardware(HW): Thiết bị phần cứng đặc trưng
    * Software(SW): Phần mềm giúp người dùng tương tác với Server
    * Firmware(FW): phần mềm cung cấp kiểm soát mức thấp cho phần cứng cụ thể của thiết bị
* Gần như tương tự 1 con máy cá nhân bình thường
# ***II.	Các thành phần chính của máy chủ***
* Máy chủ bao gồm các thành phần chính sau đây:
    * Mainboard - bo mạch chủ
    * CPU
    * RAM
    * Storage - Thành phần lưu trữ HDD hoặc SSD
    * Card Raid
    * PSU
    * Chassis server
    * I/O(Input/Output)
    * OS
    * Application
## ***1. Mainboard***
* Mainboard - Bo mạch chủ là mạch điện chính, trung tâm của 1 hệ. Nhiệm vụ kết nối và truyền dẫn giữa các thiết bị phần cứng trong máy. 
* Nó bao gồm các khe socket, các bộ xử lý, các cổng kết nối, các khe cắm Ram và ổ cứng

![](https://user-images.githubusercontent.com/52046920/192246784-a9907c67-7a42-4c21-9699-8e9e9dd413a2.png)

## ***2. CPU***
* CPU - Central Processing Unit. Bộ xử lý trung tâm gần như đóng vai trò là bộ não của cả Server, nó có vai trò là trung tâm điều hành hệ thống. 

![](https://user-images.githubusercontent.com/52046920/192246788-abe64b81-9516-4ab4-8ee5-ec5be4512999.png)
## ***3. RAM***
* RAM - Random Access Memory là bộ nhớ truy cập ngẫu nhiên.
* Là linh kiện quyết định khả năng xử lý của máy chủ tại 1 thời điểm chạy được đồng thời bao nhiều chương trình, lượng dữ liệu có thể xử lý ngay tức thời. 

![](https://user-images.githubusercontent.com/52046920/192246757-8ea29773-0a56-43b4-b39d-621a289781c4.jpg)

## ***4. Storage***

![](https://user-images.githubusercontent.com/52046920/192246767-47131313-5366-44b4-bfbe-aefbd4bf313f.jpg)
* Nơi lưu trữ dữ liệu, OS của Server thường là các ổ cứng HDD và SSD.
* Có chức năng lưu trữ các dữ liệu dưới hình thức bộ nhớ ngoài, OS, các phần mềm và dữ liệu người dùng

## ***5. Card Raid***

![](https://user-images.githubusercontent.com/52046920/192246772-ed036ed6-1f43-4608-9d19-74db5eca60e4.jpg)
* Giúp kết hợp các ổ cứng thành 1 thể thống nhất với những cơ chế sao lưu, chống lỗi giúp dữ liệu luôn được an toàn khi có sự cố xảy ra.
## ***6. PSU***

![](https://user-images.githubusercontent.com/52046920/192246775-ae6a0fab-8e2f-47c6-9d6f-65ddf6f4fa9b.jpg)
* PSU - Power Supply Unit, là bộ cấp nguồn máy chủ. Có nhiệm vụ cấp nguồn đảm bảo nguoonfd diện đủ công suất cho các thành phần bên trong máy chủ hoạt động. 
* Các Server hiện nay thường sử dụng PSU có công suất cao có khả năng thay thế và sẽ có từ 2 nguồn trở lên để dự phòng, phòng trường hợp sự cố với PSU xảy ra
## ***7. Chassis***
* Dùng để bảo vệ các thiết bị phần cứng bên trong Server. Tương tư 1 vỏ case của PC cá nhân.
* Chassis có dạng nằm ngang là Rack Mount, dạng đứng là Tower Server, Blade Server được thiết kế cho việc triển khai Server dày đặc. Có nhiều loại Chassis khác nhau và chúng có giá trị là U
* U là đơn vị các nhà sản xuất quy ước dùng để đo chiều cao thiết bị, 1U là đơn vị nhỏ nhất trong Rack Mount. 1U = 1,75 inch = 4.45 cm được ghi theo thứ tự W(Width), H(Height),D(Depth). Trong các loại Rack Mount chỉ phân biết chiều sâu (Depth)
## ***8. I/O(Input/Output)***

![](https://user-images.githubusercontent.com/52046920/192246779-1565b4d0-9165-4078-8cb8-d427df6f6ae6.jpg)
* Các thiết bị xuất dữ liệu ra ngoài Server hoặc đưa dữ liệu vào Server:
    * USB
    * Máy in
    * Modems
    * Camera
    * DVD
    * Ổ cứng
## ***9. OS***
* OS - Operating System hay hệ điều hành. Tương tự với hệ điều hành của PC cá nhân

![](https://user-images.githubusercontent.com/52046920/192246782-cf9da971-d63c-4d9b-9d53-8f20018169a4.jpg)

![](https://user-images.githubusercontent.com/52046920/192246795-298d7fc7-2158-4abe-b107-1859b2d50e90.png)

## ***10. Applications***
* Các phần mềm, ứng dụng được cài đặt lên với 1 nhiệm vụ nào đó
