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

# TÌM HIỂU VỀ HSRP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	HSRP là gì***
* HSRP - Hot Standby Router Protocol là một giao thức chuẩn của Cisco cung cấp tính sẵn sàng cho hệ thống mạng. Là một giao thức độc quyền cho cisco
HSRP có khả năng gom các router lại thành 1 nhằm mục đích tạo ra 1 gateway ảo dùng chung. Khi 1 router hỏng thì PC không thể chọc đến default gateway của router được nên sẽ phải có dự phòng.
* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/185884918-7fa0a240-58b0-45ed-9fcf-6f4d5948855b.png)
* Không thể đi ra ngoài mạng nếu không sửa lại Default gateway

![](https://user-images.githubusercontent.com/52046920/186099350-17b7d5dd-e345-4ae4-b5b2-8ad91ba752e0.png)
![](https://user-images.githubusercontent.com/52046920/185884931-2cc54c1c-6b26-4a43-bb7d-c9a23277f621.png)

* Kích hoạt HSRP

![](https://user-images.githubusercontent.com/52046920/186049952-353b6900-e8ca-46d7-b1b8-7a5093e34c00.png)

* Tại R1
```cisco
R1(config)#int g0/0
R1(config-if)#ip add 192.168.1.1 255.255.255.0
R1(config-if)#standby 1 ip 192.168.1.3             ////ip đóng vai trò làm default gateway ảo
```
* Tại R2
```cisco
R2(config)#int g0/0
R2(config-if)#ip add 192.168.1.2 255.255.255.0
R2(config-if)#standby 1 ip 192.168.1.3             ////ip đóng vai trò làm default gateway ảo
```
* Kiểm tra
```cisco
R1#show standby g0/0
```
* Ping thử từ PC đến Default gateway ảo

![](https://user-images.githubusercontent.com/52046920/186049937-b01dfa8b-7681-4661-a15b-290da3e4c1dc.png)
# ***II.	 Nguyên tắc bầu chọn Active và Standby Router***
* Active Router sẽ là Router đứng ra làm nhiệm vụ Default gateway ảo còn Standby Router sẽ là Router dự phòng khi Acctive Router hỏng
* Xác định Active Router và Standby Router sẽ được dựa vào:
    * Priority: Router nào có giá trị lớn hơn thì sẽ được chọn làm Active Router
    * Nếu Priority bằng nhau: Nó sẽ dựa vào địa chỉ ip. Địa chỉ ip của Router nào lớn hơn thì được chọn là Active Router 
* Cơ chế hoạt động: 
    * Router Active sẽ đều đặn gửi các gói tin HSRP để router Standby cập nhật tình trạng của router Active. Các gói HSRP được gửi multicast đến địa chỉ 224.0.0.2(địa chỉ multicast đến toàn bộ router trong mạng)ở HSRP ver1 hoặc 224.0.0.102 ở HSRP ver2.
    * hello timer sẽ là khoảng thời gian định kỳ Active Router gửi gói tin HSRP 
    * Hold timer là khoảng thời gian mà Standby Router chờ đợi gói tin HSRP đến. Nếu sau khoảng thời gian chờ không có gói tin HSRP nào được gửi đến Standby Router thì nó sẽ chuyển thành chức năng của mình thành Active Router thay thế

* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186049790-156a766e-93f6-4402-8c46-a917fc797fef.png)
* R1

|Interface|ip|
|-|-|
|g0/0|192.168.1.1/24|
|g0/1|192.168.3.2/24|

* R2

|Interface|ip|
|-|-|
|g0/0|192.168.1.2/24|
|g0/1|192.168.4.2/24|

* R3

|Interface|ip|
|-|-|
|g0/0|192.168.3.1/24|
|g0/1|192.168.4.1/24|
* PC1: 192.168.1.5/24, default gateway 192.168.1.3
* PC2: 192.168.5.2/24, default gateway 192.168.5.2/24
* Cách hiệu chỉnh chỉ số priority
* Tại R1
```cisco
R1(config)#int g0/0
R1(config-if)#ip add 192.168.1.1 255.255.255.0
R1(config-if)#standby 1 ip 192.168.1.3 
///Hiệu chỉnh chỉ số priority
R1(config-if)#standby 1 priority 200
R1(config-if)#standby 1 preempt     
///Bắt buộc phải sử dụng để (chức năng chiếm quyền) nếu không thiết lập thì có khả năng priority mặc dù cao hơn nhưng sẽ không được chọn làm Active Router

R1(config-if)#standby 1 timers 1 10
/// thiết lập cứ 1s active router sẽ gửi gói tin hello đến standby, sau 10 giây mà không nhận được gói tin thì R2 sẽ đóng vai trò làm active router, Các giá trị này nếu không thiết lập sẽ có giá trị mặc định là 3 giây và 10 giây

//định tuyến
R1(config)#ip route 192.168.5.0 255.255.255.0 192.168.3.1

```
* Tại R2
```cisco
R2(config)#int g0/0
R2(config-if)#ip add 192.168.1.2 255.255.255.0
R2(config-if)#standby 1 ip 192.168.1.3 
///Hiệu chỉnh chỉ số priority
R2(config-if)#standby 1 priority 100
R2(config-if)#standby 1 preempt     
///Bắt buộc phải sử dụng để (chức năng chiếm quyền) nếu không thiết lập thì có khả năng priority mặc dù cao hơn nhưng sẽ không được chọn làm Active Router
R2(config-if)#standby 1 timers 1 10

//định tuyến
R2(config)#ip route 192.168.5.0 255.255.255.0 192.168.4.1

```
* Nếu không thiết lập preempt thì Router nào được cấu hình trước sẽ được chọn là Active Router ở đây sẽ là R1, R2 thiết lập sau dù cho setup priority lớn hơn thì cũng sẽ không được chọn làm Active router.
* Tại R3
```cisco
//định tuyến
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.3.2
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.4.2

```
* Như thiết lập ở đây thì R1 sẽ được chọn làm Active Router do có priority cao hơn, R2 được chọn làm Standby Router vậy đường đi từ PC1 đến PC2 sẽ đi qua R1 với default gateway ảo của 2 Router R1 và R2 là 192.168.1.3.
* Kiểm tra thiết lập bằng câu lệnh
```cisco
R1#show standby brief

R2#show standby brief
```
![](https://user-images.githubusercontent.com/52046920/186058732-c25894b3-8b3e-4936-8891-41791795ed79.png)

* Kiêm tra đường đi từ PC1 đến PC2 nhận thấy đi qua R1

![](https://user-images.githubusercontent.com/52046920/186049786-812b607b-699e-4e19-958a-de46cfc3f88f.png)
* Khi đường đi từ R1 đến PC1 bị đứt thì PC1 sẽ đi đến PC2 bằng R2 mà không cần phải thiết lập lại default gateway

![](https://user-images.githubusercontent.com/52046920/186101248-ad250771-0262-4948-ab1c-b5e11bdb5923.png)
* Kiểm tra đường đi

![](https://user-images.githubusercontent.com/52046920/186050494-d8474fa3-ecd3-486d-8d39-afeca044ffc1.png)
* Đường đi từ PC1 đến PC2 phải đi qua R2

# ***III.	 Giải pháp cân bằng tải trong HSRP***
* Nếu thiết lập HSRP bình thường thì mọi lưu lượng sẽ chuyển hết qua cho R1 như ví dụ ở mục trước và R2 chỉ để dự phòng, điều này sẽ gây quá tải cho R1 và lãng phí tài nguyên khi R2 chỉ để đấy dự phòng mà không làm gì cả. 
* Vậy nên ta cần cân bằng tải bằng cách thiết lập nhiều Default gateway ảo và mỗi Router sẽ làm Active Router cho 1 Default gateway và ở đây ta có 2 phương pháp:
    * Thiết lập nhiều default gateway cho interface
    * Sử dụng Sub interface, thiết lập default gateway ảo cho từng cổng sub interface
## ***1.Cách 1: Thiết lập nhiều default gateway cho interface***
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186058735-0d82cf14-a5ea-414d-84fb-a38f8960210b.png)
* R1

|Interface|ip|
|-|-|
|g0/0|192.168.1.1/24|
|g0/1|192.168.3.2/24|

* R2

|Interface|ip|
|-|-|
|g0/0|192.168.1.2/24|
|g0/1|192.168.4.2/24|

* R3

|Interface|ip|
|-|-|
|g0/0|192.168.3.1/24|
|g0/1|192.168.4.1/24|
* PC1: 192.168.1.5/24, default gateway 192.168.1.3
* PC3: 192.168.1.6/24, default gateway 192.168.1.4
* PC2: 192.168.5.2/24, default gateway 192.168.5.2/24

* Ta sẽ tạo 2 default gateway ảo là 192.168.1.3 , 192.168.1.4 và sẽ cấu hình để chỉa tải thành 2 đường PC1 muốn đi ra ngoài sẽ phải đi qua R1 và PC3 muốn đi ra ngoài sẽ phải đi qua R2.
    * R1 sẽ đóng vai trò làm Active Router cho default gateway 192.168.1.3 R2 sẽ là Standby Router
    * R2 sẽ đóng vai trò làm Active Router cho default gateway 192.168.1.4
    R1 sẽ là Standby Router
* Cấu hình
* Tại R1
```cisco
R1(config)#int g0/0
R1(config-if)#ip add 192.168.1.1 255.255.255.0
///thiết lập thông số để R1 làm Active Router của default gateway 192.168.1.3
R1(config-if)#standby 1 ip 192.168.1.3 
R1(config-if)#standby 1 priority 200
R1(config-if)#standby 1 preempt     
R1(config-if)#standby 1 timers 1 10
///thiết lập thông số để R1 làm Standby Router của default gateway 192.168.1.4
R1(config-if)#standby 2 ip 192.168.1.4 
R1(config-if)#standby 2 priority 100
R1(config-if)#standby 2 preempt     
R1(config-if)#standby 2 timers 1 10

//định tuyến
R1(config)#ip route 192.168.5.0 255.255.255.0 192.168.3.1
```
* Tại R2
```cisco
R2(config)#int g0/0
R2(config-if)#ip add 192.168.1.2 255.255.255.0
///thiết lập thông số để R2 làm Standby Router của default gateway 192.168.1.3
R2(config-if)#standby 1 ip 192.168.1.3 
R2(config-if)#standby 1 priority 100
R2(config-if)#standby 1 preempt     
R2(config-if)#standby 1 timers 1 10

///thiết lập thông số để R2 làm Active Router của default gateway 192.168.1.4
R2(config-if)#standby 2 ip 192.168.1.4 
R2(config-if)#standby 2 priority 200
R2(config-if)#standby 2 preempt     
R2(config-if)#standby 2 timers 1 10

//định tuyến
R2(config)#ip route 192.168.5.0 255.255.255.0 192.168.4.1
```
* Tại R3
```cisco
//định tuyến
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.3.2
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.4.2

```
* Kiểm tra thiết lập bằng câu lệnh
```cisco
R1#show standby brief

R2#show standby brief
```
![](https://user-images.githubusercontent.com/52046920/186058739-ca0f55a0-5c8f-4314-83d2-e9c7cc366ee2.png)

* Kiểm tra đường đi từ PC1 đến PC2 và từ PC3 đến PC 2

![](https://user-images.githubusercontent.com/52046920/186058740-26bcea6b-c79c-429f-8622-e796fea7d49e.png)

* Nhược điểm của phương pháp này là nếu muốn cấp ip động thì sẽ không thể set 2 default gateway được vậy nến default gateway chỉ có thể thiết lập bằng tay cho từng PC một
## ***2.Cách 2: Sử dụng Sub interface, thiết lập default gateway ảo cho từng cổng sub interface***
* Cần thiết lập các nhóm máy thuộc vào 2 VLan khác nhau ta thiết lập default cho các cổng ảo như sau
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186073549-dddb52c8-7d71-4aaa-8618-687ab76e2b3d.png)
* Tại R1
```cisco
R1(config)#int g0/0.10
R1(config-subif)#encapsulation dot1q 10
R1(config-subif)#ip address 192.168.10.1 255.0.0.0
///thiết lập thông số để R1 làm Active Router của default gateway 192.168.1.3
R1(config-subif)#standby 1 ip 192.168.10.3 
R1(config-subif)#standby 1 priority 200
R1(config-subif)#standby 1 preempt     
R1(config-subif)#standby 1 timers 1 10
///thiết lập thông số để R1 làm Standby Router của default gateway 192.168.20.4
R1(config)#int g0/0.20
R1(config-subif)#encapsulation dot1q 20
R1(config-subif)#ip address 192.168.20.1 255.0.0.0
R1(config-subif)#standby 2 ip 192.168.20.4 
R1(config-subif)#standby 2 priority 100
R1(config-subif)#standby 2 preempt     
R1(config-subif)#standby 2 timers 1 10

//định tuyến
R1(config)#ip route 192.168.5.0 255.255.255.0 192.168.3.1
```
* Tại R2
```cisco
R2(config)#int g0/0.10
R2(config-subif)#encapsulation dot1q 10
R2(config-subif)#ip address 192.168.10.2 255.0.0.0
///thiết lập thông số để R2 làm Standby Router của default gateway 192.168.10.3
R2(config-subif)#standby 1 ip 192.168.10.3 
R2(config-subif)#standby 1 priority 100
R2(config-subif)#standby 1 preempt     
R2(config-subif)#standby 1 timers 1 10

///thiết lập thông số để R1 làm Active Router của default gateway 192.168.20.4
R2(config)#int g0/0.20
R2(config-subif)#encapsulation dot1q 20
R2(config-subif)#ip address 192.168.20.2 255.0.0.0
R2(config-subif)#standby 2 ip 192.168.20.4 
R2(config-subif)#standby 2 priority 200
R2(config-subif)#standby 2 preempt     
R2(config-subif)#standby 2 timers 1 10

//định tuyến
R1(config)#ip route 192.168.5.0 255.255.255.0 192.168.4.1
```

* Tại R3
```cisco
//định tuyến
R3(config)#ip route 192.168.10.0 255.255.255.0 192.168.3.2
R3(config)#ip route 192.168.10.0 255.255.255.0 192.168.4.2
R3(config)#ip route 192.168.20.0 255.255.255.0 192.168.4.2
R3(config)#ip route 192.168.20.0 255.255.255.0 192.168.3.2
```
* Kiểm tra đường đi từ PC1 và PC3 đến với PC2

![](https://user-images.githubusercontent.com/52046920/186073384-63d25837-dbcb-48a6-8650-23bce4d93758.png)

* Có thể sử dụng DHCP để cấp ip động được nếu sử dụng cách thức cân bằng tải này
# ***IV. Cơ chế Track giám sát trạng thái Port trong HSRP***
* Trong trường hợp đường đi từ R1 ra ngoài mạng bị đứt tuy nhiên nó vẫn là Active Router vậy nên các gói tin vẫn sẽ đi đến R1 và sẽ ko ra được ngoài mạng.
* Ví dụ:
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186127494-ee8def71-bd02-45b2-a39d-eb4f17595a9e.png)

* khi đường e0/1 bị đứt

![](https://user-images.githubusercontent.com/52046920/186128039-2445063e-7429-401b-94d8-8a70d47c4b31.png)
* Thực hiện ping từ PC1 đến PC2 không được
* Thực hiện lệnh tracert từ PC1 đến PC 2 nhận thấy PC1 liên tục gửi gói tin đến R1 và R1 không có đường đi đến PC2. Mặc dù có đường đi qua R2 để đến được PC 2 tuy nhiên vì R1 là Active Router nên là PC1 sẽ luôn phải đi qua R1. Liên kết R1 và R2 không đứt vậy nên nó vẫn gửi bản tin đều cho R2 và vẫn tiếp tục đóng vai trò Active Router.

![](https://user-images.githubusercontent.com/52046920/186127507-000b48bf-d448-400a-841b-e27a57f2a39b.png)
* Vậy nên để giải quyết vấn đề này ta sử dụng cơ chế Track ví dụ trong trường hợp này khi R1 mất kết nối với R3 dẫn đến việc nó sẽ bị R2 lấy mất quyền Active Router. Track sẽ theo dõi cổng từ R1 đến R3 và khi cổng đó của R1 bị ngắt kết nối hoặc bị tắt nó tự động hạ giá trị priority của R1 xuống thấp. Điều này dẫn đến việc quyền Active Router sẽ chuyển qua cho R2
* Cấu hình

![](https://user-images.githubusercontent.com/52046920/186127494-ee8def71-bd02-45b2-a39d-eb4f17595a9e.png)
* R1, R2, R3 đã được định tuyết sẵn, R1 được cấu hình để trở thành Active Router, R2 là Standby Router
* Ta muốn giám sát port gig0/1 của R1 để khi port này xảy ra sự cố sẽ giảm priority xuống chuyển quyền Active Router cho R2
* Có priority của R1 là 200 và R2 là 100

![](https://user-images.githubusercontent.com/52046920/186127510-72532c24-45d2-40a2-94f3-8faed2d50805.png)
![](https://user-images.githubusercontent.com/52046920/186127511-d43b2550-34e5-4387-8440-b4b098bbc40f.png)
* Tại R1
```cisco
/// Tạo object track giám sát trạng thái lớp 2 của e0/1
R1(config)#track 1 interface e0/1 line-protocol
R1(config-track)#int e0/0
R1(config-if)#standby 1 track 1 decrement 50        
///khi e0/1 down priority giảm đi 150 điểm lúc này nó sẽ thấp hơn priority của R2 nên R2 sẽ trở thành Active Router mới

```

* Tiến hành shutdown interface e0/1 và kiểm tra giá trị priority

![](https://user-images.githubusercontent.com/52046920/186127513-b04d149b-ea75-44db-bf57-d32593d562b8.png)
![](https://user-images.githubusercontent.com/52046920/186127516-1a613786-abc1-4966-a265-e80ca7b94edb.png)
* Ta thấy Priority của R1 giảm đúng như câu hình và nó đã trở thành Standby Router
* Kiểm tra ping và trace để xem đường đi đến PC2

![](https://user-images.githubusercontent.com/52046920/186127523-4965e0d3-bf60-4a47-9123-411f93d7d059.png)