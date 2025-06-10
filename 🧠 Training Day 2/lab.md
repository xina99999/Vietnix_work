# 1. Ping đến domain vietnix.vn sau đó giải thích ttl là gì, time là gì?
![Screenshot from 2025-06-10 11-40-45](https://github.com/user-attachments/assets/7f5f926a-b3f2-4996-bf9f-47c2ff517d8c)

- TTL= (Time To Live)
    Khái niệm:
    TTL là số "bước nhảy" (hop) tối đa mà gói tin được phép đi qua trước khi bị hủy. Mỗi khi gói tin qua một router (hoặc thiết bị mạng), TTL giảm đi 1. Nếu TTL=0, gói tin bị loại bỏ và trả về thông báo Time Exceeded.

    Mục đích:

        Ngăn chặn gói tin lặp vô hạn trên mạng (do định tuyến lỗi).

        Giúp xác định đường đi của gói tin (dùng trong traceroute).

    Giá trị phổ biến:

        Hệ điều hành Windows: TTL=128 (mặc định).

        Linux/Unix: TTL=64.

        Router/Internet: Thường giảm dần.

    Ví dụ trong kết quả ping:
    ttl=53 nghĩa là gói tin từ vietnix.vn đã đi qua:

        Nếu máy chủ dùng Linux (TTL=64 ban đầu) → 64 - 53 = 11 hop.

        Nếu máy chủ dùng Windows (TTL=128) → 128 - 53 = 75 hop (ít khả năng xảy ra).
  
- Time= (Round-Trip Time - RTT)
        Khái niệm:
    time= (hoặc rtt= trong hping3) là thời gian (ms) để gói tin đi từ máy bạn đến máy chủ và quay trở lại.

    Yếu tố ảnh hưởng:

        Khoảng cách địa lý giữa client và server.

        Chất lượng đường truyền mạng (cáp quang, 4G, WiFi).

        Tải trên máy chủ hoặc router trung gian.

    Giá trị lý tưởng:

        < 50ms: Tốt (cùng mạng nội bộ hoặc cùng quốc gia).

  

        50ms - 150ms: Chấp nhận được (quốc gia lân cận).

        > 200ms: Độ trễ cao (server ở xa hoặc mạng không ổn định).

# 2. SSH
## SSH password
![Screenshot from 2025-06-10 11-48-04](https://github.com/user-attachments/assets/4fe965b7-97df-4bc8-91fb-250682cbfff0)
## SSH private key
![Screenshot from 2025-06-10 11-52-54](https://github.com/user-attachments/assets/4e4b9737-c4e1-489e-a0eb-aa18e531c198)
## SSH port custom
![Screenshot from 2025-06-10 11-54-48](https://github.com/user-attachments/assets/28b26b29-8b94-44d4-a23e-7de2ddd417ec)

# 3. SCP
## SCP file
![Screenshot from 2025-06-10 11-59-15](https://github.com/user-attachments/assets/1b423b53-6b33-4d7d-960a-65ab09eabf26)
## SCP folder
![Screenshot from 2025-06-10 12-01-12](https://github.com/user-attachments/assets/5455fe3c-d1b9-446c-a9d8-ec50e6cf4800)

# 4. RSYNC
## RSYNC FILE
![Screenshot from 2025-06-10 13-36-46](https://github.com/user-attachments/assets/4a132c6b-d956-4b92-893b-5be9840f9fe3)

## RSYNC FOLDER
![Screenshot from 2025-06-10 13-40-45](https://github.com/user-attachments/assets/b50dfeef-2048-49f2-9e7e-b09b594cb9d4)

## RSYNC INCREAMENTAL
![Screenshot from 2025-06-10 13-50-00](https://github.com/user-attachments/assets/7d56e47d-c1a3-4309-9747-18e4eb71793a)

#  4. CAT COMMAND
## CAT FILE
![Screenshot from 2025-06-10 13-52-46](https://github.com/user-attachments/assets/a79fb935-41a1-4a4a-aa3e-c422fd160f63)

## CAT dòng thứ <n> trong file
![Screenshot from 2025-06-10 14-04-30](https://github.com/user-attachments/assets/c512e31b-1c67-4363-880e-2987606c822e)

## CAT nhiều dòng vào 1 file bằng EOF
![Screenshot from 2025-06-10 14-08-29](https://github.com/user-attachments/assets/fb12a979-d443-4dc9-86a1-f06d4f42b8e8)

# ECHO command
## Dùng echo để chèn thêm 1 dòng vào cuối file
![Screenshot from 2025-06-10 14-10-42](https://github.com/user-attachments/assets/e389f46d-facb-451d-9fc6-851da25e1220)

## Dùng echo để overwirte nội dung của file
![Screenshot from 2025-06-10 14-11-49](https://github.com/user-attachments/assets/dda9961a-cf4a-4920-9473-6d2a680df2f9)

# 5. Tail/head command
![Screenshot from 2025-06-10 14-24-36](https://github.com/user-attachments/assets/2c7b7d4f-e13b-4df2-9f5c-ea8aad5f89ae)
Kết luận 
- Tail gọi dòng cuối của file xong đó kết thúc
- Tail -f lấy từ dóng cuối của file và chời đợi tiếp tục

# 6. Sed command
## Dùng sed để find and replace một string trong file
![Screenshot from 2025-06-10 14-33-32](https://github.com/user-attachments/assets/5059feaa-5c2b-4276-9e06-969ea0fcdbf8)

# 7. Traceroute/tracert command
![Screenshot from 2025-06-10 14-40-38](https://github.com/user-attachments/assets/77619760-6a0a-4b48-8ce3-eb0ae0e2f04e)

Giải thích:
## 📌 Giải thích chi tiết:

| Vị trí                         | Lý do có thể xảy ra                                           |
| ------------------------------ | ------------------------------------------------------------- |
| 🏠 Hop 1 (Router )  | Có thể đã chặn ICMP hoặc không phản hồi TTL-expired packets   |
| 🌐 Các hop 2-4 (ISP, nhà mạng) | Nhà mạng thường chặn `traceroute`  |
| 🛡️ Vietnix (đích đến)         | Cấu hình bảo mật, không phản hồi traceroute để chống dò đường |
| 🔥 Tường lửa hoặc NAT          | Một số thiết bị không cho phép gói `ICMP/UDP` phản hồi        |

---

# 8. Netstat command

| Mục tiêu                               | Tùy chọn `netstat`      | Giải thích                            |
| -------------------------------------- | ----------------------- | ------------------------------------- |
| **1. Hiển thị các socket đang listen** | `-l` hoặc `--listening` | Chỉ hiển thị socket đang lắng nghe    |
| **2. Không resolve hostname**          | `-n`                    | Không chuyển IP → hostname            |
| **3. Không resolve port name**         | `-n`                    | Không chuyển port → tên dịch vụ       |
| **4. Hiển thị process name / PID**     | `-p`                    | Hiển thị PID/process đang dùng socket |
| **5. Chỉ hiển thị TCP socket**         | `-t`                    | Chỉ hiện TCP                          |
| **6. Chỉ hiển thị UDP socket**         | `-u`                    | Chỉ hiện UDP                          |

![Screenshot from 2025-06-10 14-54-01](https://github.com/user-attachments/assets/78ff8155-ee4e-43fe-bda1-622fb5dedae2)

# SORT COMMAND
## Sort theo thứ tự tăng dần
![Screenshot from 2025-06-10 15-00-55](https://github.com/user-attachments/assets/c65af4d7-12d1-4dcb-9119-a25b21a7be64)

## sort theo thứ tự giảm dần
![Screenshot from 2025-06-10 15-01-41](https://github.com/user-attachments/assets/785abba3-6d85-4caf-bf0e-e6ba028293cc)

## sort theo column
![Screenshot from 2025-06-10 15-02-52](https://github.com/user-attachments/assets/8626d810-6c28-4405-9b79-1a481dba1be2)

# UNIQ COMMAND
## lọc ra các dòng lặp lại trong một file
![Screenshot from 2025-06-10 15-13-21](https://github.com/user-attachments/assets/bcb9b20d-2678-4799-a9c4-18ee26b18cfb)

## lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại
![Screenshot from 2025-06-10 15-11-50](https://github.com/user-attachments/assets/27097f6c-82b8-4d8f-a264-2487f02dbeeb)


# WC COMMAND
## Đếm số dòng trong file
![Screenshot from 2025-06-10 15-15-43](https://github.com/user-attachments/assets/60d85f9f-f8fa-4f47-accd-8a6e0cd8b725)

## Đếm số kí tự trong file
![Screenshot from 2025-06-10 15-17-44](https://github.com/user-attachments/assets/d65bf565-13fd-464f-b896-4d0486c1fd2b)

# CHMOD, CHOWN, CHATTR command
## CHMOD Command phân quyền bằng số
![Screenshot from 2025-06-10 15-19-47](https://github.com/user-attachments/assets/0137c62f-716b-4155-89eb-1b1be74af244)

## CHMOD phân quyền bằng chữ
![Screenshot from 2025-06-10 15-22-39](https://github.com/user-attachments/assets/3bb49b60-452a-4396-990e-396612405ced)

## Đổi OWNER USER/GROUP
- Đổi user
![Screenshot from 2025-06-10 15-28-28](https://github.com/user-attachments/assets/2b942486-c87f-4c2d-94cf-8507f3333d2a)
- Đổi group
![Screenshot from 2025-06-10 15-30-01](https://github.com/user-attachments/assets/a2f325ae-b642-4bc6-8ce7-0f25164b8a10)
- Set Immutable Attribute
![Screenshot from 2025-06-10 15-32-03](https://github.com/user-attachments/assets/d4b731a7-a5e6-42c2-9bac-89b8688d3852)

# FIND COMMAND
## find các file có đuôi .log
![Screenshot from 2025-06-10 15-36-03](https://github.com/user-attachments/assets/de84f24b-65b1-4689-9a0f-ef7e9d6bb1d2)

## find các folder có tên domain
![Screenshot from 2025-06-10 15-36-03](https://github.com/user-attachments/assets/9ca8139a-0010-478b-be77-990886319631)

## find các file có tên abc
![Screenshot from 2025-06-10 15-39-16](https://github.com/user-attachments/assets/82b53099-70e3-4969-a37e-ba21f1e691dd)

## find các file có tên abc và thực hiện phần quyền read only cho file
![Screenshot from 2025-06-10 15-41-38](https://github.com/user-attachments/assets/f0302afc-fc72-4eae-ae9e-4b2507ef2ab3)

# CP COMMAND
## CP FILE
![Screenshot from 2025-06-10 15-45-17](https://github.com/user-attachments/assets/1521870f-d4c4-4e69-8fff-41c3d344a374)

## CP FOLDER
![Screenshot from 2025-06-10 15-48-14](https://github.com/user-attachments/assets/2359fcdc-7658-42d9-ae1f-7b9340cac69f)

# MV COMMAND
## MV FILE
![Screenshot from 2025-06-10 15-51-26](https://github.com/user-attachments/assets/2b1a7f3d-7928-4e49-9fec-94f75de92574)

## MV FOLDER
![Screenshot from 2025-06-10 15-52-32](https://github.com/user-attachments/assets/cfc5a503-f4c5-4e96-8002-0dd58d66a746)

# CUT COMMAND
## cut kí tự thứ <n> trong string
![Screenshot from 2025-06-10 15-58-48](https://github.com/user-attachments/assets/b2f0292d-f2ad-4827-8748-e183fafc9695)

## cut từ kí tự thứ <n> trở về sau
![Screenshot from 2025-06-10 15-59-43](https://github.com/user-attachments/assets/971b61d0-8978-43d0-946f-bdb078168abd)

## cut từ kí tự thứ <n> trở về trước
![Screenshot from 2025-06-10 16-00-10](https://github.com/user-attachments/assets/90330f00-07de-4c50-abd3-5e093803a447)

# DIG COMMAND
## Dùng Dig command để kiểm tra resolv record A, MX, NS
![Screenshot from 2025-06-10 16-04-55](https://github.com/user-attachments/assets/c4bdb526-2e05-44d1-9115-bdbbf2987039)


## Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS
![Screenshot from 2025-06-10 16-04-05](https://github.com/user-attachments/assets/ae702e9e-97d4-4aa5-a605-2b06d7501b4e)

# tar/zip/unzip command
## Nén/Giải nén file tar.gz
![Screenshot from 2025-06-10 16-15-05](https://github.com/user-attachments/assets/b09db1bc-4060-4b36-8553-a4a252a0ad80)


## Nén/Giải nén file .zip
![Screenshot from 2025-06-10 16-12-48](https://github.com/user-attachments/assets/87540056-e052-4d6d-8dbd-8f6fdae7a482)

# Symbolic Links, Hard Links command

## Định nghĩ Sym Link

## Định nghĩ Hard Link

## Ví dụ về Sym Link và Hard Link

## **Symbolic Links (Symlink) và Hard Links**

### **1. Định nghĩa**
| Loại Link          | Symbolic Link (Symlink)                                                                 | Hard Link                                                                 |
|--------------------|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| **Định nghĩa**     | Là một "shortcut" trỏ đến file hoặc thư mục khác.                                      | Là một bản sao tham chiếu trực tiếp đến inode của file gốc.               |
| **Inode**          | Có inode riêng, khác với file gốc.                                                    | Dùng chung inode với file gốc.                                           |
| **Xóa file gốc**   | Symlink bị "broken" (vẫn tồn tại nhưng không trỏ đến đâu).                            | Dữ liệu vẫn tồn tại nếu còn ít nhất 1 Hard Link.                         |
| **Liên kết**       | Có thể trỏ đến file/thư mục trên phân vùng khác.                                       | Chỉ liên kết được trong cùng một phân vùng.                              |
| **Hiển thị**       | `lrwxrwxrwx` (trong `ls -l`)                                                          | Giống file thường (không phân biệt được bằng `ls -l`).                    |

---

### **2. Ví dụ thực hành**
#### **🔗 Tạo Symlink (Symbolic Link)**
```bash
ln -s /đường/dẫn/file_hoặc_thư_mục_gốc /đường/dẫn/symlink
```
**Ví dụ:**
```bash
ln -s /var/www/html website  # Tạo symlink "website" trỏ đến /var/www/html
ls -l website                # Kết quả: lrwxrwxrwx 1 user user 14 Jan 1 12:00 website -> /var/www/html
```
**Đặc điểm:**
- Nếu xóa `/var/www/html`, symlink `website` vẫn tồn tại nhưng không hoạt động.
- Có thể trỏ đến file/thư mục trên ổ đĩa khác.

---

#### **🔗 Tạo Hard Link**
```bash
ln /đường/dẫn/file_gốc /đường/dẫn/hardlink
```
**Ví dụ:**
```bash
touch original.txt          # Tạo file gốc
ln original.txt hardlink.txt  # Tạo hardlink
ls -li                      # Kiểm tra inode (cùng số inode)
```
**Kết quả:**
```
12345 -rw-r--r-- 2 user user 0 Jan 1 12:00 original.txt
12345 -rw-r--r-- 2 user user 0 Jan 1 12:00 hardlink.txt
```
**Đặc điểm:**
- Xóa `original.txt` → `hardlink.txt` vẫn truy cập được dữ liệu.
- Không thể tạo Hard Link cho thư mục.

---

### **3. So sánh chi tiết**
| Tiêu chí          | Symbolic Link                                                                 | Hard Link                                                                 |
|-------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| **Inode**         | Khác với file gốc                                                           | Giống file gốc                                                           |
| **Phân vùng**    | Liên kết được giữa các phân vùng khác nhau                                  | Chỉ hoạt động trong cùng phân vùng                                       |
| **Thư mục**      | Có thể trỏ đến thư mục                                                      | Không thể tạo Hard Link cho thư mục                                      |
| **Xóa file gốc** | Symlink trở thành "dangling link" (broken)                                  | Dữ liệu vẫn tồn tại đến khi không còn Hard Link nào                      |
| **Dung lượng**   | Tốn ít dung lượng (chỉ lưu đường dẫn)                                       | Tăng "link count" của file gốc, không tốn thêm dung lượng                |

---

### **4. Lệnh kiểm tra**
- **Xem inode** (để phân biệt Hard Link):
  ```bash
  ls -li
  ```
- **Kiểm tra số Hard Link**:
  ```bash
  ls -l
  ```
  → Số trước owner (vd: `2` trong `-rw-r--r-- 2 user user`) là số Hard Link.

---

### **5. Khi nào dùng cái gì?**
- **Dùng Symlink khi**:
  - Cần trỏ đến file/thư mục trên phân vùng khác.
  - Cần tạo shortcut cho thư mục.
- **Dùng Hard Link khi**:
  - Muốn bảo vệ dữ liệu (không mất dữ liệu khi xóa file gốc).
  - Làm việc trong cùng phân vùng.

---

💡 **Lưu ý**:
- Hard Link không thể dùng cho thư mục (chỉ Symlink được).
- Symlink có thể gây lỗi nếu file gốc bị di chuyển/xóa.


# ls command

## Liệt kê danh sách file/thư mục
![Screenshot from 2025-06-10 16-21-55](https://github.com/user-attachments/assets/c2051410-e8a7-494f-a200-a3bc18f6fc72)

## Liệt kê danh sách file/thư mục và thuộc tính
![Screenshot from 2025-06-10 16-22-25](https://github.com/user-attachments/assets/28d2a1c0-ef6d-4f66-9916-796daeeb80a3)

## Show file ẩn
![Screenshot from 2025-06-10 16-25-25](https://github.com/user-attachments/assets/631d0fed-0881-4b82-9419-61d96625ade4)


# ps command

## show tiến trình
![Screenshot from 2025-06-10 16-30-03](https://github.com/user-attachments/assets/e7c29486-b9e9-446e-bd35-89ef0be39e59)


## kill tiến trình
![Screenshot from 2025-06-10 16-32-23](https://github.com/user-attachments/assets/ea046fb7-b45d-46f9-94f2-f335384dfa3c)

# top command

## Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy

![Screenshot from 2025-06-10 16-37-59](https://github.com/user-attachments/assets/8b517fe5-df14-413b-a0fd-d22f717eaf11)

## Giải thích về Load average, us, sy, ni, id, wa, hi, si, st, zombie process, sleeping process

- Dòng đầu tiên sẽ thể hiện thời gian của server:

    Thời gian hoạt động hiện tại: 08:05:45
    Thời gian uptime: 23 ngày
    Số lượng user đang login: 2 user
    Load average của server trong 1/5/15 phút: 0.00 0.00 0.00

    Thông thường với một máy chủ có 1 Core CPU, không sử dụng Hyper Threading thì ngưỡng hoạt động trong 1 phút của hệ thống sẽ là khoảng 0.7, Nếu Load average của vượt quá ngưỡng trên cần kiểm tra lại xem process nào đang overload hoặc có phương hướng nâng cấp tài nguyên của hệ thống lên thêm nữa.

- Tại dòng 2 Task: Thông tin các tiến trình đang hoạt động trên hệ thống.

- Tại dòng 3 Phần trăm CPU: Bao gồm các thông số sau.

    %us: %CPU được dùng cho từng tiến trình của User.
    %sy: %CPU được dùng cho từng tiến trình của hệ thống.
    %ni: %CPU dành cho low-priority processes.
    %id: %CPU ở trạng thái nghỉ.
    %wa: %CPU đang trong thời gian chờ I/O.
    %hi: %CPU được dành cho phần cứng khi bị gián đoạn.
    %si: %CPU được dành cho phần mềm khi bị gián đoạn.
    %st: %CPU ảo chờ đợi CPU thực xử lý các process.

- Tại dòng 4 là thông tin về RAM.

- Tại dòng 5 là thông tin về SWAP.

# free command

## Giải thích ram used, free, shared, buff/cache, free
![Screenshot from 2025-06-10 16-41-14](https://github.com/user-attachments/assets/00fea963-c80f-429b-9f90-0cb4ed3faae3)

- Giải thích
  
    free: Lệnh xem lượng RAM còn trống, đang sử dụng trên Linux
    -m: Đối số truyền vào để hiển thị đơn vị Megabyte. Bạn có thể sử dụng -g để xem hiển thị theo Gigabyte
    Cột used: RAM đang sử dụng
    Cột free: Ram đang còn trống.
    Cột available: Khả dụng để sử dụng.

# df command

## Xem dung lượng disk
![Screenshot from 2025-06-10 16-46-47](https://github.com/user-attachments/assets/cba3d2a0-0148-43c2-81c1-9841764afb40)

### **2. Phân vùng `/` (root) là gì?**
- **Định nghĩa**:  
  `/` là **phân vùng gốc** (root partition), chứa toàn bộ hệ thống tập tin của Linux (trừ các phân vùng được mount riêng như `/home`, `/boot`).  
  → Tất cả thư mục khác (`/etc`, `/bin`, `/usr`, ...) đều nằm trong `/` hoặc được mount vào nó.

- **Tầm quan trọng**:  
  - Nếu `/` đầy, hệ thống có thể bị treo hoặc lỗi.  
  - Thường được đặt trên phân vùng riêng (vd: `/dev/nvme0n1p4` trong ví dụ trên).

---

