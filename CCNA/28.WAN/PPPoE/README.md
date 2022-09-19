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

# TÌM HIỂU VỀ CÔNG NGHỆ PPPoE TRÊN MODEM
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. PPPoE là gì]()
# [II. Cách thức hoạt động của PPPoE]()
# [III. Cáu hình PPPoE]()

***
# ***I.	PPPoE là gì***
* PPPoE - Point to Point Protocol over Ethernet là 1 giao thức mạng bắt nguồn từ PPP. Là 1 giao thức quản lý, chia sẻ và cung cấp mạng của những nhà mạng hiện nay.
* Được thiết lập dựa trên cấu trúc phân nhánh thiết bị kết nối và truyền tải tín hiệu theo tuyến cố định. Nó hoạt động theo hệ thống truyền tin tức theo điểm - điểm bằng hệ thống đường hầm cố định và bảo mật cao.

* Công dụng chính của PPPoE
    * Tiếp nhận ID kết nối mạng: Nhà mạng nào cũng có 1 hệ thống Server điều hành để nhận dạng và cung cấp ID khi nhận tin báo từ các loại thiết bị kết nối mạng. Ở đấy PPPoE sẽ đóng vai trò 1 Server ảo làm các nhiệm vụ trên. Sau đó xét duyệt và cung cấp ID cho địa chỉ kết nối đó. Bắt buộc phải thông qua xét duyệt thì các thiết bị kết nối mới có quyền truy cập mạng
    * Khả năng phát sóng mạnh: Là 1 trạm phát sóng mạng lớn. Khi được kết nối và chia sẻ thông tin với những loại thiết bị khác sẽ được lan truyền thông tin và được phát tán sóng mạng đi đến những địa chỉ thiết bị được PPPoE nhận dạng và cho phép cung cấp
    * Quản lý và khắc phục toàn bộ những lỗi mạng: Xử lý toàn bộ các lỗi kỹ thuật cho các thiết bị trong quá trình sử dụng mạng từ các nhà mạng. Có hệ thống tự điều chỉnh, tự nhận diện và khắc phục sự cố. Hiện này PPPoE có khả năng tự xử lý tất cả những thông tin, vấn đề mà nhà mạng có thể gặp phải như gián đoạn kết nối, bị xâm nhập bởi 1 số thành phần địa chỉ ID không tin cậy,.....
* Ưu điểm
    * Tốc độ cao: PPPoE có thể ngay lập tức nhận diện được tín hiệu các thiết bị yêu cầu và lập tức phát tán tín hiệu, phát tán sóng đi ngay trong vòng vài giây.  
    * Tính bảo mật cao: Toàn bộ thông tin truyền đến PPPoE đều được phân tích vô cùng bí mật. PPPoE đảm bảo sẽ không có bất cứ 1 rò rỉ nào có thể thoát ra bên ngoài được.

# ***II.	Cách thức hoạt động của PPPoE***


* Quy trình của PPPoE gồm 2 giai đoạn:
    * Discovery(Khám phá): PPPoE Client xác định địa chị MAC Ethernet cục bộ và thiết lập ID session. Các host định vị nhiều PPPoE Server, sau đó cho phép người dùng chọn 1 máy chủ.
    * Session(Phiên): Cả host và Server được chọn đều có thông tin về kết nối PPP qua Ethernet. Sau đó, PPPoE cho phép dữ liệu được truyền qua liên kết PPP trong các PPPoE Header. Từ đó, Phiên làm việc được bắt đầu giữa người dùng và web từ xa có thể được kiểm soát

![](https://user-images.githubusercontent.com/52046920/190979340-43c12b40-3dda-4c7b-bfca-38e5a0f23ba5.png)
* Quy trình trên còn được gọi là khám phá PPPoE, cụ thể như sau:
    * Initiation – Phần mềm máy khách gửi một gói PPPoE Active Discovery Initiation (PADI) đến máy chủ để bắt đầu phiên.
    * Offer – Máy chủ phản hồi bằng gói tin Đề nghị phát hiện chủ động PPPoE (PADO).
    * Request – Khi nhận được gói PADO, máy khách phản hồi bằng cách gửi một gói PPPoE Active Discovery Request (PADR) đến máy chủ.
    * Confirmation – Sau khi nhận được gói PADR, máy chủ phản hồi bằng cách tạo một ID duy nhất cho phiên PPP và gửi nó trong gói xác nhận Phiên khám phá hoạt động PPPoE (PADS) tới máy khách.
    * Khi một phiên PPPoE được bắt đầu, địa chỉ IP đích chỉ được sử dụng khi phiên hoạt động. Địa chỉ IP được giải phóng sau khi phiên đóng cửa, cho phép sử dụng lại địa chỉ IP một cách hiệu quả.
# ***III.	Cáu hình PPPoE***

![](https://user-images.githubusercontent.com/52046920/190989246-f9878de1-d3c3-4383-9f7b-de9831e10ba9.png)
* Câu lệnh cấu hình PPPoE như sau
* Tại PPPoE Server
```cicso
PPPoE-Server(config)#interface virtual-template 1
PPPoE-Server(config-if)#ip address 123.0.0.1 255.0.0.0
PPPoE-Server(config-if)#exit
PPPoE-Server(config)#bba-group pppoe PG
PPPoE-Server(config-bba-group)#virtual-template 1
PPPoE-Server(config-bba-group)#int e0/0
PPPoE-Server(config-if)#pppoe enable group PG
PPPoE-Server(config-if)#no shutdown
```
* Tại PPPoE Client
```cicso
PPPoE-Client(config)#interface dialer 1
PPPoE-Client(config-if)#dialer pool 1
PPPoE-Client(config-if)#encapsulation ppp
PPPoE-Client(config-if)#ip address 123.0.0.2 255.0.0.0
PPPoE-Client(config-if)#mtu 1492
PPPoE-Client(config-if)#int e0/0
PPPoE-Client(config-if)#pppoe-client dial-pool-number 1
PPPoE-Client(config-if)#no shutdown

```

* Kiểm tra

```cisco
PPPoE-Server#show pppoe session

PPPoE-Client#show pppoe session
```
* Bên phía client nếu hiển thị trạng thái Up thì là đã thành công.

![](https://user-images.githubusercontent.com/52046920/190989238-bdc02c31-3758-4f43-81d0-3c8e32669884.png)

![](https://user-images.githubusercontent.com/52046920/190989241-5e6a359c-ef4f-4a48-9c2e-ad41d42d793c.png)

* Có thể ping từ client đến server

![](https://user-images.githubusercontent.com/52046920/190989244-249fa0ca-cfdd-47b1-b063-5fe52dfda09d.png)

* Lúc này cổng đi ra ngoài của 
PPPoE-Client sẽ là cổng dialer1. Nếu cấu hình Nat thì ta sẽ phải cấu hinh cổng ra là cổng dialer 1 và trong cổng dialer 1 thêm câu lệnh sau
```cisco
PPPoE-Client(config)#interface dialer 1
PPPoE-Client(config-if)#ip nat outside
```

* Cấu hình xác thực PPPoE
* Tại Server
```cicso
///Tạo Username và Password dùng cho xác thực
PPPoE-Server(config)#username cpe1 password Tai!123
PPPoE-Server(config)#interface virtual-template 1
PPPoE-Server(config-if)#ip address 123.0.0.1 255.0.0.0

///Bật xác Thực
PPPoE-Server(config-if)#ppp authentication chap callin
PPPoE-Server(config-if)#exit
PPPoE-Server(config)#bba-group pppoe PG
PPPoE-Server(config-bba-group)#virtual-template 1
PPPoE-Server(config-bba-group)#int e0/0
PPPoE-Server(config-if)#pppoe enable group PG
PPPoE-Server(config-if)#no shutdown
```

* Tại PPPoE Client
```cicso
PPPoE-Client(config)#interface dialer 1
PPPoE-Client(config-if)#dialer pool 1
PPPoE-Client(config-if)#encapsulation ppp
PPPoE-Client(config-if)#ip address 123.0.0.2 255.0.0.0
PPPoE-Client(config-if)#mtu 1492

///Khai Username và Password để xác thực
PPPoE-Client(config-if)#ppp chap hostname cpe1
PPPoE-Client(config-if)#ppp chap password Tai!123
PPPoE-Client(config-if)#int e0/0
PPPoE-Client(config-if)#pppoe-client dial-pool-number 1
PPPoE-Client(config-if)#no shutdown

```

* Cấu hình PPPoE Server cấp ip tự động cho PPPoE Client
* Tại Server
```cicso
///Tạo pool
PPPoE-Server(config)#ip local pool Mypool 123.0.0.2 123.0.0.50

///Cấu hình PPPoE
PPPoE-Server(config)#username cpe1 password Tai!123
PPPoE-Server(config)#interface virtual-template 1
PPPoE-Server(config-if)#ip address 123.0.0.1 255.0.0.0
PPPoE-Server(config-if)#ppp authentication chap callin

///Câu lệnh cấp ip tự đống
PPPoE-Server(config-if)#peer default ip address pool Mypool
PPPoE-Server(config-if)#exit
PPPoE-Server(config)#bba-group pppoe PG
PPPoE-Server(config-bba-group)#virtual-template 1
PPPoE-Server(config-bba-group)#int e0/0
PPPoE-Server(config-if)#pppoe enable group PG
PPPoE-Server(config-if)#no shutdown
```

* Tại PPPoE Client
```cicso
PPPoE-Client(config)#interface dialer 1
PPPoE-Client(config-if)#dialer pool 1
PPPoE-Client(config-if)#encapsulation ppp
PPPoE-Client(config-if)#ip address negotiated
PPPoE-Client(config-if)#mtu 1492
PPPoE-Client(config-if)#ppp chap hostname cpe1
PPPoE-Client(config-if)#ppp chap password Tai!123
PPPoE-Client(config-if)#int e0/0
PPPoE-Client(config-if)#pppoe-client dial-pool-number 1
PPPoE-Client(config-if)#no shutdown

```

* IP được cấp tự động

![](https://user-images.githubusercontent.com/52046920/190995055-4012b0e2-3de5-4a61-bf67-886844b6ff8f.png)