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
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	BGP là gì***
* Là một giao thức định tuyến kết nối Internet với nhau. 
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
* Pulbic AS numbers: 1-64 495 được sử dụng trên mạng Internet toàn cầu
* Private AS numbers: 64 512-65 534 được sử dụng trọng nội vùng.
* 