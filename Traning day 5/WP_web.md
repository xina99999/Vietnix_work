# Reverse nginx cho apache trên ubuntu 22.04 
# Cài đặt cái phần mêm cần thiết: Nginx, apache, mysql , phpadmin , php version 7.7


## Cấu hình file 




---

# ✅ Tổng quan mô hình:

* **NGINX** lắng nghe cổng 80/443 → làm **reverse proxy**
* **Apache** lắng nghe ở cổng nội bộ (ví dụ: 8080)
* **WordPress** chạy trên Apache
* **phpMyAdmin** phục vụ bởi Apache, reverse qua NGINX
* **SSL**: ZeroSSL cài vào NGINX

---

## 🔁 1. Cài đặt & cấu hình các thành phần

### 1.1. Cài đặt gói cần thiết:

## Nginx install
![Screenshot from 2025-06-14 11-40-38](https://github.com/user-attachments/assets/cb19227a-253c-41d2-b46e-8b1ca5f7b1c7)

## Apache install
![Screenshot from 2025-06-14 11-41-16](https://github.com/user-attachments/assets/40b310b0-ce14-4c95-9e2a-633aaad52fd4)

## php install
![Screenshot from 2025-06-14 11-41-50](https://github.com/user-attachments/assets/c9d96f86-3b17-43e1-9a5e-3d59076d5bd3)

## PHPadmin install 

![Screenshot from 2025-06-14 11-43-32](https://github.com/user-attachments/assets/42e3aab1-5a9b-4cc7-8a57-0ce5d9053a43)

## 📁 2. Triển khai mã nguồn WordPress

### 2.1. Giải nén source code:

```bash
unzip ~/source_code.zip -d /var/www/wp.nhan.vietnix.tech
chown -R www-data:www-data /var/www/wp.nhan.vietnix.tech
chmod -R 755 /var/www/wp.nhan.vietnix.tech
```

---

## 🧠 3. Cấu hình Apache (lắng nghe cổng 8080)

### 3.1. Tạo virtual host cho Apache:

**File:** `/etc/apache2/sites-available/wp.nhan.vietnix.tech.conf`

```apache
<VirtualHost 127.0.0.1:8080>
    ServerName wp.nhan.vietnix.tech
    DocumentRoot /var/www/wp.nhan.vietnix.tech

    <Directory /var/www/wp.nhan.vietnix.tech>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/wp_error.log
    CustomLog ${APACHE_LOG_DIR}/wp_access.log combined
</VirtualHost>
```

### 3.2. Kích hoạt:

```bash
sudo a2ensite wp.nhan.vietnix.tech.conf
sudo systemctl reload apache2
```

---

## 🌐 4. Cấu hình NGINX reverse proxy

**File:** `/etc/nginx/sites-available/wp.nhan.vietnix.tech.conf`

```nginx
server {
    listen 80;
    server_name wp.nhan.vietnix.tech;

    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    location /phpmyadmin {
        proxy_pass http://127.0.0.1:8080/phpmyadmin;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

### Kích hoạt cấu hình:

```bash
ln -s /etc/nginx/sites-available/wp.nhan.vietnix.tech.conf /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
```

---


## 🛠️ 6. Khởi tạo cơ sở dữ liệu WordPress

### 6.1. Import file SQL:

```bash
mysql -u root -p wp_nhan < ~/sql_wp_nhan_viet.sql
```

---

## ⚙️ 7. Cấu hình wp-config.php

Chỉnh các dòng trong `/var/www/wp.nhan.vietnix.tech/wp-config.php`:

```php
define('DB_NAME', 'wp_nhan');
define('DB_USER', 'root');
define('DB_PASSWORD', 'your_mysql_root_password');
define('DB_HOST', 'localhost');
```

---

## 🧪 8. Kiểm tra hoạt động

* Truy cập WordPress: `http://wp.nhan.vietnix.tech`
*
---

![Screenshot from 2025-06-14 11-49-39](https://github.com/user-attachments/assets/878f556c-b01b-44cd-977e-91c3657a18c7)

