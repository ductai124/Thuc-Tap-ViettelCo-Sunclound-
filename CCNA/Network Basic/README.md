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

# TÌM HIỂU VỀ NETWORK BASIC
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
# ***I.	Mạng máy tính là gì***
* Mạng máy tính là một hệ thống tập hợp bởi nhiều máy tính, laptop và các thiết bị được kết nối/liên kết với nhau bởi đường truyền vật lý theo một kiến trúc (Network Architecture) nào đó nhằm trao đổi dữ liệu và chia sẻ tài nguyên cho nhau.
* Để kết nối vào hệ thống mạng thì tối thiểu phải có các thành phần như:
    * Ít nhất 2 PC
    * Switch
    * Dây cáp
    * Router
* Trên PC này sẽ có card mạng (Network interface card - NIC), trên card mạng này ta sẽ sử dụng một sợi dây cáp, một đầu cắm vào card mạng đầu còn lại sẽ cắm vào switch, từ switch ta lại dùng một sợi dây cáp mạng để nối từ switch tới 1 con router, rồi từ router ta sẽ có những đường để đi ra ngoài mạng và những máy PC có thể truy cập internet bình thường.


# ***II. Các đặc điểm của hệ thống mạng***

## ***1. Tốc độ(Speed)***
* Phân chia thành 2 nhóm:
    * Tốc độ bên trong: Tốc độ truyền thông của các thiết bị trong 1 môi trường mạng cục bộ. Bị ảnh hưởng bởi kết nối, cap, tốc độ truy cập mạng của card mạng, các chuẩn kết nối không dây
    * Tốc độ bên ngoài: Tốc độ mạng nhanh hay chậm do gói cước đăng ký trên nhà mạng.
## ***2. chi phí(Cost)***
* Gồm 3 nhóm chi phí:
    * chi phí triển khai ban đầu: Để triển khai hết hệ thống mạng cần bao nhiêu tiền từ PC, laptop, server, Switch,router, đi dây như nào. Là khoản chi phí đầu tư nhiều nhất. Nếu đầu tư bài bản thì việc vận hành sẽ dễ dàng và giảm được các chi phí phát sinh như bảo trì bảo dưỡng và nâng cấp
    * Chi phí duy trì hạ tầng mạng
    * Chi phí bảo trì bảo dưỡng nâng cấp hệ thống mạng
## ***3. tính bảo mật(Security)***
* Sự bảo mật, cách thức bảo vệ một mạng từ cả bên trong lẫn bên ngoài.
* Có thể triển khai trên nhiều thiết bị, nhiều lớp
* Đối với máy tính cài đặt các phần mềm bảo mật uy tín và cập nhật hệ điều hành và các phần mềm bảo mật 1 cách thường xuyên
* Các Switch có tính năng bảo mật.
* Sử dụng firewall chuyên dụng

## ***4. Độ sẵn sàng(Availability)***
* Khi thiết kế một hệ thống mạng, đảm bảo mạng của mình được kết nối 24/24 không bị gián đoạn.
* Dự phòng thuê nhiều nhà cung cấp để nâng cao tính sẵn sàng
## ***5. Khả năng mở rộng(Scalability)***
* Khi thiết kế 1 hệ thống mạng, không nên thiết kế chỉ phù hợp cho hiện tại mà cần phải phù hợp trong vài năm tới. Chọn các thiết bị có khả nâng nâng cấp, mở rộng hệ thống.
## ***6. Độ tin cậy(Reliability)***
* Khi thiết kế hệ thống mạng, phải đảm bảo những user có thể truy cập được hệ thống mạng, họ phải gửI tài liệu đi được và đầu bên kia phải nhận được dữ liệu 1 cách hoàn chỉnh mà không mất gì cả.
## ***7. Mô hình(Topology)***
* Phải có một sơ đồ mạng khi xây dựng một hệ thống mạng để lưu trữ tất cả các thiết bị bên trong mạng của mình để nếu xảy ra sự cố thì có thể dễ dàng khoanh vùng xem nơi phát sinh lỗi là ở đâu.
# ***III. Các loại sơ đồ mạng***
## ***1. Mô hình bus***
* Các thiết bị kết nối với nhau qua 1 trục dây gọi là trục bus
* Một thiết bị muốn gửi dữ liệu thì nó sẽ gửi dữ liệu ra môi trường truyền và mọi thiết bị trong mô hình đều nhận được dữ liệu. Nên nó không có bảo mật nên hiện không còn được sử dụng phổ biến nữa
## ***2. Mô hình Ring***
* Các thiết bị kết nối với nhau thành 1 vòng tròn khép kín.
* Một thiết bị muốn gửi dữ liệu thì dữ liệu sẽ đi qua các thiết bị trung gian theo dạng vòng để đến thiết bị nhận
* Ưu điểm của mạng dạng vòng: có thể nới rộng hệ thống mạng ra xa. Số lượng dây dẫn cần thiết để sử dụng cũng ít hơn so với hai mô hình Star và Bus. 
* Nhược điểm: tồn tại 1 khuyết điểm lớn là đường dây khép kín. Một khi tín hiệu bị ngắt tại một điểm nào đó, toàn bộ hệ thống cũng sẽ ngừng hoạt động.
* Do đó cấu trúc Dual ring được phát triển để hạn chế nhược điểm của Ring
* Ở Dual Ring các dữ liệu chạy hai chiều song song ngược chiều với nhau bằng cách thêm một cấu trúc liên kết mạng tạo ra cấu trúc liên kết vòng kép. Vậy nên khi 1 vòng gặp sự cố thì sẽ có vòng còn lại dự phòng
## ***3. Mô hình Star***
* Các thiết bị đều được kết nối với 1 thiết bị trung gian.
* Khi 1 thiết bị muốn gửi dữ liệu thì nó sẽ gửi qua thiết bị trung gian rồi đến thiết bị đích.
* Ưu điểm:
    * Có khả năng mở rộng dễ dàng mà không ảnh hưởng đến các thiết bị khác.
    * Khi 1 thiết bị không phải thiết bị trung tâm xảy ra vấn đề thì không ảnh hưởng đến các thiết bị còn lại trong mạng
    * Được sử dụng phổ biến.
* Nhược điểm:
    * Nhược điểm lớn nhất của mô hình này là thiết bị trung tâm mà xảy ra lỗi thì toàn bộ mô hình sẽ không thể hoạt động
    * Tốn kém chi phí cho băng thông và hiệu suất mạng.
* Để giải quyết được phần nào nhược điểm của mô hình này mô hình Extended Star được phát triển.
* Extended Star là sự kết hợp giữa các mạng Star với nhau với nhiều thiết bị tập trung hơn. Ưu điểm của mạng hình này là có thể gia tăng khoảng cách hay độ lớn của mạng hình Star. Khi các thiết bị tập trung nhỏ xảy ra sự cố thì phần còn lại của mô hình không bị ảnh hưởng. Tuy nhiên thiết bị trung tâm lớn xảy ra sự cố thì mô hình vẫn sẽ không hoạt động


## ***4. Mô hình full Mesh***
* Là 1 mô hình mà tất cả thiết bị trong mô hình mạng này đều sẽ được kết nối với nhau. 
* Ưu điểm:
    * Do tất cả các thiết bị đều được kết nối với nhau nên tính dự phòng là vô cùng cao
* Nhược điểm
    * Chi phi cực cao nếu mở rộng mô hình ra
## ***5. Mô hình partial Mesh***
* Do chi phí để thực hiện mô hình Mesh quá cao nên mô hình Partial Mesh được đưa thêm
* Sơ đồ này không có tất cả những đường kết nối tới những thiết bị còn lại tuy nhiên những thiết bị quan trọng sẽ được kết nối với tất cả các thiết bị còn lại.
* Giảm thiểu được chi phí so với full Mesh, vẫn có tính dự phòng đối với những thiết bị quan trọng tuy nhiên tính dự phòng không cao bằng