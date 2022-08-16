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

# TÌM HIỂU VỀ STP
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
# ***I.	STP là gì***
* STP viết tắt của Spanning Tree Protocol là một giao thức dùng để ngăn chặn sự lặp vòng của hệ thống. Là giao thức khoogn thể thiếu trong tầng Datalink(Layer 2).
##	Lý do xảy ra lặp trong hệ thống***
* Trong 1 hệ thống mạng doanh nghiệp để tăng tính dữ phòng của mạng người ta thường đấu nối nhiều Switch lại với nhau, và 2 switch đấu nối với nhau cũng sẽ bằng 2 đường để nhằm mục đích tạo đường dự phòng cho đường dây chính. Chính việc này đã sinh ra vòng lặp
* Các switch khi đấu nối theo dạng Ring cũng sẽ là 1 nguyên nhân gây ra vòng lặp và còn nhiều nguyên nhân khác nữa có thể xảy ra vòng lặp nhưng chủ yếu là do tính toán dự phòng của doanh nghiệp.
* Các hình thức Loop
## ***1.	Broadcast Storm***
* Giả sử

![](https://user-images.githubusercontent.com/52046920/184801197-c0f300e3-c3f7-4cde-a690-a33f12b0372a.png)
* SW1 sẽ nối 2 đường đến SW2 1 đường chính và 1 đường dự phòng
* PC A tiến hành gửi 1 Broadcast frame vào hệ thống
* SW1 nhận frame này và đẩy qua tất cả các cổng của mình đến với SW2.
    * Frame đến với SW2 bằng đường 1 SW2 nhận frame và nhân bản nó lên rồi đẩy nó qua tất cả các cổng của chính nó trừ cổng vào và trong đó có cổng đến đường 2 nối giữa 2 SW vậy là frame lại quay lại SW1 và sau đó gói tin sẽ gửi đi gửi lại giữa 2 SW gây ra còng lặp.
    * Tương tự với việc Frame đến với SW 2 bằng đường 2 cũng xảy ra vòng lặp
* 2 SW này sẽ nhân bản frame này liên tục và gửi liên trục do bị lặp và đến khi SW hết tài nguyên không thế xử lý được thì nó sẽ bị treo dẫn đến hệ thống mạng bị ngắt

![](https://user-images.githubusercontent.com/52046920/184801193-47036757-f479-4d0e-abe6-2e153f359063.png)

## ***2.	Trùng lập Frame***
![](https://user-images.githubusercontent.com/52046920/184801197-c0f300e3-c3f7-4cde-a690-a33f12b0372a.png)
* PCA gửi một unicast frame đến PCB và địa chỉ MAC của B chưa được cập nhật vào bảng MAC của Sw thì Sw sẻ xử lý các frame này như một broadcast frame và flood ra tất cả các port trừ port nhận vào. Và Sw1 và Sw2 đều thực hiện chuyển flood frame này ra nhiều port khiến PCB phải xử lí frame này 2 lần.

## * Để đề phòng các trường hợp lặp có thể xảy ra thì STP được ra đời và giải quyết triệt để được vấn đề này


# ***II.	Cơ chế chống Loop của công nghệ STP***
* Tiến trình bầu chọn và hoạt động của Giao thức Spanning Tree:
    * Thực hiện bầu chọn Root-Bridge()
    * Bầu chọn Root-Port
    * Lựa chọn các Designated-Port
    * Blocking các Port còn lại
# ***1. Chọn Root-Bridge của Giao thức Spanning Tree***
* Khi STP được bật, các Switch sẽ gửi các gói tin BPDU(Bridge Protocol Data Unit) để trao đổi giữa các Switch. Gói tin này chứa Bridge-ID để định danh mỗi Switch tham gia STP.
* Bridge-ID dài 8byte:
    * Số Priority(2byte): có giá trị từ 0 – 65535 mặc định là 32768. Đây là trường ưu tiên và có thể cấu hình
    * MAC address(6byte)
* Tiến trình bầu chọn Root-Bridge:
    * So sánh Switch có Priority sẽ là Root-Bridge
    * Nếu các Switch được thiết lập số Priority bằng nhau(Không xác định được Root-bridge bằng Priorrity) thì so sánh MAC, MAC nhỏ nhất thì Switch được chọn làm Root-Bridge(So sánh từ trái qua phải địa chỉ MAC để biết được địa chỉ nào nhỏ hơn).

    ![](https://user-images.githubusercontent.com/52046920/184835219-36dadf83-3719-44ed-a31d-2c010bcec15f.png)
    * Sau khi được làm Root-Bridge thì Switch làm root gửi BPDU ra khỏi cổng để duy trì tiền trình STP(2s/lần). Các Switch còn lại chỉ nhận bổ sung BPDU và chuyển tiếp nó 

![](https://user-images.githubusercontent.com/52046920/184835208-5b94cfaa-14fd-48d9-afca-2ed89ff928c3.png)
# ***2. Bầu chọn Root-port của Giao thức Spanning Tree***
* Root-Port là port có đường về Root-bridge có tổng cost tích lũy nhỏ nhất. Switch được chọn làm Root-bridge không tham gia vào quá trình này

* Bảng cost của 1 số loại interface Ethernet LAN

|Tốc độ|Cost|
|--|--|
|10Mbps|100|
|100Mbps|19|
|1Gbps|4|
|10Gpbs|2|

* Nguyên tắc tính tổng Root path-cost(RPC-là tổng cost của từng port): tính từ Root-Bridge đến switch đang muốn tính
    * Đi ra: không cộng
    * Đi vào: cộng cost
* RPC sẽ là tổng cost của các cổng phải đi ra cho đến khi đến được Root-Bridge Cổng nào có RPC thấp nhất sẽ được chọn là Root-Port của Switch
* Ví dụ từ SW3 về SW1 là Root-Bridge
    * Nó có 2 đường đi đến SW1
    * Giả sử đây đều là SW của cisco thì các cổng FastEthernet có giá trị cost mặc định bằng 19
    * Cổng Fa0/1 chỉ đi 1 lần là đến SW1 nên RPC =19
    * Cổng Fa0/2 phải đi ra 3 lần để đến được SW 1 vậy nên RPC tổng cost của 3 lần đó là RPC=19+19+19=57
    * 57<19 vậy nên chọn Fa0/1 làm Root Port của SW3

![](https://user-images.githubusercontent.com/52046920/184888556-7bf84249-b998-4553-b12a-8a108bb69e99.png)
* Khi RPC của các cổng bằng nhau thì ta sẽ sử dụng các tiêu chí khác:
    * Dựa vào Bridge-ID của thiết bị láng giếng. Đứng tại Switch đang xét Root-Port nếu RPC của các cổng bằng nhau thì ta xét Priority của Switch láng giếng. Priority của Switch nào thấp hơn thì cổng kết nối với Switch đấy sẽ được chọn. Ví dụ: Tại Switch 4 có 2 đường đến SW1 và RPC của cả 2 đều bằng 19+19=38 vậy nên xét ta phải xét đến Priority của SW3 và SW2 và nhận thấy SW3 có Priority nhỏ hơn của SW2 vậy nên Fa0/1 sẽ là Root-Port

    ![](https://user-images.githubusercontent.com/52046920/184888569-06e49462-b71a-44f4-acc3-812f135127e9.png)
    ![](https://user-images.githubusercontent.com/52046920/184888571-c3ee3762-876d-418e-b6af-cfe5766f5770.png)
    * Khi Bridge-ID của Switch láng giềng là bằng nhau thì ta xét tiếp tục đến Port-ID của các Switch láng giềng. Port nào mà kết nối vời Port của Switch láng giềng có Port ID thấp hơn thì sẽ được chọn làm Root-Port

![](https://user-images.githubusercontent.com/52046920/184888575-48099995-555b-4ed2-8cf8-d5d02b3e6221.png)
* Khi các luật trên không giải quyết được thì nó sẽ xét đến Port ID trên chính nó

* Thông thường các cổng nối với switch được chọn Root-Bridge sẽ là Root-Port



# ***3. Bầu Chọn Designated port***
* Là port cung cấp đường về root-bridge có tổng cost nhỏ nhất trên phân đoạn mạng đang xét. Chỉ có một Designated port ứng với một link kết nối.
* Các Switch nối với nhau tạo ra bao nhiêu phân đoạn mạng thì sẽ có bấy nhiêu Designated port
* Port kết nối trực tiếp với Designated port ở Switch láng giềng sẽ là Alternated Port(BLoack Port)
* Cách xác định
    * Tất cả các Port của Switch được chọn làm Root-Bridge đều là Designated Port
    * Switch nào có RPC của Root-Port nhỏ hơn thì cổng của nó trên phân đoạn mạng đang xét sẽ là Designated port
    * Nếu RPC của Root-Port bằng nhau ta lại dựa vào Bridge-ID, Bridge-IDcủa Switch nào có Priority nhỏ hơn thì trên phân đoạn mạng đó Port của Switch đó sẽ là Designated port

# ***4. Alternate port(Block Port)***
* Port đối diện với Designated port mà không phải Root-port sẽ là Alternate port bị Block và sử dụng như 1 đường dự phòng.
* Khi 1 trong các phân đoạn khác bị đứt thì phân đoạn port block sẽ được mở ra để chạy.
* Khi phân đoạn trên có lại thì phân đoạn block sẽ tiếp tục bị block lại
* Tuy port block không nhận được dữ liệu nhưng nó vẫn nhận gói tin BPDU từ Root-switch để duy trì cây spanning-tree.