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

# NETWORK BASIC
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [Network Basic]()
## &ensp; [1. Network Basic]()
## &ensp; [2. Ethernet Lan]()
## &ensp; [3. Các loại Cab]()
## &ensp; [4. IPv4]()
## &ensp; [5. IPv6]()

# [1 số các khái niệm]()
***
# ***Network Basic***
## [1. Network Basic](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/f1b99d7ba793756fd1a087cd349e742f5e99bcab/CCNA/1.Network%20Basic/README.md)
## [2. Ethernet Lan](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/f1b99d7ba793756fd1a087cd349e742f5e99bcab/CCNA/2.Ethernet%20LAN/README.md)
## [3. Các loại Cab](https://docs.google.com/document/d/1LxHzzggamS7SjSUEhV133fErVDyIk4EzIHybG4lASbA/edit?usp=sharing)
## [4. IPv4](https://docs.google.com/document/d/1wwpTXPJxST9C_FUU3xdedfAMOkFB7H3G28VXJ_kpMYI/edit)
## [5. IPv6](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/f1b99d7ba793756fd1a087cd349e742f5e99bcab/CCNA/32.IPv6/README.md)
# ***1 số các khái niệm***
* Automatic Private IP Addressing - IP (APIPA):Khi client hoặc máy trạm (workstations) không thể truy cập Máy chủ DHCP và nó sẽ nhận được một Địa chỉ IP tạm thời thay thế được gọi là IP APIPA. Hệ thống tự chọn địa chỉ IP trong dải từ 169.254.1.0 đến 169.254.254.255. Theo mặc định, giao thức APIPA được bật.
* Cách tìm Trạng thái IP APIPA
    * Start > Run > ncpa.cpl

    ![](https://user-images.githubusercontent.com/52046920/196326525-9176ff9e-5a4b-49be-a341-1a473d031f46.png)
    * Chọn 1 card mạng Properties

    ![](https://user-images.githubusercontent.com/52046920/196326530-1aa77101-2a26-4b05-a8a6-13cce2bbc760.png)
    * Chọn TCP/IPv4 > Click vào Properties

    ![](https://user-images.githubusercontent.com/52046920/196326531-909b8e01-24ec-414f-852e-02ab2feb70a7.png)
    * Đi tới Tab > Alternate Configuration > APIPA

    ![](https://user-images.githubusercontent.com/52046920/196326532-94f8e514-515d-41bf-b1a1-958e4369c2ae.png)

    ![](https://user-images.githubusercontent.com/52046920/196326533-e97fd7c4-f53e-4ba9-a745-3b223b5fe618.png)
* Các thiết bị mạng(Network Devices)
    * Switch: Là một thiết bị phần cứng tập trung giao tiếp giữa các thiết bị có dây được kết nối trong một mạng LAN.
    * Wireless Access Point(WAP): Là một thiết bị phần cứng tập trung giao tiếp giữa các thiết bị Không dây và có dây trong một mạng LAN.
    * Router: Là một thiết bị cho phép giao tiếp giữa hai hoặc nhiều mạng logic khác nhau
    * Firewall: Là một thiết bị bảo vệ mạng khỏi bị truy cập trái phép. Nó cho phép và từ chối lưu lượng mạng dựa trên chính sách được cấu hình.
* Các câu lệnh Network cơ bản
    * Ping: Sử dụng để kiểm tra xem 2 máy tính đã có thể kết nối với nhau chưa

    ![]()
    * Ipconfig: Hiện thị các thông tin về mạng

    ![]()
    * Traceroute(Tracert trên window): sử dụng để kiểm tra đường đi đến 1 đích nào đó và để chuẩn đoán mạng

    ![]()
    * Netstat: Hiển thị số liệu thống kê giao thức số cổng đã sử dụng, địa chỉ local và địa chỉ foreign và các kết nối mạng TCP/IP hiện tại. Ta có các tham số
        * Proto: TCP hoặc UDP
        * Local Address: địa chỉ IP của local và số cổng được sử dụng
        * Foreign Address: Địa chỉ IP và số cổng của máy tính kết nối từ xa
        * State: trạng thái cổng

    ![]()
    * Nslookup: Sử dụng để lấy thông tin từ máy chủ DNS.

    ![]()
    * Telnet: được sử dụng để truy cập đến và điều khiển máy tính khác từ xa. Tuy nhiên nên sử dụng SSH để bảo mật hơn 
