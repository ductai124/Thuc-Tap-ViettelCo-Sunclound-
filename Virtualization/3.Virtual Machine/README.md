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

# TÌM HIỂU VỀ VIRTUAL MACHINE
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Sự khác biệt về kiến trúc vật lý và kiến trúc ảo hóa]()
## &ensp; [1. Native]()
## &ensp; [2. Hosted]()
# [II. Virtual Machine]()
## &ensp; [1 Virtual Machine File]()
## &ensp; [2 Chia sẻ tài nguyên vật lý]()
# [III. Lợi ích của việc sử dụng Virtual Machine]()
# [IV. LAB tạo 1 VM theo kịch bản thời gian thực]()

## &ensp; [1. Pre-Implementation]()

## &ensp; [2. Implementation Procedure]()

## &ensp; [3. Post-Implementation]()
## &ensp; []()

## &ensp; []()

## &ensp; []()
***
# ***I.	Sự khác biệt về kiến trúc vật lý và kiến trúc ảo hóa***
* Ta có kiến trúc vật lý thật và kiến trúc ảo hóa.
* Kiến trúc vật lý
    * Gồm các thiết bị phần cứng như Ram, CPU, Storage,....
    * OS sẽ chạy trên nền phần cứng vật lý và phụ thuộc vào phần cứng
    * Các ứng dụng sẽ được chạy trên nền của các OS được cài đặt

![](https://camo.githubusercontent.com/5cc5518d717bb08f375ef2ea891c21f79b67803fcad7f1cb7e4848099975c2d1/68747470733a2f2f692e696d6775722e636f6d2f796441585367622e706e67)
* Kiến trúc ảo hóa là kiến trúc không có thật gồm các máy ảo được tạo ra từ tài nguyên được chia sẻ từ phần cứng của máy tính.  
* Kiến trúc ảo hóa sẽ có 2 loại tương ứng với 2 loại Hypervisor là:
    * Native hay còn được gọi là bare-metal.
    * Hosted-based
## ***1. Native***
* Một Hypervisor native sẽ chạy trực tiêp trên phần cứng và tương tác trực tiếp với kernel, không chạy trên 1 OS nào cả. Nó được đính kèm với 1 phần mềm quản trị để người dùng có thể thao tác. 
* không cần OS cũng có thể chạy được nên tài nguyên dành cho Hypervisor sẽ được tối ưu do không có OS tranh tài nguyên với nó
* Các Hypervisor native phổ biến: VMware ESXi, Microsoft Hyper-V, Apple Boot Camp
* Thường được sử dụng cho các ứng dụng doanh nghiệp và cloud computing(điện toán đám mây)

![](https://camo.githubusercontent.com/8f224ab9dfefba15357bd3f4f63e6844e1030472e2f6d9e885cd674df1fc5f67/68747470733a2f2f692e696d6775722e636f6d2f4e4f6679496c542e706e67)
## ***2. Hosted***
* Hypervisor Hosted được cài đặt trên nền 1 OS của 1 máy chủ (host computer) và chạy trên nền OS đó.
* Hypervisor Hosted như 1 phần mềm trên máy tính. Nó sử dụng các dịch vụ mà OS cho phép, cung cấp để phân chia tài nguyên máy ảo
* Các Hypervisor Hosted có thể quan lý và chạy nhiều máy ảo cùng 1 lúc. 
* Có thể bật tắt linh hoạt khi cần thiết để có thể giải phóng tài nguyên máy chủ tùy từng tình huống. 
* Các Hypervisor Hosted phổ biến
gồm VMware Workstation, Oracle VirtualBox và Parallels Desktop for Mac.
* Thường được sử dụng cho cá nhân và doanh nghiệp nhỏ

![](https://camo.githubusercontent.com/b818bc6d5d17f6cd261b66ccc4bd575b5e6a231f6b1665d51aa02051e25e74b9/68747470733a2f2f692e696d6775722e636f6d2f675a4b633764702e706e67)

# ***II.	Virtual Machine***
* Virtual Machines - Máy ảo là 1 máy tính ảo được tạo ra từ các tài nguyên phần cứng được chia sẻ, khá giống với 1 máy tính thật chạy các OS và các ứng dụng khác nhau.
* Virtual Machines gồm các thành phần sau: 
    * Operating System(OS): Hệ điều hành
    * VMware tools: Tools hỗ trợ nâng cao hiệu suất OS của máy ảo. Gồm trình điều khiển thiết bị và phần mềm khác cần thiết cho máy ảo. VMware tools giúp việc kiểm soát giao diện máy ảo tốt hơn.
    * Compatibility Setting: Xác định phiên bản máy chủ ESXi nào mà máy ảo có thể chỵ và các tính năng phần cứng có sẵn cho máy ảo
    * Hardware Device - Thiết bị phần cứng ảo tương tự với các thiết bị phần cứng trên máy thật được máy chủ vật lý chi sẽ tài nguyên vật lý của mình để tạo ra

## ***1	Virtual Machine File***
* Virtual Machine bao gòm 1 số tệp được lưu trữ. Các tệp quan trọng là configuration file, virtual disk file, NVRAM setting file, và log file.

|File|Usage|Description|
|-|-|-|
|.vmx|vmname.vmx|File cấu hình máy ảo|
|.vmxf|vmname.vmxf|Các File cấu hình máy ảo bổ sung|
|vmdk|vmname.vmdk|mô tả virtual disk|
|-flat.vmdk|vmname-flat.vmdk|Ổ đĩa dữ liệu máy ảo|
|.nvram|vmname.nvram hoặc nvram|Cấu hình BIOS hoặc EFI của máy ảo|
|.vmem|vmname.vmem|paging backup file của máy ảo|
|.vmsd|vmname.vmsd|snapshot máy ảo|
|.vmsn|vmname.vmsn|snapshot file dữ liệu của máy ảo|
|.vswp|vmname.vswp|swap file của máy ảo|
|.vmss|vmname.vmss|suspend file của máy ảo|
|.log|vmware.log|file log của máy ảo hiện tại|
|-#.log|vmware-#.log(# là số bắt đầu bằng 1)|file log cũ của máy ảo|


* Các tệp bổ sung được tạo khi tương tác với máy ảo
    * .hlog là file nhật ký của vCenter Server sử dụng để theo dõi các file máy ảo phải được xóa sau khi hoàn thành 1 thao tác nhất định
    * .vmtx được tạo khi máy ảo chuyển đổi thành template. File .vmtx sẽ thay thế .vmx
## ***2	Chia sẻ tài nguyên vật lý***
* Có thể tạo VM trên:
    * máy trạm vmware
    * Máy chủ ESXi
* Tương tự có thể tạo ra các đĩa, memory, CPU.
* Giả sử hệ thống vật lý có 20 cpu và bộ nhớ cũng 20gb và kích thước đĩa là 100gb, đây là tài nguyên có sẵn nếu muốn tạo máy ảo của mình dựa trên tài nguyên vật lý.
* Chỉ có 20 cpu nghĩa là mỗi máy ảo cung cấp 2 cpu có nghĩa là tối đa chúng tôi có thể tạo tối đa 10 vms và bộ nhớ cũng như nhau, có thể phân phối cho tất cẩ vms và tương tự với đĩa.
Cũng như vậy, có thể phân phối cho máy ảo nếu không có đủ bộ nhớ, cpu bằng cách sủ dụng một hộp vật lý khác để tạo 1 vms bổ sung, như vậy có thể tăng các hộp esxi.
* Bất kể tài nguyên có sẵn trong máy tính vật lý có thể chia sẽ cho các máy ảo.
# ***III.	Lợi ích của việc sử dụng Virtual Machine***
* Sử dụng máy vật lý sẽ có 1 số nhược điểm sau:
    * Khó quản lý
    * Chi phí cao
    * Thời gian ngưng trệ các dịch vụ các dịch vụ cao khi có sự cố
    * Khả năng mở rộng không cao do chi phí
    * Bảo dưỡng khó khăn nếu có quá nhiều thiết bị
* Máy ảo giúp hạn chế được 1 phần nhược điểm của mất vật lý như sau:
    * Quản lý dễ dàng hơn
    * Chi phí không quá cao
    * Khả năng mở rộng cao do tạo ra các máy ảo đơn giản hơn việc mua các máy vật lý và còn chưa kể đến việc thuê mặt bằng để đặt các máy vật lý
    * Giảm thời gian ngưng trệ dịch vụ khi có sự cố. do việc sao lưu và chuyển đổi các máy ảo dễ dàng 
    * Bảo dưỡng dễ dàng và nhanh chóng
* Tuy tiện ích là vậy nhưng máy ảo cũng có những nhược điểm như sau: 
    * Hạn chế về khả năng tương thích ví dụ phần cứng của model như thế hệ thứ 9 hỗ trợ lên đến esxi 6.5 OS chỉ khi bản muốn sử dung esx 6.7 hoặc esxi 7.0 thì cần nâng cấp phần cứng.
    * Thông thường mỗi máy ảo chỉ dùng 1 file để lưu tất cả thông tin trong máy ảo. vậy nên nếu mất tập tin này sẽ mất tất cả
    * Nếu máy vật lý chưa các máy ảo xảy ra vấn đề thì các máy ảo sẽ đều bị ảnh hưởng.

# ***IV. LAB tạo 1 VM theo kịch bản thời gian thực***
* Thực hiện theo 3 bước:
    * Pre-Implementation - Các bước trước khi thực hiện
    * Implementation Procedure - Quy trình thực hiện
    * Post-Implementation Steps - Các bước sau khi triển khai
## ***1. Pre-Implementation***
* Cần thực hiện tìm hiểu các thông tin được yêu cầu trước khi thực hiện:
    * VM Name: Được quy ước đặt tên theo 1 chuẩn nào đó
    * vCPU(s): Số CPU yêu cầu
    * vMem: Ram được yêu cầu
    * vDisk - 1
    * vDisk - 2
    * vDisk - 3 (Các ổ đĩa theo yêu cầu)
    * nNIC: Card mạng
    * Operating System (OS): Hệ điều hành khách hàng muốn cài đặt
## ***2. Implementation Procedure***
* Khởi tạo VM theo nhu cầu đã khảo sát
* Cài hệ điều hành khách

## ***3. Post-Implementation***
* Khởi động VM
* Cài đặt VMware Tools hoặc mở VM Tools cho Linux
* Đổi tên PC thành tên giống với VMname đã đặt
* Thiết lập địa chỉ IP
* Thêm hệ thống vào tên miền(Nếu được yêu cầu)
* Kích hoạt OS khách license
* Đổi time zone phù hợp
* Tắt bảo mật của IE cho Window Server
* Tắt tường lửa
* kích hoạt RDP/SSH
* Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa
* Cài đặt các phần mềm đặc biệt theo yêu cầu
* Bảo mật VM OS khách 
* Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng

## ***4. LAB***
* [Bài lab](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/51a70fa74a8761c8054b7dfcf6779be7668dc16a/Virtualization/Lab/1.CREATE%20VIRTUAL%20MACHINE/README.md)

