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
# []()

## &ensp; []()

## &ensp; []()

## &ensp; []()

# []()
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
## ***1.	RAID 1***
* Đây là dạng Raid cơ bản có khả năng đảm bảo an toàn dữ liệu. Yêu cầu ít nhất 2 ổ cứng.RAID cung cấp phương pháp dự phòng dữ liệu đơn giản bằng kĩ thuật “mirroring” (nhân bản dữ liệu). Dữ liệu khi đọc ghi sẽ ghi ở 2 ổ giống hệt nhau. Trong trường hợp 1 ổ gặp sự cố dữ liệu cũng đã được ghi ở ổ còn lại đảm bảo sự an toàn của dữ liệu.
* Tuy nhiên khi sử dụng Raid 1 ta sẽ phải bỏ 1 ổ để chỉ sử dụng làm Mirroring nên dung lượng thực của hệ thống chỉ có dung lượng của 1 ổ
* Ưu điểm: An toàn về dữ liệu, khả năng hoạt động liên tục cao
* Nhược điểm: Hiệu suất không cao, chi phí cao do mất 1 nữa tài nguyên ổ cứng để giúp dữ liệu được an toàn
* Đối tượng sử dụng: Các dịch vụ lưu trữ, các Website nhỏ đến vừa không yêu cầu quá cao về tốc độ đọc ghi ổ cứng.
![Raid 1](https://user-images.githubusercontent.com/52046920/178389120-e1991635-8875-4b1e-9687-24416ba3d65c.png)
## ***1.	RAID 1+0***
* Là kết hợp của Raid 1 và Raid 0. Raid 1+0 Sở hữu tốc độ đọc ghi của Raid 0 vầ sự an toàn của Raid 1. Các kĩ thuật “mirroring” và “striping” kết hợp với nhau tạo ra hiệu quả dự phòng. Để có thể vận hành Raid 1+0 cần tối thiểu 4 ổ cứng. Dữ liệu sẽ được ghi lên đồng thời cả 4 ổ trong 
chia làm 2 cặp 1 ổ ghi và 1 ổ sao lưu. Dữ liệu sẽ được ghi như với Raid 0 đối với 2 ổ ghi và sẽ được sao lưu ra 2 ổ sao lưu giống với Raid 1
* Ưu điểm: An toàn về dữ liệu, khả năng hoạt động liên tục cao, tốc độ đọc ghi nhanh
* Nhược điểm: Chi phí cao do mất 1 nữa tài nguyên ổ cứng để giúp dữ liệu được an toàn và cần nhiều ổ để có thể vận hành số ổ bắt buộc phải là số chẵn. Vẫn có khả năng mất dữ liệu nếu cặp ổ ghi và ổ sao lưu cùng chết
* Đối tượng sử dụng: Raid 1+0 thích hợp với tất cả các đối tượng sử dụng (từ những yêu cầu về hiệu suất đến việc đảm bảo an toàn dữ liệu) Nếu đáp ứng được yêu cầu về chi phí.
![Raid 1+0](https://user-images.githubusercontent.com/52046920/178389160-1a640cdf-4150-4fd2-b6ae-5d24a34adc6d.png)
## ***RAID 5***
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

## ***RAID 6***
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