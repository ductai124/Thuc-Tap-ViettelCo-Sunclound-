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

# TÌM HIỂU VỀ ICMP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. ICMP là gì]()
# [II.	Ping]()

## &ensp; [1.	Bản tin Echo Request và Echo Reply của ứng dụng Ping]()

## &ensp; [2.	Bản tin TTL Expired In Transit của ứng dụng Ping]()

## &ensp; [3.	Bản tin Destination Unreachable của ứng dụng Ping]()

## &ensp; [4.	Bản tin Request Timeout của ứng dụng Ping]()

# [III.	Cơ chế hoạt động Tracert trên PC và Traceroute trên Cisco Router]()
***
# ***I.	ICMP là gì***
* Internet Control Message Protocol(ICMP). Là một giao thức của tầng mạng được sử dụng để thông báo các lỗi xảy ra trong quá trình truyền đi của các gói dữ liệu hay dùng để thăm dò và quản lý trình hoạt động mạng
* ICMP không phải là giao thức truyền tải gửi dữ liệu giữa các hệ thống. ICMP không được sử dụng thường xuyên trong các ứng dụng người dùng cuối mà được sử dụng bởi các quản trị mạng, nhằm mục đích khắc phục các kết nối Internet trong các tiện ích chẩn đoán (diagnostic utilities) bao gồm ping và traceroute
* ICMP được ứng dụng trong Ping và traceroute.
* Thông điệp ICMP được chứa trong các gói tin IP.
* Cách ICMP hoạt động như sau: Ví dụ khi không tìm được đường đến đích, router sẽ tạo và gửi message ICMP kiểu 3 tới máy tính gửi gói tin để báo lỗi. Máy tính nhận đc thông báo lỗi sẽ trả lại mã lỗi cho TCP đang cố gắng kết nối tới máy tính đích, TCP trả lỗi cho ứng dụng.

* Bản tin ICMP sẽ có những cấu tạo riêng tuy nhiên luôn có 3 trường sau
    * Type: Dạng gói tin ICMP
    * Code: Nguyên nhân gây lỗi
    * Checksum: Nó là một trường 16 bit để phát hiện xem lỗi có tồn tại trong thông báo hay không.
    * Mỗi dạng sẽ có 1 phần tương ứng khác nhau

![](https://user-images.githubusercontent.com/52046920/183334286-5096a818-bcdd-4475-bdbd-da9301b6ca6f.png)
# ***II.	Ping***
* Ping là viết tắt của Packet Internet Groper, Ping là một tiện ích dòng lệnh, có sẵn trên hầu hết mọi hệ điều hành được sử dụng để xem máy tính có hoạt động hay không và cũng để xem các kết nối mạng có còn nguyên vẹn hay không. 
## ***1.	Bản tin Echo Request và Echo Reply của ứng dụng Ping***
* Trong ping có sử dụng tin nhắn truy vấn là ICMP echo.
* Có 2 loại ICMP echo là Echo reply và Echo request dùng trong ping.
    * Type = 0 thì là Request
    * Type = 8 thì là Reply.
* Nó hoạt động bằng cách gửi một loạt các packet ICMP ECHO Request tới máy chủ đích và chờ phản hồi ICMP ECHO Reply, gửi bao nhiêu request thì sẽ có bấy nhiều reply nếu mạng trong tình trạng ổn định. Thường được sử dụng để  kiểm tra xem các mạng thông nhau chưa, kết nối mạng có ổn định không và còn có thể nhận biết được lỗi đang tồn tại trong hệ thống mạng.
* Các thông số:
    * Bytes: Kích thước của gói tin ICMP
    * Time: Thời gian hồi đáp của gói tin ICMP
    * TTL (Time-to-live): Là trường dài 8 bit có giá trị tối đa là 255 được sử dụng để chống lại sự lặp vòng. Khi TTL đi qua con Router thì giá trị sẽ giảm đi 1 đơn vị. Router nhận gói tin TTL = 0 thì sẽ tự drop gói tin đó lại.
* Sử dụng ping bằng cú pháp
```cmd

C:\Users\T>ping 192.168.68.1            

///192.168.68.1 là ip đích muốn ping đến lệnh ping này sẽ gửi đi 4 bản tin request nếu mạng không có vấn đề gì thì sẽ nhận lại 4 bản tin reply, có thể thay ip bằng tên miền
```

![](https://user-images.githubusercontent.com/52046920/183334290-01041590-5250-4cb8-9604-60ee06ad18c3.png)
* Các Option và cách sử dụng Ping:

![](https://user-images.githubusercontent.com/52046920/183334269-6eb82a46-a5ce-4365-8ab4-8b882d54ada2.png)
* Ping thử đến dantri.com và vnespress.com

![](https://user-images.githubusercontent.com/52046920/183334281-609931af-d211-437f-b7cd-3723ca15dd6e.png)
* Tại router có thể chọn cổng giao tiếp để ping đến các ip khác nhau hay lựa chọn số lần request để tùy theo nhu cầu người sử dụng
```cisco
///Ping từ cổng giao tiếp có ip 192.168.1.1 đến máy tính có ip 192.168.3.2 để kiểm tra 2 mạng có thông nhau không
ping 192.168.3.2 source 192.168.1.1


/// Ping đến máy tính có ip 192.168.3.2, bản tin request sẽ gửi 6 lần
ping 192.168.3.2 repeat 6
```
## ***2.	Bản tin TTL Expired In Transit của ứng dụng Ping***
* TTL time to live Là trường dài 8 bit có giá trị tối đa là 255 được sử dụng để chống lại sự lặp vòng. Khi TTL đi qua con Router thì giá trị sẽ giảm đi 1 đơn vị. Router nhận gói tin TTL = 0 thì sẽ tự drop gói tin đó lại.
* Sự quan trọng của TTL:
    * Giả sử ta có 1 mô hình như sau.


    * Người quản trị cấu hình định tuyến không tốt như sau nên dẫn đến trường hợp sau nếu không có TTL.


    * Trong trường hợp PC1 ping đến PC2 nếu như ping đúng địa chỉ IP thì mọi thứ vẫn diễn ra bình thường.

    ![](https://user-images.githubusercontent.com/52046920/183334250-45df33c8-aff2-4063-99c4-fc297e83d843.png)
    * Tuy nhiên trong trường hợp PC 1 ping đến 1 ip không tồn tại trong hệ thống mạng điều này sẽ diễn ra.
    * ví dụ: PC1 ping đến ip là 192.168.10.10 . Khi này gói tin sẽ được gửi lên default gateway là router R1. Nó sẽ kiểm tra trong bảng định tuyến và không phát hiện ra đường đi mạng nào dẫn đến 192.168.10.0 nên nó sẽ gửi gói tin đi theo default route đến với router R2. Tại R2 nó kiểm tra bảng định tuyến và nhận thấy cũng không phát hiện ra đường đi mạng nào dẫn đến 192.168.10.0 nên nó lại gửi theo defaut route trong bảng định tuyến của nó là đến R1. Do không có TTL vòng lặp này sẽ diễn ra vô tận và ta không thể nhận biết được lỗi xảy ra ở đâu để giải quyết.

    ![](https://user-images.githubusercontent.com/52046920/183334297-ffe49863-6306-4b01-b9fc-0f780ce725a8.png)
    ![](https://user-images.githubusercontent.com/52046920/183334318-89c8f1aa-b355-4d7e-b304-049d81ae18e5.png)
    * Khi có TTL thì cứ mỗi khi gói tin đi qua 1 router nó sẽ giảm đi 1 và khi TTL về bằng 0 nó sẽ hủy gói tin và gửi lại cho ta thông báo từ đó ta có thể nhận biết được mạng đang có vấn đề gì và vị trí xảy ra lỗi.

    ![](https://user-images.githubusercontent.com/52046920/183334330-0d38d0b1-c62b-454b-89e8-24e53ad1592f.png)

## ***3.	Bản tin Destination Unreachable của ứng dụng Ping***
* * Xảy ra khi gói tin không đến được đích. Khi người nhận gửi tin nhắn nhưng gói tin không đến được đích, router trung gian sẽ báo cáo với người gửi. Type =3.
* Nó có nhiều loại ứng với các nguyên nhân khác nhau vậy nên chúng có giá trị code khác nhau từ 0-15 như sau:
    * Code=0, mạng không thể truy cập
    * Code=1, Host không thể truy cập
    * Code=2, Giao thức không thể truy cập
    * Code=3, cổng không thể truy cập
    * Code=4, Yêu cầu phân mảnh và đặt cờ DF
    * Code=5, Nguồn định tuyến không thành công
    * Code=6, Mạng đích không xác định
    * Code=7, Máy chủ đích không xác định
    * Code=8, Máy chủ nguồn bị cô lập
    * Code=9, Mạng bị cấm về mặt hành chính
    * Code=10,Máy chủ bị cấm về mặt hành chính
    * Code=11, Mạng không thể truy cập cho TOS(Type of service)
    * Code=12, Máy chủ không thể truy cập cho TOS(Type of service)
    * Code=13, Giao tiếp bị cấm về mặt hành chính
    * Code=14,Vi phạm ưu tiên của máy chủ
    * Code=15, giới hạn ưu tiên có hiệu lực
* Thường sẽ xảy ra khi định tuyến không tốt hoặc trạng thái của các interface, dây cáp không ổn định dẫn đến việc bảng định tuyến bị thay đổi

## ***4.	Bản tin Request Timeout của ứng dụng Ping***
* Xảy ra khi quá trình ping diễn ra không thành công ví dụ như bị chặn, kết nối đích đến switch bị lỗi nên không kết nối được để gửi về bản tin reply


# ***III.	Cơ chế hoạt động Tracert trên PC và Traceroute trên Cisco Router***
* Traceroute (công cụ truy vết)là một công cụ dòng lệnh đi kèm với Windows và các hệ điều hành khác. Cùng với lệnh ping, đây là một công cụ quan trọng để hiểu các sự cố kết nối Internet, bao gồm mất gói và độ trễ cao.
* Nếu bạn gặp sự cố khi kết nối với một trang web, traceroute có thể cho bạn biết vấn đề đang ở đâu. Nó cũng có thể giúp trực quan hóa lưu lượng đường dẫn giữa máy tính của bạn và máy chủ web.
* Giả sử có mô hình như sau

![](https://user-images.githubusercontent.com/52046920/183336942-3b1ab05d-08d2-4da3-b3c1-f69e78fe0a06.png)
* Ta tiến hành tracert đến PC 2 là 192.168.2.2

* Đầu tiên máy tính sẽ soạn ra gói tin icmp có TTL=1 rồi gửi đi và khi nó đến R1 TTL=0 và gói tin sẽ bị hủy sau đó nó sẽ gửi thông tin về cho PC1 chúng ta sẽ được 1 nút.

![](https://user-images.githubusercontent.com/52046920/183336939-5f262437-8215-4b33-bc19-30026cef3093.png)
* Tiếp theo nó sẽ soạn gói tin có TTL = 2(tăng thêm 1 đơn vị so với lần 1) và khi gói tin đi đến R2 TTL=0 gói tin sẽ bị hủy và R2 sẽ gửi lại PC1 thông báo.

![](https://user-images.githubusercontent.com/52046920/183336940-37f0aedc-f44d-4211-9948-3fcebbd742cd.png)
* Cứ tiếp tục cho gửi các gói tin cho đến khi đến được đích ở đây là gói tin đến được đích khi TTL=3. 

![](https://user-images.githubusercontent.com/52046920/183336941-09783873-ae2c-49b1-a209-8765392ca26d.png)
* Ta có kết quả.

![](https://user-images.githubusercontent.com/52046920/183336943-15336a61-b1da-495c-aae7-54414f804b2e.png)
