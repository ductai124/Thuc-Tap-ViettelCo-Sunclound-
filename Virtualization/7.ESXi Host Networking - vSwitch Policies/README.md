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

# TÌM HIỂU VỀ ESXi HOST NETWORKING - vSWITCH POLOCIES
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. vSwitch use cases]()

## &ensp; [1. Use case 1]()

## &ensp; [2. Use case 2]()

## &ensp; []()

# []()
***
# ***I.	vSwitch use cases***
## ***1. Use case 1***

* Có duy nhất 1 vSwitch cấu hình VMware vSphere tối đa là 4088 Ports

![](https://user-images.githubusercontent.com/52046920/196600875-f1408636-7d86-40f6-aa7d-5135e59080ea.png)
* Với Use case 1 có thể tạo 2 vSwitch Port Groups
    * VM port group: cho VMs Network
    * VMkernel port group: cho ESXi mgmt. & Services

![](https://user-images.githubusercontent.com/52046920/196600880-6a496dfe-9a47-4c45-8f98-482bd4def7a1.png)
## ***2. Use case 2***
* Có nhiều vSwitch tuy nhiên số cổng hoạt động tối đa chỉ có 4096 Port trong 1 host

![](https://user-images.githubusercontent.com/52046920/196600888-b300abf1-f2f6-4671-83d7-3806ed83e41b.png)
* Sử dụng từng Group Port thay vì cấu hình tất cả các Group Port trên cùng một vswitch
* Khi truy cập vào máy chủ ESXi > Network > Port groups, ta có thể tìm thấy tất cả các nhóm cổng
* VLAN ID là tuỳ chọn, nếu mạng vật lý có số VLAN, chúng ta cần nhập các số VAN đó vào đây, ngược lại có thể để trống giá trị mặc định là 0
Và đây được coi là nhóm cổng vSwith tiêu chuẩn
