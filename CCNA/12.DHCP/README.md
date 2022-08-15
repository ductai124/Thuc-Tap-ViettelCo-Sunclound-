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

# TÌM HIỂU VỀ DHCP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. DHCP là gì ?](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#idhcp-l%C3%A0-g%C3%AC-)
# [II. Cấu hình DHCP Server trên Cisco Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#iic%E1%BA%A5u-h%C3%ACnh-dhcp-server-tr%C3%AAn-cisco-router)
# [III. Cấu hình DHCP Server trên Switch Layer 3](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#iiic%E1%BA%A5u-h%C3%ACnh-dhcp-server-tr%C3%AAn-switch-layer-3)
## &ensp; [1. Sử dụng Switch layer 3 cấp DHCP cho các Vlan](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#1s%E1%BB%AD-d%E1%BB%A5ng-switch-layer-3-c%E1%BA%A5p-dhcp-cho-c%C3%A1c-vlan)

## &ensp; [2. Sử dụng Router cấp DHCP và định tuyến cho cho các Vlan](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#2s%E1%BB%AD-d%E1%BB%A5ng-router-c%E1%BA%A5p-dhcp-v%C3%A0-%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-cho-cho-c%C3%A1c-vlan)
# [IV. Cấp IP cố định cho thiết bị bằng DHCP Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#ivc%E1%BA%A5p-ip-c%E1%BB%91-%C4%91%E1%BB%8Bnh-cho-thi%E1%BA%BFt-b%E1%BB%8B-b%E1%BA%B1ng-dhcp-server)
# [V. Cấu hình chức năng DHCP Relay chuyển tiếp lưu lượng xin IP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#vc%E1%BA%A5u-h%C3%ACnh-ch%E1%BB%A9c-n%C4%83ng-dhcp-relay-chuy%E1%BB%83n-ti%E1%BA%BFp-l%C6%B0u-l%C6%B0%E1%BB%A3ng-xin-ip)
# []()
# []()
## &ensp; [VI. Cấu hình chức năng DHCP Client trên Cisco Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#vic%E1%BA%A5u-h%C3%ACnh-ch%E1%BB%A9c-n%C4%83ng-dhcp-client-tr%C3%AAn-cisco-router)

## &ensp; [VII. Khắc phục sự cố Conflict IP trên DHCP Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/12.DHCP/README.md#viikh%E1%BA%AFc-ph%E1%BB%A5c-s%E1%BB%B1-c%E1%BB%91-conflict-ip-tr%C3%AAn-dhcp-server)

***
# ***I.	DHCP là gì ?***
* DHCP viết tắt của Dynamic Host Configuration Protocol là giao thức tự động cấp phát địa chỉ IP đến các thiết bị trong mạng. Các địa chỉ IP được cung cấp từ giao thức DHCP sẽ cho phép chúng ta truy cập vào internet. Ngoài ra nó cũng đảm bảo không có trường hợp hai hoặc nhiều thiết bị có cùng IP và còn cung cấp các thông tin cấu hình như DNS, subnet mask, default gateway.
* Cách thức hoạt động khá đơn giản khi có một thiết bị cần truy cập mạng, nó sẽ gửi yêu cầu từ một router và được router gán cho một địa chỉ IP khả dụng. Các ip được gán sẽ không bao giờ trùng nhau
* Router hoạt động như một máy chủ DHCP đối với các mô hình mạng nhỏ hoặc hộ gia đình. Đối với các mạng lớn hơn một router không thể quản lý số lượng lớn các thiết bị nên phải sử dụng 1 máy chủ DHCP chuyên dụng.
* Cấu trúc DHCP gồm:
    * **DHCP client**: Là các thiết bị có thể kết nối với mạng Internet như điện thoại, laptop, máy tính, máy in, tivi,… và chúng sẽ giao tiếp với máy chủ DHCP để nhận IP truy cập mạng.
    * **DHCP server**: Là thiết bị đóng vai trò là máy chủ có nhiệm vụ nhận yêu cầu và cấp phát địa chỉ IP đến các DHCP Client.
    * **DHCP relay agents**: Đóng vai trò là thiết bị trung gian giúp kết nối DHCP Client và DHCP Server. Thiết bị này thường chỉ xuất hiện trong các mô hình mạng lớn và có nhiều kết nối phức tạp
    * **Binding**: Là một tập hợp chứa các thông tin cầu hình trong đó có chưa ít nhất 1 địa chỉ IP đã được cấp phát đến 1 DHCP Client và máy chủ DHCP sẽ quản lý các kết nối này.
    * **DHCP Lease**: Là thời gian mà thiết bị sử dụng 1 địa chỉ IP trước khi gia hạn. Mỗi IP khi được cấp phát đều có thời gian sử dụng nhất định và được cấp địa chỉ mới khi hết hạn.

![](https://fptcloud.com/wp-content/uploads/2022/01/cac-thong-diep-cua-dhcp.jpg)
* Các thông điệp
    * **DHCP Discover**: Là gói tin được tạo khi thiết bị yêu cầu truy cập mạng gửi broadcast trên physical subnet để đến server DHCP.
    * DHCP Offer: Sau khi nhân được DHCP Discover thì DHCP Server sẽ gửi gói tin chứa thông tin địa chỉ IP và cấu hình TCP/IP bổ sung cho máy tính Client.
    * **DHCP Request**: Là gói thông tin do DHCP client lại cho máy chủ DHCP sau khi tiếp nhận DHCP Offer nhằm xác nhận đã chấp nhận địa chỉ IP được cấp phát.
    * **DHCP Acknowledge**: Khi xác nhận DHCP Request của máy Client thì DHCP gửi lại gói DHCP acknowledge và kèm theo đính hướng tham số để Client có thể tham gia mạng TCP/IP
    * **DHCP Nak**: Đối với các địa chỉ IP không còn giá trị sử dụng hoặc được sử dụng bởi 1 máy khác thì DHCP server thực hiện gửi gói DHCP Nak để thông báo cho Client thuê bao lại IP.
    * **DHCP Decline**: Được gửi đến các DHCP server khi Client thực hiện quyết định tham số thông tin không còn giá trị và tiến hành thuê bao lại.
    * **DHCP Release**: Do DHCP Client gửi đến server để thông báo giải phóng địa chỉ IP cùng lúc đó Client sẽ tiến hành xóa thuê bao đang tồn tại.


* Quá trình đạt được địa chỉ IP được mô tả dưới đây:

* Bước 1: Client khởi động với "địa chỉ IP rỗng" cho phép liên lạc với Server DHCP bằng giao thức UDP. Nó truyền đi DHCP Discover chứa địa chỉ MAC và tên máy tính. Client phát tán liên tục thông điệp này lên mạng cho đến khi nhận được phản hồi từ Server DHCP.

* Bước 2: Nếu Server DHCP nhận thông điệp từ Client, nó cấp xuống địa chỉ ip đầu tiên trong dải của nó thông qua DHCP Offer 

* Bước 3: Khi Client nhận DHCP Offer(sử dụng bản tin gửi đến nó đầu tiên). Client gửi tiếp bản tin  DHCP Request báo cho server biết răng nó đã sử dụng ip trong bản tin và sử dụng địa chỉ ip được cấp. 
* Bước 4: DHCP Nhận DHCP Request
nhận thấy Client đã lấy địa chỉ ip sử dụng và nó sẽ ghi chú lại địa chỉ ip đó và không cấp địa chỉ đó cho Client nào khác. Server sẽ xác nhận về cho Client 1 bản tin ACK

* Ưu điểm
    * Giúp các thiết bị kết nối mạng nhanh chóng từ máy tính, laptop, điện thoại, máy tính bảng…
    * Quản lý địa chỉ IP một cách khoa học, tránh trường hợp trùng IP trên nhiều, đảm bảo cấu hình tự động cho mọi thiết bị kết nối mạng.
    Quản lý địa chỉ IP và các tham số TCP/IP dễ dàng qua các trạm.
    * Các nhà quản trị mạng có thể thay đổi cấu hình và thông số của IP để nâng cấp cơ sở hạ tầng.
    * Các thiết bị có thể di chuyển tự do từ mạng này sang mạng khác và nhận IP mới tự động.
* Nhược điểm
    * Việc sử dụng IP động của DHCP không phù hợp với các thiết bị cố định và cần truy cập liên tục như máy in, file server.
    * DHCP thường chỉ được sử dụng tại các hộ gia đình hoặc mô hình mạng nhỏ.

* Kích hoạt chức năng DHCP trên máy tính cá nhân

![]()

# ***II.	Cấu hình DHCP Server trên Cisco Router***
* DNS server là máy chủ chứa cơ sở dữ liệu về địa chỉ IP public và các hostname được liên kết với chúng. Đây là một hệ thống chuyển đổi các tên miền website, chuyển từ dạng www.tenten.com sang dạng địa chỉ IP tương ứng với tên miền và ngược lại. 

![](https://user-images.githubusercontent.com/52046920/183797768-de9d0ad3-61e6-448f-8c1e-65d9eb0986e7.png)
* Sự dụng câu lệnh

```cisco
R1(config)#ip dhcp pool PHONG_KT
R1(dhcp-config)#network 10.0.0.0 255.0.0.0              ///Dải mạng cấp DHCP
R1(dhcp-config)#default-router 10.0.0.1                 ///Default gateway

R1(dhcp-config)#lease 1 0 0                     ///lease [day] [hour] [minute] là thời gian cấp DHCP, sau khoảng thời gian này server sẽ cấp lại DHCP cho các thiết bị
```
* Câu lệnh loại bỏ các ip trong dải ip ra khỏi bể DHCP, việc này nhằm giữ lại 1 số ip để cấu hình ip tĩnh cho các thiết bị cần ip không thay đổi
```cisco
R1(config)#ip dhcp excluded-address 10.0.0.1 10.0.0.20      /// loại bỏ ip từ 10.0.0.1 đến 10.0.0.20
```
![](https://user-images.githubusercontent.com/52046920/184571327-d6aab480-0623-4e41-a1af-7919ae2c5e94.png)
![](https://user-images.githubusercontent.com/52046920/184571325-27bbd066-2e00-4b6f-9941-eb1441d826b7.png)
![](https://user-images.githubusercontent.com/52046920/184571323-da8d1296-6e80-487a-b910-2b83ed38de7f.png)



* Khi có 2 phân đoạn mạng khác nhau thì phải tạo ra 2 ip dhcp pool

```cisco
R1(config)#ip dhcp pool PHONG_KD
R1(dhcp-config)#network 192.168.1.0 255.0.0.0              ///Dải mạng cấp DHCP
R1(dhcp-config)#default-router 192.168.1.1                 ///Default gateway
```
# ***III.	Cấu hình DHCP Server trên Switch Layer 3***
## ***1.	Sử dụng Switch layer 3 cấp DHCP cho các Vlan***
* Switch Layer 3 cũng có chức năng của 1 con Router nên ta có thể dùng Switch layer 3 để có thể cấp DHCP cho các Vlan như mô hình dưới đây

![](https://user-images.githubusercontent.com/52046920/183626729-dcb37cc8-3b07-473f-afea-76df0cc137d9.png)

* Trước tiên cấu hình Vlan
```cisco
Switch(config)#vlan 20
Switch(config-vlan)#exit 

Switch(config)#vlan 30
Switch(config-vlan)#exit

Switch(config)#int gig1/0/2
Switch(config-if)#switchport mode access 
Switch(config-if)#switchport access vlan 20
Switch(config-if)#exit

Switch(config)#int gig1/0/3
Switch(config-if)#switchport mode access 
Switch(config-if)#switchport access vlan 30


Switch(config)#int vlan 20
Switch(config-if)#ip address 20.0.0.1 255.0.0.0
Switch(config-if)#no shut
Switch(config-if)#exit


Switch(config)#int vlan 30
Switch(config-if)#ip address 30.0.0.1 255.0.0.0
Switch(config-if)#no shut
Switch(config-if)#exit
```

* Cấu hình DHCP 
```cisco
Switch(config)#ip dhcp pool LAN20
Switch(dhcp-config)#network 20.0.0.0 255.0.0.0
Switch(dhcp-config)#default-router 20.0.0.1
Switch(dhcp-config)#exit

Switch(config)#ip dhcp pool LAN30
Switch(dhcp-config)#network 30.0.0.0 255.0.0.0
Switch(dhcp-config)#default-router 30.0.0.1
Switch(dhcp-config)#exit
```
* DHCP được cấp thành công

![](https://user-images.githubusercontent.com/52046920/183626735-0b7d5594-0f9b-4559-867d-ebe06a5e04a8.png)

## ***2.	Sử dụng Router cấp DHCP và định tuyến cho cho các Vlan***
* Ta có thể cấp DHCP từ Router cho các VLan nối với switch layer 3 như mô hình dưới đây

![](https://user-images.githubusercontent.com/52046920/183626741-3b1ee634-5c16-432a-a967-7168d3238ac2.png)
* Tại router
```cisco
Router(config)#int gig0/0
Router(config-if)#no shutdown 
Router(config-if)#exit

Router(config)#int gig0/0.2
Router(config-subif)#encapsulation dot1Q 20         ///Tương đương Vlan 20
Router(config-subif)#ip address 20.0.0.1 255.0.0.0
Router(config-subif)#no shutdown 
Router(config-subif)#end

Router(config)#int gig0/0.3
Router(config-subif)#encapsulation dot1Q 30         ///Tương đương Vlan 30
Router(config-subif)#ip address 30.0.0.1 255.0.0.0
Router(config-subif)#no shutdown
Router(config-subif)#exit 

///Cấu hình DHCP
Router(config)#ip dhcp pool LAN20
Router(dhcp-config)#network 20.0.0.0 255.0.0.0
Router(dhcp-config)#default-router 20.0.0.1
Router(dhcp-config)#dns-server 8.8.8.8              ///Dns server của google Không thiết lập cũng được
Router(dhcp-config)#exit

Router(config)#ip dhcp pool LAN30
Router(dhcp-config)#network 30.0.0.0 255.0.0.0
Router(dhcp-config)#default-router 30.0.0.1
Router(dhcp-config)#dns-server 8.8.8.8              ///Dns server của google Không thiết lập cũng được 
```

* Tại switch
```cisco
Switch(config)#vlan 20
Switch(config-vlan)#exit 

Switch(config)#vlan 30
Switch(config-vlan)#exit

Switch(config)#int gig1/0/2
Switch(config-if)#switchport mode access 
Switch(config-if)#switchport access vlan 20
Switch(config-if)#exit

Switch(config)#int gig1/0/3
Switch(config-if)#switchport mode access 
Switch(config-if)#switchport access vlan 30

Switch(config)#interface gig1/0/1
Switch(config-if)#switchport mode trunk
Switch(config)#interface vlan 30
Switch(config-if)#ip address dhcp 
Switch(config)#interface vlan 20
Switch(config-if)#ip address dhcp 
```

* DHCP đã được cấp thành công

![](https://user-images.githubusercontent.com/52046920/183626736-5f2aa9a4-d688-47e8-9dc2-b63ed8d56a25.png)

# ***IV.	Cấp IP cố định cho thiết bị bằng DHCP Server***
* Trong 1 môi trường mạng sẽ có một số thiết bị đặc thù phải cấp ip cố định như máy in, camera, server.
* Tại sao phải cấp IP cố định cho thiết bị: nếu kết nối với một máy in nhất định không được cấu hình ip tĩnh mà có có sự cố bất ngờ sau đó hệ thống kết nối lại với nhau máy in sẽ được cấp 1 ip khác và tất cà những người muốn sử dụng máy in sẽ phải cập nhật lại ip của máy in nếu muốn sử dụng(Xóa đi và thêm lại máy in trên máy tính), Việc này cực kỳ khó kiểm soát trên 1 hệ thống mạng lớn có thể dẫn đến nhầm lẫn các máy in trên 1 hệ thống.
* IP cố định sẽ được cấp theo địa chỉ MAC của thiết bị, ứng với mỗi địa chỉ MAC sẽ ứng với 1 IP được cấp cố định.
* Cho mô hình. Giả sử PC tên là PR1 là máy in và sử dụng DHCP cấp phát địa chỉ ip tĩnh cho nó là 192.168.10.10/24. Bài lab thực hiện trên EVE do trên cisco packet tracer router không có câu lệnh để DHCP cấp ip tĩnh

![](https://user-images.githubusercontent.com/52046920/184571332-a7c78c82-8563-4236-93ab-da58b5499dd1.png)

```cisco
R1(config)#int e0/0
R1(config-if)#ip address 192.168.10.1 255.255.255.0
R1(config-if)#no shut
R1(config-if)#exit

R1(config)#ip dhcp excluded-address 192.168.10.1 192.168.10.20      /// loại bỏ ip từ 192.168.10.1 đến 192.168.10.20 để dự trữ làm số lượng ip tĩnh để cấp cho máy in và camera

R1(config)#ip dhcp pool LAN1
R1(dhcp-config)#network 192.168.10.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.10.1

```
* Do trên eve không có câu lệnh để kiểm tra MAC vậy nên ta sử dụng giao thức ARP bằng cách:
    * Đầu tiên cấp DHCP ngẫu nhiên cho toàn bộ máy tính
    * Sau đó tại VPC1 ping đến may PR1 giả định làm máy in. 
    * Sau khi ping thành công thì sử dụng cú pháp arp trong VPC 1 để kiểm tra bảng ARP và ở đây ta có thể thấy được địa chỉ MAC của PR1 là 00:50:79:66:68:05

![](https://user-images.githubusercontent.com/52046920/184571329-455e44fc-368f-40bc-8ea3-f959afc47b80.png)
![]()

* Thiết lập DHCP cấp ip tĩnh cho PR1
```cisco
Router(config)#ip dhcp pool PR1
Router(dhcp-config)#host 192.168.10.10 255.255.255.0

///Địa chỉ MAC phải thêm 01 vào đầu và viết lại như sau
Router(dhcp-config)#client-identifier 0100.5079.6668.05         
///01 ám chỉ là sử dụng Ethernet không phải Token Ring

Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#exit
```
* Kết quả
    * 2 Máy PC được cấp ip ngẫu nhiên
    
    ![](https://user-images.githubusercontent.com/52046920/184571316-e0066f1d-1420-4615-b377-030db823b179.png)
    * PR1 được cấp IP cố định là 192.168.10.10/24 

    ![](https://user-images.githubusercontent.com/52046920/184571321-eaa5e8db-774e-4663-a6f8-4a92cd743a53.png)

# ***V.	Cấu hình chức năng DHCP Relay chuyển tiếp lưu lượng xin IP***
* Do các gói tin gửi đến trên địa chỉ broadcast thì không được đi qua bộ định tuyến mà clients sử dụng địa chỉ broadcast để quảng bá yêu cầu cấp phát IP nên nếu có nhiều mạng thì mỗi mạng phải dựng riêng 1 DHCP server nếu muốn sử dụng DHCP cấp phát IP động.
* DHCP Replay Agent là một tính năng được cấu hình cho các Router trung gian. Nó cho phép chuyển tiếp lưu lượng xin ip đến DHCP server. 
 
* Những trường hợp cần sử dụng DHCP Relay Agent :
    * Phù hợp với những máy tính thường xuyên di chuyển giữa các lớp mạng khác nhau 
    * Thuận tiện cho việc mở rộng hệ thống mạng
    * Có thể kết hợp với mạng không dây ( Wireless)
    * Do các gói tin quảng bá không thể đi qua router nên nếu có nhiều mạng thì mỗi mạng phải dựng 1 DHCP server, việc này gây tốn kém và không cần thiết. Việc bảo trì cũng như quản lý cũng rất khó khăn. 
* Tiến trình thực hiện:

    ![](https://user-images.githubusercontent.com/52046920/184597105-0e8553dd-3199-408a-9d29-81c0fb5a2213.png)
    * Bước 1: CLient gửi Broadcast bản tin DHCP Discover trong mạng nội bộ
    * Bước 2: Tính năng DHCP Rely Agent cũng mạng sẽ nhận gói tin và chuyển đến DHCP Server bằng unicast

    ![](https://user-images.githubusercontent.com/52046920/184597104-4fd5b78c-26fd-4643-9d18-14c3d83aa59c.png)
    * Bước 3: DHCP server gửi unicast bản tin DHCP Offer trả lại DHCP Rely Agent.
    * Bước 4: DHCP Relay Agent sẽ Broadcast gói tin DHCP Offer đến các Client

    ![](https://user-images.githubusercontent.com/52046920/184597101-1404990e-e82c-4654-bbab-d2952e4388a1.png)
    * Bước 5: Client nhận DHCP Offer nó sẽ gửi Broadcasts gói tin HDCP Request cho Relay Agent.
    * Bước 6: DHCP Rely Agent nhận được DHCP Request và chuyển DHCP Server bằng unicast.

    ![](https://user-images.githubusercontent.com/52046920/184597099-3c6a2689-1222-45d1-9e14-2fc8878dd3cc.png)
    * Bước 7: DHCP server dùng tín hiệu Unicast gởi trả lời cho DHCP Relay Agent một gói tin DHCP ACK.

    * Bước 8: Và DHCP Relay Agent sẻ Broadcasts gói tin DHCP ACK đến Client để Client nhận được IP.   

    ![](https://user-images.githubusercontent.com/52046920/184597095-e5ff0166-8808-483d-88c4-eaa474434a6f.png)

* Tiến hành cấu hình chức năng DHCP Relay chuyển tiếp lưu lượng xin IP trên mô hình sau:

![](https://user-images.githubusercontent.com/52046920/184598952-5cd3ac46-a7fa-4b3d-be4e-73f6c1d7eca2.png)

* Router R1 Đóng vai trò làm DHCP Server

|Port|IP|
|--|--|
|gig0/0|172.16.0.1 /16|

* Router R2

|Port|IP|
|--|--|
|gig0/0|172.16.0.2 /16|
|gig0/1|192.168.20.1 /24|

* Router R3 sẽ đóng vai trò làm DHCP Rely Agent

|Port|IP|
|--|--|
|gig0/0|192.168.20.2 /24|
|gig0/1|10.0.0.1 /8|

* Tiến hành cấu hình
* Tại R1
```cisco
R1(config)#int g0/0
R1(config-if)#ip add 172.16.0.1 255.255.0.0
R1(config-if)#no shut
R1(config-if)#exit

///Định tuyến cho Router R1
R1(config)#ip route 10.0.0.0 255.0.0.0 172.16.0.2
R1(config)#exit

///Cấu hình DHCP
R1(config)#ip dhcp pool LAN1
R1(dhcp-config)#network 10.0.0.0 255.0.0.0
R1(dhcp-config)#default-router 10.0.0.1
R1(dhcp-config)#exit
```
* Tại R2

```cisco
R2(config)#int g0/0
R2(config-if)#ip add 172.16.0.2 255.255.0.0
R2(config-if)#no shut
R2(config-if)#exit

R2(config)#int g0/1
R2(config-if)#ip add 192.168.20.1 255.255.255.0
R2(config-if)#no shut
R2(config-if)#exit

///Định tuyến cho Router R2
R2(config)#ip route 10.0.0.0 255.0.0.0 192.168.20.2
R2(config)#exit
```
* Tại R3
```cisco
R3(config)#int g0/1
R3(config-if)#ip add 10.0.0.1 255.0.0.0
R3(config-if)#no shut
R3(config-if)#exit

R3(config)#int g0/0
R3(config-if)#ip add 192.168.20.2 255.255.255.0
R3(config-if)#no shut
R3(config-if)#exit

///Định tuyến cho router R3
R3(config)#ip route 172.16.0.0 255.255.0.0 192.168.20.1

///Cấu hình DHCP Rely Agent
R3(config)#int g0/1                                     ///Cổng kết nối với mạng muốn được cấp DHCP

R3(config-if)#ip helper-address 172.16.0.1              ///IP của DHCP Server

R3(config-if)#exit
```

* 2 PC đã được cấp IP thành công

![](https://user-images.githubusercontent.com/52046920/184597110-04eac740-dcba-4318-935a-fca2017ade2d.png)

# ***VI.	Cấu hình chức năng DHCP Client trên Cisco Router***
* Cisco router vừa đóng vai trò làm DHCP Client và DHCP Server để. Khi nó đóng vai trò làm DHCP Client nó sẽ đi xin ip để gán vào cổng mà được cấu hình DHCP Client.

![](https://user-images.githubusercontent.com/52046920/184602354-99a56e6e-1f4f-48dd-b5e8-076a0759d18c.png)
* Cấu hình như sau

* R1
```cisco
R1(config)#int g0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit

///Cấu hình DHCP Server
R1(config)#ip dhcp pool Router-Interface
R1(dhcp-config)#network 192.168.1.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.1.1
R1(dhcp-config)#exit
```
* R2 
``` cisco

R2(config)#int g0/0
R2(config-if)#no shut
R2(config-if)#ip address dhcp

```

* Kiểm tra ip của cổng g0/0 tại R2 bằng 1 trong 2 câu lệnh
    * 
    ```cisco
    R2#show ip interface brief 
    ```

    ![](https://user-images.githubusercontent.com/52046920/184602268-072d2f3c-1e20-435c-ba4e-c8062e753aba.png)
    * 
    ```cisco
    R2#show dhcp lease
    ```

    ![](https://user-images.githubusercontent.com/52046920/184602270-7ecf3719-b9a7-4875-a1df-553e0e530f14.png)
* Khởi động lại quá trình xin ip bằng câu lệnh
```cisco
R2#release dhcp g0/0
R2#renew dhcp g0/0
```
# ***VII.	Khắc phục sự cố Conflict IP trên DHCP Server***
* Hiện tượng này xảy ra khi 1 thiết bị trong mạng đặt ip tĩnh mà chúng ta quên chưa cấu hình DHCP loại bỏ ip đó ra khỏi dải ip được cấp vậy nên DHCP vẫn sẽ cấp ip đó cho thiết bị khác và dẫn đến conflict khiến cho 2 máy bị trùng ip không thế kết nối ra ngoài mạng
* DHCP server trên Cisco Router có cơ chế tự động trước khi cấp ip cho máy tính nó sẽ kiểm tra ip này đã được cấp phát chưa bằng cách ping đến ip nó chuẩn bị sử dụng để cấp để kiểm tra xem đã có ai sử dụng ip này chưa. Nếu đã có người sử dụng nó sẽ chuẩn bị ip tiếp theo trong dải và tiếp tục tiến hành kiểm tra đến khi có ip không bị trùng thì nó sẽ sử dụng ip đó để cấp  cho máy tính yêu cầu

![](https://user-images.githubusercontent.com/52046920/184608880-20771271-c2c7-4417-a2e4-61ee5edb0fd7.png)

![](https://user-images.githubusercontent.com/52046920/184608875-ed4a55fb-8f16-4c9b-92fc-e880b4e219a2.png)
* Để khắc phục sự cố trên cách chủ động nhất chính là loại bỏ các ip được sử dụng để cài đặt tĩnh ra khỏi dải ip DHCP được cấp
```cisco
R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10      /// loại bỏ ip từ 192.168.1.1 đến 192.168.1.10 

R1(config)#ip dhcp excluded-address 192.168.1.254/// loại bỏ ip 192.168.1.254
```

* Các ip bị loại bỏ có thể kiểm tra trong running-config

* Kiểm tra ip bị conflict bằng câu lệnh
```cisco
R1#show ip dhcp conflict 

\\\Xóa danh sách này bằng câu lệnh
R1#clear ip dhcp conflict 
```

* Kiểm tra các ip đã được cấp bằng DHCP
```cisco
R1#show ip dhcp binding 
```

![](https://user-images.githubusercontent.com/52046920/184608884-c2426acf-a4d0-485d-854d-df11787afc1b.png)

