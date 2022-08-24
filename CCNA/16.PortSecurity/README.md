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

# TÌM HIỂU VỀ PORTSECURITY
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
# ***I.	Tổng quan PortSecurity***
* Là một tính năng an ninh thường được triển khai trên Switch layer 2 để ngăn chặn người lạ xâm nhập vào hệ thống mạng nội bộ, giúp chống lại cuộc tấn công giả mạo Default MAC ở trong hệ thống. 
* PortSecurity có thể giới hạn đầu vào các interface bằng cách hạn chế và xác định địa chỉ MAC của các máy trạm được phép truy cập vào.
* Khi các máy được phép truy cập vào cổng truy cập tuy nhiên đã vượt quá giới hạn cho phép hoặc 1 máy tinh có địa chỉ MAC không được cho phép truy cập vào cổng lúc này thì vi phạm bảo mật sẽ xảy ra. Khi vi phạm xảy ra thì ta có thể cấu hình các hành động tương ứng với các vi phạm đó như:
    * shutdown: Ngay lập tức đóng cổng lại
    * Restrict: Port sẽ loại bỏ frame của máy tính gửi đến mà có MAC không hợp lệ, không ghi log
    * Protect: Port sẽ loại bỏ frame của máy tính gửi đến mà có MAC không hợp lệ đồng thời tạo ra log cảnh báo(Thường không được sử dụng)
# ***II.	Phương thức xử lý Port vi phạm***
* Giả sử cho mô hình:

![](https://user-images.githubusercontent.com/52046920/186360356-b8f64a70-57de-4d80-88a1-7d641e466509.png)
* Để cấu hình cần triển khai 4 câu lệnh sau
```cisco
///Kích hoạt PortSecurity trên 1 interface

SW1(config)#int e0/1
SW1(config-if)# switchport mode access                  \\\có thể thiết lập mode trunk cũng được
SW1(config-if)# switchport port-security

///Giới hạn số địa chỉ MAC được gửi dữ liệu port này, ở đây sẽ cấu hình chỉ để 1 địa chỉ MAC duy nhất được gửi dữ liệu vào port e0/1

SW1(config-if)#switchport port-security maximun 1

////Địa chỉ MAC được chỉ định hợp lệ khi gửi dữ liệu vào cổng

SW1(config-if)#switchport port-security mac-address 0060.5C20.AC7B

///Phương thức xử lý khi xảy ra vi phạm, ở đây là nếu có địa chỉ MAC ngoài địa chỉ được cấu hình ở trên gửi dữ liệu đến port port sẽ tự động đóng lại.

SW1(config-if)#switchport port-security violation shutdown
```

* Để bật lại cổng ở chế độ shutdown có 2 cách sau đây
```cisco
\\\Cách 1
SW1(config)#int f0/1
SW1(config-if)#shutdown 
SW1(config-if)#no shutdown 


\\\Cách 2
///Bật thời gian khôi phục lại khi có lỗi
SW1(config)#errdisable recovery cause psecure-violation
///Thiết lập thời gian hôi phục lại trạng thái khi có lỗi, sau 30 giây cổng sẽ được mở lại
Switch(config)#errdisable recovery interval 30
```
* Ping từ PC đến router và kiểm tra từng chế độ bằng câu lệnh
```cisco
///xem trạng thái cổng
SW1#show interfaces e0/1 status
///xem port security
SW1#show port-security
```

### Kiểm tra chế độ shutdown
* Cổng tự động tắt

![](https://user-images.githubusercontent.com/52046920/186360359-64cc3aca-52ef-4bc4-856c-4cd7d0c86e37.png)
* Ghi lại số lần lỗi

![](https://user-images.githubusercontent.com/52046920/186360360-d29317f9-1f9a-476c-bbf2-141a9af7910a.png)
 * Port hồi phục lại trạng thái sau 30 giây

![](https://user-images.githubusercontent.com/52046920/186360324-d1e9c3e1-5038-4d3e-acfb-549050a350d6.png)

### Kiểm tra chế độ Restrict
* Log được hiển thị trên màn hình

![](https://user-images.githubusercontent.com/52046920/186360326-593a7879-c1e6-4d19-99e7-e7c314099966.png)
* Đếm lại lỗi

![](https://user-images.githubusercontent.com/52046920/186360329-69858e10-9d55-4dba-a9a5-838e2b291b9a.png)

###  Kiểm tra chế độ Protect

![](https://user-images.githubusercontent.com/52046920/186360319-d653d3bc-8787-40d7-8246-7252bde9a8e8.png)

* Chế độ Protect này chặn hủy gói tin đi đến do MAC khác với MAC thiết lập cho phép tuy nhiên không hiển thị bất cứ thông tin gì và không lưu lại số lần lỗi gây ra khó khăn trong kiểm soát. Do vậy ta nên sử dụng 2 chế độ còn lại


* Kiểm tra lại các thiết lập PortSecurity bằng câu lệnh
```cisco
SW1#show running-config interface e0/1
```

![](https://user-images.githubusercontent.com/52046920/186364686-a641b48f-e233-46ef-9bda-d57364069bce.png)
* Kiểm tra lại các port đang vi phạm bằng câu lệnh
```cisco
SW1#show interfaces status err-disabled
```

![](https://user-images.githubusercontent.com/52046920/186364700-d80b5057-0a4c-4b1b-840d-7cb0f8c5bd22.png)
* Kiểm tra lại tính năng PortSecurity
```cisco
SW1#show port-security interface e0/1
```

![](https://user-images.githubusercontent.com/52046920/186364697-923ddc53-3745-4978-b6d8-311c92001a5d.png)

* Kiểm tra các địa chỉ hợp lệ trong PortSecurity
```cisco
SW1#show port-security address
```

![](https://user-images.githubusercontent.com/52046920/186365508-86521313-053b-4c45-a2e8-f04a5e6c35da.png)

# ***III.	Phương thức tự động cập nhật MAC hợp lệ***
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186381985-db02db56-5ce2-491d-9fb3-7c3ec77d9e97.png)
* Ta muốn giới hạn chỉ 2 địa chỉ MAC của 2 PC1 và PC2 có thể đi qua cổng e0/1 của SW1 bằng câu lệnh

```cisco
SW1(config)#int e0/1
SW1(config-if)# switchport mode access
SW1(config-if)# switchport port-security
SW1(config-if)#switchport port-security maximun 3           ///Do tính cả địa chỉ MAC của SW liền kề địa chỉ MAC này được tự động thêm vào
SW1(config-if)#switchport port-security mac-address 0050.7966.6803
SW1(config-if)#switchport port-security mac-address 0050.7966.6805
SW1(config-if)#switchport port-security violation shutdown
```
* Kiểm tra các địa chỉ MAC được cho phép đi qua SW1
```cisco
SW1#show port-security address
```

![](https://user-images.githubusercontent.com/52046920/186381988-ff0174c0-35c2-4028-b3be-327fd23b124d.png)

* Thay vì cấu hình từng địa chỉ MAC 1 ta có thể cấu hình cho Switch học các địa chỉ MAC đầu tiên gửi đến. Các địa chỉ MAC đầu tiên gửi đến sẽ được lưu lại cho phép đi qua Switch.

* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/186382008-12a5b8f9-8ca4-4de8-8080-47f2998c2400.png)
```cisco
SW1(config)#int f0/3
SW1(config-if)# switchport mode access
SW1(config-if)# switchport port-security
SW1(config-if)#switchport port-security maximun 3
SW1(config-if)#switchport port-security mac-address sticky
SW1(config-if)#switchport port-security violation shutdown
```
* Ta có thể phối hợp sticky và cấu hình thủ cổng

* Sau khi cấu hình xong thực hiện ping đến router để SW1 học được MAC
* Kiểm tra các địa chỉ MAC được cho phép đi qua SW1
```cisco
SW1#show port-security address
```
![](https://user-images.githubusercontent.com/52046920/186382002-5e9d26f8-d5ed-4489-a215-3768339f307a.png)

* Xóa các địa chỉ sticky đi để thiết SW1 học lại các địa chỉ MAC bằng câu lệnh
```cisco
SW1#clear port-security sticky
```

* Muốn gỡ bỏ cấu hình có 2 cách
```cisco
///Cách 1
SW(config)#default int f0/3

///Cách 2
SW1(config)#int f0/3
SW1(config-if)#no switchport port-security
SW1(config-if)#no switchport port-security maximun 3
SW1(config-if)#no switchport port-security mac-address sticky
SW1(config-if)#no switchport port-security violation shutdown
```