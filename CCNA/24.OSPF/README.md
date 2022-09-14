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

# TÌM HIỂU VỀ OSPF
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. OSPF là gì]()
# [II. Cách thức hoạt động]()
# [III. Định dạng gói tin của OSPF, Các trạng thái của OSPF]()
## &ensp; [1. Định dạng gói tin OSPF]()

## &ensp; [2. Trạng thái của OSPF]()
# [IV. Ưu nhược điểm của OSPF]()
# [V. Cấu hình OSPF]()
## &ensp; [1. Cấu hình cơ bản]()

## &ensp; [2. Cấu hình chia các Area]()

## &ensp; [3. Default route]()
## &ensp; [4. Hiệu chỉnh metric]()

## &ensp; [5. Tùy chỉnh Router-ID]()

## &ensp; [6. Hiệu chỉnh Hello Timer và Dead timer(Hold Timer)]()
## &ensp; [7. Tiến trình bầu chọn DR,BDR và DROther]()

***
# ***I.	OSPF là gì***
* OSPF là viết tắt của Open Shortest Path First. Là 1 giao thức định tuyến nội vùng và là 1 giao thức link-state. Đây là 1 giao thức được sử dụng rộng rãi trong các mậng doanh nghiệp lớn.
* Mỗi router chạy OSPF sẽ gửi trạng thái link đến các router trong vùng(area). Sau khi trao đổi, các router đồng nhất dữ liệu trạng thái link(Link State Database-LSDB)với nhau. Sau đó router sẽ sử dụng giải thuật Dijkstra để tính ra đường đi ngắn nhất.

# ***II.	Cách thức hoạt động***
* 1 Router chạy OSPF sẽ thông qua các bước cơ bản sau:
    * Bước 1: chọn Router ID: người dùng phải tạo ra 1 định danh gọi là Router ID có 2 cách:
        * Cách 1: Router tự tạo định danh
        * Cách 2: Cấu hình định danh
    * Bước 2: Thiết lập quan hệ neighbors. Router thực hiện gửi gói tin hello đến các cổng chạy OSPF 10s/lần để tìm kiếm neighbors và thiết lập, duy trì quan hệ.Router được xếp làm neighbors nếu đáp ứng các điều kiện:
        * Cùng Area-ID
        * Cùng Subnet
        * Cùng thông số hello timer và hold timer(mặc định là 40s và 10s)
        * Cùng xác thực trên 2 cổng kết nối với nhau(mạng lớn)
        * Cùng MTU trên 2 cổng kết nối với nhau
    * Bước 3: Trao đổi LSDB(Link State Database)
    * Bước 4: Tính toán đường đi ngắn nhất bằng giải thuật Dijkstra. OSPF sử dụng Cost thay cho Metric. Cost chỉ tính đi vào không tính đi ra ở 1 cổng. Đường nào có metric thấp hơn sẽ được lựa chọn làm đường đi
* Về cơ bản thì có thể gói gọn cách thức hoạt động trên lại thành 3 bước chính là: 
    * 1. Tìm kiếm và xác lập quan hệ với neighbors
    * 2. Trao đôi LSDB
    * 3. Sử dụng thuật toán Djistra để tìm đường đi ngắn nhất
* Trong OSPF có 4 loại liên kết:
    * Point-to point link: Là liên kết điểm - điểm, kết nối trực tiếp giữa 2 router
    * Transient link: là liên kết tạm thời, có 2 cách triển khai:
        * Cấu trúc liên kết không thực tế: toàn bộ các router kết nối với nhau
        * Cấu trúc liên kết thực tế: một vài router được chỉ định trong mạng thực hiện kết nối với nhau. Các gói tin đuuợc router khác gửi đi sẽ chuyển qua router chỉ định
    * Stub link: hệ thống mạng có độc nhất 1 router
    * virtual link: liên kết ảo giữa các router

# ***III.	Định dạng gói tin của OSPF, Các trạng thái của OSPF***
# ***1. Định dạng gói tin OSPF***
* Gói tin của OSPF như sau

![](https://user-images.githubusercontent.com/52046920/189837256-745d0847-dbef-48b4-83db-f350200997cf.png)

* Version: Là trường 8 bit, giữ vai trò chỉ định phiên bản của giao thức định tuyến OSPF. 
* Type: Là trường 8 bit, giữ vai trò chỉ định loại gói OSPF.
* Message: Là trường 16 bit, giúp xác định độ dài của thông báo (kể cả header). 
* Source IP address: Thực hiện nhiệm vụ xác định địa chỉ IP của gói tin được gửi đi. 
* Area identification: Xác định khu vực diễn ra quá trình định tuyến. 
* Checksum: Thực hiện việc phát hiện lỗi và sửa lỗi.
* Authentication type: Có 2 loại xác thực là 0 và 1. Trong đó:
    * 0: Không có xác thực nào khả dụng.
    * 1: Chỉ định xác thực dựa vào mật khẩu. 
* Authentication: Là trường 32 bit, đóng vai trò chứa giá trị của dữ liệu xác thực.
* Gói tin OSPF có 5 loại:
    * Hello
    * Database Description
    * Link State Request
    * Link State Update
    * Link State Acknowledgment

|Gói tin|Chức năng|
|-|-|
|Hello|Sử dụng để thiết lập quan hệ neighbors|
|Database Description|Khi kết nối lần đầu nó sẽ gửi LSDB(Link State Database)|
|Link State Request|Được gửi để lấy thông tin của 1 route chỉ định|
|Link-State Update|Được sử dụng để quảng cáo trạng thái liên kết của router|
|Link State Acknowledgment|Xác nhận các bản cập nhật trạng thái liên kết|

# ***2. Trạng thái của OSPF***
* Thiết bị chạy OSPF sẽ có những trạng thái sau:
    * Down: quá trình OSPF chưa được bắt đầu
    * Init: Thiết bị đã nhận được gói Hello từ router khác
    * 2WAY: 2 Routẻ đã nhận được Hello từ Router khác và các kết nối được thiết lập giữa các Router.
    * Exstart: Khi 2 Router bắt đầu quá trình trao đổi thì Router sẽ chuyển qua trạng thái này(khởi động). Tại trạng thái này chủ và khách được chọn dựa trên ID của Router.
    * Exchange: 2 Router sẽ gửi danh sách các LSA cho nhau
    * Loading: Các LSR(Link state request), LSU(Link State Update) và LSA(Link state Acknowledgment) được trao đổi
    * Full: Sau khi hoàn tất trao đổi thì các Router sẽ chuyển qua trạng thái này

# ***IV.	Ưu nhược điểm của OSPF***
* Ưu điểm: 
    * Mỗi Router sẽ đồng bộ cấu trúc mạng nên khó bị lặp
    * Hỗ trợ VLSM(Variable Length Subnet Masking - kỹ thuật chia nhỏ mạng) và CIDR(Classless Inter Domain Routing - 1 phương pháp định vị địa chỉ IP).
* Nhược điểm:
    * Tốn tài nguyên bộ nhớ, cần năng lực xử lý cao nên chi phí đầu tư cũng khá cao
    * Hệ thông phải chia thành nhiều vùng nhỏ để giảm độ phức tạp và độ lớn của LSDB.
    * Người quản trị phải nắm rõ được giao thức 
# ***V.	Cấu hình OSPF***
## ***1. Cấu hình cơ bản***
* Câu lệnh cấu hình
```cisco
R1(config)#router ospf [id ospf]
R1(config-router)#network [mạng tham gia định tuyến] [Wildcard] area [id area]

//Cấu hình cho interface tham gia OSPF
R1(config-router)#network [IP của interface tham gia định tuyến] 0.0.0.0 area [id area]

// Câu lệnh cấu hình interface tham gia OSPF cách 2
R1(config)#int g0/0
R1(config-if)#ip ospf [id ospf] area [id area]

/// Để tất cả các cổng giao tiếp tham gia vào OSPF cấu hình như sau
R1(config-router)#network 0.0.0.0 255.255.255.255 area [id area]

///ví dụ
R1(config)#router ospf 1
R1(config-router)#network 192.168.1.0 0.0.0.255 area 0
R1(config-router)#network 192.168.2.0 0.0.0.255 area 0

R1(config)#int g0/0
R1(config-if)#ip ospf 1 area 0

```
## ***2. Cấu hình chia các Area***
* Việc chia Area giúp topology của Router tham gia OSPF hạn chế được tài nguyên
* Area Border Router Là một Router trung gian chứa toàn bộ topology của các Router khác và nó sẽ là một Router được đầu tư tài nguyên nhất. Các router nếu muốn kết nối qua mạng khác mà topology của nó không có thì phải liên hệ với Area Border Router.
* Ví dụ

![](https://user-images.githubusercontent.com/52046920/189837261-a4552114-7345-4775-8e67-5557335b8a57.png)
* Trong 1 mạng như trên nểu R1 có 100 route và R2 có 50 route thì để định tuyến thì R1 và R2 sẽ phải thuộc cùng 1 Area và phải lưu trữ toàn bộ route của nhau là 150 route vậy nếu mạng lớn hơn thì tài nguyên phải đầu tư cho Router là cực kỳ lớn

![](https://user-images.githubusercontent.com/52046920/189837266-2a491af2-f4fe-49b8-bcfb-e4a4bb2485cf.png)
* Tuy nhiên nếu sử dụng Area Border Router và chỉa nhỏ các area thì ta chỉ cần đầu tư cho Area Border Router là chủ yếu các router còn lại sẽ chỉ cần lưu trữ các route của chính mình mà thôi

![](https://user-images.githubusercontent.com/52046920/189838082-f5b4077e-4808-43c3-8855-0811b5c19e33.png)

* Để cấu hình thì tải Router ABR ta sẽ cấu hình cho Router này thuộc 2 Area
```cisco
R1(config)#router ospf 1
R1(config-router)#network 192.168.1.1 0.0.0.0 area 0
R1(config-router)#network 192.168.2.1 0.0.0.0 area 1
```
* Vậy là R1 dù không thuộc Area 1 tuy nhiên vẫn có thể học được các route của Area 1 thông qua Router ABR và R2 dù không thuộc Area1 tùy nhiên vẫn có thể học được các route của Area 0 thông qua Router ABR. Do vậy ta cần đầu tư về mặt tài nguyên cho Router ABR để nó có thể chứa được nhiều Area mà không cần phải đầu tư đều cho các Router khác nếu như không dùng cách thức này.

* Sau khi cấu hình xong phải reset lại prosess của tất cả các router để nó có thể nhận cấu hình.
```cisco
R1#clear ip ospf process 
Reset ALL OSPF processes? [no]: y
```
## ***3. Default route***

![](https://user-images.githubusercontent.com/52046920/189852480-70af5fa6-472a-4501-9b60-721fbd583826.png)
* Sử dụng câu lệnh sau để cấu hình default route
```cisco
R1(config)#ip route 0.0.0.0 0.0.0.0 g0/0

/// Cấu hình OSPF định tuyến default route
R1(config)#router ospf 1
R1(config-router)#default-information originate
```
* Sau khi cấu hình xong phải reset lại prosess của tất cả các router để nó có thể nhận cấu hình.
```cisco
R1#clear ip ospf process 
Reset ALL OSPF processes? [no]: y
```
## ***4. Hiệu chỉnh metric***
* Hiệu chỉnh metric giúp ta có thể điều chỉnh, bẻ hướng đi của gói tin theo ý muốn 
* Cách tính metric:
    * Metric = tổng cost từ ngồn cho đến đích, chỉ tính cổng đi ra không tính cổng đi vào
    * Cost = preference Bandwidth/Interface Bandwidth
    * Mặc định Cost = $ 10^{8} $/Bandwidth(bps)

ví dụ:

![](https://user-images.githubusercontent.com/52046920/189869473-20b1838e-c8dc-4dbb-b79b-370d0162c1ac.png)

* Đường nào có metric thấp hơn sẽ được lựa chọn làm đường đi

* Hiệu chỉnh cost bằng câu lệnh
```cisco
R1(config)#int g0/1
R1(config-if)#ip ospf cost 10
```
* Kiểm tra metric
```cisco
R1#show ip ospf interface g0/0
```
* Khi metric của 2 đường đi đều bằng nhau thì có thể sử dụng cả 2 đường để truyền dữ liệu
* Hiệu chỉnh preference Bandwidth
```cisco
R1(config)#router ospf 1
R1(config-router)auto-cost reference-bandwidth 1000

///100 là mặc định và 1000 ở đây có giá trị là 1000mbs
```
* Sau khi cấu hình xong phải reset lại prosess của tất cả các router để nó có thể nhận cấu hình.
```cisco
R1#clear ip ospf process 
Reset ALL OSPF processes? [no]: y
```
## ***5. Tùy chỉnh Router-ID***
* Router ID nhằm đánh dấu các route được gửi đi để khi router nguồn nhận được route thì nó sẽ nhận ra Router ID của mình nên route mà nó nhận được ứng với Router ID này là route của chính nó rồi vậy nên nó sẽ không học nữa
* Các Router ID đã được thiết lập sẵn nhưng nếu như ta muốn tự thiết lập Router ID theo ý mình thì có thể thực hiện câu lệnh sau
```cisco
R1(config)#router ospf 1
R1(config-router)router-id 0.0.0.2
```
* lưu ý không được cấu hình 2 Router có Router ID giống nhau vì điều này dẫn đến việc 2 Router sẽ không học được route của nhau
* Nếu không cấu hình Router ID thì Router ID sẽ chọn trên các interface của Router giá trị IP cao nhất làm Router ID
* Kiểm tra Router ID
```cisco
R1#show ip ospf
```

![](https://user-images.githubusercontent.com/52046920/189869479-a760914e-7d5f-4309-af10-cb57f1e41ba1.png)
* Sau khi cấu hình xong phải reset lại prosess của tất cả các router để nó có thể nhận cấu hình.
```cisco
R1#clear ip ospf process 
Reset ALL OSPF processes? [no]: y
```
## ***6. Hiệu chỉnh Hello Timer và Dead timer(Hold Timer)***
* Định kỳ 10s(Hello Timer) Router sẽ gửi gói tin cho Neighbors của mình, tuy nhiên khi có sự cố và sao 40s(Dead Timer) không nhận được gói tin từ neighbors Router sẽ hủy quan hệ neighbors và xóa toàn bộ route học được từ router gặp sự cố
* Cấu hình bằng câu lệnh như sau
```cisco
R1(config)#int g0/0
R1(config-if)#ip ospf hello-interval 10
R1(config-if)#ip ospf dead-interval 40

///Mặc định hello-timer là 10s và dead-timer là 40s
```
### ***Chú ý***: Các Timer này đều phải được đồng bộ trên toàn bộ các Router trong mạng vì đây là điều kiện tiên quyết nằm trong 5 điều kiện thiết lập neighbors 

## ***7. Tiến trình bầu chọn DR,BDR và DROther***
* DR là Designated Router, BDR là Backup Designated Router và DROther là Designated Router Other.
* DR là 1 Router được chọn để đứng ra đóng vai trò làm nơi các Router khác trao đổi thông tin với nhau. 
* BDR là Backup Designated Router, đúng như tên gọi nó là 1 Router để Backup cho DR khi DR gặp sự cố
* Trong môi trường Point-To-Point thì các Router kết nối trực tiếp với nhau nên không cần 1 Router đứng ra làm DR, vậy nên cũng không có BDR

![](https://user-images.githubusercontent.com/52046920/190057615-8872fc65-52dc-4156-81d8-f048a31e8948.png)
* Trong môi trường Broadcast Multiaccess cần 1 Router đứng ra đóng vai trò làm DR làm nơi trung chuyển thông tin cho các Router trong mạng. Điều này giúp hạn chế được được tài nguyên của mạng. Khi DR gặp sự cố BDR sẽ đứng lên thay thế cho DR và các DROther se trở thành BDR. 

![](https://user-images.githubusercontent.com/52046920/190051893-fa794554-7d71-416f-9da2-28f1f9b9db7f.png)
* Việc bầu chọn DR dựa vào các chỉ số sau:
    * Priority(Mặc định là 1 nếu không hiệu chỉnh)
    * Nếu các priority bằng nhau thì nó sẽ căn cứ vào Router ID để xác định DR
* Router có chỉ số priority, hoặc Router ID cao nhất thì được chọn là DR. tiếp theo là BDR và cuối cùng là DROther

![](https://user-images.githubusercontent.com/52046920/190051887-da46c7ec-49c6-4a50-9da5-d6edcf11a486.png)

![](https://user-images.githubusercontent.com/52046920/190051890-30c95106-10ed-48e2-94be-8ae3a9b5b9ff.png)
* Khi DR gặp sự cố BDR sẽ đứng lên thay thế cho DR và các DROther se trở thành BDR. Tuy nhiên nếu DR cũ được khôi phục thì nso chỉ còn có thể đóng vai trò là DROther do trong giao thức này các thiết bị được kết nối vào mạng sau dù có đủ điều kiện thì cũng chỉ có chức năng DROther.

![](https://user-images.githubusercontent.com/52046920/190052998-b2e0a5fd-2df3-4df5-9658-35e60aa8187e.png)
* Muốn Router khôi phục lại chức năng ban đầu thì ta phải reset lại các tiến trình của giao thức OSPF bằng câu lệnh
```cisco
R#clear ip ospf process
```
* Hiệu chỉnh giá trị priority bằng câu lệnh 
```cisco
R1(config)#int g0/0
R1(config-if)ip ospf priority 30
```
* Kiểm tra trạng thái và nhiệm vụ của Router bằng câu lệnh
```cisco
R2#show ip ospf neighbor 
```

* Ví dụ

![](https://user-images.githubusercontent.com/52046920/190060951-f2c5e837-4ca7-4d54-8484-7129cc25d800.png)

||g0/0|g0/1|
|-|-|-|
|R1|null|192.168.3.1|
|R3|192.168.3.2|192.168.10.1|
|R4|192.168.3.3|192.168.30.1|
* Cấu hình cho Router1 làm DR Router4 làm BDR và Router3 là DROther
* Tại R1
```cisco
R1(config)#router ospf 1
R1(config-router)#network 192.168.3.0 0.0.0.255 area 0

///Hiệu chỉnh priority của cổng kết nối với Router3 và Router4
R1(config-router)#exit
R1(config)#int g0/1
R1(config-if)#ip ospf priority 30
```
* Tại R3
```cisco
R3(config)#router ospf 1
R3(config-router)#network 192.168.3.0 0.0.0.255 area 0
R3(config-router)#network 192.168.10.0 0.0.0.255 area 0

///Hiệu chỉnh priority của cổng kết nối với Router1 và Router4
R3(config-router)#exit
R3(config)#int g0/1
R3(config-if)#ip ospf priority 1
```
* Tại R4
```cisco
R4(config)#router ospf 1
R4(config-router)#network 192.168.3.0 0.0.0.255 area 0
R4(config-router)#network 192.168.30.0 0.0.0.255 area 0

///Hiệu chỉnh priority của cổng kết nối với Router1 và Router3
R4(config-router)#exit
R4(config)#int g0/1
R4(config-if)#ip ospf priority 20
```
* Do không cấu hình Router ID nên là Router ID sẽ được tự động lựa chọn là IP cao nhất nên ta có

|Router|RouterID|
|---|---|
|R1|192.168.3.1|
|R3|192.168.10.1|
|R4|192.168.30.1|
* Kiểm tra
    * Tại R1 nhận thấy R3 là DROTHER R4 là BDR

    ![](https://user-images.githubusercontent.com/52046920/190059638-b5a5ec1b-082a-4bcb-a6e2-8212fe8d27fb.png)
    * Tại R2 nhận thấy R3 là DROTHER R1 là DR
 
    ![](https://user-images.githubusercontent.com/52046920/190059643-5863fda8-6d80-43b4-931d-1549f99d6645.png)
    * Tại R3 nhận thấy R1 là DR R4 là BDR

    ![](https://user-images.githubusercontent.com/52046920/190059647-581ebc46-d99a-4fa6-8e3c-e5b8859d628a.png)
* Để tự kiểm tra vai trò của mình sử dụng câu lệnh

```cisco
R1# show ip ospf interface g0/1
```
* Tại R1

![](https://user-images.githubusercontent.com/52046920/190062641-db65cc0e-847d-4eba-8542-170511cd673a.png)
* Tại R3

![](https://user-images.githubusercontent.com/52046920/190062634-c24bf132-57df-4860-973d-e3036cedd0dd.png)
* Tại R4

![](https://user-images.githubusercontent.com/52046920/190062639-eee5f7f2-0cbe-4ec2-9258-02c7d6d1c08f.png)



*  Thiết lập 2 Router kết nối với nhau với môi trường Point-To-Point bằng câu lệnh
```cisco
R1(config)#int g0/0
R1(config-if)#ip ospf network-type point-to-point
```
* Ví dụ: 

![](https://user-images.githubusercontent.com/52046920/190058543-e308ff2b-2c70-4b2f-a97c-c7e44463cb12.png)
* Cấu hình 2 Router sau kết nối với nhau với môi trường Point-To-Point
* Tại R1
```cisco
R1(config)#router ospf 1
R1(config-router)#network 192.168.1.0 0.0.0.255 area 0
R1(config-router)#network 123.0.0.0 0.255.255.255 area 0

R1(config)#int g0/0
R1(config-if)#ip ospf network-type point-to-point
```
* Tại R2
```cisco
R2(config)#router ospf 1
R2(config-router)#network 10.0.0.0 0.255.255.255 area 0
R2(config-router)#network 123.0.0.0 0.255.255.255 area 0

R2(config)#int g0/0
R2(config-if)#ip ospf network-type point-to-point
```
* Kiểm tra 
```cisco
R2#show ip ospf neighbor 
```

![](https://user-images.githubusercontent.com/52046920/190057615-8872fc65-52dc-4156-81d8-f048a31e8948.png)