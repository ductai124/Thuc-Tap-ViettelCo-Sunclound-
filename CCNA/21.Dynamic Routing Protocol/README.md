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

# TÌM HIỂU VỀ DYNAMIC ROUTING
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Dynamic Routing là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/21.Dynamic%20Routing%20Protocol/README.md#idynamic-routing-l%C3%A0-g%C3%AC)

# [II. Phân loại Dynamic Routing Protocol](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/21.Dynamic%20Routing%20Protocol/README.md#iiph%C3%A2n-lo%E1%BA%A1i-dynamic-routing-protocol)
***
# ***I.	Dynamic Routing là gì***
* Dynamic Routing là định tuyến động.
* Định tuyến động là loại định tuyến mà trong đó các router sẽ thực hiện định tuyến tự động bằng các giao thức mà không cần phải thiết lập thủ công chỉ ra từng đường như định tuyến tĩnh. Tự chạy một phương thức tính toán nào đó để xác định xem để đi đến các mạng này thì phải sử dụng đường đi nào là tối ưu.
* Được sử dụng trên Internet hoặc môi trường mạng quá rộng lớn mà việc định tuyến tĩnh là khó khăn 
# ***II.	Phân loại Dynamic Routing Protocol***
* Có 2 loại giao thức định tuyến dộng là :
    * Exterior Gateway Protocols(EGP): Định tuyến các thiết bị trong cùng 1 vùng(Các hệ thống khác nhau, công ty khác nhau). Thường được dùng định tuyến trên Internet. giao thức tiêu biểu là BGP(Border Gateway Protocol)
    * Interior Gateway Protocols(IGP): Định tuyến các thiết bị không nằm trong 1 vùng(Cùng 1 hệ thống, công ty ). Được sử dụng để định tuyến các thiết bị trong cùng 1 hệ thống, công ty. Giao thức tiêu biểu có RIP(Routing Information Protocol), OSPF(Open Shortest Path First) là giao thức chuẩn quốc tế và EIGRP(Enhance Interio Gateway Routing Protocol) là giao thức độc quyền của cisco và chỉ chạy trên các thiết bị cisco. Có nhiều cách phân loại giao thức IGP. Giao thức phân loại dựa theo thuật toán định tuyến sử dụng chia thành 3 loại:
        * Distance-vector: Sử dụng thuật toán vector khoảng cách Bellman-Ford. Các router sẽ gửi cho các nút láng giếng của nó toàn bộ routing table định kỳ. Dựa vào đó và sử dụng thuật toán vector khoảng cách để tính toán đường đi tốt nhất. Giao thức tiêu biểu là RIP. Loại định tuyến này có khả năng xảy ra lặp vậy nên cần 1 bộ quy tắc chống lặp.
        * Link-state: Sử dụng thuật toán Dijkstras hay còn gọi là thuật toán tìm đường đi ngắn nhất(SPF-Shotesst Path First). Các router sẽ gửi bản tin trạng thái đường liên kết LSA(Link-state Advertisement) là 1 gói dữ liệu mạng thông tin định tuyến cho nhau. Việc tính toán định tuyến thì  thì sẽ sử dụng thuật toán Dijkstras để tính toán.
        * Hybrid: là kết hợp của 2 loại trên. Giao thức tiêu biểu là EIGRP(Enhance Interio Gateway Routing Protocol)
    * Hoặc có thể phân loại dựa trên cấu trúc phân cấp của IP chia thành 2 loại là: 
        * Các giao thức classfull: Router không gửi kèm subnetmask trong bản tin routing. Giao thức tiêu biểu là Ripv1. Không hỗ trợ trong sơ đồ chỉa nhỏ mạng VLSM (Variable Length Subnet Mask) là kỹ thuật chia nhỏ một mạng thành các mạng có độ dài khác nhau (sẽ có các subnet mask khác nhau). Không hỗ trợ sơ đồ mạng gián đoạn là 1 mạng chính bị phân tách bởi 1 mạng khác ví dụ:

        ![](https://user-images.githubusercontent.com/52046920/188349626-bdb8274f-c828-4bb1-9e42-2b2feb9a1d1c.png)
        * Các giao thức classess: Router có gửi kèm subnetmask trong bản tinh routing. Giao thức tiêu biểu là Ripv2, OSPF, EIGRP. Có hỗ trợ mô hình chia nhỏ mạng VLSM và sơ đồ mạng gián đoạn
# ***II.	Độ ưu tiên của các giao thức định tuyến***
* Giá trị AD(Administrative Distance) là giá trị được sử dụng để chỉ ra mức độ ưu tiên giữa các kỹ thuật định tuyến khác nhau. Một router có thể học được nhiều đường đi khác nhau bởi các kỹ thuật định tuyến khác nhau và nó sẽ chọn kỹ thuật có AD nhỏ nhất.

|Kỹ thuật Routing|AD|
|--|--|
|Kết nối trực tiếp(Các mạng kết nối trực tiếp với router có sẵn trong bảng định tuyến)|0|
|Định tuyến tĩnh|1 hoặc 0|
|EIGRP|90|
|OSPF|110|
|RIP|120|

* Nếu cùng sử dụng 1 giao thức thì metric sẽ được đưa ra so sánh, với từng giao thức metric sẽ được tính khác nhau

|giao thức|giá trị làm metric|
|---|---|
|RIP|hop count|
|EIGRP|bandwidth , delay , load , reliability , MTU |
|OSPF|cost(Dựa vào bandwidth)|
