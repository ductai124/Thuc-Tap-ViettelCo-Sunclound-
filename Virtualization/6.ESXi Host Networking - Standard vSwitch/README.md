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

# TÌM HIỂU VỀ ESXi HOST NETWORKING - STANDARD vSWITCH
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Khái niệm ESXi Networking]()
# [II. Kiến trúc vSphere Standard Switch]()
## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	Khái niệm ESXi Networking***
* Switch vật lý là 1 thiết bị phần cứng sử dụng để kết nối các thiết bị khác và cho phép chúng giao tiếp với nhau qua mạng.
* Switch vật lý:
    * Quản lý traffic(lưu lượng) giữa các máy  trên mạng vật lý
    * Có nhiều cổng có thể kết nối được nhiều thiết bị với nhau
    * Mỗi cổng có thể cấu hình tùy theo nhu cầu sử dụng
    * Vậy nên Switch là cốt lõi trong mạng vật lý.
* Mạng vật lý: Mạng của máy vật lý giúp kết nối và gửi dữ liệu cho các máy kết nối mạng với nhau. VMWare ESXi chạy trên 1 máy vật lý.
* Virtual Network: 
    * Một mạng các VMs chạy trên một máy vật lý được kết nối logic với nhau để chúng có thể gửi dữ liệu đến và nhận dữ liệu từ nhau.
    * Các VMs có thể được kết nối với mạng ảo mà chúng ta tạo ra khi chúng ta thêm 1 mạng
* vShpere Standard Switch(vSS) or vSwitch:
    * Hoạt động tương tự Switch vật lý
    * vSwitch tạo liên kết giữa NICs và các vNICs
    * vSwitches cung cấp kết nối giữa VMs trên cùng ` Host hoặc khác Host với nhau
    * vSwitch tuy hoạt động giống Switch vật lý tuy nhiên nó vẫn không có 1 số lựa chọn, chức năng nâng cao như Switch vật lý
    * vSwitch có khả năng tạo ra các VLAN, vSwitch không thể kết nối trực tiếp đến các vSwitch khác

    ![]()
# ***II.	Kiến trúc vSphere Standard Switch***
* Có thể tạo ra các thiết bị mạng ảo được gọi là vSphere Standard Switch. Standard Switch cung cấp kết nối mạng cho Host và các VM.

![](https://user-images.githubusercontent.com/52046920/196326534-f552ad83-22a1-44b5-89e6-ec7c9c7851ca.png)
* Để cung cấp kết nối mạng cho Server và các VM cần kết nối các NIC(Network Interface Card-Card mạng) vật lý của Server với các cổng Uplink(Uplink port là port kết nối từ LAN tới WAN) trên Standard Switch(Switch tiêu chuẩn). Các VMs có vNIC kết nối với các Group Port(nhóm cổng) trên vSphere Standard Switch. Mỗi Group Port có thể sử dụng 1 hoặc nhiều NIC vật lý để xử lý. Nếu 1 Group Port không có NIC vật lý kết nối đến thì chỉ có thể giao tiếp được bên trong nội bộ không giao tiếp được bên ngoài mạng


![]()
* VM Gourp Port:
    * Để quản lý mạng của các VMs

* VM Kernel Port Group:
    * Cung cấp các kết nối IP storage, vSphere vMotion, Fault Tolerance (FT), VSAN, Cấp phép, v.v. (Đề cập ở phần vCenter)
    * Để quản lý mạng ESXi

* Host Networking Maximums

|ESXi Networking|Configuration Maximums|
|-|-|
|Các cổng tạo vSwitch với mỗi Standard switch|4088|
|Tổng số cổng Switch Mạng ảo trên mỗi host /host ESXi|4096|
|Tổng Nhóm cổng trên mỗi vSphere standard switch (vSS)|512|
|Tổng NICs vật lý 10 Gbps /20 Gbps /25 Gbps trên mỗi host|16|
