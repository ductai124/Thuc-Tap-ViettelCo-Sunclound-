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

# TÌM HIỂU VỀ ẢO HÓA
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Công nghệ ảo hóa](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#ic%C3%B4ng-ngh%E1%BB%87-%E1%BA%A3o-h%C3%B3a)
# [II. Lợi ích của công nghệ ảo hóa](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#iil%E1%BB%A3i-%C3%ADch-c%E1%BB%A7a-c%C3%B4ng-ngh%E1%BB%87-%E1%BA%A3o-h%C3%B3a)
# [III. Hypervisor](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#iiihypervisor)
## &ensp; [1. Native](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#1-native)

## &ensp; [2. Hosted](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#2-hosted)


# [IV. Các loại công nghệ ảo hóa](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#ivc%C3%A1c-lo%E1%BA%A1i-c%C3%B4ng-ngh%E1%BB%87-%E1%BA%A3o-h%C3%B3a)
## &ensp; [1. Network](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#1-network)
## &ensp; [2. Hosted](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#2-storage)
# [IV. Các loại công nghệ ảo hóa](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#2-hosted)
## &ensp; [1. Network](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#1-network)
## &ensp; [2. Storage](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#2-storage)

## &ensp; [3. Server](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#3-server)

## &ensp; [4. Data](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#4-data)
## &ensp; [5. Data center](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#5-data-center)
## &ensp; [6. Application](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#6-application)
# [V. Các mức độ ảo hóa](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#vc%C3%A1c-m%E1%BB%A9c-%C4%91%E1%BB%99-%E1%BA%A3o-h%C3%B3a)
## &ensp; [1. Ảo hóa toàn phần (full virtualization)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#1%E1%BA%A3o-h%C3%B3a-to%C3%A0n-ph%E1%BA%A7n-full-virtualization)
## &ensp; [2. Ảo hóa song song, 1 nửa(Para virtualization)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#2%E1%BA%A3o-h%C3%B3a-song-song-1-n%E1%BB%ADapara-virtualization)
## &ensp; [3. Ảo hóa 1 phần (Partial virtualization)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#3%E1%BA%A3o-h%C3%B3a-1-ph%E1%BA%A7n-partial-virtualization)
## &ensp; [4. Ảo hóa Hệ điều hành (OS virtualization)](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/1.Overview/What%20is%20Virtualization/README.md#4%E1%BA%A3o-h%C3%B3a-h%E1%BB%87-%C4%91i%E1%BB%81u-h%C3%A0nh-os-virtualization)
***
# ***I.	Công nghệ ảo hóa***
* Công nghệ ảo hóa cơ bản là tạo ra một bản sao giống với bản sao vật lý nhưng nó là bản sao ảo.
* Đối với máy chủ thì ảo hóa là tạo ra một bản sao của máy chủ ảo giống với máy chủ vật lý. Các máy ảo được gọi là Virtual Machines.  
* Bằng cách sử dụng công nghệ ảo hóa ảo hóa, Ta có thể tạo ra nhiều máy chủ ảo độc lập trên 1 máy chủ vật lý. Mỗi máy chủ ảo được tạo ra có thể được thiết lập thành 1 hệ thống riêng biệt với OS, các ứng dụng, nhiệm vụ hoàn toàn khác nhau.


# ***II.	Lợi ích của công nghệ ảo hóa***
* Tối ưu tài nguyên: Nếu không có ảo hóa mỗi máy chủ sẽ cần có 1 thiết bị phần cứng thật sự để triển khai, mỗi thiết bị phần cứng đó lại cần có các linh kiện đặc thù. Việc này gây tốn kém về mặt tài chính khi phải bỏ khả nhiều tiền để mua phần cứng và diện tích để đặt chúng. Ảo hóa giúp có thể tạo ra nhiều máy chủ ảo trên 1 thiết bị phần cứng duy nhất nên giảm chi phí mua phần cứng và diện tích, không gian lắp đặt phần cứng. Ngoài ra còn giảm chi phí bảo trì phần cứng do đã giảm được các thiết bị nhờ ảo hóa
* Dễ dang quản lý: Do sử dụng phần mềm để ảo hóa nền có thể tự động hóa được 1 số quá trình quan lý.
* Thời gian down time tối thiểu: Nếu 1 Máy chủ gặp sự cố  thì sẽ phải có 1 máy chủ dự phòng không thì phải sửa chữa máy chủ đó gây ra thời gian down time. Nếu sử dụng ảo hóa thì quản trị có thể chạy nhiều máy ảo dự phòng nếu 1 máy có sự cố có thể chuyển qua máy ảo khác việc này đỡ tốn kém hơn nhiều so với việc sử dụng máy vật lý làm dự phòng  
* Cung cấp nhanh: Nhanh hơn với việc đi mua build 1 bộ PC desktop và rồi sau đó cài đặt OS và driver cho chúng. Có thể cung cấp máy ảo ngay lập tức thậm chí còn có thể tự động hóa việc này



# ***III.	Hypervisor***
* Ảo hóa được xây dựng dựa trên giải pháp chia 1 máy vật lý thành nhiều máy ảo con. Nó được gọi là VMM - Virtual Machine Monitor hay thường được gọi là Hypervisor. 
* Hypervisor được sử dụng để khởi tạo máy ảo, quản lý các máy ảo đó và điều khiển chúng.
* Có 2 loại Hypervisor
## ***1. Native***
* Một Hypervisor native sẽ chạy trực tiêp trên phần cứng và tương tác trực tiếp với kernel, không chạy trên 1 OS nào cả. Nó được đính kèm với 1 phần mềm quản trị để người dùng có thể thao tác. 
* không cần OS cũng có thể chạy được nên tài nguyên dành cho Hypervisor sẽ được tối ưu do không có OS tranh tài nguyên với nó
* Các Hypervisor native phổ biến: VMware ESXo, Microsoft Hyper-V, Apple Boot Camp
* Thường được sử dụng cho các ứng dụng doanh nghiệp và cloud computing(điện toán đám mây)

## ***2. Hosted***
* Hypervisor Hosted được cài đặt trên nền 1 OS của 1 máy chủ (host computer).
* Hypervisor Hosted như 1 phần mềm trên máy tính. Nó sử dụng các dịch vụ mà OS cho phép, cung cấp để phân chia tài nguyên máy ảo
* Các Hypervisor Hosted có thể quan lý và chạy nhiều máy ả cùng 1 lúc. 
* Có thể bật tắt linh hoạt khi cần thiết để có thể giải phóng tài nguyên máy chủ tùy từng tình huống. 
* Các Hypervisor Hosted phổ biến
gồm VMware Workstation, Oracle VirtualBox và Parallels Desktop for Mac.
* Thường được sử dụng cho cá nhân và doanh nghiệp nhỏ

# ***IV.	Các loại công nghệ ảo hóa***
* Các loại ảo hóa thường gặp
## ***1. Network***
* Switch, Card mạng được ảo hóa linh động. Các Switch ảo và Card mạng ảo này có có khả năng giống với các thiết bị thật.
* Các tài nguyên này sẽ được phân chia băng thông thành các kênh độc lập ví dụ như ảo hóa mạng có khả năng tạo ra các vlan mà máy tính không thể tạo được.
* Có thể tạo ra vô số các cổng kết nối ảo, card mạng ảo giúp cho việc kết nối mạng trở nên dễ dàng hơn mà không bị hạn chế quá nhiều bởi các thiết bị phần cứng

## ***2. Storage***
* Là tập hợp các thiết bị lưu trữ được ảo hóa thành 1 thiết bị lưu trữ duy nhất
* Ảo hóa lưu trữ giúp cho việc lưu trữ, backup và restore dữ liệu hiệu quả hơn, tăng tốc khả năng truy suất cũng như tăng dung lượng lưu trữ.   
* Raid là 1 dạng ảo hóa lưu trữ.
* SAN - Storage Area Network là 1 công nghệ lưu trữ khá nổi tiếng, nó là 1 mạng được thiết kế cho việc thêm các thiết bị lưu trữ cho máy chủ như: Disk Aray Controllers, hay Tape Libraries
## ***3. Server***
* Là 1 phương pháp phân chia tài nguyên máy chủ cho nhiều máy ảo độc lập chạy trên 1 máy chủ duy nhất. 
* Lợi ích:
    * Tiết kiệm chi phí đầu tư máy chủ ban đầu
    * Hoạt động hoàn toàn như 1 máy chủ riêng
    * Có thể dùng máy chủ ảo hóa cài đặt các ứng dụng khác tùy theo nhu cầu của doanh nghiệp
    * Bảo trì, sửa chữa, nâng cấp nhanh chóng và dễ dàng
    * Dễ dàng nâng cấp tài nguyên
## ***4. Data***
* Là quá trình thu thập thông tin trong hệ thống và tạo ra 1 thông tin dạng ảo cho tất cả các thiết bị trong hệ thống truy cập mà dữ liệu gốc không cần phải di chuyển.

## ***5. Data center***
* Ảo hóa phần cứng của Data center cho phép admin chia 1 data center thành nhiều data center ảo chó các dịch vụ khác nhau
## ***6. Application*** 
* Lớp ứng dụng được tách hoàn toàn khỏi OS. Ứng dụng chạy dưới dạng đóng gói không phụ thuộc vào OS.
* Người dùng có thể truy cập và sử dụng ứng dụng mà không cần phải cài đặt trên máy thật của mình. 
* Khi được ảo hóa thì các ứng dụng được chạy trong môi trường sandbox. Sanbox là 1 môi trường cô lập ứng dụng ngăn chặn các phần mềm độc hại thường dùng trong bảo mật để kiểm tra cài đặt các ứng dụng.
* Lợi ích của ảo hóa ứng dụng:
    * Tất cả các máy tính đều có thể sử dụng phần mềm ảo như đang cài trên máy tính của mình không lo về cấu hình. tốc độ phần mềm ổn định và không phụ thuộc và cấu hình từng máy.
    * Các máy con không sợ virus hay spyware do cài các phần mềm
    * Sử dụng phần mềm không cần quan tâm đến OS
    * Phân phối phần mềm linh hoạt cho các cá nhân hoặc nhóm có nhu cầu sử dụng mà không cần cài đặt. Phân phối và gỡ bỏ phần mềm nhanh gọn. 
***7. Desktop***
* Cho phép triên khai các thiêt lập của máy tính cá nhân trên trên 1 máy ảo khác. 
* Người dùng có thể truy cập vào các máy ảo desktop trên server để sử dụng chỉ với 1 máy tính có cấu hình tối thiểu 
* Có thể truy cập từ xa trong các trường hợp không thể đến công ty. 
* Máy ảo có thể được sử dụng như 1 máy cá nhân của người dùng với gần như đầy đủ các tính năng

# ***V.	Các mức độ ảo hóa***
## ***1.	Ảo hóa toàn phần (full virtualization)***
* Toàn bộ phần cứng của máy tính sẽ được ảo hóa hết. Nó tách biệt phần cứng, OS và dịch vụ của máy ảo với máy chủ. Các máy ảo trong ảo hóa toàn phần không khác gì 1 máy thật
* Khi ảo hóa toàn phần, máy ảo có thể truy cập toàn bộ tài nguyên, tính năng của phần cứng 
* Sử dụng phổ biến: KVM, VirtualBox, VMware ESXi,.....
## ***2.	Ảo hóa song song, 1 nửa(Para virtualization)***
* Là loại ảo hóa không ảo hóa phần cứng 1 cách hoàn chỉnh để chạy OS ảo mà nó tạo ra 1 lớp GUI để các OS ảo và Hypervisor giao tiếp với nhau
* Sử dụng phổ biến: Oracle VM, ...
## ***3.	Ảo hóa 1 phần (Partial virtualization)***
* Chỉ tiến hành ảo hóa 1 số phần cứng nhất định của máy tính nên không đủ tài nguyên vận hành 1 OS hoàn ảo hoàn chỉnh. Nó cho phép cài đặt 1 số phần mềm, ứng dụng để tranh lãng phí tài nguyên
## ***4.	Ảo hóa Hệ điều hành (OS virtualization)***
* Máy ảo sử dụng 1 phần của OS để có thể sử dụng toàn bộ tính năng như ảo hóa toàn phần. Các máy ảo không phải chạy cùng OS với máy chủ. Máy chủ độc lập với các máy chủ ảo
* Sử dụng phổ biến : Docker, Linux LXC,.....


## Tài liệu tham khảo
[Tổng quan ảo hóa](https://lamth.github.io/Report-MDT/KVM/docs/01.tongquan-aohoa.html)

[VIBLO](https://viblo.asia/p/tan-man-ao-hoa-ai-cung-biet-nhung-cu-the-no-la-gi-Do754NV3ZM6)
[RedHat](https://www.redhat.com/en/topics/virtualization/what-is-virtualization)

[Global Knowledge](https://www.globalknowledge.com/us-en/resources/resource-library/articles/virtualization-for-newbies-five-types-of-virtualization/#gref)

[Viettel IDC](https://viettelidc.com.vn/tin-tuc/tat-tan-tat-nhung-dieu-ban-can-biet-ve-cong-nghe-ao-hoa)

[thegioimaychu](https://www.thegioimaychu.vn/blog/ao-hoa/huong-dan-tong-quan-ve-ao-hoa-vmware-p3588/)
