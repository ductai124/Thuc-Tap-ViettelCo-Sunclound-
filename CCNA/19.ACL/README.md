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

# TÌM HIỂU VỀ ACL
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. ACL là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#iacl-l%C3%A0-g%C3%AC)
# [II. Cấu hình ACL](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#iic%E1%BA%A5u-h%C3%ACnh-acl)

## &ensp; [1. Cấu hình ACL Standard](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#1c%E1%BA%A5u-h%C3%ACnh-acl-standard)

## &ensp; [2. Cấu hình ACL Extended](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#2c%E1%BA%A5u-h%C3%ACnh-acl-extended)

# [III. Khảo sát ACL cấm telnet theo ip trên router](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#iiikh%E1%BA%A3o-s%C3%A1t-acl-c%E1%BA%A5m-telnet-theo-ip-tr%C3%AAn-router)
# [IV. Named ACL](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#ivnamed-acl)
# [IV. Lọc lưu lượng theo thời gian Time Range](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#ivl%E1%BB%8Dc-l%C6%B0u-l%C6%B0%E1%BB%A3ng-theo-th%E1%BB%9Di-gian-time-range)
# [V. Phát hiện lưu lượng vi phạm bằng tính năng Log ACL](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/CCNA/19.ACL/README.md#vph%C3%A1t-hi%E1%BB%87n-l%C6%B0u-l%C6%B0%E1%BB%A3ng-vi-ph%E1%BA%A1m-b%E1%BA%B1ng-t%C3%ADnh-n%C4%83ng-log-acl)
# []()
# []()
***
# ***I.	ACL là gì***
* ACL hay Access Control list. Là danh sách các câu lệnh dùng để quản lý truy cập trên 1 thiết bị nó giống như tường lửa vậy, ACL chỉ có khả năng lọc các IP trên các cổng.
* Các doanh nghiệp và tổ chức tin dùng ACL do:
    * Kiểm soát được lưu lượng ra vào
    * Lưu lượng mạng bị hạn chế để đảm bảo hiệu suất mạng tốt hơn
    * Mức độ bảo mật cao trong việc truy cập mạng. Nó giúp chỉ định các khu vực riêng mà tùy từng nhóm người có thể truy cập hay không thể truy cập
    * Giảm lưu lượng ra vào hệ thống
* Mục đích chính ACL là cung cấp bảo mật cho hạ tầng mạng.
* Ví dụ: trong 1 doanh nghiệp gồm các phòng ban, phòng Server, và mạng cho khách hàng dùng. 

![](https://user-images.githubusercontent.com/52046920/187388476-8da8aa55-3572-411a-9177-7b04e941e208.png)

* Nếu không có ACL thì bất cứ phòng ban nào hay khách hàng cũng đều có thể truy cập được vào server của công ty, hay bất cứ nhân viên nào cũng có thể được truy cấp đến server và thao tác. Điều này có thể dẫn đến các cuộc tấn công vô cùng nguy hiểm đối với doanh nghiệp. Vì vậy cần phải có ACL để có thể chặn khách hàng truy cập vào Server cũng như các nhân viên và chỉ cho phép những người có quyền thao tác với Server mới được truy cập vào

* ACL có 2 loại
    * Standard ACL: Là những ACL đơn giản nhất. Được đánh số từ 1-99. Chỉ lọc địa chỉ nguồn nên sẽ đặt ở những nơi cần chỉ định chính xác các gói tin được đi quá, thường được đặt ở gần đích đến của các gói tin
    * Extended ACL: Là những ACL mở rộng. Được đánh số từ 100-199. Nó có thể chỉ định Port, IP nguồn và đích, giao thức và nhiều tùy chọn khác. Thường được đặt ở gần nguồn gửi gói tin
* Các thức hoạt động:
    * Khi gói tin đến với thiết bị được cấu hình ACL. Thiết bị đối chiếu với các điều kiện được thiết lập.
    * Nếu thõa mãn cấu hình thì cho phép đi qua nếu nằm trong danh sách bị chặn thì sẽ chặn gói tin lại
    * Các điều kiện được thiết lập sẽ được kiểm tra tuần tự. Nếu điều kiện ở trước thỏa mãn thì mới kiểm tra điều kiện tiếp theo.

![](https://user-images.githubusercontent.com/52046920/187394833-92cee8a1-c880-4b42-b1fa-e2997e8c6020.png)
* Các điền kiện sẽ được xét từ trên xuống dưới, khi khớp với 1 điều kiện rồi thì không xét đến điều kiện phía dưới nữa
# ***II.	Cấu hình ACL***
## ***1.	Cấu hình ACL Standard***
* Có 2 cách cấu hình ACL như sau
    * C1:
    ```cisco
    \\\Câu lệnh
    R1(config)#access-list [ACL number từ 1-99 do đang cấu hình ACL Standard] [permit/deny] [source ipadd/any/host và đị chỉ ip của host] [wildcard mask]

    \\\ví dụ
    R1(config)#access-list 10 permit 192.168.10.1 0.0.0.255
    
    R1(config)#access-list 10 deny host 192.168.20.5 0.0.0.255

    R1(config)#access-list 10 permit any
    ```
    
    
    * C2
    ```cisco
    R1(config)#ip access-list [standard] [ACL number 1-99]
    R1(config-std-nacl)#[permit/deny] [source ipadd/any/host và đị chỉ ip của host] [wildcard mask]

    ```

    * Gán ACL vào port
    ```cisco
    \\\Đầu tiên truy cập vào port muốn cấu hình ACL
    R1(config)#int gig0/0
    R1(config-if)#ip access-group [ACL number hoặc ACL name] [in/out]
    \\\\Phải trùng với tên ACL name hoặc ACL number đã thiết lập
    ```
* Các tham số trong ACL:
    * ACL Number: đánh số cho ACL. Standerd ACL từ 1-99 và Extended ACL từ 100-199
    * Permit/deny: Cho phép hoặc không cho phép gói tin đi qua thiết bị
    * Remark:
    * Sourrce ip add: Địa chỉ ip nguồn
    * any: Tất cả các source IP
    * host: địa chỉ 1 host
    * Wildcard mask: Wildcard mask của địa chỉ ip nó có dạng là có bit làm netID sẽ bằng 0 và các bit là HostID sẽ bằng 1. Hoặc khi cần gom các địa chỉ IP lại thành 1 địa chỉ ip thì ta có các bit giống nhau của các IP sẽ bằng 0 và các bit không giống nhau của các địa chỉ ip cần gom sẽ bằng 1(Gần như là ngược lại của subnet mask). Khi các giá trị của Wildcard mask là 0.0.0.0 thì địa chỉ ip đi kèm với nó sẽ là địa chỉ của 1 host chứ không phải là 1 dải ip
    * in/out: chiều đi vào hay ra của gói tin trên cổng thiết bị
    * ACL name: Tên ACL
* Ví dụ:
cho mô hình sau

![](https://user-images.githubusercontent.com/52046920/187388508-5aea81bc-1290-4d54-b06b-2f7b463e03ac.png)
* Mô hình đã được định tuyến và thiết lập VLan
* Server này chỉ dùng trong nội bộ công ty và chỉ admin được quyền truy cập vậy nên cấu hình chỉ cho PC1 của phòng admin được truy cập (các PC phòng admin thuộc dải ip 192.168.10.0 sẽ được phép truy cập vào server). Tuy nhiên các PC vẫn có thể truy cập ra bên ngoài đến PC3 được. Ta cấu hình như sau
* Tại router
```cisco
\\Tạo ACL
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
Router(config)#access-list 1 deny any

\\\Gán ACL vào cổng
Router(config)#int g0/0
Router(config-if)#ip access-group 1 out
```
* Kiểm tra ping thử các máy đến server

![](https://user-images.githubusercontent.com/52046920/187388515-62c8d96e-2761-4b10-89f1-0a8fce9ba57b.png)

## ***2.	Cấu hình ACL Extended***
* Cũng có 2 cách cấu hình bằng câu lệnh như sau:
    * C1:
    ```cisco
    \\\Câu lệnh
    R1(config)#access-list [ACL number từ 100-199 do đang cấu hình ACL Extended] [permit/deny] [protocol] [source ip/any/host và địa chỉ ip của host] [destination ip/any/host và địa chỉ ip của host] [protocol qualification] [logging]

    \\\ví dụ
    R1(config)#access-list 100 deny 192.168.10.1 0.0.0.255 192.168.20.5 eq 80

    R1(config)#access-list 100 permit any
    ```
    
    
    * C2
    ```cisco
    R1(config)#ip access-list [extended] [ACL number 100-199]
    R1(config-std-nacl)#[permit/deny] [protocol] [source ip/any/host và địa chỉ ip của host] [destination ip/any/host và địa chỉ ip của host] [protocol qualification] [logging]

    ```

    * Gán ACL vào port
    ```cisco
    \\\Đầu tiên truy cập vào port muốn cấu hình ACL
    R1(config)#int gig0/0
    R1(config-if)#ip access-group [ACL number hoặc ACL name] [in/out]
    \\\\Phải trùng với tên ACL name hoặc ACL number đã thiết lập
    ```
* Các tham số trong ACL:
    * ACL Number: đánh số cho ACL. Standerd ACL từ 1-99 và Extended ACL từ 100-199
    * Permit/deny: Cho phép hoặc không cho phép gói tin đi qua thiết bị
    * Remark:
    * Source ip: Địa chỉ ip nguồn và Wildcard mask
    * destination ip: Địa chỉ ip đích và Wildcard mask
    * any: Tất cả các source IP
    * host: địa chỉ 1 host
    * Protocol: Giao thức sử dụng TCP, UDP, ICMP,....
    * protocol qualification: nếu protocol là TCP hoặc UDP 
    * in/out: chiều đi vào hay ra của gói tin trên cổng thiết bị
    * ACL name: Tên ACL
* Một số các định danh port dịch vụ trên cisco packet tracer

![](https://user-images.githubusercontent.com/52046920/187388499-c8dbecd3-baf5-417b-a60b-388897db46ad.png)

* Ví dụ:
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/187388465-9269b05a-9274-4dda-b576-8b147486537c.png)
* Mô hình đã được định tuyến và thiết lập VLan
* Như ở ví dụ về standard ACL ta sẽ phải chọn chặn cổng ra ở phía g0/0 thì nếu có thêm 1 server mà vlan20 cần phải truy cập, tuy nhiên ta lại chặn ip của vlan 20 đi ra khỏi cổng g0/0 vì vậy nên ta phải sử dụng Extended ACL. Ta cấu hình PC1 có thể truy cập vào toàn bộ các Server, PC2 chỉ có thể truy cập vào Server 2, PC3 không thể truy cập vào các Server chỉ có thể thống đến các PC. Cấu hình như sau:

```cisco
R1(config)#access-list 100 permit ip 192.168.10.2 0.0.0.0 any
R1(config)#access-list 100 permit ip 192.168.20.0 0.0.0.255 192.168.2.3 0.0.0.0
R1(config)#access-list 100 deny ip any any

///lưu ý: Wildcard mask nếu có giá trị là 0.0.0.0 thì ip đứng trước nó sẽ được chỉ định chính xác là địa chỉ ip chứ không phải dải ip hoặc có thể thay thế bằng host ở phía trước ip và không cần nhập Wildcard mask nữa

\\\Gán ACL vào cổng
Router(config)#int g0/0
Router(config-if)#ip access-group 100 out
```
* Kiểm tra PC 1 ping được đến các Server

![](https://user-images.githubusercontent.com/52046920/187391069-b909b6f5-766c-4feb-8a2c-f837d2e67e2b.png)
* Kiểm tra PC2 Ping đén Server2 và Server1. Chỉ ping được đến Server 2

![](https://user-images.githubusercontent.com/52046920/187391074-23b8059b-6801-4a30-aa36-ae4306d5eced.png)
* Kiểm tra PC3 không thể truy cập được vào các Server

![](https://user-images.githubusercontent.com/52046920/187391077-4f0bcb0b-e9fd-4760-9882-1ecf6dd76d87.png)

# ***III.	Khảo sát ACL cấm telnet theo ip trên router***
* Cho mô hình

![](https://user-images.githubusercontent.com/52046920/187407918-45d7cd16-aac8-4a1c-82f6-2e126345e859.png)
* Mô hình đã được định tuyến và thiết lập VLan
* Tại R2 cấu hình chỉ cho phép PC 1 được phép telnet đến R2 như sau
* Cấu hình Standard ACL
    * Tại R2 cấu hình như sau
    ```cisco
    R2(config)#access-list 1 permit host 192.168.10.2
    R2(config)#enable password Tai123!
    R2(config)#line vty 0 4
    R2(config-line)#access-class 1 in
    R2(config-line)#password Tai123!
    R2(config-line)#login
    ```
* Kiểm tra telnet từ PC1 và PC2 đến R2

![](https://user-images.githubusercontent.com/52046920/187407904-ea5f7623-41d3-4052-9218-39720454a4ad.png)
* Cấu hình Extended ACL
    * Tại R2 cấu hình như sau
    ```cisco
    R2(config)#access-list 100 permit tcp host 192.168.10.2 host 192.168.2.2 eq 23
    R2(config)#access-list 100 permit tcp host 192.168.10.2 host 10.0.0.1 eq 23
    R2(config)#access-list 100 deny tcp any host 192.168.2.2 eq 23
    R2(config)#access-list 100 deny tcp any host 10.0.0.1 eq 23
    R2(config)#access-list 100 permit ip any any 
    
    R2(config)#enable password Tai123!
    R2(config)#line vty 0 4
    R2(config-line)#password Tai123!
    R2(config-line)#login
    R2(config-line)#exit

    R2(config-if)#ip access-group 100 in
    ```
* Kiểm tra telnet từ PC1 và PC2 đến R2 chỉ có PC1 telnet được, PC2 vẫn có thể Ping đến Server

![](https://user-images.githubusercontent.com/52046920/187407914-44c4bcd0-3335-4b0b-8b79-7a5f25e81b9e.png)
* Trong trường hợp này nên sử dụng Standard ACL để việc cấu hình trở nên dễ dàng hơn mà mục đích cấu hình vẫn được đảm bảo
# ***IV.	Named ACL***
* Named ACL ngoài việc chỉ để dẽ dàng nhận biết các ACL để quản lý ra nó còn giúp chung ta trong cấu hình như sau
* Như đã trình bày ở trên Cấu hình ACL có 2 cách:
* C1: Ta sẽ cấu hình
```cisco
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#access-list 1 deny any
```
* Ở cách cấu hình này, nếu như chỉ muốn xóa điều kiện số 2 trong ACL thì không thể vì khi xóa ACL ta thực hiện câu lệnh
```cisco
Router(config)#no access-list 1 deny any

///Câu lệnh trên tương đường với câu lệnh sau
Router(config)#no access-list 1 
```
* Toàn bộ ACL sẽ bị xóa bỏ hoàn toàn mà không thể xóa được riêng những điều kiện mà muốn lược bỏ đi vậy nên sử dụng cách cấu hình 2 sẽ giúp giải quyết vấn đề này

* C2: Ta sẽ cấu hính
```cisco
R1(config)#ip access-list standard acltest
R1(config-std-nacl)#permit 192.168.10.0 0.0.0.255
Router(config)#deny any
```
* Khi muốn xóa 1 điề kiện trong cấu hình ta kiểm tra bị trí điều kiện đó trong ACL
```cisco
R1#show access-lists 
```

![](https://user-images.githubusercontent.com/52046920/187411396-cfde6217-d7ff-4535-835c-10c9b162cfd3.png)
* Giả sử muốn xóa điều kiện số 2, ta có điều kiện thứ 2 có số 20 ta sẽ xóa bằng câu lệnh
```cisco
R1(config)#ip access-list standard acltest
R1(config-std-nacl)#no 20

//Muốn xóa nhiều dòng thì sử dụng câu lệnh ví dụ như sau
R1(config)#ip access-list standard acltest
R1(config-std-nacl)#no 20, 10, 30
```
* Kiểm tra lại ACL acltest và thấy điều kiện số 2 đã bị loại bỏ

![](https://user-images.githubusercontent.com/52046920/187411403-a49b5193-3297-4b4a-9b65-4d4eca8a86e1.png)

* Ta có thể chèn điều kiện vào giữa các điều kiện đã thiết lập mà không cần xóa đi tạo lại để điều kiện có thể chạy theo đúng thứ tự mong muốn.

![](https://user-images.githubusercontent.com/52046920/187411396-cfde6217-d7ff-4535-835c-10c9b162cfd3.png)
* Giả sử muốn chèn thêm 1 điều kiện vào giữa 2 điều kiện trên ta cấu hình như sau
```cisco
R1(config)#ip access-list standard acltest
R1(config-std-nacl)#15 permit 192.168.20.0 0.0.0.255
```

![]()
* Nếu cấu hình ACL bằng C1 ta vẫn có thể xóa các điều kiện hay chèn điều kiện giống như C2 do C1 ACL tạo ra thì sẽ có tên là số ta gán cho nó vậy nên ta có thể áp dụng các câu lệnh ở trên để thực hiện xóa điều kiện mà mình muốn xóa cũng như chèn điều kiện.

```cisco
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#access-list 1 deny any
```

![](https://user-images.githubusercontent.com/52046920/187413696-609fd624-8d0c-40bc-adc9-20f7d089e326.png)
* Xóa điều kiện số 2
```ciso
R1(config)#ip access-list standard 1
R1(config-std-nacl)#no 20
```

![](https://user-images.githubusercontent.com/52046920/187413700-7fe931bb-7cbb-4c0b-acf8-daf3d009a42e.png)

# ***IV.	Lọc lưu lượng theo thời gian Time Range***
* Sử dụng để hạn chế thời gian truy cập các dịch vụ của các IP
* Ví dụ: Các nhân viên cần truy cập vào Server trong giờ làm việc vậy ta sẽ cấu hình để cho các phòng ban của nhân viên có thể truy cập vào Server trong khoảng thời gian từ 8:00am đến 5:00pm. ip của Server 10.0.0.2

![](https://user-images.githubusercontent.com/52046920/187407918-45d7cd16-aac8-4a1c-82f6-2e126345e859.png)
```cisco
///Thiết lập time-range
R2(config)#time-range AccessServer
R2(config-time-range)# periodic daily 8:00 to 17:00

///Truyền time-range vào ACL
R2(config)#access-list 100 permit ip any host 10.0.0.2 time-range AccessServer 
```

* Các mốc thời gian có thể cấu hình

![](https://user-images.githubusercontent.com/52046920/187572564-36ac5172-7d40-4a07-ad97-a3b8f9d5c87a.png)

# ***V.	Phát hiện lưu lượng vi phạm bằng tính năng Log ACL***
* Cho mô hình sau

![](https://user-images.githubusercontent.com/52046920/187579933-ee24140d-31a0-4272-866c-939b9c8a6105.png)
* Cấu hình chỉ cho PC1 telnet đến R1 và nếu PC1 telnet đến R1 hoặc PC2 telnet đến R2 thì hiện log lên thông báo
* Cấu hình như sau
```cisco
R1(config)#access-list 1 permit ip host 192.168.10.2 log 
R1(config)#access-list 1 deny any log 
R1(config)#enable password Tai123!
R1(config)#line vty 0 4
R1(config-line)#access-class 1 in
R1(config-line)#password Tai123!
R1(config-line)#login
```
* Khi sự kiện xảy ra đáp ứng đúng điều kiện mà ta cấu hình để hiển thị log thì log sẽ được hiển thị ra ngoài màn hình cmd của thiết bị và có thể gửi log đó về Syslog Server

* Khi PC1 telnet đến R1, PC2 telnet đến R1 và bị deny

![](https://user-images.githubusercontent.com/52046920/187579946-4e45cd05-0283-4c47-9971-236656503911.png)

![](https://user-images.githubusercontent.com/52046920/187579942-19f8f38f-b270-4227-ab82-90493d332728.png)
