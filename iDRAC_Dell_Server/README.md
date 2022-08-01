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

# THỰC HIỆN THAO TÁC TRÊN SERVER QUA iDRAC
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
# ***I.	Tổng quan iDRAC***
* Ngày nay, đối với một người kỹ sư hệ thống 24 tiếng một ngày dường như không đủ để tối ưu cho hệ thống của mình. Thực tế đã xảy ra rất nhiều trường hợp server vật lý để ở Datacenter gặp sự cố về phần cứng mà người quản trị không thể giám sát và có cảnh báo kịp thời dẫn tới có những sự cố downtime đáng tiếc, mang lại thiệt hại lớn cho cá nhân, tổ chức, doanh nghiệp. Có những công cụ nhỏ tích hợp sẵn trong dòng server Dell nhưng không hẳn kỹ sư hệ thống nào cũng biết đó là việc sử dụng chức năng iDRAC.

* Đối với dòng server DELL thế hệ mới model Power Edge Server thế hệ thứ 12 của Dell thì đều có tích hợp iDRAC (Integrated Dell Remote Access Controller) cung cấp tính năng để quản lý các thông số hardware của server từ xa, troubleshoot, remote thông qua một giao diện web người quản trị có thể không phải di chuyển tới server cắm màn hình cũng có thể thao tác với server của mình.

* iDRAC được cấu hình thông qua một port riêng, kết nối qua đường RJ45 được cấu hình các thông số về network.

# ***II.	Cài đặt iDRAC***
* Khởi động server
* Ở đây có 4 chế độ
    * F2=system Setup
    * F10=Lifecycle Controller
    * F11=Boot Manager
    * F12=PXE Boot

    ![](https://user-images.githubusercontent.com/52046920/182092291-fa967152-96a7-4f76-af70-6e41ba2d0c56.png)
* Chọn F2 sau đó chờ đợi
* Tại system Setup Main Menu, chọn iDRAC settings

![](https://user-images.githubusercontent.com/52046920/182092274-0c41e99b-8b03-4f1f-9f38-dd1d038240f7.png)
* Chọn Network để chỉnh cấu hình
* Enable NIC chọn Enable
* NIC Selection: chọn card mạng phù hợp

![](https://user-images.githubusercontent.com/52046920/182092293-af8fe909-a3f3-4480-8347-a251fe79323b.png)
* Ở dây ip server được cấu hình là
    * ip là 10.14.11.48
    * subnetmask 255.255.255.0
* Hình ảnh mình họa

![](https://user-images.githubusercontent.com/52046920/182092287-3c789ac1-2ea2-431d-9012-f02914effe50.png)
* Sau đó qua lại chọn User Configuration

![](https://user-images.githubusercontent.com/52046920/182092282-1f7d89ad-3ab3-4647-85bc-1e983d31e744.png)
* ở đây ta thấy User Name mặc định là root ta có thể thay đổi hoặc giữ nguyên
* Click vào change Password để thiết lập mật khẩu.

![](https://user-images.githubusercontent.com/52046920/182092278-1fc9b079-d449-4a74-bc95-d43db1a2b250.png)
* Sao đó quay lại click finish rồi chờ đợi server reboot.
* Ở bên máy truy cập ta sẽ thiết lập ip sao cho cùng thuộc 1 dải mạng so với server.

![](https://user-images.githubusercontent.com/52046920/182092296-1a407249-ba30-4762-8620-06731e703ad2.png)
* Sau đó truy cập trình duyệt rồi tiến hành truy cập vào server và đăng nhập vào server

![](https://user-images.githubusercontent.com/52046920/182092297-99c7fe7d-e2c9-46c1-9461-410680304248.png)
* Giao diện của iDRAC 9

![](https://user-images.githubusercontent.com/52046920/182092300-c4f6dd2a-fb09-4d23-b7ab-24b822ea3da6.png)
* Trên trang quản lý của iDRAC sẽ bao gồm các Menu : Dashboard, System, Storage, Configuration, Maintenaince, và iDRAC Settings.

    * Dashboard : Thông tin tổng quan về hệ thống của Server.
    * System :
    * Storage :
    * Configuration :
    * Maintenance :
    * iDRAC Settings :

![](https://user-images.githubusercontent.com/52046920/182092305-2521e11c-3fb8-4efb-b959-934658974ea7.png)
## ***1.	Dashboard***
* Có thể chọn Graceful shutdown để shutdown server
* Truy cập vào giao diện dòng lệnh như kết nối trực tiếp với server chọn Start the Virtual Console.

![](https://user-images.githubusercontent.com/52046920/182092307-de41bda5-08be-4766-b71f-6cfce92aa2a5.png)
* Revent Logs ghi lại log các lỗi khi khởi động server

![](https://user-images.githubusercontent.com/52046920/182092314-af366cde-935b-42b5-89a0-b7256afbed4a.png)
## ***2.	System***
### ***a.	Overview***
* Summary:
    * Power State(Trạng thái nguồn): ở đây đang được bật
    * Model: Tên của thiết bị ở đây là PowerEdge R440
    * Host name
    * Operating Sytem: Hệ điều hành, do chưa cài nên sẽ không hiển thị
    * Operating System version: Phiên bản hệ điều hành
    * Service Tag: Mã định danh cho server
    * iDRAC MAC Address: địa chỉ Mac của iDRAC
    * License: Giấy phép

![](https://user-images.githubusercontent.com/52046920/182092320-7e668268-0ec3-43d6-b71f-4aeb878fc51a.png)
* Batteries(Pin): pin COSMOS

![](https://user-images.githubusercontent.com/52046920/182092746-9c07f40a-eae6-4c4d-9446-e1def451f778.png)

* Cooling: Hệ thống quạt làm mát và thông số nhiệt độ của server
    * Cooling Overview(Tổng quát)
    
    ![](https://user-images.githubusercontent.com/52046920/182095257-bcefde2a-b0c9-4a09-a76c-0089a3b90df2.png)
    * Fan(Thông số quạt) 

    ![](https://user-images.githubusercontent.com/52046920/182095261-f5ba82fd-6032-4dd6-a4c0-899b9adbd368.png)

    * Temperatures(Nhiệt độ phần cứng)
    
    ![](https://user-images.githubusercontent.com/52046920/182095264-a2b82e42-6f92-4e79-9a35-1ba25692de37.png)
* CPU(Thông số về CPU)

![](https://user-images.githubusercontent.com/52046920/182095537-a9dbc76d-bafb-411f-b661-4d40e4685ac1.png)
* Front Panel: đây là nguồn cấp dữ liệu trực tiếp hiển thị trên LEDS của bảng điều khiển phía trước, sử dụng phần này để ẩn hoặc hiện thông báo lỗi hiện tại từ bảng điều khiển phía trước (điều này không ngăn các thông báo lỗi trong tương lai xuất hiện trên bảng điều khiển phía trước)
![](https://user-images.githubusercontent.com/52046920/182096151-6a13cd11-5c51-4421-8e09-3a3050497120.png)

* Accelerator: Các thiết bị giúp gia tăng tốc độ xử lý: Card đồ họa(GPUs), FPGA(Field-programmable gate array) là một thiết bị bán dẫn có thể lập trình được hay có thể hiểu nó là một loại chip trắng cho phép người dùng có thể tái cấu hình lại kiến trúc theo ý người dùng để thực thi một chức năng cụ thể(RAM).

![](https://user-images.githubusercontent.com/52046920/182099214-e08549cb-4d99-4b7b-b9c7-c3ecd6191859.png)
* Instrusion: Phát hiện xâm nhập (Ở đây khung bảo vẹ đã được đóng lại và khóa lại)

![](https://user-images.githubusercontent.com/52046920/182099806-39c2b19b-4fcf-460e-ad30-9b611ef530a4.png)
* Memory(Ram): thông tin Ram
    * Memory Attributes

    ![](https://user-images.githubusercontent.com/52046920/182100614-c5e15c5e-a077-43e6-945b-87f74f73c3d4.png)
    * Individual Memory Detail

    ![](https://user-images.githubusercontent.com/52046920/182100622-57ae8b61-ed3e-4dc6-b0ac-bad58bf0bba6.png)
* Network Devices(Thiết bị mạng): Ở đây đang hiện thị 2 card mạng

![](https://user-images.githubusercontent.com/52046920/182101071-1cc7ca0e-703a-4dca-8f31-794523c6bae3.png)

* Power: Các thông số về nguồn

![](https://user-images.githubusercontent.com/52046920/182102072-d7bf7fe5-6c4b-4e1f-a661-332ec4ae1035.png)
![](https://user-images.githubusercontent.com/52046920/182102081-c102c12a-58ff-40f2-9a3d-538a26b5499f.png)

* Voltages: Các thông số về điện áp của nguồn

![](https://user-images.githubusercontent.com/52046920/182102083-9187abd2-2a3b-495c-8d84-d7352f761e46.png)
### ***b.	Details***
* Gồm thông tin chi tiết của 
    * System

    ![](https://user-images.githubusercontent.com/52046920/182103961-1979d58b-bdf3-458d-92ca-d448dc39dd66.png)
    * iDRAC
    
    ![](https://user-images.githubusercontent.com/52046920/182103969-587c8cb3-957a-40af-bd6c-a44ca138a47c.png)
    * Asset

    ![](https://user-images.githubusercontent.com/52046920/182103973-700b6acb-9347-48e7-aa62-5da2a009cde2.png)
### ***c.	Inventory***
* Gồm các thông tin về
    * Firmware Inventory(Các firmware của server): là "một loại chương trình máy tính cung cấp kiểm soát mức thấp cho phần cứng cụ thể của thiết bị".
    * Hardware Inventory(Phần cứng của server)

![](https://user-images.githubusercontent.com/52046920/182105027-48f3bc4d-ed13-445b-8fc5-5487b516b167.png)
![](https://user-images.githubusercontent.com/52046920/182105032-69796708-76a5-453e-83c5-4a463c2cc45c.png)
### ***d.	Performance***
* Chứ các thông tin về % sử dụng của RAM, CPU,... dưới dạng biểu đồ

![](https://user-images.githubusercontent.com/52046920/182105622-684f98b9-bfe6-4148-9f46-47378a735fa9.png)
### ***e.	HostOS***
![](https://user-images.githubusercontent.com/52046920/182105622-684f98b9-bfe6-4148-9f46-47378a735fa9.png)
## ***3.	Storage***
* Thông tin các ổ đĩa lưu trữ dữ liệu trên server
* Bảo gồm:
    * Summary: Thông tin tổng quan về phần cứng
    
    ![](https://user-images.githubusercontent.com/52046920/182107263-947c5976-6474-4357-9e78-56c538ce2ab5.png)
    * Controllers: các điều khiển ổ cứng (Card Raid)

    ![](https://user-images.githubusercontent.com/52046920/182107273-f9b79f31-c0d3-413d-921f-6ff67a95eda8.png)
    * Physical Disk: Ổ đĩa vật lý, Ở do server đang không lắp ổ cứng nên sẽ không hiển thị thông tin
    
    ![](https://user-images.githubusercontent.com/52046920/182107274-ced7a30f-6310-447a-a4b5-ef34c24941fb.png)
    * Virtual Disk: ổ đĩa ảo

    ![](https://user-images.githubusercontent.com/52046920/182107276-c4efa97c-0593-4d8d-b5cd-d5e4ce48f9b2.png)
    * Enclosures:

    ![](https://user-images.githubusercontent.com/52046920/182107277-c041aaaa-9855-4ecd-a948-47fc3855bc77.png)
## ***4.	Configuration***
* Cấu hình các phần của server
![](https://user-images.githubusercontent.com/52046920/182109331-95171e33-d01c-468e-ab49-305d391bc7c6.png)
## ***5.	Maintenance***
* Maintenance(Sự bảo trì)Gồm các thông số
![](https://user-images.githubusercontent.com/52046920/182110235-da5f7033-cbab-46c4-9632-ce1f3b47cf5f.png)
## ***6.	iDRAC Setting***
* Cấu hình và thong số của iDRAC
![](https://user-images.githubusercontent.com/52046920/182110239-0070aa81-030f-4150-ac19-c3ece504a6ca.png)