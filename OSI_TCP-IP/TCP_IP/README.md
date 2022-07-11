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

# TÌM HIỂU VỀ MÔ HÌNH TCP/IP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I.	Mô hình TCP/IP là gì]()

## &ensp; [1. Tầng vật lý (Network Access)]()

## &ensp; [2. Tầng mạng (Internet)]()

## &ensp; [3. Tầng vận chuyển (Transpot)]()

## &ensp; [4. Tầng ứng dụng (Application)]()

# [II.	Cách thức hoạt động]()

# [II.	So sánh với OSI]()
## &ensp; [1. Giống nhau]()
## &ensp; [2. Khác nhau]()
***
# ***I.	Mô hình TCP/IP là gì***
* TCP/IP(Transmission Control Protocol/ Internet Protocol) là 1 tập hợp các giao thức trao đổi thông tin được sử dụng để truyền tải và kết nối các thiết bị trong mạng. Nó chỉ rõ cho chúng ta cách thức đóng gói thông tin, được gửi và nhận bởi các máy tính có kết nối với nhau
* Một mô hình TCP/IP bao gồm 4 tầng gồm:
    1. Tầng vật lý (Network Access)
    2. Tầng mạng (Internet)
    3. Tầng giao vận (Transport)
    4. Tầng ứng dụng (Application)
* Đi vào chi tiết các tầng như sau
## ***1. Tầng vật lý (Network Access)***
* Là sự kết hợp của tầng Datalink và Physical trong mô hình OSI.
* Chịu trách nhiệm truyền dữ liệu giữa các thiết bị trong cùng một mạng. Tại đây các gói dữ liệu được đóng vào Frame và được định tuyết đi đến đích được chỉ định ban đầu.
## ***2. Tầng mạng (Internet)***
* Được định nghĩa là một giao thức chịu trách nhiệm truyền tải dữ liệu một cách logic trong mạng.
* Tầng mạng có vai trò:
    * Xử lý quá trình truyền gói tin trên mạng.
    * ĐỊnh tuyến: tìm tuyết đường qua các nút trung gian để gửi dữ liệu từ nguồn tới đích
    * Chuyển tiếp: chuyển tiếp gói tin từ cổng nguồn tới cổng đích theo tuyến đường.
    * Định danh các nút mạng
    * Nhận dữ liệu từ giao thức, chèn thêm header chứ thông tin của tầng mạng và chuyển đến tầng tiếp theo
    * Đảm bảo thông số phù hợp của đường truyền theo từng dịch vụ
* Tầng mạng sử dụng 3 giao thức chính: 
    * IP
    * ICMO
    * ARP
## ***3. Tầng vận chuyển (Transpot)***
* Có chức năng xử lý các vấn đề trong quá trình giao tiếp của các máy chủ. Các máy chủ này có thể trong cùng 1 mạng hoặc khác mạng. Nếu khác mạng, các máy chủ sẽ được kết nối thông qua bộ định tuyến.
* Dữ liệu ở tầng giao vận sẽ được phân thành các đoạn có kích thước khác nhau và nhỏ hơn 64KB. Cấu trúc một segment gồm đoạn Header chứa thông tin điều khiển, sau header là các đoạn dữ liệu.
* Tầng này có 2 giao thức:
    * TCP: giúp đảm bảo chất lượng thông tin trong quá trình truyền nhận. Tuy nhiên sẽ mất nhiều thời gian do việc kiểm tra thứ tự thông tin lâu
    * UDP: Có thời gian truyền dữ liệu nhanh hơn nhưng sẽ không đảm bảo chất lượng dư liệu như TCP
## ***4. Tầng ứng dụng (Application)***
* Tầng ứng dụng cung cấp giao diện người dùng
* Cung cấp các ứng dụng cho phép người dùng trao đổi dữ liệu ứng dụng thông qua các dịch vụ mạng khác nhau
* Một số giao thức của tầng ứng dụng: 
    * SMTP
    * SSH
    * FTP
...
* Dữ liệu khi đến đây sẽ được định dạng theo byte by byte, cùng với đó là thông tin định tuyết giúp xác định đường đi đúng của một gói tin

# ***II.	Cách thức hoạt động***
* TCP/IP là kết hợp của 2 giao thức:
    * IP(Giao thức liên mạng) cho phép các gói tin được gửi đến đích đã định sẵn bằng việc thêm thông tin dẫn đường vào các gói tin.
    * TCP(Giao thức truyền vận) đóng vai trò kiểm tra, đảm bảo an toàn cho các gói tin đi qua mỗi trạm. Nếu TCP nhận thấy gói tin lỗi nó sẽ phát tín hiệu yêu cầu hệ thống gửi lại gói tin khác

# ***II.	So sánh với OSI***
## ***1. Giống nhau***
* 2 mô hình có những điểm tương đồng sau:
    * Đều là mô hình logic có kiến trức phân lớp
    * đều có tầng giao vận và tầng vận chuyển
    * cùng sử dụng kỹ thuật truyền packet

## ***2. Khác nhau***
* Hình ảnh quy chiếu OSI qua TCP/IP 
![Hình ảnh quy chiều OSI qua TP/IP](https://codelearnstorage.s3.amazonaws.com/Upload/Blog/tim-hieu-osi-va-tcpip-63733700999.9992.jpg)

| Nội dung | OSI | TCP/IP |
|:------------------------------------------:|:------------------------------------------:|:------------------------------------------:|
| Độ tin cậy và phổ biến | Được nhiều người cho rằng chỉ là mô hình tham khảo và đã cũ nên hạn chế sử dụng| Được chuẩn hóa, nhiều người tin cậy và sử dụng phổ biến|
| Phương pháp tiếp cận| Theo chiều dọc| Theo chiều ngang |
| Sự kết hợp giữa các tầng | Mỗi tầng khác nhau sẽ thực hiện một nhiệm vụ khác nhau, không có sự kết hợp giữa bất cứ tầng nào | Trong tầng ứng dụng có tầng trình diễn và tầng phiên được kết hợp với nhau| 
|Phát triển| Mô hình trước giao thức sau| Giao thức trước mô hình sau |
|Số tầng| 7 | 4 |
|Hỗ trợ truyền thông| Hỗ trợ cả không dây và kết nốt định tuyến| Hộ trợ truyền thông không kết nối từ tầng mạng|
|Tính phụ thuộc| Độc lập| Phụ thuộc vào giao thức|


