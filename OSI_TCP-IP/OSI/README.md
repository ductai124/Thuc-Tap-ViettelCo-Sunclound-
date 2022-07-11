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

# TÌM HIỂU VỀ MÔ HÌNH OSI
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
[1. Mô hình OSI là gì]()

[2. ]()

[3. ]()

***
# ***I.	Mô hình OSI là gì***
* Mô hình kết nối các hệ thống mở OSI là mô hình căn bản về các tiến trình truyền thông, thiết lập các tiêu chuẩn kiến trúc mạng ở mức Quốc tế, là cơ sở chung để các hệ thống khác nhau có thể liên kết và truyền thông được với nhau. Mô hình OSI tổ chức các giao thức truyền thông thành 7 tầng, mỗi một tầng giải quyết một phần hẹp của tiến trình truyền thông, chia tiến trình truyền thông thành nhiều tầng và trong mỗi tầng có thể có nhiều giao thức khác nhau thực hiện các nhu cầu truyền thông cụ thể.
* Mô hình OSI được tạo ra với mục đích là cho phép sự tương giao (interoperability) giữa các hệ máy (platform) đa dạng được cung cấp bởi các nhà sản xuất khác nhau. Mô hình cho phép tất cả các thành phần của mạng hoạt động hòa đồng, bất kể thành phần ấy do ai tạo dựng. Vào những năm cuối thập niên 1980, ISO đã tiến cử việc thực thi mô hình OSI như một tiêu chuẩn mạng.
* Mô hình OSI gồm 7 tầng:
    1. Tầng vật lý (Physical layer)
    2. Tầng liên kết (Datalink) 
    3. Tầng mạng (Network) 
    4. Tầng vận chuyển (Transport)
    5. Tầng phiên (Session)
    6. Tầng trình diễn (Presentation) 
    7. Tầng Ứng dụng (Application)

![Mô hình OSI](https://user-images.githubusercontent.com/52046920/178251580-20cda5a5-abb4-49d8-8d75-7ed5a846bae2.PNG)   

* Đi vào chi tiết các tầng sẽ như sau:
## ***1. Tầng vật lý (Physical layer)***
* Tầng vật lý là tầng thấp nhất trong mô hình dùng để xác định các chức năng, thủ tục về điện, cơ, quang để kích hoạt duy trì và giải phóng các kết nối vật lý giữa các hệ thống mạng. Nói đơn giản thì tầng vật lý định nghĩa tất cả các đặc tả về điện và vật lý cho các thiết bị. Trong đó bao gồm bố trí của các chân cắm, các hiệu điện thế, các đặc tả về cáp 
nối,…

* Các thiết bị tầng vật lý bao gồm Hub, bộ lặp, thiết bị chuyển đối tín hiệu, thiết bị tiếp hợp mạng, thiết bị tiếp hợp kênh máy chủ,…

* Chức năng căn bản của tầng vật lý:

    * Thiết lập hoặc ngắt mạch kết nối điện với một môi trường truyền dẫn phương tiện truyền thông.
    * Tham gia vào quy trình, trong đó các tài nguyên truyền thông được chia sẻ giữa nhiều người dùng.
    * Điều chế hoặc biến đổi giữa dữ liệu số của các thiết bị người dùng và các tín hiệu tương ứng được truyền qua kênh truyền thông.
## ***2. Tầng liên kết (Datalink)***
* Tầng liên kết dữ liệu có chức năng chính là thực hiện thiết lập các liên kết, hủy bỏ và duy trì các liên kết
* Phát hiện và có thể sửa chữa các lỗi trong tầng vật lý nếu có
* Tầng liên kết dữ liệu chính là nơi các thiết bị chuyển mạch hoạt động. Kết nối chỉ đượ cung cấp giữa các nút mạng được nối với nhau trong mạng nội bộ. 
## ***3. Tầng mạng (Network)***
* Tầng mạng cung cấp các chức năng và quy trình cho việc truyền các chuỗi dữ liệu từ  một nguồn tới 1 đích thông qua một hoặc nhiều mạng
* Tầng mạng chọn đường đi cho các gói tin. Ngoài ra chúng còn có chức năng điều kiển tắc nghẽn khi nhiều gói tin cùng lưu chuyển trên 1 đường và xảy ra nghẽn
## ***4. Tầng vận chuyển (Transport)***
* Tầng giao vận có nhiệm vụ chuyển dữ liệu giữa các giữa  các người dùng tại đầu cuối
* Kiểm soát độ tin cậy của một kết nối được cho trước
* Tầng giao vận thực hiện chia nhỏ các gói tin lớn trước khi gửi đi và đánh dấu thứ tự cho các gói tin để chúng được chuyển theo thứ tự. Ngoài ra còn theo dõi các gói tin và truyền lại các gói tin thất bại
* Đây là tâng cuối chịu trách nhiệm về độ an toàn trong truyền dữ liệu
## ***5. Tầng phiên (Session)***
* Có nhiệm vụ kiểm soát các phiên làm việc giữa các máy. Tầng này thiết lập, duy trì, đồng bộ hóa và quản lý các kết nối giữa trình ứng dụng.

## ***6. Tầng trình diễn (Presentation)***
* Tầng trình diễn có nhiệm vụ giải quyết các vấn đề liên quan đến các cú pháp và ngữ nghĩa của các thông tin được truyền đi. Tại máy truyền dữ liệu sẽ dịch dữ liệu được gửi từ tầng ứng dụng qua định dạng chung. Tại máy nhận thì chuyển từ định dang chung sang định dạng của tầng ứng dụng.
## ***7. Tầng Ứng dụng (Application)***
* Cung cấp giao diện sử dụng cho người sử dụng và môi trường truyền tin
# ***II. Các giao thức trong OSI***
* Có 2 loại giao thức sử dụng trong mô hình là:
    * Giao thức hướng liên kết (Connection Oriented)
    * Giao thức không liên kết (Connectionless)
## ***1. Giao thức hướng liên kết***
* Trước khi truyền dữ liệu, các thức thể trong cùng một tầng của hai hệ thống khác nhau cần thiết lập liên kết logic chung.
* Sau đó chúng tiến hành trao đổi với nhau về các tập tham số sử dụng trong quá trình truyền dữ liệu, có thể cắt bớt hoặc gộp dữ liệu để tăng độ tin cậy và an toàn trong quá trình trao đổi
## ***2. Giao thức Không liên kết***
* Chỉ có duy nhất 1 giai đoạn là truyền dữ liệu.
* Dữ liệu được truyền độc lập trên các tuyến khác nhau
# ***III. Phương thức hoạt động của mô hình OSI***
![Cách thức hoạt động](https://user-images.githubusercontent.com/52046920/178251528-e0e7c6a2-30d8-4424-99f9-75b030b86507.PNG)
## ***1. Bên máy gửi***
* Tại tầng 7 (Tầng ứng dụng/Application) người dùng đưa thông tin vào máy tính dưới dạng văn bản, hình ảnh,...
* Tại tầng 6 (Tầng trình diễn/Presentation) tiếp nhận thông tin được chuyển đến từ tầng 7, thông tin sẽ được tiến hành mã hóa và nén dữ liệu. Sau khi được mã hóa và nén, dữ liệu được chuyển đến tầng 5.
* Tại tầng 5 (Tầng phiên/ Session) các dữ liệu sẽ được xử lý sau đó bổ sung thêm các thông tin cần thiết(Có thể hiểu đây là bước xác nhận các thông tin). Sau khi xác nhận xong thông tin được đẩy xuống tầng 4
* Tại tầng 4 (Tầng vận chuyển/Transport) các dữ liệu sẽ được chia thành nhiều phần nhỏ, đồng thời nó cũng được bổ sung thêm các thông tin như phương thức vận chuyển để đảm bảo tính bảo mật sau đó chuyển tới tầng 3.
* Tại tầng 3 (Tầng mạng/Network) các phần dữ liệu vừa được chia nhỏ lại tiếp tục được chia ra thành nhiều gói thông tin khác nhau. Sau đó các gói thông tin sẽ được vận chuyển theo đúng tuyến đường đi đã được định sẵn tới tầng 2.
* Tại tầng 2 (Tầng liên kết/Datalink) các gói thông tin nhỏ từ tầng 3 tiếp tục được cắt nhỏ thành những Frame tại đây, đồng thời được bổ sung thông tin kiểm tra các gói tin chứa dữ liệu này để có thể kiểm tra ở đầu máy nhận khi thông tin tới.
* Tại tầng cuối, tầng 1 (Tầng vật lý/Physical) các Frame khi được chuyển đến đây sẽ được chuyển thành các chuỗi bit nhị phân, sau đó được đưa lên, phát tin hiệu trên các công cụ truyền dẫn (dây cáp quang) để chuyển tới được máy nhận.
## ***1. Bên máy nhận***
* Dữ liệu từ máy gửi đến tiếp xúc đầu tiên với tầng 1 (Tầng vật lý/Physical) của máy nhận. Ở đây, các dữ liệu sẽ được kiểm tra đồng bộ và đưa các chuỗi bit nhị phân vào vùng đệm, sau đó là gửi thông báo cho Tầng 2 “dữ liệu đã được nhận).
* Tại tầng 2 (Tầng liên kết/Datalink) kiểm tra xem có lỗi nào đối với các Frame dữ liệu vừa gửi không. Khi phát hiện Frame bị lỗi thì sẽ hủy bỏ Frame đó. Tiếp đến là quá trình kiểm tra địa chỉ Data Link (địa chỉ MAC Address) có khớp với địa chỉ máy nhận hay không. Kiểm tra đúng, Data Link sẽ gỡ bỏ Header để chuyển dữ liệu đến tầng 3.
* Tại tầng 3 (Tầng mạng/Network) tiếp nhận và kiểm tra địa chỉ gói tin dữ liệu có phải là địa chỉ máy nhận không (địa chỉ ở tầng này là IP). Nếu đúng các gói tin dữ liệu tiếp tục được gỡ bở Header của tầng Network rồi được chuyển tới tầng 4.
* Tại tầng 4 (Tầng vận chuyển/Transport) sẽ được hỗ trợ phục hồi và xử lý lỗi bằng cách gửi các gói tin ACK, NAK là những gói tin dùng để phản hồi xem các gói chứa dữ liệu đã được gửi đến máy nhận hay chưa. Khi các gói tin đã được phục hồi xong sẽ được chuyển tiếp lên tầng 5
* Tại tầng 5 (Tầng phiên/ session) kiểm tra chắc chắn các gói tin toàn vẹn từ máy gửi tới máy nhận. tiếp tục gỡ bỏ header của tầng 5 và chuyển thông tin đi.
* Tại tầng 6 (Tầng trình diễn/Presentation) tiếp nhận, tiến hành chuyển đổi định dạng dữ liệu để xử lý gói tin đưa đến tầng 7
* Tại Tầng 7 (Tầng ứng dụng/Application) nhận dữ liệu, gỡ bỏ nốt header, kết thúc quá trhf nhận dữ liệu đến.
