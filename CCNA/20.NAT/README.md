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

# TÌM HIỂU VỀ NAT
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. NAT là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#inat-l%C3%A0-g%C3%AC)

## &ensp; [1. Hoạt động của NAT](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#1ho%E1%BA%A1t-%C4%91%E1%BB%99ng-c%E1%BB%A7a-nat)

## &ensp; [2. Các thuật ngữ được sử dụng trong NAT](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#2c%C3%A1c-thu%E1%BA%ADt-ng%E1%BB%AF-%C4%91%C6%B0%E1%BB%A3c-s%E1%BB%AD-d%E1%BB%A5ng-trong-nat)

## &ensp; [3. Ưu nhược điểm](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#3%C6%B0u-nh%C6%B0%E1%BB%A3c-%C4%91i%E1%BB%83m)
# [II. Phân loại và cấu hình NAT](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#iiph%C3%A2n-lo%E1%BA%A1i-v%C3%A0-c%E1%BA%A5u-h%C3%ACnh-nat)
## &ensp; [1. Static NAT](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#1static-nat)
## &ensp; [2. Dynamic NAT](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#2dynamic-nat)
## &ensp; [3. NAT Overload](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#3nat-overload)
## &ensp; [4. Cấu hình Static NAT IP và Port](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/20.NAT/README.md#4c%E1%BA%A5u-h%C3%ACnh-static-nat-ip-v%C3%A0-port)
***
# ***I.	NAT là gì***
* NAT hay Network Address Translation là một kỹ thuật biên dịch địa chỉ IP này thành địa chỉ IP khác cụ thể hơn là biên dịch từ IP Private thành IP Public giúp cho hệ thống có thể truy cập mạng.
* Do Private IP không được sử dụng trên môi trường ngoài mạng internet vậy nên NAT giúp cho các ip Private có thể truy cập được mạng internet. Vị trí đặt NAT là những Router nối mạng nội bộ ra ngoài internet được gọi là Router biên(nơi kết nối 2 mạng).
## ***1.	Hoạt động của NAT***
* NAT thực hiện truyền gói tin qua các lớp mạng khác nhau, nó còn tiến hành thay đổi ip bên trong gói tin. Khi gói tin muốn đi ra ngoài mạng NAT sẽ thực hiện chuyển đổi IP Private thành IP Public để gói tin có thể đi ra ngoài mạng. Khi gói tin quay lại nó sẽ chuyển đổi IP Pulbic thành IP private và chuyển về đúng máy có IP Private.
* Nhờ cơ chế đó của mình NAT cũng giúp được việc che giấu các IP đứng sau nó ở trong mạng nội bộ giúp gia tăng bảo mật
* 1 địa chỉ NAT có thể được sử dụng thay thế cho rất nhiều địa chỉ IP Private đi ra ngoài mạng

## ***2.	Các thuật ngữ được sử dụng trong NAT***
* Private IP: là một dải IP được sử dụng trong mạng nội bộ và không thể kết nối trực tiếp ra ngoài mạng internet
* Pulbic IP: là địa chỉ được cung cấp bởi các các tổ chức ví dụ như nhà mạng thường sẽ sử dụng NAT để chuyển đổi IP Private thành IP Public để ó thể kết nối với mạng internet bên ngoài
* Địa chỉ inside local: là địa chỉ được gán cho 1 thiết bị ở mạng nội bộ bên trong chính là  IP Private
* Địa chỉ inside global: là địa chỉ được đăng ký tại các nhà cung cấp dịch vụ thường dùng để thay thế cho inside local. Là 1 địa chỉ Public
* Địa chỉ outside local: là địa chỉ IP của thiết bị bên ngoài mạng nằm trong 1 mạng khác
* Địa chỉ outside global: địa chỉ được đặt cho thiết bị thuộc ngoài mạng. Là 1 địa chỉ ip Pulbic
## ***3.	Ưu nhược điểm***
* Ưu điểm:
    * Tiết kiệm địa chi IPv4: Chỉ cần 1 địa chỉ IP Public có thể giúp cho rất nhiều địa chỉ IP Private có thể truy cập mạng. Điều đó giúp giảm thiểu rất nhiều số lượng địa chỉ IP cần sử dụng
    * Che giấu đi địa chỉ IP nội bộ đứng sau NAT. Giúp tăng bảo mật
* Nhược điểm:
    * Tăng độ trễ của tốc độ đường truyền do NAT phải mất thêm thời gian để kiểm tra và biên dịch ÍP
    * NAT giúp che giấu các địa chỉ IP đằng sau nó việc này giúp tăng bảo mật tuy nhiên nếu có sự cố sẽ khó tìm được vấn đề và nguồn gốc của IP gây ra sự cố hoặc đang gặp sự cố, gây khó cho việc truy vết

# ***II.	Phân loại và cấu hình NAT***
## ***1.	Static NAT***
* Được dùng để chuyển đổi 1:1 giữa 2 IP Private và IP Public. Phải cấu hình cho từng IP một muốn ánh xạ.
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/187649750-9ff59b85-4bb1-4139-97cb-b52291ae8cd7.png)
* Cấu hình NAT cho Server 1 và Server 2 ra ngoài có ip Public lần lượt là 100.0.0.1 và 100.0.0.2
* Tại Sw1
```cisco
SW1(config)#vlan10
SW1(config-vlan)#vlan20
SW1(config-vlan)#exit
SW1(config)#int f0/2
SW1(config-if)#switchport mode access 
SW1(config-if)#switchport access vlan 10
SW1(config-if)#int f0/3
SW1(config-if)#switchport mode access 
SW1(config-if)#switchport access vlan 20
SW1(config-if)#int f0/1
SW1(config-if)#switchport mode trunk 
```
* Tại SW2
```cisco
SW2(config)#vlan10
SW2(config-vlan)#vlan20
SW2(config-vlan)#exit
SW2(config)#int f0/2
SW2(config-if)#switchport mode access 
SW2(config-if)#switchport access vlan 10
SW2(config-if)#int f0/3
SW2(config-if)#switchport mode access 
SW2(config-if)#switchport access vlan 20
SW2(config-if)#int f0/1
SW2(config-if)#switchport mode trunk 
```

* Tại Router2
```cisco
R2(config)#int g0/1.10
R2(config-subif)#encapsulation 
R2(config-subif)#encapsulation dot1Q 10
R2(config-subif)#ip address 172.17.0.1 255.255.0.0
R2(config-subif)#int g0/1.20
R2(config-subif)#encapsulation dot1Q 20
R2(config-subif)#ip address 172.18.0.1 255.255.0.0
R2(config-subif)#exit
R2(config)#ip route 100.0.0.0 255.0.0.0 205.0.0.1
```

* Tại router1
```cisco
R1(config)#int g0/1.10
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip address 192.168.10.1 255.255.255.0
R1(config-subif)#int g0/1.20
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip address 192.168.20.1 255.255.255.0
R1(config-subif)#exit

R1(config)#ip route 172.16.0.0 255.255.0.0 205.0.0.2
R1(config)#ip route 172.17.0.0 255.255.0.0 205.0.0.2
R1(config)#ip route 172.18.0.0 255.255.0.0 205.0.0.2
```
* Cấu hình NAT tại R1 như sau

```cisco
///interface hướng vào trong mạng lan sẽ để inside ở đây do các Server nằm ở các VLAN khác nhau nên sẽ sử dụng sub-interface vì vậy phải cấu hình ở sub-interface
R1(config)#int g0/1.10
R1(config-subif)#ip nat inside 
R1(config-subif)#int g0/1.20
R1(config-subif)#ip nat inside 

///interface hướng ra ngoài sẽ để outside
R1(config-if)#int g0/0
R1(config-if)#ip nat outside 
R1(config-if)#exit

R1(config)#ip nat inside source static 192.168.10.2 100.0.0.1
R1(config)#ip nat inside source static 192.168.20.2 100.0.0.2

```
* Kiểm tra từ PC1 và PC2 ping đến Server1 và Server2 thông qua ip Public được cấu hình của chúng 

![](https://user-images.githubusercontent.com/52046920/187649757-b2191c1a-0406-4677-8b3c-52628fb4f054.png)

* Kiểm tra NAT table bằng câu lệnh
```cisco
R1#show ip nat translations
```

![](https://user-images.githubusercontent.com/52046920/187650366-1e41aefb-ebfa-46f3-ad94-86a289e4ab9c.png)
* Đã cấu hình Static NAT thành công
## ***2.	Dynamic NAT***
* Dùng để ánh xạ Private IP sang Public IP 1 cách tự động theo 1 bể ip Public được đăng ký và được cấu hình chỉ định sẵn
* Câu lệnh
```cisco
Router (config) # ip nat pool [tên pool] [IP public bắt đầu dải] [IP Public kết thúc của dải được cấp] netmask [netmask]

///ví dụ
Router (config) # ip nat pool abc 202.1.1.177 202.1.1.185 netmask 255.255.255.0

///Tạo 1 ACL chỉ định các ip được phép chuyển đổi thành IP Public ví dụ
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#access-list 1 permit 192.168.20.0 0.0.0.255

/// truyền ACL vào làm list các ip được cấp NAT
Router (config) # ip nat inside source list <acl-number> pool <name>

///ví dụ
R1(config)#ip nat inside source list 1 pool abc
```
* Còn lại giống với Static NAT
* Sử dụng mô hình sau

![](https://user-images.githubusercontent.com/52046920/187649738-66024221-4eca-4c6e-9799-f616df7348a7.png)
* Cấu hình cho Dynamic NAT cho Server1 và Server2 ra ngoài với ip public thuộc khoảng 100.0.0.1-100.0.0.20.
* Các cấu hình khác tương tự phần static NAT. Ta sẽ đi vào cấu hình Dynamic NAT trên router R1

```cisco
R1(config)#ip nat pool abc 100.0.0.1 100.0.0.20 netmask 255.0.0.0
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#access-list 1 permit 192.168.20.0 0.0.0.255
R1(config)#ip nat inside source list 1 pool abc


R1(config)#int g0/1
R1(config-if)#ip nat inside 
R1(config-if)#int g0/0
R1(config-if)#ip nat outside 
```
* Kiểm tra ping từ server ra ngoài. Sau đó kiểm tra bảng ip NAT

![](https://user-images.githubusercontent.com/52046920/187649744-bcf8ba0e-ca31-4920-a9dc-d84c40314a7d.png)
* NAT đã được cấp động
## ***3.	NAT Overload***
* NAT Overload hay còn gọi là PAT hay Port Address Translation. Có thể coi là 1 biến thể của Dynamic NAT có thể chuyển đổi IP 1 cách tự động. PATH sẽ ánh xạ các IP Private thành 1 IP Public và nó phân biệt các IP Private ánh xạ qua bằng các Port thay vì tạo 1 bể các IP. Điều này giúp tiết kiệm được địa chỉ IP. Địa chỉ IP Public thì nó sẽ dùng địa chỉ của cổng ra ngoài mạng luôn
```cisco
R1(config)#ip nat inside source list 1 interface g0/0 overload
```

* Sử dụng mô hình sau

![](https://user-images.githubusercontent.com/52046920/187650371-6d4e2435-c4dd-48f5-9b76-632ff9265c09.png)
* Cấu hình cho PAT NAT cho Server1 và Server2 ra ngoài với ip public thuộc khoảng 100.0.0.1-100.0.0.20.
* Các cấu hình khác tương tự phần static NAT. Ta sẽ đi vào cấu hình PAT NAT trên router R1
```cisco
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#ip nat inside source list 1 interface g0/0 overload

R1(config)#int g0/1
R1(config-if)#ip nat inside 
R1(config-if)#int g0/0
R1(config-if)#ip nat outside 
```

* Kiểm tra hãy ping thử đến bên ngoài sau đó kiểm tra bảng NAT

![](https://user-images.githubusercontent.com/52046920/187649747-eb1a0789-ff6f-4a0e-9b42-4bcbab75367a.png)

* Trong trường hợp interface đi ra ngoài sử dụng dhcp để xin cấp IP ví dụ ở đây nó R2 cấp cho R1 1 dải ip 203.0.0.1-203.0.0.6 ta cấu hình như sau
```cisco

R1(config)#ip nat inside source list 1 pool DHCP overload

R1(config)#ip nat pool DHCP 203.0.0.1 203.0.0.6 255.255.255.0
```
## ***4.	Cấu hình Static NAT IP và Port***
* Trong trường hợp cấu hình Static NAT cho server tuy nhiên chi có 1 địa chỉ IP Public thì ta sẽ phái cấu hình theo cổng của từng dịch vụ của server
* Câu lệnh cấu hình như sau
```cisco
ip nat inside source static [Giao thức] [ip server] [cổng dịch vụ server đó sử dụng] [IP Public] [Cổng được gán]
///Cấu hình dịch vụ web Server 1
R1(config)#ip nat inside source static tcp 192.168.10.2 80 100.0.0.1 80

///Cấu hình cho dịch vụ TFTP của server 2
R1(config)#ip nat inside source static udp 192.168.20.2 69 100.0.0.1 69
```
* Trong trường hợp cả 2 Server đều sử dụng dịch vụ web
```cisco
R1(config)#ip nat inside source static tcp 192.168.10.2 80 100.0.0.1 80
R1(config)#ip nat inside source static tcp 192.168.20.2 80 100.0.0.1 8080
```



### ***Lưu ý:*** Server web sẽ chỉ thiết lập Static NAT để các máy tính ngoài internet đều có thể truy cập
