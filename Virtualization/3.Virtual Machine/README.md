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
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
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
### ***4.1 Bước 1: Pre-Implementation - Bước trước triển khai***
* Xác định yêu cầu của khách hàng:
* VM 1
    |VM Components|Description|
    |-|-|
    |VM Name|VM-1|
    |vCPU(s)|2|
    |vMem|4gb|
    |vDisk - 1|30gb|
    |vDisk - 2||
    |vDisk - 3||
    |nNIC|1|
    |Operating System (OS)|Window Server 2016|

* VM2

    |VM Components|Description|
    |-|-|
    |VM Name|VM-2|
    |vCPU(s)|1|
    |vMem|2gb|
    |vDisk - 1|25gb|
    |vDisk - 2||
    |vDisk - 3||
    |nNIC|1|
    |Operating System (OS)|Centos 7|

### ***4.2 Bước 2: Implementation Procedure - Quy trình thực hiện***
## ***Cài đặt VM-1***
* Mở VMware Workstation

![](https://user-images.githubusercontent.com/52046920/192462209-5ba07133-412c-4698-a7a9-1e85b81175d8.png)

* Tại giao diện VMware Workstation chọn `Create a New Virtual Machine`

![](https://user-images.githubusercontent.com/52046920/192461903-698221d3-1a88-44c0-b6c6-4349e2a8764d.png)

* Cửa sổ `New Virtual Machine Wizard`
* Chọn `Custom(advanced)`

![](https://user-images.githubusercontent.com/52046920/192461905-d5866c6d-8b46-4735-891a-d370228ca7d8.png)

* Để các tùy chọn mặc định và lựa chọn `Next`

![](https://user-images.githubusercontent.com/52046920/192461906-5073b421-cec8-424f-ad71-b3a1b86f23f1.png)

* Tích chọn `I will install the Operating system later` sau đó chọn `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461911-acf79c23-bdb1-43c9-8a78-ea4d207782c0.png)

* Ở đây do yêu cầu đề bài là VM-1 sử dụng OS là Windows Server 2016 nên lựa chọn tích vào `Microsoft Windows` và lựa chọn `Windows Server 2016` làm version sau đó click vào `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461916-70f1affb-121c-4a51-86bf-89e9495e5022.png)

* Click vào `Browse...` để chọn nơi máy ảo được lưu trữ

![](https://user-images.githubusercontent.com/52046920/192461921-0a6eb99c-e462-46ea-a64b-b01bf2df1009.png)
* Lựa chọn nơi máy ảo được lưu trữ

![](https://user-images.githubusercontent.com/52046920/192461922-e96a2bb6-dbd3-437f-aa76-96130340273d.png)
* Do yêu cầu đề bài VM này có VMname là VM-1 nên đặt VM name là `VM-1` sau đó click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461919-aba14999-b1e7-40a9-864a-76514e4f05dd.png)

* Tiếp tục lựa chọn `Next`

![](https://user-images.githubusercontent.com/52046920/192461926-948c58d6-6f7b-4fe7-9b29-27ed642e084a.png)

* Do bài toán yêu cầu 2 vCPU nên lựa chọn `Number of processors` là 2 còn số nhận trong cpu không yêu cầu nên ở đây để là 1. CLick vào `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461929-3bbcb509-335f-4ac1-b0a6-562836c56f65.png)

* Lựa chọn Ram là 4gb do đề bài yêu cầu bằng cách thay đổi thông số ở ô `Memory for this virtual machine` hoặc chọn giá trị mình mong muốn ở thành giá trị bên trái. Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461934-c92ae794-7d88-455f-a5b9-0ab12cb24e63.png)
* Tiếp tục click `Next`

![](https://user-images.githubusercontent.com/52046920/192461938-418340f7-b1eb-4608-bd31-f9c77efd0aef.png)

* I/O nên để giá trị được recommended. Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461942-0b057ec3-48f3-4e1d-8c64-b9a90889a1b4.png)

* Chọn loại ổ cứng, nên để theo `Recommended`. Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461947-c68ccfae-e90e-4a8c-953b-6cb121af685d.png)

* Để tạo 1 ổ ảo chọn `Create a new virtual disk`. Chọn `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461953-310ce950-25b2-4c61-865f-f5b1596a2063.png)

* `Maximum disk size(GB)` lựa chọn 30GB theo yêu cầu, lựa chọn `Store virtual disk as a single file`. Sau đó chọn `Next`
để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461956-69cb66f3-82ee-42da-84bb-6a0c8b627d2a.png)

* Các lựa chọn ở cửa sổ này là:
    * Allocate all disk space now: Nếu check vào đây thì ổ cứng ảo sẽ lấy hẵn dung lượng mà bạn chọn ở Maximum disk size trên ở cứng vật lý, nếu dùng hay không dùng thì ổ cứng vật lý của bạn cũng sẽ mất đúng dung lượng này. Với người dùng thông thường, ơ đây bạn không nên check chọn để tiết kiệm dung lượng cho ổ cừng vật lý của bạn, máy ảo sẽ tự động dùng đến đâu thì lấy dung lượng đến đó cho đến khi đạt đến dung lượng mà bạn đã chọn ở Maximum disk size thì dừng.
    * Store vitual disk as a single file: Lưu trữ với một file ổ cứng duy nhất, với HDD thật mà dùng dịnh dạng ổ đỉa là NTFS thì bạn nên dùng tùy chọn này.
    * Split virtual disk into multiple files: Chi nhỏ ổ cứng ảo ra thành nhiều file, với định dạng ổ cứng máy thật là FAT thì nên chọn tùy chọn này. Việc chia nhỏ còn giúp cho việc chép máy ảo từ máy vật lý này qua máy vật lý khác nhanh hơn, nhưng nếu lở ta xóa nhắm hoặc chép thiếu 1 file trong số ổ cứng có thể làm máy không hoạt động được.
* Đặt tên cho thư mục .vmdk, mặc định là VM-1.vmdk do VMname đã đặt trước đó là VM-1. Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461959-15f339da-6159-41a3-89eb-630fa647a49a.png)
* Click vào `Customize Hardware...`

![](https://user-images.githubusercontent.com/52046920/192461962-4e776dd7-6112-43b9-8490-4cb7d31e80bb.png)

* Click vào `New CD/DVD(SATA)` rồi tích vào lựa chọn `Local ISO image file` để lựa chọn file ISO cài OS trên local. Click vào `Browse...`.

![](https://user-images.githubusercontent.com/52046920/192461964-8af032b6-e27c-47d6-878d-764062f82b19.png)
* Lựa chọn file ISO của Windows Server 2016

![](https://user-images.githubusercontent.com/52046920/192461965-77d65a00-0606-44af-9b37-977280f35667.png)
* Click `Close` để thoát ra

![](https://user-images.githubusercontent.com/52046920/192461969-c4f31d50-def3-4ab7-9ba3-c9a5c79a6568.png)
* Click `Finish để hoàn thành`

## ***Cài đặt VM-2***
* Tại giao diện VMware Workstation chọn `Create a New Virtual Machine`

![](https://user-images.githubusercontent.com/52046920/192461903-698221d3-1a88-44c0-b6c6-4349e2a8764d.png)

* Lần này sẽ lựa chọn `Typical (recommended)` để cài đặt

![](https://user-images.githubusercontent.com/52046920/192461977-52399188-38f4-4e4d-aa82-1f0898ff8969.png)

* Tích chọn `I will install the Operating system later` sau đó chọn `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461911-acf79c23-bdb1-43c9-8a78-ea4d207782c0.png)

* Lựa chọn `Guest Operating system` là Linux và `Version` là CentOS 7 64-bit theo đúng yêu cầu. Sau đó click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461988-05f9ba6c-e342-46a0-8b85-f315fee16487.png)
* Đổi VMname thành VM-2 click vào Browse... để chọn nơi lưu trữ máy ảo

![](https://user-images.githubusercontent.com/52046920/192461990-8b7bd4df-b616-4df8-920b-95bbd2b90034.png)

* Chọn nơi lưu trữ máy ảo
![](https://user-images.githubusercontent.com/52046920/192461993-29e176c1-1a52-4376-925a-809cb6dded0e.png)

* Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192461995-beb18d2f-cb96-4086-a510-90b9a8f9209e.png)

* Lựa chọn dung lượng ổ cứng là 25GB, tích chọn `Store virtual disk as a single file`. Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192462000-ae2f71c6-589a-492e-93cc-d96feb8a2676.png)

* Chọn `Customiza Hardware...`

![](https://user-images.githubusercontent.com/52046920/192462004-9f2a0036-359e-401e-a900-1d823bf7179f.png)
* Click `Processors` điều chỉnh `Number of processors` thành 2

![](https://user-images.githubusercontent.com/52046920/192462008-b8246ca9-3f59-4338-9e3b-27298bf6636e.png)
* Click vào `Memory` và thiết lập Ram là 2GB theo yêu cầu

![](https://user-images.githubusercontent.com/52046920/192462012-75705438-e29c-45b6-ad17-d6fedab413ce.png)

* lựa chọn vị trí file ISO local

![](https://user-images.githubusercontent.com/52046920/192462015-c4ede8ab-8767-42a7-a753-400f627636fe.png)

* Lựa chọn ISO của Centos 7

![](https://user-images.githubusercontent.com/52046920/192462018-b9e5fd2f-07c7-4f33-8766-ea73486c7c32.png)

* `Close` để hoàn thành

![](https://user-images.githubusercontent.com/52046920/192462021-4e70b1a4-f60d-454d-b8d9-9a97096d234f.png)

* `Finish` để hoàn thành việc khởi tạo

![](https://user-images.githubusercontent.com/52046920/192462023-87fbc6e3-60a7-4352-9dd4-bc5a22595619.png)

* Vậy là VM-1 và VM-2 đã được khởi tạo thành công

![](https://user-images.githubusercontent.com/52046920/192462024-166176fd-2cc1-4963-a48f-cbb7ac11f425.png)

* Tiếp theo tiến hành cài đặt OS cho VM-1 và VM-2
## ***Cài đặt OS cho VM-1***
* Click chọn `VM-1`

![](https://user-images.githubusercontent.com/52046920/192476160-02b183aa-75d6-44fa-acef-2b4446b933c5.png)

* Khởi động VM-1 bằng cách click vào `Power in this vitual machine`

![](https://user-images.githubusercontent.com/52046920/192476170-88024152-faa4-4c27-bfed-60cffc7b92e3.png)

* Click phím bất kỳ để boots vào file ISO

![](https://user-images.githubusercontent.com/52046920/192476178-b638df3e-77e0-42a9-a3e2-34328611e02a.png)

![](https://user-images.githubusercontent.com/52046920/192476183-ce1c4008-1213-40a9-90d5-0d9714bff9a6.png)
* Click `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192476187-9e532a4f-ffd3-4e7f-891d-8b63280deef8.png)
* Click `Install now`

![](https://user-images.githubusercontent.com/52046920/192476190-bfdd508a-2c8e-436e-8552-bb3fc828f1a3.png)

* Tích chọn `I accept the license terms` sau đo click `Next`

![](https://user-images.githubusercontent.com/52046920/192476194-2c90c770-16f9-4b91-9504-c01ef64bbe4c.png)
* Click chọn `Custom: Install Windows only(advanced)`

![](https://user-images.githubusercontent.com/52046920/192476195-ac89bf55-c47c-44ec-8318-dc1fcba95e35.png)
* Click chọn ổ đĩa sau đó click vào `Next` để tiếp tục

![](https://user-images.githubusercontent.com/52046920/192476196-1fb5c2e2-506e-4aa3-8a65-2710ced31f8f.png)
* Chờ đợi cài đặt hoàn tất

![](https://user-images.githubusercontent.com/52046920/192476203-a5d3f45a-df35-41ae-914e-d1d944c1b9ab.png)
* Đặt mật khẩu cho User Administrator sau đó click vào `Finish` để hoàn thành

![](https://user-images.githubusercontent.com/52046920/192476206-84222645-ae6d-4373-846e-05cb6b0db4b6.png)




## ***Cài đặt OS cho VM-2***

* Click chọn VM-2

![](https://user-images.githubusercontent.com/52046920/192476208-dcdd6fb3-836e-418f-8b17-16628f74b4f7.png)
* Khởi động VM-2 bằng cách click vào `Power in this vitual machine`

![](https://user-images.githubusercontent.com/52046920/192476211-42df7ee8-884b-4188-af90-bf4c4bdbd245.png)
* Click vào màn hình máy ảo, bấm mũi tên lên xuống lựa chọn `Install CentOS 7` sau đó nhấn phím `Enter` để xác nhận

![](https://user-images.githubusercontent.com/52046920/192476216-fe3d0999-6968-4695-9e47-337d19685b55.png)

* Bấm `Enter` 1 lần nữa để tiếp tục cài đặt

![](https://user-images.githubusercontent.com/52046920/192476217-6a044a19-5c82-411f-a69b-00fd40b69fb6.png)
* Thiết lập bàn phím và ngôn ngữ để mặc định là tiếng anh

![](https://user-images.githubusercontent.com/52046920/192476220-62a3b028-4127-437f-b725-43d712d9b36b.png)
* Lựa chọn `INSTALLATIN DESTINATION` để tiến hành phân vùng

![](https://user-images.githubusercontent.com/52046920/192476223-75f84e70-b0eb-4374-8cd3-8a7ad4c44a65.png)
* Ta sẽ phần vùng 1 cách tự động nên bấm Done để kết thúc

![](https://user-images.githubusercontent.com/52046920/192476225-8738d5e4-eb62-444b-b4e3-11301eeb0a2f.png)
* Click vào `Begin Instalation` để bắt đầu cài đặt

![](https://user-images.githubusercontent.com/52046920/192476228-a26157a1-a688-4e4e-994d-310f511411b3.png)
* Click `Root Password` để đặt mật khẩu cho User Root

![](https://user-images.githubusercontent.com/52046920/192476230-6a6cc1d6-fe89-40b0-8911-d44d27dca0b1.png)
* Đặt mật khẩu và xác nhận lại mật khẩu sau đó click Done để hoàn thành

![](https://user-images.githubusercontent.com/52046920/192476231-52646ba2-bd46-47d5-ba51-a2873b77883d.png)
* Chờ đợi cài đặt hoàn thành

![](https://user-images.githubusercontent.com/52046920/192476232-87e4b86e-4814-4ea9-9cd8-ec5d6380063d.png)
* Cài đặt hoàn thành reboot lại để vào OS

![](https://user-images.githubusercontent.com/52046920/192476236-d2e0363c-d9e6-4faa-b558-085e58340549.png)


### ***4.3 Post-Implementation Steps - Các bước sau khi triển khai***
## ***VM-1***
### ***Khởi động VM***
* Tại giao diện của VMware Workstation click chọn `VM-1`

![](https://user-images.githubusercontent.com/52046920/192476160-02b183aa-75d6-44fa-acef-2b4446b933c5.png)

* Khởi động VM-1 bằng cách click vào `Power in this vitual machine`

![](https://user-images.githubusercontent.com/52046920/192476170-88024152-faa4-4c27-bfed-60cffc7b92e3.png)
### ***Cài đặt VMware Tools***

### ***Thiết lập địa chỉ IP***
* Thiết lập lại địa chỉ IP nếu có yêu cầu
### ***Thêm hệ thống vào tên miền(Nếu được yêu cầu)***
* Thêm hệ thông tên miền nếu có yêu cầu
### ***Kích hoạt OS khách license***
### ***Đổi time zone phù hợp***

### ***Tắt bảo mật của IE cho Window Server***

### ***Tắt tường lửa***

### ***kích hoạt RDP/SSH***

### ***Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa***

### ***Cài đặt các phần mềm đặc biệt theo yêu cầu***

### ***Bảo mật VM OS khách*** 

### ***Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng***