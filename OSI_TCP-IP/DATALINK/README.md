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

# TÌM HIỂU VỀ MÔ HÌNH TCP/IP
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
# ***I.	Chức năng và nhiệm vụ***
* Nó chịu trách nhiệm truyền dữ liệu từ nút này sang nút khác. Vai trò chính của nó là đảm bảo truyền thông tin không bị lỗi. Nó cũng chịu trách nhiệm mã hóa, giải mã và tổ chức dữ liệu đi và đến.

* Nhiệm vụ:
    * Đóng gói các Packet thành Frame phù hợp với công nghệ đường truyền mà Frame sẽ đi vào.  
    * Liên kết dữ liệu với tầng trên.
    * Điều khiển Frame truy cập đường truyền bằng việc sử dụng các kỹ thuật điều khiển truy cập đường truyền và phát hiện lỗi.
    * Quy định cấu trúc địa chỉ ở tầng Data Link và thêm Địa chỉ nguồn và đích vào Frame.

![](https://user-images.githubusercontent.com/52046920/178717357-dc01f9d3-2180-4c3b-a7d1-af029e4452c3.png)
* Dịch vụ tầng DATALINK:
## ***1.  Đóng khung dữ liệu (Framing)***
* Một gói dữ liệu di chuyển xuống từ tầng mạng được đóng gói thành 1 frame. Cấu trúc của frame được quy định cụ thể bởi giao thức tầng liên kết

## ***2. Kiểm soát truy cập đường truyền***
* Giao thức điều khiển truy cập (MAC) chỉ định các quy tắc mà khung đƣợc truyền lên liên kết
* Hai loại kết nối
    * point-to-point link (điểm-điểm) : một đường truyền duy nhất kết nối 2 node. Các giao thức nổi bật : PPP , HDLC Thường có trong ADSL , Telephone modem, Leased , Line…
    * broadcast link (quảng bá) : nhiều node chia sẻ cùng một đường truyền. Một frame được gửi từ 1 node đến 1 node sẽ đượctruyền đi tới tất cả các node trên mạng – gọi là broadcast hay quảng bá Thường có trong mạng LAN truyền thống (bus hay star topology); Wireless LAN, radio network, mobile network, …
* Các giao thức đa truy nhập:
    * Chia kênh (channel partitioning) Chia tài nguyên của đường truyền thành nhiều phần nhỏ (thời gian – TDMA, Tần số - FDMA , Mã -CDMA). Chia từng phần nhỏ đó cho từng node
    * Truy nhập ngẫu nhiên (random access) Không chia kênh, cho phép đồng thời truy nhập, chấp nhận có xung đột (collision). Cung cấp cơ chế phát hiện và tránh xung đột Pure Aloha, Slotted Aloha, CSMA/CD, CSMA/CA ,…
    * Quay vòng (taking-turn) Các node chiếm kênh truyền theo hình thức quay vòng Token Ring, Token bus ,…
* Các giao thức chia kênh:
    * TDMA (Time division multiple access): Phân chia thời gian truyền trên kênh theo time framesvà time slots. Mỗi node chỉ thực hiện truyền các bit dữ liệu khi đến lượt và trong time slot của mình
    * FDMA (Frequency division multiple access): Tạo ra N kênh truyền có tần số khác nhau cho N node
    * CDMA (Code division multiple access): Mỗi node sử dụng một mã riêng để mã hóa các bit dữ liệu mà nó gửi đi
    * Các giao thức trên cho phép đa truy nhập, ngăn chặn được đụng độ tuy nhiên chúng có những nhược điểm sau
    * Nhược điểm :
        * TDMA (Time division multiple access): Mỗi nút bị giới hạn ở băng thông trung bình ngay cả khi nó là nút duy nhất vào kênh truyền. Một nút phải luôn luôn chờ đợi đến lượt của mình, ngay cả khi chỉ có nó là nút cần gửi.
        * FDMA (Frequency division multiple access): Nút bị giới hạn ở băng thông trung bình ngay cả khi nó là nút duy nhất vào kênh truyền.
        * CDMA (Code division multiple access): Thường chỉ sử dụng trên điện thoại di động

![](https://user-images.githubusercontent.com/52046920/178717364-8325224d-df4b-42db-9146-f31d19cd68a0.png)
* Truy nhập ngẫu nhiên (random access): Dữ liệu của node truyền chiếm toàn bộ kênh truyền. Cho phép đa truy nhập, chấp nhận va chạm Khi các node gặp va chạm và sẽ truyền lại frame sau 1 khoảng thời gian chờ. Node có thể phải truyền lại nhiều lần
* Token Ring  (mạng vòng dùng thẻ bài): Sử dụng một frame đặc biệt gọi là token (thẻ bài). Token được chuyển lần lượt giữa các node theo 1 thứ tự nhất định. Node chỉ truyền dữ liệu của nó khi nhận được token. Gửi dữ liệu xong / hoặc ko có nhu cầu gửi dữ liệu, node phải chuyển token cho node kế tiếp
## ***3. Dịch vụ truyền tin cậy***
* Khi cung cấp dịch vụ truyền tin cậy, giao thức tầng liên kết dữ liệu đảm bảo truyền chính xác gói dữ liệu trên một đường truyền. Dịch vụ truyền tin cậy thường được sử dụng trên đường truyền có tỉ lệ lỗi cao (ví dụ như các đường truyền không dây).
## ***4. Kiểm soát lưu lượng***
* Khả năng lưu trữ tạm thời của các frame tại các nút trên mỗi phía của đường truyền không phải là vô hạn. Đây sẽ là vấn đề khi tốc độ tới của các frame nhanh hơn tốc độ nút nhận có thể xử lý được. Nếu không kiểm soát lưu lượng, bộ đệm phía nhận có thể bị tràn và frame sẽ bị mất.
## ***5. Phát hiện lỗi và sửa lỗi***
* Phát hiện lỗi: nút nhận có thể nhận bit 0 trong khi phía gửi gửi bit 1 hoặc ngược lại. Nguyên nhân bit bị lỗi có thể là do tín hiệu bị suy hao hay nhiều điện từ. Nhiều giao thức tầng liên kết dữ liệu cung cấp cơ chế phát hiện lỗi. Điều này được thực hiện bằng cách phía gửi sẽ thiết lập một số bit phát hiện lỗi trong frame và phía nhận thực hiện việc kiểm tra lỗi.
* Sửa lỗi: Sửa lỗi cũng tương tự phát hiện lỗi. Tuy nhiên không chỉ xác định được bit có khả năng lỗi mà phía nhận còn có khả năng xác định chính xác vị trí lỗi xuất hiện trong frame và do đó có thể sửa được những lỗi này.
# ***II. Lớp liên kết dữ liệu được chia thành hai lớp con***
* LLC(Logical Link Control): Nó có trách nhiệm quản lý và đảm bảo tính toàn vẹn của việc truyền dữ liệu. Chúng cung cấp logic cho liên kết dữ liệu. Nó cũng kiểm soát các chức năng đồng bộ hóa, ghép kênh, kiểm tra lỗi hoặc sửa chữa. Nó cũng cho phép giao tiếp đa điểm trên một loạt các mạng máy tính. . Cung cấp chức năng điều khiển lưu lượng, và phát hiện các gói tin bị bỏ (drop) và truyền lại nếu được yêu cầu.
* MAC(Media Access Control): Là một dãy số 48-bit của phần cứng máy tính, được nhà sản xuất card mạng nhúng vào. Là một định danh duy nhất (unique identifier). Địa chỉ Mac gồm 6 octet, mỗi octet 8 bits, được biểu diễn bằng 6 cặp chữ số hoặc ký tự khác nhau có thể bao gồm bất kể số nào từ 0 đến 9 hoặc chữ cái từ A đến F và được ngăn cách bởi dấu hai chấm. Địa chỉ MAC cung cấp cho lớp con này một bộ nhận dạng duy nhất để mỗi điểm truy cập mạng có thể truyền thông với mạng. Lớp con MAC cũng có trách nhiệm cho việc truy cập cáp mạng, hoặc môi trường truyền thông.

# ***III. Cấu trúc frame***
![Cấu trúc frame](https://user-images.githubusercontent.com/52046920/178717371-f1e80f22-4cb8-4859-9b93-b274f65d2901.PNG)
* Về cơ bản frame gồm có 3 phần:
    * Data: là dữ liệu chuyển từ lớp mạng
    * Header: chứa thông tin điều khiển như địa chỉ MAC đích, địa chỉ MAC nguồn. Các trường Header điển hình bao gồm:
        * Start Frame field: là trường cho biết phần bắt đầu của khung.
        * Source and Destination address fields: cho biết nút nguồn và nút đích
        * Type: cho biết dịch vụ lớp trên 
        * Logical connection control field: dùng để thiết lập kết nối logic giữa các nút.
        * Physical link control field: thiết lập kết nối vật lý
        * Flow control field: Trường điều khiển luồng
        * Congestion control field: Trường kiểm soát tắc nghẽn
    * Trailer: Thường chứa các bit dư thừa để kiểm soát lỗi FCS(Frame check sequence)
* Frame cụ thể sẽ như sau tùy :
    * Frame Header : chứa địa chỉ nguồn và đích của khung và các byte điều khiển.
    * PAYLOAD FILED : Mang dữ liệu của lớp mạng.
    * TRAILER: chứa các bit phát hiện lỗi và sửa lỗi. Nó còn được gọi là Trình tự kiểm tra khung (FCS).
    * FLAG: Hai cờ ở hai đầu đánh dấu điểm đầu và điểm cuối của khung.
![Cấu trúc frame](https://user-images.githubusercontent.com/52046920/178717378-cf1c7356-5c09-41cf-9ce9-5311f217f937.PNG)
* Cấu trúc của nó có thể thay đổi tùy theo giao thức sử dụng
# ***IV. Các giao thức***
## ***1. Giao thức High-level Data Link Control (HDLC)***
* HDLC là giao thức truyền thông mục đích chung điểm-điểm hoạt động ở cấp liên kết dữ liệu. Nó cung cấp khả năng phục hồi lỗi trong trường hợp mất gói dữ liệu, lỗi chuỗi và các lỗi khác, do đó nó cung cấp liên lạc đáng tin cậy giữa máy phát và máy thu.
* Là một giao thức quan trọng vì nó là cơ sở cho nhiều giao thức điều khiển liên kết dữ liệu.

![Cấu trúc frame](https://user-images.githubusercontent.com/52046920/178717368-d0d558f6-c093-4acd-977d-775ed7ee4316.PNG)
* Cấu trúc frame của HDLC:
    * FLAG : Là một chuỗi 8 bit với mẫu bit 01111110.

    * ADDRESS : Chứa địa chỉ của người nhận. Trường địa chỉ có thể từ 1 byte đến vài byte.

    * CONTROL : là 1 hoặc 2 byte chứa thông tin kiểm soát luồng và lỗi.

    * INFORMATION : Mang dữ liệu từ lớp mạng. Độ dài của nó có thể thay đổi từ mạng này sang mạng khác.

    * FCS : Đây là một chuỗi kiểm tra khung 2 byte hoặc 4 byte để phát hiện lỗi. Mã tiêu chuẩn được sử dụng là CRC (mã dự phòng theo chu kỳ)
## ***2. Giao thức Point – to – Point (PPP)***
* PPP là giao thức lớp 2 phổ biến cho mạng WAN. Hai thành phần của PPP tồn tại: LCP (Link Control Protocol) đàm phán kết nối và NCP (Network Control Protocol) đóng gói lưu lượng.
*  Giao thức kiểm soát liên kết (Link Control Protocol): LCP được sử dụng để thiết lập, định cấu hình và kiểm tra kết nối liên kết dữ liệu. Nó linh hoạt trong việc xử lý các kích cỡ khác nhau của các gói, phát hiện một liên kết ngược, lỗi cấu hình và chấm dứt liên kết.
* Giao thức điều khiển mạng (Network Control Protocol): NCP được sử dụng để thiết lập và định cấu hình các giao thức lớp Mạng khác nhau.
PPP cho phép sử dụng đồng thời nhiều giao thức lớp Mạng. 

![Cấu trúc frame](https://user-images.githubusercontent.com/52046920/178717374-620bd5f9-ce5d-49b7-afce-c52754d39a88.PNG)
* Cấu trúc frame của PPP:
    * FLAG : Có 1 byte với mẫu bit 01111110.

    * ADDRESS : 1 byte được đặt thành 11111111 trong trường hợp phát sóng.

    * CONTROL : 1 byte được đặt thành giá trị không đổi là 11000000.

    * PROTOCOL : 1 hoặc 2 byte xác định loại dữ liệu có trong INFORMATION.

    * INFORMATION :Mang dữ liệu từ lớp mạng. Độ dài tối đa là 1500 byte.

    * FCS : Đây là một chuỗi kiểm tra khung 2 byte hoặc 4 byte để phát hiện lỗi. Mã tiêu chuẩn được sử dụng là CRC (mã dự phòng theo chu kỳ).
## ***3. Công nghệ ETHERNET***
* Là 1 cộng nghệ mạng sử dụng kết nối các mạng lại với nhau trong mạng cục bộ. Cho phép các thiết bị có thể giao tiếp với nhau qua 1 giao thức và 1 bộ quy tắc hoặc ngôn ngữ mạng chung.
* Là một giao thức DATALINK nó xác định 2 đơn vị truyền: Packet và Frame.
* Gói tín của Ethernet Ethernet IEEE 802.3 gồm:
    * Preamble Gồm 1 dãy các giá trị bit 0 và 1 xen kẽ đế báo hiệu trạm nhận có frame đang tới. Cho phép các thiết bị trên mạng dễ dàng đồng bộ, cung cấp đồng bộ hóa ở mức bit. Độ dài 56 bit(7Byte) như sau:
    10101010 - 10101010 - 10101010 - 10101010 - 10101010 - 10101010 - 10101010
    * SFD(Start Frame Delimiter): là 1 chuỗi 8 bit(1 Byte) 10101011. đánh dấu kết thúc của preamble, trường đầu tiên của một packet Ethernet, và chỉ ra điểm bắt đầu của một frame Ethernet bằng 2 bit cuối là 11. SFD được thiết kế để phá vỡ pattern bit của preamble và đánh tín hiệu sự bắt đầu của một frame thực sự. 
    * Cấu trúc frame Ethernet IEEE 802.3 gồm:
        * Destination ADDRESS(DA): Gồm 6 Bytes để xác nhận trạm sẽ nhận frame. Chứa địa chỉ MAC của đích sắp đến của gói tin.
        * Source Address (SA): Gồm 6 bytes chứa địa chỉ MAC của thiết bị cuối cùng chuyển tiếp gói.
        * EtherType 2 Bytes và có thể dùng cho nhiều mục đích khác nhau. Nếu <= 1500 thì nó được dùng chỉ kích thước payload bằng octet, nếu >= 1536 thì dược dùng chỉ kiểu EtherType, xác định protocol nào được đóng gói trong payload.
        * Payload có dung lượng lớn nhất 1500 Bytes. Nó chứa dữ liệu từ lớp mạng
        * Frame check sequence(FCS): Là 1 phương pháp kiểm tra phát hiện lỗi theo chu kỳ, có độ dài 4 Bytes. Nó cho phép kiểm tra và phát hiện dữ liệu bị hỏng bên trong toàn bộ frame theo mã CRC-32
## ***3. Giao thức ARP***
* ARP(Address Resolution Protocol) là một giao thức truyền thông phân giải địa chỉ động giữa địa chỉ lớp network và địa chỉ lớp datalink.
* Quá trình thực hiện bằng cách: một thiết bị IP trong mạng gửi một gói tin broadcast đến toàn mạng yêu cầu thiết bị khác gửi trả lại địa chỉ phần cứng ( địa chỉ lớp datalink ) của mình.
* Ban đầu ARP chỉ được sử dụng trong mạng Ethernet để phân giải địa chỉ IP và địa chỉ MAC. Nhưng ngày nay ARP đã được ứng dụng rộng rãi và dùng trong các công nghệ khác dựa trên lớp hai.
* Cách thức hoạt động:
    * Khi một network device muốn biết MAC address của một network device nào đó mà nó đã biết địa chỉ ở tầng network (IPv4) , nó sẽ gửi một “ARP request” bao gồm địa chỉ MAC address của nó và IP address của network device mà nó cần biết MAC address trên toàn bộ miền broadcast .
    * Mỗi network device nhận được request này sẽ so sánh địa chỉ IP trong request với IP address của mình . Nếu trùng IP address thì sẽ gửi ngược lại cho network device kia một packet “ARP request” ( trong đó có MAC address của mình ) .
# ***IV. Các Thiết bị hoạt động trên tầng này***
* Switch là thiết bị chủ yếu ở tầng này vì nó có chức năng chuyển mạch, cụ thể là chuyển các Frame. Switch hoạt động trên 7 tầng của OSI nhưng nhiệm vụ chuyển mạch là nhiệm vụ chính tại tầng Data link.
* Bridge là một thiết bị hoạt động ở lớp 2 của mô hình OSI dùng để kết nối các phân đoạn mạng nhỏ có cùng cách đánh địa chỉ và công nghệ mạng lại với nhau và gửi các gói dữ liệu giữa chúng. Việc trao đổi dữ liệu giữa hai phân đoạn mạng được tổ chức một cách thông minh cho phép giảm các tắc nghẽn cổ chai tại các điểm kết nối. Các dữ liệu chỉ trao đổi trong một phân đoạn mạng sẽ không được truyền qua phân đoạn khác, giúp làm giảm lưu lượng trao đổi giữa hai phân đoạn. Bridge có thể nối nhiều hub lại với nhau như hình dưới đây.