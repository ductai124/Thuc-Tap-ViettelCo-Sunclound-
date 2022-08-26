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

# TÌM HIỂU VỀ SYSLOG VÀ NTP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Syslog là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#isyslog-l%C3%A0-g%C3%AC)
# [II. Định dạng tin nhắn Syslog](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#ii%C4%91%E1%BB%8Bnh-d%E1%BA%A1ng-tin-nh%E1%BA%AFn-syslog)
# [III. Syslog gửi tin nhắn hoạt động như thê nào](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#iiisyslog-g%E1%BB%ADi-tin-nh%E1%BA%AFn-ho%E1%BA%A1t-%C4%91%E1%BB%99ng-nh%C6%B0-th%C3%AA-n%C3%A0o)
# [IV. Ưu nhược điểm](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#iv-%C6%B0u-nh%C6%B0%E1%BB%A3c-%C4%91i%E1%BB%83m)
# [V. Cấu hình Router và Switch gửi thông báo lỗi về cho Syslog Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#vc%E1%BA%A5u-h%C3%ACnh-router-v%C3%A0-switch-g%E1%BB%ADi-th%C3%B4ng-b%C3%A1o-l%E1%BB%97i-v%E1%BB%81-cho-syslog-server)
# [VI. Giao thức NTPlà gì? Cấu hình giao thức NTP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/17.Syslog/README.md#vigiao-th%E1%BB%A9c-ntpl%C3%A0-g%C3%AC-c%E1%BA%A5u-h%C3%ACnh-giao-th%E1%BB%A9c-ntp)

***
# ***I.	Syslog là gì***
* Syslog hay System Logging Protocol(giao thức ghi Log hệ thống) là một giao thức tiêu chuẩn  được sử dụng để gửi nhật ký hệ thống hoặc thông báo 1 sự kiện phát sinh lỗi đến Syslog Server
* Được kích hoạt trên hầu hết các Router, Firewall, Switch, hệ thống dựa trên Unix và Linux
* Syslog được sử dụng như 1 tiếu chuẩn chuyển tiếp và thu thấp log. Syslog có thể xác định mức độ nghiêm trọng (Severity levels) giúp quản trị viên dễ dàng trong việc kiểm soát các thiết bị.
* Syslog có những yếu tố sau:
    * ***Defining an architecture***(Xác định kiến trúc): Là 1 giao thức và là 1 phần của kiến trúc mạng hoàn chỉnh, với nhiều server và client
    * ***Message format***(Định dạng tin nhắn): Syslog xác định cách định dạng tin nhắn. Xác định, chuẩn hóa những bản ghi gì máy client có thể tạo ra và những bản ghi gì server có thể nhận được.
    * ***Specifying reliability***(chỉ định độ tin cậy): Syslog cần xác định cách xử lý các tin nhắn không thể gửi được (tùy theo sử dụng UDP hay TCP).
    * ***Dealing with authentication or message authenticity***(Xử lý xác thực và xác thực thư): syslog cần một cách đáng tin cậy để đảm bảo rằng máy khách và máy chủ đang nói chuyện một cách an toàn và tin nhắn nhận được không bị thay đổi.
* Kiến trúc Syslog

![](https://user-images.githubusercontent.com/52046920/186904913-74b5cb62-d65c-4c27-a0b8-fbebcff60523.png)
* Gồm: 
    * Syslog Client: Tạo ra các tin nhắn thông báo và gửi về cho Syslog server
    * Relay device: Thiết bị chuyển tiếp các tin nhăn từ Syslog Client đến Syslog Server.
    * Syslog Server: Thu thập, nhận các tin nhắn được gửi về và lưu trữ Log đó lại

# ***II.	Định dạng tin nhắn Syslog***

![](https://user-images.githubusercontent.com/52046920/186904879-7d587656-cf13-407c-8c49-137607cbef01.png)
* Được chia là 3 phần, có tổng độ dài không được vượt quá 1024 bytes:
    * PRI: chi tiết các mức độ ưu tiên của tin nhắn cũng như các mức độ cơ sở(mail, auth,....). một số gồm 8 bit:
        * 3 bit đầu tiên thể hiện cho tính nghiêm trọng của thông báo.
        * 5 bit còn lại đại diện cho sơ sở sinh ra thông báo.
        * PRI=Facility number X 8 + Severity number.
        * ví dụ: 165=20 X 8 +5 nên ta có Facility = 20(local0-local7) và Severity = 5(Notice)
    * Header: Bao gồm 2 trường là TIMESTAMP(Giờ:Phút:Giây) và HOSTNAME(IP hoặc tên máy)
    * MSG: phần này chưa thông tin thực tế về sự kiện đã xảy ra. Nó cũng được chỉa thành trường TAG và CONTENT.
* Cấp độ cơ sở Syslog:
    * Được sử dụng để xác định chương trình hoặc 1 phần của hệ thống tạo ra các bản ghi
    * Một số phần trong hệ thống được cung các các mức facility như kernel sử dụng kern facility, mail sử dụng mail facility.
    * Các cấp độ facility Syslog:

    |Numerical code|Keyword|Facility name|
    |-|-|-|
    |0|kern|Những log do kernel sinh ra|
    |1|user|Log ghi lại cấp độ người dùng|
    |2|mail|Log của hệ thống mail|
    |3|daemon|Log của tiến trình nền trên hệ thống|
    |4|auth|Log quá trình đăng nhập hệ thống hoặc xác thực hệ thống|
    |5|syslog|Log từ syslogd|
    |6|lpr|Log từ quá trình in ấn|
    |7|news|Thông tin tin tức từ hệ thống liên quan đến giao thức nntp(Network News Protocol)|
    |8|uucp|Tập hợp các chương trình cấp thấp cho phép kết nối các máy Unix với nhau|
    |9|cron|Tiện ích cho phép thực hiện các tác vụ theo định kì|
    |10|authpriv|Các thông báo liên quan đến truy cập và bảo mật|
    |11|ftp|Log của FTP|
    |12|ntp|Log của NTP|
    |13|security|Kiểm tra đăng nhập|
    |14|console||
    |15|solaris-cron||
    |16-23|local0-local7|| 
* Mức độ cảnh báo của Syslog gồm 8 cấp độ từ 0-7:

    ||||
    |-|-|-|
    |0|Emergency|emerg-Thông báo tình trạng khẩn cấp|
    |1|Alert|alert-Hệ thống cần can thiệp ngay|
    |2|Critical|crit-Tình trạng nguy kịch|
    |3|Error|err-Thông báo lỗi đối với hệ thống|
    |4|Warning|warning-Mức cảnh báo đối với hệ thống|
    |5|Notice|notice-Chú ý đối với hệ thống|
    |6|Informational|infor-Thông tin của hệ thống|
    |7|Debug|debug-Quá trình kiểm tra hệ thống|

# ***III.	Syslog gửi tin nhắn hoạt động như thê nào***
* Chuyển tiếp nhật ký hệ thống (syslog forwarding) gửi log máy khách đến một máy chủ từ xa để chúng được tập trung hóa, giúp phân tích log dễ dàng hơn.
* Quản trị sẽ chỉ cần giám sát thông qua log được ghi tập trung tại máy chủ Syslog
* Syslog có thể sử dụng cả UDP lần TCP
# ***IV. Ưu nhược điểm***
* Ưu điểm:
    * Giúp quản trị viên có cái nhìn chi tiết về hệ thống -> có định hướng tốt hơn về hướng giải quyết
    * Mọi hoạt động của hệ thống được ghi lại và lưu trữ ở một nơi an toàn (log server) -> đảm bảo tính toàn vẹn phục vụ cho quá trình phân tích điều tra các cuộc tấn công vào hệ thống
    * Log tập trung kết hợp với các ứng dụng thu thập và phân tích log khác nữa giúp cho việc phân tích log trở nên thuận lợi hơn -> giảm thiểu nguồn nhân lực.
* Nhược điểm:
    * Có nhiều nguồn sinh ra log, log nằm trên nhiều máy chủ khác nhau nên khó quản lý.
    * Do tính tập trung Syslog nên có nguy cơ quá tải máy chủ syslog của mình có thể là do bị tấn công hoặc do phần cứng không đáp ứng đủ
    * Syslog Server bị hỏng dẫn đến việc mất hết toàn bộ log do lưu tập trung. 
    * Nếu máy chủ ngừng hoạt động, máy khách sẽ bắt đầu lưu trữ thư cục bộ cho đến khi máy chủ khả dụng trở lại, do đó không gian đĩa ở phía máy khách sẽ dần bị đầy.
# ***V.	Cấu hình Router và Switch gửi thông báo lỗi về cho Syslog Server***

![](https://user-images.githubusercontent.com/52046920/186904888-9883ad29-b635-4e48-85e0-34e190e0133c.png)
* Trên router và switch chỉ cần thực hiện duy nhất 1 câu lệnh sau
```Cisco
R1(config)#logging 192.168.1.1
\\\IP trên là ip của Syslog Server

\\\Tương tự với Switch
SW(config)#logging 192.168.1.1
```
* Kiểm tra ta sẽ tắt 1 cổng trên Router1 ở đấy tắt cổng nối với Switch là gig0/1

![](https://user-images.githubusercontent.com/52046920/186904890-423c22eb-d96f-4bb0-8039-11e1d23ee821.png)

* Khi cổng được bật lại

![](https://user-images.githubusercontent.com/52046920/186904892-a81eab1e-e8ea-4b07-bf7d-45a6f5bd974e.png)
* Khi có config được thực hiện qua console

![](https://user-images.githubusercontent.com/52046920/186904893-27e832c7-84c7-4a0b-a2bb-495452180d90.png)

# ***VI.	Giao thức NTPlà gì? Cấu hình giao thức NTP***
* Giao thức NTP (Network Time Protocol) là một giao thức để đồng bộ đồng hồ của các hệ thống máy tính thông qua mạng dữ liệu chuyển mạch gói với độ trễ biến đổi. Do trong hệ thống để việc đồng bộ thời gian thực sự rất quan trọng, nếu thời gian ko được đồng bộ sự cố sẽ rất khó được khắc phục

* Phương thức hoạt động
    * NTP Client gửi 1 gói tin, trong đó chứa thẻ thời ian tới cho NTP Server.
    * NTP Server nhận được gói tin, gửi trả lại NTP client 1 gói tin khác có thẻ thời gian là thời điểm nó gửi gói tin đó đi.
    * NTP Client nhận được gói tin đó, tính toán độ trể dựa vào thẻ thowfig ian mà nó nhận được cùng với độ trẻ đường truyền, NTP CLient sẽ set lại thời gian của nó.
* Cấu hình thời gian trên Router và Switch của cisco
```cisco
R1#clock set 13:12:00 26 Aug 2022
R1#show clock
```
![](https://user-images.githubusercontent.com/52046920/186905646-6393f536-086c-4960-886c-cd784134f31b.png)

* Khi sử dụng câu lệnh trên thì thiết bị bị khởi động lại thông tin thời gian có thể không được chính xác nữa vậy ta có 2 cách để giải quyết vấn đề này
```cisco
R1#calendar set 13:12:00 26 Aug 2022
R1#show calendar


\\\khi đã thiết lập bằng câu lệnh Clock thì ta chỉ cần thực hiện câu lệnh sau
R1#clock update-calendar

```
* khi set calendar thì clock không được set theo hay có câu lệnh nào như clock thiết lập qua calendar cả

* Để thiết lập NTP ta chọn Router R1 làm NTP Server và SW1 và SW2 là client. Ta cấu hình như sau

```cisco
\\\Tại R1
R1(conffig)#ntp master

\\\Nhớ phải thực hiện Set Clock


\\\Tại các switch
SW1(config)#ntp server 192.168.1.1
SW1(config)#do sh clock

SW2(config)#ntp server 192.168.2.1
SW2(config)#do sh clock

SW3(config)#ntp server 192.168.1.1
SW3(config)#do sh clock
```
