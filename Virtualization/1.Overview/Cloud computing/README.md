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

# TÌM HIỂU VỀ CLOUD COMPUTING
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
# ***I.	Cloud computing là gì***
* Cloud - Đám mây thuật ngữ dùng để chỉ mạng hoặc internet. Nó có thể cung cấp dịch vụ qua các mạng public và private là WAN và LAN hoặc VPN.
* Các ứng dụng e-mail, web, CRM - customer relationship management hay quản lý quan hệ khác hàng thực thi trên Cloud.
* Cloud Computing - Điện toán đám mây để cập tới thao tác, cấu hình và truy cập tài nguyên phần cứng, phần mềm từ xa. Nó cung cấp dữ liệu trực tuyến, cơ sở hạ tầng và ứng dụng. Nó còn cung cấp tính độc lập của nền tảng
# ***II.	Các mô hình triển khai***
* Các mô hình triển khai xác định kiểu truy cập vào Cloud
## ***1. Public Cloud***
* Cho phép hệ thống và các dịch vụ được truy cập dễ dàng bởi mọi người. Public cloud kém bảo mật do tính mở của nó.
* Public cloud là loại hình được vận hành bởi các nhà cung cấp dịch vụ trung gian. Các nhà cung cấp sẽ cung cấp tài nguyên Cloud của họ như máy chủ và bộ nhớ thông qua Internet.
* Người dùng có thể truy cập và quản lý các dịch vụ của mình thông qua trình duyệt. Toàn bộ phần cứng, phần mềm, cơ sở hạ tầng đều do nhà cung cấp dịch vụ sở hữu và quản lý
## ***2. Private Cloud***
* Private cloud chỉ cho phép các dịch vụ và hệ thống được truy cập trong 1 tổ chức. Các tài nguyên đó sẽ chỉ sử dụng riêng cho 1 tổ chức hoặc doanh nghiệp đó mà thôi. Độ bảo mật cao bởi sự riêng tư của mình.
* Lúc này các tài nguyên của hệ thống CNTT trong doanh nghiệp đều được chia sẻ về hệ thống máy chủ tính toán, giúp doanh nghiệp tần dụng được tài nguyên hiệu quả, bảo mật và giảm thiểu được chi phí
* Ngoài ra các doanh nghiệp có thể tận dụng các hạ tầng có sẵn của các đơn vị bên thứ 3 để triển khai dịch vụ riêng cho mình nếu bên cung cấp dịch vụ có thể đảm bảo được hạn tầng đó có thể sử dụng trên 1 mạng riêng
## ***3. Community Cloud***
* Community CLoud cho phép hệ thông và các dịch vụ được truy cập bởi các nhóm tổ chức, doanh nghiệp
* Đây là lựa chọn thích hợp cho các công ty liên doanh, các đơn vị kinh doanh, các tổ chức đấu thầu.
* Nhiều tổ chức thường có nhu cầu về 1 ứng dụng có sẵn tại 1 tập hợp các Cloud Server. Do đó công ty nào có nhiều Server thì không thể cung cấp 1 Server cụ thể trên Cloud được. Ta có thể cho phép nhiều khách hàng kết nối vào Cloud và phân khúc các phiên sử dụng của họ. Khách hàng có thể sử dụng cùng 1 phần cứng với các khách hàng khác. Có thể hiểu là Server sử dụng cùng 1 ứng dụng để tạo ra 1 Community Cloud.
## ***4. Hybrid Cloud***
* Hybrid Cloud là sự kết hợp giữa Public Cloud và Private Cloud. Những hoạt quan trọng cần phải giải quyết bằng Private Cloud thì sẽ chạy trên Private Cloud còn những hoạt động không mấy quan trọng sẽ được thực hiện bằng Public Cloud. 

# ***III.	Mô hình dịch vụ***
* Cloud computing dựa trên các mô hình dịch vụ. Chúng được phân loại thành 3 mô hình dịch vụ cơ bản là:
    * IaaS - Infrastructure as a Service : Có nghĩa là cơ sở hạ tầng như 1 dịch vụ
    * PaaS - Platform as a Service : Có nghĩa là Nền tảng như 1 dịch vụ
    * SaaS - Software as a Service : Phần mềm như 1 dịch vụ
* Ngoài ra còn còn XaaS - Anything as a Service : Có nghĩa là Toàn bộ như 1 dịch vụ và nó bao gồm Network as a Service, Business as a Service, Identity as a Service, Database as a Service hoặc Strategy as a Service

## ***1. IaaS***
* IaaS nó là level cơ bản nhất của dịch vụ. Mỗi 1 mô hình dịch vụ kế thừa cơ chế bảo mật và quản lý cơ chế từ mô hình cơ bản
* Với IaaS, Server có thể quản lý và khởi tạo các tài nguyên cơ sở hạ tầng trên Cloud. Nó cung caosa quyền truy cập vào các tài nguyên cơ bản như máy vật lý, máy ảo, bộ nhớ ảo,... .Người dùng có thể sử dụng phần cứng và phần mềm chỉ bằng cách trả phí
## ***2. PaaS***
* PassS cung cấp nền tảng để khởi tạo, xuất bản và tùy chỉnh phần mềm trong môi trường được lưu trữ.
## ***3. SaaS***
* SaaS cung cấp 1 phương tiện cho phép sử dụng phần mềm từ mọi nơi như 1 dịch vụ cho người dùng