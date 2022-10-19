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
# [III. ESXi Networking - lab]()
## &ensp; [1. Tạo vSwitch]()
## &ensp; [2. Tạo VM Port Group]()
## &ensp; [3. Tạo VMkernel Port Group]()
## &ensp; [4. Thêm NIC hoặc Uplinks vào vSwitch để dự phòng]()
## &ensp; [5. Tuân thủ Chính sách kết nối vSwitch]()
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
    * vSwitch có khả năng tạo ra các VLAN, vSwitch không thể kết nối trực tiếp đến các vSwitch khác mà phải thông qua adapter vật lý

![](https://user-images.githubusercontent.com/52046920/196574516-342a6bf9-c3fb-41ef-aba9-4565e8a9cf7c.png)
# ***II.	Kiến trúc vSphere Standard Switch***
* Có thể tạo ra các thiết bị mạng ảo được gọi là vSphere Standard Switch. Standard Switch cung cấp kết nối mạng cho Host và các VM.

![](https://user-images.githubusercontent.com/52046920/196326534-f552ad83-22a1-44b5-89e6-ec7c9c7851ca.png)
* Để cung cấp kết nối mạng cho Server và các VM cần kết nối các NIC(Network Interface Card-Card mạng) vật lý của Server với các cổng Uplink(Uplink port là port kết nối từ LAN tới WAN) trên Standard Switch(Switch tiêu chuẩn). Các VMs có vNIC kết nối với các Group Port(nhóm cổng) trên vSphere Standard Switch. Mỗi Group Port có thể sử dụng 1 hoặc nhiều NIC vật lý để xử lý. Nếu 1 Group Port không có NIC vật lý kết nối đến thì chỉ có thể giao tiếp được bên trong nội bộ không giao tiếp được bên ngoài mạng

![](https://user-images.githubusercontent.com/52046920/196574517-277c0d80-58ec-494b-b6da-c37a66172362.png)
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

![](https://user-images.githubusercontent.com/52046920/196575346-3d82e518-5338-4cbf-abea-091954b0fc7d.png)

* Về mặt vật lý, các VLAN có thể được kết nối với các cổng mà host ESXi đã chỉ định.
* Tất cả các mạng có thể được hiển thị cho máy ảo khi thích hợp, nhưng vẫn duy trì tính bảo mật cần thiết trong doanh 
* vSwitch có 2 loại:
    * Standard Switch(VSS):Quản lý network các VMs ở mức độ host. Có sẵn trên ESXi, vSphere. Cấu hình switch ảo cho một host duy nhất.

    ![](https://user-images.githubusercontent.com/52046920/196578820-1c8071cc-ac80-493d-9a32-540534d7b3dc.png)
    * Distributed Switches(DVS): Quản lý network các VM ở mức độ Datacenter, dùng để quản lý tập trung(chỉ cần quản lý duy nhất 1 vSwitch từ máy chủ), không có sẵn trong vSphere.
        * Switch ảo được cấu hình cho toàn bộ data Center.
        * Có thể gắn tới 2.000 host trên cùng một Distributed switch.
        * Cấu hình nhất quán trên tất cả các host được đính kèm.
        * Các host phải có giấy phép Enterprise Plus hoặc thuộc cụm vSAN(Virtual Storage Area Network là 1 nền tảng ảo hóa lưu trữ dữ liệu từ VMware).

    ![](https://user-images.githubusercontent.com/52046920/196578822-851482dc-0851-493a-ab70-573b26b81fe0.png)
* Cả hai loại switch đều có tính elastic-đàn hồi (Flexible-Linh hoạt): các cổng được tạo và loại bỏ tự động.
    
# ***III. ESXi Networking - lab***
* Tạo vSwitch
* Tạo VM Port Group
* Tạo VMkernel Port Group
* Thêm NIC hoặc Uplinks vào vSwitch để dự phòng
* Tuân thủ Chính sách kết nối vSwitch


## ***1. Tạo vSwitch***
* Truy cập vào ESXi và click chọn `Networking`

![](https://user-images.githubusercontent.com/52046920/196585642-f8f8e15b-ae1a-426a-bf34-76a14c436722.png)
 
* Click tab `Virtual switches`

![](https://user-images.githubusercontent.com/52046920/196585646-1efcc6b2-b11b-4031-9336-2a3b090452e5.png)

* Có vSwitch0 là vSwitch được khỏi tạo mặc định sau khi cài đặt ESXi

![](https://user-images.githubusercontent.com/52046920/196585649-1570b896-028b-4504-9d57-f6aad21fdaa4.png)

* Để tạo thêm vSwitch khác click vào `Add standard virtual switch`

![](https://user-images.githubusercontent.com/52046920/196585650-59d19cac-994b-44cf-9ce5-01d6b97b0a9f.png)
* Đặt tên cho vSwitch rồi click `Add` để hoàn thành việc tạo vSwitch mới

![](https://user-images.githubusercontent.com/52046920/196585652-efffd56a-9315-45e0-8b66-309f0099834c.png)
## ***2. Tạo VM Port Group***
* Lựa chọn tab `Port groups` tại `Networking` sau đó click vào `Add port group`

![](https://user-images.githubusercontent.com/52046920/196585863-177c099e-6a48-4ea2-bf1f-84a49e7eb214.png)
* Đặt tên cho Port Group, lựa chọn vSwitch là vSwitch vừa tạo ở trên sau đó click `Add` để tạo

![](https://user-images.githubusercontent.com/52046920/196585655-53b62d14-20f2-47b6-91c8-76a3756e15ba.png)
* Port Group đã được tạo

![](https://user-images.githubusercontent.com/52046920/196585658-e1bb3f04-4275-4855-9185-12ac91b0e9ba.png)

## ***3. Tạo VMkernel Port Group***
* Click chuyển qua tab `VMkernel NICs`

![](https://user-images.githubusercontent.com/52046920/196585661-e1254852-dbea-4eb1-a398-35032f7c6497.png)
* Click `Add VMkernel NIC`

![](https://user-images.githubusercontent.com/52046920/196585663-6fc89b3e-3dd3-4300-a195-cd431a8c6f5d.png)
* Cửa sổ `Add VMkernel NIC` hiện ra

![](https://user-images.githubusercontent.com/52046920/196585665-ba9e460f-476b-42ac-ac3f-5901ae08410c.png)
* `Port group` Là các network label được kế thừa từ label của Group Port phân tán.

![](https://user-images.githubusercontent.com/52046920/196585667-76228e81-c94f-4d12-bfff-566007c96b56.png)
* Lựa chọn `IPv4 only` hoặc `IPv4 and IPv6`

![](https://user-images.githubusercontent.com/52046920/196587422-152d6366-a68b-4e54-80fb-feec965e68e8.png)
* lựa chọn :
    * `Default TCP/IP stack`: KHông thể thay đổi sau này nếu sử dụng lựa chọn này
    * `Provisioning stack`: 
    * `vMotion stack`: Chỉ có thể sử dụng ngăn xếp này để xử lý lưu lượng vMotion(là 1 tính năng cho phép 1 máy ảo đang chạy có thể di chuyển qua máy chủ vật lý khác mà không cần tắt nguồn, không có thời gian chết và không mất kết nối mạng ảo).

![](https://user-images.githubusercontent.com/52046920/196587416-7cccbae7-997a-482b-abb9-f55629e685c1.png)
* Lựa chọn các dịch vụ có sẵn:
    * `vMotion`: cho phép CMkernel tự quảng bá mình đến các host khác làm kết nối mạng nơi các vMotion traffic được gửi
    * `Provisioning`: Dữ liệu truyền qua cho VM cold migration(migration là quá trình di chuyển VM từ Host này qua Host khác, cold migration là quá trình di chuyển VM từ host này qua host khác khi VM đã được tắt), Cloning và di chuyển snapshot(snapshot migration)
    * `Fault tolerance logging`: Cho phép ghi Fault tolerance logging(log chịu lỗi) trên host
    * `Management`: Cho phép quản lý lưu lượng cho host và vCenter Server
    * `Replication`
    * `NFC replication`

![](https://user-images.githubusercontent.com/52046920/196585669-8333ea02-f180-4974-b8b6-c3930212f0eb.png)

![](https://user-images.githubusercontent.com/52046920/196593141-1f424db8-bb3e-4afe-a021-3964d7caa298.png)

![](https://user-images.githubusercontent.com/52046920/196593032-e4fd9aec-c7cd-49de-a9d6-c9b78134b2e8.png)
## ***4. Thêm NIC hoặc Uplinks vào vSwitch để dự phòng***
* Thêm card mạng cho VM ESXi

![](https://user-images.githubusercontent.com/52046920/196592792-2f386c14-c0c1-4db2-8b4f-2a8ac62a2761.png)

![](https://user-images.githubusercontent.com/52046920/196592797-c8f274d7-df22-4f07-942d-d79d0727c76f.png)

![](https://user-images.githubusercontent.com/52046920/196592800-f91e5d57-c9d3-4d1e-84e1-20acc3a2cf4a.png)

![](https://user-images.githubusercontent.com/52046920/196592801-c3fe06d3-0090-4666-8d4e-048d0db4b8ee.png)
* Thêm uplinks vào vSwitch để dự phòng. chọn vSwitch muốn thêm được uplinks

![](https://user-images.githubusercontent.com/52046920/196593896-da950d20-5fdc-438a-a824-14003e81bef7.png)
* Click `Add uplink`

![](https://user-images.githubusercontent.com/52046920/196593899-6b9b4b36-dda6-40e4-a9c5-5459d76541ce.png)
* Chọn NIC sau đó click `Save` để hoàn thành thêm uplink

![](https://user-images.githubusercontent.com/52046920/196593902-3699dbc8-0d08-4c73-bce3-b3e98d64130b.png)
* Nếu muốn có thêm uplink dự phòng thì phải thêm NIC và add thêm NIC vào các vSwitch. Ta sẽ thêm 2 NIC nữa vào VM ESXi. Ta sẽ thêm cho vSwitch0 và vSW1 mỗi vSwitch 1 uplink dự phòng

![](https://user-images.githubusercontent.com/52046920/196594722-fd996999-0790-482e-803b-a13caf577d1e.png)

![](https://user-images.githubusercontent.com/52046920/196594726-63a8242f-4b3e-434c-afa8-60feb3558810.png)
* Thêm Uplink cho vSwitch0, chọn vSwitch0

![](https://user-images.githubusercontent.com/52046920/196594731-3044292f-b3ef-48f5-ae7b-1d6b5cb5608a.png)
* `Add uplink`

![](https://user-images.githubusercontent.com/52046920/196594732-dd4a0706-db14-4983-b4b8-84b45506b2ac.png)
* Chọn đường uplink số 2 sau đó click `Save`

![](https://user-images.githubusercontent.com/52046920/196594736-40a8b9e4-cfe6-45fb-9487-6fd7a58ab9a7.png)
* Hoàn thành

![](https://user-images.githubusercontent.com/52046920/196594738-cc0b7829-f8b9-449f-8774-7e7e18461081.png)
* Tương tự với vSW1

![](https://user-images.githubusercontent.com/52046920/196594739-1669dce9-ff76-4c03-ac14-99437c64f378.png)
* Hoàn thành

![](https://user-images.githubusercontent.com/52046920/196594743-09f231b2-e9c2-47b5-836b-dd47c3afb0d2.png)
## ***5. Tuân thủ Chính sách kết nối vSwitch***
* Các chính sách của vSwitch0

![](https://user-images.githubusercontent.com/52046920/196595154-e13a6e14-a369-4f1f-bdbb-3617ee7d9bd2.png)
* Các chính sách của vSW1

![](https://user-images.githubusercontent.com/52046920/196595154-e13a6e14-a369-4f1f-bdbb-3617ee7d9bd2.png)


