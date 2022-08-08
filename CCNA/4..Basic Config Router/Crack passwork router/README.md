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

# TÌM HIỂU VỀ CRACK PASSWORK TRÊN CISCO ROUTER
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Load Startup-config(Tiến trình khởi động)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/Basic%20Config%20Router/Crack%20passwork%20router/README.md#iload-startup-configti%E1%BA%BFn-tr%C3%ACnh-kh%E1%BB%9Fi-%C4%91%E1%BB%99ng)

# [II. Crack Password trên cisco Router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/Basic%20Config%20Router/Crack%20passwork%20router/README.md#ii-crack-password-tr%C3%AAn-cisco-router)
***
# ***I.	Load Startup-config(Tiến trình khởi động)***
* Tiến trình khởi động phải trải qua 4 giai đoạn gồm
    * POST(Power On Self Test): kiểm tra phần cứng, nếu trong quá trình lắp đặt mà thiếu thiết bị trong router nó sẽ phát tín hiệu cảnh báo ví dụ quên gắn Ram cho router
    * Bootstrap: danh sách các mã lệnh giúp router khởi động, giai đoạn này nó sẽ Load boostrap
    * Cisco Internetwork Operating system: Cisco sẽ tìm và tải hệ điều hành từ bộ nhớ Flash qua Ram
    * Configuration: Router sẽ tìm và tải file config trong nó là Startup-config vào bộ nhớ Ram(running config)
![]()
* Nếu Sisco router không có startup config trong NVRAM thì nó sẽ rơi vào chế độ Startup config. Quá trình khởi động của 1 router bị chi phối bởi 1 tham số là Config-register(Giá trị thanh ghi). Nếu thanh ghi được thiết lập là  0x2102 thì nó sẽ sử dụng file startup config nhưng nếu thanh ghi có giá trị là 0x2142 thì nó sẽ khởi động với cấu hình trắng (Setup mod ban đầu). Từ đó ta biết được đây là mấu chốt để có thể Crack mật khẩu và khởi động lại mật khẩu cho thiết bị Router.
* Có thể kiểm tra giá trị thanh ghi bằng câu lệnh
```cisco
R1> show version
```

![](https://user-images.githubusercontent.com/52046920/182055986-90de8dd6-37ab-4631-a61d-9589329893f5.png)

# ***II. Crack Password trên cisco Router***
* Mấu chốt của việc này nằm ở chỗ thay đổi thanh đổi giá trị thanh ghi thành 0x2142 để router có thể trở về cấu hình trắng và ta có 2 cách để làm việc này.
* Sử dụng 1 trong 2 câu lệnh
```cisco
R1(config)# config-register 0x2142
```
* Tuy nhiên câu lệnh trên lại chỉ có thể sử dụng khi truy cập chế độ global config mà để vào được chế độ này thì phải nhập mật khẩu enable và mật khẩu console vậy nên để trực quan hơn ta se tiến hành crack mật khẩu từ bên ngoài.
* Ta sẽ phải đứng ở chế độ Rommon để điều chỉnh thanh ghi. để truy cập chế độ đó ta cần thực hiện các bước sau:
    * Tắt nguồn router
    * bật nguồn lên và trong khoảng 30 giây t bấm tổ hợp phím ctrl + break(ở dell là ctrl+fn+B, các tổ hợp phím sẽ khác nhau trên từng dòng máy nếu bàn phím không có phím break)

    ![](https://user-images.githubusercontent.com/52046920/182055983-35f582fc-e0f1-4139-9924-538c225746dc.png)
    * Thực hiện câu lệnh
    ```cisco
    rommon 1 > confreg 0x2142
    rommon 2 > reset
    ```
    
    ![](https://user-images.githubusercontent.com/52046920/182055984-cd1cafd8-47a1-4dff-bb25-7b302e1deaee.png)
    * Sau đó router sẽ được khởi động với chế độ cấu hình trắng mặc dù startup config vẫn còn. ta sẽ tiến hành copy startup config qua running config để lấy lại cấu hình sau đó vào chế độ global config để sửa lại mất khẩu theo ý muốn. 
    * Sau khi thiết lập lại mật khẩu thì ta cần điều chỉnh lại thanh ghi về đúng giá trị để khi khởi động lại nó sẽ nhảy và file startup config
    ```cisco
    R1(config)# config-register 0x2102
    ```
    * Và ghi lại dữ liệu vào startup config sau đó khởi động lại và kiểm tra kết quả.
