# Hệ thống tên miền (DNS)

## 1. DNS là gì?
DNS (Domain Name System) là hệ thống phân giải tên miền thành địa chỉ IP, được phát minh năm 1984. Đây là nền tảng quan trọng cho các dịch vụ Internet, Mail server và Web server.

## 2. Chức năng chính
- **Dịch tên miền ↔ IP**: Chuyển đổi tên miền dễ nhớ (ví dụ: google.com) thành địa chỉ IP máy tính có thể hiểu (ví dụ: 142.250.204.46)
- Mỗi thiết bị/website có địa chỉ IP duy nhất trên Internet

## 3. Cách hoạt động
![Quy trình DNS](https://vietnix.vn/dns-la-gi/)

1. **Truy vấn**: Trình duyệt gửi yêu cầu đến DNS resolver
2. **Kiểm tra cache**: Tìm trong bộ nhớ tạm trước khi hỏi server
3. **Phân cấp truy vấn**:
   - Root Server → TLD Server (.com, .net) → Authoritative Server
4. **Nhận kết quả**: Trả về IP cho trình duyệt

## 4. Các loại bản ghi DNS
| Loại bản ghi | Chức năng | Ví dụ |
|--------------|-----------|-------|
| A | Trỏ tên miền → IPv4 | 192.168.1.1 |
| AAAA | Trỏ tên miền → IPv6 | 2001:db8::1 |
| CNAME | Tạo bí danh tên miền | www → example.com |
| MX | Chỉ định mail server | mail.example.com |
| TXT | Lưu thông tin văn bản | DKIM, SPF records |
| NS | Chỉ định nameserver | ns1.example.com |
| SRV | Xác định dịch vụ/port | _sip._tcp.example.com |

## 5. Các loại DNS Server
### 5.1. Root Name Server
- 13 server gốc toàn cầu (a.root-servers.net → m.root-servers.net)
- Quản lý các TLD (.com, .org, .net)

### 5.2. Local Name Server
- DNS của ISP/doanh nghiệp
- Lưu cache kết quả truy vấn

### 5.3. Các server khác
| Loại Server | Vai trò |
|-------------|---------|
| Recursor | "Thư viện" chuyển đổi tên miền → IP |
| TLD Server | Quản lý phần mở rộng (.com, .org) |
| Authoritative | Server cuối cùng chứa bản ghi chính thức |

## 6. Cấu hình DNS
**Các bước thay đổi DNS trên Windows:**
1. Vào Control Panel > Network and Sharing Center
2. Chọn mạng đang dùng > Properties
3. Chọn "Internet Protocol Version 4 (TCP/IPv4)"
4. Nhập DNS thủ công (ví dụ: 8.8.8.8, 1.1.1.1)

## 7. Bảo mật DNS
### 7.1. Rò rỉ DNS
**Nguyên nhân:**
- VPN cấu hình sai khiến lưu lượng DNS đi thẳng qua ISP
- Lộ thông tin truy cập website

**Cách kiểm tra:**
1. Dùng [DNSleaktest.com](https://dnsleaktest.com)
2. Kiểm tra IP hiển thị có khớp VPN không

### 7.2. Các hình thức tấn công
- **DDoS**: Làm quá tải DNS server
- **Spoofing**: Giả mạo DNS response
- **Cache Poisoning**: Đưa bản ghi sai vào cache

## 8. So sánh Public vs Private DNS
| Tiêu chí | Public DNS | Private DNS |
|----------|------------|-------------|
| Phạm vi | Toàn cầu | Nội bộ (LAN) |
| Ví dụ | 8.8.8.8, 1.1.1.1 | Active Directory |
| Bảo mật | Thấp hơn | 🔒 Cao (có firewall) |
| IP | Public IP | 192.168.x.x, 10.x.x.x |
| Ưu điểm | Dễ truy cập | Quản lý tập trung |

## 9. Các loại truy vấn DNS
1. **Recursive Query**: Yêu cầu trả lời chính xác hoặc báo lỗi
2. **Iterative Query**: Nhận câu trả lời tốt nhất hiện có
3. **Non-recursive Query**: Truy vấn bản ghi đã cache

## 10. Sự cố DNS
**Khi server DNS lỗi:**
- Gây chậm trễ truy cập
- Có thể làm mất kết nối Internet
- Ví dụ: Sự cố DDoS tấn công Dyn (2016)

**Giải pháp:**
- DNS caching
- Hệ thống dự phòng
- Anycast routing
