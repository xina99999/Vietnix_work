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


