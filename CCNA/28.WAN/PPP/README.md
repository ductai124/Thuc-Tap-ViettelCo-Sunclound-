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

# TÌM HIỂU VỀ CÔNG NGHỆ PPP TRÊN SERIAL INTERFACE
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Giao thức PPP là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/28.WAN/PPP/README.md#igiao-th%E1%BB%A9c-ppp-l%C3%A0-g%C3%AC)
# [II. Các bước thiết lập phiên kết nối PPP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/28.WAN/PPP/README.md#ii-c%C3%A1c-b%C6%B0%E1%BB%9Bc-thi%E1%BA%BFt-l%E1%BA%ADp-phi%C3%AAn-k%E1%BA%BFt-n%E1%BB%91i-ppp-1)
# [III. Cấu hình PPP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/28.WAN/PPP/README.md#iii-c%E1%BA%A5u-h%C3%ACnh-ppp-1)

***
# ***I.	Giao thức PPP là gì***
* PPP là giao thức lớp 2 phổ biến cho mạng WAN. Hai thành phần của PPP tồn tại: LCP (Link Control Protocol) đàm phán kết nối và NCP (Network Control Protocol) đóng gói lưu lượng.
    *  Giao thức kiểm soát liên kết (Link Control Protocol): LCP được sử dụng để thiết lập, định cấu hình và kiểm tra kết nối liên kết dữ liệu. Nó linh hoạt trong việc xử lý các kích cỡ khác nhau của các gói, phát hiện một liên kết ngược, lỗi cấu hình và chấm dứt liên kết.
    * Giao thức điều khiển mạng (Network Control Protocol): NCP được sử dụng để thiết lập và định cấu hình các giao thức lớp Mạng khác nhau.
    PPP cho phép sử dụng đồng thời nhiều giao thức lớp Mạng. 
* Có hai kiểu đóng gói dữ liệu của PPP là PPPoE (Point-to-Point Protocol over Ethernet) và PPPoA (Point-to-Point Protocol over ATM), chúng được sử dụng bởi các nhà cung cấp dịch vụ Internet để kết nối tới dịch vụ Internet.

![Cấu trúc frame](https://user-images.githubusercontent.com/52046920/178717374-620bd5f9-ce5d-49b7-afce-c52754d39a88.PNG)
* Cấu trúc frame của PPP:
    * FLAG : Có 1 byte với mẫu bit 01111110.

    * ADDRESS : 1 byte được đặt thành 11111111 trong trường hợp phát sóng.

    * CONTROL : 1 byte được đặt thành giá trị không đổi là 11000000.

    * PROTOCOL : 1 hoặc 2 byte xác định loại dữ liệu có trong INFORMATION.

    * INFORMATION :Mang dữ liệu từ lớp mạng. Độ dài tối đa là 1500 byte.

    * FCS : Đây là một chuỗi kiểm tra khung 2 byte hoặc 4 byte để phát hiện lỗi. Mã tiêu chuẩn được sử dụng là CRC (mã dự phòng theo chu kỳ).
* Có 2 kiểu xác thực là PAP và CHAP. CHAP sẽ bảo mật hơn so với PAP
    * PAP: Sử dụng bắt tay 2 bước

        ![](https://user-images.githubusercontent.com/52046920/190960907-09af41c8-120b-46a8-9382-110311fc43dd.png)
        * Bước 1: Router A muốn truy cập qua Router B Thì phải gửi User name, Pass dạng Clear text(không bảo mật về User name, Pass)
        * Bước 2: Router B đồng ý và chấp nhận kết nối
    * CHAP: Sử dụng bắt tay 3 bước

        ![](https://user-images.githubusercontent.com/52046920/190960913-a04f3f18-2a4b-47bd-836f-3e9ae0118386.png)
        * Bước 1: Router A gửi qua Router HQ(Head Quarter là trung tâm) 1 mẫu tin Chanllenge
        * Bước 2: Router B Sẽ dụng hàm băm để băm mẫu tin và User name, Password của mình kia rồi gửi lại thông tin là Response. Do được băm nên bảo mật được thông tin.
        * Bước 3: Router HQ kiểm tra thông tin. Nếu thấy phù hợp nó sẽ gửi đáp trả là xác nhận.
# ***II. Các bước thiết lập phiên kết nối PPP***
* Để thiết lập phiên kết nối giữa 2 thiết bị đầu cuối thì 2 thiết bị này sẽ trải qua 3 giải đoạn sau:
    * Thiết lập đường link giữa 2 thiết bị
    * Xác thực lẫn nhau giữa 2 thiết bị này thông qua giao thức xác thực PAP hoặc CHAP
    * Triển khai giao thức PPP sau khi thiếp lập

# ***III. Cấu hình PPP***
* Câu lệnh cấu hình
```cisco
R1(config)#interface serial 0/3/0
R1(config-if)encapsulation ppp
```
* Ví dụ: Cho 2 Router
* Đầu tiền phải gắn serial cho 2 Router

![](https://user-images.githubusercontent.com/52046920/190963048-d0baf9ea-46f1-4c0d-bb22-fc181dca2f77.png)

* Sau đó dùng 1 trong 2 dây nối serial DTE hoặc serial DCE nối 2 router lại qua cồng Serial 0/3/0 

![](https://user-images.githubusercontent.com/52046920/190963306-b3c5df5b-342a-46f6-a85a-3ddb139dfdaf.png)

* Sau khi nối xong
![](https://user-images.githubusercontent.com/52046920/190963303-4392abbf-de9a-499a-aeff-af13ccd8d116.png)

* Tiến hành cấu hình PPP trên 2 Router
* Tại R1
```cisco
R1(config)#interface serial 0/3/0
R1(config-if)encapsulation ppp
R1(config-if)no shut
```

* Tại R2
```cisco
R2(config)#interface serial 0/3/0
R2(config-if)encapsulation ppp
R2(config-if)no shut
```

* Kiểm tra bằng câu lệnh
```cisco
R1#show interface s0/3/0

R2#show interface s0/3/0
```

![](https://user-images.githubusercontent.com/52046920/190964137-dc64feeb-62c2-4472-89e4-c2d8f068efb4.png)

![](https://user-images.githubusercontent.com/52046920/190964141-7df390cd-f01c-46bb-a568-d6e92757bd58.png)

* Kết nối thành công

* Nếu không kết nối thành công

![](https://user-images.githubusercontent.com/52046920/190966600-28a04cf1-bb95-4f42-8cfa-f51b02c68027.png)

* Cấu hình xác thực bằng câu lệnh như sau

    ![](https://user-images.githubusercontent.com/52046920/190972216-e5b56323-99ef-4592-93ab-a8604d712330.png)
    * PAP
        * Xác thực 1 chiều
            * Tại server
            ```cisco
            R1(config)#username R2 password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp authentication pap
            ```
            * Tại client
            ```cisco
            R2(config)#interface serial 0/3/0
            R2(config-if)encapsulation ppp
            R2(config-if)no shut
            R2(config-if)ppp pap sent-username R2 password Tai!123
            ```
        * Xác thực 2 chiều
            ```cisco
            R1(config)#username R2 password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp authentication pap
            R2(config-if)ppp pap sent-username R2 password Tai!123
            ```
            * Tại client
            ```cisco
            R2(config)#username R1 password Tai!123
            R2(config)#interface serial 0/3/0
            R2(config-if)encapsulation ppp
            R2(config-if)no shut
            R2(config-if)ppp authentication pap
            R2(config-if)ppp pap sent-username R1 password Tai!123
            ```
        * Username là host name của Router còn lại
    * CHAP
        * Xác thực 1 chiều
            * Tại server
            ```cisco
            R1(config)#username siteHN password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp authentication chap
            R1(config-if)ppp authentication chap callin
            ```
            * Tại client
            ```cisco
            R1(config)#username [Host name server] password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp chap hostname siteHN
            R1(config-if)ppp chap password Tai!123
            ```
        * Xác thực lẫn nhau
            * Tại server
            ```cisco
            R1(config)#username [Hostname client] password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp authentication chap
            ```
            * Tại client
            ```cisco
            R1(config)#username [Host name server] password Tai!123
            R1(config)#interface serial 0/3/0
            R1(config-if)encapsulation ppp
            R1(config-if)no shut
            R1(config-if)ppp authentication chap
            ```
        * Lưu ý password 2 router phải giống nhau. Username phải trùng với hostname của Router còn lại so với Router đang đứng tại đó
* Có thể bật debug lên để quan sát quá trình thực hiện xác thực trên dòng lệnh hiển thị ra màn hình
```cisco
R1#debug ppp authentication
R1#debug ppp negotiation
```

![](https://user-images.githubusercontent.com/52046920/190972211-f6a87e14-6c2b-4bf1-8041-a3ab2a8f4098.png)
