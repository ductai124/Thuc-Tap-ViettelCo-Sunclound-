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

# TÌM HIỂU VỀ ESXi HOST CONFIGURATION AND MANAGEMENT
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
# ***I. ESXi Components***
* Kiến trúc ESXi bao gồm hệ điều hành cơ bản, được gọi là VMkernel và các processes chạy trên nó
* VMkernel cũng giống như một OS, cung cấp một phương tiện để chạy các processes trên hệ thống gồm các ứng dụng quản lý và Agent và các máy ảo
* Nó điều khiển tất cả phần cứng thiết bị trên server và quản lý tài nguyên cho các ứng dụng.
* Các main processes chạy trên VMkernel là:
    * DCUI - Direct Console User Interface: là mức độ cấu hình thấp và quản lý thấp nhất. Chủ yếu được sử dụng cho những cấu hình ban đầu
    * VMM - Virtual Machine Monitor: Process cung cấp môi trường thực thi cho máy ảo và 1 process hỗ trợ là VMX
    * VMwware Agents(hostd,vpxa): cho phép quản lý cơ sở hạ tầng VMware ở mức độ cao từ các ứng dụng từ xa
    * Common Infomation Model(CIM) System: Giao diện cho phép quản lý mức độ phần cứng từ các ứng dụng từ xa thông qua các API.

 
# ***II. File System ESXi***
* VMkernel sử dụng đơn giản trong bộ nhớ file system để chứa các file cấu hình ESXi Server, File Log và các bản vá theo giai đoạn (có nghĩa là các bản vá đã được áp dụng)
* File system này độc lập với Vmware vSphere VMFS File System được sử dụng để lưu trữ các máy ảo
* ESXi có thể cấu hình Syslog Server từ xa và dump server(Kết xuất) từ xa. Cho phép lưu toàn bộ thông tin log trên  hệ thống bên ngoài
* Các Log Files
|STT|Tên Log|Mô tả|
|-|-|-|
|1|/var/log/auth.log|ESXi xác thực Shell Success hay Failure|
|2|/var/log/esxupdate.log|ESXi patch và update cài đặt logs|
|3|/var/log/hostd.log|Log của dịch vụ quản lý Host, bao gồm máy ảo và Host Task và Event giao tiếp với vSphere Client và vCenter Server vpxa agent, và kết nối SDK|
|4|/var/log/syslog.log|Khởi tạo dịch vụ quản lý, cơ quan giám sát, task đã lên kế hoạch và sử dụng DCUI|
|5|/var/log/vmkernel.log|logs của Core VMKernelS bap gồm các thiết bị discovery, storage, các thiết bị networking các sự kiện driver và khởi động khởi động|
|6|/var/log/vmkwarning.log|Bản tóm tắt Warning Log và Alert Log được trích từ VMkernel Logs|
|7|/var/log/vmksummary.log|Bsnr tóm tắt về ESXi host khởi động và tắt nguồn, heartbeat(là một loại gói tin liên lạc được gửi giữa các nút, được sử dụng để theo dõi tình trạng các nút) hàng giờ với thời gian hoạt động, số lượng máy ảo đang chạy và mức tiêu thụ tài nguyên dịch vụ|
|8|/var/log/vpxa.log|Logs vCenter Server vpxa agent, bao gồm giao sự giao tiếp với vCenter Server và Host Management host agent|
|9|/var/log/fdm.log|vSphere Log tính khả dụng cao, được tạo ra bởi dịch vụ FDM|


# ***III. Cấu hình cơ bản trên giao diện DUCI***


* Giao diện DCUI

![](https://user-images.githubusercontent.com/52046920/194980772-3b04b30f-4ed5-46d9-a1db-1376c1ebf0bc.png)

* Bấm F2 để cấu hình hệ thống

![](https://user-images.githubusercontent.com/52046920/193213129-400f81e8-d0cd-4088-b786-170806aa507f.png)

* Nhập mật khẩu root

![](https://user-images.githubusercontent.com/52046920/193213131-1d42e9d7-0075-470f-9b36-504d90ec3e14.png)

* giao diện System Customization

![](https://user-images.githubusercontent.com/52046920/194985334-3254338a-33be-40ed-a78e-6396e37d86fc.png)

* `Configuration Password`: Thiết lập lại mật khẩu root
* `Configuration Management Network`: Cấu hình mạng
    
    ![](https://user-images.githubusercontent.com/52046920/194986581-7d9aab8d-0007-4802-a589-28f96534fc8f.png)
    * `Network Adapter`: thay đổi network adapter
    * `Vlan(optional)`: tạo Vlan
    * `IPv4 Configuration`: cấu hình ipv4
    * `IPv6 Configuration`: cấu hình ipv6
    * `DNS Configuration`: cấu hình DNS
    * `Custom DNS Sufixes`
* `Restart Management Network`: Restart lại cấu hình mạng
* `Test Management Network`: Test mạng bằng cách ping đến 1 số địa chỉ IP

![](https://user-images.githubusercontent.com/52046920/194994931-de58c420-797c-4523-ad7c-9977d5b646ad.png)

![](https://user-images.githubusercontent.com/52046920/194994934-4cd24911-00ca-4e95-b2f6-6e61cb37d992.png)
* `Network Restore Options`: khôi phục lại cấu hình network
* `Configure Keyboard`: lựa chọn kiểu phím
* `Troubleshooting Options`: Option Khắc phục sự cố như:

    ![](https://user-images.githubusercontent.com/52046920/194995996-bb2281ec-aef4-456e-8218-8507e7ab50f0.png)
    * Enable truy cập shell: sau khi Enable, để truy cập shell bấm tổ hợp phím `Alt` + `F1`. Để trở lại chế độ DCUI bấm tổ hợp phím `Alt` + `F2`

    ![](https://user-images.githubusercontent.com/52046920/194997915-a666339e-92c7-4edf-a1c0-e573618099b0.png)
    * Enable SSH
    * Cấu hình thời gian chờ (Khi không tác động trong 1 khoảng thời gian phiên DCUI sẽ bị khoá)
    * Khởi động lại Management Agent
* `View System Logs`: Lựa chọn các option để xem logs

    ![](https://user-images.githubusercontent.com/52046920/194996290-9c70e92a-2e2f-435e-b631-9b612998154c.png)

    * ví dụ bấm phím số 1 để xem Syslog của hệ thống

    ![](https://user-images.githubusercontent.com/52046920/194996442-827c703d-b9a3-4484-bd7a-1e84ce954d69.png)
* `View Support information`: bấm page down và page up để kiểm tra các thông tin serial number, bios, license, firmware,...

![](https://user-images.githubusercontent.com/52046920/194996712-7bc2ec36-f07d-4634-8bbb-11f8b08c0613.png)

![](https://user-images.githubusercontent.com/52046920/194996810-911fd355-7850-4dce-a714-5ef7e3467833.png)
* `Reset System Configuration`: Reset lại hệ thống

# ***III. Các giao diện quản lý  ESXi***
## ***1. VMWare Host Client***
## ***2. vSphere CLient***
## ***3. CLI***