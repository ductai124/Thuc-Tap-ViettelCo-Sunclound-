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

# TÌM HIỂU VỀ VMWARE vSPHERE 7
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Các khái niệm Virtualization cơ bản](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/4.VMware%20vSphere%207.x/README.md#i-c%C3%A1c-kh%C3%A1i-ni%E1%BB%87m-virtualization-c%C6%A1-b%E1%BA%A3n)

## &ensp; []()

## &ensp; []()

## &ensp; []()

# [II. VMWARE vSPHERE 7](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Virtualization/4.VMware%20vSphere%207.x/README.md#iivmware-vsphere-7)
***
# ***I. Các khái niệm Virtualization cơ bản***
* Host/Node/Server:
    * Các Server vật lý cung cấp tài nguyên cho ESXi Hypercisor.
    * Ví dụ như các mấy chủ vật lý của Dell, HPE, IBM, ...
* Operating System (Hệ điều hành):
    * Phần mềm được thiết kế để chỉ định tài nguyên vật lý cho các ứng dụng
    * Có các hệ điều hành như MS Windows, Linux, ...
* Hypervisor:
    * 1 hệ điều hành đặc biệt hoặc 1 phần mềm để chạy các Virtual Machines(VM)
    * Ví dụ: ESXi, VMW Workstation, Fusion, MS Hyper-V & Oracle Virtual Box, ....
* Virtual Machine:
    * Được các phần mềm tạo ra, nó tương tự các Server vật lý.
    * Là 1 ứng dụng đặc biệt giúp trừu tượng hóa tài nguyên phần cứng thành phần mềm
    * Ví dụ: ESXi -VMs, MS Hyper-V-VMs, Oracle Virtual Box VMs.
* Guest OS(Hệ điều hành khách)
    * Các hệ điều hành được chạy trên máy ảo được gọi là Guest OS
    * Ví dụ như các hệ điều hành của MS Windows, Linux, ...
* Application(ứng dụng):
    * Các phần mềm chạy trên nên của OS. Các ứng dụng này tiêu thụ phần cứng hoặc tài nguyên máy ảo
    * Ví dụ: MS Office, Chrome, SAP, MS SQL,....
* vSphere:
    * Sản phẩm Server ảo hóa của VMware kết hợp ESXi Hypervisor và vCenter Server Management Platform.

# ***II.	VMWARE vSPHERE 7***
* Là 1 nền tảng ảo hóa của VMware, biến các trung tâm dữ liệu thành cơ sở hạ tầng Cloud Computing tổng hợp bao gồm tài nguyên CPU, Storage và mạng. vShpere quản lý các cơ sở hạ tầng này như 1 môi trường hoạt động thống nhất và cung cấp các công cụ quản trị trung tâm dữ liệu tham gia vào môi trường đó.
![](https://docs.vmware.com/en/VMware-vSphere/images/GUID-5EB66614-1EE8-4F39-8C8B-1E97EEE76791-high.png)

* 2 Thành phần cốt lõi của vSphere là ESXi và vCenter Server
    * ESXi là nền tảng ảo hóa nơi mà người dùng tạo ra, chạy các máy ảo và thiết bị ảo. 
    * vCenter Server là dịch vụ  được sử dụng để quản lý các Server được kết nối trong mạng. 

![](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.esxi.install.doc/images/GUID-5FE2EE35-63AD-4EA4-8C02-15E4407DB135-high.png)
* VMWare Vsphere có quy trình thiết lập và cài đặt như sau:
    * 1. Đọc vSphere release notes
    * 2. Cài đặt ESXi
    * 3. Cấu hình ESXi boot, network, direct console,.... 
    * 4. Thiết lập Syslog Server cho việc ghi log từ xa để đảm bảo đủ không gian disk storage cho log files. thiết lập ghi log trên host từ xa cực kỳ quan trọng cho những host hạn chế về lưu trữ local
    * 5. Install vCenter
    * 6. Kết nối với vCenter Server từ vSphere Client
    * 7. Configure vCenter Server



# [ESXi](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/beafd5c98a37c25c309e98b0ed7ddcb270fda790/Virtualization/4.VMware%20vSphere%207.x/ESXi/README.md)
# [vCENTER]()
<!---
# ***VI. lab***

[Bài lab Host Build Procedure]()

* Truy cập vào trang web [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php)

-->
