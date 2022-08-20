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

# TÌM HIỂU VỀ FIREWALL CMD
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
***
# ***FIRE WAL CMD và thiết lập firewall cho centos7 ***
* Tường lửa (Firewall) là một bức rào chắn giữa mạng nội bộ (local network) với một mạng khác (chẳng hạn như Internet), điều khiển lưu lượng ra vào giữa hai mạng này. Nếu như không có tường lửa thì lưu lượng ra vào mạng nội bộ sẽ không chịu bất kỳ sự điều tiết nào, còn một khi tường lửa được xây dựng thì lưu lượng ra vào sẽ do các thiết lập trên tường lửa quy định.
* Firewall cmd hay FirewallD là tường lửa mặc định của hàu hết sẽ được cài đặt sẵn trên centos sau khi cài xong OS thì có thể sử dụng được luôn. Thường được sử dụng để thiết lập bảo mật bên trong nội bộ
* Cách sử dụng FirewallD
```php
# Nếu FirewallD chưa được cài đặt thì cài đặt bằng câu lệnh
yum -y install firewalld
#Tạo 1 zone riêng

firewall-cmd --permanent --new-zone=sqlzone

firewall-cmd --reload

#Kiểm tra lại các zone

firewall-cmd --get-zones

#Thêm những luật sau vào zone: Mở ssh, mysql, chỉ cho phép ip 192.168.1.15(ip của máy muốn truy cập) truy cập và mở cổng 3306(cổng mặc định của mysql)

firewall-cmd --zone=sqlzone --add-service=mysql --permanent  
firewall-cmd --zone=sqlzone --add-service=ssh --permanent   
firewall-cmd --zone=sshzone --add-source='192.168.1.15' --permanent
firewall-cmd --zone=sqlzone --add-port=3306/tcp --permanent 
firewall-cmd --zone=sqlzone --change-interface=ens33

#Loại bỏ dịch vụ ssh trên zone public
firewall-cmd --zone=public --remove-service=ssh
firewall-cmd --reload

#kiểm tra lại

firewall-cmd --list-all-zones

# Các thiết lập firewalld trên chỉ cần khởi động máy lên là sẽ tự đọng hoạt động còn nếu muốn chỉ thiết lập lúc máy mở khi restart máy các cấu hình sẽ không hoạt động thì lọa bỏ --- permanent

```