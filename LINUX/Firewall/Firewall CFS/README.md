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

# TÌM HIỂU VỀ FIREWALL CSF
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
# ***Firewall CSF và cách cài đặt, sử dụng***
* CSF (ConfigServer Security & Firewall) là tường lửa Stateful Packet Inspection (SPI) mã nguồn mở phổ biến, giúp bảo vệ hệ thống sử dụng hệ điều hành Linux. Ngoài các tính năng cơ bản của Firewall là filter packet in/out thì CSF còn hỗ trợ ngăn chặn các cuộc tấn công như Brute Force, DDoS Attack.
* Khác với Firewalld thì Firewall CSF thường được sử dụng để ngăn chặn các cuộc tấn công từ bên ngoài vào trong hệ thống. 
* Sử dụng tường lửa CSF
```php
#cài đặt gói sau

dnf -y install @perl

#Cài đặt tường lửa CSF

cd /tmp
wget https://download.configserver.com/csf.tgz
tar -zxvf csf.tgz
cd csf
./install.sh
rm -rf /tmp/csf
rm -f /tmp/csf.tgz

#Tắt tường lửa mặc định và bật tường lửa CSF để sử dụng
systemctl stop firewalld
systemctl disable firewalld

systemctl enable csf
systemctl enable lfd
systemctl start csf

#Kiểm tra CSF đã hoạt động chưa
systemctl status csf

#Test iptable

/etc/csf/csftest.pl

#Kích hoạt
vi /etc/csf/csf.conf

#Tìm đến dòng có TESTING và FASTSTART và sửa giá trị như sau

TESTING = 0
FASTSTART = 1
#Thi thoảng tường lửa vẫn chặn ip trong csf.alow nên chỉnh về 1 để không bị chặn
IGNORE_ALLOW = "1"
#Cho phép user truy cập tới (incoming) các TCP port trên server
TCP_IN = "20,21,22,25,53,80,110,143,443,465,587,993,995"
#Ta mở thêm cổng 3306 để cho phép kết nối với mysql
TCP_IN = "20,21,22,25,53,80,110,143,443,465,587,993,995,3306"
#Server kết nối ra (outgoing) tới các TCP port bên ngoài
TCP_OUT = "20,21,22,25,53,80,110,113,443"
#Ta mở thêm công 3306 để cho phép kết nối với mysql
TCP_OUT = "20,21,22,25,53,80,110,113,443,3306"
#Chặn ping 
#Thay đổi giá trị sau
ICMP_IN = "1"
#Thành
ICMP_IN = "0"
#Truy cập vào cổng 22 5 lần trong 300 giấy sẽ bị chặn 300 giây
PORTFLOOD = “22; tcp; 5; 300

#1 Số lệnh cơ bản trong trong lửa CSF
#Start CSF	
csf -s
#Flush/Stop firewall rules (note: lfd may restart csf)	
csf -f
#Restart CSF	
csf -r
#Kiểm tra các rules
csf -l
#Allow an IP	
csf -a ip-address
#Xóa ip khỏi danh sách cho phép
csf -ar ip-address
#Deny IP	
csf -d ip-address
#Bỏ chặn ip
csf -dr ip-address
#Remove and unblock all entries	
csf -df
#Stop firewall	
csf -x
#Enable firewall	
csf -e


#Cho phép ip truy
vi /etc/csf/csf.allow

#Cho phép tcp kết nối inbound cổng 22 ip 192.168.1.2
tcp|in|d=22|s=192.168.1.2

#Cho phép tcp kết nối outbound cổng 22 ip 192.168.1.2
tcp|out|d=22|s=192.168.1.2

#Chặn ip truy cập
vi /etc/csf/csf.deny
#Chặn tcp kết nối inbound cổng 22 ip 192.168.1.12
tcp|in|d=22|s=192.168.1.12
#Chặn ip trong 1 khoảng thời gian
csf -td 0.0.0.0/0 60 -d inout "block all in/out connections for 60 seconds" 

#các câu lệnh firewall CSF
#Kiểm tra 
csf -t
# Chặn ip
csf -d 1.1.1.1
#Remove ip bị chặn
csf -dr 1.1.1.1
#Restart Firewall
csf -r
#Stop firewall
csf -s
#Disable Firewall
csf -f
# Khởi động lại Firewall
systemctl restart csf.service
```
* Ngoài ra còn nhiều thông số khác có thể điều chỉnh trong Firewall CSF tuy nhiên đây là những cấu hình cơ bản nhất cho tường lửa CSF

