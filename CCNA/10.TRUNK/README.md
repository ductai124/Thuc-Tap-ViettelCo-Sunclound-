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

# TÌM HIỂU VỀ TRUNK
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Tổng quan về đường Trunk](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/10.TRUNK/README.md#it%E1%BB%95ng-quan-v%E1%BB%81-%C4%91%C6%B0%E1%BB%9Dng-trunk)
# [II. Cấu hình kết nối Trunk trên Cisco Switch](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/10.TRUNK/README.md#iic%E1%BA%A5u-h%C3%ACnh-k%E1%BA%BFt-n%E1%BB%91i-trunk-tr%C3%AAn-cisco-switch)
# [III. Giải pháp mở rộng VLAN nếu thiếu Port trên Switch](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/10.TRUNK/README.md#iiigi%E1%BA%A3i-ph%C3%A1p-m%E1%BB%9F-r%E1%BB%99ng-vlan-n%E1%BA%BFu-thi%E1%BA%BFu-port-tr%C3%AAn-switch)
# [IV. Giao thức VTP đồng bộ hóa thông tin VLAN giữa các Switch](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/10.TRUNK/README.md#ivgiao-th%E1%BB%A9c-vtp-%C4%91%E1%BB%93ng-b%E1%BB%99-h%C3%B3a-th%C3%B4ng-tin-vlan-gi%E1%BB%AFa-c%C3%A1c-switch)

***
# ***I.	Tổng quan về đường Trunk***
* Kết nối trunk (đường trunk) là một kỹ thuật dùng chỉ một kết nối cho phép dữ liệu của các VLAN có thể cùng lưu thông qua đường này, gần như là gộp 2 còn switch vào làm 1. Người ta gọi kết nối này là đường trunk.
* Được sử dụng để tránh lãng phí tài nguyên về dây nối và các cổng.
* Ví dụ 

![](https://user-images.githubusercontent.com/52046920/183376892-556475fa-9d37-4441-a4b1-7264d0f84ea1.png)
* vlan 2 bên switch số 2 muốn kết nối với vlan 2 bên switch số 1 ta cần phải nối switch 1 với switch 2 và cho 2 cổng đó cùng thuộc vlan 2. Nếu muốn 2 máy thuộc vlan 3 ở 2 bên kết nối cũng tương tự lại cần thêm 1 đường dây nữa và 2 cổng thuộc vlan 3. Nếu như cần chia nhiều Vlan điều này cực kỳ gây lãng phí tài nguyên vậy nên Trunk sẽ được sử dụng trong trường hợp này

# ***II.	Cấu hình kết nối Trunk trên Cisco Switch***
* Thiết lập đường trunk để cho phong kế toán và phòng kế toán 2 có thể thông được đến nhau. VLAN ở 2 phòng đã được cấu hình là VLAN2

![](https://user-images.githubusercontent.com/52046920/183378518-f0eba4da-7655-42c4-865f-4acb40c8aa77.png)

* Sử dụng câu lệnh
```cisco
Switch(config)#interface fa0/1
Switch(config-if)#switchport mod trunk
Switch(config-if)#switchport trunk encapsulation dot1q


\\\hoặc
Switch(config)#interface fa0/1
Switch(config-if)#switchport mod trunk
Switch(config-if)#switchport trunk encapsulation isl



\\\dot1q là chuẩn đóng gói chuẩn quốc tế, ISL là chuẩn đóng gói độc quyền của cisco và nên sử dụng dot1q. mặc định các thiết bị của bài lab trên cisco sẽ  chỉ hỗ trợ dot1q nên không cần thiết lập câu lệnh switchport trunk encapsulation dot1q hay câu lệnh switchport trunk encapsulation isl

```
* Một số switch sẽ mặc định chuẩn đóng gói là dot1q vậy nên không cần câu lệnh Switch(config-if)#switchport trunk encapsulation dot1q

* Chỉ cần cấu hình trên 1 switch là được
* Kiểm tra bằng câu lệnh
```cisco
Switch# show interface trunk
```

![](https://user-images.githubusercontent.com/52046920/183378327-520d88f7-8a3f-4efc-9364-8b37f3434529.png)
* Sau khi thiết lập đường trunk xong 2 máy thuộc vlan2 của 2 switch đã có thể ping thông được đến nhau

![](https://user-images.githubusercontent.com/52046920/183378333-5b35ce41-87b5-4ba7-99fe-bc9cbc0f8fc3.png)

* Ngoài ra ta có thể kiểm soát được những VLAN được quyền sử dụng đường trunk bằng câu lệnh
```cisco
Switch(config)#interface fa0/1

///Do mặc định các thiết bị của bài lab trên cisco sẽ  chỉ hỗ trợ dot1q nên không cần thiết lập, không thì ta sẽ phải thêm câu lệnh
SW1(config-if)#switchport trunk encapsulation dot1q

///Các thiết bị trên cisco thì chỉ cần 2 câu lệnh sau

Switch(config-if)#switchport mod trunk
Switch(config-if)#switchport trunk allow vlan 1-2

\\\ nếu muốn mở cho toàn bộ vlan
Switch(config-if)#switchport trunk allow vlan all
```
* Ở đây chỉ cho phép vlan 1-2 được sử dụng đường trunk ngoài 2 vlan này ra thì không vlan nào được sử dụng đường trunk 
* Vậy là nếu ta tạo thêm 2 vlan 3 ở 2 switch thì 2 pc ở 2 vlan này không được sử dụng đường trunk nên chúng không thể ping thông cho nhau được
* Mặc định sẽ mở cho vlan từ 1-1005.
* Các option khác trên đường trunk

![](https://user-images.githubusercontent.com/52046920/183380454-3a0d90cb-5537-4ebf-bb0c-1c8aeef93b13.png)

# ***III.	Giải pháp mở rộng VLAN nếu thiếu Port trên Switch***
* Giả sử 1 mô hình như sau

![](https://user-images.githubusercontent.com/52046920/183389732-6474713a-02b7-4f17-9b48-14982afb2d86.png)
* SW1 đã hết cổng giao tiếp để có thể mở rộng VLAN2 Và VLAN3 vậy ta có thể mở rộng như sau: 
    * Trunk đến mối SW mới để mở rộng thêm vlan lúc này ta khai báo các cổng của SW2 thuộc VLAN nào thì VLAN đó sẽ được mở rộng chỉ việc bớt đi 1 port của SW1

    ![](https://user-images.githubusercontent.com/52046920/183389658-81825359-9655-42e5-b657-33b22c1e1f8f.png)
    * SW2 kết nối với SW1 qua cổng giao tiếp. Trên cổng giao tiếp kết nối từ SW1 đến SW2 ta tạo vlan cho cổng giao tiếp là là vlan mà ta muốn mở rộng thì ngay lập tức cụm mạng mà switch mới liên kết sẽ thuộc vlan muốn mở rộng.

    ![](https://user-images.githubusercontent.com/52046920/183389667-f100764a-131b-499d-b5f1-6ad6b34e8470.png)

# ***IV.	Giao thức VTP đồng bộ hóa thông tin VLAN giữa các Switch***
* VTP (Vlan Trunking Protocol) là giao thức hoạt động ở tầng liên kết dữ liệu trong mô hình OSI. VTP giúp cho việc cấu hình VLAN luôn đồng nhất khi thêm, xóa, sửa thông tin về VLAN trên các switch trong hệ thống mạng. Giao thức này chỉ có thể hoạt động trên cổng trunk
* VTP gửi thông điệp quảng bá qua VTP domain mỗi 5 phút một lần, hoặc khi có sự thay đổi xảy ra trong quá trình cấu hình VLAN. Một thông điệp VTP bao gồm rivision-number, tên VLAN (VLAN name), số hiệu VLAN. Bằng sự cấu hình VTP Server và việc quảng bá thông tin VTP tất cả các switch đều đồng bộ về tên VLAN và số liệu VLAN của tất cả các VLAN. 
* Bất cứ thao tác nào với VLAN đều tăng rivision-number, khi rivision-number nhận vào của switch mà lớn hơn chính rivision-number của switch đó thì đã có VLAN thay đổi và nó sẽ cập nhật lại thông tin của mình và rivision-number. Nếu rivision-number bằng nhau thì không cần cập nhật

![](https://www.totolink.vn/public/uploads/img_article/vtplagivlantrunkingprotocollagihoatdongcuavtp.png)
* VTP hoạt động ở một trong 3 cơ chế sau:
    * Server: Có khả năng lan truyền thông tin Vlan cho switch xung quanh biết. Có thể tạo sửa xóa Vlan
    * Client: Học thông tin Vlan từ switch server và tiếp tục lan truyền thông tin đi xung quanh. Không thể tạo sửa xóa Vlan.
    * Transparent: Không có khả năng học và lan truyền thông tin. Có thể tạo sửa xóa Vlan. Chỉ có một việc duy nhất là chuyển tiếp thông điệp VTP

![](https://www.totolink.vn/public/uploads/img_article/vtplagivlantrunkingprotocollagi3cochehoatdongcuavtp.png)
* Client và server sẽ học được các thông tin Vlan thông qua các server và client khác

![](https://user-images.githubusercontent.com/52046920/183423314-3ab1116f-98cd-4cde-989e-64eb056941ae.png)
* Sử dụng trong 1 hệ thống lớn, có rất nhiều vlan mà nếu cấu hình bằng tay từng thiết bị một sẽ có thể dẫn đến nhầm lẫn và mất rất nhiều thời gian để cấu hình và nếu cấu hình sai thì sẽ càng mất nhiều thời gian hơn nữa cho việc rà soát lại toàn bộ. Thay vào đó sử dụng giao thức VTP chỉ cần cấu hình vlan 1 lần nó sẽ dạy cho các switch xung quanh. ***lưu ý***: các cổng thuộc vlan nào thì vẫn phải tự khai báo
* Cấu hình VTP
* Cấu hình VTP domain
```cisco
Switch (config) # vtp domain <domain_name>
```
Cấu hình VTP mode
```cisco
Switch (config) #vtp [client| transparent| server]
```
Lệnh xem cấu hình VTP
```cisco
Switch # show vtp status
```

* Ví dụ: Cho sơ đồ mạng
![](https://user-images.githubusercontent.com/52046920/183424021-e7c62b7c-38fc-48bb-b806-0ada257ab7b7.png)

* Tại SW1
```cisco
SW1(config)#vtp mode server
SW1(config)#vtp domain T
SW1(config)#vtp password 123

SW1(config)#vlan 2 
SW1(config-vlan)#name KeToan
SW1(config-vlan)#exit 
SW1(config)#vlan 3
SW1(config-vlan)#name KinhDoanh

SW1(config)#int fa0/1

///Do mặc định các thiết bị của bài lab trên cisco sẽ  chỉ hỗ trợ dot1q nên không cần thiết lập, không thì ta sẽ phải thêm câu lệnh
SW1(config-if)#switchport trunk encapsulation dot1q

///Các thiết bị trên cisco thì chỉ cần câu lệnh sau

SW1(config-if)#switchport mode trunk 
```


* Tại SW2
```cisco
SW2(config)#vtp mode client
SW2(config)#vtp domain T
SW2(config)#vtp password 123
```

* Kiểm tra tại SW2 nhận thấy tên cac VLAN đã đồng bộ

![](https://user-images.githubusercontent.com/52046920/183423328-68f014bf-8546-4227-b236-b967b7d17fb3.png)

* Thông tin VTP
```cisco
SW1#show vtp status
```

![](https://user-images.githubusercontent.com/52046920/183423335-808a3ea4-40c2-4245-aced-2f85b4179932.png)

# ***V.	Giao thức DTP tự động thiết lập kết nối Trunk giữa các Switch***
* Là giao thức tự động thiết lập kết nối trunk giữa các switch tùy vào các mode của interface.
* 1 interface có 3 mod:
    * Auto: Thường là mod mặc định trên switch layer 2, phản hồi các DTP nếu nhận được DTP từ Switch chứ không tự gửi
    * Trunk on: Kết nối các switch khác nhau và mang theo lưu lượng của Vlan
    * Desirable: tự động gửi DTP định kỳ
    * Access: dùng để gán cho 1 Vlan duy nhất 
* Kiểm tra mode bằng câu lệnh
```cisco
SW1#show interface trunk
```

![](https://user-images.githubusercontent.com/52046920/183552315-742800b3-7432-4161-99a7-30eede5f797c.png)

![](https://user-images.githubusercontent.com/52046920/183552326-fbe7b325-e754-4166-9a1e-00e3490b7baa.png)

* Có thể thay đổi mode của cổng bằng câu lệnh
```cisco
SW2(config)#int fa0/1
SW2(config-if)#switchport mode dynamic desirable
```

* Mode có thể thay đổi

![](https://user-images.githubusercontent.com/52046920/183552336-d5496b61-1f64-486e-8810-2dc0fde92ab7.png)

![](https://user-images.githubusercontent.com/52046920/183552333-5e8e2390-67a3-4a57-a38f-0be69f1ff2ec.png)

* Các tình huống khi 2 cổng switch thuộc các mode khác nhau

![](https://user-images.githubusercontent.com/52046920/183552323-f7556826-5a80-44a5-bb57-20df9d6c1f51.png)

* Tắt giao thức DTP trên cổng sử dụng câu lệnh
```cisco
SW2(config)#int fa0/3
SW2(config-if)#switchport nonegotiate
```
![](https://user-images.githubusercontent.com/52046920/183552337-1f0ffead-7b43-4b5b-a80c-2e7d3dd4ed30.png)
* Nên tắt giao thức trên các cổng sử dụng mode access vì nó không cần thiết và tốn tài nguyên

# ***VI.	Hiệu chỉnh Native VLAN trên đường Trunk sử dụng kiểu đóng gói dot1q***
* Native VLAN là một VLAN được sử dụng để cấu hình Trunking do một số thiết bị không tương thích với nhau. Khi một cổng của switch được cấu hình trunk, trong phần tag của frame đi qua cổng đó sẽ được thêm một số hiệu VLAN thích hợp. và nếu 1 bản tin không được dán nhãn Vlan nó sẽ mặc định gửi cho native vlan
* Mục đích của vlan native giúp cho các thiết bị không hiểu tag vlan id sẽ vẫn nhận frame
* Native Vlan mặc định là Vlan 1
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/183796307-840e2c4e-2c57-4657-84a4-89a79307e6ab.png)

* Cấu hình native vlan cho vlan 10 ở PC 2
* Tại switch ta thực hiện câu lệnh
```cisco
SW1(config)#int f0/3

///Do mặc định các thiết bị của bài lab trên cisco sẽ  chỉ hỗ trợ dot1q nên không cần thiết lập, không thì ta sẽ phải thêm câu lệnh
SW1(config-if)#switchport trunk encapsulation dot1q
///Các thiết bị trên cisco thì chỉ cần 2 câu lệnh sau

SW1(config-if)#switchport mode trunk
SW1(config-if)#switchport trunk native vlan 10
```

![](https://user-images.githubusercontent.com/52046920/183796302-724ec265-a394-4c47-a1c4-c8c8448d40b3.png)

* Kiểm tra 2 PC2 và PC3 ở Vlan 10 đã thông với nhau

![](https://user-images.githubusercontent.com/52046920/183796563-cb30aad3-7c1f-43ce-b1d8-73ae87f0be07.png)   
* Sau này nếu mở rộng Vlan 10 ở PC 2 thêm thì ta không cần switch có hỗ trợ Vlan chỉ cần nối switch vào cổng f0/3 rồi chia ra các PC mới là được.