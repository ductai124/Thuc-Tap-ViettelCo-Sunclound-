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
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	Định tuyến là gì***

* Định tuyến hay còn gọi là routing là quá trình tìm và xác định đường đi tốt nhất để truyền tiếp dữ liệu tới nút đích thông qua các thiết bị định tuyến. Router dựa vào IP đích trong các gói tin và bảng định tuyến (Routing Table) để xác định đường đi cho chúng.

* Có 2 loại định tuyến là:
    * Định tuyến tĩnh
    * Định tuyến động
## ***1.	Định tuyến tĩnh***
* Định tuyến tĩnh là loại định tuyến mà trong đó router sử dụng các tuyến đường đi tĩnh để vận chuyển dữ liệu đi. Các tuyến đường đi tĩnh được thiết lập thủ công và cố định.
* Default router là 1 định tuyến mặc định được sử dung khi chưa cấu hình đường đi nào để định tuyến mặc định tất cả dữ liệu đến một mạng bất kỳ đi theo đường nào đó. Nhưng nếu mạng đó đã có đường đi trong bảng định tuyến, thì gói tin sẽ ưu tiên đi theo đường đi rõ ràng trước.
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
# ***II.	Tổng quan về kỹ thuật định tuyến***
