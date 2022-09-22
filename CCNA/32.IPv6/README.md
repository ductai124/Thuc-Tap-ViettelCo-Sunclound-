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

# TÌM HIỂU VỀ IPv6
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. IPv6 là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#iipv6-l%C3%A0-g%C3%AC)
# [II. Địa chỉ IPv6](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#ii%C4%91%E1%BB%8Ba-ch%E1%BB%89-ipv6)
# [III. Phân loại địa chỉ IPv6](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#iiiph%C3%A2n-lo%E1%BA%A1i-%C4%91%E1%BB%8Ba-ch%E1%BB%89-ipv6)

## &ensp; [1. Address type loopback](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#1address-type-loopback)

## &ensp; [2. Address type Global Unicast Address](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#2address-type-global-unicast-address)

## &ensp; [3. Link-local](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#3link-local)
# [IV. Cơ chế tự EUI-64 tự động phát trinh 64 bit Interface ID(HOST ID) IPv6](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#ivc%C6%A1-ch%E1%BA%BF-t%E1%BB%B1-eui-64-t%E1%BB%B1-%C4%91%E1%BB%99ng-ph%C3%A1t-trinh-64-bit-interface-idhost-id-ipv6)
# [V. Cơ chế cấp IPv6 tự động SLAAC và DHCP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#vc%C6%A1-ch%E1%BA%BF-c%E1%BA%A5p-ipv6-t%E1%BB%B1-%C4%91%E1%BB%99ng-slaac-v%C3%A0-dhcp)
# [VI. Giải pháp IPv6 tunnel](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/32.IPv6/README.md#v%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-ipv6)
***
# ***I.	IPv6 là gì***
* IPv6 - Internet Protocol version 6 . Địa chỉ IPv6 ra đời nhằm giải quyết cho sự khan hiếm IPv4 do đó địa chỉ IPv6 ra đời với không gian địa chỉ IP lớn hơn nhằm đáp ứng nhu cầu kết nối vào Internet. Tuy vậy hiện nay vẫn sử dụng đan xen giữa 2 công nghệ trên
* Với IPv6 thì ta có thể định danh cho từng thiết bị trên hệ thống mạng toàn cầu và công nghệ NAT lúc này là không cần thiết


* Gói tin IPv6 

![](https://user-images.githubusercontent.com/52046920/191646720-824157e2-ad1b-446c-aedd-03577b3884e0.png)

* Số trường đã được rút gọn so với IPv4 nên sẽ xử lý ít hơn 

* Các trường của IPv6:
    * Version: Chỉ định phiên bản của IP, có giá trị 4 bit

    * Traffic Class: Trường này được sử dụng để biểu diễn mức ưu tiên của gói tin.

    * Payload Length: Trường này thay thế cho trường Total length của địa chỉ ipv4. Tuy nhiên, nó chỉ xác định chiều dài phần payload. Trường Payload Length bao gồm cả header mở rộng. Bằng 16 bit, có thể chỉ định IPv6 payload tới 65,535 byte. Trường này có giá trị 16 bit

    * Hop Limit: Thay thế trường Time to live của địa chỉ ipv4. Trường này có giá trị 8 bit

    * Next Header: Thay thế trường Protocol. Nó chỉ định đến header mở rộng đầu tiên (nếu có) hoặc thủ tục lớp trên như TCP, UDP, ICMPv6. Nếu sử dụng để chỉ định thủ tục lớp trên, trường này sẽ có giá trị tương tự như trường Protocol của địa chỉ ipv4. Trường này có giá trị 8 bit

    * Flow Label: Trường Flow Label có chiều dài 20 bít, là trường mới được thiết lập trong IPV6. Trường này được sử dụng để chỉ định rằng gói tin thuộc một dòng (flow) nhất định giữa nguồn và đích, yêu cầu IPv6 router phải có cách xử lý đặc biệt. Flow Label được dùng khi muốn áp dụng chất lượng dịch vụ (quality of service) không mặc định

    * Next Header: xác định gói tin có tồn tại header mở rộng hay không. Nếu không có, trường này sẽ có giá trị xác định header của tầng cao hơn (TCP hay UDP). Nếu có, giá trị trường Next Header chỉ ra loại header mở rộng đầu tiên theo sau header cơ bản. Trường Next Header của Header mở rộng sẽ trỏ tới header đằng sau nó. Trường này có giá trị 8 bit

    * Source Address: Địa chỉ nguồn
    * Destination Address: Địa chỉ đích
* Header mở rộng trong IPv6: Header mở rộng (extension header) là đặc tính mới trong thế hệ địa chỉ IPV6. Địa chỉ IPv6 đưa những đặc tính mở rộng và các dịch vụ thêm vào thành một phần riêng, gọi là header mở rộng. Gói tin IPv6 có thể có một hay nhiều header mở rộng, được đặt sau header chính, trước phần dữ liệu. Các header mở rộng được đặt nối tiếp nhau theo thứ tự quy định, mỗi dạng có cấu trúc trường riêng


# ***II.	Địa chỉ IPv6***

* IPv6 có chiều dài là 128 bit. Thường được hiện thị dưới dạng hexa cứ 4 bit thì được gom thành 1 số hexa và 4 số hexa được ngăn bởi dấu ":" ví dụ: 2001:0DB8:AC10:FE01:0000:0000:0000:0000

![](https://user-images.githubusercontent.com/52046920/191648120-e775735d-310a-40bb-b0ab-668fc79df092.png)

* Bảng quy đổi số Hexa

![](https://user-images.githubusercontent.com/52046920/191648477-bb1e5123-0d65-4ae6-9429-f13043ee087c.png)
* Địa chỉ IPv6 được chia thành 8 octet mỗi octet là 16 bits. 4 octet đầu là Network Prefix (NET ID)và 4 octet còn lại là Interface ID(HOST ID)

![](https://user-images.githubusercontent.com/52046920/191647616-e445d22c-62d7-44ee-9d24-ce39eeec1cd0.png)

* Rút gọn địa chỉ IPv6 bằng cách:
    * Loại bỏ các số 0 đầu tiên của mỗi octet
    * Các dải số 0 liên tiếp nhau có thể thay thế bằng cặp dấu "::". Cặp dấu "::" chỉ được xuất hiện 1 lần trong địa chỉ IPv6

![](https://user-images.githubusercontent.com/52046920/191649013-8bcadd98-c495-4bd2-be22-84986b357e7f.png)

* Vậy địa chỉ IPv6 2001:0ABC:00AB:000A:0000:0000:0000:1001 có thể được viết gọn dưới 1 trong 2 dạng sau

![](https://user-images.githubusercontent.com/52046920/191649017-91eb5a21-589c-4c4a-9273-ef83c1701b66.png)

# ***III.	Phân loại địa chỉ IPv6***

![](https://user-images.githubusercontent.com/52046920/191649540-324074ab-4ef5-4aab-9461-21fa419c601b.png)
* Địa chỉ IPv6 bao gồm 3 loại là:
    * Unicast:được chia nhỏ thành 3 loại địa chỉ là:
        * Global Unicast Address: 2000/3
        * Link local: FE80::/10
        * Loopback: ::1/128
    * Anycast: thực chất là Unicast gán trên nhiều thiết bị khác nhau
    * Multicast: có 3 loại địa chỉ thường tiếp xúc với có địa chỉ IPv6 đặc biệt như sau:
        * OSPFv3: FF02::5
        * RIPng: FF02::9
        * EIGRP: FF02::A

![](https://user-images.githubusercontent.com/52046920/191649656-da6504e5-5f79-4d7f-8c08-2103a0669bf8.png)

* IPv6 không có địa chỉ Broadcast mà thay thế bằng Multicast

## ***1.	Address type loopback***
* Được quy ước là địa chỉ ::1/128 là địa chỉ đặc biệt này. với IPv4 thì nó là địa chỉ 127.0.0.1

![](https://user-images.githubusercontent.com/52046920/191649944-8b0844e4-17e7-4e02-9da4-beb6aab858b8.png)

* Nếu máy tính có khả năng trao đổi dữ liệu với cả IPv4 và IPv6 một cách đồng thời thì nó máy tính được hỗ trợ Dual-stack

## ***2.	Address type Global Unicast Address***

![](https://user-images.githubusercontent.com/52046920/191649948-6c9861ea-6746-47d0-88de-afb16dbf1035.png)
* Tương ứng với IP public của IPv4. Với các địa chỉ này thì các thiết bị bên trong mạng có thể trao đỏi dữ liệu với Internet IPv6 bên ngoài
* Theo khuyến nghị thì các thiết bị bên trong mạng LAN nên sử dụng lớp mạng IPv6 là /64

![](https://user-images.githubusercontent.com/52046920/191649955-62719fe3-8f8b-40e4-82cf-e95faf01e0c6.png)
* Đối với IPv6 ta có thể căn cứ vào 32 bit đầu tiên để xác định xem đây là IPv6 được cấp bởi nhà cung cấp dịch vụ nào(VNPT, FPT, Viettel).
* Căn cứ vào 48 bit đầu tiên để xác định IPv6 thuộc khách hàng nào.
* 16 bit từ 48-68 để chia subnet trong hệ thống mạng nội bộ của doanh nghiệp.
* 64 Bit HOST ID sẽ giúp chúng ta định danh từng thiết bị trong mạng LÁN
## ***3.	Link-local***

* Là một địa chỉ có 64 bit đầu tiên luôn là FE80:: . Trong một interface có thể gán nhiều IPv6 tuy nhiên sẽ chỉ có duy nhất 1 địa chỉ đóng vai trò làm Link-Local. Địa chỉ Link-local dùng đẻ định danh duy nhất cho interface trên hệ thống mạng LAN.
* Khi gói tin tại Router gửi qua Interface thì địa chỉ Link-Local sẽ là Soure IP.
* Địa chỉ FF02::1 tương đương với 255.255.255.255 trên IPv4
* Cấu hình địa chỉ Link-local
```cisco
R1(config)#int g0/0
///Khởi động IPv6
R2(config-if)#ipv6 enable
///Gán địa chỉ link-local
R2(config-if)#ipv6 address fe80::1 link-local
```
* Chỉ cần kích hoạt IPv6 thì interface cũng được cấp tự động 1 địa chỉ IP Link-local mà không cần phải cấu hình. Sử dụng câu lệnh sau để kiểm tra
```cisco
R1#show ipv6 interface brief
```

![](https://user-images.githubusercontent.com/52046920/191653970-8af91cf5-9e89-4830-ac1a-a318f1b63b34.png)
* Trên là địa chỉ IPv6 Link-local được cấp tự động sau khi khởi động IPv6


* Địa chỉ Link-Local chỉ có thể giao tiếp được với các thiết bị bên trong vùng mạng của mình.

# ***IV.	Cơ chế tự EUI-64 tự động phát trinh 64 bit Interface ID(HOST ID) IPv6***
* Khi khởi động IPv6 thì đầu tiên là Link-local sẽ tự động phát sinh 
* Cơ chế EUI-64 sẽ chế biến địa chỉ MAC của thiết bị thành 64 Bit HOST ID qua 2 giai đoạn
    * Giai đoạn 1: Địa chỉ MAC sẽ được chia thành 2 phần bằng nhau. 24 bit đầu và 24 bit cuối.
    * Giai đoạn 2: chèn thêm 16 bit FF và FE vào giữa 2 chuỗi giá trị vừa chi ở giai đoạn 1. Nó sẽ chuyển giá trị của Bit số 7 thành 1 nếu bit đấy đang có giá trị là 0 sau đó nó gắn với 64 bit tạo thành địa chỉ Link-local FE80::

![](https://user-images.githubusercontent.com/52046920/191655151-9482ee6b-1f01-4665-8c30-e345e7c0445f.png)
* Ta có thể tận dụng cơ chế này tự động phát sinh ra 64 bit phần HOST bằng cách khi khai báo IPv6 chỉ cần Khai báo 64 bit đầu với lớp mạng /64 và khai báo phương thức EUI-64.
```cisco
R1(config)#int g0/1
R1(config-if)#ipv6 address 2001:0000:0000:0001::/64 eui-64 
```
# ***V.	Cơ chế cấp IPv6 tự động SLAAC và DHCP***

![](https://user-images.githubusercontent.com/52046920/191656765-b911de7e-7650-48b1-b0ed-495f56d7932f.png)
* SLAAC - Stateless Address Auto Configuration
```cisco
R1(config)#int g0/0
R1(config-if)#ipv6 enable
R1(config-if)#ipv6 address 2001::1/64 eui-64

///hiệu chỉnh thời gian gửi gói tin định kỳ để cấp IPv6 măc định là 200
R1(config-if)#ipv6 nd ra interval 200
R1(config-if)#exit

///Kích hoạt tính năng định tuyến (kích hoạt SLAAC)
R1(config)#ipv6 unicast-routing
```

* Statefull DHCP
```cisco
///Tạo pool IPv6
Router(config)#ipv6 dhcp pool P1

///Tạo dải mạng cấp và thời gian cấp vô hạn
Router(config-dhcpv6)#address prefix 2001::/64 lifetime infinite infinite
Router(config-dhcpv6)

///Default gateway
#link-address 2001::1/64
Router(config-dhcpv6)#ex

R1(config)#int g0/0
R1(config-if)#ipv6 enable
R1(config-if)#ipv6 address 2001::1/64 eui-64

///Tắt cơ chế gửi gói tin theo thời gian định kỳ
R1(config-if)#ipv6 nd ra suppress

///Nhúng Pool DHCP
R1(config-if)#ipv6 dhcp server P1
```
* Kết quả của 2 phương pháp cấp IPv6 động trên

![](https://user-images.githubusercontent.com/52046920/191658498-e0d33198-6a52-43ad-b767-5d86b4a4139c.png)

# ***V.	Định tuyến IPv6***
* Cấu hình bằng câu lệnh

![](https://user-images.githubusercontent.com/52046920/191658868-12fe3050-b415-4a24-af76-9c676c7b4f01.png)
```cisco
///Khởi động định tuyến 
R1#ipv6 unicast-routing

///Cấu hình tương tự IPv4 những sẽ không còn có subnet mask nữa mà chỉ có 2 trường là mạng đích và IP next hop

R1#ipv6 route 2002:0:0:0::/64 2001::2

///Hoặc
R1#ipv6 route 2002::/64 2001::2

```

* Cấu hình định tuyết động với các giao thức RIP, OSPF và EIGRP 

![](https://user-images.githubusercontent.com/52046920/191659411-b5694d09-d983-455e-b6af-00d205d0fc68.png)

# ***VI.	Giải pháp IPv6 tunnel***

![](https://user-images.githubusercontent.com/52046920/191659881-3823f40f-c40b-49e4-be2b-b29ce7fb2aec.png)

* Giải này pháp cho phép kết 2 hạ tầng IPv6 với nhau thông qua 1 hạ tầng IPv4 bằng cách tạo ra các interface tunnel cho 2 Router biên của hạ tầng IPv6

* Thiết lập Mannual Tunnel
* Đứng tại R1 và R3 thiết lập interface tunnel và gán IPv6 cho đường tunnel này

![](https://user-images.githubusercontent.com/52046920/191659883-c28aa090-1661-4e72-be1e-e6a3c906ec64.png)

* Các câu lệnh sử dụng

![](https://user-images.githubusercontent.com/52046920/191659886-567496e3-ede3-42d0-81bd-02f9a5ef2271.png)

* Thiết lập GRE Tunnel ta vẫn cấu hình như trên chỉ thay câu lệnh tunnel mode ipv6ip thành tunnel mode gre ip
* GRE cho phép chạy định tuyến động trên đường tunnel vậy nên lúc này sẽ không cần sử dụng giao thức định tuyến tính nữa

![](https://user-images.githubusercontent.com/52046920/191660769-9f796fee-1b49-4928-83ec-87857ebfbc47.png)
