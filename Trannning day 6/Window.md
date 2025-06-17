
# 🛡️ PHẦN 1: CẤU HÌNH WINDOWS FIREWALL BẰNG GIAO DIỆN (UI)

## ✅ **1. Allow port / IP**

**Ví dụ: Cho phép port 80 hoặc IP cụ thể truy cập**

### Bước 1: Mở Windows Defender Firewall with Advanced Security

* Bấm `Start`, gõ: `Windows Defender Firewall with Advanced Security` và mở nó.

### Bước 2: Chọn mục **Inbound Rules** → Chọn **New Rule…**

### Bước 3: Chọn loại rule

* **Port** → Next
* Chọn: **TCP** → nhập port ví dụ `80` → Next
* Chọn: **Allow the connection** → Next
* Tick cả 3 (Domain, Private, Public) → Next
* Đặt tên: `Allow Port 80` → Finish

### Kết quả thực hiện 
![Screenshot from 2025-06-17 08-54-43](https://github.com/user-attachments/assets/03044373-ee2f-482f-a6ff-07bdb548161d)


### 🔁 Tương tự để Allow theo IP:

* Chọn loại **Custom**
* Đến bước **Scope**, ở phần **Remote IP address**, chọn: **These IP addresses**
  → Add IP cần cho phép (VD: `192.168.0.133`)

## Kết quả thực hiện được
![Screenshot from 2025-06-17 08-59-33](https://github.com/user-attachments/assets/07cbe167-1be3-45d6-bd41-da2bc7340589)


---

## 🚫 **2. Block port / IP**

Thực hiện tương tự như trên nhưng:

* Ở bước **Action**: Chọn **Block the connection**
* Ở bước **Scope**: Nếu block IP → nhập IP cần chặn
* Ở bước **Protocol and Ports**: Nếu block port → nhập port cần chặn

### Kết qquả thực hiện được 
- Add block port 443
  
![Screenshot from 2025-06-17 09-01-56](https://github.com/user-attachments/assets/b66a4ad5-f2f0-484e-bf1b-53a1c3dfae04)
![Screenshot from 2025-06-17 09-03-15](https://github.com/user-attachments/assets/11c7fe82-2aae-44b5-b0b0-bce2473ecfd3)

- Add block ip 192.168.0.100

![Screenshot from 2025-06-17 09-04-43](https://github.com/user-attachments/assets/6177f1d2-6240-48ad-98e2-4be08a3fa594)


---

## 🔐 **3. Giới hạn IP truy cập port**

Chỉ cho phép IP cụ thể truy cập port (ví dụ port 3389 - Remote Desktop):

1. Tạo **rule Allow** port 3389 cho IP cụ thể như trên
2. Sau đó tạo thêm **rule Block** tất cả IP khác cho cùng port

## Kết quả thực hiện 
![Screenshot from 2025-06-17 09-16-08](https://github.com/user-attachments/assets/d39b9f0f-fde0-4fb6-be95-a5b0966b5352)


---

# 🌐 PHẦN 2: CÀI ĐẶT IIS + WORDPRESS + MYSQL + SSL BẰNG GIAO DIỆN

## ✅ **1. Cài đặt IIS**

### Bước 1:

* Mở `Server Manager` → `Add roles and features`
* Chọn:

  * Role-based
  * Web Server (IIS)
  * Tick: Web Server, Common HTTP Features
  * Install
  * Application 
![Screenshot from 2025-06-17 09-29-35](https://github.com/user-attachments/assets/eb89e4e0-03a5-4feb-be29-7885f6685db4)


## ✅ **2. Cài MySQL**

* Tải MySQL Installer từ: [https://dev.mysql.com/downloads/installer/](https://dev.mysql.com/downloads/installer/)
* Chạy file, chọn **Developer Default**
* Đặt password cho `root`, cấu hình port (mặc định là 3306)

![Screenshot from 2025-06-17 09-58-09](https://github.com/user-attachments/assets/ed0b3ba6-ddbd-4f84-b6c4-74744c1fe5b5)

## ✅ **3. Cài PHP**

* Tải PHP: [https://windows.php.net/download/](https://windows.php.net/download/)
* Giải nén vào `C:\PHP`
* Vào **IIS Manager**:

  * Chọn server > **Handler Mappings** → Add Module Mapping:

    * Request path: `*.php`
    * Module: `FastCgiModule`
    * Executable: `C:\PHP\php-cgi.exe`
    * Name: `PHP_via_FastCGI`
### Kết quả đạt được 


![Screenshot from 2025-06-17 09-39-57](https://github.com/user-attachments/assets/d97e728d-20e1-4762-b8b5-276948a327e6)

## ✅ **4. Cài WordPress**

* Tải từ [https://wordpress.org/latest.zip](https://wordpress.org/latest.zip)
![Screenshot from 2025-06-17 10-23-38](https://github.com/user-attachments/assets/b5564178-823e-4be4-b3ba-6a1481728465)


* Giải nén vào thư mục `C:\inetpub\wwwroot\wp`
* Chỉnh sửa file php.init đảm bảo cài đặt các gói sau
  `
  extension=mysqli
extension=pdo_mysql
extension=mbstring
extension=openssl
extension=curl
`
* Trong **IIS Manager**:

  * Click phải `Sites` → Add Website:

    * Site name: wp.nhan.vietnix.tech
    * Path: C:\inetpub\wwwroot\wp
    * Host name: wp.nhan.vietnix.tech
   
      ![Screenshot from 2025-06-17 10-21-58](https://github.com/user-attachments/assets/2920ff3a-7dbd-4dd1-9b84-b42e8c89a5b1)

* Sau đó truy cập trình duyệt: `'http://wp.nhan.vietnix.tech/'
![Screenshot from 2025-06-17 10-48-32](https://github.com/user-attachments/assets/51f9da9f-1d1e-4b26-8a7e-4e9a3b6adbf2)

## ✅ **5. Cài SSL (HTTPS) với ZEROSSL**

### Bước 1:
Tải chứng chỉ ssl từ https://app.zerossl.com/certificates
![Screenshot from 2025-06-17 11-22-02](https://github.com/user-attachments/assets/8cb53f16-e326-4111-947d-e1b0da6af22d)






### Bước 2:
Vào website [sslshopper](https://www.sslshopper.com/ssl-converter.html)
Để chuyển từ file PEM thành file PFX 
![Screenshot from 2025-06-17 11-23-49](https://github.com/user-attachments/assets/0e2155e6-dd21-43af-ba62-68e092d4e6fc)

### Bước 3 Vào giao diện ISS Manager 

* Chọn `N` → `Create new certificate (simple)` → chọn site
* Tool sẽ tự cấu hình SSL và gia hạn tự động cho IIS
![Screenshot from 2025-06-17 11-26-15](https://github.com/user-attachments/assets/a82b5350-5838-470b-aed1-2b101bd19261)

---


### Bước 4 Add SSl vào website
* Click vào wp.nhan.vietnix.tech
* Click vào blinding
* Chọn https, domain và ssl

![Screenshot from 2025-06-17 11-28-12](https://github.com/user-attachments/assets/ad6bb2c0-f113-44e5-ac48-46eee5e44247)

### Kết quả đạt được 

![Screenshot from 2025-06-17 11-29-34](https://github.com/user-attachments/assets/6f479512-8c79-4e1e-88b3-8862410fa046)
![Screenshot from 2025-06-17 11-30-01](https://github.com/user-attachments/assets/583ff4d9-86bf-400e-8159-972cc49b9c21)


