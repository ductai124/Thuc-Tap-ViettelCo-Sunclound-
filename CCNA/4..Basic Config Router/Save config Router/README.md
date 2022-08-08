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

# TÌM HIỂU CẤU HÌNH ROUTER LƯU CẤU HÌNH LÊN FTP SERVER VÀ TFTP SERVER
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. FTP SERVER](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#iftp-server)

## &ensp; [1. FTP SERVER là gì?](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#1ftp-server-l%C3%A0-g%C3%AC)

## &ensp; [2. Chức năng](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#2ch%E1%BB%A9c-n%C4%83ng)


# [II. TFTP SERVER](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#iitftp-server)

## &ensp; [1. TFTP SERVER là gì?](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#1tftp-server-l%C3%A0-g%C3%AC)

## &ensp; [2. Chức năng](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#2ch%E1%BB%A9c-n%C4%83ng-1)

# [III. Lưu cấu hình của thiết bị lên TFTP Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#iiil%C6%B0u-c%E1%BA%A5u-h%C3%ACnh-c%E1%BB%A7a-thi%E1%BA%BFt-b%E1%BB%8B-l%C3%AAn-tftp-server)

# [IV. Lưu cấu hình của thiết bị lên FTP Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#ivl%C6%B0u-c%E1%BA%A5u-h%C3%ACnh-c%E1%BB%A7a-thi%E1%BA%BFt-b%E1%BB%8B-l%C3%AAn-ftp-server)

# [V. Cisco IOS](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#vcisco-ios)

# [VI. Lưu hệ điều hành IOS của router lên tftp server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#vil%C6%B0u-h%E1%BB%87-%C4%91i%E1%BB%81u-h%C3%A0nh-ios-c%E1%BB%A7a-router-l%C3%AAn-tftp-server)
# [V. Lưu hệ điều hành IOS của router lên ftp server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/CCNA/Save%20config%20Router#vl%C6%B0u-h%E1%BB%87-%C4%91i%E1%BB%81u-h%C3%A0nh-ios-c%E1%BB%A7a-router-l%C3%AAn-ftp-server)
## &ensp; []()
***
# ***I.	FTP SERVER***
## ***1.	FTP SERVER là gì?***
* FTP là viết tắt của File Transfer Protocol, là một loại giao thức truyền tải tập tin từ máy tính này sang máy tính khác thông qua 1 mạng TCP hoặc mạng Internet
* Thông qua giao thức này, người dùng có thể truyền dữ liệu từ máy tính đến server hoặc tải 1 tập tin trên server về máy cá nhân
* FTP server là máy tính cung cấp không gian lưu trữ, chia sẻ dữ liệu trong môi trường internet. Bạn có quyền quản lý toàn bộ các dữ liệu dạng tập tin và thư mục có trên host ngoại trừ database
* Mục đích sử dụng:
    * Khuyển khích việc dùng chung tập tin (chương trình ứng dụng, dữ liệu)
    * Khuyến khích sử dụng máy tính từ xa
    * Che đậy sử khác biệt về hệ thống lưu trữ tập tin giữa các server
    * Truyền tải dữ liệu đáng tin cậy, hiệu quả cao
    * Trong trường hợp này thì cũng có thể sử dụng để lưu cấu hình router.
## ***2.	Chức năng***
* Truyền tải dữ liệu website lên máy chủ
* Truyền tải dữ liệu giữa các máy tính
# ***II.	TFTP SERVER***
## ***1.	TFTP SERVER là gì?***
* TFTP là viết tắt của Trivial File Transfer Protocol là công nghệ truyền file giữa các thiết bị mạng và là phiên bản đơn giản hóa của FTP. TFTP sử dụng UDP để giao tiếp tệp
* TFTP server cũng là là máy tính cung cấp không gian lưu trữ, chia sẻ dữ liệu trong môi trường internet. Bạn có quyền quản lý toàn bộ các dữ liệu dạng tập tin và thư mục có trên host ngoại trừ database.
## ***2.	Chức năng***
* Truyền tệp.
* Upgrade code.
* Sao lưu cấu hình mạng.
* Sao lưu các tệp cấu hình bộ định tuyến.
* Lưu hình ảnh IOS.
* Ngày nay, TFTP hầu như không được sử dụng để chuyển file qua Internet. Do sử dụng giao thức UDP nên có khả năng bị mất dữ liệu


## ***Bình thường ta có thể backup dữ liệu từ Ram qua NVram (copy từ running config quá startup config) tuy nhiên trong trường hợp cần nâng cấp, thay thế router mới do router cũ có vấn đề. Để thuận tiện cho việc cấu hình router mà không phải cấu hình lại từ đầu các bước ta sẽ thực hiện Backup cấu hình của router lên FTP server hoặc TFTP server. Khi thay thế router thành công ta có thẻ restore lại cấu hình router***
# ***III.	Lưu cấu hình của thiết bị lên TFTP Server***

![](https://user-images.githubusercontent.com/52046920/181462674-7b0ea3e4-fb33-45ab-bd47-cd70f3635110.png)
* Kết nối tftp server với switch trong mô hình
* Thiết lập IP cho tftp server

![](https://user-images.githubusercontent.com/52046920/181462673-7b09cccc-a940-4639-807f-c1eca54484ab.png)
* Sau đó kiểm tra server và router đã thông nhau chưa bằng ping
* Khi router và server đã thông nhau rồi thì đứng tại router tiến hành backup dữ liệu bằng câu lệnh sau
```cisco
R1# copy running-config tftp:           ///Backup file running-config
R1# copy startup-config tftp:           ///Backup file startup-config
```
* Giả sử ta mua một router mới và thay thế con router cũ, ta cấu hình ip cho cổng kết nối với switch như router cũ là 192.168.1.1 với cổng gigabitEthernet 0/0/0
* Kiểm tra router mới và tftp đã thông nhau chưa bằng ping
* Nếu router và tftp server đã thông nhau thì tiến hành restore lại các cấu hình còn lại của router cũ bằng câu lệnh
```cisco
Router# copy tftp: running-config           ///Restore lại vào file running-config
Router# copy tftp: startup-config           ///Restore lại vào file startup-config
```

![](https://user-images.githubusercontent.com/52046920/181462667-d1214cf8-3916-46bd-a1d6-851fb88f19b2.png)
* Nếu restore vào startup-config thì ta thấy router chưa được thiết lập cấu hình ngay và luôn mà phải reload lại router cấu hình mới được thiết lập.
* Nếu restore lại running-config cấu hình sẽ được thiết lập luôn. Nhớ phải lưu ngay vào startup-config sau khi restore running config.
* File backup của running-config và startup-config có thể restore chéo cho nhau ví dụ: backup startup-config có thể restore vào running-config và ngược lại

# ***IV.	Lưu cấu hình của thiết bị lên FTP Server***

![](https://user-images.githubusercontent.com/52046920/181462644-afd87754-0cb5-4085-b52b-ddc01c2a6d81.png)
* Do TFTP sử dụng UDP làm giao thức truyền file vậy nên trong lúc backup và restore có thể dẫn đến mất file hỏng cấu hình được backup, khiên file đó không còn giá trị sử dụng vậy nên FTP là giải pháp backup tốt hơn do sử dụng giao thức TCP.
* Kêt nối FTP server đến switch trong mô hình
* Thiết lập IP cho tftp server

![](https://user-images.githubusercontent.com/52046920/181462654-939f7f06-88a8-42d9-aa87-2499ca4126f7.png)
* Các thông số tftp server
* username và passwork của ftp server mặc định là 
    * Username: cisco
    * Password: cisco
    * Tất cả các quyền truy cập(đọc, ghi xóa, đổi tên, danh sách)
* Ta có thể thêm các user với các quyền khác nhau trên ftp server
* Sau đó kiểm tra server và router đã thông nhau chưa bằng ping
* Khi router và server đã thông nhau rồi thì đứng tại router tiến hành các bước sau
* Truy cập vào chế độ global config
* khai báo username password của người dùng trên ftp server

```cisco
Router(config)#ip ftp username cisco         ///username mặc định của server cisco
Router(config)#ip ftp password cisco        ///Mật khẩu mặc định server cisco
```
* Username và password ftp server có thể được lưu vào cấu hình
* Sau đó quay lại chế độ Priviledged và tiến hành backup dữ liệu bằng câu lệnh
```cisco
R1# copy running-config ftp:           ///Backup file running-config
R1# copy startup-config ftp:           ///Backup file startup-config
```

* Ở bước này nếu chưa khai báo username và password fpt server thì sẽ hiện thông báo lỗi như sau và phải tiến hành khai báo 2 thông số trên nếu muốn tiến hành backup.

![](https://user-images.githubusercontent.com/52046920/181462642-6bb653de-3f9c-4d5c-bbf6-af3a0e421b81.png)
* Backup thành công

![](https://user-images.githubusercontent.com/52046920/181462649-dc806c07-b960-43d9-8ef9-5deb4a2040a7.png)
* Khi sử dụng 1 router mới thay thế ta cấu hình ip cho cổng kết nối với switch như router cũ là 192.168.1.1 với cổng gigabitEthernet 0/0/0.
* Kiểm tra router mới và ftp đã thông nhau chưa bằng ping
* Nếu router và tftp server đã thông nhau thì tiến hành restore lại các cấu hình còn lại của router cũ bằng câu lệnh
```cisco
Router# copy ftp: running-config           ///Restore lại vào file running-config
Router# copy ftp: startup-config           ///Restore lại vào file startup-config
```

![](https://user-images.githubusercontent.com/52046920/181462647-bb2ef1f9-b12b-4cad-8502-bb46a3ebc752.png)


# ***V.	Cisco IOS***
* Cisco IOS (Internetwork Operating System) là hệ điều hành đa nhiệm được sử dụng rộng rãi trên các sản phẩm Router và Switch của hãng Cisco (Switch cũ hơn sử dụng CatOS). IOS hỗ trợ các chức năng định tuyến, chuyển mạch, liên kết mạng và truyền thông.
* Hệ điều hành của Cisco router sẽ được lưu trực tiếp trên bộ nhớ flash của router.


## ***Việc backup hệ điều hành nhằm mục đích***
 * lưu trữ bên ngoài để dự phòng cho trường hợp khi xảy ra lỗi, ta sẽ có sẵn IOS để load lại cho thiết bị. 
 * Trong trường hợp chúng ta có được một IOS tốt hơn IOS đang sử dụng và được phép nâng cấp, thao tác này sẽ giúp chúng ta thay thế IOS cũ trên thiết bị bằng một IOS mới tốt hơn và sử dụng 
 * Trong trường hợp thiết bị bị mất IOS hoặc bị lỗi IOS và cần phải cài lại IOS từ đầu

 # ***VI.	Lưu hệ điều hành IOS của router lên tftp server***
 * Vẫn sử dụng mô hình trước ta kiểm tra flash của thiết bị để lấy tên file hệ điều hành.

 ![](https://user-images.githubusercontent.com/52046920/181462595-533f8e5a-fdbb-4a1a-909a-ae029a487d42.png)
 
 * Thực hiện lưu hệ điều hành lên tftp server bằng câu lệnh
 ```cisco
 R1# copy flash: tftp:
 ```
![](https://user-images.githubusercontent.com/52046920/181462599-e236ceb9-5069-4f85-8025-9e090f8bc3a3.png)

![](https://user-images.githubusercontent.com/52046920/181462605-892dc9f9-ec5b-4b48-84cf-3cbb9a596837.png)
 * Thực hiện copy IOS về Flash bằng câu lệnh
 ```cisco
 R1#copy tftp: flash: 
 ```
 ![](https://user-images.githubusercontent.com/52046920/181462609-ac4f636a-0d98-4a74-bcd5-82fee943ced4.png)






# ***V.	Lưu hệ điều hành IOS của router lên ftp server***
* Vẫn sử dụng mô hình trước ta kiểm tra flash của thiết bị để lấy tên file hệ điều hành.
* Truy cập vào chế độ global config
* khai báo username password của người dùng trên ftp server

```cisco
Router(config)#ip ftp username cisco         ///username mặc định của server cisco
Router(config)#ip ftp password cisco        ///Mật khẩu mặc định server cisco
```

* Thực hiện lưu hệ điều hành lên ftp server bằng câu lệnh
 ```cisco
 R1# copy flash: ftp:
 ```

* Thực hiện copy IOS về Flash bằng câu lệnh
 ```cisco
 R1#copy ftp: flash: 
 ```


 ### ***Lưu ý*** Do tftp sử dụng UDP làm phương thức truyền nên trong quá trình truyền dữ liệu có thể dẫn đến mất dữ liệu vì vậy nên sử dụng ftp server do nó sử dụng giao thức tcp mặc dù quá trình lưu dữ liệu lên server sẽ chậm hơn tuy nhiên dữ liệu sẽ được đảm bảo và không bị mất
