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

# TÌM HIỂU VỀ Kỹ thuật AAA hỗ trợ xác thực và phân quyền Telnet trên thiết bị 
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
# ***I.	Kỹ thuật AA hỗ trợ xác thực và phân quyền Telnet***
* AAA là Authentication(xác thực) Authorization(phân quyền) Accounting(kiểm toán). Nó hỗ trợ 3 cái dịch vụ như tên gọi của nó
    * Authentication(Xác thực): chỉ có ai biêt username và password mới được quyền truy cập telnet đến thiết bị.
    * Authorization(phân quyền): các người dùng sẽ được phân quyền và tùy vào quyền của người dùng thì sẽ bị giới hạn các câu lệnh cấu hình.
    * Accounting(kiểm toán): ghi lại nhật ký hoạt động của hệ thống mạng như: User nào đã telnet vào hệ thống, từ lúc nào và trong thời gian bao nhiêu, đã thực hiện những câu lệnh gì

# ***II.	Xác thực Authentication***
* Cấu hình phương thức xác thực dịch vụ telnet bằng câu lệnh sau.
```cisco
R1(config)#aaa new-model
R1(config)#aaa authentication login localAAA local          ///local AAA là tên bất kỳ, phương thức xác thực local 

R1(config)#username admin password 123456           ///Username và mật khẩu phục vụ cho xác thực người dùng

R1(config)#username tai password tai123
R1(config)#line vty 0 4
R1(config-line)#login authentication localAAA
```

```cisco
R1(config)#enable secret level 15 tai123
```
* Kiểm tra các user đang telnet

![]()
![]()

# ***III.	Phân quyền Authorization***
* Cisco router hỗ trợ 16 cấp độ bảo mật từ level 0-15. level 1 tương ứng với chế độ User EXEC Mode.
* Để truy cập vào level từ 2-14 thì cần phải định nghĩa các phân quyền của các level. Các level trên đều có thể sử dụng các câu lệnh ở level 1
* Các câu lệnh
```cisco
R1(config)#enable secret level 8 ciscolv8          ///Thiết lập mật khẩu enable level 8

///Phân quyền cho level 8
R1(config)#privilege exec level 8 show interfaces
R1(config)#privilege exec level 8 show running-config
R1(config)#privilege exec level 8 configure terminal

/// Đối với các câu lệnh trên tương ứng với chế độ privilege EXEC Mode và cho phép thực hiện 3 câu lệnh ở sau level 8 là show interfaces, show running-config, configure terminal. Các câu lệnh khác ở chế độ này sẽ không được quyền sử dụng


R1(config)#privilege configure level 8 interface
R1(config)#privilege interface level 8 ip address

/// Đối với các câu lệnh trên tương ứng với chế độ 
global configure mod(R1(config)#), và chế độ con của nó là là configure interface (R1(config-if)#). Ở chế độ global configure mod thì chỉ được thao tác với lệnh interface, muốn thao tác đến những cổng nào cần thiết lập thêm vào câu lệnh trên. Ở chế độ con configure interface chỉ được thiết lập địa chỉ ip và không được tắt bật cổng.

```
* Các mod có thể định nghĩa

![](https://user-images.githubusercontent.com/52046920/182798660-6414bdeb-4e1e-4633-aaa1-02e6de29a659.png)
* Ở chế độ 15 ta có thể toàn quyền cấu hình thiết bị mà không bị giới hạn bới bất cứ câu lệnh nào.
* Muốn truy cập vào level 8 trên thì thực hiện câu lệnh
```cisco
R1> enable 8 
///kiểm tra level đang truy cập
R1# show privilege
```

![](https://user-images.githubusercontent.com/52046920/182798664-11825e7c-3980-45af-8a51-a8d4949c666d.png)
* Kiểm tra phân quyền, telnet vào router và truy cập level 8, kiểm tra các câu lệnh đã được định nghĩa show interfaces, show running-config, configure terminal. Kiểm tra câu lệnh show startup-config và ta nhận thấy không được sử dụng, kiểm tra bằng câu lệnh hostname cũng nhận thấy không sử dụng được do chưa được định nghĩa cho level này 

![](https://user-images.githubusercontent.com/52046920/182798666-544d0e6b-a241-46cb-ba67-3a108e766d4f.png)
![](https://user-images.githubusercontent.com/52046920/182798669-7d484ac5-8d96-4bff-963c-803e302f0330.png)

* Còn có thể cấp quyền cho người dùng bằng câu lệnh
```cisco
R1(config)#username admin privilege 15 password tai123          ///Cấp trực tiếp quyền 15 cho user admin và user này khi đăng nhập sẽ đăng nhập thằng vào mod privilege với level 15
```
# ***IV.	Nhật ký truy nhập mạng Accounting***
* Trong quá tình hiệu chỉnh cấu hình của hệ thống mạng có thể xảy ra lỗi, không ổn định. Để kiểm tra ta cần truy cập nhật ký để kiểm tra lại các câu lệnh đã sử dụng xem vấn đề đang xảy ra ở đâu
```cisco
R1(config)#archive
R1(config-archive) log config
R1(config-archive-log-cfg) logging enable
```
* Kiểm tra lại log bằng câu lệnh
```cisco
R1# show archive logg config all
```

# ***V.	Login Block-For giới hạn số lần***
* Đối với các router được public ra ngoài mạng nguy cơ bị tấn công khá cao vì vậy để hạn chế việc bị tấn công dò mật ta sử dụng chức năng login block-for. Sử dụng câu lệnh sau
```cisco
login block-for 120 attempts 2 within 60
\\\trong vòng 60 giây chỉ được đăng nhập thất bại 2 lần nếu vượt quá sẽ tạm thời bị chặn trong khoảng 120 giây
```
* Để kiểm tra ta sử dụng câu lệnh
```cisco
R1#show login
R1#show login failures           ///Kiểm tra ip telnet thất bại
```
* show login khi không có máy nào xác thực thất bại

![](https://user-images.githubusercontent.com/52046920/182798683-ce57d437-363c-49a0-b9a7-8526e1ad8196.png)

* show login khi có máy xác thực thất bại vượt quá số lần quy định sẽ hiện thời gian đếm ngược để có thể tiếp tục telnet

![](https://user-images.githubusercontent.com/52046920/182798676-1b3d6eb5-f516-48f0-9c93-02f5940f6db0.png)

* show login failures

![](https://user-images.githubusercontent.com/52046920/182798652-488e4f89-a6f0-4b84-9111-bda2f42acb78.PNG)
# ***VI.	Xác thực Telnet bằng RADIUS Server***
* Radius Server là một máy chủ xác thực hỗ trợ xác thực và quản lý tập trung.
* Cấu hình như sau
```cisco
R1(config)#aaa new-model
R1(config)#aaa authentication login Central group radius local
R1(config)#radius server RAS
R1(config-radius-server)#address ipv4 192.168.1.4 
R1(config-radius-server)#key bqk
R1(config-radius-server)#exit
R1(config)#username admin privilege 15 password tai123          ///Mật khẩu local nếu radius server lỗi
R1(config)#line vty 0 4
R1(config-line)#login authentication Central

```
* Trên radius server thiết lập như sau

![](https://user-images.githubusercontent.com/52046920/182798686-d25a9e1e-5410-40aa-92ed-135c0fdaf9b8.png)
* Có thể xác thực bằng username và mất khẩu trên radius server

![](https://user-images.githubusercontent.com/52046920/182798694-123e3fd9-4da1-4a88-a136-82c8b3071f0a.png)
* Vẫn có thể xác thực bằng tài khoản và mật khẩu local nếu radius lỗi

![](https://user-images.githubusercontent.com/52046920/182798691-0b8595a7-0a70-490b-b0db-9f335763ed86.png)