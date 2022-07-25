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

# TÌM HIỂU VỀ ROUTER VÀ CẤU HÌNH ROUTER CƠ BẢN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Router là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Router#irouter-l%C3%A0-g%C3%AC)

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
***
# ***I.	Router là gì***
* Router (thiết bị định tuyến hoặc bộ định tuyến) là thiết bị mạng dùng để chuyển các gói dữ liệu đến các thiết bị đầu cuối. Nói một cách dễ hiểu, Router là một thiết bị để chia sẻ Internet tới nhiều các thiết bị khác trong cùng lớp mạng.
* Các thành phần của Router là :
    * CPU — bộ xử lý trung tâm, các bạn chỉ cần hiểu nó giống như CPU của máy tính.
    * ROM — chứa chương trình kiểm tra khởi động (POST), Bootstrap (giống BIOS của máy tính) và Mini-IOS (recovery password, upgrade IOS). Nhiệm vụ chính của ROM là kiểm tra phần cứng khi khởi động, sau đó chép HĐH Cisco IOS từ flash vào RAM. Nội dung trong bộ nhớ ROM thì không thể xóa được.
    * RAM/DRAM — lưu trữ routing table, ARP cache, fast-switching cache, packet buffering (shared RAM), và packet hold queues (một số thuật ngữ đi vào các bài học sau các bạn sẽ hiểu từ từ); Đa số HĐH Cisco IOS chạy trên RAM; RAM còn lưu trữ file cấu hình đang chạy của router (running-config). Nội dung RAM bị mất khi tắt nguồn hoặc restart router.
    * FLASH — lưu toàn bộ HĐH Cisco IOS; giống với Harddisk trên máy tính.
    * NVRAM — non-volatile RAM lưu trữ file cấu hình backup/startup của router (startup-config); nội dung của NVRAM vẫn được giữ khi tắt nguồn hoặc restart router.
    * Interfaces — còn gọi là cổng, được kết nối trên board mạch chủ hoặc trên interface modules riêng biệt, qua đó những packet đi vào và đi ra router. Cổng Console sử dụng cáp rollover, dùng để cấu hình trực tiếp cho router. Cổng AUX giống với cổng console, nhưng sử dụng kết nối dial-up tới modem, hỗ trợ việc cấu hình từ xa. Còn lại là các cổng kết nối mạng thông thường: Gigabit, Fast Ethernet, Serial, …

# ***II.	Cấu hình Router cơ bản***
![](https://static.cuongquach.com/resources/images/2017/08/type-mode-config-router.jpg)
* Có 3 chế độ cấu hình cơ bản:
    * User EXEC Mode: bắt đầu bằng dấu “>”, cho phép các câu lệnh hiển thị thông tin một cách hạn chế, câu lệnh kết nối (ping, traceroute, telnet, ssh, …).
    * Priviledged EXEC Mode: bắt đầu bằng dấu “#”, cho phép toàn bộ câu lệnh hiển thị, một số cấu hình cơ bản (clock, copy, erase, …).
    * Global Configuration Mode: bắt đầu bằng “(config)#”, cho phép toàn bộ câu lệnh cấu hình lên router. Bên trong mode này, sẽ có các mode con cho từng loại cấu hình riêng biệt.
* Tiến hành cấu hình router cơ bản trên Cisco packet tracer
* Đầu tiên tạo 1 router sau đó double click vào router đó rồi chọn tab CLI và đợi Router khởi động
* Chọn no để tiến hành tự thiết lập cấu hình router
```Cisco
Would you like to enter the initial configuration dialog? [yes/no]:no
```
* – Chế độ User sẽ giới hạn các câu lệnh mà người dùng có thể thực thi được. Đối với chế độ cấu hình này người dùng chỉ có khả năng hiển thị các thông số cấu hình trên router. Không thể cấu hình để thay đổi các thông số cấu hình và hoạt động của router.

```cisco
Router>
```
* Truy cập Chế độ Priviledged EXEC Mode.
```cisco
Router> enable
Router#
```
* Truy cập Chế độ Global Configuration.
```cisco
Router# config terminal
Router(config)#
```
* Quay lại chế độ Privileged
```cisco
Router(config)#
Router# exit
```
* Quay lại chế độ User EXEC Mode
```cisco
Router# disable
Router> 
```
* Có thể sử dụng tính năng hỗ trợ gợi nhớ câu lệnh bằng cú cách gõ ?
* ví dụ:
![](https://user-images.githubusercontent.com/52046920/180779798-73ad59c9-c0e5-4348-aeec-6d70a59ceb32.png)
![](https://user-images.githubusercontent.com/52046920/180779801-e50f4f31-7fbc-4ecf-be2c-94b6ea90a465.png)
![](https://user-images.githubusercontent.com/52046920/180779804-ae3ca013-f99c-4d25-8073-151f446ed048.png)

## ***1. Tiến hành cấu hình hostname cho Router***
* Tiến hành truy cập vào chế độ Global Configuration Mode
```cisco
Router> enable
Router# config terminal
Router(config)#
```
* Tiến hành đặt tên Host name cho thiết bị
```
Router(config)# hostname Tai
Tai(config)#
```
* Nếu muốn đổi Host name cho thiết bị thì thực hiện lại câu lệnh trên
```
Tai(config)# hostname R1
R1(config)#
```
* Kiểm tra cấu hình của thiết bị đầu tiên quay lại chế độ Priviledged EXEC Mode sau đó thực hiện câu lệnh show running-config
```cisco
R1(config)# exit
R1# show running-config
```
![](https://user-images.githubusercontent.com/52046920/180779788-2f78f670-f7f9-4181-b645-924f62be578c.png)
* Sau đó tiến hành lưu cấu hình dữ liệu đề phòng trường hợp router bị tắt thì sẽ phải cấu hình lại từ đầu
```
R1# write memmory
```

![](https://user-images.githubusercontent.com/52046920/180779793-8e318ddf-10f2-405a-a53b-f51355c8aaf8.png)
* Tắt router đi bật lại để kiểm tra cấu hình
## ***2. Thiết lập mật khẩu Console và mật khẩu Enable***
* Mật khẩu console dùng để kiểm soát cấu hình quả cổng console. Mật khẩu enable để kiểm soát cho phép những người có quyền hạn mới được phép cấu hình router
* Thiết lập mật khẩu console, Đầu tiên truy cập chế độ Global Configuration Mode
```cisco
R1> enable
R1# config terminal
R1(config)#
```
* Sau đó truy cập chế độ line bằng câu lệnh
![](https://user-images.githubusercontent.com/52046920/180779810-416964b2-7dc1-4b0f-afb3-c2bca188e11f.png)
```cisco
R1(config)# line console 0              ///console 0 do các cisco router thường chỉ có 1 cổng console và mặc định là 0
R1(config-line)#
```

* Sau đó cấu hình mật khẩu cho console như sau

```cisco
R1(config-line)# password viettelcoTai              ///Đây là mật khẩu console
R1(config-line)# login          ///Áp dụng mật khẩu
```
* Trong tình huông muốn gỡ mật khẩu thì vẫn truy cập vào truy cập chế độ line  sau đó thực hiện như sau
```cisco
R1(config-line)# no password            

```
* Thiết lập mật khẩu enable, Đầu tiên truy cập chế độ Global Configuration Mode
```cisco
R1> enable
R1# config terminal
R1(config)#
```
* Sau đó cấu hình mật khẩu enable như sau
```cisco
R1(config-line)# enable password tai123              
```
* Trong tình huông muốn gỡ mật khẩu thì vẫn truy cập chế độ Global Configuration Mode sau đó thực hiện như sau
```cisco
R1(config-line)# no enable password            

```
