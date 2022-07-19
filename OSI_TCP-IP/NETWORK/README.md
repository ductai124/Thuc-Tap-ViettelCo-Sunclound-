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

# TÌM HIỂU VỀ TẦNG NETWORK
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
# ***I.	Tổng quan***
* Là tầng thứ 3 trong mô hình OSI
* Tầng này cung cấp đường truyền giữa 2 máy tính của tầng mạng. Cụ thể hơn là chuyển gói tin (segment) của tầng transport từ máy tính này đến máy tính khác.
# ***II. Chức năng***
* Gồm các chức năng chính sau:
    * Routing(Định tuyến): Tìm tuyến đường để gửi dữ liệu từ nguồn tới đích.
    * Forwarding(Chuyển tiếp): chuyển gói tin ở cổng vào đến cổng ra theo đường định tuyến.
    * Addressing(Định địa chỉ): định danh các nút mạng
    * Encapsulating(đóng gói dữ liệu): Nhận dữ liệu từ giao thức ở trên, thêm tiêu đề mang thông tin điều khiển quá trình truyền dữ liệu từ nguồn tới đích.
    * De-Encapsulating(Tách gói tin): Khi gói tín được chuyển đến đích thì nếu đúng ip đích tiến hành xóa tiêu đề ip khỏi gói(hủy đóng gói)
    * QoS(Đảm bảo chất lượng dịch vụ): đảm bảo các thông số phù hợp của đường truyền theo từng dịch
vụ

# ***II. Các giao thức tầng mạng***
* Các giao thức tầng mạng gồm:
    * Giao thức định tuyến: Giúp tìm tuyến đường để gửi dữ liệu. Các giao thức phổ biến RIP (Routing Information Protocol)OSPF ( Open Shortest Path First)
    * Các giao thức báo lỗi, kiểm tra trạng thái nút mạng: ICMP(Internet Control Message Protocol)
## ***1. Định tuyến***
* Là quá trính xác định đường đi tốt nhất trên 1 mạng máy tínhđể gói tin đến được đích thông qua các nút trung gian là các bộ định tuyến(Router).
* Router dựa vào địa chỉ IP đích trong các gói tin và sử dụng bảng định tuyến của mình để xác định đường đi cho chúng.
* Phân loại định tuyến:
    * Định tuyến tĩnh: là quá trình router thực hiện chuyển gói dữ liệu tới địa chỉ mạng đích qua thông tin đương đi được xây dựng bởi bảng định tuyến của router. Bảng định tuyến được thực hiện bởi quản trị và mọi thứ được thiết lập sẵn. Khi có thay đổi gì thì phải thay đổi lại bảng định tuyến
    *  Định tuyến động: Các router tự trao đổi thông tin về các địa chỉ mạng trên sơ đồ, tự chạy một phương thức tính toán nào đó (sử dụng các giao thức) để xác định xem để đi đến các mạng này thì phải sử dụng đường đi nào là tối ưu. 
    * Định tuyến khoảng cách(Distance vector): Chọn đường đi theo hướng và khoảng cách tới đích. 1 bộ định tuyến không cần biết toàn bộ đường dẫn đến mọi phân đoạn mạng, nó chỉ yếu cầu hướng hoặc vector để gửi gói.
    * Link State: Chọn đường đi ngắn nhất dựa vào cấu trúc của toàn bộ mạng theo trạng thái của các đường liên kết mạng.
## ***2. Giao thức ICMP***
* Internet Control Message Protocol(ICMP). Là một giao thức của tầng mạng được sử dụng để thông báo các lỗi xảy ra trong quá trình truyền đi của các gói dữ liệu hay dùng để thăm dò và quản lý trình hoạt động mạng
* ICMP không phải là giao thức truyền tải gửi dữ liệu giữa các hệ thống. ICMP không được sử dụng thường xuyên trong các ứng dụng người dùng cuối mà được sử dụng bởi các quản trị mạng, nhằm mục đích khắc phục các kết nối Internet trong các tiện ích chẩn đoán (diagnostic utilities) bao gồm ping và traceroute
* ICMP được ứng dụng trong Ping và traceroute.
* Thông điệp ICMP được chứa trong các gói tin IP.
* Cách ICMP hoạt động như sau: Ví dụ khi không tìm được đường đến đích, router sẽ tạo và gửi message ICMP kiểu 3 tới máy tính gửi gói tin để báo lỗi. Máy tính nhận đc thông báo lỗi sẽ trả lại mã lỗi cho TCP đang cố gắng kết nối tới máy tính đích, TCP trả lỗi cho ứng dụng.
![]()
* Gói tin ICMP cấu tạo như sau:
    * Type: Dạng gói tin ICMP
    * Code: Nguyên nhân gây lỗi
    * Checksum: Nó là một trường 16 bit để phát hiện xem lỗi có tồn tại trong thông báo hay không.
    * Mỗi dạng sẽ có 1 phần tương ứng khác nhau:
* Các dạng của ICMP
![]()
## ***3. Giao thức IP***
* Internet Protocol là Giao thức liên mạng không liên kết cho phép các gói tin được gửi đến đích đã định sẵn bằng việc thêm thông tin dẫn đường (Header) vào các gói tin.
* Trên Internet thì địa chỉ IP của mỗi người là duy nhất và nó sẽ đại diện cho chính người đó, địa chỉ IP được sử dụng bởi các máy tính khác nhau để nhận biết các máy tính kết nối giữa chúng tuy nhiên không giống với địa chỉ MAC(Là duy nhất) địa chỉ IP vẫn có lúc bị trùng với nhau.
![]()
* Cấu trúc gói tin như sau:
    * VER (4 bits): Version hiện hành của IP đƣợc cài đặt(IPv4 hay IPv6).
    * IHL (4 bits): Internet Header Length của gói tin.
    * Type of service (8 bits): Thông tin về loại dịch vụ và mức ƣu tiên của gói IP:
    * Total Length (16 bits): Chỉ độ dài gói tin
    * Identification (16bits): Định danh cho một gói tin trong thời gian sống của nó.
    * Flags (3 bits): Liên quan đến sự phân mảnh (Fragment) các Datagram:
    * Fragment Offset (13 bits): Chỉ vị trí của phân mảnh trong gói tin.
    * Time To Live (TTL-8 bits): Thời gian sống của một gói dữ liệu.
    * Protocol (8 bits): Chỉ giao thức tầng trên sử dụng TCP(Transmission Control Protocol), UDP(User Datagram Protocol),....
    * Header Checksum (16 bits): Mã kiểm soát lỗi CRC (Cycle Redundancy Check).
    * Source Address (32 bits): địa chỉ của trạm nguồn.
    * Destination Address (32 bits): Địa chỉ của trạm đích.
    * Option (có độ dài thay đổi): Sử dụng trong trƣờng hợp bảo mật, định tuyến đặc biệt.
    * Padding (độ dài thay đổi): Vùng đệm cho phần Header luôn kết thúc ở 32 bits
    * Data (độ dài thay đổi): Độ dài dữ liệu tối đa là 65.535 bytes, tối thiểu là 8 bytes. 

* Đường truyền có một giá trị MTU (Kích thước đơn vị dữ liệu tối đa) 
* Một gói tin IP có kích
thước lớn quá MTU sẽ bị:
    * Chia làm nhiều gói tin nhỏ hơn
    * Được tập hợp lại tại trạm đích
* Quá trình phân mảnh gói tin như sau:
    * P dùng Flag (3 bit thấp của trường Flags trong phần đầu của gói IP) và trường Flagment offset của gói IP (đã bị phân đoạn) để định danh gói IP đó là một phân đoạn và vị trí của phân đoạn này trong gói IP gốc.
    * Các gói cùng trong chuỗi phân mảnh đều có trường này giống nhau. Flag bằng 1 nếu là gói đầu của chuỗi phân mảnh và 0 nếu là gói cuối của gói đã được phân mảnh.
![]
* Ví dụ muốn truyền 1 gói tín có kích cỡ 1980 byte mà độ dài  lớn  nhất  MTU  của  một khung  dữ liệu Ethernet là 1500 byte thì ta tiến hành phân mảnh gói tin ra làm 2
    * Gói 1: Có độ dài 1.500 byte. 20 byte sẽ là tiêu đề IP và 1.480 byte sẽ là dữ liệu. 
    * Gói 2: Có độ dài 500 byte. 20 byte sẽ là tiêu đề IP và 480 byte sẽ là dữ liệu.
