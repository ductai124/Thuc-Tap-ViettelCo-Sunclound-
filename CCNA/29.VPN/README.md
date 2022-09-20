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

# TÌM HIỂU VỀ VPN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. VPN là gì]()
# [II. Tính năng quan trọng của VPN]()
## &ensp; [1. Mã hóa]()
## &ensp; [2. Split tunneling]()
## &ensp; [3. Giới hạn dữ liệu và băng thông]()
## &ensp; [4. Chính sách không ghi log]()
## &ensp; [5. Kết nối nhiều thiết bị đồng thời]()
## &ensp; [6. Kill switch]()
## &ensp; [7. Chống rò rỉ IP]()
## &ensp; [8. IP Shuffle]()

# [III. Kỹ thuật GRE VPN trên Cisco Router]()
***
# ***I.	VPN là gì***
* VPN - Virtual Private Network hay mạng riêng ảo. VPN được sử dụng để tạo ra kết nối riêng tư giữa các thiết bị thông qua internet vì nó truyền dữ liệu 1 cách an toàn và ẩn danh qua các mạng công cộng. VPN hoạt động bằng cách ẩn đi địa chỉ IP của người dùng và mã hóa dữ liệu để chỉ người được cấp quyền nhận dữ liệu mới có thể đọc được.
* Được sử dụng bởi các tập đoàn lớn, cơ quan lớn để cho phép người dùng từ xa kết nối an toàn đến mạng riêng của cơ quan mình.
* Ứng dụng:
    * Truy cập vào mạng doanh nghiệp từ xa: sử dụng để truy cập vào tất cả tài nguyên trên mạng cục bộ mà không cần tiếp xúc trực tiếp với internet, làm tăng tính bảo mật.
    * Truy cập mạng gia đình, dù không ở nhà
    * Duyệt web ẩn danh, mã hóa thông tin truyền qua mạng
    * Truy cập đến những website bị chặn bởi 1 số nhà mạng, bỏ qua kiểm duyệt internet, vượt tường lửa
    * Tải tập tin: Tăng tốc độ tải file
# ***II.	Tính năng quan trọng của VPN***
# ***1. Mã hóa***
* Nó chuyển đổi dữ liệu thành 1 định dạng không thể đọc được. Dữ liệu được bảo vệ bằng khóa mã hóa(key) do người dùng đặt. Muốn giải mã ngược thì cần có key giải mã. VPN sẽ mã hóa dữ liệu và biến nó trở lại định dạng đầu ở đầu bên kia
* Có 3 kỹ thuật các VPN hầu hết đều có:
    * Mã hóa đối xứng
    * Mã hóa key public
    * Hashing
# ***2. Split tunneling***
* Tính năng này cho phép người dùng chọn ứng dụng bảo mật với VPN và các ứng dụng hoạt động bình thường mà không sử dụng VPN
# ***3. Giới hạn dữ liệu và băng thông***
* Giới hạn định lượng dữ liệu người dùng có thể truyền hoặc băng thông có thể sử dụng tịa 1 thời điểm
# ***4. Chính sách không ghi log***
* Không lưu trữ log về hoạt động trực tuyến của người dùng. Tuy nhiên không nhiều VPN cung cấp dịch vụ này, kể các VPN không quá nghiêm ngặt về ghi log cũng phải ghi lại 1 số log
# ***5. Kết nối nhiều thiết bị đồng thời***
* Nhiều thiết bị đồng thời có thể truy cập VPN cùng 1 lúc. Hầu hết các VPN đều đặt giới hạn cho kết nối đồng thời và rất ít có thể đáp ứng các kết nối khong giới hạn tại 1 thời điểm
# ***6. Kill switch***
* Là 1 tính năng ngắt kết nối thiết bị khỏi Internet nếu kết nối VPN bị ngắt đột ngột. Là 1 tính năng quan trọng giúp ngăn gửi dữ liệu bên ngoài VPN bảo mật
# ***7. Chống rò rỉ IP***
* Ẩn đi IP thực của người dùng trên Internet. Tuy nhiên IP thực của người dùng vẫn có nguy cơ bị lộ dù đã dùng VPN bởi các sự cố rò rỉ IP.
* Các VPN hàng đầu có tính năng bảo vệ chống rò rỉ IP/DNS mặc định. Nếu tính năng này hoạt động IP thực và IP VPN gán cho người dùng se không trùn nhau
# ***8. IP Shuffle***
* Là 1 tính năng bảo mật VPN ngẫu nhiên hóa địa chỉ IP của người dùng bằng cách kết nối lại người dùng với 1 VPN Server khác sau 1 khoảng thời gian nhất định.

# ***III.	Kỹ thuật GRE VPN trên Cisco Router***
* GRE VPN - Generic Routing Encapsulation VPN là giao thwusc được phát triển đầu tiên bởi cisco. Nó sẽ đóng gói 1 số kiểu gói tin vào bên trong IP tunnels để tạo thành các kết nối Point-Point. Các IP tunnels chạy trên các hạ tậng mạng công cộng
* Ví dụ 

![](https://user-images.githubusercontent.com/52046920/191153755-c68b5d5e-8ecd-42ff-9f1d-c0e26884460a.png)
* PC1 muốn ping đến PC3 nó sẽ soạn ra gói tin có ip đích là PC3 tuy nhiên khi gửi ra ngoài mạng Router IPS sẽ đúng ra hủy gói tin vì IP đích là IP Private và không được định tuyến trên mạng vậy cần phải thiết lập VPN để 2 site HCM và HN có thể kết nối với nhau. 

![](https://user-images.githubusercontent.com/52046920/191153759-db0e9516-2c50-4697-94a5-1fb5de47d7e3.png)

* Sau khi thiết lập VPN thì gói tin gửi đi sẽ được đính kèm thêm IP header mặt ngoài và khi IPS nhận được nó sẽ chuyển tiếp gói tin đến đích và khi Router site đích nhận được nó sẽ gỡ bỏ IP header mặt ngoài và chuyển gói tin đến đích trong nội bộ

![](https://user-images.githubusercontent.com/52046920/191153760-7bdb7eb4-109a-4134-869d-787fb7696b1a.png)

![](https://user-images.githubusercontent.com/52046920/191153762-a8279805-1bc3-4ace-ac56-77dbca70c9b9.png)

![](https://user-images.githubusercontent.com/52046920/191153764-4c66438f-6bad-471e-995a-b617afee8f2a.png)


* Mô phỏng lại mô hình trên

![](https://user-images.githubusercontent.com/52046920/191157806-806b3aed-c25c-4ad9-ad2d-5419016a2eca.png)
* Cấu hình như sau
* Router site HCM
```cisco
HCM(config)#ip route 0.0.0.0 0.0.0.0 1.0.12.2
HCM(config)#ip nat inside source list 1 interface g0/0 overload 
HCM(config)#access-list 1 permit 10.0.1.0 0.0.0.255
HCM(config)#int g0/1
HCM(config-if)#ip nat inside 
HCM(config-if)#int g0/0
HCM(config-if)#ip nat outside 
HCM(config-if)#end
```
* Router site HN
```cisco
HCM(config)#ip route 0.0.0.0 0.0.0.0 1.0.23.2
HCM(config)#ip nat inside source list 1 interface g0/0 overload 
HCM(config)#access-list 1 permit 10.0.3.0 0.0.0.255
HCM(config)#int g0/1
HCM(config-if)#ip nat inside 
HCM(config-if)#int g0/0
HCM(config-if)#ip nat outside 
HCM(config-if)#end
```

* Cấu hình VPN site HN và site HCM
* Tại Router site HCM
```cisco
///Tạo interface tunnel khác với interface tunnel bên site HN
HCM(config)#interface tunnel 1

///Gán IP bắt kỳ tuy nhiên phải cùng dải với IP của interface tunnel bên site HN
HCM(config-if)#ip address 10.0.13.1 255.255.255.0

///Nguồn là cổng ra của Router kết nối với IPS(có thể là IP nguồn của mặt ngoài kết nối với Router IPS)
HCM(config-if)#tunnel source g0/0

///IP đích là mặt ngoài của Router phía site HN
HCM(config-if)#tunnel destination 1.0.23.3

///Định tuyết đường tunnel

HCM(config)#ip route 10.0.3.0 255.255.255.0 10.0.13.3

///Có thể dùng định tuyến động vì GRE VNP cho phép sử dụng định tuyến động
```



* Tại Router site HN
```cisco
///Tạo interface tunnel khác với interface tunnel bên site HCM
HN(config)#interface tunnel 0

///Gán IP bắt kỳ tuy nhiên phải cùng dải với IP của interface tunnel bên site HCM
HN(config-if)#ip address 10.0.13.3 255.255.255.0

///Nguồn là cổng ra của Router kết nối với IPS(có thể là IP nguồn của mặt ngoài kết nối với Router IPS)
HCM(config-if)#tunnel source g0/0

///IP đích là mặt ngoài của Router phía site HCM
HN(config-if)#tunnel destination 1.0.12.1


///Định tuyết đường tunnel

HN(config)#ip route 10.0.1.0 255.255.255.0 10.0.13.1

///Có thể dùng định tuyến động vì GRE VNP cho phép sử dụng định tuyến động
```


* Kiểm tra ping từ PC 1 đến PC 3

![](https://user-images.githubusercontent.com/52046920/191158361-28be6410-ec9d-4bd7-9630-b4ff4aa8869a.png)
* Ping thành công, vậy là 2 site HN và HCM đã kết nối được với nhau

* Ngoài ra còn có thể cấu hình thêm keepalive
```cisco
HCM(config)#interface tunnel 1

HCM(config-if)#keepalive 10 3

///Router gửi gói tin định kỳ 10s 1 lần sau 3 lần không nhận được gói tin từ router phía bên kìa thì interface tunnel 1 sẽ đóng lại

///Câu lệnh sau thường sẽ không được sử dụng vì khi bật tunnel và cấu hình đầy đủ các bước trên  tunnel sẽ ở trạng thái up và mặc định là GRP
HCM(config-if)#tunnel mode grp ip
```