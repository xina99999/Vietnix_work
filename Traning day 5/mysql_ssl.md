# Đăng nhập mysql từ xa


### Bước 1: Mở file cấu hình MySQL

```bash
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

Tìm dòng:

```ini
bind-address = 127.0.0.1
```

➡️ Thay **`127.0.0.1`** thành:

```ini
bind-address = 0.0.0.0
```

![Screenshot from 2025-06-16 09-43-38](https://github.com/user-attachments/assets/9ecf311f-6095-47b7-811f-734dea06019d)


---

### Bước 2: Tạo tài khoản để đăng nhập

Vào MySQL:

```bash
mysql -u root -p
```

Sau đó chạy:

```sql
SELECT user, host FROM mysql.user WHERE user = 'admin';
```

Nếu chưa thấy dòng `admin | %`, thì bạn tạo lại:

```sql
CREATE USER 'admin'@'%' IDENTIFIED BY 'your_secure_password';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

---

### Bước 3. **Kiểm tra firewall VPS (nếu có)**

Nếu bạn đang dùng UFW (Ubuntu Firewall), mở cổng 3306:

```bash
sudo ufw allow 3306
```

Kiểm tra lại:

```bash
sudo ufw status
```

---

### Bước 4: Khởi động lại MySQL

```bash
sudo systemctl restart mysql
```

---

### Bước 5: Kiểm tra lại

```bash
ss -tuln | grep 3306
```


```
tcp   LISTEN 0      151        0.0.0.0:3306       0.0.0.0:*
```

---

### Bước 6: Test lại kết nối từ máy ngoài

```bash
mysql -u admin -p -h 14.225.254.103
```

---

![Screenshot from 2025-06-16 09-43-38](https://github.com/user-attachments/assets/64313b7a-8dc9-4458-88d2-f524fdbc5e59)


```



