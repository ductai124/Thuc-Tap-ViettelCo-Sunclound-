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

# TÌM HIỂU VỀ ETHERCHANNEl
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
# ***I.	EtherChannel là gì***
* Là công nghệ cho phép chúng ta nhóm nhiều đường kết nối vật lý thành 1 đường truyền ảo và mang sức mạnh của toàn bộ các đường vật lý mà nó gộp vào
* Kỹ thuật này sử dụng múc đích chính làm tăng tốc độ truyền dữ liệu và khả năng dự phòng cho hệ thống nhưng ít gây lãng phí tài nguyên.
* Khác với cân bằng tải mỗi đường vẫn chạy riêng thì EtherChannel gộp các đường vật lý lại làm 1 đường ảo. Điều này giúp cho việc tăng tốc độ của đường truyền, ngoài ra còn khắc phục điểm yếu của cân bằng tải đó là tiết lập cân bằng tải có thể bị STP loại bỏ 1 số đường nhằm chống loop trong hệ thống.
* EtherChannel có thể bó các đường link FE, GE, 10GE thành 1 đường link logical. Các port đó hợp lại như 1 port duy nhất.
* Có 2 loại giao thức EtherChannel:
    *  LACP (Link Aggregation Control Protocol): Là giao thức cấu hình chuẩn quốc tế. Có thể dùng cho mọi loại thiết bị, hỗ trợ ghép tối đa 16 Link vật lý(8 Port Active-8 Port Passive). được sử dụng nhiều hơn do có thể ghép được nhiều cổng hơn và có trên nhiều thiết bị
    * PAgP (Port Aggregation Protocol): Là giao thức cấu hình EtherChannel độc quyền của các thiết bị hãng Cisco và chỉ hỗ trợ ghép tối đa 8 link vật lý. Độc quyền trên các thiết bị cisco nên ít được sử dụng hơn.

* Điều kiện cấu hình:
    * Khi cấu hình hãy tắt hết tất cả các cổng vật lý đi và các cổng phải có cùng 1 chuẩn như nhau có tốc độ truyền tải dữ liệu như nhau
    * Các Port kết nối EtherChannel giữa 2 Switch phải tương đồng với nhau:
        * Cấu hình
        * Tốc độ
        * Băng thông 
        * Duplex(Chế độ truyền). Có 3 chế độ truyền như sau:

        ||Simplex|Half Duplex|Full Duplex|
        |-|-|-|-|
        |Hướng truyền tín hiệu|Đơn hướng|2 chiều, mỗi lần theo 1 hướng|2 chiều, đồng thời theo 2 hướng|
        |Gửi/nhận|Bên gửi chỉ có thể gửi dữ liệu|Bên gửi có thể gửi hoặc nhận dữ liệu trong 1 thời điểm|Bên gửi có thể gửi và nhận dữ liệu cùng 1 lúc|
        |Hiệu suất|Chế độ truyền kém nhất|Tốt hơn Simplex|Tốt nhất|
        |Ví dụ áp dụng|Bàn phím|Bộ đàm|Điện thoại|
        * NativeVlan và các Vlan
        * Switchport mod(Trunk, Access)
* Có 3 chế độ:
    * On: Chế độ cấu hình EtherChannel tĩnh, chế độ này thường không được dùng vì các Switch cấu hình EtherChannel có thể hoạt động được và cũng có thể không hoạt động được vì các Switch được cầu hình bằng tay phục thuộc vào con người nên hoàn toàn không có bước thương lượng trao đổi chính sách giừa bên dẫn đến khả năng Loop cao và bị STP Block.
    * Active: Chế độ tự động – Tự động thương lượng với đối tác
    * Passive: Chế độ bị động – Chờ được thương lượng 
# ***II.	Cấu hình thủ công***
* Cấu hình gộp 2 cổng fa0/1-q của 2 switch

![](https://user-images.githubusercontent.com/52046920/185838854-ce1da164-3ce5-4eeb-9863-2fcfab844c70.png)
* Tại SW1 
```cisco
SW1(config)int range fa0/1-4
SW1(config-if-range)#shutdown
SW1(config-if-range)#channel-group 1 mode on
SW1(config-if-range)#int port-channel 1
SW1(config-if)#shutdown 

```
* Tại SW2
```cisco
SW2(config)int range fa0/1-4
SW2(config-if-range)#shutdown
SW2(config-if-range)#channel-group 1 mode on
SW2(config-if-range)#int port-channel 1
SW2(config-if)#shutdown 

```
* Sau khi cấu hình xong tại 2 SW ta mới bắt đầu bật các interface lên
```cisco
\\\SW1
SW1(config)int range fa0/1-4
SW1(config-if-range)#no shutdown
SW1(config-if-range)#int port-channel 1
SW1(config-if)#shutdown 
SW1(config-if)#no shutdown 

\\\SW2
SW2(config)int range fa0/1-4
SW2(config-if-range)#no shutdown
SW2(config-if-range)#int port-channel 1
SW2(config-if)#shutdown 
SW2(config-if)#no shutdown 
```
* Nếu không bật tắt các interface như vậy có thể xảy ra khả năng các cổng không đồng bộ sẽ có cổng bị tắts
* Các mode có thể thiết lập

![](https://user-images.githubusercontent.com/52046920/185838767-0f45c71f-ff49-4760-ad7d-433dee538f1d.png)
* Kiểm tra 
```cisco
SW1#show etherchannel summary       // kiểm tra trạng thái các cổng
SW1#show mac-address-table          //các địa chỉ mac từ Sw2 gửi tới được lưu lại

SW2#show etherchannel summary
SW2#show mac-address-table 
```
![](https://user-images.githubusercontent.com/52046920/185838779-16865e65-6426-43ef-9c4e-04121f509e6d.png)

![](https://user-images.githubusercontent.com/52046920/185839137-2733bc38-dbe5-4b2d-9859-6ec64121916d.png)
* Muốn xóa cấu hình về mặc định sử dụng các câu lệnh sau
```cisco
SW2(config)default int range fa0/1-4
SW2(config-if-range)#no int port-channel 1
```

# ***III.	Cấu hình EtherChannel bằng giao thức LACP hoặc PAgP***
## ***1. Cấu hình bằng giao thức LACP***
* LACP có 2 mode channel-group là:
    * Active: định kỳ gửi bản tin lacp để thương lượng tham gia kết nối etherchannel
    * Passive:không định kỳ gửi bản tin lacp mà khi nhận được lacp nó sẽ hồi đáp lại và thương lượng tham gia kết nối etherchannel
* Cấu hình LACP

![](https://user-images.githubusercontent.com/52046920/185838772-87fa4bea-718f-42b9-a36d-c6755aa426f5.png)
* SW1
```cisco
SW1(config)#int range f0/1-2
SW1(config-if-range)shutdown
SW1(config-if-range)#channel-protocol lacp 
SW1(config-if-range)#channel-group 1 mode active 
```
* SW2
```cisco
SW2(config)#int range f0/7-8
SW2(config-if-range)shutdown
SW2(config-if-range)#channel-protocol lacp 
SW2(config-if-range)#channel-group 1 mode passive
```
* Do mode auto chỉ phản hồi lại gói tin lacp nếu có gói tin được gửi đến nên nếu cả 2 switch để thiết lập mode passive thì sẽ không thiết lập được.
* Có thể thiết lập cả 2 đầu là mode active
* Sau đó bật các interface của các SW đó lên lại
* Kiểm tra

![](https://user-images.githubusercontent.com/52046920/185838760-7dc3d660-0277-4afa-a29a-3ae8dc92b2d9.png)
![](https://user-images.githubusercontent.com/52046920/185838760-7dc3d660-0277-4afa-a29a-3ae8dc92b2d9.png)

## ***2. Cấu hình bằng giao thức PAgP***
* * PAgP có 2 mode channel-group là:
    * Desirable: định kỳ gửi bản tin lacp để thương lượng tham gia kết nối etherchannel
    * Auto:không định kỳ gửi bản tin lacp mà khi nhận được lacp nó sẽ hồi đáp lại và thương lượng tham gia kết nối etherchannel
* Cấu hình PAgP
![](https://user-images.githubusercontent.com/52046920/185838854-ce1da164-3ce5-4eeb-9863-2fcfab844c70.png)
* SW1
```cisco
SW1(config)#int range f0/1-2
SW1(config-if-range)shutdown
SW1(config-if-range)#channel-protocol lacp 
SW1(config-if-range)#channel-group 1 mode desirable 
```
* SW2
```cisco
SW2(config)#int range f0/1-2
SW2(config-if-range)shutdown
SW2(config-if-range)#channel-protocol pagp 
SW2(config-if-range)#channel-group 1 mode auto
```
* Do mode auto chỉ phản hồi lại gói tin pagp nếu có gói tin được gửi đến nên nếu cả 2 switch để thiết lập mode auto thì sẽ không thiết lập được.
* Có thể thiết lập cả 2 đầu là mode desirable
* Sau đó bật các interface của các SW đó lên lại
* Kiểm tra

![](https://user-images.githubusercontent.com/52046920/185838773-1ab0dcaa-2bdc-42ad-bbbb-0535812fa27d.png)

# ***IV. Cấu hình EtherChannel hoạt động ở chế độ Layer 3***