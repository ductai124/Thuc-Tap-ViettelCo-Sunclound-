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

# TÌM HIỂU VỀ TELNET
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
# ***I.	TELNET là gì***
* Telnet viết tắt là Terminal network là 1 giao thức mạng được dùng trên các kết nối với Internet hoặc mạng LAN. 
* Telnet cung cấp những phiên đăng nhập từ xa giữa các máy, thiết bị trên Internet để quản lý các thiết bị khác nhau, có khả năng cung cấp giao tiếp tương tác 2 chiều. Giúp người quản trị có thể quản lý cấu hình các thiết bị từ xa mà không cần phải kết nối trực tiếp 
* Giao thức này chỉ có dòng lệnh không bao gồm đồ họa. 
* Trước đây telnet là 1 giao thức rất phổ biến được sử dụng bỏi nhiều loại thiết bị, trong các môi trường khác nhau như:
    * Router
    * Switch
    * Firewall
    * Linux
    * Window
# ***II.	Cấu hình Telnet***
## ***1.	Cấu hình cơ bản***
![](https://user-images.githubusercontent.com/52046920/182316204-5099bd1f-0342-4991-b51b-2c9703f96b17.png)
* Trước khi cấu hình telnet hãy kiểm tra máy tính và router đã có thể kết nối với nhau chưa thông qua ping.
* Trong mô hình trên muốn cấu hình dịch vụ telnet lên router thì thực hiện câu lệnh.
```cisco
R1(config)#line vty 0 4         \\\cho phép 5 người telnet dồng thời đến router (Từ 0 đến 4), nếu chỉ muốn 1 người thì chỉ số là 0
R1(config-line)#password 123            ////mật khẩu telnet
R1(config-line)#login       ///khởi động kiểm tra mật khẩu
```


* Sau đó ta tiến hành telnet đến router bằng câu lệnh
```cmd
telnet 192.168.1.1
```
* sau đó nhập mật khẩu đã thiết lập ở trên và ta đã telnet thành công đến router

![](https://user-images.githubusercontent.com/52046920/182275169-ea282dbe-afdf-46a7-b0ab-4882f47b9309.png)
* Tuy nhiên để có thể thực hiện cấu hình trên router thì bắt buộc phải thực hiện đặt mật khẩu enable nếu không khi telnet ta sẽ chỉ có thể đứng ở chế độ user chỉ có thể xem thông số chứ không thể cấu hình được và để vào các chế độ cấu hình thì cần phải thiết lập mật khẩu enable cho router nếu không nó sẽ hiển thị như sau.

![](https://user-images.githubusercontent.com/52046920/182275174-b6c2cce2-2782-40fd-a0fb-882593d0640e.png)

* Sau khi đã thiết lập mật khẩu enable thì ta có thể đứng từ xa telnet vào router và có thể truy cập vào các chế độ khác nhau để cấu hình nếu có mật khẩu enable
![](https://user-images.githubusercontent.com/52046920/182275952-b0c50afc-532c-422e-9da1-383ab8ba9429.png)
* Khi vượt quá số người truy cập đã thiết lập các thiết bị khác sẽ không thể telnet được đến với router nữa

![](https://user-images.githubusercontent.com/52046920/182275183-803458e9-feda-48c3-8ec4-8a94560b3413.png)
* Ta có thể kiểm tra những ai đang telnet vào router bằng câu lệnh
```cisco
Router#show user

```
![](https://user-images.githubusercontent.com/52046920/182310674-d7d6f8f7-c79d-4493-89fb-ea1bf79e042d.png)
## ***2.	Thay đổi hoặc gỡ bỏ mật khẩu Telnet***
* Muốn thay đổi mật khẩu telnet ta thực hiện truy cập lại line vty mà chúng ta thiết lập rồi thực hiện câu lệnh
```cisco
R1(config)# line vty 0 4
R1(config-line)# no passwork
```
* Khi gỡ mật khẩu thì toàn bộ người dùng muốn telnet đến router đều không thực hiện được và muốn đổi mấy khẩu thì ta thực hiện như bước thiết lập mật khẩu telnet cho router
```cisco
R1(config)#line vty 0 4         
R1(config-line)#password tai123            
R1(config-line)#login       
```
* Không cần gỡ mật khẩu trước khi đổi mật khẩu
* Có thể cấu hình mật khẩu cho từng người kết nối theo thứ tự tuy nhiên trên thực tế sẽ không ai làm việc này do không biêt được mình là người số thứ tự bảo nhiêu telnet đến với thiết bị và dẫn đến phải dò mật khẩu gây mất thời gian, khó chịu 
## ***3.	Cấu hình xác thực bằng username và password***
* Bằng việc cấu hình này ta có thể nhận biết được người nào đang telnet vào router dễ dang cho việc kiểm soát và có thể phân chia ra mỗi người 1 phiên telnet riêng.
* Ta cấu hình như sau:

```cisco
R1(config)#username tai password 123            \\\Khai báo user tai với mật khẩu là 123
R1(config)#username tai password 123            \\\khai bảo user my vỡi mật khẩu 1234
R1(config)#line vty 0 4
R1(config-line)#no password         ///Do đã thiết lập từng user riêng nên không cần mật khẩu chung telnet nữa
R1(config-line)#login local             ///
```
* Sau đó tại máy tính thực hiện telnet đến router, lúc này router sẽ bắt phải đăng nhập bằng username và password

![](https://user-images.githubusercontent.com/52046920/182315959-4641b465-37e0-42cb-a1d5-fa5cd3899b69.png)
* Ta kiểm tra những phiên telnet đến router bằng câu lệnh
```cisco
R1# show users
```

![](https://user-images.githubusercontent.com/52046920/182315956-6a4234c7-eaca-45cb-bade-3c9af00f55a3.png)

## ***4.	Cấu hình xác thực bằng username và password***
* Việc cấc hình này nhằm mục đích giúp cho việc cấu hình trở nên nhanh chóng hơn và thường sử dụng để lab là chủ yếu. Thực tế sẽ không sử dụng cấu hình này.
* Thực hiện telnet không cần password bằng các câu lệnh sau
```cisco
R1(config)#line vty 0 4            
R1(config-line)#no login       
```

![](https://user-images.githubusercontent.com/52046920/182320588-c8077449-5137-475b-a60f-fa131c20e932.png)
* Truy cập thẳng  vào chế độ đặc quyền mà không cần nhập bất cứ 1 mật khẩu nào thực hiện như sau
```cisco
R1(config)#line vty 0 4         
R1(config-line)#privilege level 15
R1(config-line)#no login       
```

![](https://user-images.githubusercontent.com/52046920/182320598-f3ef54b7-46a3-408a-8f8e-60cb2a9b2a4d.png)

## ***5.	Configuration Lock chỉ cho phép một người***
* Tại 1 thời điểm chỉ chó phép 1 người telnet vào thiết bị
* Cấu hình bằng câu lệnh như sau
```cisco
R1(config)#configuration mode exclusive auto
```

## ***6.	Thay đổi Port dịch vụ telnet***
* Do telnet chạy trên cổng mặc định là 23 nên có nguy cơ bị tận dụng để tấn công cổng vậy nên thay đổi cổng sẽ làm giảm, chậm khả năng bị tấn công đi hơn là để cổng mặc định.
* 