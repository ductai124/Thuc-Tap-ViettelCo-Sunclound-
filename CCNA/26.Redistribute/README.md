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

# TÌM HIỂU REDISTRIBUTE 

## Người viết : Phạm Đức Tài
## SDT : 0837686717
## Mail : phamductai123456@gmail.com

***
# Mục lục
# [I. Redistribute là gì]()

# [II. Quảng bá các route vào EIGRP]()
# [III. Quảng bá các route vào OSPF]()
***
# ***I.	Redistribute là gì***
* Là 1 kỹ thuật quảng bá các route thuộc miền định tuyến của giao thức này sang miền định tuyến của giao thức khác cùng AS và khác AS đều sử dụng được kỹ thuật này(các Process khác nhau cũng phải sử dụng kỹ thuật này).
* Khi quảng bá các route từ miền định tuyến này qua miền định tuyến khác thì ta phải tinh chỉnh lại metric sao cho phù hợp do các giao thức đểu có cách thức tính metric khác nhau. Ví dụ như trong 1 mạng EIGRP và OSPF cùng lúc được sử dụng, ta quảng bá 

# ***II.	Quảng bá các route vào EIGRP***
* Các route có thể được Redistribute vào EIGRP này có:
    * Static route
    * Route học từ RIP
    * Route học từ OSPF 
    * Các mạng kết nối trực tiếp với thiết bị
    ...

![](https://user-images.githubusercontent.com/52046920/190635024-acc89c55-a2c2-4bae-b5c1-a29e501e5b9f.png)


* Cấu hình như sau
```cisco
R1(config)#router eigrp 200
R1(config-router)#redistribute static
R1(config-router)#redistribute ospf 1
R1(config-router)#redistribute connected

/// điều chỉnh lại metric phải khai báo default-metric thì các mạng trên mới được redistribute vào eigrp 100
R1(config-router)#default-metric 100000 100 255 125 1500
```
* Có thể khai báo độc lập metric cho tùy từng giao thức
```cisco
R1(config)#router eigrp 200
R1(config-router)#redistribute static metric 100000 100 255 125 1500
R1(config-router)#redistribute ospf 1 metric 100000 100 255 125 1500
R1(config-router)#redistribute connected metric 100000 20 255 125 1500

R1(config-router)#default-metric 100000 100 255 125 1500
```
* Nếu cả 2 miên đều sử dụng eigrp thì không cần khải báo metric hay default-metric

![](https://user-images.githubusercontent.com/52046920/190635028-59fca7b8-86de-4b1a-af2c-13683df9f359.png)

# ***III.	Quảng bá các route vào OSPF***
* Cấu hình như sau
```cisco
R1(config)#router ospf 10
R1(config-router)#redistribute static subnets
R1(config-router)#redistribute eigrp 100 subnets
R1(config-router)#redistribute connected subnets


```
* Nếu không khai báo metric thì metric sẽ được thiết lập mặc định là 20. Giao thức này các network redistribute vào phải là major network còn nuế không nó sẽ không được redistribute vào 
* Thiết lập metric như sau
```cisco
R1(config)#router ospf 10
R1(config-router)#redistribute static subnets metric 30
R1(config-router)#redistribute eigrp 100 subnets metric 40
R1(config-router)#redistribute connected subnets metric 25

```
* Metric type 1 cộng dồn toàn bộ route cả trong lẫn ngoài
```cisco
R1(config)#router ospf 1
R1(config-router)#redistribute ospf 100 subnets metric 20 mtric-type 1
```
* Metric type 2 chỉ tính route ngoại vùng
```cisco
R1(config)#router ospf 1
R1(config-router)#redistribute ospf 100 subnets metric 20 mtric-type 2
```

![](https://user-images.githubusercontent.com/52046920/190635018-b9c15479-e6cf-40ab-83c5-e8ea45c2cc69.png)