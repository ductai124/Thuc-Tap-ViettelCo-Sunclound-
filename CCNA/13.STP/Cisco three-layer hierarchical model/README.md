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

# TÌM HIỂU VỀ MÔ HÌNH MẠNG 3 PHÂN LỚP CỦA CISCO
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
# ***I.	Tổng quan***
* Một hệ thống mạng được thiết kế bài bản sẽ dẫn đến việc quản lý, mở rộng, vận hành sẽ dễ dàng và trơn tru hơn. Và để đạt được điều đó Cisco đã đưa là các thiết kế mạng theo dạng phân cấp để nhằm mục đích đó.
* Hệ thống mạng 3 phân lớp của Cisco là 1 mô hình được áp dụng trong các hệ thống vừa và lớn có đòi hỏi tốc độ truyền tải kèm theo bảo mật thông tin cao. Hệ thống này đảm bảo sự ổn định cũng như công suất cao cho mạng.
* Mô hình này gồm 3 phân lớp:
    * Core Layer : Là lớp mạng trung tâm hay lớp lõi
    * Distribution : Là lớp phân tán hay có thể gọi là phân phối
    * Access Layer : Là lớp truy cập 
* Nên sử dụng thiết kế phân cấp do tốc độ truyền tin nhanh, hiệu năng tốt, tính mở rộng cao

![](https://user-images.githubusercontent.com/52046920/184797371-08916dca-eb3e-47f5-95ac-4e5aff8e9cfa.png)
* Đi vào chi tiết các lớp 

# ***II.	Core Layer***
* Là lớp lõi các thiết bị ở đây sẽ kết nối từng lớp phân tán lại với nhau
* Ở lớp này tốc độ là vấn đề quan trọng nhất
* Các thiết bị sử dụng ở lớp này là các router
* Do nếu lớp lõi xảy ra vấn đề toàn bộ mạng LAN đều ảnh hưởng do vậy lớp này là lớp cực kỳ quan trọng và sự dự phòng các thiết bị cho lớp này là vô cùng cần thiết. Vậy nên nên sử dụng thiết kế Partial Mesh hoặc full Mesh cho lớp lõi
* Do lớp lõi vận chuyển một số lượng lớn dữ liệu nên độ trễ ở đây cần phải thiết lập sao cho cực kỳ nhỏ
# ***III.	Distribution Layer***
* Lớp phân tán là tầng liên kết giữa lớp lõi và lớp truy cập, Nó giúp giảm tải cho lớp Core trong quá trình truyền tin trong mạng
* Lớp này sử dụng các router hoặc switch layer 3 để liên kết các đoạn mạng LAN lại với nhau.
* Lớp này thực hiện các thao tác như định tuyến và lọc gói tin.
* Do lớp này nếu xảy ra lỗi sẽ gây ảnh hưởng cho 1 phân đoạn mạng LAN ở lớp Access vậy nên lớp này cũng nên được thiết kế dự phòng bằng cách mỗi thiết bị ở lớp truy cập sẽ được nối đến với 2 thiết bị ở lớp phân tán. Khi 1 thiết bị xảy ra sự cố thì vẫn còn 1 thiết bị dự phòng kết nối với phân đoạn mạng lan đó ở lớp access. 
# ***IV.	Access Layer***
* Là nơi các nút trạm kết nối tới các thiết bị tập trung như hub hoặc switches.
* Được thiết kế cung cấp các cổng kết nối đến tùng máy trạm trên cùng mạng giúp người dùng kết nối với các tài nguên trên mạng hoặc giao tiếp với lớp mạng được phân bố
* VLANS có thể đượ sử dụng để tạo miên quảng bá phân tách các miên.
* Với thiết kế phân lớp thì lỗi ở lớp truy cập chỉ ảnh hưởng đến các thiết bị kết nối trực tiếp với nó mà thôi. Vậy nên để tiết kiệm chi phí thì không cần thiết phải dự phòng tại lớp này
* Lớp này đặc trung bởi các phân đoạn mạng LAN. 
* Đặc tính:
    * Chuyển mạc lớp 2
    * STP(Spanning tree)
    * Hỗ trợ VLAN
    
    ....
# ***IV.	Các lựa chọn thiết kế***
* Có 4 thiết kế cơ bản;
    * Point to point
    * Hub and Spoke
    * Partial Mesh
    * Full Mesh
## ***1.	Point to Point***
* Là thiết kế điểm nối với điểm được sử dụng để nối 2 site với nhau.

![](https://user-images.githubusercontent.com/52046920/184797372-3528be88-5d41-4835-9d17-23ebf399c467.png)
## ***2.	Hub and Spoke***
* Là mô hình 1 nút trung gian(Hub) sẽ kết nối với các nút xung quanh(Spoke) và từ nút trung gian đi lên nút tổng. Dữ liệu từ các Spoke sẽ được tập hợp tại Hub và gửi lên nút tổng và ngược lại dữ liệu từ nút tổng đi đến Hub và sẽ chia ra các Spoke

![](https://user-images.githubusercontent.com/52046920/184797374-6060aebd-da4e-42f8-8b75-8cc18e031cca.png)
* Mô hình này không tồn tại dự phòng
    * Nếu có đường truyền lỗi, sẽ không có cách phục hồi 
    * Nếu đường truyền đến các nút thu thập hoặc đường truyền trung tâm lỗi các gói tin sẽ không có khả năng lan truyền được lên trên trong kiểu thiết kế này
## ***3. Mô hình full Mesh***
* Là 1 mô hình mà tất cả thiết bị trong mô hình mạng này đều sẽ được kết nối với nhau. 
* Ưu điểm:
    * Do tất cả các thiết bị đều được kết nối với nhau nên tính dự phòng là vô cùng cao
* Nhược điểm
    * Chi phi cực cao nếu mở rộng mô hình ra

![](https://bkhost.vn/wp-content/uploads/2022/06/image10-e1654486282846.jpg)
## ***4. Mô hình partial Mesh***
* Do chi phí để thực hiện mô hình Mesh quá cao nên mô hình Partial Mesh được đưa thêm
* Sơ đồ này không có tất cả những đường kết nối tới những thiết bị còn lại tuy nhiên những thiết bị quan trọng sẽ được kết nối với tất cả các thiết bị còn lại.
* Giảm thiểu được chi phí so với full Mesh, vẫn có tính dự phòng đối với những thiết bị quan trọng tuy nhiên tính dự phòng không cao bằng

![](https://ofbit.in/wp-content/uploads/2022/05/Partial-Mesh-Topology-OFBIT-768x768.jpg)

* Từ đó tùy vào nhu cầu ta sẽ sử dụng các mô hình thích hợp.