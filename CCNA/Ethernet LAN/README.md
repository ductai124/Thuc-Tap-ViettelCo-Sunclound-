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

# TÌM HIỂU VỀ ETHERNET LAN
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
# ***I.	Tổng quan Ethernet LAN***
* Mạng Lan(Local Area Network) hay mạng cục bộ : một hệ thống mạng Lan chỉ cần gồm 2 máy tính kết nối sử dụng công nghệ Ethernet để trao đổi dữ liệu với nhau là có thể gọi đó là mạng Lan. Với mạng Lan có quy mô nhỏ thì hệ thống được gọi Small Office Lan. Với hệ thống gồm nhiều mạng Lan kết nối lại với nhau tạo thành 1 mạng Lan quy mô lớn được gọi là Large Office Lan

### ***Ethernet LAN: MAC***
* Ethernet là 1 trong các công nghệ được sử dụng phổ biến trên các hệ thống mạng lan. Ethernet là một dạng công nghệ mạng, sử dụng kết nối các mạng lại với nhau trong mạng cục bộ. Đây là nơi để các thiết bị điện tử kết nối với nhau thông qua một giao thức. Là nơi giúp máy tính, laptop, tivi,... có thể kết nối với mạng, kết nối dữ liệu với các thiết bị khác. Trong Ethernet sẽ có khung, để chia luồng dữ liệu thành các gói gồm địa chỉ nguồn và đích, có chức năng phát hiện lỗi trong dữ liệu được truyền và yêu cầu truyền lại.
* Đặc điểm nổi bật nhất của Ethernet là các thiết bị khi mà tham gia kết nối vào mạng Lan sẽ được định danh bằng địa chỉ MAC.
* Mỗi máy tính muốn kết nối với hệ thống mạng Lan cần phải được trang bị card mạng và mỗi card mạng thì đều sở hữu 1 địa chỉ MAC duy nhất không trùng với bất cứ địa chỉ MAC nào
* Địa chỉ MAC được hiển thị cho chúng ta ở dạng 12 số hexa để dễ dàng quan sát.


# ***II. Xác định địa chỉ MAC của máy tính trên hệ điều hành Window***
* Sử dụng CMD:
    * Mở CMD lên và thực hiện câu lệnh
```cmd
    ipconfig /all
```
* Ở đây máy tính đang sử dụng mạng wifi thì ta sẽ kiểm tra Wireless LAN adapter Wi-Fi và Physical Addess là địa chỉ MAC của card mạng

![](https://user-images.githubusercontent.com/52046920/181193258-22e79c2a-fc17-4360-a81b-6d211270f0b4.png)

* Sử dụng giao diện Network Connections

![](https://user-images.githubusercontent.com/52046920/181193259-e9ba41d7-8dff-40ed-889f-1a3c8b549830.png)
* Ở đây có 4 card mạng là Ethernet, 2 Card mạng cho máy ảo và card Wifi, Do đang kết nối wifi nên card mạng wifi đang hoạt động và card mạng Ethernet đang không được hoạt động nên ta tiên hành kiểm tra địa chỉ MAC của card wifi.
Click chuột phải vào card mạng wifi chọn status

![](https://user-images.githubusercontent.com/52046920/181193261-fd393c05-6ded-4842-a9af-9788e1c2fec5.png)
* Sau đó chọn Details... 

![](https://user-images.githubusercontent.com/52046920/181193264-138ef6a3-d4a3-4f0d-93a6-fd19d2556de8.png)
* Địa chỉ MAC chính là physical Address

![](https://user-images.githubusercontent.com/52046920/181193267-4dba76d8-1a44-469a-b5aa-f35746180652.png)

# ***III. Tìm hiểu cấu trúc của địa chỉ MAC***
* MAC viết tắt Media Access Control. Địa chỉ MAC là một dãy số 48-bit của phần cứng máy tính, được nhà sản xuất card mạng nhúng vào. Địa chỉ MAC được ví là địa chỉ vật lý của thiết bị mạng tương tự như việc muốn đi đến nhà nào cũng phải biết địa chỉ của nhà đó
* Cấu trúc địa chỉ MAC dài 48 bit và chia làm 2 phần gồm:
    * 24 bit đầu Organization Unique Identifier là những ký tự MAC định danh nhà sản xuất thiết bị. Có thể căn cứ vào để biết được card mạng do hãng nào sản xuất, các hãng sản xuất phải liên hệ với tổ chức quản lý MAC để mua 24 bit này
    * 24 bit cuối Vendor Assigned định danh cho các card mạng được sản xuất ra, được gán bởi nhà sản xuất.
        * CC:46:D6 - Cisco 
        * 3C:5A:B4 - Google Inc.
        * 3C:D9:2B - Hewlett Packard
        * 00:9A:CD - HUAWEI TECHNOLOGIES CO.,LTD
* Thử kiểm tra Card mạng của máy tinh cá nhân có địa chỉ MAC là :F8-28-19-6A-26-57

![](https://user-images.githubusercontent.com/52046920/181193258-22e79c2a-fc17-4360-a81b-6d211270f0b4.png)

* Có 6 chữ số đầu của địa chỉ MAC là F8-28-19

* Kiểm tra được hãng sản xuất trên web [aruljohn](https://aruljohn.com/mac.pl)

![](https://user-images.githubusercontent.com/52046920/181200573-4b61ae82-e173-48e9-ad4e-4784492cc4eb.png)
# ***IV. Các tiêu chuẩn Ethernet***
*   Institute of Electrical and Electronics Engineers (IEEE) đã bắt đầu thực hiện dự án 802 để tiêu chuẩn hóa các mạng local area network (LAN) vào 1980.
* Ethernet chuẩn IEEE 802.3, 10 BASE-T
* Ngoài ra còn có
    *   Fast Ethernet có các chuẩn :
        * 802.3u, 100BASE-TX
        * 802.3, 100BASE-FX
    * Gigabit Ethenet có các chuẩn
        * 802.3z
        * 802.3x
        * 802.3 ab
* Và còn rất nhiều các tiêu chuẩn khác nữa

# ***V. Quá trình trao đổi dữ liệu giữa các thiết bị trên mạng LAN***
* Các thiết bị đầu cuối (máy tính, ...) trước khi có thể giao tiếp được với các thiết bị khác chúng cần phải được định danh bởi 2 thông tin là địa chỉ MAC và địa chỉ IP.
* Ví dụ PC 1 muốn giao tiếp đến PC 2 nó se gửi frame bao gồm Source IP, Destination IP, Source MAC và Destination MAC đến switch.
* Switch căn cứ vào Destination MAC rồi gửi đến đúng máy 2 sau đó PC 2 sẽ đọc tiếp vào Destination IP nêu đúng địa chỉ IP của nó thì nó sẽ sẽ thực hiện xử lý gói tin.
# ***VI. Cơ chế chuyển mạch của Ethernet Switch***
* Chức năng chính của Switch là Switching(chuyển mạch). Nó là quá trình Switch nhận 1 frame trên 1 cổng giao tiếp và xử lý đẩy frame đó qua các cổng giao tiếp khác theo đúng yêu cầu, quá trình như vậy được gọi là quá trình chuyển mạch.
* Quá trình chuyển mạch switch cần dựa vào bảng chuyển mạch
. Bảng chuyển mạch bảo gồm 2 cột là cổng giao tiếp và địa chỉ MAC.
* Quá trình chuyển mạch diễn ra như sau:
    * PC A gửi frame đến B với Source MAC là A và Destination MAC là B. 
    * Frame đi đến switch nó sẽ kiểm tra trong bảng chuyển mạch để tìm kiểm Destination MAC là B và chuyển nó đến đúng địa chỉ

![](https://user-images.githubusercontent.com/52046920/181255627-f8bba295-d34b-4a84-84f3-e352dc4ceaec.png)
* Cách thức xây dựng bảng chuyển mạch. Một Switch mới thì bảng chuyển mạch của nó sẽ không có giá trị nào hết và nó sẽ phải xây dựng bảng chuyển mạch 1 cách tự động. Để xây dựng bảng chuyển mạch nó thực hiện như sau:
    * Học Source MAC và chuyển tiếp dựa vào Destination MAC. Khi 1 Frame được chuyển đến switch nó sẽ học Source Mac và lưu vào cổng giao tiếp gửi frame đến sau đó đọc trong bảng chuyển mạch nó vì do bảng chuyển mạch chưa có gì ngoài địa chỉ MAC vừa học nên nó chuyển tiếp frame đến tất cả các cổng còn lại trừ cổng gửi. Nếu phát hiện được Destination MAC thì nó sẽ chuyển tiêp frame đến đo như bình thường.
    * Quá trình lặp lại cho đến khi Switch đã học được hết các địa chỉ MAC cho các cổng giao tiếp và xây dựng xong bảng chuyển mạch.
    * Bảng chuyển mạch sẽ chỉ lưu địa chỉ MAC trên công giao tiếp trong vòng 5 phút nếu như không có frame nào được gửi đến cổng giao tiếp đó trong vòng 5 phút nó sẽ xóa địa chỉ MAC trên công đó. Điều này nhằm mục đích làm gọn tài nguyên của bảng chuyển mạch
# ***VII. Các kiểu truyền thông trên hệ thống mạng LAN***
* Trên hệ thống mạng Ethernet Lan tồn tại 3 kiểu truyền thông:
    * Unicast: một thiết bị máy tính sẽ gửi dữ liệu cho 1 máy tính
    * Broadcast: một máy tính sẽ gửi dữ liệu cho tất cả máy tính. Địa chỉ MAC broadcast được quy ước trên hệ thống mạng Lan là địa chỉ FFFF.FFFF.FFFF
    * Multicast: Một máy tính sẽ gửi dữ liệu cho 1 nhóm các máy tính
* Unicast: Khi PC A muốn gửi dữ liệu cho PC C thì frame có Source MAC là địa chỉ Mac của PC A và Destination MAC là địa chỉ MAC của PC C. Khi này switch sẽ làm nhiệm vụ chuyển mạch như bình thường

![](https://user-images.githubusercontent.com/52046920/181193274-82505c88-b346-41e6-924f-e6813668ec5e.png)
* Broadcast Khi PC A muốn gửi dữ liệu cho tất cả các PC thì thì frame có Source MAC là địa chỉ Mac của PC A và Destination MAC là địa chỉ MAC của Broadcast là FFFF.FFFF.FFFF. Switch khi nhận được 1 frame có địa chỉ MAC là broadcast là FFFF.FFFF.FFFF switch sẽ nhân bản frame đó và gửi cho tất cả các cổng còn lại trừ cổng vào.

![](https://user-images.githubusercontent.com/52046920/181193247-9b919db4-a04a-4d40-bb22-7a5358c2abef.png)

# ***VIII. Cơ chế hoạt động của giao thức ARP***
* Giao thức phân giải địa chỉ (Address Resolution Protocol hay ARP) là một giao thức truyền thông được sử dụng để chuyển địa chỉ từ tầng mạng (Internet layer) sang tầng liên kết dữ liệu (Data Link layer) theo mô hình OSI.
* ARP được sử dụng để từ một địa chỉ mạng (ví dụ một địa chỉ IPv4) tìm ra địa chỉ vật lý như một địa chỉ Ethernet (địa chỉ MAC), hay còn có thể nói là phân giải địa chỉ IP sang địa chỉ máy.
* Giả sử Máy PC A ping đến PC B:
    * Ping máy A đến ip máy B. PC sẽ soạn thảo bản tin gồm IP nguồn và IP đích và để gửi đến B thì cần gắn MAC nguồn và MAC đích mà đứng ở PC A không biết được MAC đích là MAC của B là gì. Từ đó là dựa vào IP B để phân giải nó ra địa chỉ Mac của B.

    ![](https://user-images.githubusercontent.com/52046920/181193239-e765fe6d-34e6-4887-a680-1c9ac0e36089.png)
    * Để phân giải địa chỉ IP thành một địa chỉ MAC tương ứng. PC A sẽ gửi 1 bản tin ARP request với Mac nguồn là của máy A và Mac đích là Mac broadcast đi toàn bộ mạng để hỏi xem máy nào là máy có địa chỉ IP của B thì hồi đáp cho nó địa chỉ Mac tương ứng.
    * Các PC ko có IP tương ứng sẽ không hồi đáp. Máy B có địa chỉ IP tương ứng nên hồi đáp lại ARP reply lại địa chỉ Mac tương ứng. PC B sẽ gửi Unicast trực tiếp về PC A.

    ![](https://user-images.githubusercontent.com/52046920/181193245-1777c0be-b38b-4912-984d-186e26f77da9.png)
    * Sau khi có địa chỉ MAC thì lúc đó mới chuyển frame đến với switch và thực hiện như bình thường
* Sau khi quá trình trên diễn ra thông tin sẽ được lưu trữ vào bảng ARP để sử dụng cho những lần sau mà không cần phải phân giải địa chỉ thêm 1 lần nữa

![](https://user-images.githubusercontent.com/52046920/181193231-b68178ef-04e5-4940-8d46-7afc3367358d.png) 
# ***IX. Tìm hiểu Broadcast Domain trên mạng Ethernet LAN***
* Broadcas Domain là một vùng trong đó thông tin được gửi tới tất cả các thiết bị được kết nối. Thiết bị giới hạn broadcast domain là các router. Và cũng chính router tạo ra các broadcast domain. Như vậy mỗi một interface của Router là một broadcast domain.
![]()
* Trong 1 Broadcast domain thì chỉ được sử dụng 1 mạng (dải NETWORK duy nhất) duy nhất nếu sử dụng mạng khác nhau thì sẽ bị cô lập không giao tiếp được với các máy còn lại
* Router ngăn cách 2 Broadcast domain
![]()

# ***X. Cơ chế truyền Half Duplex và Full Duplex***
* Cơ chế full Duplex: các thiết bị kết nối với nhau thông quá switch thì có khả năng truyền dữ liệu full Duplex là các thiết bị vừa có thể truyền và nhận dữ liệu 1 cách đồng thời.
* Cơ chế half Duplex: Ta sẽ đi vào cơ chế Hub trước. 
    * Khác với cơ chế chuyển mạch của switch. Hub được coi là thiết bị lớp 1 và nó không hiểu được Ethernet header của frame để gửi đến đúng nơi nhận như switch mà nó chỉ hiểu được frame đi tới là các tín hiệu dưới dạng các bit 010101... . Vậy nên nó sẽ khuếch đại tín hiệu và gửi nó đến toàn bộ các cổng còn lại của nó trừ cổng vào nó dẫn đến việc ngốn tài nguyên và bảo mật do toàn bộ các máy trong mạng đều nhận được thông tin trong khi chỉ có 1 đích là cần nhận.
    * Cơ chế half Duplex tại 1 thời điểm chỉ có 1 thiết bị được truyền dữ liệu và các thiết bị khác không được truyền dữ liệu nữa. Half Duplex sẽ gâp ra nhược điểm chia sẻ bằng thông không tận dụng tối ưu được toàn bộ khả năng của cab và băng thông mạng. Càng nhiều thiết bị kết nối thì băng thông càng bị chia nhỏ
* Do đó để đảm bảo tốc độ trên hệ thống mạng nên sử dụng switch để có thể sử dụng cơ chế full Duplex

# ***XI. Tìm hiểu Collision Domain và cơ chế tránh đụng độ CSMA CD***
* Collision Domain xảy ra khi sử dụng hub. Sử dụng Hub thì chỉ có thể sử dụng cơ chế half Duplex mà cơ chế này là tại 1 thời điểm chỉ được 1 thiết bị truyền dữ liệu và khi xảy ra trường hợp 2 thiết bị cùng truyền dữ liệu khiến cho các dữ liệu có khả năng đụng độ. Collision Domain có thể hiểu nó là 1 vùng mà 2 thiết bị trong vùng này cùng gửi dữ liệu sẽ có nguy cơ đụng độ
* Để chống lại nguy cơ đụng độ xảy ra các thiết bị trong Collision Domain sẽ sử dụng cùng 1 cơ chế là Carrier Sense Multiple Access with Collision Detect(CSMA/CD). Cơ chế này được tự động kích hoạt trên các thiết bị đang hoạt động ở chế độ Half Duplex
* Theo phương pháp này, khi một máy tính muốn truyền một gói tin nó sẽ thực hiện các bước như sau 
    * Một thiết bị cần truyền sẽ dữ liệu lắng nghe đường truyền cho đến khi nào đường truyền Ethernet không còn bị chiếm.
    * Khi đường truyền Ethernet không còn bị chiếm, máy gửi bắt đầu gửi dữ liệu.
    * Máy gửi cũng bắt đầu lắng nghe để đảm bảo rằng không có xung đột xảy ra.
    * Nếu có xung đột, tất cả các máy trạm đã từng gửi ra dữ liệu sẽ gửi ra một tín hiệu nghẽn để đảm bảo tất cả các máy trạm đều nhận ra xung đột.
    * Sau khi tín hiệu nghẽn là hoàn tất, mỗi máy gửi của những dữ liệu bị xung đột sẽ khởi động một bộ định thời (timer được đề xuất ngẫu nhiên trên từng thiết bị và được đề xuất để các thiết bị cực kỳ quá xung đột nhau) và chờ hết khoản thời gian này sẽ cố gắng truyền lại. Những máy không tạo ra xung đột sẽ không phải chờ.
    * Sau khi các thời gian định thời là hết, máy gửi có thể bắt đầu một lần nữa với bước 1.
* Ta có thể phân biệt và xác định Broadcast domain và Collision Domain như sau
    * Broadcast domain được xác định với số cổng mà router kết nối mỗi cổng của router được tính là 1 Broadcasr domain
    * Mỗi cổng của switch sẽ được coi là 1 Collision Domain. Toàn bộ các thiết bị kết nối với hub thì được tính là 1 collision domain
    * Đặc biết cổng của router có thể được thiết lập là full duplex hoặc là half duplex nên nếu được thiết lập là full duplex thì cổng đó sẽ được gọi là 1 Broadcast domain và nếu được thiết lập là half duplex thì cổng đó sẽ được gọi là 1 collision domain
<!--



# ***XII.***
# ***XIII.***
-->