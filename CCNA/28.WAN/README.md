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

# TÌM HIỂU VỀ CÔNG NGHỆ WAN
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. WAN là gì]()
# [II. Hoạt động giao tiếp của WAN]()
# [III. Các loại hình kết nối của WAN]()
## &ensp; [1.Dedicated Connection(Kết nối dành riêng)]()

## &ensp; [2. Circuilt Switched Network(Mạng chuyển mạch)]()

## &ensp; [3. Packet switched(Mạng chuyển mạch gói)]()

# [IV. Các dịch vụ của WAN]()
## &ensp; [1. PSTN]()

## &ensp; [2. Leased Line]()

## &ensp; [3. X25]()
## &ensp; [4. Frame Replay]()

## &ensp; [5. ISDN]()
## &ensp; [6. ATM]()

***
# ***I.	WAN là gì***
* WAN là Wide Area Network(Mạng diện rộng). Thường được sử dụng để kết nối các LAN cách xa nhau ví dụ như side Hà Nội muốn kết nối với side HCM thì sẽ sử dụng công nghệ WAN. Phạm vi của nó là cực kỳ rộng có thể là toàn thế giới, mạng WAN lớn nhất chính là Internet toàn cầu hiện nay. 
* WAN là công nghệ không thể thiếu của doanh nghiệp ngày nay và các công ty thường có thể sử dụng WAN để thực hiện các công việc như:
    * Video call
    * Share tài nguyên giữa nhân viên và khách hàng
    * Truy cập kho dữ liệu và sao lưu dữ liệu từ xa
    * Kết nối các ứng dụng chạy trên cloud
    * Chạy và lưu trữ các ứng dụng nội bộ
* WAN giúp cho các tổ chức, doanh nghiệp cập nhật thông tin 1 cách an toàn, nhanh chóng và đáng tin cậy. Nó đóng vai trò rất quan trọng đối với năng suất và tính liên tục của doanh nghiệp
* Các giao thức WAN:
    * ***Chuyển tiếp khung***: gói dữ liệu dạng khung và truyền nó qua 1 đường dây riêng đến 1 nút chuyền tiếp khung. Hoạt động trên lớp 1 và 2 giúp việc truyền tin từ LAN này qua LAN khác qua nheiuef Switch và Router dẽ dàng hơn
    * ***Chế độ truyền không đồng bộ(ATM)***: định dạng dữ liệu thành các ô dữ liệu 53 byte. Các thiết bị mạng ATM sử dụng phương pháp ghép kênh phân chia theo thời gian để chuyển đổi tín hiệu kỹ thuật số thành acsc ô cố định, truyền nó đi và tập hợp tại đích. 
    * ***Gói tin qua SONET/SDH***: là một giao thức truyền thông xác định cách các liên kết point-point giao tiếp khi sử dụng cab quang
    * ***TCP/IP***: xác định giao tiếp đầu cuối bằng cách chỉ định cách dữ liệu được gỡ goins, gửi, truyền , định tuyến và nhận.
* Đặc điểm:
    * Kết nối các LAN với nhau. 
    * 1 mạng WAN có thể có nhiều công nghệ mạng khác nhau để giao tiếp giữa các LAN.
    * Tốc độ truyền thông chậm
    * Dung lượng cao
    * Là 1 mạng cực kỳ lớn nên việc thiết lập và quản lý khá là phức tạp
* Một mạng WAN điển hình như sau

![](https://user-images.githubusercontent.com/52046920/190944153-32858089-8ba7-46c3-b50c-290040d85871.png)
# ***II.	Hoạt động giao tiếp của WAN***
* Doanh nghiệp sẽ có nhiều tài nguyên chạy ở trong nhiều các trung tâm dữ liệu khác nhau ở nhiều vị trí khác nhau. Để kết nối được tài nguyên, doanh nghiệp sử dụng nhiều kết nối mạng và dịch vụ Internet. Các công ty thuê cơ sở hạ tầng mạng của các nhà cung cấp trên nhiều khu vực địa lý khác nhau để truyền dẫn dữ liệu
* Một thông điệp được khởi tạo từ khách và được gửi đi bởi 1 thiết bị DTE tới nhà cung cập dịch vụ WAN. Các thiết bị DCE của nhà cung cấp sẽ đẩy gói tin tới WAN, sau đó đi qua các thiết bị chuyển mạch để tới đích. Các thiết bị tương tự ở phía đầu nhận.
* Ta có các định nghĩa cần biết:
    * ***DTE - Data Terminal Equipment*** là các thiết bị đầu cuối dữ liệu. Là các thiết bị có chức năng gửi và nhận dữ liệu. DTE được đặt tại vị trí của người thuê, chính là điểm kết nối giữa LAN của người thuê và WAN của nhà cung cấp dịch vụ. DTE thường là Router, nó có thể là máy tính hoặc bộ dồn kênh(multiplexer). Các DTE ở đầu này sẽ thực hiện kết nối với DTE ở đầu kia
    * ***Damarcationg Point(Điểm ranh giới)***: Điểm kết nối giữa đường dây kết nối của công ty điện thoại với đường dây người thuê. Điểm ranh giới còn được gọi là interface mạng hay điểm hiện diện(Point of Presence).
    * Local Loop(Cab nối chặng cuối): Cab nối từ điểm ranh đến văn phòng trung tâm của công ty cung cấp dịch vụ.
    * ***Văn phòng trung tâm(Central Office)***: Trạm tổng đài gần nhất, là điểm cung cấp dịch vụ mạng WAN gần nhất với người thuê bao. Cung cấp điểm vào cho các cuộc gọi đi vào cloud WAN và các điểm ra cho các cuộc gọi từ cloud WAN tới người sử dụng. Ngoài ra nó còn đóng vai trò như 1 điểm chuyển mạng để chuyển các gói dữ liệu tới các văn phòng trung tâm khác. Nó cũng cung cấp dòng điện 1 chiều ổn định cho hệ thống cab nối đích để thiết lập mạch điện.
    * ***DCE - Data Circuit-terminating Equipment(Thiết bị đóng mạch dữ liệu)***: Thiết bị truyền thông với cả DTE và cloud WAN. Thường là 1 Router nhà cung cấp dịch vụ cung cấp dùng để chuyển tiếp giữa khách hàng và cloud WAN
    * ***Cloud WAN***: là tập hợp của hạ tầng truyền dẫn của công ty cung cấp dịch vụ. Gọi là cloud vì nó có cấu trúc vật lý thay đổi thường xuyên
    * ***PSE-Packet switching exchange(Tổng đài chuyển mạch gói)***: là các điểm trung gian trong WAN cloud
# ***III.	Các loại hình kết nối của WAN***
* Cóc các loại kết nối sau:
## ***1.Dedicated Connection(Kết nối dành riêng)***
* Kết nối trực tiếp thiết bị này đến thiết bị khác. Kết nối này có tính ổn định và nhanh tuy nhiên chi phí cao. Do kết nối trực tiếp nên nếu tăng các vị trí kết nối số đường dây sẽ tăng theo ví dụ muốn kết nối 2 vị trí chỉ cần 2 đường dây tuy nheine 4 vị trí thì cần 6 đường dây. 
* Các đặc trưng
    * Luôn có sẵn
    * Sử dụng đường dây người dùng thuê của nhà cung cấp WAN
    * Đắt hơn các giải pháp WAN khác
    * Sử dụng kết nối riêng
* Nên sử dụng khi
    * Có lưu lượng cao dữ liệu luân chuyển trong LAN
    * Cần kết nối thường xuyền
    * có ít điểm cần kết nối
## ***2. Circuilt Switched Network(Mạng chuyển mạch)***
* Cho phép sử dụng những đường dây chung. Làm việc 2 chiều, cho phép thiết lập các kết nối quay số vào và quay số ra(dial-in và dial-out)
* Khi sử dụng mạng chuyển mạch:
    * Máy gửi dữ liệu quay số vào đường dây và kết nối được thiết lập
    * Máy nhận dữ liệu gửi xác nhận, khóa đường dây
    * Máy gửi dữ liệu truyền qua kết nối được thiết lập
    * Hoàn tất, giải phóng kết nối cho người khác sử dụng.
* Mạng chuyển mạch sử dụng các mạch ảo chuyền mạch (SVC - Switched virtual circuit). Một đường truyền dữ liệu giành riêng được thiết lập khi bắt đầu quá trình truyền thông nhờ một loạt các bộ chuyển mạch điện tử.
    
## ***3. Packet switched(Mạng chuyển mạch gói)***
* Đường đi của thông điệp được thiết lập cơ động khi dữ liệu chuyển qua. Có kết nối thường xuyên
* Đặc trưng:
    * Thông điệp chỉ nhỏ thành các gói
    * Các gói chuyển độc lập qua mạng
    * Sắp xếp lại thứ tự các gói tại đích
    * Thiết bị nhận, gửi kết nối thường trực
* Mạng chuyển mạch gói sử dụng các mạch ảo thường trực (PVC- permanent virtual circuit)

# ***IV.	Các dịch vụ của WAN***
# ***1. PSTN***
* Là mạng điện thoại chuyển mạch công cộng. Có các đặc trưng sau
    * Là mạng chuyển mạch, phạm vi toàn cầu
    * Tốc độ giới hạn ở 56 Kbit/s

# ***2. Leased Line***
* Leased Line là đường thuê riêng. Là đường độc lập và có tốc độ cao hơn so với PSTN tuy nhiên chi phí cao
* Đặc trưng:
    * Cung cấp kết nối thường xuyên, chất lượng ổn định
    * Có thể nâng cấp nếu bỏ thêm chi phí
    * Chi phí cao
# ***3. X25***
* Sử dụng kỹ thuật chuyển mạch gói qua mạng điện thoại.
* Giao thức X25 là 1 bộ quy tắc xác định cách thực thiết lập và duy trì kết nối giữa csac DTE và DCE trong 1 mạng PDN(Public Data Network). Nó quy định các thiết bị DTE/DCE và PSE sẽ truyền dữ liệu như thế nào. 
* Đặc trưng:
    * Cần trả phí khi sử dụng X25
    * Khi sử dụng có thể tạo kết nối tới PDN qua 1 đường dây dành riêng
    * Tốc độ 64Kbit/s
    * Kích thước Frame không cố định
    * Có cơ chế kiểm tra và sửa lỗi mạnh nên có thể ổn định trên cơ đường dây điện thoại chất lượng thấp
    * Được sử dụng phổ biến do nhiều nơi chất lượng đường dây chưa được tốt
# ***4. Frame Replay***
* Khi gửi dữ liệu Frame Replay sẽ định tuyến nó tới node gần nhất với nơi nhận và chuyển dữ liệu xuống đường dây người nhận
* Đặc trưng:
    * Nhiều điểm tương tự X25 khi triển khai
    * Có kiểm tra lỗi nhưng không khắc phục lỗi
    * Tốc độ 1.54Mbit/s
    * Cho phép nhiều kích thước gói tin khác nhau
    * Triển khai được qua nhiều loại đường kết nối khác nhau(56k, T1, T3)
# ***5. ISDN***
* ISDN - Intergrated Services Digital Network cung cấp khả năng truy cập WAN cho các hộ gia đình và doanh nghiệp sử dụng cab đồng điện thoại. 
* Đặc trưng:    
    * Cho phép phát quảng bá nhiều kiểu dữ liệu
    * Tốc độ truyền dữ liệu và tốc độ kết nối cao hơn so với kết nối quay số
# ***6. ATM***
* ATM - Asynchronous Transfer Mode là Chế độ truyền không đồng bộ. Đây là hệ thống chuyển mạch gói tiên tiến, có thể truyền đồng thời dữ liệu, âm thanh và hình ảnh số hoá trên cả mạng LAN và mạng WAN.
* Là phương pháp kết nối WAN nhanh nhất hiện nay
* Đặc điểm:
    * Sử dụng gói dữ liệu (cell) nhỏ. Kích thước cố định 53 byte
    * Tốc độ truyền cao 155Mbit/s-622Mbit/s. Lý thuyết có thể lên đến 1.2Gbit/s
    * Chất lượng cao, đọ nhiễu thấp -> Không cần đến kiểm tra lỗi
    * Sử dụng được với các phương tiện truyền dẫn khác nhau
    * Có thể truyền đồng thời nhiều loại dữ liệu.