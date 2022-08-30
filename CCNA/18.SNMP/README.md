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

# TÌM HIỂU VỀ SNMP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. SNMP là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/18.SNMP/README.md#isnmp-l%C3%A0-g%C3%AC)
# [II. Thành phần của SNMP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/18.SNMP/README.md#iith%C3%A0nh-ph%E1%BA%A7n-c%E1%BB%A7a-snmp)
## &ensp; [1. SNMP Manager](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/18.SNMP/README.md#1snmp-manager)

## &ensp; [2. SNMP Agent](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/18.SNMP/README.md#2snmp-agent)

# [III. Cách thức hoạt động của SNMP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/18.SNMP/README.md#iiic%C3%A1ch-th%E1%BB%A9c-ho%E1%BA%A1t-%C4%91%E1%BB%99ng-c%E1%BB%A7a-snmp)

***
# ***I.	SNMP là gì***
* SNMP hay Simple Network Monitoring Protocol(Giao thức giám sát mạng đơn giản). Là 1 giao thức truyền thông để quản lý trong mạng, đặc biết là sử dụng trong mạng LAN, tùy thuộc vào phiên bản đã chọn.
* Là một giao thức mạng để quản lý, giám sát các phần tử mạng. Hầu hết các thiết bị mạng hiện nay đều đi kèm với SNMP Agent để thu thập và gửi các thông tin cần thiết từ các thiết bị về cho máy chủ SNMP để giám sát các thiết bị
# ***II.	Thành phần của SNMP***
* SNMP gồm 2 thành phần chính như sau:
## ***1.	SNMP Manager***
* Là một máy tính sử dụng các phần mềm để giao tiếp với các SNMP Agent để quản lý các thiết bị mạng trong hệ thống.
* Các chức năng chính:  
    * Agent truy vấn
    * Nhận Reponse từ các Agent
    * Đặt các biến trong Agent
    * Xác nhận các sự kiện không đồng bộ từ các Agent
## ***2.	SNMP Agent***
* Các thiết bị được quản lý là: các Router, Switch, Server, máy trạm, máy in, UPS, .....
* Các thiết bị trên sẽ được cài đặt 1 phần mềm gọi là SNMP Agent. Đây là một phần mềm thu thập cơ sở dữ liệu, thông tin cần quản lý từ các thiết bị cần giám sát và gửi nó lại cho SNMP Manager
* Các chức năng chính:
    * Thu thập thông tin các chỉ số cần quản lý của thiết bị
    * Lưu trữ và tuy xuất các thông tin quản lý
    * Báo hiệu sử kiện cho SNMP Manager
    * Hoạt động như 1 proxy cho 1 số nút mạng không thể quản lý.
# ***III.	Cách thức hoạt động của SNMP***
* SNMP sử dụng các phương thức cơ bản để giao tiếp giữa SNMP Manager và SNMP Agent

![](https://user-images.githubusercontent.com/52046920/187388355-7741b39f-2bc4-4b5b-8a0c-b36de3712e69.png)
* GET: Để nhận trạng thái từ SNMP Agent SNMP Manager đưa ra tin nhắn GET và GETNEXT để yêu cầu thông tin cụ thể.
    * GetResponge: Khi nhận được GET hoặc GETNEXT, SNMP Agent gửi về tin nhắn GetRespone cho SNMP Manager chứa thông tin được yêu cầu hoặc lỗi giải thích không lấy được thông tin
* SET: Cho phép SNMP Manager thay đổi các điều khiển trên thiết bị quản lý.
    * Set-respone: SNMP Agent trả lời bằng tin nhắn Set-respone nếu thay đổi được thực hiện, còn nếu không thì gửi về lỗi giải thích không thực hiện được
* TRAP: Dùng để cảnh báo cho manager khi có sự kiện quản trọng ví dụ như sự kiện gây ra lỗi nghiêm trọng xảy ra
* INFORM: Giống TRAP nhưng tốt hơn. Các SNMP Agent gửi cho SNMP Manager và nếu Manager nhận được nó thì Manager gửi respone đến các Agent nhằm báo hiệu là đã nhận được tin nhắn. Agent không nhận được hồi đáp thì nó sẽ gửi lại tin nhắn INFORM.
