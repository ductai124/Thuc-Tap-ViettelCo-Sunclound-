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

# TÌM HIỂU VỀ CÁCH GỬI TIN NHẮN TỪ CENTOS VỀ TELEGRAM VÀ TẠO BOT TELEGRAM
## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I.	Tạo bot trên telegram](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/LINUX/README.md#it%E1%BA%A1o-bot-tr%C3%AAn-telegram-1)

# [II.	Gửi tin nhắn từ Centos đến telegram](https://github.com/ductai124/Thuc-Tap-ViettelCo-Sunclound-/blob/main/LINUX/README.md#iig%E1%BB%ADi-tin-nh%E1%BA%AFn-t%E1%BB%AB-centos-%C4%91%E1%BA%BFn-telegram-1)
***
# ***I.	Tạo bot trên telegram***
* Đầu tiên hãy đăng nhập telegram sau đó chọn setting và thiết lập username của mình.
* Ở thanh tìm kiếm search từ khóa: BotFather . và ta sẽ chọn bot có tích xanh
![](https://user-images.githubusercontent.com/52046920/185291540-2a144512-f1bb-4a85-b111-8f2d95f0f40f.png)


* Bắt đầu chat với từ khóa /newbot là lệnh tạo bot sao đó bot sẽ bắt ta khai báo tên Bot, Username cho bot với dạng: UsernameBot_bot. Ở bài hướng dẫn sẽ tạo 1 bot có:
    * Tên bot:CheckMK
    * Username bot:PDTai3110_bot
* Sau khi hoàn thành nó sẽ cung cấp cho chúng ta 1 mã token, hãy lưu lại và không chia sẽ cho ai khác

![](https://user-images.githubusercontent.com/52046920/185291541-eefbdd5a-4ea5-45e7-ae4f-ca78acf22d09.png)

* Kiểm tra Token bằng cách nhập tên miên sau vào trong trình duyệt sẽ có kết quả tương tự như sau
```http
https://api.telegram.org/bot<TOKEN>/getMe
```
![](https://user-images.githubusercontent.com/52046920/185292369-d120958a-91ca-4b12-9b22-556239584ad2.png)

* Sau đó nhập từ khóa /mybots chọn bot mình vừa tạo

![](https://user-images.githubusercontent.com/52046920/185292711-bb897527-77b1-468b-9c74-e16be83db1af.png)
* Click vào Username của bot để chuyển đến phần chat

![](https://user-images.githubusercontent.com/52046920/185291528-d36dc383-24f5-4c9a-9d06-9173da9d4b2e.png)

* Khởi động bot với cú pháp /start và sau đó hay chat với bot vài từ bất kỳ rồi tiến hành kiểm tra id của bot bằng cách gõ tên miên sau vào trình duyệt

```http
https://api.telegram.org/bot<TOKEN>/getUpdates

```
* Ở đây ta sẽ thấy được ID của bot từ các tin nhắn mà ta vừa gửi cho bot lúc trước hay lưu ID lại

![](https://user-images.githubusercontent.com/52046920/185291536-bd55a3eb-e15d-473b-95d0-3f1a40fd1756.png)


# ***II.	Gửi tin nhắn từ Centos đến telegram***
* Trước tiên cài đặt JQ
```shell
yum install epel-release -y
yum install jq -y
```

* Gửi tin nhắn bằng phương thức POST với Curl
```shell
#Thay thế <ID_BOT> Bằng ID bot vừa tạo ví dụ chat_id="12312314", tương tự <TOKEN> sẽ thay thế bằng TOKEN vừa tạo

curl -s -X POST "https://api.telegram.org/bot<TOKEN>/sendMessage" -d chat_id="<ID_BOT>" -d text="HELLO BOT"


```
* Quay lại telegram kiểm tra tin nhắn cả BOT

![](https://user-images.githubusercontent.com/52046920/185294119-c70c9c66-352d-40f1-bb80-a61a333b1f9e.png)
