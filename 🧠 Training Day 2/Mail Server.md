# MX Record

## MX Record là gì?

MX Record (Mail Exchange) là một loại bản ghi DNS giúp điều hướng email đến đúng máy chủ thư. Bản ghi này chỉ ra địa chỉ IP của máy chủ thư của một miền.

**Công dụng:**
- Phân biệt giữa máy chủ web và máy chủ email
- Chỉ dẫn email đến đúng máy chủ thư (vd: Gmail hoặc máy chủ email thuê ngoài)
- Chỉ định và sắp xếp thứ tự ưu tiên cho nhiều máy chủ email
- Quan trọng trong khắc phục sự cố gửi email

## Cấu trúc DNS MX Record

| Thành phần       | Mô tả                                                                 | Ví dụ               |
|------------------|-----------------------------------------------------------------------|---------------------|
| Tên miền         | Tên miền áp dụng MX Record                                           | examplesite.com     |
| TTL              | Thời gian sống của bản ghi trong cache DNS (tính bằng giây)          | 3600 (1 giờ)        |
| Độ ưu tiên       | Số nguyên xác định thứ tự ưu tiên (số nhỏ hơn = ưu tiên cao hơn)     | 10                  |
| Máy chủ thư      | Tên miền của máy chủ thư nhận email                                  | mail.examplesite.com|

---

# DKIM

## DKIM là gì?

DomainKeys Identified Mail (DKIM) là phương thức xác nhận email thông qua chữ ký số, giúp:
- Phát hiện email giả mạo
- Gắn chữ ký điện tử liên kết với tên miền vào mỗi email gửi đi
- Cho phép người nhận xác minh bằng khóa công khai trong DNS

## Tại sao DKIM quan trọng?

✅ Giảm khả năng email vào thư mục Spam/Rác  
✅ Chống giả mạo email từ miền đáng tin  
✅ Tương thích với SPF và DMARC để tăng bảo mật  
✅ Xây dựng danh tiếng tên miền với ISP  

**Hạn chế:**  
❌ Không mã hóa nội dung email  
❌ Không phải tiêu chuẩn bắt buộc  

## Cách hoạt động

1. **Người gửi:**
   - Tạo cặp khóa private/public (dùng OpenSSL)
   - Public key → Bản ghi TXT trên DNS
   - Mail server dùng private key ký email trước khi gửi

2. **Người nhận:**
   - Nhận email có thông điệp mã hóa DKIM
   - Query DNS lấy Public key để giải mã
   - Xác nhận nguồn gửi nếu giải mã thành công

---

# SPF

## SPF là gì?

Sender Policy Framework (SPF) là cơ chế xác thực email giúp:
- Phát hiện và ngăn chặn email giả mạo
- Kiểm tra máy chủ gửi có được ủy quyền không
- Sử dụng bản ghi TXT SPF trong DNS

## Lợi ích SPF

✔️ Ngăn chặn thư rác/giả mạo  
✔️ Tăng cường bảo mật hệ thống email  
✔️ Nâng cao uy tín tên miền  
✔️ Cải thiện khả năng gửi email  

## Định dạng TXT SPF Record

Bắt đầu bằng `v=spf1` + các quy tắc phân cách bằng khoảng trắng/dấu phẩy

## 📄 Bảng Tùy Chọn SPF Record

| Tùy chọn | Mô tả                                                                                                                   |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| `a`      | Ủy quyền cho địa chỉ IP từ bản ghi A của tên miền gửi email thay mặt tên miền                                           |
| `mx`     | Ủy quyền cho địa chỉ IP từ bản ghi MX của tên miền gửi email thay mặt tên miền                                          |
| `ip4`    | Ủy quyền cho địa chỉ IPv4 được chỉ định gửi email thay mặt tên miền                                                     |
| `ip6`    | Ủy quyền cho địa chỉ IPv6 được chỉ định gửi email thay mặt tên miền                                                     |
| `include`| Thêm bản ghi SPF của một tên miền khác vào bản ghi hiện tại                                                             |
| `all`    | Xác định cách xử lý các địa chỉ không khớp với bất kỳ quy tắc nào. Có thể dùng với:                                     |
|          | - `-all` (hard fail): Từ chối nhận email không hợp lệ                                                                  |
|          | - `~all` (soft fail): Chấp nhận email nhưng đánh dấu là đáng ngờ                                                        |
|          | - `+all` (pass): Chấp nhận tất cả email                                                                                 |
|          | - `?all` (neutral): Không xác định, không fail cũng không pass                                                          |


---

# PTR Record

## PTR là gì?

Point Record (PTR) là bản ghi ngược (Reverse DNS) chuyển đổi từ IP sang tên miền.

**Khác biệt với A Record:**
- A Record: Tên miền → IP
- PTR Record: IP → Tên miền

## Tầm quan trọng

🔹 Yêu cầu bắt buộc cho reverse DNS lookup  
🔹 Tăng độ tin cậy server mail (chống spam)  
🔹 Kiểm tra hostname gửi email bất kỳ lúc nào  

**Lưu ý:** PTR Record và A Record hoạt động độc lập
