
## I. Cài đặt CyberPanel

### Bước 1: Cập nhật hệ thống

```bash
sudo yum update -y    # với CentOS / AlmaLinux

```

### Bước 2: Cài đặt CyberPanel

```bash
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
```

### Bước 3: Chọn cấu hình khi script hỏi:

* Cài CyberPanel với OpenLiteSpeed (chọn \[1])
* Cài đặt Full service (chọn \[1])
* Thiết lập mật khẩu admin
* Chọn Yes cho CSF Firewall nếu cần
* Cuối cùng: Reboot hệ thống khi cài xong

---

## II. Truy cập CyberPanel

Mở trình duyệt:

```
https://14.225.254.103:8090
```



---

## III. Cấu hình và Triển khai Website

### ✅ Tạo Website trên CyberPanel

1. Vào `Websites → Create Website`
2. Điền thông tin:

   * Select Package: `Default`
   * Select Owner: `admin`
   * Domain Name: ví dụ `wp.example.com` hoặc `laravel.example.com`
   * Email, PHP Version: chọn PHP 7.4 hoặc 8.0 tùy website
3. Bấm `Create Website`

---
![Screenshot from 2025-06-18 09-48-29](https://github.com/user-attachments/assets/8a0abfa6-3d16-4a1d-a81f-91fbf74dbec4)
  

## IV. Cài đặt WordPress

### 1. Vào `Websites → List Websites → Manage`

### 2. Vào thư mục pbulic_html đưa đưa source vào sau đó giải nén

![Screenshot from 2025-06-18 09-53-32](https://github.com/user-attachments/assets/6a63195d-5e17-4e01-bb0f-2293f2075c82)


---
### 3. Cài database 
  - Chọn create database tạo database name, user , password
  - Vào phpmyadmin , import data vào database vừa tạo
![Screenshot from 2025-06-18 09-51-13](https://github.com/user-attachments/assets/6550323d-9c38-4fcb-be9a-cadcabe21668)

### 4 Kiểm tra cấu hình trong config.php các cấu hình database
### 5 Kết quả đạt đươc
![Screenshot from 2025-06-18 09-49-33](https://github.com/user-attachments/assets/b4c67987-24c9-458b-8263-5f3c8d55641f)

## V. Cài đặt Laravel

### 1. Vào `Websites → List Websites → Manage`

### 2. Vào thư mục pbulic_html đưa đưa source vào sau đó giải nén

![Screenshot from 2025-06-18 09-54-37](https://github.com/user-attachments/assets/1d4c7bfd-e482-4f24-bac2-2a0b7acebd9c)


---
### 3. Cài database 
  - Chọn create database tạo database name, user , password
  - Vào phpmyadmin , import data vào database vừa tạo
![Screenshot from 2025-06-18 09-54-55](https://github.com/user-attachments/assets/b8204c5d-3e35-4eed-84a7-3a91cf4bf00a)


### 4 Kiểm tra cấu hình trong .env các cấu hình database
### 5 Vào website -> laravel.nhan.vietnix.tech -> manage -> vhost kiểm tra [ docRoot                   $VH_ROOT/public_html/public] nếu không trỏ vào thư mục public thì laravel không chạy được
![Screenshot from 2025-06-18 09-57-27](https://github.com/user-attachments/assets/42b1e914-9c3b-46df-a86f-2db0b511b70e)

### 6 Kết quả đạt đươc
![Screenshot from 2025-06-18 09-57-45](https://github.com/user-attachments/assets/38768fa5-430a-499d-8d5b-64aed4f0524a)

#
