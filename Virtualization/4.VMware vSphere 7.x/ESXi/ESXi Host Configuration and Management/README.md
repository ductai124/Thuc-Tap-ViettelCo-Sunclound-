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
# [I. ESXi Components]()
# [II. File System ESXi]()
# [III. Cấu hình cơ bản trên giao diện DCUI]()
# [IV. Các giao diện quản lý ESXi]()
## &ensp; [1. VMWare Host Client - Lab tạo Storage, tạo VM trên ESXi]()

## &ensp; [2. vSphere CLient]()

## &ensp; [3. CLI]()

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


# ***III. Cấu hình cơ bản trên giao diện DCUI***


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

# ***IV. Các giao diện quản lý  ESXi***

![](https://user-images.githubusercontent.com/52046920/195477796-6cdc3eea-c8ce-4aa9-aacd-9863a3914c12.png)
* Có 3 giao diện quản lý ESXi sau
## ***1. VMWare Host Client - Lab tạo Storage, tạo VM trên ESXi***
* Tại màn hình giao diện DCUI ta thấy được đường dẫn để có thể quản trị ESXi

![](https://user-images.githubusercontent.com/52046920/195478269-b521d372-f123-43ad-826b-67d17b09ff9c.png)
* Truy cập vào Brower(Trình duyệt) và nhập địa chỉ của ESXi khi đang trong môi trường local với ESXi

![](https://user-images.githubusercontent.com/52046920/195478265-0fa28849-ff34-4af3-92bf-7f25d6331ff8.png)
* Sau đó đăng nhập bằng tài khoản root để truy cập giao diện quản lý ESXi VMware Host Client.

![](https://user-images.githubusercontent.com/52046920/195478443-1f44062d-7b0b-4215-b30f-72e7ec8db058.png)

![](https://user-images.githubusercontent.com/52046920/195479370-c69d076c-54f0-4152-a022-085f415de21e.png)

![](https://user-images.githubusercontent.com/52046920/195479372-71b622d0-8ea6-494c-b600-23e66c6650d7.png)

* Các Actions ESXi
    * Tại `Services` có thể tắt SSH và Console shell
    
    ![](https://user-images.githubusercontent.com/52046920/195480315-7683a295-d18c-4e33-9bdc-49b0ee546de6.png)
    * Chế độ bảo trì `Enter maintenance mode`

    ![](https://user-images.githubusercontent.com/52046920/195480320-7ab066f4-c89a-489a-bfa6-9dc2de300815.png)

    ![](https://user-images.githubusercontent.com/52046920/195480323-42c1e555-71fb-49d9-9de1-2526cd175fb8.png)

    * Tại `Lockdown Mode` có thể kích hoạt chế độ Lockdown giúp ngăn chặn các phiên đăng nhập mới diễn ra trên máy chủ. Do đó sẽ vô hiệu hóa được 1 số loại hình tấn công. Có 2 chế độ là:
        * `Normal Lockdown Mode`: DCUI vẫn hoạt động bình thường ở chế độ này. Nếu kết nối với hệ thống vCenter Server bị mất và không thể truy cập thông qua vSphere Client. Chỉ các tài khoản đặc quyền mơi dược đăng nhập vào ESXi để có thể thoát chế độ này. Những User được quyền truy cập chế độ khóa:
            * Các User trong dánh sách người dùng ngoại lệ cho chế độ Lockdown
            * User được xác định trong tùy chọn nâng cao DCUI.Access của Host. Các User này được truy cập khẩn cấp trực tiếp vào giao diện điều khiển. Các User này không yêu cầu quyền admin trên Host

        * `Strict Lockdown Mode`: Trong chế độ này, DCUI bị dừng. Nếu kết nối với Host ESXi bị mất và  vSphere Client không còn khả dụng, Host ESXi sẽ không còn khả dụng trừ khi ESXi Shell và SSH được bật và người dụng ngoại lệ được xác định(các tài khoản được truy cập trong chế độ khóa). Nếu không thì bắt buộc phải cài lại Host ESXi

    ![](https://user-images.githubusercontent.com/52046920/195480317-bb428324-5081-4946-ba3f-28f08b14c237.png)
    * Tại `Permissions` có thể tạo các user và cấp quyền cho chúng. Có 3 User tạo sẵn là vpxuser, DCUI và root(được tạo khi cài đặt ESXi)

    ![](https://user-images.githubusercontent.com/52046920/195480329-8a1db4d8-fa64-48b0-9181-e54e4c24781b.png)

    ![](https://user-images.githubusercontent.com/52046920/195480326-93b30244-624a-407e-84fc-f791a046526b.png)


    * Tại `SSH Console` có thể truy cập vào ESXi bằng chế độ SSH

    ![](https://user-images.githubusercontent.com/52046920/195480334-38f0f801-8764-41d9-9ccf-26cd6712a6b6.png)

    ![](https://user-images.githubusercontent.com/52046920/195481506-0748b4d8-e1a6-404e-bd2b-0d883ae910b6.png)
    * Tại chế độ `Generate support bundle` có thể tạo một gói hỗ trợ(Generate support bundle) cho máy chủ ESXi mà bạn đã đăng nhập. Gói hỗ trợ chứa các tệp nhật ký và thông tin hệ thống mà bạn có thể sử dụng để chẩn đoán và giải quyết sự cố.

    ![](https://user-images.githubusercontent.com/52046920/195480332-0c92841f-e3b6-4ff0-bec0-01c07b37aa90.png)

    ![](https://user-images.githubusercontent.com/52046920/195480336-3541a271-91e5-4736-a097-578ba576a3ec.png)

    ![](https://user-images.githubusercontent.com/52046920/195481074-60f096d9-91ee-410e-90bc-9bdbea8b66cb.png)
# Lab
## Tạo Storage trên ESXi
* Thêm ổ cứng cho máy ảo ESXi theo các bước sau

![](https://user-images.githubusercontent.com/52046920/195610539-f5206a77-d1e2-46a1-b8e8-631a23d3568b.png)

![](https://user-images.githubusercontent.com/52046920/195610545-9fc690b3-625f-43b0-85f2-ee51785b53f7.png)

![](https://user-images.githubusercontent.com/52046920/195610548-01f7d288-3dea-47b0-8ce4-102c9cbf7f85.png)

![](https://user-images.githubusercontent.com/52046920/195610552-8ad2f8be-4805-4419-9cc0-fd05b27a59e5.png)

![](https://user-images.githubusercontent.com/52046920/195610555-dad682e2-8bb7-429c-9caa-0296aee8006e.png)

![](https://user-images.githubusercontent.com/52046920/195610557-4d33251a-66c4-4f40-8a2c-8f485ae9ba17.png)

![](https://user-images.githubusercontent.com/52046920/195610559-c5f84a67-0fc9-445f-9718-e7a99d0a9977.png)

![](https://user-images.githubusercontent.com/52046920/195610561-6f9cb99a-ec28-4a5a-8357-f68dc7516de1.png)

* Quay lại web quản trị Click vào `Storage`

![](https://user-images.githubusercontent.com/52046920/195610564-52523f68-1d71-418c-81ac-f5bba06d262c.png)
* Chọn `New datastore`

![](https://user-images.githubusercontent.com/52046920/195610568-f9803fa6-b013-447a-a772-8368c3f3a107.png)
* Chọn `Create new VMFS datastore`

![](https://user-images.githubusercontent.com/52046920/195610571-e03623a7-4f3f-4b56-ba18-7030e7a3e5e1.png)
* Đặt tên cho Storage, chọn ổ đĩa dùng làm Storage sau đó bấm `Next`

![](https://user-images.githubusercontent.com/52046920/195610573-2c49c2fb-aab6-4276-aa7c-f8dd606506ea.png)
* Để mặc định sau đó bấm `Next`

![](https://user-images.githubusercontent.com/52046920/195610578-196c4e4a-d67b-41ae-ad0e-98c8d48eda39.png)
* Bấm Finish để hoàn tất khởi tạo `Storage`

![](https://user-images.githubusercontent.com/52046920/195610581-26a0c6be-515e-4f8d-8928-8977367bbc22.png)
* Chọn `Yes`

![](https://user-images.githubusercontent.com/52046920/195610585-9b5a13b8-58af-4735-b1d6-6217f5d14eae.png)
* Storage đã được tạo thành công

![](https://user-images.githubusercontent.com/52046920/195610589-51f738d0-3001-4d97-be53-e5ff28104209.png)


## Đẩy file ISO lên trên Storage của ESXi
* Chọn Storage vừa tạo

![](https://user-images.githubusercontent.com/52046920/195610593-78b10d83-7895-487c-84d5-df28e0a1cdc0.png)
* Chọn `Datastore browser`

![](https://user-images.githubusercontent.com/52046920/195610596-6b26081a-9ba1-4161-84ab-ac58e28871c5.png)
* Tạo 1 thư mục chưa ISO của các OS

![](https://user-images.githubusercontent.com/52046920/195610598-d65b934d-e3f0-4ab0-84b2-1977138e0983.png)
* Bấm chọn thư mục `Iso` vừa tạo sau đó click `Upload`

![](https://user-images.githubusercontent.com/52046920/195610600-c0cca705-363d-4fea-8164-d32af7acc21f.png)
* Chọn File từ máy thật và để Upload lên thử mục `Iso` của ESXi sau đó chờ đợi file ISO được upload lên

![](https://user-images.githubusercontent.com/52046920/195610602-4de235a9-de5c-4b8d-93a7-33eccba95ad5.png)
* File ISO của Win7 đã được Upload lên trên thư mục `Iso`

![](https://user-images.githubusercontent.com/52046920/195610608-5bfd62d1-f186-4425-8fbb-a6e7c7596877.png)

## Cài đặt máy ảo
* Chọn `Host`

![](https://user-images.githubusercontent.com/52046920/195610615-a1f2a815-2101-444b-be24-bbbfa033163a.png)
* Chọn `Create/Register VM` để tiến hành cài đặt máy ảo

![](https://user-images.githubusercontent.com/52046920/195610619-fc5f7b73-b5b8-4bd7-8cf5-c93eabd1ad91.png)
* Chọn `Create a new virtual machine`sau đó click `Next`

![](https://user-images.githubusercontent.com/52046920/195610626-b8cc0cfa-97c5-4826-b749-1e5bc31131f8.png)
* Đặt tên cho máy ảo, Chọn họ nhà OS và Version OS muốn cài đặt sau đó click `Next`

![](https://user-images.githubusercontent.com/52046920/195610629-150fd8e7-a55a-4077-8c25-bd98d2dba866.png)
* Chọn Storage lưu trữ máy ảo

![](https://user-images.githubusercontent.com/52046920/195610638-dc913e38-19a2-462a-ae00-cdf87b362510.png)

* Tiến hành hiết lập các thông số phần cứng ảo cho máy ảo như sau
* Tại CPU lựa chọn các thông số cho CPU và chọn `Enable CPU Host Add` để có thể chỉnh sửa CPU sau khi cài xong VM ngay cả khi VM đang chạy

![](https://user-images.githubusercontent.com/52046920/195610641-21559af3-6a42-46a6-884c-73b13f335cfd.png)

* Thiết lập thông số cho Ram và mục `Memory Hot Plug` tích chọn `Enable` để có thể thay đổi thông số cho Ram sau khi cài VM kể cả khi VM vẫn đang chạy

![](https://user-images.githubusercontent.com/52046920/195610643-9d2ff258-b4b4-4614-a41f-ce6909c76ea0.png)

* Lựa chọn đường dẫn file ISO để tiến hành cài đặt bằng cách lựa chọn `CD/DVD Drive 1`

![](https://user-images.githubusercontent.com/52046920/195610646-d7802756-c3d5-4907-897d-5c2ba37bd3f7.png)
* Click chọn `Datastorage ISO file`

![](https://user-images.githubusercontent.com/52046920/195610649-5e5ae1e2-2723-4c39-86e0-d1730206edd0.png)
* Chọn file ISO Đã đẩy lên ở bước trước

![](https://user-images.githubusercontent.com/52046920/195610654-9593a66f-c9e7-43ff-b66e-d9360afcf06b.png)
* Click `Next` sau khi đã thiết lập xong phần cứng ảo

![](https://user-images.githubusercontent.com/52046920/195610656-2a8209ad-816e-4dbc-95fd-692ee6fed8ed.png)
* Kiểm tra lại thông số phần cứng trước khi hoàn thành thiết lập cài đặt, sau đó click `Finish`.

![](https://user-images.githubusercontent.com/52046920/195610658-69557a61-0097-4c8d-95fb-ab5a4832357e.png)

* Lựa chọn Virtual Machines

![](https://user-images.githubusercontent.com/52046920/195610661-ed8cb399-781f-4a10-8d8c-8cc4fc8398c6.png)

* Chọn VM vừa tạo

![](https://user-images.githubusercontent.com/52046920/195610664-c4dd2d0b-1fdb-4909-be4d-fa2e1fa7188e.png)

![](https://user-images.githubusercontent.com/52046920/195610668-a14f2677-ce54-478a-b2e2-9e1b92346167.png)

* Khởi động VM

![](https://user-images.githubusercontent.com/52046920/195610673-6d024e1a-e5d5-4361-b218-b0255f782296.png)

* Click vào cửa sổ để mở cửa sổ giao diện của VM

![](https://user-images.githubusercontent.com/52046920/195610676-04586037-7223-4b9a-ab9c-33b4ae79b21d.png)

* Cài đặt Window như bình thường

![](https://user-images.githubusercontent.com/52046920/195610679-01ed566c-6cf4-4093-acb8-9d58bf2a34b5.png)

* Để chỉnh sửa lại cấu hình phần cứng của VM lựa chọn như sau

![](https://user-images.githubusercontent.com/52046920/195610690-8ebcc3ba-f5c3-410d-9e32-743f536c0eda.png)

* Thay đổi lại Card mạng

![](https://user-images.githubusercontent.com/52046920/195610697-164cdef9-6435-45f4-bc5e-42ad643d9042.png)
## ***2. vSphere CLient***
## ***3. CLI***
