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

# TÌM HIỂU VỀ STP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. STP là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#istp-l%C3%A0-g%C3%AC)
## &ensp; [1. Broadcast Storm](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#1broadcast-storm)
## &ensp; [2. Trùng lập Frame](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#2tr%C3%B9ng-l%E1%BA%ADp-frame)
# [II. Cơ chế chống Loop của công nghệ STP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#iic%C6%A1-ch%E1%BA%BF-ch%E1%BB%91ng-loop-c%E1%BB%A7a-c%C3%B4ng-ngh%E1%BB%87-stp)
## &ensp; [1. Chọn Root-Bridge của Giao thức Spanning Tree](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#1-ch%E1%BB%8Dn-root-bridge-c%E1%BB%A7a-giao-th%E1%BB%A9c-spanning-tree)
## &ensp; [2. Bầu chọn Root-port của Giao thức Spanning Tree](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#2-b%E1%BA%A7u-ch%E1%BB%8Dn-root-port-c%E1%BB%A7a-giao-th%E1%BB%A9c-spanning-tree)
## &ensp; [3. Bầu Chọn Designated port](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#3-b%E1%BA%A7u-ch%E1%BB%8Dn-designated-port)
## &ensp; [4. Alternate port(Block Port)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/13.STP/README.md#4-alternate-portblock-port)
# []()
# []()
# []()
# []()
***
# ***I.	STP là gì***
* STP viết tắt của Spanning Tree Protocol là một giao thức dùng để ngăn chặn sự lặp vòng của hệ thống. Là giao thức khoogn thể thiếu trong tầng Datalink(Layer 2).
##	***Lý do xảy ra lặp trong hệ thống***
* Trong 1 hệ thống mạng doanh nghiệp để tăng tính dữ phòng của mạng người ta thường đấu nối nhiều Switch lại với nhau, và 2 switch đấu nối với nhau cũng sẽ bằng 2 đường để nhằm mục đích tạo đường dự phòng cho đường dây chính. Chính việc này đã sinh ra vòng lặp
* Các switch khi đấu nối theo dạng Ring cũng sẽ là 1 nguyên nhân gây ra vòng lặp và còn nhiều nguyên nhân khác nữa có thể xảy ra vòng lặp nhưng chủ yếu là do tính toán dự phòng của doanh nghiệp.
* Các hình thức Loop khi không có giao thức STP
## ***1.	Broadcast Storm***
* Giả sử

![](https://user-images.githubusercontent.com/52046920/184801197-c0f300e3-c3f7-4cde-a690-a33f12b0372a.png)
* SW1 sẽ nối 2 đường đến SW2 1 đường chính và 1 đường dự phòng
* PC A tiến hành gửi 1 Broadcast frame vào hệ thống
* SW1 nhận frame này và đẩy qua tất cả các cổng của mình đến với SW2.
    * Frame đến với SW2 bằng đường 1 SW2 nhận frame và nhân bản nó lên rồi đẩy nó qua tất cả các cổng của chính nó trừ cổng vào và trong đó có cổng đến đường 2 nối giữa 2 SW vậy là frame lại quay lại SW1 và sau đó gói tin sẽ gửi đi gửi lại giữa 2 SW gây ra còng lặp.
    * Tương tự với việc Frame đến với SW 2 bằng đường 2 cũng xảy ra vòng lặp
* 2 SW này sẽ nhân bản frame này liên tục và gửi liên trục do bị lặp và đến khi SW hết tài nguyên không thế xử lý được thì nó sẽ bị treo dẫn đến hệ thống mạng bị ngắt

![](https://user-images.githubusercontent.com/52046920/184801193-47036757-f479-4d0e-abe6-2e153f359063.png)

## ***2.	Trùng lập Frame***
![](https://user-images.githubusercontent.com/52046920/184801197-c0f300e3-c3f7-4cde-a690-a33f12b0372a.png)
* PCA gửi một unicast frame đến PCB và địa chỉ MAC của B chưa được cập nhật vào bảng MAC của Sw thì Sw sẻ xử lý các frame này như một broadcast frame và flood ra tất cả các port trừ port nhận vào. Và Sw1 và Sw2 đều thực hiện chuyển flood frame này ra nhiều port khiến PCB phải xử lí frame này 2 lần.

## * Để đề phòng các trường hợp lặp có thể xảy ra thì STP được ra đời và giải quyết triệt để được vấn đề này


# ***II.	Cơ chế chống Loop của công nghệ STP***
* STP sử dụng khái niệm Block Port(Port dự phòng) để can thiệp vào quá trình bị lặp trong hệ thống mạng. Các Switch sẽ giao tiếp với nhau và quyết định Block Port để ngăn chặn quá trình lặp trong mạng.
* Port bị Block chỉ bị Block logic trên thực tế nó vẫn hoạt động tuy nhiên không nhận và truyền dữ liệu. Nó chỉ có thể sửu dụng khi có phân đoạn mạng liên kề với nó bị hỏng nó sẽ khởi động với vai trò đường dự phòng. Khi phân đoạn mạng được sửa chữa thì nó lại quay lại trạng thái ban đầu
* Tiến trình bầu chọn của Giao thức Spanning Tree sẽ gồm 4 bước:
    * Thực hiện bầu chọn Root-Bridge()
    * Bầu chọn Root-Port
    * Lựa chọn các Designated-Port
    * Blocking các Port còn lại
# ***1. Chọn Root-Bridge của Giao thức Spanning Tree***
* Khi STP được bật, các Switch sẽ gửi các gói tin BPDU(Bridge Protocol Data Unit) để trao đổi giữa các Switch. Gói tin này chứa Bridge-ID để định danh mỗi Switch tham gia STP.
* Bridge-ID dài 8byte:
    * Số Priority(2byte): có giá trị từ 0 – 65535 mặc định là 32768. Đây là trường ưu tiên và có thể cấu hình
    * MAC address(6byte)
* Tiến trình bầu chọn Root-Bridge:
    * So sánh Switch có Priority sẽ là Root-Bridge
    * Nếu các Switch được thiết lập số Priority bằng nhau(Không xác định được Root-bridge bằng Priorrity) thì so sánh MAC, MAC nhỏ nhất thì Switch được chọn làm Root-Bridge(So sánh từ trái qua phải địa chỉ MAC để biết được địa chỉ nào nhỏ hơn).

    ![](https://user-images.githubusercontent.com/52046920/184835219-36dadf83-3719-44ed-a31d-2c010bcec15f.png)
    * Sau khi được làm Root-Bridge thì Switch làm root gửi BPDU ra khỏi cổng để duy trì tiền trình STP(2s/lần). Các Switch còn lại chỉ nhận bổ sung BPDU và chuyển tiếp nó 

![](https://user-images.githubusercontent.com/52046920/184835208-5b94cfaa-14fd-48d9-afca-2ed89ff928c3.png)

* Root-Bridge sẽ đóng vai trò là điểm hội tụ toàn bộ lưu lượng của hệ thống mạng trước khi đi ra ngoại mạng
# ***2. Bầu chọn Root-port của Giao thức Spanning Tree***
* Root-Port là port có đường đến Root-bridge có tổng cost tích lũy nhỏ nhất(Gửi dữ liệu nhanh nhất đến Root-Bridge). Switch được chọn làm Root-bridge không tham gia vào quá trình này.
* là Port được chọn để gửi dữ liệu đến Root-Bridge do nó là port gửi dữ liệu nhanh nhất đến với Root-Bridge

* Bảng cost của 1 số loại interface Ethernet LAN

|Tốc độ|Cost|
|--|--|
|10Mbps|100|
|100Mbps|19|
|1Gbps|4|
|10Gpbs|2|

* Nguyên tắc tính tổng Root path-cost(RPC-là tổng cost của từng port): tính từ Root-Bridge đến switch đang muốn tính
    * Đi ra: không cộng
    * Đi vào: cộng cost
* RPC sẽ là tổng cost của các cổng phải đi ra cho đến khi đến được Root-Bridge Cổng nào có RPC thấp nhất sẽ được chọn là Root-Port của Switch
* Ví dụ từ SW3 về SW1 là Root-Bridge
    * Nó có 2 đường đi đến SW1
    * Giả sử đây đều là SW của cisco thì các cổng FastEthernet có giá trị cost mặc định bằng 19
    * Cổng Fa0/1 chỉ đi 1 lần là đến SW1 nên RPC =19
    * Cổng Fa0/2 phải đi ra 3 lần để đến được SW 1 vậy nên RPC tổng cost của 3 lần đó là RPC=19+19+19=57
    * 57<19 vậy nên chọn Fa0/1 làm Root Port của SW3

![](https://user-images.githubusercontent.com/52046920/184888556-7bf84249-b998-4553-b12a-8a108bb69e99.png)
* Khi RPC của các cổng bằng nhau thì ta sẽ sử dụng các tiêu chí khác:
    * Dựa vào Bridge-ID của thiết bị láng giếng. Đứng tại Switch đang xét Root-Port nếu RPC của các cổng bằng nhau thì ta xét Priority của Switch láng giếng. Priority của Switch nào thấp hơn thì cổng kết nối với Switch đấy sẽ được chọn. Ví dụ: Tại Switch 4 có 2 đường đến SW1 và RPC của cả 2 đều bằng 19+19=38 vậy nên xét ta phải xét đến Priority của SW3 và SW2 và nhận thấy SW3 có Priority nhỏ hơn của SW2 vậy nên Fa0/1 sẽ là Root-Port

    ![](https://user-images.githubusercontent.com/52046920/184888569-06e49462-b71a-44f4-acc3-812f135127e9.png)
    ![](https://user-images.githubusercontent.com/52046920/184888571-c3ee3762-876d-418e-b6af-cfe5766f5770.png)
    * Khi Bridge-ID của Switch láng giềng là bằng nhau thì ta xét tiếp tục đến Port-ID của các Switch láng giềng. Port nào mà kết nối vời Port của Switch láng giềng có Port ID thấp hơn thì sẽ được chọn làm Root-Port

![](https://user-images.githubusercontent.com/52046920/184888575-48099995-555b-4ed2-8cf8-d5d02b3e6221.png)
* Khi các luật trên không giải quyết được thì nó sẽ xét đến Port ID trên chính nó

* Thông thường các cổng nối trực tiếp đến với switch được chọn Root-Bridge sẽ là Root-Port



# ***3. Bầu Chọn Designated port***
* Là port cung cấp đường đến root-bridge có tổng cost nhỏ nhất trên phân đoạn mạng đang xét. Chỉ có một Designated port ứng với một link kết nối.
* Port này là Port được quyền gửi chuyển tiếp bản tin BPDU đi qua nó.
* Các Switch nối với nhau tạo ra bao nhiêu phân đoạn mạng thì sẽ có bấy nhiêu Designated port
* Port kết nối trực tiếp với Designated port ở Switch láng giềng sẽ là Alternated Port(BLoack Port)
* Cách xác định
    * Tất cả các Port của Switch được chọn làm Root-Bridge đều là Designated Port
    * Switch nào có RPC của Root-Port nhỏ hơn thì cổng của nó trên phân đoạn mạng đang xét sẽ là Designated port
    * Nếu RPC của Root-Port bằng nhau ta lại dựa vào Bridge-ID, Bridge-IDcủa Switch nào có Priority nhỏ hơn thì trên phân đoạn mạng đó Port của Switch đó sẽ là Designated port

# ***4. Alternate port(Block Port)***
* Port đối diện với Designated port mà không phải Root-port sẽ là Alternate port bị Block không có khả năng truyền nhận dữ liệu và sử dụng như 1 đường dự phòng.
* Khi 1 trong các phân đoạn khác liền kề với phân đoạn mạng chứa port block bị đứt thì phân đoạn mạng chứa port block sẽ được mở ra để chạy và khi sự cố được giải quyết thì nó sẽ trở về trạng thái khóa.
* Khi phân đoạn trên có lại thì phân đoạn block sẽ tiếp tục bị block lại
* Tuy port block không nhận được dữ liệu nhưng nó vẫn nhận gói tin BPDU từ Root-switch để duy trì cây spanning-tree.
* Nếu Root-Sw chết hay port block không nhận được BPDU thì mất 20s nó mới hoạt động (tự mở lên hoặc bầu chọn lại Root-sw) và nó sẽ mở ra cho dữ liệu đi qua

# ***III.	Chức năng PortFast và các trạng thái Port State trong STP***
* Các trạng thái khi switch khởi động diễn ra theo trình tự như sau:
    * Disable: down
    * Blocking: nhận BDPU> không gửi BPDU > không học MAC > không forward frame.
    * Leaning: nhận BDPU > gửi BPDU > học MAC > không forward frame.
    * Listening: nhận BDPU > gửi BPDU > không học MAC > không forward frame
    * Forwarding: nhận BDPU > gửi BPDU > học MAC > forward frame
* Tốc độ chuyển đổi trạng thái mặc định
    * Từ trạng thái Blocking sang Listening mất 20s.
    * Từ Listening sang Leaning mất 15s.
    * Từ Learning sang Forwarding mất 15s.

* Các timer của STP
    *  Helo timer: định kỳ sau thời gian 2s sẽ gửi BPDU
    * Forward timer: 15(s) là khoảng thời gian duy trì ở trạng thái learning trước khi chuyển qua trạng thái Listening hoặc learning trước khi chuyển qua trạng thái Forwarding
    * Max-age times: 20(s) Khoảng thời gian duy trì ở Blocking cho đến khi chuyển thành Listening khi không nhận được bản tin BDPU
* Các tham số trên đều có thể tinh chỉnh và nó sẽ ảnh hưởng đến các trạng thái. Nếu hiệu chỉnh tại Root-Bridge thì toàn bộ hệ thống sẽ sử dụng các timer được hiệu chỉnh tại đây
* Chức năng Port fast được sử dụng trên các port nối đến các PC và các thiết bi khác như máy in, camera,... . Chức năng này có khả năng bỏ qua các trạng thái ở trên 

# ***IV.	Giải pháp cân bằng tải lưu lượng của PVST+ trên các Cisco Switch***
* Giao thức PVST (PerVlan STP Plus) là một biến thể của giao thức STP là một giao thức tích hợp mặc định trên các sw của cisco.
* Đối với STP nó sẽ không thiết lập cho từng VLAN mã là toàn bộ hệ thống mạng vì vậy dẫn đến trường hợp như sau.

![](https://user-images.githubusercontent.com/52046920/185333245-e9115ad4-4864-4af9-9deb-2a48b86ba153.png)

* khi PC ở VLAN 10 và VLAN 20 muốn đi ra ngoài internet ví dụ ở đây cổng nối từ SW3 đến SW 2 sẽ là cổng BLock Port được chọn ra dựa vào STP và khi đó mọi dữ liệu từ cả 2 VLAN đi ra ngoài sẽ phải đi qua  SW1. Điều này dẫn đến tắc nghẽn đường đi từ SW3 đến SW1 do toàn bộ dữ liệu muốn đi ra ngoài sẽ phải đi qua đường này và lãng phí đường đi từ SW3 đến SW2. Và để giải quyết vấn đề này ta có PVST 

![](https://user-images.githubusercontent.com/52046920/185333241-eff600df-6848-4aa7-8c3a-4e86b5b3a343.png)
* Kỹ thuật này cơ bản là mỗi VLAN trên các SW này sẻ chạy một tiến trình STP độc lập với nhau. Có thể giúp người quản trị cân bằng tải và sử dụng đường truyền một cách tối ưu nhất. Nói đơn giản là nó sẽ tạo STP cho từng Vlan một và mỗi Vlan sẽ có đường đi riêng tránh gây lãng phí tài nguyên

![](https://user-images.githubusercontent.com/52046920/185333248-baa7303c-7574-44cd-87fe-f070f62b5ab0.png)

# ***V.	Hiệu chỉnh các giá trị của STP và PVST***

* Các câu lệnh sẽ được sử dụng
```cisco

///Kiểm tra các giá trị của STP trên SW
SW1# show spanning-tree

\\\Thiết lập priority cho vlan(mặc định các VLAN trên các SW là VLAN 1)
SW1(config)#spanning-tree vlan 1 priority 100       


\\\Show port ip và port priority, cost của post
SW1(config)#show spanning-tree interface f0/1


\\\chỉnh sửa lại cost của cổng đối với tùy vlan
SW1(config)interface f0/1
SW1(config-if)spanning-tree vlan 1 cost 8
```

* CHo mô hình sau

![](https://user-images.githubusercontent.com/52046920/185366402-2a5c5021-7e3c-4ece-9814-2272e21624e7.png)
* Thực hiện tùy chỉnh đường đi của các VLAN như trong hình

* Ta thiết lập
* Đầu tiên là tạo Vlan 10 và 20 ở tất cả các switch, tại SW4 và SW7 thì tạo trunk qua 2 SW6 và SW5, Tại SW6 và SW5 thiết lập Vlan cho từng cổng giống như hình vẽ và thiết lập ip cho các máy tính. Sau đó sẽ là bước thiết lập đường đi
* Tại SW4 sẽ là đường đi của VLAN 10 vậy nên thiết lập chỉ số Priority của vlan 10 thấp hơn priority của vlan 20
```cisco
SW4(config)#spanning-tree vlan 10 priority 4096
SW4(config)#spanning-tree vlan 20 priority 8192
```
* Các giá trị sau đây được gán cho priority

![](https://user-images.githubusercontent.com/52046920/185365824-361d10cb-6a65-4d32-a263-bba9efe8dad7.png)
* Tại SW7 sẽ là đường đi của VLAN 20 vậy nên thiết lập chỉ số Priority của vlan 20 thấp hơn priority của vlan 10
```cisco
SW4(config)#spanning-tree vlan 20 priority 4096
SW4(config)#spanning-tree vlan 10 priority 8192
```

* Ping từ PC5 đến PC4

![](https://user-images.githubusercontent.com/52046920/185365820-3ce423ed-f29e-45be-86fe-3cbf9a6028cf.png)
![](https://user-images.githubusercontent.com/52046920/185365817-b4f015af-f02a-49cb-b3d8-38cba96cd232.png)
![](https://user-images.githubusercontent.com/52046920/185365815-954b8ab2-6072-449a-bc9c-ad3e38f408de.png)
![](https://user-images.githubusercontent.com/52046920/185365811-9cb4c18f-4d03-47ce-9bc9-ea55a1779a56.png)
* Đã đi đúng đường thiết lập

* Ping từ PC6 đến PC7

![](https://user-images.githubusercontent.com/52046920/185365807-689b5843-1bd7-467b-935a-ecb933f1e305.png)
![](https://user-images.githubusercontent.com/52046920/185365804-2503b70b-075e-4878-a9ea-eb34c524e0b0.png)
![](https://user-images.githubusercontent.com/52046920/185365798-c96039c8-385d-40b1-b82f-b3a41f50dff9.png)
![](https://user-images.githubusercontent.com/52046920/185365793-c8953182-2bc1-4f82-b0ca-e08a339ef1da.png)
* Đã đi đúng đường thiết lập