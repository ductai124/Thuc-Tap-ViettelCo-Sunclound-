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

# TÌM HIỂU VỀ RIP
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. RIP là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#irip-l%C3%A0-g%C3%AC)
# [II. Đặc điểm RIP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#ii%C4%91%E1%BA%B7c-%C4%91i%E1%BB%83m-rip)
# [III. Nguyên lý hoạt động](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#iiinguy%C3%AAn-l%C3%BD-ho%E1%BA%A1t-%C4%91%E1%BB%99ng)
# [IV. Các bộ quy tắc chống loop](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#ivc%C3%A1c-b%E1%BB%99-quy-t%E1%BA%AFc-ch%E1%BB%91ng-loop)
# [V. RIPv1 và RIPv2](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#vripv1-v%C3%A0-ripv2)
## &ensp; [1. RIPv1](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#1-ripv1)

## &ensp; [2. RIPv2](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#2-ripv2)

## &ensp; [3. So sánh RIPv1 và RIPv2](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#3-so-s%C3%A1nh-ripv1-v%C3%A0-ripv2)

# [VI. Major Network](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#vimajor-network)
# [VII. Cấu hình RIP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/22.RIP/README.md#viic%E1%BA%A5u-h%C3%ACnh-rip)
***
# ***I.	RIP là gì***
* Routing Information Protocol(RIP) là một giao thức định tuyến động và được phân loại là  một giao thức IGP (Interior Gateway Protocols-Giao thức định tuyến trong) và thuộc loại giao thức Distance Vector(Định tuyến vector). RIP sử dụng  giá trị đo lường là Hop count(Số bước nhảy) từ nguồn đến đích.
* RIP hoạt động như sau: Router đều đặn gửi toàn bộ Routing table ra các nút xung quanh nó cứ lan truyền ra các Router xung quanh theo chu kỳ 30 giây. Các router nhận được thông tin sẽ cập nhật lại, tính toán và tiếp tục quảng bá cho các nút xung quanh.
* RIP hiện có 2 phiên bản RIPv1 và RIPv2. RIPv2 đang được sử dụng rộng rãi hơn do nó thừa hưởng
# ***II.	Đặc điểm RIP***
* RIP sử dụng hop-count là 1 giá trị định tuyến để tìm kiếm đường đi tốt nhất giữa 2 nút. Nó là số lượng Router mà 1 gói tin phải đi qua cho đến khi đến được đích. Giới hạn Hop-count tối đa là 16 để tránh trường hợp lặp vô hạn. Khi router nhận được thông tin của nút láng giềng nó sẽ tăng chi số Hop+1 và cập nhật vào routing table.
* RIP sử dụng thuật toán vector khoảng cách: là thuật toán định tuyến tính toán đường đi ngắn nhất giữa các cặp nút trong mạng. Cụ thể thuật toán sử dụng là Bellman-Ford.
* RIP có bộ các timer gồm
    * Route update timer
    * Routing invalid timer
    * Holddown timer
    * Route flush timer
* Các timer trên sẽ được làm rõ ở các phần sau
# ***III.	Nguyên lý hoạt động***
* Khi một router xuất hiện nó gửi Request Message đến mọi nút khác
* Các nút khi nhận được sẽ gửi lại Response Message với bảng định tuyến của nó
* Bảng định tuyến gồm nhiều bản ghi, mỗi bản ghi lưu: đích, khoảng cách đến đích, nút tiếp theo cần đi qua.	
* Mỗi nút xử lý bảng định tuyến của mình khi nhận được 1 bảng định tuyến theo luật sau:	
	* Nếu không có đích nào trong bảng định tuyến của nút tương ứng với các đường đi nhận được sẽ thêm đích mới vào bảng định tuyến, kèm nút đã cung cấp thông tin (làm next hop)
	* Nếu đã có đích nhận được trong bảng định tuyến và đường đi mới tốt hơn (ít hop hơn) sẽ cập nhật khoảng cách mới theo Bellman-ford. 
	* Nếu đã có đích nhận được trong bảng định tuyến và đường đi mới nhận được không tốt bằng đường đã biết sẽ cập nhật bản ghi cho đích này với khoảng cách = 16 nút (tương đương vô cùng). Việc quy định metric này giúp giải quyết được vấn đề lặp. Tuy vậy các gói tin vẫn gếp tục được vận chuyển theo đường đi cũ.
	    * Holddown timer được khởi tạo để bỏ qua tất cả các cập nhật từ các router khác cho đích này
	    * Sau khi Holddown timer hết hạn các thông gn từ các router khác cho đường đi này mới được cập nhật
* Trao đổi bảng định tuyến(broadcast)
	* Định kỳ
    	* Các routers chạy RIP sẽ broadcast một/một số thông điệp cập nhật việc định tuyến thường xuyên (30s).
	    * Các thông tin được lấy từ broadcast gồm: Một tập hợp các cặp, trong đó mỗi cặp chứa một địa chỉ mạng đích IP và một số nguyên là khoảng cách hop đến mạng đó
	* Sự kiện
    	* Mỗi khi thay đổi sẽ gửi thông tin đến cho các nút ở gần
	    * Các nút (Router) neighbor nhận được thông tin sẽ cập nhật lại broadcast
* Ví dụ:
* giả sử có 3 router R1, R2, R3 khi chưa cấu hình định tuyến bảng định tuyến của các router sẽ như sau

![](https://user-images.githubusercontent.com/52046920/188395155-a9e51fa6-b4ac-400a-9459-324859c41293.png)
* Tất cả kết nối trực tiếp metric sẽ = 0 
* Sau khi định tuyến RIP cho các Router cơ chế sẽ như sau:
	* R1 gửi thông tin định tuyến cho R2
	* R2 nhận được thông tin định tuyến thấy mạng 192.168.1.0/24 chưa có trong routing table của mình nên nó tiến hành điền mạng này vào bảng định tuyến của mình và đẩy metric lên thêm 1 chỉ số. Sau đó nó tiến hành gửi toàn bộ routing table của nó cho R3.
	* R3 nhận thông tin của R2 và điền các mạng còn thiếu vào trong ip routing đồng thời đẩy metric lên thêm 1 chỉ số

	![](https://user-images.githubusercontent.com/52046920/188398830-234f9c40-8f5e-4307-aa6b-82e8cf7b5529.png)
	* 192.168.1.0/24 is directly connected, Gig0/0, metric 1 có nghĩa là mạng 192.168.1.0/24 được học từ cổng Gig0/0 và phải đi qua 1 Router mới đến được đích. Tương tự ở R3 192.168.1.0/24 is directly connected, Gig0/0, metric 2 mạng 192.168.1.0/24 được học từ cổng Gig0/0 và phải đi qua 2 Router mới đến được đích,...
	* Tương tự R3 sẽ gửi lại thông tin bảng định tuyến cho R2 và R2 sẽ gửi lại thông tin bảng định tuyến cho R1 ta được kết quả

	![](https://user-images.githubusercontent.com/52046920/188399293-11d8e044-5bfc-4cea-8a48-88eef5dddffd.png)
	* định tuyến hoàn thành
* Do có nguyên lý hoạt động như vậy sẽ xảy ra loop như sau
	* xết trường hợp mạng 192.168.1.0/24 đột ngột bị ngắt kết nối ngay lập tức R1 sẽ xóa ngày mạng này ra khỏi bảng định tuyến của mình. 

	![](https://user-images.githubusercontent.com/52046920/188404844-f6688583-4dd5-41ff-9990-e8613e5b8a20.png)

	![](https://user-images.githubusercontent.com/52046920/188404855-769895e6-092b-48ea-814a-9aa25d6f2658.png)
	* Tuy nhiên trong vòng 30s sau hoặc có thể ngắn hơn tùy vào thời gian R1 bị xóa mạng 192.168.1.0/24 R2 lại gửi cho R1 thông tin định tuyến của mình mà mạng 192.168.1.0/24 không có trong ip routing của R1 vậy nên nó lại thêm và và tăng metric lên

	![](https://user-images.githubusercontent.com/52046920/188405164-a9c99462-9012-48f7-ba05-17014d1e19c5.png)
	* Sau 30s R1 gửi thông tín đển R1 mạng 192.168.1.0/24 sẽ lại được thêm vào R2 với metric mới do R2 không kết nối trực tiếp với mạng đó và nó học của R1 nên metric lại phải + 1.

	![](https://user-images.githubusercontent.com/52046920/188404856-928aa366-431f-46df-868f-5916b77c28b4.png)
	* Vòng lặp cứ lặp đi lặp lại vô tận.
* Để giải quyết được vấn đề trên sinh thì các kỹ thuật, bộ quy tắc phòng tránh loop được ra đời
# ***IV.	Các bộ quy tắc chống loop***
* Để giải những vấn đề này RIP sử dụng những kỹ thật sau:
	* ***Split horizon update*** (kỹ thuật cắt hàng ngang): khi 1 tuyến đường học được từ một Router thì tuyến đường đó sẽ không quảng cáo lại trên Router đó. ví dụ: R2 học mạng 192.168.1.0/24 từ R1 thì R2 se không quảng bá lại mạng này đến R1 nữa. Thường được bật tự động khi cấu hình
	* ***Router poisoning***: khi tuyến đương bị lỗi router sẽ gửi cật nhật về định tuyến đó với giá trị metric là 16 làm cho con đường này không thể truy cập và sẽ không còn được sử dụng cho định tuyến dữ liệu.
	* ***Poison reverse***: tuyến đường học được từ cổng giao tiếp sẽ được quảng bá ngược lại cổng giao tiếp đó nhưng được đánh dấu với giá trị số metric là 16.
	* ***Triggered update***: Split horizon có thể xử lý được trường hợp chỉ có 2 router liên quan đến việc lặp vô hạn, nếu có từ 3 router trở lên thì sẽ sử dụng Triggered update:
		* Triggered update yêu cầu các router phải quảng bá ngay bảng định tuyến (mà không chờ đến chu kỳ update) mỗi khi một tuyến đường có sự thay đổi metric
	* ***Sử dụng các Timer***: RIP sử dụng một số bộ đếm thời gian kiểm soát việc cập nhật các gói tin. Các bộ đếm đều giảm dần đến 0. Điều chỉnh các timer sẽ giúp ngăn ngừa lặp.
* RIP sử dụng các timer sau:
    * ***Route update timer***: là thời gian thông tin routing của toàn bộ bảng định tuyến của các router với các cổng giao tiếp đang bật. Định kỳ 30s
    * ***Routing invalid timer***: Khoảng thời gian xác định 1 tuyến đường không hợp lệ. Nếu sau khoảng thời gian Hold time mà không nhận được update thì Routing invalid Timer sẽ chạy. Khi nó chạy hết khoảng thời gian đó Router sẽ gửi thông tin đến các nút thông báo tuyến đường không hợp lệ
    * ***Holddown timer***: Sử dụng Khi có thông tin routing bị thay đổi. Router nhận thông tin thay đổi, nó đặt vào đường đi đó trạng thái hold-down. Router sẽ không nhận thông tin, quảng bá thông tin đó trong khoảng thời gian holddown timer. Khi holddown timer chạy hết thì bắt đầu nhận thông tin và quảng bá thông tin như bình thường. Mặc định là 180s.
    * ***Route flush timer***: là thời gian đường đi ko hợp lệ bị xóa khỏi routing table. Routing invalid timer phải nhỏ hơn Route flush timer. 

![](https://1.bp.blogspot.com/-8qCmSur-hDY/X1EKvkIW4HI/AAAAAAAAC1k/AoTuo_LoQqoorjMA_a-oOUSjVdlAg66FwCLcBGAsYHQ/w640-h249/RIP%2BTimers.webp)

# ***V.	RIPv1 và RIPv2***
## ***1. RIPv1***
* Là giao thức định tuyến Interior Gateway Protocols(IGP) và thuộc loại classfull
* Giao thức RIPv1 không gửi kèm subnetmask trong bản tin routing
* Đặc điểm RIPv1:
	* Là một giao thức định tuyến theo véctơ khoảng cách, sử dụng số lượng hop làm thông số định tuyến.
	* Giá trị hop tối đa là 16.
	* Thời gian giữ chậm (hold-down) cũng là 180 giây.
	* Sử dụng cơ chế split horizon, triggered update, reverse poison để chống lặp vòng.

* Định dạng gói tin RIPv1

![](https://user-images.githubusercontent.com/52046920/188418887-ccb545ff-5415-4506-b913-fb103da8c06d.png)
* Command xác định các thao tác thực hiện và cũng phân biệt gói tin request hay response.
* Version chứa các phiên bản hoạt động của RIP
* Must be zero  được đặt theo chính giá trị mặc định của nó là 0. Trường này được thêm vào để cung cấp sự tương thích với các phiên bản RIP khác nhau
* Address-family identifier (AFI) được sử dụng để đặc tả giao thức được định tuyến sử dụng. Ví dụ giá trị của AFI cho giao thức IP là 2
* IP Address chỉ địa chỉ IP của đích/mạng đích
* Metric chỉ số hop cần phải nhảy để tới đích. Giá trị cho đường đi hợp lệ từ 1-15, và 16 cho poisoning route.

## ***2. RIPv2***
* RIPv2 là giao thức định tuyến Interior Gateway Protocols(IGP) và thuộc loại classess
* RIPv2 có thông tin về mặt nạ mạng con và hỗ trợ các mạng con có độ dài mặt nạ khác nhau.
* RIPv2 là bản được phát triển từ RIPv1 nên có các đặc điểm như RIPv1: 
	* Là một giao thức định tuyến theo véctơ khoảng cách, sử dụng số lượng hop làm thông số định tuyến.
	* Giá trị hop tối đa là 16.
	* Thời gian giữ chậm (hold-down) cũng là 180 giây.
	* Sử dụng cơ chế split horizon, triggered update, reverse poison để chống lặp vòng.
* RIPv2 đã khắc phục được những điểm giới hạn của RIPv1.
	* RIPv2 có gửi mặt nạ mạng con đi kèm với các dịa chỉ mạng trong thông tin định tuyến. Nhờ đó mà RIPv2 có thể hỗ trợ IP không phân lớp và các mạng con có mặt nạ khác nhau.
	* RIPv2 có hỗ trợ việc xác minh thông tin định tuyến.
	* RIPv2 gửi thông tin định tuyến theo địa chỉ đa hướng 244.0.0.9.
* Cấu trúc bản tin của RIPv2 cho phép mang nhiều thông tin hơn RIPv1
* Một số đặc tính sau đây là những dấu hiệu lớn nhất được bổ sung vào RIPv2:
	* Xác thực các gói tin RIP với router.
	* Hỗ trợ mặt nạ con.
	* Địa chỉ IP bước kế tiếp.
	* Bản tin quảng bá nhờ địa chỉ multicast.
* RIPv2 không thể tương thích ngược được với RIPv1

* Định dạng gói tin RIPv2
![](https://user-images.githubusercontent.com/52046920/188418898-6a855a76-70d7-4994-8db7-6fcc63a20e4b.png)

* Command, Version, Must be zero, AFI, IP Address và Metric tương tự như RIPv1
* Route tag (Nhãn đường đi): Cung cấp một phương thức phân biệt giữa bộ định tuyến nội bộ (sử dụng giao thức RIP) và các bộ định tuyến ngoài (sử dụng các giao thức định tuyến khác).
* Subnet mask: Chứa đựng mặt nạ mạng con cho các bộ định tuyến.
* Next hop: Cho biết địa chỉ IP của router tiếp theo mà gói tin có thể được chuyển tiếp đến.

## ***3. So sánh RIPv1 và RIPv2***

![](https://user-images.githubusercontent.com/52046920/188423861-897ba3cf-71e7-4350-adbd-5f44d329b478.png)

# ***VI.	Major Network***
* Là một mạng lớn chưa bị chia nhỏ. Cụ thể nó là 1 địa chỉ IP thuộc 1 lớp nào đó với frefix mặc định ví dụ lớp A có frefix là 8, lớp B có frefix là 16 và lớp C có frefix là 24.
* Ví dụ: Phân biết giữa Major Network và subnet

|Major Network|Subnet|
|---|---|
|10.0.0.0/8|10.0.0.0/24|
|172.16.0.0/16|172.16.0.0/24|
|192.168.1/24|192.168.1.0/27|

# ***VII.	Cấu hình RIP***
* Câu lệnh cấu hình như sau
```cisco
R1(config)#router rip

\\\Muốn sử dụng version 2 thì sử dụng câu lệnh
R1(config-router)#version 2

\\\Major Network của các cổng giao tiếp mà Router đang sử dụng
R1(config-router)#network 192.168.1.0

\\\Tắt giao thức này nhằm trường hợp muốn các Router láng giềng có thể học được các subnet của cùng 1 Major Network
R1(config-router)#no auto-summary
```
* Trường hợp tắt auto-summary như sau: Ví dụ nếu R1 có 2 mạng 172.16.10.0/24 và 172.16.20.0/24 cùng có Major Network là 172.16.0.0/16. Nếu không tắt auto-summary thì các Router láng giềng sẽ chỉ học được mạng Major Network do R1 gửi mà thôi, còn nếu tắt tính năng này đi thì các Router láng giềng có thể học được cả 2 subnet trên


* ví dụ cho mô hình:

![](https://user-images.githubusercontent.com/52046920/188530561-f1ec9ae1-f93a-491d-b9e6-332669e3d2ed.png)
* Cấu hình định tuyến RIP cho cả 3 Router như sau
* Tại R1
```cisco
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#network 192.168.1.0
R1(config-router)#network 192.168.2.0
R1(config-router)#no auto-summary
```
* Tại R2
```cisco
R2(config)#router rip
R2(config-router)#version 2
R2(config-router)#network 192.168.2.0
R2(config-router)#network 192.168.3.0
R2(config-router)#network 192.168.5.0
R2(config-router)#no auto-summary
```

* Tại R3
```cisco
R3(config)#router rip
R3(config-router)#version 2
R3(config-router)#network 192.168.3.0
R3(config-router)#network 192.168.4.0
R3(config-router)#no auto-summary
```

* Kiểm tra các Major Network sử dụng học được từ RIP
```cisco
R1#show ip route rip
```
* Tại R1

![](https://user-images.githubusercontent.com/52046920/188530541-c3b85ae2-9026-4a55-835a-9942b249987a.png)
* Tại R2

![](https://user-images.githubusercontent.com/52046920/188530548-0b9734a3-2b70-434b-b260-76ad6bff0e02.png)
* Tại R3

![](https://user-images.githubusercontent.com/52046920/188530550-53d68eda-5be3-4ebb-a45e-d04adcf9f4fa.png)
* Kiểm tra trong bảng định tuyến
```cisco
R1#show ip route
```
* Tại R1

![](https://user-images.githubusercontent.com/52046920/188530553-dac4ac86-8e5e-457e-a80f-b04fe96c17cf.png)
* Tại R2

![](https://user-images.githubusercontent.com/52046920/188530554-e2d0a067-3643-43de-9c3f-d256ed6b3c59.png)
* Tại R3

![](https://user-images.githubusercontent.com/52046920/188530558-45583957-fcd7-4ce2-9825-ac2860560356.png)

## Quảng bá default route trong giao thức RIP
* Được sử dụng khi muốn gửi dữ liệu trong mạng nội bộ ra ngoài Internet. RIP sẽ giải quyết được hạn chế của định tuyến tĩnh như nếu có thay đổi gì ở interface đi ra ngoài mạng thì sẽ phải cấu hình lại default route còn RIP sẽ tự động sửa đổi lại.
* Ví dụ:

![](https://user-images.githubusercontent.com/52046920/188533772-5b3bd3b4-a050-4ba5-9b58-cf8f49d3a5e5.png)
* R3 là Router kết nối ra ngoài mạng và nếu các router khác muốn kết nối ra ngoài mạng thì phải cấu hình cho R3 default route. Các router muốn ra ngoài mạng sẽ gửi dữ liệu cho R3 và được R3 chuyển tiếp ra ngoài internet
* Câu lệnh cấu hình như sau
```cisco
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#network 192.168.1.0

\\\Cấu hình Default Route
R1(config-router)#default-information originate
R1(config-router)#no auto-summary
```

* Kiểm tra RIP học được

![](https://user-images.githubusercontent.com/52046920/188533774-397d2a39-78f3-4f6c-99c9-67cbc017802e.png)


