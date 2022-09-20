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

# TÌM HIỂU VỀ WLAN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. WLAN là gì?]()
## &ensp; [1. AC là gì]()
## &ensp; [2. Wireless LAN]()
## &ensp; [3. SSID]()
## &ensp; [4. Bridge Mode AC]()
## &ensp; [5. Client Mode AC]()
## &ensp; [6. Repeater Mode Access AC]()
## &ensp; [7. WLC]()


# [II. Đặc điểm của WLAN]()
## &ensp; [1. Ưu điểm]()
## &ensp; [2. Nhược điểm]()
# [III. Cấu hình AC]()
# [IV. Tính năng Roaming trên AC]()
***
# ***I.	WLAN là gì?***
* WLAN(wireless local area network) mạng LAN không dây, là một mạng cho phép các thiết bị kết nối và giao tiếp không dây. Các thiết bị trên mạng WLAN giao tiếp qua WiFi.
* Cách thức hoạt động giống mạng LAN truyền thống chỉ khác ở chỗ cách dữ liệu được truyền đi.
* Các khái niệm trong WLAN
## ***1. AC là gì***
* AC là Access Point
* Là các thiết bị phát sóng kết nối mạng không dây cung cấp kết nối mạng cho các thiết bị đầu cuối.

![](https://cdn-fmgfa.nitrocdn.com/uVliNOEwsqAHTsYKHBOJSOWtixYQenOd/assets/static/optimized/rev-84613cc/wp-content/uploads/2019/07/access-point-la-gi-1024x1024.jpg)
## ***2. Wireless LAN***
* Thông qua các thiết bị AC, chúng tạo ra vùng mạng không dây và vùng mạng đấy được gọi là Wireless LAN
* Mạng không dây sẽ giúp mở rộng hạ tầng mạng LAN có dây bình thường và lúc này AC sẽ đóng vai trò làm trạm chung chuyển dữ liệu giữa 2 môi trường LAN có dây và Wireless LAN
* AC kết nối trực tiếp với Router sẽ sinh ra 1 vùng mạng Wireless LAN riêng độc lập với các mạng khác. Còn nếu AC kết nối với 1 Switch và Swith lại kết nối với các mạng LAN có dây thì cả vùng đó sẽ là 1 vùng mạng chung.

![](https://user-images.githubusercontent.com/52046920/191161965-b0239f59-4598-4372-af7c-0d93c868bc74.png)
## ***3. SSID***
* SSID - Service Set Identifier. Định danh mạng SSID dùng để phân biệt các mạng Wireless LAN khác nhau.

![](https://user-images.githubusercontent.com/52046920/191161972-5472470b-0663-41bb-938c-72010d506543.png)
* Các SSID ở trên cho ta thấy được các mạng phân biệt với nhau
## ***4. Bridge Mode AC***
* Các AC có sử dụng Bridge Mode có khả năng kết nối 2 hệ thống mạng LAN với nhau qua môi trường không dây

![](https://user-images.githubusercontent.com/52046920/191163390-be1fe8ff-e457-4faa-bc1f-ea85957dc3cf.png)
## ***5. Client Mode AC***
* AC có thể thiết lập ở chế độ Client và kết nối với AC khác. Lúc này Client AC có thể chia sẽ mạng Wireless LAN đó cho các mạng có dây khác kết nối với nó

![](https://user-images.githubusercontent.com/52046920/191163399-ca162b5d-26b0-4726-adb7-9074d7fed71b.png)
## ***6. Repeater Mode Access AC***
* AC thiết lập ở Repeater Mode có nhiệm vụ mở rộng Wireless LAN tuy nhiên việc này gây ảnh hưởng lớn tốc độ truy cập mạng vì vật phần phủ sống của AC Repeater và AC kết nối với nó phải chồng lên nhau ít nhất 50% để giải quyết vấn đề này

![](https://user-images.githubusercontent.com/52046920/191163400-6c2571aa-c7a3-4f3d-bd29-8d8912ac5526.png)

* Repeater AC sẽ giúp  mở rộng vùng phủ sóng hiện tại qua vùng phủ sóng rộng hơn giúp lấp đầy Wireless LAN cho 1 phòng lớn hoặc 1 công ty

![](https://user-images.githubusercontent.com/52046920/191164427-518163ec-7e45-4d04-9d9a-0d85b49cfa5a.png)
## ***7. WLC***
* WLC - Wireless LAN Controller là giải pháp giúp mở rộng Wireless LAN với mô hình quá nhiều thiết bị 
* Ví dụ một công ty muốn triển khai 75 thiết bị AC trên 1 hạ tầng mạng. thay vì cấu hình tận 75 AC thì ta chỉ cần cấu hình 1 AC đóng vai trò là WLC. Sau đó thiết bị WLC sẽ đổ cấu hình cho các AC còn lại tự động. Các AC còn lại sẽ chuyển qua chế độ Lightweight AC.
* Còn nếu hệ thống mạng chỉ có vài AC thì chỉ cần cấu hình chế độ stanalone cho từng AC và cấu hình từng AC 1

# ***II.	Đặc điểm của WLAN***
## ***1. Ưu điểm***
* Các thiết bị có thể kết nối không dây, loại bỏ được dây cáp(Giảm chi phí)
* Không bị giới hạn số cổng vật lý trên router nên có thể kết nối được nhiều thiết bị mà không bị giới hạn bởi phần cứng.
* Dễ dàng nâng cấp bằng cách thay thế các router. Không cần phải nâng cấp các dây cáp nhưng mạng truyền thống
## ***2.	Nhược điểm***
* Kém an toàn hơn so với mạng truyền thống
* Dễ bị ảnh hưởng bởi các tín hiệu khác hoặc rào cản vật lý gây nhiễu sóng hoặc bị chặn sóng dẫn đến kết nối kém và không ổn định
* Tốc độ không cao như mạng có dây, độ ổn định cũng vậy

# ***III.	Cấu hình AC***
* Các tham số phải cấu hình trên AC:
    * Tham số cơ bản:
        * DHCP
        * Chuẩn mạng không dây
        * lựa chọn kênh phát sóng(sử dụng kênh 1, 6, 11 nếu có 3 AC gần nhau để tránh nhiễu)
    * Tham số bảo mật
        * SSID
        * Phương thức xác thực không dây: WPA hoặc WPA2 PSK
        * Thuật toán mã hóa: TKIP hoặc AES
* Trên các thiết bị AC hiện nay thường sẽ có 4 Port LAN và 1 Port WAN.

![](https://user-images.githubusercontent.com/52046920/191170556-3c426f9b-f607-4a97-9f52-c9bc431ce204.png)

* Port WAN nếu kết nối với Router sẽ phải thiết lập ip cùng dải với interface kết nối trực tiếp với Router. Các PC kết nối không dây với AC sẽ được cấp dải IP riêng với DHCP. Mặc định các PC trước khi đi qua WAN sẽ phải NAT Overload

![](https://user-images.githubusercontent.com/52046920/191170551-35e9690a-1c90-45db-b2e8-03fce7afbfce.png)

* Nếu kết nối Switch với Port LAN của AC thì khi đó các máy tính kết nối với Switch sẽ thuộc cùng mạng với các máy tính đang kết nối không dây với AC. lúc này nó sẽ cấp ip bằng DHCP cho cả các máy tính kết nối với Switch

![](https://user-images.githubusercontent.com/52046920/191170558-d3d1c8ee-8f30-47fa-adeb-f823ebf2f42e.png)

* Nếu AC kết nối với Router bằng Port LAN thì các máy tính kết nối không dây sẽ tham gia vào cùng lớp mạng của interface kết nối với AC. lúc này AC sẽ tắt tính năng DHCP và để Router đóng vai trò làm DHCP Server hoặc tắt tính năng DHCP trên Router và sử dụng AC như 1 DHCP Server. AC lúc này sẽ tương tự 1 con Switch nhưng có thể phát mạng không dây

![](https://user-images.githubusercontent.com/52046920/191170561-2425720e-0196-4be2-8137-daed9c4186d2.png)

# ***IV.	Tính năng Roaming trên AC***
* Roaming là tính năng cho phép các thiết bị kết nối với vùng phủ sóng này khi di chuyển qua vùng phủ sóng khác sẽ kết nối vào mà không bị ngắt kết nối. ví dụ trong công ty ta có thể đi từ từ tầng 1 đến bất cứ tầng nào trong công ty mà không bị văng mạng do có chế roaming này khi ta di chuyển qua tầng khác ta sẽ roaming vào AC của tầng đó 
* Để sử dụng chức năng này thông thường sẽ sử dụng các thiết bị AC cùng dòng sản phẩm
* Ta cần thiết lập các giá trị như sau :
    * SSID giống nhau
    * Mật khẩu xác thực giống nhau
    * Các AC tham gia vào cùng 1 Broadcast Domain
    * Sử dụng các kênh không chông lấn với nhau
    * Vùng chồng lấn tối thiểu phải 10% để roaming có thể hoạt động ổn định
    * Chuẩn mạng không dây trên tất cả các AC phải giống nhau

![](https://user-images.githubusercontent.com/52046920/191170564-d9c1272c-0a11-4265-8fd7-2358e957de90.png)