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
# [I. EIGRP là gì]()
# [II. Đặc điểm EIGRP]()
# [III. Nguyên lý hoạt động của EIGRP]()
# [IV. Cấu hình EIGRP]()
## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
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
* TOPOLOGY

![](https://user-images.githubusercontent.com/52046920/189083349-abfc212e-30f9-4f55-bc12-a99336c1a91f.png)
* Trên 1 đường đi có 2 giá trị Metric đi kèm:
    * FD(Feasible DIstance): Tính từ đầu tới đích(R đến R4 = 1000)
    * AD(Adverrtised Distance): Tính từ router Neighbor đến đích (R1 đến R4). Chú ý từ AD này không phải Administrative Distance
* Bảng Topology

|Network|Next hop|FD|AD||
|---|---|---|---|---|
|A|R1|1000|900|Successor|
|A|R2|2000|1100||
|A|R3|3000|800|Feasible Successor|

* Có đường đi ngắn nhất đưcọ gọi là Successor là đường có FD min. Các đường có AD nhỏ hơn FD min được gọi là Feasible Successor điều này để việc lặp sẽ không bao giờ xảy ra.
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
```

* Tại R2
```cisco
R1(config)#router eigrp 100
R1(config-router)#network 192.168.2.0 0.0.0.255
R1(config-router)#network 192.168.3.0 0.0.0.255
R1(config-router)#network 172.168.0.0 0.0.0.255
```

* Tại R3
```cisco
R1(config)#router eigrp 100
R1(config-router)#network 192.168.3.0 0.0.0.255
R1(config-router)#network 10.0.0.0 0.255.255.255
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
* Cấu hình default route thực hiện câu lệnh
```cicso
R1(config)#router eigrp 100
R1(config-router)#redistribute static 
```
<!--
* Hiệu chỉnh hold-timer và hello timer
```cisco
R1(config)#ip hello-interval eigrp 1
R1(config)#ip hold-time eigrp 3
```
--->