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

# TÌM HIỂU VỀ VLAN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Tổng quan về VLAN](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/9.VLAN/README.md#it%E1%BB%95ng-quan-v%E1%BB%81-vlan)

# [II. Cấu hình VLAN trên switch](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/9.VLAN/README.md#iic%E1%BA%A5u-h%C3%ACnh-vlan-tr%C3%AAn-switch)
***
# ***I.	Tổng quan về VLAN***
* VLAN viết tắt của Virtual LAN hay cụ thể hơn là Virtual Local Area Network và còn được gọi là mạng LAN ảo. VLAN là 1 kỹ thuật cho phép tạo lập các mạng LAN ảo độc lập 1 cách logic trên switch, VLAN tương đương như mạng con. 
* VLAN dựa trên logic thay vì các kết nối vật lý. 
* Mỗi 1 VLAN sẽ là 1 broadcast domain và sử dụng lớp mạng khác nhau
* VLAN được sử dụng khi mạng máy tính quá lớn và có lưu lượng truy cập quá nhiều thường là các công ty lớn.
* Mạng VLAN gồm có 3 loại chính như sau:
    * Port - based VLAN: là cách cấu hình VLAN đơn giản và phổ biến. Mỗi cổng của Switch được gắn với một VLAN xác định (mặc định là VLAN 1), do vậy bất cứ thiết bị host nào gắn vào cổng đó đều thuộc một VLAN nào đó.
    * MAC address based VLAN: Cách cấu hình này ít được sử dụng do có nhiều bất tiện trong việc quản lý. Mỗi địa chỉ MAC được đánh dấu với một VLAN xác định.
    * Protocol – based VLAN: Cách cấu hình này gần giống như MAC Address based, nhưng sử dụng một địa chỉ logic hay địa chỉ IP thay thế cho địa chỉ MAC. Cách cấu hình không còn thông dụng nhờ sử dụng giao thức DHCP.
* Lợi ích của VLAN:
    * Tiết kiệm băng thông của mạng
    * Tăng khả năng bảo mật: Các VLAN không truy cập được vào nhau nếu không khai báo định tuyến nên nếu có sự cố sẽ không ảnh hưởng đến nhau.
    * Mạng có tinh linh động cao.
    * Giúp giảm thiểu miền quảng bá.
    * Giảm tải thiết bị khi muốn chia nhỏ mạng, giúp tận dụng triệt để được tài nguyên của phần cứng
    * Có tính linh động cao
* VLAN Ranges

|VLANS|Phạm vi|Sử dụng|
|---|---|---|
|0 và 4095||Không được sử dụng và chỉ làm dự phòng trong tương lai|
|1||VLAN mặc định của cisco, có thể sử dụng được và không thể xóa|
|VLAN từ 2-1001||Sử dụng cho Ethernet VLANS, có thể tùy ý sử dụng|
|VLAN từ 1002-1005||Là VLAN được tạo sẵn trên các thiết bị cisco để tương thích với các công nghệ cũ như Token ring/bus. Tuy nhiên hiện nay đã ít sử dụng và chỉ sử dụng  công nghệ Ethernet|
|VLAN từ 1006-4094|Mở rộng|chỉ sử dụng trên các switch hoạt động ở CTP mode transparent|

# ***II.	Cấu hình VLAN trên switch***
* Mặc định trên switch của cisco tất cả các port đều là VLAN 1 vậy nên khi cấu hình chia switch thành nhiều VLAN ta sẽ bắt đầu từ VLAN 2.
* Ví dụ ta muốn chia VLAN cho 2 phòng sau

![](https://user-images.githubusercontent.com/52046920/183376890-a348a905-b2c7-4f5b-83e6-e2fe2c6f476c.png)
* Trước khi chia vlan 2 máy tính có thể ping thông được với nhau.

![](https://user-images.githubusercontent.com/52046920/183376889-7d731212-cdfa-4159-8115-7addb10fe151.png)

* Các VLAN mặc định đã được bật sẵn

![](https://user-images.githubusercontent.com/52046920/183376895-d7805f78-2294-4414-be34-2a21c80438b5.png)
* Tiến hành cấu hình VLAN bằng câu lệnh
```cisco
Switch(config)#vlan 2
Switch(config-vlan)#name VLAN_Phong_Ketoan       \\\ tên của VLAN nên đặt theo phòng để có thể dễ dàng quản lý
\\\Lưu ý vlan 1 không thể đổi tên


\\\ Sau khi tạo VLAN thì tiến hành quy hoạch các cổng sẽ thuộc VLAN đó
Switch(config)#interface f0/2
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 2

\\\ Add nhiều cổng cùng 1 lúc
Switch(config)#interface f0/2 - 5 , f0/7 , f0/10
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 2

```
* Kiểm tra vlan
```cisco
Switch# show vlan brief
```

![](https://user-images.githubusercontent.com/52046920/183378104-486a753c-b5b0-4409-965c-bfd0ae45b92b.png)
* Xóa vlan
```cisco
Switch(config)#no vlan 2

\\Xóa dải vlan
Switch(config)#no vlan 2-10 ,12

```
* Khi VLAN bị xóa thì các cổng của vlan đó sẽ không quay lại vlan 1 nữa và nó sẽ đợi vlan 2 được bật lên rồi tiếp tục gia nhập vlan 2

![](https://user-images.githubusercontent.com/52046920/183376900-9ce2b2bc-5418-41ab-8683-3e96b31e242f.png)
* Nếu muốn khởi động với cấu hình trắng thì ta phải xóa file vlan.dat trong flash đi. Nếu chỉ xóa mỗi startup config thì vlan được thiết lập vẫn còn

![]()
* Thực hiện xóa thông tin vlan và khởi động với cấu hình trắng

```cisco
Switch#delete flash:vlan.dat
Switch#erase startup-config
Switch#reload
```

![](https://user-images.githubusercontent.com/52046920/183376880-9397088c-760e-4387-a041-79bf4f38cd0d.png)
* Sau khi chia VLAN xong thì 2 máy tính đã không thể ping thông đến nhau được nữa

![](https://user-images.githubusercontent.com/52046920/183376887-e9a64585-58ba-4f9d-b259-8cf44a1211ad.png)
