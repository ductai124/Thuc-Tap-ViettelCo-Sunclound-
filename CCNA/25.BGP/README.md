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

# TÌM HIỂU VỀ BGP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. BGP là gì]()
# [II. Chức năng và cách thức hoạt động của BGP]()
## &ensp; [1. Chức năng]()
## &ensp; [2. Phương thức hoạt động]()
# [III. Cấu hình]()
## &ensp; [1. Cấu hình thiết lập neighbors]()
## &ensp; [2. Hiệu chỉnh Hello timer và dead timer]()
## &ensp; [3. Hiệu chỉnh TTL để thiết lập neighbors khi không kết nối trực tiếp]()
## &ensp; [4. Quảng bá các route]()
## &ensp; [5. eBGP và iBGP]()

***
# ***I.	BGP là gì***
* Là một giao thức định tuyến động kết nối Internet với nhau. 
* Là giao thức đang được hệ thống mạng Internet toàn cầu sử dụng để định tuyến giữa các nhà cung cấp mạng, AS(Automatic System) khác nhau. Tùy nhiên cũng có thể sử dụng BGP trong 1 vùng AS
* Có 2 loại BGP
    * External BGP(eBGP) được sử dụng giữa các AS
    * Internal BGP(iBGP) được sửu dụng trong cùng 1 AS
* Các khái niệm, chỉ số của BGP:
    * Sử dụng cổng 179 trao đổi thông tin
    * Giá trị AD là 20 đối với eBGP và là 200 đối với iBGP
    * Các Router chỉ có thể chạy 1 BGP tại 1 thời điểm
    * BGP là 1 giao thức kiểu Path-vector. Đường đi của nó đến 1 mạng gồm danh sách các AS
    * Các BGP Neighbors được gọi là các Peers phải được cấu hình tĩnh
    * BGP có 1 cơ chế chống loop là ASN (Autonomous System Number). Khi có Update của 1 mạng đi ra khỏi AS, ASN của AS đó được gửi kèm theo, Khi AS khác nhận Update, nó kiểm tra trong ASN list, nếu ASN là của chính nó thì update sẽ bị xóa.
* BGP Database có 3 loại:
    * Neighbors database: danh sách tất cả BGP láng giềng được cấu hình.
    * BGP database hay RIB(Routing infomation Base): danh sách các mạng mà BGP biết kèm theo đường đi(paths)và thuộc tính(attributes)
    * Routing table: bảng định tuyến
* Các thông điệp BGP:
    * Open: để thiết lập kết nối BGP láng giềng (Peers)
    * Update: Sử dụng để trao đổi thông tin route giữa các Peers
    * Keepalive: Các Peers trao đổi thông tin này định kỳ 60s đồng thời chúng giữ phiên làm việc giữa các Peers được active
    * Notification: thông điệp này được gửi thông báo router kết thúc phiên BGP và ngắt kết nối.
# ***II.	Chức năng và cách thức hoạt động của BGP***
## ***1. Chức năng***
* BGP thực hiện 3 chức năng:
    * Thu thập và xác thực các Peers. Thực hiện trao đổi thông điệp đảm bảo rằng đồng ý giao tiếp
    * Gửi thông tin khả năng tiếp cận tiêu cực hoặc tích cực
    * Xác minh các Peers và kết nối mạng giữa chúng đang hoạt động chính xác
* Các chức năng quản lý thông tin tuyến đường:
    * Lưu trữ: BGP lưu thông tin cách tiếp cận các mạng khác
    * Cập nhập: Cập nhập các route
    * Lựa chọn route: Dựa vào thông tin trong database chọn đường đi tốt nhất
    * Quảng bá route: BGP thương xuyên trao đổi với Peers về các mạng và phương pháp tiếp cận các mạng đó.
## ***2. Phương thức hoạt động***
* Các Router sử dụng BGP kết nối thành từng cặp bằng cách thiết lập phiên làm việc thông qua cổng 179 TCP. Phiên duy trì bằng cách gửi các thông điệp keepalive định kỳ 60 giây.
* Thứ tự ưu tiên của cơ chế tìm đường:
    * Chọn đường đi tường minh trong bảng trước(so với đường đi mặc định)
    * Chọn đường đi có trọng số cao nhất (weight) (chỉ với router của Cisco)
    * Chọn đường đi có độ ưu tiên cục bộ cao nhất (local preference)
    * Chọn đường đi do chính người quản trị mạng cài đặt trên router (static route, có thuộc tính origin là INCOMPLETE)
    * Chọn đường đi đi qua ít AS nhất (AS path ngắn nhất)
    * Chọn đường đi có nguồn gốc bên trong trước (origin = IGP < EGP)
    * Chọn đường đi có độ ưu tiên gần/xa thấp nhất MED (Multi exit discriminator)
    * Chọn đường đi ra bên ngoài trước (external path)
    * Chọn đường đi có độ đo IGP đến hop tiếp theo thấp nhất (IGP metric to the next hop)
    * Chọn đường đi tồn tại trong bảng lâu nhất (oldest one)
    * Chọn đường đi đến router tiếp theo có BGP ID thấp nhất

# ***III.	Cấu hình***
* Pulbic AS numbers: 1-64 495 được sử dụng trên mạng Internet toàn cầu. Sử dụng cho eBGP
* Private AS numbers: 64 512-65 534 được sử dụng trọng nội vùng. Được sử dụng khi có doanh nghiệp muốn sử dụng iBGP với mạng nội bộ của mình
## ***1. Cấu hình thiết lập neighbors***
* Câu lệnh cấu hình eBGP thiết lập mối quan hệ neighbors giữa 2 thiết bị
```cisco
R1(config)#router bgp [AS mà Router tham gia]
R1(config-router)#neighbor [Địa chỉ IP] remote-as[AS láng giềng]
```
* Ví dụ:
![](https://user-images.githubusercontent.com/52046920/190575010-df20f97f-5a7f-4c50-a879-abf19353bb98.png)

* Tại R1
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.2 remote-as 2
```
* Tại R2
```cisco
R2(config)#router bgp 20
R2(config-router)#neighbor 9.0.0.1 remote-as 10
```
* Kiểm tra thiết lập neighbors
```cisco
R1#show ip bgp summary
```

![](https://user-images.githubusercontent.com/52046920/190573548-da7298c6-43b6-493f-88ed-e7b5c9624d30.png)

![](https://user-images.githubusercontent.com/52046920/190573515-303e2ace-02fc-444f-928c-62baa6d3fbed.png)
* Khi chưa thiết lập Router ID thì Router sẽ nhận ip cao nhất làm Router ID
* Thiết lập Router-ID
* Tại R1
```cisco
R1(config)#router bgp 10
R1(config-router)#bgp router-id 9.0.0.1
```
* Tại R2
```cisco
R2(config)#router bgp 20
R2(config-router)#bgp router-id 9.0.0.2
```
* Kiểm tra

![](https://user-images.githubusercontent.com/52046920/190573521-8d693a94-cc63-4db6-a69c-5d61c6a43446.png)

![](https://user-images.githubusercontent.com/52046920/190573519-058a5b7d-c9bf-450c-87b0-ec169c8e3174.png)
* Ngoài ra còn có thể thiết lập quan hệ láng giềng 2 Router bằng nhiều đường (Multi-link). 
* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/190577187-8bb27b60-6d5c-49f9-b0a8-5ffcb924f753.png)
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.2 remote-as 20
R1(config-router)#neighbor 11.0.0.2 remote-as 20

R2(config)#router bgp 10
R2(config-router)#neighbor 9.0.0.1 remote-as 10
R2(config-router)#neighbor 11.0.0.1 remote-as 10
```
* Do có Router ID đánh dấu nên lặp sẽ không xảy ra ở trường hợp này
## ***2. Hiệu chỉnh Hello timer và dead timer***

* Câu lệnh hiệu chỉnh hello timer và dead timer như sau
```cisco
R2(config)#router bgp 20
R2(config-router)#timer bgp [hello-timer] [dead-timer]

///ví dụ
R2(config-router)#timer bgp 30 60
```
* Mặc định của hello timer là 60s và dead timer(hold timer) là 180s
## ***3. Hiệu chỉnh TTL để thiết lập neighbors khi không kết nối trực tiếp***
* Trong trường hợp khi R1 và R2 bị ngăn cách bởi 1 router mà vẫn muốn thiết lập neighbor cho chúng thì ta phải điều chỉnh lại TTL trong cấu hình AS.

![](https://user-images.githubusercontent.com/52046920/190573525-73af1377-13e0-4812-99f0-40ac27ec7fa3.png)
* Trong trường hợp TTL mặc định sẽ = 1. 2 neigbors muốn thiết lập quan hệ với nhau thì mặc định phải gửi gói tin hello định kỳ 60 giây cho nhau. Tuy nhiên TTL mặc định là 1. 

![](https://user-images.githubusercontent.com/52046920/190573530-c828341a-3948-4d69-b2ac-d4c7818976c7.png)
* TTL khi đi qua 1 Router nó sẽ giảm xuống 1 chỉ số, và nếu TTL=0 gói tin sẽ bị hủy. Trong trường hợp trên gói tin hello sau khi đi đến R3 TTL mặc định sẽ giảm xuống 1 chỉ số và bằng 0 nên R3 sẽ nhận gói tin hủy gói tin hello của R1. Gói tin hello không thể đến được R2 nên không thể thiết lập quan hệ Neighbors giữa R1 và R2.

![](https://user-images.githubusercontent.com/52046920/190573534-db804d4c-21b9-4ffe-9d2f-527e0ec7a680.png)
* Vậy để R2 có thể nhận được gói tin của R1 thì TTL của R1 phải bằng 2 và ngược lại

* Câu lệnh để cấu hình TTL trong BGP là 
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 11.0.0.1 ebgp-multihop 2

R2(config)#router bgp 10
R2(config-router)#neighbor 9.0.0.1 ebgp-multihop 2
```

* Ví dụ: 

![](https://user-images.githubusercontent.com/52046920/190573535-8dba3182-e645-4385-a438-4863390cb09f.png)
* Cấu hình cho R1 và R2 thiết lập neighbors
* Tại R1
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 11.0.0.1 remote-as 20
```
* Tại R2
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.1 remote-as 10
```
* Tạm thời định tuyến tĩnh cho R1 và R2 để cho phép gói tin được gửi từ R1 đến R2
* Khi chưa cấu hình TTL cho R1 và R2 nó sẽ chưa xác nhận và thiết lập liên kết neighbors với nhau

![](https://user-images.githubusercontent.com/52046920/190573537-466ad23c-398c-4528-8e27-c3b1da029e95.png)
![](https://user-images.githubusercontent.com/52046920/190573537-466ad23c-398c-4528-8e27-c3b1da029e95.png)

* Cấu hình TTL cho R1 và R2 thiết lập môi quan hệ neighbors
* Tại R1
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 11.0.0.1 ebgp-multihop 2
```
* Tại R2
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.1 ebgp-multihop 2
```
* Kiểm tra

![](https://user-images.githubusercontent.com/52046920/190573544-bb2dcbd8-9d87-4b12-9050-b3e3a0fc17a7.png)

![](https://user-images.githubusercontent.com/52046920/190573545-a3cffc37-c1e5-4e2a-867b-67cb5070dfdc.png)

## ***4. Quảng bá các route***
* BGP chỉ quảng bá mạng nào đã có trong routing table
* Câu lệnh cấu hình quảng bá route của BGP như sau
```cisco
R1(config)#router bgp 10

R1(config-router)#network [route muốn quảng bá] mask [subnet mask]

```

* Cho ví dụ

![](https://user-images.githubusercontent.com/52046920/190575010-df20f97f-5a7f-4c50-a879-abf19353bb98.png)

* Cấu hình quảng bá route của R1 và R2 cho nhau
* Tại R1
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.2 remote-as 2
R1(config-router)#network 192.168.1.0 mask 255.255.255.0

```
* Tại R2
```cisco
R2(config)#router bgp 20
R2(config-router)#neighbor 9.0.0.1 remote-as 10
R2(config-router)#network 192.168.2.0 mask 255.255.255.0
```

* Kiểm tra

![](https://user-images.githubusercontent.com/52046920/190581716-e443b931-b43f-49e3-916b-2ab4ff0213ec.png)

![](https://user-images.githubusercontent.com/52046920/190581725-20f91b3b-be8c-465b-95a5-b7db7fcfd5f0.png)

* Quảng bá route summary

Ví dụ

![](https://user-images.githubusercontent.com/52046920/190586789-57853a51-5bfa-4733-9653-a1a64809bb21.png)

* Muốn quảng bá 4 mạng của AS 20 ta chỉ cần gom thành 192.168.0.0/18
```cisco
R2(config)#router bgp 20
R1(config-router)#aggregate 192.168.0.0 255.255.0.0 summary-only
``` 
* Phải có câu lệnh summary-only để nó không quảng bá 4 mạng con nữa mà nó chỉ quảng bá 1 192.168.0.0/18 đại diện cho 4 mạng con mà thôi tránh việc routing table bị ghi quá nhiều route
* Hoặc có thể quảng bá mạng summary bằng cách
```cisco
R2(config)#ip route 192.168.0.0 255.255.0.0 null0

///do BGP chỉ quảng bá mạng nào đã có trong routing table
R2(config)#router bgp 20
R1(config-router)#network 192.168.0.0 mask 255.255.0.0
```
## ***5. eBGP và iBGP***

![](https://user-images.githubusercontent.com/52046920/190606429-85284113-09c1-49c6-b859-dee6b239700e.png)
* R1
```cisco
R1(config)#router bgp 10
R1(config-router)#neighbor 9.0.0.2 remote-as 20
R1(config-router)#network 192.168.10.0 mask 255.255.255.0
```
* R2
```cisco
R2(config)#router bgp 20
R2(config-router)#neighbor 9.0.0.1 remote-as 10
R2(config-router)#neighbor 10.0.0.2 remote-as 20

```
* R3
```cisco
R3(config)#router bgp 20
R3(config-router)#neighbor 10.0.0.1 remote-as 20
R3(config-router)#network 172.16.9.0 mask 255.255.0.0
```

* ở ví dụ trên sau khi đã cấu hình bgp ta có 2 môi trường:
    * R1-R2 là môi trường eBGP
    * R2-R3 là môi trường iBGP

* Ta có thể thấy được R1 và R2 trao đổi route với nhau và chúng học được các route của nhau do chúng là eGBP nên chugns sẽ tự động trao đổi các route đã học với nhau mà không cần phải quảng bá bằng câu lệnh(Không tính các ip của chính nó).
 
![](https://user-images.githubusercontent.com/52046920/190612940-4a89a220-bb43-40ba-912c-2b311440b9da.png)

![](https://user-images.githubusercontent.com/52046920/190606434-e0432d79-da09-4bf1-8185-4494e2fb7792.png)

<!--Do R1 và R2 là eBGP và là neighbor của nhau nên khi R1 quảng bá 192.168.10.0/24 thì next hop kèm theo chính là cổng kết nối trực tiếp với R2 là 9.0.0.1. Khi R2 nhận được và quảng bá nó tiếp vì-->
* R3 lúc này chưa học được do R2 chưa thực hiện quảng bá route cho R3

![](https://user-images.githubusercontent.com/52046920/190606423-6d00a8c4-63a1-46bd-9c3e-459490a471dd.png)
* Để R3 học được Route của R1 ta cấu hình như sau
    * Cách 1: R2 quảng bá mạng 9.0.0.0/8 vào trong AS 20
    ```cisco
    R2(config)#router bgp 20
    R2(config-router)#network 9.0.0.0 mask 255.255.0.0
    ```

    * Cách 2: R2 sẽ quảng bá các mạng học được bên ngoài với cho neighbor của nó trong môi trường iBGP là R3 với next hop là cổng kết nối trực tiếp 2 router
    ```cisco
    R2(config)#router bgp 20
    R2(config-router)#neighbor 10.0.0.2 next-hope-seft
    ```

![](https://user-images.githubusercontent.com/52046920/190606436-96a85952-d554-43f9-be3d-ae20e57d8a1a.png)
<!--
* IGP Synchronazation giúp hạn chế cho Router biên kết nối ra bên ngoài phải kết nối iBGP full mesh với tất cả thiết bị trong AS. Không dùng cơ chế này khi Router biên thiết lập full mesh.
* Ta có thể cấu hình tất cả những ip học được quả BGP vào định tuyến OSPF nội vùng
```cisco
R1(config)#router ospf 10
R1(config-router)#redistrubute bgp [Vùng AS nội vùng] subnets
```

* Các router còn lại thì bật chức năng Synchronazation lên
```cisco
R1(config)#router bgp 10
R1(config-router)#synchronazation
```
--->
