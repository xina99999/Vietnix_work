Rất tốt! Nếu bạn muốn thực hiện mọi thứ bằng **giao diện đồ họa (UI)** trên Windows, mình sẽ hướng dẫn chi tiết từng bước theo giao diện. Chúng ta chia làm 2 phần lớn:

---

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

### 🔁 Tương tự để Allow theo IP:

* Chọn loại **Custom**
* Đến bước **Scope**, ở phần **Remote IP address**, chọn: **These IP addresses**
  → Add IP cần cho phép (VD: `192.168.1.100`)

---

## 🚫 **2. Block port / IP**

Thực hiện tương tự như trên nhưng:

* Ở bước **Action**: Chọn **Block the connection**
* Ở bước **Scope**: Nếu block IP → nhập IP cần chặn
* Ở bước **Protocol and Ports**: Nếu block port → nhập port cần chặn

---

## 🔐 **3. Giới hạn IP truy cập port**

Chỉ cho phép IP cụ thể truy cập port (ví dụ port 3389 - Remote Desktop):

1. Tạo **rule Allow** port 3389 cho IP cụ thể như trên
2. Sau đó tạo thêm **rule Block** tất cả IP khác cho cùng port

---

# 🌐 PHẦN 2: CÀI ĐẶT IIS + WORDPRESS + MYSQL + SSL BẰNG GIAO DIỆN

## ✅ **1. Cài đặt IIS**

### Bước 1:

* Mở `Server Manager` → `Add roles and features`
* Chọn:

  * Role-based
  * Web Server (IIS)
  * Tick: Web Server, Common HTTP Features, Application Development (bao gồm CGI nếu dùng PHP)
  * Install

## ✅ **2. Cài MySQL**

* Tải MySQL Installer từ: [https://dev.mysql.com/downloads/installer/](https://dev.mysql.com/downloads/installer/)
* Chạy file, chọn **Developer Default**
* Đặt password cho `root`, cấu hình port (mặc định là 3306)

## ✅ **3. Cài PHP**

* Tải PHP: [https://windows.php.net/download/](https://windows.php.net/download/)
* Giải nén vào `C:\PHP`
* Vào **IIS Manager**:

  * Chọn server > **Handler Mappings** → Add Module Mapping:

    * Request path: `*.php`
    * Module: `FastCgiModule`
    * Executable: `C:\PHP\php-cgi.exe`
    * Name: `PHP_via_FastCGI`

## ✅ **4. Cài WordPress**

* Tải từ [https://wordpress.org/latest.zip](https://wordpress.org/latest.zip)
* Giải nén vào thư mục, ví dụ `C:\inetpub\wwwroot\wordpress`
* Trong **IIS Manager**:

  * Click phải `Sites` → Add Website:

    * Site name: `WordPress`
    * Path: folder WordPress
    * Port: 80 hoặc 8080
    * Host name: có thể thêm tên miền nếu có
* Sau đó truy cập trình duyệt: `http://localhost/` hoặc `http://localhost:8080`

## ✅ **5. Cài SSL (HTTPS) với Let's Encrypt UI**

Dùng công cụ miễn phí \[**Win-ACME**]:

### Bước 1:

* Tải về tại: [https://www.win-acme.com/](https://www.win-acme.com/)
* Giải nén và chạy file `wacs.exe`

### Bước 2:

* Giao diện dạng dòng lệnh nhưng dễ hiểu
* Chọn `N` → `Create new certificate (simple)` → chọn site
* Tool sẽ tự cấu hình SSL và gia hạn tự động cho IIS

---

Bạn có thể thực hiện song song trên **máy ảo** (VM) để luyện tập trước nếu chưa chắc.

---

Nếu bạn muốn mình **gửi hình ảnh từng bước**, mình có thể tạo bản ảnh minh họa. Bạn cần mình hỗ trợ thêm phần nào trước?
