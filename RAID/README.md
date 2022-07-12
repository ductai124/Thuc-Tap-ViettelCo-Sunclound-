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

# TÌM HIỂU VỀ RAID
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. RAID là gì](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#iraid-l%C3%A0-g%C3%AC)

## &ensp; [1. RAID 0](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#1raid-0)

## &ensp; [2. RAID 1](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#2raid-1)

## &ensp; [3. RAID 1+0](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#3raid-10)

## &ensp; [4. RAID 5](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#4-raid-5)

## &ensp; [5. RAID 6](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#5-raid-6)

# [II. Cài đặt RAID](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#ic%C3%A0i-%C4%91%E1%BA%B7t-raid)

## &ensp; [1. Thiết lập RAID 1 trên centos7](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#1-thi%E1%BA%BFt-l%E1%BA%ADp-raid-1-tr%C3%AAn-centos7)

## &ensp; [2. Thiết lập RAID 5 trên Windows server 2016](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/tree/main/RAID#2-thi%E1%BA%BFt-l%E1%BA%ADp-raid-5-tr%C3%AAn-windows-server-2016)
***
# ***I.	RAID là gì***
* Raid là viết tắt của Redundant Array of Independent Disks. Là một giải pháp phòng hộ vì nó cho phép ghi dữ liệu lên nhiều đĩa cững cùng lúc. Về sau, Raid đã có nhiều biến thể giúp không chỉ đảm bảo an toàn dữ liệu mà còn giúp gia tăng đáng kể tốc độ truy xuất.
* Raid chỉ nên làm việc với các loại ổ cứng cùng dung lượng
* Sử dụng Raid phải chấp nhận sẽ tốn số lượng ổ nhiều hơn bình thường nhưng đổi lại sự an toàn dữ liệu
* Có thể dùng cho bất cứ hệ điều hành nào
* Có 4 loại Raid phổ biến
    * Raid 0
    * Raid 1
    * Raid 1+0
    * Raid 5

## ***1.	RAID 0***
* Là dạng Raid không giúp gì cho vấn đề bảo toàn dữ liệu. RAID 0 sử dụng một kĩ thuật gọi là “striping”. “Striping” phân chia khối dữ liệu đơn trải chúng qua các ổ cứng theo tuần tự. 
* Yêu cầu tối thiểu 2 ổ cứng. Khi đọc ghi dữ liệu Raid 0 cho phép máy tính ghi dữ liệu lên cả 2 ổ, mỗi ổ 1 nửa nếu làm tăng hiệu suất trao đổi dữ liệu. Tuy nhiên cũng chính vì vậy dữ liệu bị phân mảnh nếu một ổ gặp lỗi dữ liệu sẽ mất hết.
* Ưu điểm: Tăng tốc độ đọc ghi
* Nhược điểm: Không đảm bảo an toàn về dữ liệu còn tăng khả năng mất dữ liệu, không đúng so với mục đích của Raid.
* Đối tượng sử dụng: người dùng cá nhân là chủ yếu và có nhu cầu đọc ghi ổ cứng mạnh không quá đề cao việc mất mát dữ liệu.
![Raid 0](https://user-images.githubusercontent.com/52046920/178389092-79644dbc-961d-4be2-be84-1cb245beae12.png)
## ***2.	RAID 1***
* Đây là dạng Raid cơ bản có khả năng đảm bảo an toàn dữ liệu. Yêu cầu ít nhất 2 ổ cứng.RAID cung cấp phương pháp dự phòng dữ liệu đơn giản bằng kĩ thuật “mirroring” (nhân bản dữ liệu). Dữ liệu khi đọc ghi sẽ ghi ở 2 ổ giống hệt nhau. Trong trường hợp 1 ổ gặp sự cố dữ liệu cũng đã được ghi ở ổ còn lại đảm bảo sự an toàn của dữ liệu.
* Tuy nhiên khi sử dụng Raid 1 ta sẽ phải bỏ 1 ổ để chỉ sử dụng làm Mirroring nên dung lượng thực của hệ thống chỉ có dung lượng của 1 ổ
* Ưu điểm: An toàn về dữ liệu, khả năng hoạt động liên tục cao
* Nhược điểm: Hiệu suất không cao, chi phí cao do mất 1 nữa tài nguyên ổ cứng để giúp dữ liệu được an toàn
* Đối tượng sử dụng: Các dịch vụ lưu trữ, các Website nhỏ đến vừa không yêu cầu quá cao về tốc độ đọc ghi ổ cứng.
![Raid 1](https://user-images.githubusercontent.com/52046920/178389120-e1991635-8875-4b1e-9687-24416ba3d65c.png)
## ***3.	RAID 1+0***
* Là kết hợp của Raid 1 và Raid 0. Raid 1+0 Sở hữu tốc độ đọc ghi của Raid 0 vầ sự an toàn của Raid 1. Các kĩ thuật “mirroring” và “striping” kết hợp với nhau tạo ra hiệu quả dự phòng. Để có thể vận hành Raid 1+0 cần tối thiểu 4 ổ cứng. Dữ liệu sẽ được ghi lên đồng thời cả 4 ổ trong 
chia làm 2 cặp 1 ổ ghi và 1 ổ sao lưu. Dữ liệu sẽ được ghi như với Raid 0 đối với 2 ổ ghi và sẽ được sao lưu ra 2 ổ sao lưu giống với Raid 1
* Ưu điểm: An toàn về dữ liệu, khả năng hoạt động liên tục cao, tốc độ đọc ghi nhanh
* Nhược điểm: Chi phí cao do mất 1 nữa tài nguyên ổ cứng để giúp dữ liệu được an toàn và cần nhiều ổ để có thể vận hành số ổ bắt buộc phải là số chẵn. Vẫn có khả năng mất dữ liệu nếu cặp ổ ghi và ổ sao lưu cùng chết
* Đối tượng sử dụng: Raid 1+0 thích hợp với tất cả các đối tượng sử dụng (từ những yêu cầu về hiệu suất đến việc đảm bảo an toàn dữ liệu) Nếu đáp ứng được yêu cầu về chi phí.
![Raid 1+0](https://user-images.githubusercontent.com/52046920/178389160-1a640cdf-4150-4fd2-b6ae-5d24a34adc6d.png)
## ***4. RAID 5***
* Cũng là loại Raid lưu trữ truyền thống có thể tách ra lưu trữ các ổ cứng riêng biệt và vẫn có phương án dự phòng khi có sự cố phát sinh đối với 1 ổ bất kỳ. Để thiết lập Raid 3 cần ít nhất 3 ổ cứng. Phương pháp này sử dụng phân chia “parity” (chẵn lẻ) để duy trì dự phòng dữ liệu.
* Dữ liệu và bản sao lưu được chia lên tất cả các ổ cứng. Giả sử có n ổ (n>3)nguyên lý Raid 5 như sau:
    * Dữ liệu ghi vào tất cả các ổ trừ ổ cuối và sao lưu ghi vào ổ cuối.
    * Dữ liệu sao lưu ghi vào ổ n-1 các dữ liệu thì ghi vào các ổ còn lại theo thứ tự
    * Dữ liệu sao lưu ghi vào n-2, dữ liệu thì ghi vào các ổ còn theo thứ tự
    .....
    * Dữ liệu sao lưu ghi vào ổ 1, dữ liệu được ghi vào các ổ còn lại
    * Lặp lại từ đầu dữ liệu sao lưu vào ổ cuối nếu có dữ liệu mới.
* Ưu điểm: Nâng cao hiệu suất, an toàn dữ liệu
* Nhược điểm: Chi phí cao. không sử dụng được hết toàn bộ dung lượng của toàn bộ ổ(Tổng dung lượng sau cùng=Tổng dung lượng các ổ cứng trừ đi dung lượng 1 ổ). Khả năng mất dữ liệu là vẫn có nếu có từ 2 ổ bị hỏng trở lên. thời gian khôi phục ổ khá lâu vậy nên trong thời gian đó nếu hỏng thêm ổ nữa sẽ mất sạch dữ liệu
* Đối tượng: Tất cả những website, dịch vụ, ứng dụng có số lượng truy cập và yêu cầu tài nguyên từ nhỏ đến lớn.
![Raid 5](https://user-images.githubusercontent.com/52046920/178389189-669a2659-2ddb-4f7a-85ba-cad214ae93aa.png)

## ***5. RAID 6***
* Giống với RAID 5 tuy nhên dữ liệu parity được ghi vào 2 ổ đĩa. Vậy nên để sử dụng RAID 6 cần ít nhất 4 ổ. Dữ liệu chỉ mất khi 2 ổ cùng hỏng mà điều này khó xảy ra.
* Dữ liệu sẽ được ghi vào 2 ổ còn 2 parity sẽ được ghi vào 2 ổ còn lại ví dụ có 4 ổ đĩa:
    * Ta ghi dữ liệu 1a và 1b vào 2 ổ đầu và 2 ổ 1 và 2, ổ 3 và 4 sẽ để lưu parity
    * Dữ liệu 2a và 2b sẽ ghi vào ổ 1 và 4, dữ liệu parity sẽ ghi vào ổ 2 và 3
    * Dữ liệu 3a và 3b sẽ ghi vào ổ 3 và 4, dữ liệu parity ghi vào ổ 1 và 2
    * Dữ liệu 4a và 4b sẽ ghi vào ổ 2 và 3, dữ liệu parity ghi vào ổ 1 và 4
    * Nếu có dữ liệu ghi thêm thì lặp lại quy trình trên.
* Ưu điểm: Giống Raid 5 tuy nhiên độ an toàn cao hơn do 2 ổ trở lên chết cùng lúc dữ liệu mới chết mà điều này hiếm khi xảy ra.
* Nhược điểm: Ghi dữ liệu chậm hơn Raid 5(Chậm hơn khoảng 20%) do dữ liệu parity bổ sung phải được tính toán. Việc khôi phục dữ liệu mất nhiều thời gian và trong qua trình khôi phục vẫn có rủi ro như Raid 5. Dù an toàn hơn Raid 5 nhưng vẫn có khả năng mất dữ liệu nếu chết từ 2 ổ trở lên cùng 1 lúc mặc dù điều này khó xảy ra. dung lượng sử dụng sẽ - đi dung lượng 2 ổ do dùng để làm backup dữ liệu.
* Đối tượng: Ưu tiên sử dụng trong các server ứng dụng và file mà sử dụng nhiều ổ lớn để lưu trữ 
![Raid 6](https://user-images.githubusercontent.com/52046920/178406755-b2702ef1-a97d-4da1-bfdb-696131d5c271.png)

# ***II.	Cài đặt RAID***
## ***1. Thiết lập RAID 1 trên centos7***
* Bước 1: Cập nhật hệ thống và cài đặt mdadm để quản lý RAID

Để thiết lập RAID1 trên hệ điều hành Linux chúng ta cần thực hiện cập nhật (update) hệ thống và cài đặt gói mdadm.

![Cài đặt mdadm](https://user-images.githubusercontent.com/52046920/178436809-d3124035-e88f-4eb3-8fc3-441be64dbaf4.png)
* Bước 2: Kiểm tra thông tin ổ đĩa trên máy:

    * Trước khi tạo RAID1, chúng ta cần có ít nhất hai ổ đĩa cứng chạy lệnh sau để kiểm tra:
    ```bash
    fdisk -l | grep sd
    ```
    ![Kiểm tra ổ cứng](https://user-images.githubusercontent.com/52046920/178436811-645d00cc-a326-4960-aeda-cc92f1c6bd4e.png)

    * Ta thấy có 2 đĩa cứng mới. Thực hiện kiểm tra xem các ổ cứng có sử dụng RAID nào chưa bằng lệnh sau.
        ```bash
        mdadm -E /dev/sd[b-c]
        ```
        ![Kiểm tra đã có Raid sẵn hay chưa](https://user-images.githubusercontent.com/52046920/178436816-23726b2e-a702-4442-b8fc-61accd42c543.png)

* Bước 3: Tạo phân vùng đĩa cứng. Tạo phân vùng đĩa sdb và sdc cho RAID
    * Tạo phân vùng trên ổ đĩa sdb.
    * Chạy lệnh fdisk /dev/sdb để tạo phân vùng cho sdb và thực hiện các thao tác sau:
        * Nhấn n để tạo phân vùng mới.
        * Sau đó chọn p cho phân vùng chính.
        * Tiếp theo chọn số phân vùng là 1 .
        * Nhập giá trị ban đầu, giá trị kết thúc và nhấn phím Enter.
        * Tiếp theo nhấn p để in phân vùng đã được tạo.
    
    ![Phân vùng ổ cứng](https://user-images.githubusercontent.com/52046920/178436819-c9b46992-4758-4fa2-a3d4-590169cbab5e.png)
    
    * Thực hiện các bước sau đây để tạo Linux RAID tự động trên các phân vùng:
        * Nhấn L để liệt kê tất cả các loại có sẵn.
        * Nhập t để chọn phân vùng.
        * Nhập fd để chọn Linux RAID tự động và nhấn Enter để áp dụng.
        * Sử dụng phím p để in những thay đổi.
        * Cuối cùng chúng ta nhấn phím w lưu các thay đổi.

    ![Phân vùng ổ cứng](https://user-images.githubusercontent.com/52046920/178436822-90aa4e01-52f2-4056-a389-997b22eee838.png)

    * Tương tự thực hiện tạo phân vùng trên sdc.

    * Tiếp theo chạy lệnh sau để kiểm tra xem các đĩa hiện có tham gia RAID nào không:
    ```bash
    fdisk -l | grep sd
    mdadm -E /dev/sd[b-c]
    mdadm -E /dev/sd[b-c]1
    ```
    ![](https://user-images.githubusercontent.com/52046920/178436827-c7fdd1b6-9290-4851-9c69-27ff7eea4b2b.png)
    ![](https://user-images.githubusercontent.com/52046920/178436830-d995cd56-9b07-4b35-8616-9443806905ed.png)

* Bước 4: Tạo RAID1. 
    * Tiếp theo tạo thiết bị RAID1 có tên /dev/md0 bằng cách sử dụng lệnh và xác thực RAID1 đã được tạo.
        ```bash
        mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sd[b-c]1
        ```
    * Trong quá trình tạo hệ thống yêu cầu chúng ta xác nhận tạo RADI thì bấm phím y để xác nhận.
    ![Tạo thiết bị Raid](https://user-images.githubusercontent.com/52046920/178436835-695683c3-8646-4d27-aae4-147848ce80ac.png)
    * Qua kết quả trên thấy RAID1 đã được tạo với hai phân vùng sdb1 và sdc1. Kiểm tra bằng lệnh:
    ```bash
    mdadm --detail /dev/md0
    ```
    ![Kiểm tra Raid](https://user-images.githubusercontent.com/52046920/178436838-868b7182-a456-47fa-99a0-9d430b9226e2.png)

* Bước 5: Tạo file system (ext4) cho thiết bị RAID /dev/md0

    * Tiếp theo tạo thư mục gắn kết raid1 để gắn thiết bị /dev/md0 thực hiện như bên dưới.
        
        ```bash
            mkdir raid1
            mount /dev/md0 raid1/
        ```
    ![Mount](https://user-images.githubusercontent.com/52046920/178436844-95b8c057-8c8d-4315-9909-76ecf938e1ae.png)
    
    * Kiểm tra bằng lệnh
            ```bash
                df -h
            ```
    ![Kiểm tra mount](https://user-images.githubusercontent.com/52046920/178436848-1ce8c8a0-60d0-4d91-a227-64d53c31244c.png)
        
    * Để tự động gắn kết /dev/md0 khi khởi động lại hệ thống chúng ta cần tạo một mục trong tệp /etc/fstab. Bạn có thể sử dụng trình soạn thảo vi để nhập dòng bên dưới vào:
            ```bash
            vi /etc/fstab
            ```
    * Lưu lại và chạy lệnh sau để kiểm tra xem có bất kỳ lỗi nào trong mục /etc/fstab không.

    ![Thêm thông tin](https://user-images.githubusercontent.com/52046920/178436850-be0b623b-269e-41ee-8cdf-6b061c3cf306.png)
        
    * Nếu có lỗi, không reboot server để tránh tình trạng server không thể khởi động. Kiểm tra cấu hình trong file /etc/fstab và chạy lại lệnh cho tới khi không có thông báo lỗi. Kiểm tra bằng câu lệnh.
        ```bash
            mount a
            mount -av
        ```
    ![Kiểm tra](https://user-images.githubusercontent.com/52046920/178436851-c62c6af1-f6fb-45e8-adaf-d18ee1be3b39.png)

## ***2. Thiết lập RAID 5 trên Windows server 2016***
* Chuẩn bị 3 ổ cứng.
* Mở thiết lập Disk Management.
![Mở Disk Managerment](https://user-images.githubusercontent.com/52046920/178456061-a5f577dc-f8d6-4d2b-9159-e7ec23c19e18.png)
![3 ổ cứng đã chuẩn bị](https://user-images.githubusercontent.com/52046920/178456050-d1e07dff-df54-44a2-92b3-3d06895b42ee.png)
* Chọn 1 ổ trống click chuột phải sau đó chọn "New RAID-5 Volume Wizard".
![Chọn New RAID-5 Volume](https://user-images.githubusercontent.com/52046920/178456064-6e15d0c4-1777-46ba-9c88-be395bbe1e7c.png)
* 1 cửa sổ sẽ hiện ra sau đó nhấp vào next.
![](https://user-images.githubusercontent.com/52046920/178456068-6fdc4c62-1f9c-4e86-905e-288bb3f9c13e.png)
* Sau đó chọn những ổ còn lại đã chuẩn bị cho Raid rồi bấm vào add
![](https://user-images.githubusercontent.com/52046920/178456072-26a3ac8b-2f17-49f6-8410-6c953e9052f1.png)
* Sau đó gán ký tự ổ đĩa cho ổ đĩa RAID 5 và định dạng ổ đĩa và nhấp vào "Next" và "Next" tiếp tục ở bước tiếp theo.
![](https://user-images.githubusercontent.com/52046920/178456075-de9380b8-999c-4d09-bf82-20756007e03d.png)
![](https://user-images.githubusercontent.com/52046920/178456078-e1a527c7-8ad6-4cf6-a641-916476dfd2cf.png)
* Sau đó bấm Finish và chờ đợi thiết lập Raid trên 3 ổ đó
![](https://user-images.githubusercontent.com/52046920/178456080-0a902ea9-20a0-42f6-8550-e74db866e1e4.png)

* 3 ổ đang tiến hành thiết lập RAID
![](https://user-images.githubusercontent.com/52046920/178456083-4f20e424-0721-4345-97f7-ff4efa44d810.png)
* Sau khi thiết lập xong ta có kết quả
![](https://user-images.githubusercontent.com/52046920/178456084-b81385b3-0deb-49ee-beac-affcbb142895.png)
* Ổ E là RAID 5 tạo ra từ 3 ổ mỗi ổ 10GB của dung lượng cuối là 20GB
![](https://user-images.githubusercontent.com/52046920/178456087-2efe4e48-65b3-4140-b242-3a371c09fe6a.png)
