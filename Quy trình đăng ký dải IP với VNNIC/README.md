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

# QUY TRÌNH ĐĂNG KÝ 1 DẢI MẠNG VỚI VNNIC
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. VNNIC là ai?](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#ivnnic-l%C3%A0-ai)
# [II. Quy trình đăng ký cấp, phân bổ IP](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#iiquy-tr%C3%ACnh-%C4%91%C4%83ng-k%C3%BD-c%E1%BA%A5p-ph%C3%A2n-b%E1%BB%95-ip)
## &ensp; [1. Nguyên tắc thực hiện](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#1-nguy%C3%AAn-t%E1%BA%AFc-th%E1%BB%B1c-hi%E1%BB%87n)

## &ensp; [2. Nguyên tắc thực hiện](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#2-nguy%C3%AAn-t%E1%BA%AFc-th%E1%BB%B1c-hi%E1%BB%87n)

## &ensp; [3. Phương thức nộp hồ sơ](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#3-ph%C6%B0%C6%A1ng-th%E1%BB%A9c-n%E1%BB%99p-h%E1%BB%93-s%C6%A1)
## &ensp; [4. Quy trình thực hiện](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/Quy%20tr%C3%ACnh%20%C4%91%C4%83ng%20k%C3%BD%20d%E1%BA%A3i%20IP%20v%E1%BB%9Bi%20VNNIC/README.md#4-quy-tr%C3%ACnh-th%E1%BB%B1c-hi%E1%BB%87n)

***
# ***I.	VNNIC là ai?***
* VNNIC là viết tắt của Vietnam Internet Network Information Center có nghĩa là trung tâm Internet Việt Nam là đơn vị trực thuộc Bộ Thông tin và Truyền thông. VNNIC chịu trách nhiệm thiết lập, quản lý, kha thác hạ tầng trọng yếu của mạng Internet Việt Nam qua Hệ thống máy chủ tên miền DNS(Domain Name System) quốc gia và Trạm trung chuyển Internet quốc gia (VNIX).

![](https://user-images.githubusercontent.com/52046920/191929110-f0fbaed8-f739-419d-bec3-10cf527bff6f.png)

<!--# ***II.	Quy trình đăng ký cấp, phân bổ số hiệu mạng(ASN)***
* ASN - Autonomous System Number hay còn gọi là số hiệu mạng là số được sử dụng để định danh 1 mạng máy tính tham gia vào hoạt động định tuyến chung trên Internet-->

# ***II.	Quy trình đăng ký cấp, phân bổ IP***
## ***1. Nguyên tắc thực hiện***
*  Cơ quan, tổ chức, doanh nghiệp có nhu cầu thiết lập mạng kết nối với Internet muốn xin cấp IP thì chuẩn bị hồ sơ cấp, phân bổ địa chỉ IP theo quy định và nộp đến trung VNNIC. Hiện tại đang khuyến khích đăng ký IPv6
* Địa chỉ IP được cấp, phân bổ cho nhu cầu sử dụng thực tế và có giá trị sử dụng trên toàn bộ lãnh thổ Việt Nam. Những thành phần xin cấp IP tham gia hoạt động Internet phải đảm bảo:
    * Thực hiện routing các vùng địa chỉ IP ở Việt Nam theo hướng dẫn của VNNIC
    * Không được Routing những IP nằm ngoài danh mục quản lý của VNNIC trừ kết nối với cổng quốc tế
    * Phối hợp với VNNIC về kỹ thuật và chính sách định tuyến để đảm bảo hệ thống DNS quốc gia và VNIX, Internet Việt Nam hoạt động an toàn và hiệu quả
    * Có kế hoạch đưa IPv6 vào hoạt động phù hợp kết hoạch ahnhf động quốc gia về IPv6
* Quá hạn 6 tháng tính từ ngày cấp mà địa chỉ không được đưa vào sử dụng sẽ bị thu hồi nếu không giải trình được mục đích sử dụng chính đáng
* Các vùng IP sẽ bị thu hồi trong các trường hợp không xác định được chủ thể do mạo danh đăng ký hoặc thông tin không chính xác.
* Chính sách cấp phát IPv4 đang cạn kiệt: mỗi tổ chucwsc được quyền đăng ký cấp tối đa 1 dải /23 từ dải 103/8 của APNIC. Vùng địa chỉ độc lập tối thiều mà tổ chức có nhu cầu đăng ký tới VNNIC là /24 (256 địa chỉ IP).
* Đối với IPv6, thành viên được xét cấp miễn phí IPv6 tương đương với địa chỉ IPv4 mà thành viên được cấp. Trường hợp khối IPv6 vượt quá khối IPv4 hoặc khi thành viên chưa có địa chỉ IPv4, mức phí thành viên cần đóng sẽ phụ thuộc theo phí địa chỉ IPv6. [Tham khảo thông tin sử dụng](https://www.vnnic.vn/diachiip/hotro/thamkhao/bi%E1%BB%83u-m%E1%BB%A9c-ph%C3%AD-l%E1%BB%87-ph%C3%AD)
* Lưu ý: Khi có vùng địa chỉ IPv4 còn trống, VNNIC thực hiện niêm yết tại địa chỉ [www.diachiip.vn](https://www.vnnic.vn/diachiip/) để các tổ chức, doanh nghiệp có nhu cầu nộp hồ sơ về VNNIC theo quy định. Các hồ sơ không có giá trị bảo lưu trong các đợt mở cấp phát IPv4 tiếp theo.
## ***2. Nguyên tắc thực hiện***
* Thành phần hồ sơ đăng ký địa chỉ IP chuẩn bị:
    * Bản khai đăng ký địa chỉ IP ([Bản khai](https://vnnic.vn/sites/default/files/mau-2022-ban_khai_dang_ky_cap_ip_hoac_ip_va_asn.docx))
    * Bản sao có chứng thực hoặc bản sao kèm bản chính (để đối chiếu) Quyết định thành lập hoặc các loại Giấy chứng nhận hợp lệ khác được cấp trước ngày có hiệu lực của Luật Doanh nghiệp năm 2014 hoặc Mã số doanh nghiệp.
## ***3. Phương thức nộp hồ sơ***
* Nộp trực tuyến tại địa chỉ: [https://dichvucong.mic.gov.vn/](https://dichvucong.mic.gov.vn/)

    * Tổ chức, thành viên đăng ký tài khoản.

    * Nộp hồ sơ trực tuyến (khai thông tin hồ sơ và ký số điển tử của tổ chức, doanh nghiệp).

* Trường hợp không thể nộp trực tuyến thì nộp trực tiếp hoặc qua bưu chính tới địa chỉ: Trung tâm Internet Việt Nam, tầng 24, tòa nhà VNTA, Dương Đình Nghệ, Yên Hòa, Cầu Giấy, Hà Nội.

## ***4. Quy trình thực hiện***
* Trường hợp đăng ký theo chính sách chung của khu vực Châu Á - Thái Bình Dương.

![](https://user-images.githubusercontent.com/52046920/191930486-4c106498-6b11-4a6a-93ad-b2bdd64255e0.png)
* Chi tiết:

|STT|Thủ tục|Nội dung công việc|Người thực hiện|Thời lượng|
|--|--|---------|--|--|
|1|Nộp hồ sơ|Tổ chức nộp hồ sơ đến VNNIC|Tổ chức/Thành viên|Ngay khi nhận|
|2|Thẩm định hồ sơ|VNNIC thẩm định hồ sơ, trong trường hợp cần thiết, có thể yêu cầu tổ chức nộp hồ sơ bổ sung hồ sơ hoặc cung cấp thêm thông tin trong 3-5 ngày kể từ khi nhận. Nếu kết quả thẩm định phù hợp chuyển qua bước tiếp theo của quy trình. Nếu yêu cầu đăng ký địa chỉ IP không phát sinh phí, quy trình chuyển sang bước 6.|VNNIC|3-5 ngày làm việc|
|3|Gửi thông báo phí lệ phí cho tổ chức xin tài nguyên|VNNIC ra thông báo thu phí|VNNIC|2 ngày làm việc|
|4|Nộp lệ phí|Thành viên đóng phí theo thông báo của VNNIC(chuyển khoản hoặc tiền mặt)|Tổ chức/Thành viên|theo giấy báo|
|5|Gửi yêu cầu lên APNIC|VNNIC gửi yêu cầu cấp địa chỉ IP, lên APNIC trong vòng 05 ngày làm việc kể từ khi tổ chức xin địa chỉ hoàn tất việc nộp phí|1-2 ngày làm việc|
|6|Ra quyết định cấp phát|VNNIC ra Quyết định cấp phát địa chỉ IP cho tổ chức xin địa chỉ thông qua quyết định hành chính. Tổ chức được cấp địa chỉ chính thức trở thành thành viên địa chỉ của VNNIC.|VNNIC|2-3 ngày làm việc|
|7|Thông báo kết quả cho thành viên|Thông báo kết quả cho thành viên|VNNIC|T10 ngày làm việc sau khi nhận được đầy đủ hồ sơ hợp lệ và phí, lệ phí đăng ký IP|
