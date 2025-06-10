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

# Tail/head command
![Screenshot from 2025-06-10 14-24-36](https://github.com/user-attachments/assets/2c7b7d4f-e13b-4df2-9f5c-ea8aad5f89ae)
Kết luận 
- Tail gọi dòng cuối của file xong đó kết thúc
- Tail -f lấy từ dóng cuối của file và chời đợi tiếp tục

# Sed command
## Dùng sed để find and replace một string trong file
![Screenshot from 2025-06-10 14-33-32](https://github.com/user-attachments/assets/5059feaa-5c2b-4276-9e06-969ea0fcdbf8)

# traceroute/tracert command
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

# Netstat command

| Mục tiêu                               | Tùy chọn `netstat`      | Giải thích                            |
| -------------------------------------- | ----------------------- | ------------------------------------- |
| **1. Hiển thị các socket đang listen** | `-l` hoặc `--listening` | Chỉ hiển thị socket đang lắng nghe    |
| **2. Không resolve hostname**          | `-n`                    | Không chuyển IP → hostname            |
| **3. Không resolve port name**         | `-n`                    | Không chuyển port → tên dịch vụ       |
| **4. Hiển thị process name / PID**     | `-p`                    | Hiển thị PID/process đang dùng socket |
| **5. Chỉ hiển thị TCP socket**         | `-t`                    | Chỉ hiện TCP                          |
| **6. Chỉ hiển thị UDP socket**         | `-u`                    | Chỉ hiện UDP                          |

![Screenshot from 2025-06-10 14-54-01](https://github.com/user-attachments/assets/78ff8155-ee4e-43fe-bda1-622fb5dedae2)















