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

# TÌM HIỂU VỀ TRANSPORT LAYER
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
# ***I.	TRANSPORT LAYER là gì***
* Transport Layer - Tầng giao vận, là tầng thứ 4 trong mô hình osi. 
* Tầng vận chuyển kiểm soát hoạt động truyền dữ liệu giữa 2 máy. Nói cách khác là quản lý và thực hiện các tác vụ truyền dữ liệu từ đầu cuối đến đầu cuối đảm bảo hoạt động này diễn ra hiệu quả nhất.
* Các giao thức tiêu biểu tầng Transport sử dụng :
    * TCP(Transmission Control Protocol)
    * UDP(User Datagram Protocol)
# ***II.	Chức năng***
* Tầng vận chuyển Thực hiện 5 chức năng chủ đạo sau
    * Ghép phiên kết nối
    * Phân mảnh dữ liệu
    * Phương thức truyền
    * Đảm bảo truyền thông tin cậy
    * Điều khiển luồng

## ***1.	Ghép phiên kết nối(Session multiplexing)***
* Tổ chức ghép nối các phiên làm việc giữa 2 máy tính vào 1 đường truyền duy nhất
## ***2.	phân mảnh dữ liệu(Segmenttation)***
* Quá trình chia nhỏ dữ liệu từ tầng trên đưa xuống thành các Segment rồi chuyển đi
## ***3.	Phương thức truyền***
* Lớp Transport cung cấp 2 cơ chế truyền dữ liệu: Connection oriented và Connectionless.
* Connection oriented (Truyền theo hướng kết nối) là một quá trình gồm 3 giai đoạn: 
    * Thiết lập kết nối
    * Truyền dữ liệu
    * Kết thúc / Ngắt kết nối
* Connection oriented được sử dụng ở giao thức TCP.
* Connectionless (Truyền không kết nối): khi máy có gói tin thì nó lập tức đẩy ngay gói tin vào đường truyền mà nó không cần thiết lập kết nối từ trước. Connectionless được sử dụng ở giao thức UDP.

## ***4.	Truyền thông tin cậy(Reliability)***
* Khi máy nguồn gửi cho máy đích một gói tin thì phải chắc chắn rằng máy đích sẽ nhận được gói tin này. Máy nhận khi nhận được gói tin thì phải gửi lại 1 gói tin thông báo đã nhận được gói tin từ phía máy gửi. Nếu máy nhận không thông báo lại thì máy gửi sẽ gửi gói tin liên tục cho đến khi máy nhận gửi thông báo đã nhận được.
* Tùy theo giao thức được sử dụng thì truyền thông tin cậy sẽ được áp dụng. Áp dụng với TCP và không áp dụng với UDP
## ***5.	Điều khiển luồng(Flow control)***
* 	Khi máy gửi gửi quá nhiều dữ liệu cho máy nhận, nếu máy nhận xử lý không kịp thì gói tin có thể sẽ bị hủy bỏ hay mất gói dữ liệu. Lúc này máy nhận sẽ gửi tín hiệu yêu cầu máy gửi chuyển dữ liệu chậm lại. 
* Cơ chế này không phải giao thức nào cũng có. không phải lúc nào cơ chế này cũng được thi hành mà chỉ khi nào có yêu cầu thì mới có. Nó tồn tại trên TCP, UDP không sử dụng
# ***II.	Giao thức***
## ***1.	Giao thức TCP***
* TCP (Tranmission Control Protocol)Là một giao thức truyền tải hướng kết nối Connection oriented là một quá trình gồm 3 giai đoạn: 
    * Thiết lập kết nối
    * Truyền dữ liệu
    * Kết thúc / Ngắt kết nối
* Cung cấp cơ chế báo nhận(Acknowledgement)
* Cung cấp cơ chế đánh số thứ tự gói tin cho các đơn vị dữ liệu được truyền sử dụng để ráp lại các gói tin ở điểm nhận và loại bỏ gói tin trùng nhau
* Cơ chế điều khiển luồng tránh nghẽn
* Hỗ trợ cơ chế truyền và nhận dữ liệu cùng lúc
* Phục hồi dữ liệu bị mất trên đường truyền nếu không thấy xác nhận gửi sẽ gửi lại.

## ***a. Cấu trúc gói tin TCP***
* Cấu trúc gói tin

![](https://images.viblo.asia/ca199b5e-2deb-42b0-ac36-33dbf30f3e20.png)

* Source port(16 bit): Cổng của máy gửi
* Destination port(16 bit): Cổng máy nhận
* Sequence number(32 bit): Trường này có 2 nhiệm vụ:
    * Cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tin gửi có số thứ tự + 1. 
    * Nếu không có cờ thì đây là số thứ tự của byte đầu tiên
* Acknowledgement number(32 bit): dùng để báo đã nhận được gói tin nào và mong nhận được byte mang số thứ tự nào tiếp theo
* HL - Header Length (4 bits): cho biết chiều dài tính theo từ của phần tiêu đề
* Reserved (4 bit): là trường để dùng cho tương lai
* control (9 bit): thực hiện các chức năng điều khiển như thiết lập, kết thúc một session, kiểm soát nghẽn,… Mỗi bit này còn được gọi là một cờ (flag).
* Window Size (16 bits): là số lượng dữ liệu tối đa bên nhận có thể nhận.
* Checksum (16 bits): trường này chứa mã kiểm tra lỗi theo phương pháp (CRC)
* Urgent Pointer (16 bits): sử dụng trong trường hợp cần ưu tiên dữ liệu, tuy nhiên thì trường này thường để trống vì URG không được sử dụng.
* Options (tối đa 32 bits): chứa các thông tin tùy chọn.
* Data: dữ liệu của lớp trên

## ***b.	Cách thức hoạt động tổng quan***
* Giả sử có 2 máy A và B. Mấy A muống truyền dữ liệu cho B qua kết nối TCP.
* Ta phải trải qua 3 giai đoạn: 
    * Thiết lập kết nối
    * Truyền dữ liệu
    * Kết thúc / Ngắt kết nối

* ***Giai đoạn 1 thiết lập kết nối*** :Trước khi truyền A phải thực hiện kết nối TCP với B qua quá trình bắt tay 3 bước. Đây là quá trình thỏa thuận những tham số mà 2 thiết bị hỗ trợ như kích thước tối đa của segment, tốc độ truyền dữ liệu phù hợp
* Cơ chế bắt tay 3 bước như sau:
    * Máy A gửi tín hiệu SYN thăm dò B sẵn sàng cho quá trình truyền nhận chưa
    * Máy B nếu đã đủ tài nguyên phục vụ cho quá trình truyền nhận thì nó sẽ gửi lại 1 gói tin ACK để thông báo đã sẵn sang quá trình truyền nhận đồng thời gửi kèm thêm 1 tín hiệu SYN để hỏi xem máy A đã sẵn sàng cho quá trình truyền nhận chưa.
    * Máy A nếu đã đủ tài nguyên phục vụ cho quá trình truyền thông thì nó sẽ gửi lại một gói tin ACK chấp nhận quá trình truyền thông

![](https://user-images.githubusercontent.com/52046920/181156568-4ee4c76b-07db-4796-8f45-f0b4248189a3.png)
* ***Giai đoạn 2 truyền dữ liệu*** : Trước khi truyền dữ liệu máy truyền sẽ tiến hành phân mảnh dữ liệu thành nhiều các segment có kích thước tối đa là 1480 byte và đánh số thứ tự cho các segment
    * Giả sử máy A gửi đi 4 segment nó sẽ gửi đi từng segment 1 theo số thứ tự. Khi B nhận được 1 segment thì nó sẽ gửi lại 1 gói tin ACK để xác nhận đã nhận được segment đó sau khi A nhận được gói tin ACK thì A mới gửi tiếp segment tiếp theo.
    * Trong trường hợp bị mất gói tin B sẽ không gửi lại gói tin ACK và sau 1 khoảng thời gian A không nhận được gói tin ACK xác nhận segment vừa được gửi đã được nhận thì A sẽ gửi segment đó lại cho B đến khi nào B gửi lại gói tin ACK hồi đáp đã nhận được segment đó thì thôi
    * Nhờ có chế truyền dữ liệu như vậy nên gói tin sẽ không bị mất dữ liệu trong quá trình truyền

![](https://user-images.githubusercontent.com/52046920/181156558-66384ebc-4e1b-434b-b534-3a5642a1a438.png)
* ***Giai đoạn 3 kết thúc/ngắt kết nối*** : Khi quá trình truyền tin đã kết thúc thì ngắt kết nối TCP giữa 2 máy

## ***c.	Cơ chế điều khiển luồng(Flow Control)***
* TCP có cơ chế truyền thông tin cậy tuy nhiên nhược điểm là tốc độ truyền khá chậm vậy nên cơ chế điều khiển luồng sẽ giúp cải thiện khả năng truyền của TCP.
### ***Fix Windowing***
* Tham số window size(Trường window size có trong gói tin TCP) áp dụng cho cơ chế flow control.
* Giá trị window size được hiểu như sau. Nếu Window size bằng 1 thì tại 1 thời điểm máy gửi sẽ chỉ gửi được 1 segment
sau đó đợi hồi đáp ACK. Nếu máy nhận nhận được segment 1 nó sẽ gửi về gói tin ACK2 xác nhận đã nhận được segment 1 và yêu cầu gửi segment số 2. Cứ thế tiếp tục đến khi gửi hết segment

![](https://user-images.githubusercontent.com/52046920/181156256-f8ffb046-c9b3-4ed2-82b3-8c6d23e7c616.png)
* Vậy để cải thiện tốc độ gửi ta sẽ tăng giá trị window size lên ví dụ giá trị Window size của cả 2 máy bằng 3 thì máy gửi sẽ gửi liên tiếp 3 segment rồi mới chờ đợi hồi đáp ACK. Máy gửi gửi 3 segment 1, 2, 3 và chờ đợi hồi đáp ACK. Nếu máy nhận đã nhận được đủ 3 segment nó sẽ hồi đáp ACK4 để xác nhận đã nhận được 3 segment và yêu cầu gửi segment tiếp theo bắt đầu từ segment 4. cứ thế tiếp tục cho đến khi gửi hết segment.

![](https://user-images.githubusercontent.com/52046920/181156257-d61d8ff0-5b5a-48be-8264-3f875f79af97.png)
### ***Sliding Windowing***
* 2 thiết bị đầu cuối để tự động có thể thỏa thuận sử dụng, tinh chỉnh giá trị window size tùy theo từng trường hợp(mạng nghẽn, mạng thông thoáng) thì ta sự dụng cơ chế Sliding Windowing
* Hệ điều hành sẽ tự động tính toán window size cho 2 máy gửi và nhận
* Giả sử máy A có window size = 3 và máy B có window size = 2. Máy A gửi dữ liệu cho máy B với cơ chế Sliding Windowing như sau:
    *  Máy A là máy gửi dữ liệu cho B và do có Window size = 3 nên nó gửi 3 segment và chờ đợi phản hồi ACK.
    * Máy B nhận segment của máy A tuy nhiên window size của nó chỉ là 2 nên nó chỉ nhận được 2 segment và segment 3 không đủ tài nguyên lưu trữ nên sẽ bị mất. Sau đó B gửi ACK lại A với ACK3 với mong muốn muốn nhận segment số 3 và thông báo đã nhận 2 segment 1, 2.
    * Máy A nhận được ACK3 của B nó hiểu được window size của máy B là 2 và đang yêu cầu gửi segment 3 nên các lần sau nó sẽ chỉ gửi 2 segment và nó sẽ gửi lại bắt đầu từ segment thứ 3.
![](https://user-images.githubusercontent.com/52046920/181156856-2570f0ae-5d11-4eca-907e-506557e42bfd.png)

## ***2.	Giao thức UDP***
* UDP(User Datagram Protocol) là một giao thức truyền thông không kết nối (Connectionless).
UDP không cung cấp sự tin cậy và thứ tự truyền nhận, các gói dữ liệu có thể đến không đúng thứ tự và bị mất mà không có thông báo.
* Giao thức UDP:
    * Không có giai đoạn thiết lập kết nối.
    * Không duy trì trạng thái kết nối.
    * không có cơ chế đánh số cho các segment.
* Tuy nhiên tốc độ tuyền của giao thức này lại rất nhanh
## ***a. Cấu trúc gói tin UDP***
![](https://vnpro.vn/upload/user/images/Th%C6%B0%20Vi%E1%BB%87n/h%C3%ACnh%202.jpg)

* Source Port (Cổng nguồn): xác định số cổng của trương trình ứng dụng
* Destination Port (Cổng đích): xác định số cổng của trương trình ứng dụng nhận

* UDP length(Độ dài tổng): cho biết chiều dài của toàn bộ UDP datagram.

* UDP checksum: thực hiện kiểm tra lỗi cho toàn bộ UDP datagram.

* Data: dữ liệu lớp trên được đóng gói vào UDP datagram đang xét.

## ***b.	Cách thức hoạt động***
* Trước khi gửi tiến hành phân nhỏ dữ liệu thành các segment có kích thước tối đa là 1480 byte.
* Máy gửi sẽ gửi các segment không được đánh số và gửi đi 1 cách ồ ạt và nhanh đến với máy nhận.
* Trong các segment được gửi nếu mất các segment thì sẽ không thế khôi phục và gửi lại như TCP được.

# ***III.	So sánh và ứng dụng của 2 giao thức***
![](https://user-images.githubusercontent.com/52046920/181156252-cf6c73b4-d052-45a7-bac9-3911680b6b44.png)

# ***IV. Tham số Port nguồn, Port đích***
* Port nguồn: các phiên làm việc được phân biệt với nhau và định danh bằng port nguồn. Port nguồn được hệ điều hành thiết lập ngẫu nhiên.
* Port đích: các dịch vụ được truy cập sử và sử dụng và được quy ước sẵn port nào ứng với dịch vụ nào chứ không được chỉ định ngẫu nhiên ví dụ: web ứng với port 80, FPT(File Transfer Protocol) ứng với port 21,....
* Có thể coi các port là địa chỉ của lớp này tương tự IP của tầng mạng và MAC của tầng kết nối. Nó định danh cho từng phiên làm việc khác nhau