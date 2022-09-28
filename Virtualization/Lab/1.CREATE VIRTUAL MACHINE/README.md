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

# BÀI LAB TẠO VM
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I Bước 1: Pre-Implementation - Bước trước triển khai]()
# [VM-1]()
## &ensp; [II. Bước 2: Implementation Procedure - Quy trình thực hiện]()
## &ensp; [III Post-Implementation Steps - Các bước sau khi triển khai]()
## &ensp; &ensp; [1. Khởi động VM]()
## &ensp; &ensp; [2. Cài đặt VMware Tools]()
## &ensp; &ensp; [3. Đổi tên PC thành tên giống với VMname đã đặt]()
## &ensp; &ensp; [4. Thiết lập địa chỉ IP]()
## &ensp; &ensp; [5. Thêm hệ thống vào tên miền(Nếu được yêu cầu)]()
## &ensp; &ensp; [6. Kích hoạt OS khách license]()
## &ensp; &ensp; [7. Đổi time zone phù hợp]()
## &ensp; &ensp; [8. Tắt bảo mật của IE cho Window Server]()
## &ensp; &ensp; [9. Tắt tường lửa]()
## &ensp; &ensp; [10. kích hoạt RDP/SSH]()
## &ensp; &ensp; [11. Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa]()
## &ensp; &ensp; [12. Cài đặt các phần mềm đặc biệt theo yêu cầu]()
## &ensp; &ensp; [13. Bảo mật VM OS khách]()
## &ensp; &ensp; [14. Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng]()
# [VM-2]()
## &ensp; [II. Bước 2: Implementation Procedure - Quy trình thực hiện]()
## &ensp; [III Post-Implementation Steps - Các bước sau khi triển khai]()
## &ensp; &ensp; [1. Khởi động VM]()
## &ensp; &ensp; [2. Cài đặt VMware Tools]()
## &ensp; &ensp; [3. Đổi tên PC thành tên giống với VMname đã đặt]()
## &ensp; &ensp; [4. Thiết lập địa chỉ IP]()
## &ensp; &ensp; [5. Thêm hệ thống vào tên miền(Nếu được yêu cầu)]()
## &ensp; &ensp; [6. Kích hoạt OS khách license]()
## &ensp; &ensp; [7. Đổi time zone phù hợp]()
## &ensp; &ensp; [8. Tắt bảo mật của IE cho Window Server]()
## &ensp; &ensp; [9. Tắt tường lửa]()
## &ensp; &ensp; [10. kích hoạt RDP/SSH]()
## &ensp; &ensp; [11. Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa]()
## &ensp; &ensp; [12. Cài đặt các phần mềm đặc biệt theo yêu cầu]()
## &ensp; &ensp; [13. Bảo mật VM OS khách]()
## &ensp; &ensp; [14. Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng]()
***
# ***Các bước thực hiện bài lab***
# ***I Bước 1: Pre-Implementation - Bước trước triển khai***
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

# ***VM-1***
# ***II. Bước 2: Implementation Procedure - Quy trình thực hiện***
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

# ***Cài đặt OS***
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


# ***III Post-Implementation Steps - Các bước sau khi triển khai***
## ***1. Khởi động VM***
* Tại giao diện của VMware Workstation click chọn `VM-1`

![](https://user-images.githubusercontent.com/52046920/192476160-02b183aa-75d6-44fa-acef-2b4446b933c5.png)

* Khởi động VM-1 bằng cách click vào `Power in this vitual machine`

![](https://user-images.githubusercontent.com/52046920/192476170-88024152-faa4-4c27-bfed-60cffc7b92e3.png)


## ***2. Cài đặt VMware Tools***
* Click chuột phải chọn `Install VMware Tools...`

![](https://user-images.githubusercontent.com/52046920/192665241-82444cdc-7175-4454-9f05-9eca86597839.png)

* Vào My Computer chọn `DVD Drive (D:) VMware Tools` để tiến hành cài đặt VMware Tools

![](https://user-images.githubusercontent.com/52046920/192665247-cadfe94b-ec6e-4a65-a31e-b38c98297eff.png)

* Click `Next`

![](https://user-images.githubusercontent.com/52046920/192665250-cdf1511d-3b6b-4c70-9f66-64dfad147e44.png)

* Chọn giá trị mặc định là `Typical` rồi click `Next`

![](https://user-images.githubusercontent.com/52046920/192665251-533e0345-0e26-48c7-9014-0d078345f7e1.png)

* Click `Install để tiến hành cài đặt`

![](https://user-images.githubusercontent.com/52046920/192665255-a320b45f-7867-499c-8a4d-425363a37d87.png)

* Cài đặt hoàn thành Click `Finish`

![](https://user-images.githubusercontent.com/52046920/192665257-b1b627ed-efea-43c4-ab1d-a1a86528ad74.png)

* Restart lại VM-1

![](https://user-images.githubusercontent.com/52046920/192665258-eabb5a72-9eb1-4062-adac-e89bce489e6c.png)

## ***3. Đổi tên PC thành tên giống với VMname đã đặt***
* Thay đổi tên Computer name giống như tên hiển thị máy ảo có 2 cách
* C1:
    * Chọn `Server Manager`

    ![](https://user-images.githubusercontent.com/52046920/192665269-78bb24a5-ae2c-461c-b948-ae4c4d00fb2f.png)
    * Chọn Local Server rồi click vào bên cạnh Computer name
    
    ![](https://user-images.githubusercontent.com/52046920/192671701-94ea53cd-ec49-4739-aab7-9233f9f0e353.png)
    * Click vào change

    ![](https://user-images.githubusercontent.com/52046920/192671706-007a87df-7d8a-4e5e-9ec4-20928defacc2.png)
    * Đổi tên PC thành VM-1 sau đó click `OK`

    ![](https://user-images.githubusercontent.com/52046920/192671709-47394e28-7d33-4b49-9b39-24a163f2396f.png)
    * Reset máy để hoàn thành thiết lập

    ![](https://user-images.githubusercontent.com/52046920/192671711-2e47abb4-af5a-457a-b20d-e614d1188a33.png)

    ![](https://user-images.githubusercontent.com/52046920/192671714-472b84a5-a22d-4339-afe1-ef7c89e964d1.png)
* C2:
    * Click chuột phải vào `This PC` xong chọn `Properties`

    ![](https://user-images.githubusercontent.com/52046920/192671702-88f5a823-8e17-49a8-a869-4103d59d4901.png)
    * Chọn `Change setting`

    ![](https://user-images.githubusercontent.com/52046920/192671704-66f3b9c1-de0d-41b8-b0b5-2275bcf398be.png)
    * Sau đó cửa số `System properties` hiện ra và thực hiện như C1
## ***4. Thiết lập địa chỉ IP***
* Thiết lập lại địa chỉ IP nếu có yêu cầu
## ***5. Thêm hệ thống vào tên miền(Nếu được yêu cầu)***
* Thêm hệ thống tên miền nếu có yêu cầu
## ***6. Kích hoạt OS khách license***
* Sử dụng key kích hoạt license cho Windows Server
## ***7. Đổi time zone phù hợp***
* Có 2 cách
* C1:
    * Lựa chọn Windows Server Essenstials Dashboard

    ![](https://user-images.githubusercontent.com/52046920/192665259-3a7f6d4d-d227-4640-800a-ffa1618b25dc.png)
    * Chọn `Date and time settings` sau đó click change system date and time settings

    ![](https://user-images.githubusercontent.com/52046920/192665260-af20d70c-efb7-4510-a269-be73ba0e00fe.png)

    * Chọn `Change time zone...`

    ![](https://user-images.githubusercontent.com/52046920/192665262-b42990cf-9e06-4b0c-b996-186cb67df0eb.png)

    * Chọn Time zone đúng vùng như ở đây là `(UTC+07:00) Bangkok, Hanoi, Jakarta` sau đó click `OK`

    ![](https://user-images.githubusercontent.com/52046920/192665263-fe550939-cc58-4e5d-a4a0-1c466279a02b.png)

    * Thời gian đã được thiết lập thành thời gian thực, click `OK` để hoàn thành

    ![](https://user-images.githubusercontent.com/52046920/192665264-3efc2222-2da6-489c-9989-9dd891b54d76.png)

* C2:
    * Chọn `Server Manager`

    ![](https://user-images.githubusercontent.com/52046920/192665269-78bb24a5-ae2c-461c-b948-ae4c4d00fb2f.png)

    * Chọn `Local Server` sau đó chọn trường bên cạnh Time zone

    ![](https://user-images.githubusercontent.com/52046920/192668383-6b34f7e0-2f6e-4b4e-aa48-db7d0bb90b9c.png)
    * Các bước còn lại giống bước 1
## ***8. Tắt bảo mật của IE cho Window Server***
* Chọn `Server Manager`

![](https://user-images.githubusercontent.com/52046920/192665269-78bb24a5-ae2c-461c-b948-ae4c4d00fb2f.png)
* Chọn Local Server rồi click vào `On` bên cạnh `IE Sercurity Configuration`

![](https://user-images.githubusercontent.com/52046920/192665274-e408cfd8-76d5-44c9-8b2a-1449bfdaf389.png)

* Tích hết vào off rồi click `OK`

![](https://user-images.githubusercontent.com/52046920/192665276-5378eb15-2e39-4224-bc90-06ff345ca7d3.png)
## ***9. Tắt tường lửa***
* Tắt tường lửa của máy ảo nếu được yêu cầu
## ***10. kích hoạt RDP/SSH***
* Chọn `Server Manager`

![](https://user-images.githubusercontent.com/52046920/192665269-78bb24a5-ae2c-461c-b948-ae4c4d00fb2f.png)

* Chọn Local Server rồi click vào remote desktop

![](https://user-images.githubusercontent.com/52046920/192665277-f6b4749a-4297-4e07-969d-efae585afb7a.png)

* Nếu 2 mục `Allow remote connections to this computer` và trường bên dưới đấy chưa được tích chọn thì tích chọn sau đó click `OK` để hoàn thành

![](https://user-images.githubusercontent.com/52046920/192665279-8bfe764b-9f7c-4acb-babe-856048636c94.png)

## ***11. Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa***
* Mở Remote Desktop trên máy thật chứa máy ảo

![](https://user-images.githubusercontent.com/52046920/192671718-bba39181-df96-47c5-9ae4-ab4808276fde.png)

* Kiểm tra IP của máy ảo

![](https://user-images.githubusercontent.com/52046920/192671715-cc0d0120-fa49-4933-a7a6-6d58ebfddaab.png)

* Remote đến VM-1

![](https://user-images.githubusercontent.com/52046920/192665282-06aa01f5-0e47-4bfd-8bcc-c895d86e5ed7.png)

* Nhập user password

![](https://user-images.githubusercontent.com/52046920/192665284-69640f10-a87e-460b-ad09-d1b77f130ecb.png)

* Click `Yes` để kết nối đến VM-1

![](https://user-images.githubusercontent.com/52046920/192665286-bba12766-cd47-4cb0-999a-ca169a9981ba.png)

* Trong trường hợp xảy ra lỗi như sau

![](https://kb.hostvn.net/kb_upload/image/screenshot_3(1).png)
* Lỗi này xảy ra là do 1 số chính sách bảo mật của Window nên nó ảnh hưởng đến Remote desktop nếu remote bằng các phiên bản khác nhau. 
* Để khắc phục lỗi này, đứng tại máy sử dụng để remote đến có thể làm theo các bước dưới đây:

    * Bước 1: Bấm phím Windows + R  và gõ vào regedit để mở registry.

    ![](https://kb.hostvn.net/kb_upload/image/screenshot_4(3).png)
    * Bước 2: Truy cập theo đường dẫn [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System và tạo tạo key CredSSP nếu chưa có.

    ![](https://kb.hostvn.net/kb_upload/image/24.jpg)
    
    ![](https://kb.hostvn.net/kb_upload/image/screenshot_5(2).png)
    * Bước 3: Tạo tiếp key Parameters bên trong key CredSSP

    ![](https://kb.hostvn.net/kb_upload/image/screenshot_6(2).png)
    * Bước 4: Trong Parameters tạo DWORD Value và đặt tên là AllowEncryptionOracle

    ![](https://kb.hostvn.net/kb_upload/image/25.jpg)

    ![](https://kb.hostvn.net/kb_upload/image/26.jpg)
    * Bước 5: Click đúp chuột vào key AllowEncryptionOracle và đăt Value data là 2

    ![](https://kb.hostvn.net/kb_upload/image/screenshot_7(3).png)
* Sau khi thực hiện xong các bước sau có thể Remote Desktop vào VM-1
## ***12. Cài đặt các phần mềm đặc biệt theo yêu cầu***

## ***13. Bảo mật VM OS khách*** 

## ***14. Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng***



# ***VM-2***

# ***II. Bước 2: Implementation Procedure - Quy trình thực hiện***
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

# ***Cài đặt OS cho VM-2***

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
# ***III Post-Implementation Steps - Các bước sau khi triển khai***

## ***1. Khởi động VM***
* Tại giao diện của VMware Workstation click chọn `VM-2`

* Khởi động VM-1 bằng cách click vào `Power in this vitual machine`
* Khởi động centos 7 và đăng nhập vào hệ thống dưới quyền Root

![](https://user-images.githubusercontent.com/52046920/192715592-b41706b1-6f77-4477-90ff-7b7932d858dc.png)

![](https://user-images.githubusercontent.com/52046920/192715600-11b76083-9c61-4c4e-8c9a-bdf86f61090c.png)

## ***2. Cài đặt VMware Tools***
* Chạy các câu lệnh sau để cài đặt VM tools

```shell
mount /dev/cdrom /mnt
cd /mnt
#Tùy từng phiên bản có thể kiểm tra lại bằng câu lệnh ls
cp VMwareTools-10.3.10-13959562.tar.gz /tmp
cd /tmp
#Tùy từng phiên bản có thể kiểm tra lại bằng câu lệnh ls
tar -xzvf VMwareTools-10.3.10-13959562.tar.gz
cd vmware-tools-distrib
./vmware-install.pl

#Enter để chọn default cho tất cả các lựa chọn và chọn y cho các lựa chọn
#Cài đặt xong unmout file cài đặt trong /mnt
umount /mnt
```


## ***3. Đổi tên PC thành tên giống với VMname đã đặt***
* Thiết lập Hostname bằng câu lệnh
```shell
hostnamectl
hostnamectl set-hostname VM-2
```

![](https://user-images.githubusercontent.com/52046920/192715624-d6562251-4de1-4c2a-917d-d3f38f1222c8.png)
## ***4. Thiết lập địa chỉ IP***
* Kiểm tra mạng
```shell
nmcli d
```

![](https://user-images.githubusercontent.com/52046920/192715603-e16844c0-3e13-48fd-9944-8785b86a46c1.png)

* Khởi động card mạng lên bằng cách chỉnh sửa file
```shell
vi /etc/sysconf ig/network-scripts/ifcfg-ens33
```

![](https://user-images.githubusercontent.com/52046920/192715607-293cf7f8-270c-470b-9787-864388b58409.png)

* Đổi tham số ONBOOT = no thành ONBOOT = yes và mặc định là DHCP. Nếu muốn đặt ip tĩnh thì, sửa đổi BOOTPROTO = dhcp thành BOOTPROTO = static thêm các tham số sau vào file trên

```shell
IPADDR=[Địa chỉ IP muốn đặt]
NETMASK=[Dải mạng]
GATEWAY=[Địa chỉ Default gateway]
DNS1=[DNS1]
DNS2=[DNS2]
#Ví dụ
IPADDR=192.168.68.10
NETMASK=192.168.68.0
GATEWAY=192.168.1.1
DNS1=8.8.8.8
DNS2=8.8.4.4
```

* Save file lại và thoát ra sau đó reset lại dịch vụ network sau đó kiểm tra

```shell
service network restart
nmcli d
```

![](https://user-images.githubusercontent.com/52046920/192715610-c33eacd0-bfe9-4a03-bb09-77d2310dfc69.png)
* Kiểm tra IP DHCP cấp động bằng câu lệnh 
```shell 
ipa
```

![](https://user-images.githubusercontent.com/52046920/192715615-89feaa4f-dd58-4bbc-96de-fc0d75e14482.png)
## ***5. Thêm hệ thống vào tên miền(Nếu được yêu cầu)***
* Tùy theo yêu cầu. Ở đây không thiết lập
## ***6. Kích hoạt OS khách license***
* Centos 7 là mã nguồn mở không cần kích hoạt license
## ***7. Đổi time zone phù hợp***
* Kiểm tra Time zone bằng câu lệnh 
```shell
timedatectl
```

![](https://user-images.githubusercontent.com/52046920/192715632-de8eb231-0103-4d69-b5d8-48967eeb0139.png)

* Kiểm tra list timezone
```shell
timedatectl list-timezones
```

![](https://user-images.githubusercontent.com/52046920/192715636-a3390709-6bf1-41cb-9398-79cccf81c1fc.png)

* Chọn Time zone là Asia/Ho_Chi_Minh 
```shell
timedatectl set-timezone Asia/Ho_Chi_Minh
```

* Đã chuyển đổi time zone xong

![](https://user-images.githubusercontent.com/52046920/192715641-12555956-0695-4dc8-bb47-271d57cdd4ad.png)
## ***8. Tắt bảo mật của IE cho Window Server***
* Đây là Linux nên không cần
## ***9. Tắt tường lửa***
* Tùy theo yêu cầu. Có thể tắt tường lửa bằng câu lệnh
```shell
systemctl disable firewalld
```
## ***10. kích hoạt RDP/SSH***
* Do cổng dịch vụ ssh trên centos 7 được mở sẵn lúc mới cài đặt vậy nên không cần phải thiết lập

## ***11. Kiểm tra VM đã có thể truy cập qua RDP/SSH chưa***
* Kiểm tra IP của VM-2

![](https://user-images.githubusercontent.com/52046920/192715615-89feaa4f-dd58-4bbc-96de-fc0d75e14482.png)
* Thực hiện SSH đến VM-2

![](https://user-images.githubusercontent.com/52046920/192715630-ef2c813a-a866-437b-af97-ec49f675cf25.png)
## ***12. Cài đặt các phần mềm đặc biệt theo yêu cầu***
* Tùy theo yêu cầu
## ***13. Bảo mật VM OS khách*** 
## ***14. Cung cấp thông tin chi tiết về máy ảo cho người dùng cuối/Client/khách hàng***


