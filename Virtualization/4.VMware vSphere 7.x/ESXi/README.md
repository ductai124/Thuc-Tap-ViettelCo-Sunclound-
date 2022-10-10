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

# TÌM HIỂU ESXi
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. ESXi]()
# [II. Kiến trúc ESXi]()
# [III. Tổng quan về ESXi 7.0 System Storage]()
# [IV. Host Build Procedure]()
## &ensp; [1. Các bước trước khi cài đặt ESXi]()

## &ensp; [2. Quy trình cài đặt ESXi]()

## &ensp; [3. Các bước sau khi cài đặt ESXi]()
# [V. Cài đặt ESXi 7]()
# [VI. ESXi Host Configuration and Management]()

## &ensp; []()

## &ensp; []()

## &ensp; []()
***
# ***I.	ESXi***
* ESXi là nền tảng ảo hóa dùng để tạo ra và chạy các máy ảo, thiết bị ảo
* ESXi là 1 Native Hypervisor hay bare metal Hyperrvisor vậy nên nó không phải là 1 phần mềm cài đặt trên hệ điều hành như VMware Workstation
* ESXi cài đặt trực tiếp trên máy chủ vật lý cho phép truy cập trực tiếp vào tất cả các tài nguyên máy chủ.
* Cho phép các máy ảo được chạy gần với hiệu suất nguyên bản nhất. không giống với Hosted base hypervisors.
* ESXi có thể cài đặt trên các ổ đĩa cứng, SAN LUNs, SD card, SATADOM.
* ESXi có 1 small disk footprint(Cho phép làm việc chỉ với 150MB dụng lượng) để tăng thêm độ an toàn và độ tin cậy
* ESXi 7.x cho phép: 
    * Sử dụng lên đến 768 Logical CPUs trên mỗi host
    * Sử dụng lên đến 16 TB RAM trên mỗi host
    * Triển khai (Deployment) lên đến 1024 virtual machines trên mỗi host
# ***II.	Kiến trúc ESXi***

![](https://user-images.githubusercontent.com/52046920/193181052-8d505995-5cd2-49a5-ba2b-67ac0c0fe4f2.png)
* Network and Storage - Mạng và lưu trữ : Storage để cài đặt ESXi Server. Network để truy cập Server từ xa.
* VMKernel - Lõi ảo hóa: Là hạt nhân của OS. Quản lý, phân phối việc truy cập tới tài nguyên phần cứng trên máy chủ
* Local Support Console(ESXi Shell): Sử dụng để truy cập vào VMKernel tương tự với CMD bên windows, Terminal bên linux.
* VMware Management Framework là 1 Agentless Systems Management - Quản trị hệ thống không tác nhân. Có nghĩa là không có tác nhân(Agent) nào quản lý.
* CLI Commands for Configuration And Support: cấu hình bất cứ thứ gì có thể thực hiện từ chế độ đồ hoạ hoặc sử dụng giao diện dòng lệnh CLI.

* Common Information Model(CIM): Dịch vụ chạy ở VMkernel Level. Là 1 Agentless Hardware Monitoring - Giám sát hệ thống không tác nhân. Không cần Agent để giám sát phần cứng của ESXi Server. Có thể giám sát phần cứng của ESXi thông qua SMNP hoặc địa chỉ IP
* VM - Virtual Machine: Các máy ảo được thiết lập trên ESXi Server

# ***III. Tổng quan về ESXi 7.0 System Storage***
* Phân vùng lưu trữ hệ thống gồm 4 phần

||||
|-|-|-|
|System Boot|Lưu trữ boot loader và EFI(Extensible Firmware Interface Firmware-là các tệp thực thi của trình tải khởi động, sử dụng để sắp xếp các bản cập nhật Firmware, khởi động hệ điều hành và chạy các chương trình trước khi khởi động.) modules|FAT16|
|Boot-bank 0|Không gian System để lưu trữ ESXi boot modules|FAT16|
|Boot-bank 0|Không gian System để lưu trữ ESXi boot modules|FAT16|
|ESX-OSData|Để lưu trữ các modules bổ sung. Không được sử dụng cho booting và Virtual Machines. Hợp nhất phân vung legacy / scratch. Phân vùng khóa cho CMWare tools và các core dump destinations |VMFS-L|
* Các phân vùng trên đã được cố định kích thước ngoại trừ phân vùng /scratch và  optional VMFS datastore và các phân vùng số tĩnh, hạn chế quản lý phân vùng. 


* Kích thước lưu trữ hệ thống ESXi

|Boot Media Size|4-10 GB|10-32 GB|32-128 GB|>128 GB|
|-|-|-|-|-|
|System Boot|100MB||||
|Boot-bank 0|500MB||||
|Boot-bank 1|500MB||||
|ESX-OSData|Còn lại|Còn lại|Còn lại|lên đến 128 GB|
|VMFS datastore||||Còn lại cho media size>142 GB|

* Đường dẫn system storage

# ***IV. Host Build Procedure***

![](https://user-images.githubusercontent.com/52046920/193181056-5c1307c3-ec35-461e-ba9c-bece39ea68aa.png)
# ***1. Các bước trước khi cài đặt ESXi***
* Xác minh danh sách tương thích phần cứng
* Chọn phần cứng tương thích (Server Tower/Rack mount/ Blade)
* Hệ thống cáp Server hoạt động với sự trợ giúp của Nhà cung cấp
* Định cấu hình HPE-ILO hoặc DELL- IDRAC hoặc IBM- RSA hoặc Fujitsu - iRMC
* Kết nối với các Máy chủ bằng địa chỉ IP quản lý từ xa
* Cài đặt hoặc Upgrade Firmware mới nhất
* Bật RAID 1 hoặc 5 ở BIOS level
* Bật Intel-VT hoặc AMD-V ở BIOS Level
* Download tệp ESXi 7.x ISO hoặc tệp ISO Custom
* Nhận IP Settings từ Networking Team hoặc IP Inventory list (Danh sách kiểm kê IP)
* Nhận thông tin chi tiết về Storage từ Storage team.
* Tạo bản ghi host (A) và PTR records trong DNS server


## ***2. Quy trình cài đặt ESXi***
* Mount ISO qua option Virtual media
* Reset Server vật lý bằng Power Mgmt.Option
* Theo dõi quá trình khởi động ESXi từ Remote Mgmt.Console
Làm theo hướng dẫn trên màn hình để cài đặt, tức là nhấn F11

## ***3. Các bước sau khi cài đặt ESXi***
* Thay đổi thông tin đăng nhập gốc qua SSH/Enable SSH
* Bật NTP, Port -123: Đồng bộ hoá theo thời gian (For Time Syncronization)
* Bật SNMP, Port - 161,162: Để giám sát máy chủ ESXi
* Áp dụng các bản vá lỗi trên host ESXi (Optional)
* Cấu hình Mạng host ESXi -vSwitch, DvSwitch
* Cấu hình Storage trên host ESXi - Local, NAS, ISCSI và SAN
* Chuyển nhương giấy phép ESXi (Assign ESXi License)
* Tắt chế độ ESXi lockdown
* Cấu hình ESXi Syslog server
* Xác thực trang thái kết nối host ESXi và kiểm tra Health
* Tạo một VMs Test và Kiểm tra image Backup
* Mở các port Firewall cần thiết (Optional)
* Xác thực Dung lượng disk host ESXi
* Set VMs auto start với host (Optional)
# ***V.	Cài đặt ESXi 7***
* Cài đặt ESXi theo VMWare Doc gồm các bước:
   * 1. Xác minh hệ thống đáp ứng yêu cầu phần cứng tối thiểu
    * 2. Xác định option cài đặt ESXi boot từ CD hay USB,...
    * 3. Xác định vị trí đặt và boot trình cài đặt ESXi. Nếu sử dụng PXE để boot trình cài đặt, hãy xác minh rằng cơ sở hạ tầng PXE mạng được thiết lập đúng cách
    * 4. Tạo 1 bảng chứa các thông tin cần thiết khi cài đặt. Bảng các thông tin được bắt buộc cài đặt

    ![](https://user-images.githubusercontent.com/52046920/194791653-d4b8a61b-9413-4bb1-966d-0490d7870712.png)
    * 5. Cài đặt ESXi
        * Installing ESXi Interactively
        * Installing or Upgrading Hosts by Using a Script
* Khởi động máy ảo chứa ESXi 7

![](https://user-images.githubusercontent.com/52046920/193181022-10669662-a4eb-4aaa-9c09-ca50ea486eec.png)
* Chờ đợi load vào file iso

![](https://user-images.githubusercontent.com/52046920/193181018-66a1f3ed-ffec-4242-b7b4-5257a265aa51.png)

* Bấm phím `Enter` để tiến hành cài đặt

![](https://user-images.githubusercontent.com/52046920/193181021-f3c150e2-564d-4afb-b708-7a36f32d8061.png)

* Nhấm phím `Enter để tiếp tục`

![](https://user-images.githubusercontent.com/52046920/193181026-01ff4d85-bf64-4117-9b17-4c3f688b4db6.png)

* Chọn ổ đĩa để cài đặt sau đó bấm phím `Enter`

![](https://user-images.githubusercontent.com/52046920/193181028-5ceccb50-6d7c-4ca8-8f63-4e204c221ae0.png)

* Lựa chọn kiểu bàn phím sau đó nhấn phím `Enter`

![](https://user-images.githubusercontent.com/52046920/193181029-6d0138ba-c957-4485-966a-dcb55cd2751e.png)
* Nhập `Root Password` muốn đặt và xác nhận mật khẩu đó. Sau khi mật khẩu root và xác nhận thành công thì nhấn phím `Enter`

![](https://user-images.githubusercontent.com/52046920/193181032-1ba4d212-a656-4e1e-be9d-baaac60379d5.png)

* Nhấn phím `Enter` để xác nhận cài đặt

![](https://user-images.githubusercontent.com/52046920/193181035-131de06b-a11c-40e2-ab61-3dd45fa544f1.png)

* Nhấn `Enter` để `Reboot` lại hệ thống

![](https://user-images.githubusercontent.com/52046920/193181038-bdc2e62c-fe50-4e9a-b575-a96fdc1b6320.png)

* Cài đặt hoàn thành

![](https://user-images.githubusercontent.com/52046920/193181039-fa820e06-78ca-4020-9b75-b73209e76b6f.png)
* Có thể truy cập vào địa chỉ IPv4 hoặc địa chỉ IPv6 trên trên trình duyệt web để có thể quản trị ESXi thông qua giao diện web

![](https://user-images.githubusercontent.com/52046920/193181041-93f6606a-dfa1-44fc-8148-fcb62552adec.png)

* Nhập User name là root và mật khẩu đã đặt ở bước cài đặt thì sau đó ta truy cập được vào giao diện quản trị trên web của ESXi

![](https://user-images.githubusercontent.com/52046920/193181044-32bf038f-8ed6-4ce9-b587-2863a95a84a7.png)

* Để SSH được vào ESXi Server truy cập vào VM chứa ESXi bấm phím `F2`. Sau đó lựa chọn `Troubleshooting Options`

![](https://user-images.githubusercontent.com/52046920/193181046-4554ac52-560f-4124-a120-64562f850876.png)

* Đến lựa chọn SSH và bấm phím `Enter`. Kiểm tra trạng thái bên phải nếu hiện thị là `SSH is Enabled` là đã thành công


# ***VI. ESXi Host Configuration and Management***
