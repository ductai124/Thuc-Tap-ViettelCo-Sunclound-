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

# TÌM HIỂU VỀ TỔNG QUAN KỸ THUẬT ĐỊNH TUYẾN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Định tuyến là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#i%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-l%C3%A0-g%C3%AC)

## &ensp; [1. Định tuyến tĩnh](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#1%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-t%C4%A9nh)

## &ensp; [2. Định tuyến động](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#2%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-%C4%91%E1%BB%99ng)

# [II. Tổng quan về kỹ thuật định tuyến tĩnh](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#iit%E1%BB%95ng-quan-v%E1%BB%81-k%E1%BB%B9-thu%E1%BA%ADt-%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-t%C4%A9nh)

# [III. Cấu hình định tuyến trên cisco router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#iiic%E1%BA%A5u-h%C3%ACnh-%C4%91%E1%BB%8Bnh-tuy%E1%BA%BFn-tr%C3%AAn-cisco-router)

# [IV. Cấu hình Default Route trên Cisco Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#ivc%E1%BA%A5u-h%C3%ACnh-default-route-tr%C3%AAn-cisco-router)

# [V. Điều hướng lưu lượng bằng cách hiệu chỉnh AD của Static Route](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/7.Static%20router#v%C4%91i%E1%BB%81u-h%C6%B0%E1%BB%9Bng-l%C6%B0u-l%C6%B0%E1%BB%A3ng-b%E1%BA%B1ng-c%C3%A1ch-hi%E1%BB%87u-ch%E1%BB%89nh-ad-c%E1%BB%A7a-static-route)
***
# ***I.	Định tuyến là gì***

* Định tuyến hay còn gọi là routing là quá trình tìm và xác định đường đi tốt nhất để truyền tiếp dữ liệu tới nút đích thông qua các thiết bị định tuyến. Router dựa vào IP đích trong các gói tin và bảng định tuyến (Routing Table) để xác định đường đi cho chúng.

* Có 2 loại định tuyến là:
    * Định tuyến tĩnh
    * Định tuyến động
## ***1.	Định tuyến tĩnh***
* Định tuyến tĩnh là loại định tuyến mà trong đó router sử dụng các tuyến đường đi tĩnh để vận chuyển dữ liệu đi. Các tuyến đường đi tĩnh được thiết lập thủ công và cố định.
* Ưu điểm: 
    * Sử dụng ít bằng thông 
    * Không tốn tài nguyên tính toán và phân tích gói tin định tuyến
    * Dễ dàng triền khai cấu hình
    * Bảo mật tốt
* Nhược điểm:
    * Không có khả năng tự cập nhật đường đi mà phải cập nhật bằng tay.
    * Mở rộng kém thích hợp với mô hình mạng nhỏ do phải cấu hình bằng tay mà nếu là 1 mạng lớn sẽ rất khó kiểm soát.
* Định tuyến tĩnh thường được sử dụng trong những trường hợp:
    * Đường truyền băng thông thấp
    * Cần phải kiểm soát các kết nối trong hệ thống.
    * Hệ thông có ít kết nối, hệ thống nhỏ.
    * dùng các làm dự phòng cho các định tuyến động.
## ***2.	Định tuyến động***
* Định tuyến động là loại định tuyến mà trong đó các router sẽ thực hiện định tuyến tự động bằng các giao thức mà không cần phải thiết lập thủ công chỉ ra từng đường như định tuyến tĩnh. Tự chạy một phương thức tính toán nào đó để xác định xem để đi đến các mạng này thì phải sử dụng đường đi nào là tối ưu
* Có 2 loại giao thức định tuyến là :
    * Exterior Gateway Protocols(Định tuyến các thiết bị trong cùng 1 vùng)
    * Interior Gateway Protocols(Định tuyến các thiết bị không nằm trong 1 vùng)
# ***II.	Tổng quan về kỹ thuật định tuyến tĩnh***
![](https://user-images.githubusercontent.com/52046920/183083368-ade112c6-edc7-4677-8df9-f751b81ac6f5.png)
* Router 1

|Cổng|ip|
|---|---|
|Gig0/0|192.168.1.2/24|
|Gig0/1|192.168.2.1/24|
|Gig0/2|192.168.4.2/24|
* Router 2

|Cổng|ip|
|---|---|
|Gig0/0|192.168.2.2/24|
|Gig0/1|192.168.3.2/24|
|Gig0/2|192.168.5.2/24|
* Router 3

|Cổng|ip|
|---|---|
|Gig0/0|192.168.4.1/24|
|Gig0/1|192.168.5.1/24|
|Gig0/2|192.168.6.1/24|

* PC 1: ip 192.168.1.1/24, default gateway 192.168.1.2
* PC 2: ip 192.168.6.2/24, default gateway 192.168.6.1
* PC 3: ip 192.168.3.1/24, default gateway 192.168.3.2

* Câu lệnh kiểm tra bảng định tuyến.

![](https://user-images.githubusercontent.com/52046920/183083365-899a574b-d3e5-4137-aacb-72589468a7d0.png)
```cisco
R1#show ip route
```
* Giả sử PC1 ping đến PC2 đầu tiên nó sẽ gói tin sẽ đi đến default gateway là router1 và ở đây router sẽ dựa vào bảng định tuyến của mình để tìm ra đường đi cho gói tin đến được với PC2 tuy nhiên theo bảng định tuyến mặc định thì trong nó không có đường đi nào đi đến dải ip 192.168.6.0 và nó sẽ tiến hành hủy gói tin. 


* Giả sử PC1 ping đến Router2, gói tin sẽ đi đến Router1 và ở bảng định tuyến mặc định Router 1 có đường đi đến Router2 nó sẽ chuyển gói tín đến Router2 tuy nhiên khi Router2 nhận được gói tin nó sẽ soạn gói tin reply nhưng trong bảng định tuyến mặc định của nó không có đường đi đến dải mạng 192.168.1.0 vậy nên nó hủy gói tin do khong biết đường đi.


* Vậy nên ta cần phải thêm định tuyến tĩnh vào bảng định tuyến cho router để nó có thể xác định được đường đi mà gói tin cần phải đi để có thể đến được đích


# ***III.	Cấu hình định tuyến trên cisco router***
* Đứng từ Router1 ta thấy muốn đến được mạng 192.168.3.0 cần phải đi qua cổng Gig0/2 với ip 192.168.2.2 của Router2. Muốn đến được mạng 192.168.6.0 thì phải đi qua cổng Gig0/0 với ip 192.168.4.1 của Router3. Ta cấu hình như sau
```cisco
///ip route (dai mang cua dich) (subnetmask) (next hope)

R1(config)#ip route 192.168.3.0 255.255.255.0 192.168.2.2
R1(config)#ip route 192.168.6.0 255.255.255.0 192.168.4.1
```

* Tương tự với các router khác. 
* Router 2
```cisco
R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.2.1
R2(config)#ip route 192.168.6.0 255.255.255.0 192.168.5.1
```
* Router 3
```cisco
R3(config)#ip route 192.168.3.0 255.255.255.0 192.168.5.2
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.4.2
```

![](https://user-images.githubusercontent.com/52046920/183083362-efbd2825-e263-46a8-a4f4-f75d9c9e6060.png)
* Sau khi định tuyến ta sẽ kiểm tra ping thử các PC với nhau. Từ PC1 ping đến PC2 và PC3.

![](https://user-images.githubusercontent.com/52046920/183083366-e5ca8f17-7fc7-46c9-9672-7106b9c96c21.png)

# ***IV.	Cấu hình Default Route trên Cisco Router***
* Một con router muốn gửi dữ liệu ra ngoài mạng thì router phải có 1 route đặc biệt là default route có :
    * ip: 0.0.0.0 
    * subnetmask: 0.0.0.0
* Nó là đường đi mặc định để đi ra ngoài mạng nếu như ta không biết được các đường đi tiếp theo và thiết lập định tuyến vì bên ngoài mạng có rất nhiều các route mà ta không thể biết được.
* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/183083355-d9ed8e80-71c5-41bf-8785-8f8b2a4ebc4d.png)
* Router 1

|Cổng|ip|
|---|---|
|Gig0/0|192.168.2.2/24|
|Gig0/1|192.168.1.1/24|
* Router 2

|Cổng|ip|
|---|---|
|Gig0/0|192.168.2.1/24|
|Gig0/1|192.168.3.1/24|

* PC 1: ip 192.168.1.2/24, default gateway 192.168.1.2
* PC 2: ip 192.168.3.2/24, default gateway 192.168.6.1

* Giả sử ta muốn ping từ PC1 đén PC2 tuy nhiên không có địa chỉ cụ thể của PC2 từ bảng định tuyến vậy ta sẽ sử dụng default route ở đây
```cisco
R1(config)#ip route 0.0.0.0 0.0.0.0 192.168.2.2

R2(config)#ip route 0.0.0.0 0.0.0.0 192.168.2.1
```
![](https://user-images.githubusercontent.com/52046920/183083356-07f2ff2e-e790-42b6-85ae-a09ae354cb92.png)
* Kiểm tra ta thấy được 2 máy đã có thể ping thông với nhau.
* Gói tin sẽ đi đến router1 và nó không biết đường đi đến PC2 do không có trong bảnh đỉnh tuyến nên nó sẽ mặc định gửi ra ngoài đến cổng gig0/0 của router2 rồi nó mới xử lý tiếp và ở router 2 thì nó có thông tin của pc 2 nên nó chuyển gói tin đến pc2 và gói tin reply được soạn quay lại tương tự như request.

# ***V.	Điều hướng lưu lượng bằng cách hiệu chỉnh AD của Static Route***
* AD viết tắt của administrative distance(Khoảng cách quản trị) là chỉ số ưu tiên của 1 giao thức trong hệ thống mạng. AD càng nhỏ thì càng được ưu tiên và càng tin cậy.
* Việc hiệu chỉnh AD của static route sẽ quyết định  gói tin, dữ liệu sẽ được đi qua đường nào
* Được sử dụng khi có 2 đường truyền và muốn sử dụng cho mục đích 1 đường truyền dữ liệu chính và 1 đường dự phòng. Khi đường tryền chính có vấn đề ví dụ như bị đứt thì nó sẽ bị xóa khỏi bảng định tuyến thay vào đó đường dự phòng sẽ được sử dụng. Và khi đường truyền chính được sửa chữa khôi phục thì nó sẽ trở lại với vị trí của mình
* Ta cũng có thể thiết lập 2 đường truyền với mục đích khác nhau như ưu tiên 1 đường để truyền và 1 đường để nhận dữ liệu.
* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/183084629-493aab4e-64bc-4287-8be1-9694e0a7c80f.png)
```cisco
\\\ chỉ số cuối câu lệnh chính là AD muốn thiết lập ở đây đường đi đến cổng có ip 192.168.2.2 sẽ là route chính và route có AD bằng 2 sẽ là dự phòng

R2(config)#ip route 192.168.4.0 255.255.255.0 192.168.2.2 1             
R2(config)#ip route 192.168.4.0 255.255.255.0 192.168.3.2 2
```

![](https://user-images.githubusercontent.com/52046920/183083353-a06e28df-781a-48aa-a5d1-66d7e6d7738b.png)

* Tương tự với router R1
* Sau khi thiết lập xong

![](https://user-images.githubusercontent.com/52046920/183083349-cc059b86-ea10-45d4-b2ab-fce5d2c8b24e.png)
* Khi đường chính có vấn đề hoặc bị hỏng đường dự phòng sẽ được sử dụng và hiển thị trong bảng định tuyến. Khi đường chính được khôi phục thì đường đi sau sẽ lại trở về làm đường dự phòng

![](https://user-images.githubusercontent.com/52046920/183083341-15ef258f-0f27-478d-85c9-968ef9d44603.png)
<!---
# ***VI.	Cơ chế Proxy ARP trong định tuyến***
* 

# ***VII.	Cấu hình cân bằng tải Load Balancing trên Cisco Router***
* Đảm bảo hệ thống mạng luôn luông hoạt động không bị gián đoạn và không bị quá tải bằng cách phân ra nhiều đường đi cùng đến 1 đích

# ***VII.	Tối ưu định tuyến bằng kỹ thuật Summary***
* Summary hay còn gọi là classless inter-domain Routing(CIDR). Kỹ thuật giúp định tuyến nhanh hơn
* Ví dụ : có một mô hình như hình sau, từ router 1 ta sẽ phải định tuyến 3 lần cho 3 mạng bên trái tuy nhiên ta có thể gom chúng vào làm 1 mạng to và định tuyến vào mạng to đấy.

![]()

* <span style="color: green">192.168.00000</span>011.0/24
* <span style="color: green">192.168.00000</span>100.0/24
* <span style="color: green">192.168.00000</span>101.0/24

* Ta nhận thấy 3 dải ip trên có 21 bit giống nhau ta sẽ gộp được thành mạng 192.168.0/21 subnetmask 192.168.248.0 
* Từ router 1 ta có thể định tuyến đến mạng 192.168.0/21 là được

--->
