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

# TÌM HIỂU VỀ RESTORE ISO ROUTER
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

# ***I.	Hướng dẫn khôi phục HDH IOS***
* Cisco Internetwork Operating System(Cisco IOS) thông thường được lưu trong bộ nhớ Flash của router. trong quá trình khởi động router sẽ tải hệ điều hành đó lên và chạy trực tiếp trên Ram
* Bên cạnh hệ điều hành chính ta còn 1 hệ điều hành phụ gọi là mini ISO được lưu trữ trong ROM. Khi hệ điều hành chính bị lỗi thì router sẽ sử dụng tạm mini IOS
* Vậy nếu muốn khôi phục lại ISO khi hệ điều hành này hỏng thì ta sẽ phải đứng tại mini ISO thì và tiến hành khôi phục lại IOS
* Các biến phải khai báo
    * FE_PORT=0(Cổng kết nối router) 
    * IP_ADDRESS=192.168.1.1(Địa chỉ ip của cổng Router)
    * IP_SUBNET_MASK=255.255.255.0(Subnet mask của địa chỉ IP trên)
    * DEAFAULT_GATEWAY=(Nếu router và Server kết nối với nhau thì không cần khai báo còn nếu không thì khai báo địa chỉ ip của server)
    * TFTP_SERVER=192.168.1.2(IP của server)
    * TFTP_FILE=isr4300-universalk9.16.06.04.SPA.bin(Tên file muốn lấy về) 
* Tiến hành khổi phục hệ điều hành với mô hình như sau

![](https://user-images.githubusercontent.com/52046920/182059368-34ff07d3-9a00-4056-98c2-17957752a6df.png)
* Tiến hành thử nghiệm xóa file hệ điều hành của router đi và tiến hành khôi phục
    ```cisco
    R1# delete flash:
    R1# reload
    ```

![](https://user-images.githubusercontent.com/52046920/182059370-8424733d-f933-4c46-9b48-158ef4a80981.png)
* Khai báo các giá trị sau
```cisco
rommon 1 > GE_PORT=0
rommon 2 > IP_ADDRESS=192.168.1.1
rommon 3 > IP_SUBNET_MASK=255.255.255.0
rommon 4 > DEFAULT_GATEWAY=192.168.1.4
rommon 5 > TFTP_SERVER=192.168.1.4
rommon 6 > TFTP_FILE=isr4300-universalk9.16.06.04.SPA.bin
```
* Ngoài ra còn có các lệnh
```cisco
rommon>SET         ///Kiểm tra lại các thông tin
rommon>unset GA_PORT            ///Gỡ biến được khai báo
```
![](https://user-images.githubusercontent.com/52046920/182059973-3709fb3c-0baa-4c6e-bf16-9aca104f2698.png)

* Khi đã khai báo các biên đúng giá trị thì ta tiến hành lấy file hệ điều hành về từ tftp server
```cisco
rommon> tftpdnld
```

![](https://user-images.githubusercontent.com/52046920/182059374-c0a8d817-f78b-4a3a-ada0-ecd66ab5c213.png)
* Sau khi tải về file hệ điều hành ta có thể tiến hành kiểm tra bằng câu lệnh
```cisco
rommon> dir flash:
rommon> reset           ///khởi động lại thiết bị để nó chạy file hệ điều hành
```
![]()
* Hệ điều hành được khôi phục thành công
