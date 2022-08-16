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

# TÌM HIỂU VỀ SSH
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. SSH là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/169125346fbe8bad4e2c66a7da7565bb1b7a57d9/CCNA/6.Telnet/SSH/README.md#issh-l%C3%A0-g%C3%AC)
# [II. Cơ chế hoạt động](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/169125346fbe8bad4e2c66a7da7565bb1b7a57d9/CCNA/6.Telnet/SSH/README.md#iic%C6%A1-ch%E1%BA%BF-ho%E1%BA%A1t-%C4%91%E1%BB%99ng)
# [III. Cấu hình SSH](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/169125346fbe8bad4e2c66a7da7565bb1b7a57d9/CCNA/6.Telnet/SSH/README.md#iiic%E1%BA%A5u-h%C3%ACnh-ssh)
***
# ***I.	SSH là gì***
* SSH  hay Secure Shell, là một giao thức hỗ trợ các nhà quản trị mạng truy cập vào máy chủ từ xa thông qua mạng internet không bảo mật.
* SSH tạo ra cơ chế xác thực qua mật khẩu mạnh, hình thành mối liên kết giao tiếp dữ liệu mã hóa ra giũa 2 máy qua mạng. 
# ***II.	Cơ chế hoạt động***
* SSH hoạt động theo mô hình CLient-Server để xác thực hai bên và mã hóa dữ liệu giữa chúng. CLient sẽ là thành phần tạo phiên kết nối SSH đến thành phần khác. Server sẽ cho phép Client mở pheien SSH kết nối vào mình
* Có 3 bước chính:
    * Bước 1: Khởi tọa kết nối SSH, chính là tạo ra kênh giao tiếp bảo mật giữa Server và Client.
    * Bước 2: CLient xác thực Server. Sau khi CLient xác định được định danh của Server, 1 kết nối bảo mật đối xứng được hình thành giữa 2 bên
    * Bước 3: Server xác thực CLient dựa trên kết nối được thiết lập ở trên

![](https://vnpro.vn/upload/images/ssh-la-gi-cach-hoat-dong-cua-ssh.jpg)

# ***III.	Cấu hình SSH***
* Tiến hành cấu hình cho máy tính có thể SSH được đến router

![](https://user-images.githubusercontent.com/52046920/184822863-83ddefd6-f398-476d-89f5-bff69e0c8025.png)

|Thiết bị|IP|
|--|--|
|Router e0/0|192.168.1.1/24|
|PC|192.168.1.2/24 và default gateway là 192.169.1.1/24|

```cisco
///Cấu hình cơ bản cho router
Router(config)#hostname R1
R1(config)#int e0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#no shut
Router(config-if)#exit
Router(config)#enable password 123


///Đặt Domain-name cho router và router sẽ dùng domain name này để tạo SSH key mã hóa
R1(config)#ip domain-name test.org

///Tạo key mã hóa rsa
R1(config)#crypto key generate rsa
///Sau đó nhập số có giá trị trên 768 do hiện nay chủ yếu chỉ hỗ trợ SSH 2

///Kiểm tra key được tạo ra bằng câu lệnh sau
R1#show crypto key mypubkey rsa

///Cấu hình mật khẩu và chuyển phương thức truy cập vty thành SSH do mặc định của nó là telnet
Router(config)#username admin password 123
Router(config)#line vty 0 4
Router(config-line)#transport input ssh
Router(config-line)#login local
Router(config-line)#exit


```
* Key được tạo ra

![](https://user-images.githubusercontent.com/52046920/184822866-1265a02e-e32b-4d04-b9bc-3b4f89a1816c.png)
* Tiền hành SSH đến router

![](https://user-images.githubusercontent.com/52046920/184822869-47aa3fb5-18ad-4136-954c-9be1350b7c46.png)
