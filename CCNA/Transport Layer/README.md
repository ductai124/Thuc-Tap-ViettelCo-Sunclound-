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

# TÌM HIỂU VỀ TRANSPORT LAYER
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
# ***I.	TRANSPORT LAYER là gì***
* Transport Layer - Tầng giao vận, là tầng thứ 4 trong mô hình osi. 
* Tầng vận chuyển kiểm soát hoạt động truyền dữ liệu giữa 2 máy. Nói cách khác là quản lý và thực hiện các tác vụ truyền dữ liệu từ đầu cuối đến đầu cuối đảm bảo hoạt động này diễn ra hiệu quả nhất
* Các giao thức tiêu biểu tầng Transport sử dụng :
    * TCP(Transmission Control Protocol)
    * UDP(User Datagram Protocol)
# ***II.	Chức năng***
* Tầng vận chuyển Thực hiện 5 chức năng chủ đạo sau
    * Ghép phiên kết nối
    * Phân mảnh dữ liệu
    * Bắt tay 3 bước trước khi thực hiện quá trình tuyền thông
    * Đảm bảo truyền thông tin cậy
    * Điều khiển luồng

## ***1.	Ghép phiên kết nối(Session multiplexing)***
* Tổ chức ghép nối các phiên làm việc giữa 2 máy tính vào 1 đường truyền duy nhất
## ***2.	phân mảnh dữ liệu(Segmenttation)***
* Quá trình chia nhỏ dữ liệu từ tầng trên đưa xuống thành các Segment rồi chuyển đi
## ***3.	Bắt tay 3 bước(three-way handshake)***
* Lớp Transport cung cấp 2 cơ chế truyền dữ liệu: Connection oriented và Connectionless.
* Connection oriented  là một quá trình gồm 3 giai đoạn: 
    * Thiết lập kết nối
    * Truyền dữ liệu
    * Kết thúc / Ngắt kết nối
* Connection oriented được sử dụng ở giao thức TCP.
* Connectionless: khi máy có gói tin thì nó lập tức đẩy ngay gói tin vào đường truyền mà nó không cần thiết lập kết nối từ trước. Connectionless được sử dụng ở giao thức UDP.

## ***4.	Truyền thông tin cậy(Reliability)***
* Khi máy nguồn gửi cho máy đích một gói tin thì phải chắc chắn rằng máy đích sẽ nhận được gói tin này. Máy nhận khi nhận được gói tin thì phải gửi lại 1 gói tin thông báo đã nhận được gói tin từ phía máy gửi. Nếu máy nhận không thông báo lại thì máy gửi sẽ gửi gói tin liên tục cho đến khi máy nhận gửi thông báo đã nhận được.
* Tùy theo giao thức được sử dụng thì truyền thông tin cậy sẽ được áp dụng. Áp dụng với TCP và không áp dụng với UDP
## ***5.	Điều khiển luồng(Flow control)***
* 	Khi máy gửi gửi quá nhiều dữ liệu cho máy nhận, nếu máy nhận xử lý không kịp thì gói tin có thể sẽ bị hủy bỏ hay mất gói dữ liệu. Lúc này máy nhận sẽ gửi tín hiệu yêu cầu máy gửi chuyển dữ liệu chậm lại. 
* Cơ chế này không phải giao thức nào cũng có. không phải lúc nào cơ chế này cũng được thi hành mà chỉ khi nào có yêu cầu thì mới có. Nó tồn tại trên TCP, UDP không sử dụng
# ***II.	Giao thức***
## ***1.	Giao thức TCP***
* Là một giao thức truyền tải hướng kết nối. Phải thực hiện quá trình bắt tay 3 bước trước khi kết nối:
    * Thiết lập kết nối
    * Truyền dữ liệu
    * Kết thúc / Ngắt kết nối
* Cung cấp cơ chế báo nhận(Acknowledgement)
* Cung cấp cơ chế đánh số thứ tự gói tin cho các đơn vị dữ liệu được truyền sử dụng để ráp lại các gói tin ở điểm nhận và loại bỏ gói tin trùng nhau
* Cơ chế điều khiển luồng tránh nghẽn
* Hỗ trọ cơ chế truyền và nhận dữ liệu cùng lúc
* Phục hồi dữ liệu bị mất trên đường truyền nếu không thấy xác nhận gửi sẽ gửi lại.
* Cấu trúc gói tin

![](https://images.viblo.asia/ca199b5e-2deb-42b0-ac36-33dbf30f3e20.png)

* Source port(16 bit): Cổng của máy gửi
* Destination port(16 bit): Cổng máy nhận
* Sequence number(32 bit): Trường này có 2 nhiệm vụ:
    * Cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tin gửi có số thứ tự + 1. 
    * Nếu không có cờ thì đây là số thứ tự của byte đầu tiên
* Acknowledgement number(32 bit): dùng để báo đã nhận được gói tin nào và mong nhận được byte mang số thứ tự nào tiếp theo
* Header length