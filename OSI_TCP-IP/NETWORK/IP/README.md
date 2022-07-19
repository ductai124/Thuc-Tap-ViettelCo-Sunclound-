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

# TÌM HIỂU VỀ IP
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
# ***I.	IP là gì***
* Internet Protocol là Giao thức liên mạng không liên kết cho phép các gói tin được gửi đến đích đã định sẵn bằng việc thêm thông tin dẫn đường (Header) vào các gói tin.
* Trên Internet thì địa chỉ IP của mỗi người là duy nhất và nó sẽ đại diện cho chính người đó, địa chỉ IP được sử dụng bởi các máy tính khác nhau để nhận biết các máy tính kết nối giữa chúng 
* Hiện nay đang có  2 loại là IPv4 và IPv6
# ***II. IPv4 là gì***
* là 1 địa chỉ IP giúp định danh máy tính trên môi trường mạng.
* IPv4 gồm 32 bit chia thành 4 octet
* Cấu trúc gồm phần chính
    * Network ID: địa chỉ mạng
    * Host ID: Địa chỉ của máy
* VD: 203.162.1.12/24
* Phần sau gạch chéo là số bit được sử dụng làm NetID Dạng bit nhị phân   
    <span style="color: red">11001011</span>.<span style="color: red">10100010</span>.<span style="color: red">00000001</span>.<span style="color: blue">00001100</span>  
* Ta có:
    * NetID:<span style="color: red">11001011.10100010.00000001</span>
    * HostID:<span style="color: blue">00001100</span>  
* Quy tắc:
    * Các bit phần mạng không được phép đồng thời bằng 0. ví dụ: địa chỉ 0.0.0.1 là không hợp lệ
    * Nếu các bit phần host đồng thời bằng 1, ta có một địa chỉ quảng bá (broadcast).
    * Nếu các bit phần host đồng thời bằng 0, ta gọi đó là một địa chỉ mạng.

* Lớp mạng được chia làm 5 lớp A,B,C,D,E
    * Lớp A: Có class bit là 0, 1 byte làm NetID và 3 bytes làm Host IP. Bit đầu tiền của lớp A sẽ là 0.
    * Lớp B: Có class bit là 10, 1 bytes là NetID và 2 bytes làm HostID. 2 bit đầu tiên là 10.
    * Lớp C: Sử dụng class bit là 110 3 bytes làm NetID và 1 bytes làm HostID
    *  Lớp D: Multicast
    * Lớp E: Nghiên cứu
* Dải địa chỉ khả dụng cho các lớp:
    * Lớp A: 1.x.x.x – 126.x.x.x .Đây là lớp dành cho các tổ chức lớn trên thế giới. 
    * Lớp B: 128.x.x.x – 191.x.x.x .Đây là lớp dành riêng cho các tổ chức được xếp loại trung trên thế giới.
    * Lớp C: 192.x.x.x – 223.x.x.x .Được dùng cho các tổ chức có quy mô nhỏ, gồm cả máy tính cá nhân. 
    * Lớp D: 224.x.x.x – 239.x.x.x .Lớp D dành cho các tổ chức phát thông tin (multicast/broadcast).
    * Lớp E: 240.x.x.x – 255.x.x.x .Lớp này dành riêng cho công tác nghiên cứu
* Công thức tính số Net và số Host
    * Công thức tính số Net: Nets = $ 2^{n} $
    * Công thức tính Số Host:
    Host = $ 2^{m}-2$

* Trong đó 
    * n : số bits được dùng là Net
    * m: số bits được dùng làm Host
* Giới hạn của các lớp
    * Lớp A: có 27 = 128 Nets, 224 – 2 = 16777214 Host
    * Lớp B: có 214 = 16382 Nest và 216 – 2 = 65534 Host
    * Lớp C: có 221 = 2097150 Nest và 28-2 = 254 Host
    * Lớp D, E không phân chia
## ***1. Các loại địa chỉ IP***
* Public: là địa chỉ IP sử dụng cho các gói tin đi trên môi trường Internet, không thể sử dụng cho mạng LAN. Địa chỉ này là địa chỉ duy nhất cho mỗi hostname tham gia vào Internet.
* Địa chỉ Private: chỉ được sử dụng trong mạng nội bộ (mạng LAN), không được định tuyến trên môi trường Internet. Có thể được sử dụng lặp đi lặp lại trong các mạng LAN khác nhau. Dải địa chỉ private được quy định trong các lớp như sau:
    * Lớp A: 10.0.0.0 => 10.255.255.255
    * Lớp B: 172.16.0.0 => 172.31.255.255
    * Lớp C: 192.168.0.0 => 192.168.255.255
* Kỹ thuật NAT (Network Address Translation) được sử dụng để chuyển đổi giữa IP private và IP public.

* Ý nghĩa của địa chỉ private: được sử dụng để bảo tồn địa chỉ IP public đang dần cạn kiệt.

* Địa chỉ Unicast: Khi muốn gửi một gói tin đến một máy tính cụ thể, nó sẽ gửi dưới dạng Unicast(Point to point).
* Địa chỉ Multicast: đây là trường hợp muốn gửi gói tin đến nhiều máy tính, lúc này ta sẽ không gửi lần lượt tới tất cả các máy mà sẽ gửi đến một địa chỉ đại diện cho nhóm thiết bị đó gọi là địa chỉ Multicast. Đây là dải địa chỉ Lớp D
* Các địa chỉ đặc biệt:
    *  Địa chỉ IP loopback: là loại địa chỉ IP được gửi và nhận dữ liệu của chính nó với Dải địa chỉ IP: 127.x.x.x . Phổ biến nhất là 127.0.0.1 là địa chỉ localhost
    * Địa chỉ NetID: là loại địa chỉ IP có HostID gồm toàn bit 0
    * Địa chỉ broadcast: là loại địa chỉ IP có HostID gồm toàn bit 1. Nó sẽ đại diện cho tất cả các thiết bị kết nối cùng mạng. Khi một gói tin được gửi đến địa chỉ Broadcast, toàn bộ các thiết bị trong mạng đều nhận được. Broadcast gồm 2 loại: 
        * Direct broadcast: ví dụ 192.168.1.255 . Dùng trong trường hợp một thiết bị trong mạng muốn chuyển gói tin đến tất cả các thiết bị trong mạng khác
        * Local broadcast: 255.255.255.255 .Dùng trong trường hợp muốn chuyển gói tin đến toàn bộ các thiết bị trong local


## ***2. Chia địa chỉ IP***
* Kỹ thuật chia một mạng thành nhiều mạng còn được gọi là subnet
* Đặt vấn đề tại sao phải chia mạng: 
    * Tránh xung đột
    * Giảm tải băng thông
    * Dễ dàng trong công tác quản lý
    * Các máy có cùng ip có cùng NetID thì mới làm việc được với nhau
* Để chia mạng người ta sử dụng mặt nạ mạng con - Subnetmask
* Kỹ thuật subnetmask là vay bớt số bit đang được dùng là HostID để làm NetID.
* Subnetmask cho biết số bit được sử dụng là NetID. Nó gồm có 32 bit được chia làm 4 phần giống như IP tuy nhiên tất cả các bit làm NetID đều có giá trị là 1 và tất cả các bit làm HostID đều có giá trị là 0.
* Subnetmask:
    * Lớp A: 255.0.0.0
    * Lớp B: 255.255.0.0
    * Lớp C: 255.255.255.0
* Số prefix: Để mô tả một địa chỉ IP, người ta dùng một đại lượng khác được gọi là số prefix. Nó là số bit mạng trong một địa chỉ IP, viết ngay sau địa chỉ IP và được ngăn cách bằng một dấu “/”.
    * Ví dụ : 192.168.1.1/24 địa chỉ có 24 bit làm bit mạng
                192.168.1.24/29 địa chỉ có 29 bit làm bit mạng
* Trước khi đi vào tính toán ta có 1 số thứ phải nên ghi nhớ:
    * lũy thừa của 2
    * Cách đổi từ thập phân qua nhị phân và ngược lại
    * Bảng bước nhảy:

|Số bit mượn|1|2|3|4|5|6|7|8|
|------|------|------|------|-----|------|------|-----|----|
|Bước nhảy|128|64|32|16|8|4|2|1|
### ***a. Bài toán số 1***
* Bài toán cho 1 mạng và số bit cho mượn, xác định:
    * Số subnet
    * Số host/subnet
    * Địa chỉ mạng của mỗi subnet.
    * Địa chỉ host đầu của mỗi subnet.
    * Địa chỉ host cuối của mỗi subnet.
    * Địa chỉ broadcast của mỗi subnet.
    * Subnet mask được sử dụng.
* Công thức tính: 
    * Ta có n là số bit mượn
    * Ta có m là số bit host còn lại
    * Số subnet có thể chia được(số mạng có thể chia được): 
        * $2^{n}$ nếu hỗ trợ subnet-zero hoặc $2^{n}-2$ nếu không được hỗ trợ subnet-zero.
        * Luật Subnet-zero: nếu OS trên host không bật subnet-zero thì khi chia subnet phải bỏ đi 2 mạng con broadcast và địa chỉ mạng. Nếu địa chỉ mạng bật thì được quyền sử dụng. Do hầu hết hiện tại tính năng này đều bật mặc định vậy nên nếu không có yêu cầu gì thêm mặc định tính năng này được sử dụng.
    * Số host: $ 2^{m}-2 $
    * m+n= tổng số bit Host nếu không cho mượn
    * Mỗi subnet:
        * Địa chỉ mạng: có octet bị mượn(chỉ tính octet chia cắt Net và Host bị mượn bao nhiêu bit) là bội số của bước nhảy ở bảng bước nhảy bên trên.
        * Host đầu: địa chỉ mạng + 1
        * Broadcast: bằng địa chỉ mạng tiêp theo - 1
        * Host cuối: bằng Broadcast - 1
* Bài tập 1: cho mạng 192.168.1.0/24, mượn 2 bit

Giải

* Ta có 2 bit mượn => n = 2 => $ 2^{2} = 4 $ . Vậy ta có số mạng chia được là 4
* m + n = 8 nên m = 6 (số bít Host còn lại)
* $2^{m}-2 = 62$ Host
* Octet số 4 là octet chia cắt Net và Host số bit mượn là 2 nên ta có địa chỉ mạng sẽ là bội số của 64.
* Ta có bảng sau:

|Số thứ tự mạng|Địa chỉ mạng|Địa chỉ Host đầu|Địa chỉ Broadcast|Địa chỉ Host cuối|
|-|-|-|-|-|
|1|192.168.1.0/26|192.168.1.1/26|192.168.1.63/26|192.168.1.62/26|
|2|192.168.1.64/26|192.168.1.65/26|192.168.1.127/26|192.168.1.126/26|
|3|192.168.1.128/26|192.168.1.129/26|192.168.1.191/26|192.168.1.190/26|
|4|192.168.1.192/26|192.168.1.193/26|192.168.1.255/26|192.168.1.254/26|

* Bài tập 2: cho mạng 192.168.12.0/24, mượn 3 bit

Giải

* Ta có 3 bit mượn => n = 3 => $ 2^{3} = 8 $ . Vậy ta có số mạng chia được là 8
* m + n = 8 nên m = 5 (số bít Host còn lại)
* $2^{5}-2 = 30$ Host
* Octet số 4 là octet chia cắt Net và Host số bit mượn là 3 nên ta có địa chỉ mạng sẽ là bội số của 32.
* Ta có bảng sau:

|Số thứ tự mạng|Địa chỉ mạng|Địa chỉ Host đầu|Địa chỉ Broadcast|Địa chỉ Host cuối|
|-|-|-|-|-|
|1|192.168.12.0/27|192.168.12.1/27|192.168.12.63/26|192.168.12.62/27|
|2|192.168.12.32/27|192.168.12.33/27|192.168.12.63/26|192.168.12.62/27|
|3|192.168.12.64/27|192.168.12.65/27|192.168.12.95/26|192.168.12.94/27|
|4|192.168.12.96/27|192.168.12.97/27|192.168.12.127/27|192.168.12.126/27|
|5|192.168.12.128/27|192.168.12.129/27|192.168.12.159/26|192.168.12.158/27|
|6|192.168.12.160/27|192.168.12.161/27|192.168.12.191/26|192.168.12.190/27|
|7|192.168.12.192/27|192.168.12.193/27|192.168.12.223/26|192.168.12.222/27|
|8|192.168.12.224/27|192.168.12.225/27|192.168.12.255/27|192.168.12.254/27|

### ***b. Bài toán số 2***
* Bài toán tóm tắt địa chỉ (summary)
* Mục đích: làm gọn bảng định tuyến của các router. Các địa chỉ mạng sẽ được tóm tắt về một địa chỉ mạng lớn hơn đại diện bao trùm tất cả các mạng được tóm tắt.
* VD:  Hãy tóm tắt các mạng sau đây thành một địa chỉ mạng duy nhất:

            192.168.0.0/24

            192.168.1.0/24

            192.168.2.0/24

            192.168.3.0/24

* Nguyên tắc: khi tóm tắt là xem xét các octet từ trái qua phải và bắt đầu phân tích từ octet có sự khác nhau đầu tiên ở đây là octet thứ ba là octet khác nhau đầu tiên. Ta xét chi tiết octet này:

            192.168.|000000|00.0

            192.168.|000000|01.0

            192.168.|000000|10.0

            192.168.|000000|11.0

* Ta thấy octet thứ ba còn có thêm 6 bit giống nhau. Vậy ta có mạng tóm tắt là 192.168.0.0/22. Chú ý: subnet mask bây giờ là 255.255.252.0 với prefix là 22.
### ***c. Bài toán số 3 Cho sơ đồ mạng, xác định số bit mượn phù hợp để chia subnet***
* Ví dụ: Cho một mạng 192.168.1.0/24. Hãy cung cấp đủ các địa chỉ IP cho 5 mạng như sau:
![](https://vnpro.vn/upload/images/Th%C6%B0%20vi%E1%BB%87n/Ch%C6%B0%C6%A1ng%201/chuong-1-dia-chi-ip-chia-subnet-vlsm-summary-10.jpg)
* Nhận thấy có tất cả 5 mạng (tính ra 2 router nối nhau là 1 mạng), mạng nhiều host nhất là mạng có 26 host (cộng thêm một địa chỉ cổng router). Gọi số bit mượn là n số bit host là m. Ta có: 
* $2^{n}$ ≥ 5 (số mạng chia ra tối thiểu phải bằng 5).

* $2^{m}$ – 2 ≥ 26 (nếu mỗi mạng con đáp ứng được số host của mạng 26 host, nó sẽ đáp ứng được yêu cầu về số host của tất cả các mạng còn lại trên sơ đồ).
* m + n = 8

n = 3, m = 5 là phù hợp. Vậy ta có tất cả 23 = 8 mạng và mỗi mạng này có 25 – 2 = 30 host, đáp ứng được yêu cầu của sơ đồ trên.
* Các mạng như sau:
|Số thứ tự mạng|Địa chỉ mạng|
|-|-|
|1|192.168.1.0/27|
|2|192.168.1.32/27|
|3|192.168.1.64/27|
|4|192.168.1.96/27|
|5|192.168.1.128/27|
|6|192.168.1.160/27|
|7|192.168.1.192/27|
|8|192.168.1.224/27|

### ***d. Bài toán số 4 Chia subnet VLSM***