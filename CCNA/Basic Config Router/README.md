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

# [II. Cấu hình Router cơ bản](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Router#iic%E1%BA%A5u-h%C3%ACnh-router-c%C6%A1-b%E1%BA%A3n)

## &ensp; [1. Tiến hành cấu hình hostname cho Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#1-ti%E1%BA%BFn-h%C3%A0nh-c%E1%BA%A5u-h%C3%ACnh-hostname-cho-router)

## &ensp; [2. Thiết lập mật khẩu Console và mật khẩu Enable](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#2-thi%E1%BA%BFt-l%E1%BA%ADp-m%E1%BA%ADt-kh%E1%BA%A9u-console-v%C3%A0-m%E1%BA%ADt-kh%E1%BA%A9u-enable)

## &ensp; [3. Tính năng tự động đăng xuất Exec-Timeout trên kết nối Console](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#3-t%C3%ADnh-n%C4%83ng-t%E1%BB%B1-%C4%91%E1%BB%99ng-%C4%91%C4%83ng-xu%E1%BA%A5t-exec-timeout-tr%C3%AAn-k%E1%BA%BFt-n%E1%BB%91i-console)

## &ensp; [4. Khai báo địa chỉ IP trên các cổng giao tiếp của router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#4-khai-b%C3%A1o-%C4%91%E1%BB%8Ba-ch%E1%BB%89-ip-tr%C3%AAn-c%C3%A1c-c%E1%BB%95ng-giao-ti%E1%BA%BFp-c%E1%BB%A7a-router)

## &ensp; [5. Tính năng chống trôi dòng lệnh Logging Synchronous](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#5-t%C3%ADnh-n%C4%83ng-ch%E1%BB%91ng-tr%C3%B4i-d%C3%B2ng-l%E1%BB%87nh-logging-synchronous)

## &ensp; [6. Tính năng phân giải tên miền ip domain-lookup](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#6-t%C3%ADnh-n%C4%83ng-ph%C3%A2n-gi%E1%BA%A3i-t%C3%AAn-mi%E1%BB%81n-ip-domain-lookup)

## &ensp; [7. Lưu cấu hình và khởi động lại thiết bị](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#7-l%C6%B0u-c%E1%BA%A5u-h%C3%ACnh-v%C3%A0-kh%E1%BB%9Fi-%C4%91%E1%BB%99ng-l%E1%BA%A1i-thi%E1%BA%BFt-b%E1%BB%8B)

## &ensp; [8. Xóa cấu hình và khởi động lại thiết bị](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#8-x%C3%B3a-c%E1%BA%A5u-h%C3%ACnh-v%C3%A0-kh%E1%BB%9Fi-%C4%91%E1%BB%99ng-l%E1%BA%A1i-thi%E1%BA%BFt-b%E1%BB%8B)

## &ensp; [9. Tính năng mã hóa mật khẩu trong file cấu hình](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Basic%20Config%20Router#9-t%C3%ADnh-n%C4%83ng-m%C3%A3-h%C3%B3a-m%E1%BA%ADt-kh%E1%BA%A9u-trong-file-c%E1%BA%A5u-h%C3%ACnh)


## &ensp; [10. Khai báo địa chỉ IP trên Cisco Switch]()
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

![](https://user-images.githubusercontent.com/52046920/180779810-416964b2-7dc1-4b0f-afb3-c2bca188e11f.png)


## ***2. Thiết lập mật khẩu Console và mật khẩu Enable***
* Mật khẩu console dùng để kiểm soát cấu hình quả cổng console. Mật khẩu enable để kiểm soát cho phép những người có quyền hạn mới được phép cấu hình router
* Thiết lập mật khẩu console, Đầu tiên truy cập chế độ Global Configuration Mode
```cisco
R1> enable
R1# config terminal
R1(config)#
```
* Sau đó truy cập chế độ line bằng câu lệnh
```cisco
R1(config)# line console 0              ///console 0 do các cisco router thường chỉ có 1 cổng console và mặc định là 0
R1(config-line)#
```

* Sau đó cấu hình mật khẩu cho console như sau

```cisco
R1(config-line)# password viettelcoTai              ///Đây là mật khẩu console
R1(config-line)# login          ///Áp dụng mật khẩu
```
* Để kiểm tra ta exit 3 lần để thoát ra khỏi truy cập router thì nó đã bắt ta phải đăng nhập mật khẩu console sau đó nhớ lưu lại cấu hình nếu không muốn khi router khởi động lại cấu hình bị mất
 ```
R1# write memmory
```
* Ta cũng có thể kiểm tra mật khẩu bằng câu lệnh show running-config

![](https://user-images.githubusercontent.com/52046920/180914547-7f48c711-f6fe-4782-a638-7306bac3b1a8.png)
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
R1(config)# enable password tai123              
```
* Muốn kiểm tra thì quay lại chế độ đầu tiên sau đó truy cập chế độ đPriviledged EXEC Mode router sẽ bắt ta đăng nhập mật khẩu enable. Nhớ lưu lại cấu hình nếu không muốn khi router khởi động lại cấu hình bị mất
 ```
R1# write memmory
```
* Kiểm tra bằng câu lệnh show running-config

![](https://user-images.githubusercontent.com/52046920/180914545-e27a7c4f-cfcf-4282-b44c-0f6ad20b3994.png)
* Trong tình huông muốn gỡ mật khẩu thì vẫn truy cập chế độ Global Configuration Mode sau đó thực hiện như sau
```cisco
R1(config)# no enable password            

```
## ***3. Tính năng tự động đăng xuất Exec-Timeout trên kết nối Console***
* Được sử dụng khi người quản trị tiến hành cấu hình router thông qua công console mà quên không đăng xuất tránh trường hợp điều đó bị lợi dụng để tấn công router
* Ta truy cập vào chế độ line console 0 và thực hiện câu lệnh thiết lập thời gian tự động đăng xuất
```cisco
R1(config)# line console 0              
R1(config-line)# exec-timeout 1 30          ///Tự động đăng xuất sau 1 phút 30 giây
```
* Sau 1 phút 30 giây sau thì người dùng sẽ tự động đăng xuất
* Nếu muốn gỡ bỏ thời gian tự đăng xuất thì ta thay tham số như sau
```cisco         
R1(config-line)# exec-timeout 0 0          ///gỡ bỏ tự động đăng xuất
```
* Có thể kiểm tra bằng lệnh show running-config
![]()
* Nhớ lưu lại cấu hình 
 ```
R1# write memmory
```
## ***4. Khai báo địa chỉ IP trên các cổng giao tiếp của router***
* Đầu tiên xác định router có bao nhiêu cổng giao tiếp ta đứng tại Priviledged EXEC Mode thực hiện câu lệnh sau
```cisco
R1# show ip interface brief   
```
![](https://user-images.githubusercontent.com/52046920/180914541-fca57f8b-b38c-4220-bec7-9beac58a0324.png)
* Ở con router này thì có 3 cổng và đều chưa được thiết lập ip

* Tiếp đến ta vào Global Configuration Mode thực hiện các câu lệnh sau

```cisco
R1(config)#interface GigabitEthernet 0/0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
no shutdown         ///để bật cổng giao tiếp lên
```

* Các cổng giao tiếp khác

![](https://user-images.githubusercontent.com/52046920/180914539-4426010e-63a3-46f6-aa40-90812c1291bd.png)
* Tiến hành kiểm tra bằng câu lệnh
```cisco
R1# show ip interface brief   
```
![](https://user-images.githubusercontent.com/52046920/180914538-5174bdc7-f215-4317-85b6-0e733cb385e7.png)
* Nhớ lưu lại cấu hình 
 ```
R1# write memmory
```
* Muốn gỡ bỏ ip thì ta thực hiện câu lệnh
```cisco
R1(config)#interface GigabitEthernet 0/0/0
R1(config-if)#no ip address
no shutdown
```
* Protocol muốn ở trạng thái up thì phải được cắm cap và kết nối với thiết bị khác
* Kiểm tra nối router với 2 switch 1 switch nối với cổng giao tiếp đã thiết lập ip và 1 switch kết nối với cổng giao tiếp chưa thiếp lập ip. Ta thấy được Switch kết nối với cổng giao tiếp đã thiết lập ip có thể kết nối và truyền dữ liệu với router còn switch còn lại thì không.

![](https://user-images.githubusercontent.com/52046920/180914535-3ee115e8-79cb-4fec-9536-794869dabfbe.png)
* Nối thêm máy tính và kiểm tra kết nối đến với router
* Kết nối 2 máy tính đến switch và đặt ip cho nó là 192.168.1.3

![](https://user-images.githubusercontent.com/52046920/180914531-5a36269e-6995-4deb-8b7a-827eade85418.png)
* Kiểm tra ping từ router đến máy tính và từ máy tính đến router
* Ping từ router đến máy tính

![](https://user-images.githubusercontent.com/52046920/180914548-eba68250-ebd8-4079-80c4-406928b1353a.png)
    
* ping từ máy tính đến router

![](https://user-images.githubusercontent.com/52046920/180914548-eba68250-ebd8-4079-80c4-406928b1353a.png)
* Đây là ping thành công

## ***5. Tính năng chống trôi dòng lệnh Logging Synchronous***
* Khi cấu hình thiết bị, các log ghi ra màn hình terminal từ các sự kiện sẽ bị dính vào các câu lệnh đang. Điều này sinh ra sự khó chịu và khó quan sát các thao tác dòng lệnh đang sử dụng, chính vì vậy câu lệnh logging synchronous sẽ hỗ trợ chúng ta nhảy dòng giữ nguyên dòng config đang gõ nếu có sự kiện log nào bắn ra màn hình terminal. Khảo sát 2 tình huống.    
* Tắt chống trôi dòng lệnh thực hiện tắt bằng câu lệnh

```cisco
Router(config)# line console 0              
Router(config-line)#no logging synchronous
```
* Giả sử ta thực hiện no shutdown với interface gigabitEthernet 0/0/0 để xuất hiện log. Sau khi xuất hiện log ta phải bấm thêm enter hoặc thực hiện lệnh tiếp theo ngay sau đoạn log. Điều này tốn thêm 1 bước và nếu như thực hiện luông thao tác dòng lệnh mà không enter xuống dòng thì ta có thể sẽ nhầm chế độ truy cập dẫn đến các bước cấu hình sai và mất thời gian 
![]()
* Bật chống trôi dòng lệnh
```cisco
Router(config)# line console 0              
Router(config-line)#logging synchronous
```
* Thực hiện như trên nhưng đối với interface gigabitEthernet 0/0/1. Sau khi chạy lệnh no shutdown ta thấy dòng lệnh tự nhảy xuống dòng và hiện thị được chế độ cấu hình đang được sử dụng. nó giúp giảm thao tác, tránh nhầm lẫn, tránh gây khó chịu và đỡ mất thời gian khi cấu hình. 

## ***6. Tính năng phân giải tên miền ip domain-lookup***
* Tính năng này tự động phân dải một câu lệnh nhập vào không đúng sang một host name.
* Trong quá trình cấu hình cisco router khi ta chạy dòng lệnh sai thì router sẽ cố gắng phân giải tên câu lệnh đó ra địa chỉ ip và việc này xáy ra rất lâu ta có thể dừng quá trình đó lại bằng cách bấm tổ hợp phím Ctrel + Shift + 6.
vậy để thuận tiện trong việc cấu hình ta nên tắt chế độ này đi
```cisco
R1(config)#no ip domain-lookup
```


![](https://user-images.githubusercontent.com/52046920/181007953-59e01374-1193-431c-b501-89c8efd6afb9.png)
* Khi đó router sẽ không cố phân giải những câu lệnh sai thành tên miên nữa. Trong quá trình cấu hình nên tắt đi để tăng tốc độ cấu hình

* Bật tính năng này bằng câu lệnh
```cisco
R1(config)#ip domain-lookup
```
## ***7. Lưu cấu hình và khởi động lại thiết bị***
* Như đã nói ở các phần cấu hình trên. Mục đích lưu cấu hình để khi router khơi động lại nếu như không lưu cấu hình trước đó toàn bộ cấu hình sẽ bị mất hết và câu lệnh lưu cấu hình là
```
R1# write memmory
```
* Ngoài ra còn có câu lệnh 
```
R1# copy running-config startup-config          /// lưu cấu hình từ ram(running config) vào nvram (Startup-config)
```
* Đồng ý lưu thì bấm enter
* Sử dụng câu lệnh reload để khởi động lại router và kiểm tra kết quả.


## ***8. Xóa cấu hình và khởi động lại thiết bị***
* Mục đích: để cấu hình lại từ đầu router xóa sạch cấu hình đã được thiết lập.
* Ví dụ: khi ta mua 1 con router cũ về và muốn cấu hình cho hệ thống của mình nhưng con router đã được thiết lập trước các cấu hình như hostname là R3 và ip là 192.168.10.1 khi đó ta thực hiện như sau

* Thực hiện câu lệnh xóa toàn bộ cấu hình router như sau

```cisco
R3# erase startup-config
```
![](https://user-images.githubusercontent.com/52046920/181007949-4f0cab03-7810-4c2d-8fbe-930223c145df.png)

* Kiểm tra bằng câu lệnh
```cisco  
R3# show startup-config
```
* Vậy cấu hình đã được xóa ta khởi động lại bằng lệnh reload và cấu hình router từ còn số 0 theo ý của mình

## ***9. Tính năng mã hóa mật khẩu trong file cấu hình***
* Mục đích: giảm nguy cơ rò rỉ thông tin về bảo mật
* Mã hóa bằng thuật toán md7
* khi thực hiện câu lệnh mã hóa thì mật khẩu mã hóa chỉ lưu vào running-config và startup-config chưa được mã hóa nên ngay sau khi ma hóa ta thực hiện lưu cấu hình thì mật khẩu tren startup-config cũng được mã hóa theo.
* Do md7 là thuật toán mã hóa 1 chiều nên dù cho có huy dịch vụ mã hóa thì mật khẩu vẫn không được khổi phục ở trên running-config và startup-config. Ta chỉ có thể đặt lại mật khẩu để mật khẩu mới hiển thị được dưới dạng không mã hóa
* Thực hiện mã hóa một router có mật khẩu console là 0837686717 và mật khẩu enable là tai123 như sau
```cisco
Router(config)# service password-encryption.
Router(config)#exit
Router# write memmory           ///Lưu để mật khẩu mã hóa được ghi vào startup-config
```

* Kiểm tra bằng lệnh

```cisco
Router# show running-config

Router# show startup-config
```

![](https://user-images.githubusercontent.com/52046920/181007923-9742c95e-60b2-4523-a1a3-d90155d807d4.png)

![](https://user-images.githubusercontent.com/52046920/181007915-c90a5b9d-d2a9-4250-890c-e98a42afa7cf.png)

## ***9. Khai báo địa chỉ IP trên Cisco Switch***
* Mục đích: trong tình huống muốn sử dụng telnet đến switch để cấu hình từ xa hoặc muốn lưu cấu hình dự phòng của switch trên server thì phải đặt ip cho switch
* Switch không thể tự đặt ip trên các cổng giao tiếp của mình nên muốn đặt được ip cho switch thì phải sử dụng 1 interface đặc biệt đó là interface vlan 1
* Cách cấu hình tương tự với router
```cisco
Switch>enable
Switch#config terminal
Switch(config)#interface vlan 1
Switch(config-if)#ip address 192.168.1.10 255.255.255.0
Switch(config-if)#no shutdown
```
