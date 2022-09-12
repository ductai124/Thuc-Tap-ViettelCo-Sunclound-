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

# TÌM HIỂU VỀ EIGRP 
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. EIGRP là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#ieigrp-l%C3%A0-g%C3%AC)
# [II. Đặc điểm EIGRP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#ii%C4%91%E1%BA%B7c-%C4%91i%E1%BB%83m-eigrp)
# [III. Nguyên lý hoạt động của EIGRP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#iiinguy%C3%AAn-l%C3%BD-ho%E1%BA%A1t-%C4%91%E1%BB%99ng-c%E1%BB%A7a-eigrp)
# [IV. Cấu hình EIGRP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#ivc%E1%BA%A5u-h%C3%ACnh-eigrp)
# [V. Hiệu chỉnh metric bằng Delay và Bandwidth](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#vhi%E1%BB%87u-ch%E1%BB%89nh-metric-b%E1%BA%B1ng-delay-v%C3%A0-bandwidth)
# [VI. Hiệu chỉnh Variance cân bằng tải theo tỉ lệ](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/23.EIGRP/README.md#vhi%E1%BB%87u-ch%E1%BB%89nh-variance-c%C3%A2n-b%E1%BA%B1ng-t%E1%BA%A3i-theo-t%E1%BB%89-l%E1%BB%87)
***
# ***I.	EIGRP là gì***
* EIGRP là Enhance Interio Gateway Routing Protocol. Là một giao thức định tuyến do CIsco phát triển, độc quyền trên các thiết bị Cisco.
* Là một dạng giao thức Hybrid Routing. Không sử dụng thuật toán Distance-vector Bellman-Ford mà sử dụng thuật toán riêng DUAL.
# ***II.	Đặc điểm EIGRP***
* Hội tụ nhanh(Rapid Convergence) do sử dụng giao thức DUAL
* Hỗ trợ cơ chế classless và có 100% cơ chế chống loop
* Dễ cấu hình
* Hỗ trợ tốt khả năng cập nhật Routing Table. EIGRP không gửi Routing Table định kỳ mà nó chỉ gửi cho nhau 1 lần, sau đó nó chỉ gửi những cập nhật thay đổi.
* Có khả năng cân bằng tải qua các đường không bằng nhau

![](https://user-images.githubusercontent.com/52046920/189083345-33232553-8974-4ef9-b5f0-f933aaaa6277.png)
* Hỗ trợ VLSM
* Bảo tồn bằng thông, sử dụng băng thông hiệu quả: Do chỉ gửi Routing Table định kỳ mà chỉ gửi khi có thây đổi nên bằng thông chỉ được sử dụng ở mức tối thiểu
* Sử dụng cổng 88
* Không sử dụng boradcast mà sử dụng multicast hoặc unicast trong tùy từng trường hợp cụ thể(EIGRP: 223.0.0.10)
* Đây là một giao thức cực kỳ nhiều ưu điểm tuy nhiên việc chỉ độc quyền trên Cisco là 1 nhược điểm khá lớn của nó khi nó không thể chạy trên các sản phẩm khác không thuộc nhà Cisco.
# ***III.	Nguyên lý hoạt động của EIGRP***
* EIGRP sử dụng 3 bảng sau
    * Neighbor table: Liệt kê các nút neighbor kết nối trực tiếp. sau khi xây dựng xong nó sẽ gửi qua bTypology Table.
    * Topology Table: Router lưu lại Neighbor table. Sử dụng DUAL để tính ra đường đi tốt nhất. Sau đó gửi qua Router table.
    * Router table: Làm nhiệm vụ định tuyến
* Router trao đổi 5 bản tin:
    * Hello: Thiết lập neighbor giữa các Router chạy EIGRP. Khi các neighbor được thiết lập thì mới gửi định tuyến cho nhau được
    * Reply: Trả lời xác nhận thông tin
    * Request: Gửi yêu cầu update Neighbor Table
    * Update: Cập nhật Neighbor Table
    * ACK: là thông tin xác nhận. Nếu 1 ACK không nhận được sau 16 lần truyền lại thì Router xác định đã chết(ACKnowledgement).

* Các neighbor sẽ gửi định kỳ 5s gói tin hello. Thời gian giữ gói tin là 15s(holdtimer). Sau 15s không có gói tin thì coi như neighbor đã chết. Hello và holdtimer ở 2 interface có thể khác nhau.
* Ta có thể thay đổi thông sô trên bằng câu lệnh
```cisco
R1(config-if)#ip hello-interval eigrp 1
R2(config-if)#ip hold-time eigrp 4

```
* Lưu ý là chúng ta phải vào tất cả các cổng giao tiếp trên hệ thống mạng chạy EIGRP để hiệu chỉnh timer và hold timer đồng nhất giữa các thiết bị.

* TOPOLOGY

![](https://user-images.githubusercontent.com/52046920/189083349-abfc212e-30f9-4f55-bc12-a99336c1a91f.png)
* Trên 1 đường đi có 2 giá trị Metric đi kèm:
    * FD(Feasible DIstance): Tính từ đầu tới đích(R đến R4 = 1000 là những đường màu đỏ trên hình)
    * AD(Adverrtised Distance): Tính từ router Neighbor đến đích (R1 đến R4, là những đường màu đen trên hình). Chú ý từ AD này không phải Administrative Distance
* Bảng Topology

|Network|Next hop|FD|AD||
|---|---|---|---|---|
|A|R1|3000|900|Feasible Successor|
|A|R2|2000|1100||
|A|R3|1000|800|Successor|

* Có đường đi ngắn nhất được gọi là Successor là đường có FD min. Các đường có AD nhỏ hơn FD min được gọi là Feasible Successor điều này để việc lặp sẽ không bao giờ xảy ra. Đây sẽ là đường dự phòng cho đường successor
* Đường Successor sẽ đưa vào Routing Table còn Feasible Successor sẽ làm dự phòng.

# ***IV.	Cấu hình EIGRP***
* Các câu lệnh cấu hình
```cisco
\\\Chỉ số AS, các router cùng vùng mạng sẽ phải cấu hình cùng AS
R1(config)#router eigrp [AS]

R1(config-router)#network [lớp mạng cần quảng bá] [Wildcard Mask]

\\\Nếu muốn chỉ định IP rõ ràng thì cấu hình 
R1(config-router)#network [Địa chỉ IP] 0.0.0.0
```
* Ví dụ: Cho mô hình

![](https://user-images.githubusercontent.com/52046920/189083367-fd5784e4-b467-4b16-bff3-692e47efb46a.png)
* Cấu hình EIGRP cho 3 Router
* Tại R1
```cisco
R1(config)#router eigrp 100
R1(config-router)#network 192.168.1.0 0.0.0.255
R1(config-router)#network 192.168.2.0 0.0.0.255
R1(config-router)#no auto-summary
```

* Tại R2
```cisco
R2(config)#router eigrp 100
R2(config-router)#network 192.168.2.0 0.0.0.255
R2(config-router)#network 192.168.3.0 0.0.0.255
R2(config-router)#network 172.168.0.0 0.0.0.255
R2(config-router)#no auto-summary
```

* Tại R3
```cisco
R3(config)#router eigrp 100
R3(config-router)#network 192.168.3.0 0.0.0.255
R3(config-router)#network 10.0.0.0 0.255.255.255
R3(config-router)#no auto-summary 
```

* Kiểm tra các  route học được từ EIGRP

```cisco
R1#show ip route eigrp
```

![](https://user-images.githubusercontent.com/52046920/189083358-b778c1b5-d753-4453-aab7-1798399a25de.png)

![](https://user-images.githubusercontent.com/52046920/189083362-6e068a5d-d6c3-4c0a-a7ab-623383f7666e.png)

![](https://user-images.githubusercontent.com/52046920/189083365-44451dd6-15c2-49a4-99df-05f9a9c00024.png)

* Kiểm tra các cổng đang tham gia vào định tuyến EIGRP

```cisco
R1#show ip eigrp interfaces
```
* Kiểm tra các nút hàng xóm
```cisco
R1#show ip eigrp neighbors
```

* Cấu hình default route thực hiện câu lệnh
```cicso
R1(config)#router eigrp 100
R1(config-router)#redistribute static 
```
* Tuy nhiên trước khi thực hiện câu lệnh trên phải thực hiện cấu hình default route tĩnh trước đã
```cisco
R1(config)#ip route 0.0.0.0 0.0.0.0 123.0.0.2 
```
<!--
* Hiệu chỉnh hold-timer và hello timer
```cisco
R1(config)#ip hello-interval eigrp 1
R1(config)#ip hold-time eigrp 3
```
--->

# ***V.	Hiệu chỉnh metric bằng Delay và Bandwidth***
* AD (Administrative Distance) là tham số được căn cứ để chọn đường đi tốt hơn. Nó được xét đến trước khi xét đến metric. Với các giao thức định tuyến khác nhau thì sẽ có chỉ số AD khác nhau ví dụ: OSPF có AD là 110, EIGRP có AD là 90. Trong routing table nếu có nhiều đường đi đến 1 mạng thì sẽ chỉ hiển thị đường đi tối ưu nhất(AD nhỏ nhất và metric nhỏ nhất).
* Chỉ số metric của giao thức EIGRP phụ thuộc vào Delay, Bandwidth, Load(Tải) và reliability(Độ tin cậy).
* Kiểm tra các chỉ số trên bằng câu lệnh
```cisco
R1#show interface g0/0
```

![](https://user-images.githubusercontent.com/52046920/189563317-f49479a2-9ab8-49ae-a80f-f260a684ab80.png)
* Load(Tải) và reliability(Độ tin cậy) là cứ 5 phút router sẽ tự tính toán lại do đó nếu cho chúng tham gia vào qua trình tính metric thì sẽ không được tối ưu. EIGRP cho phép ta được chọn các tham số được tham gia vào tính toán metric và mặc định sẽ chỉ có 2 tham số là Delay và Bandwidth là tham gia vào quá trình tính toán metric
* Cổng thức tính metric:

![](https://user-images.githubusercontent.com/52046920/189563319-b3afde65-5673-465b-9f32-e57e6053474e.png)
* Thời gian là microsecond
* Bandwidth tính theo Kbps
* Bandwidth min là băng thông nhỏ nhất trong các chặng từ nguồn đến đích. 
* Tổng delay của toàn bộ các chặng từ nguồn đến đích
* Ví dụ

![](https://user-images.githubusercontent.com/52046920/189563320-c2abfa2d-c452-432f-9665-170a6b55b4ba.png)
* Đây là băng thông và delay của các interface đi ra và hướng tới đích
* có thể kiểm tra metric đến mạng đích bằng câu lệnh
```cisco
R1#show ip eigrp topology 10.0.0.0

\\\10.0.0.0 là địa chỉ mạng đích
```
![](https://user-images.githubusercontent.com/52046920/189563322-a0e2ced0-6a53-4115-a03f-6211bf382a21.png).

* Hiệu chỉnh delay và bandwidth bằng câu lệnh bằng câu lệnh
```cisco
R1(config)#interface g0/0
R1(config-if)#delay 83661

R1(config-if)#bandwidth 1000
```
* Interface này phải là interface đi ra và hướng đến đích.
* Việc hiệu chỉnh băng thông thì sẽ phải hiệu chỉnh băng thông nhỏ nhất (Bandwidth min) thì chỉ số metric mới có thay đổi hoặc hiệu chỉnh 1 băng thông của 1 cổng trên tuyến đường đi và biến nó trở thành Bandwidth min mới
* Ta có thể thiết lập thêm các tham số khác tham gia vào việc hiệu chỉnh metric như sau
```cicso
R1(config)#metric-weight 0 K1 K2 K3 K4 K5

/// K1-K5 nếu muốn thiết lập chúng tham gia vào hiệu chỉnh metric thì để giá trị là 1, không thì để giá trị là 0
///Cụ thể các Router sẽ được cấu hình mặc định như sau
R1(config)#metric-weight 0 1 0 1 0 0

```

|Default|K1|K2|K3|K4|K5|
|-|-|-|-|-|-|
|Tương ứng với giá trị tham gia hiệu chỉnh|Bandwidth|Load|Delay|Reliability|Reliability|
* Kiểm tra các giá trị K1-K5 được thiết lập
```cisco
R1#show ip protocols 
```

![](https://user-images.githubusercontent.com/52046920/189599868-6f1bc3fb-1e09-4eac-a811-8e134e81a88f.png)
# ***V.	Hiệu chỉnh Variance cân bằng tải theo tỉ lệ***
*Ví dụ:  

![](https://user-images.githubusercontent.com/52046920/189083349-abfc212e-30f9-4f55-bc12-a99336c1a91f.png)
* Bảng Topology

|Network|Next hop|FD|AD||
|---|---|---|---|---|
|A|R1|3000|900|Feasible Successor|
|A|R2|2000|1100||
|A|R3|1000|800|Successor|

* Cân bằng tải theo tỉ lệ chỉ có hiệu lực trên Successor và Feasible Successor. vậy nên nếu muốn tất cả các đường đều được cân bằng tải theo tỉ lệ thì ta phải căn chỉnh lại chỉ số metric hoặc FD min sao cho đường đi có next hope là R2 cũng trở thành đường Feasible Successor.
* Hiệu chỉnh tham số variance
```cisco
R1(config)#router eigrp 100
R1(config-router)#variance 2

///variance có thể hiệu chỉnh giá trị từ 1-128
```
* Nguyên tắc cân bằng tải theo tỉ lệ: Nếu ***FD Feasible Successor < variance X FDmin*** thì đường Feasible Successor sẽ được cân bằng tải theo tỉ lệ cùng với đường Successor theo tỉ lệ giao thức tự sắp xếp.
* Ví dụ như bài trên và ta đã thiết lập variance bằng 2 có:

    * FD của Feasible Successor = 3000. 
    * Variance X FDmin = 1000 X 2 = 2000.
    * 3000 > 2000 nên không thể cân bằng tải theo tỉ lệ ở đường Feasible Successor vậy ta phải thiết lập variance > 3 thì lúc này Variance X FDmin = 1000 X 4 = 4000 > 3000. lúc này thì đường Feasible Successor mới có thể cân bằng tải theo tỉ lệ cùng với đường Successor.
