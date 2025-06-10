
# Domain

## Domain là gì?
**Domain**, hay còn gọi là **tên miền**, là địa chỉ website của bạn trên Internet. Giống như mỗi ngôi nhà có địa chỉ riêng, mỗi website cũng cần một domain để người dùng truy cập. Domain giúp thay thế cho các địa chỉ IP khó nhớ bằng tên dễ đọc, dễ ghi nhớ và chia sẻ.

## Các trạng thái của domain

### Trạng thái tên miền tại Đơn vị Cấp phát tên miền (Registry)

#### 📄 Bảng Trạng Thái Tên Miền

| Trạng thái | Mô tả | Hành động/Khuyến nghị |
|------------|-------|------------------------|
| `OK / active` | Tên miền hoạt động bình thường. | Nên bật: `clientTransferProhibited`, `clientDeleteProhibited`, `clientUpdateProhibited` |
| `addPeriod` | Trạng thái ngay sau khi đăng ký tên miền. | Không có vấn đề, sẽ tự kết thúc sau vài ngày. |
| `autoRenewPeriod` | Sau khi tên miền được tự động gia hạn. | Có thể hủy gia hạn nhưng có thể bị tính phí. |
| `inactive` | Đã đăng ký nhưng chưa gán Name Server. | Liên hệ nhà đăng ký nếu kéo dài quá lâu. |
| `pendingCreate` | Đang xử lý yêu cầu tạo tên miền. | Chờ xử lý hoàn tất. |
| `pendingDelete` | Tên miền chờ xóa sau khi hết hạn. | Có thể chờ đăng ký lại nếu cần. |
| `pendingRenew` | Đang xử lý yêu cầu gia hạn tên miền. | Theo dõi tiến trình. |
| `pendingRestore` | Tên miền hết hạn đang chờ khôi phục. | Theo dõi 7 ngày, nếu về `redemptionPeriod` thì liên hệ gấp nhà đăng ký. |
| `pendingTransfer` | Tên miền chờ chuyển nhà đăng ký. | Nếu không chuyển, yêu cầu từ chối và đặt `clientTransferProhibited`. |
| `pendingUpdate` | Đang chờ cập nhật thông tin tên miền. | Liên hệ nhà đăng ký nếu không yêu cầu cập nhật. |
| `redemptionPeriod` | Tên miền hết hạn, cần trả phí để khôi phục. | Liên hệ nhà đăng ký trong vòng 30 ngày để giữ tên miền. |
| `renewPeriod` | Trạng thái sau khi gia hạn. | Xác nhận lại thông tin gia hạn nếu cần. |
| `serverDeleteProhibited` | Ngăn xóa tên miền (thường do tranh chấp hoặc redemption). | Liên hệ nhà đăng ký để xử lý. |
| `serverHold` | Không kích hoạt tên miền trong DNS. | Kiểm tra với nhà đăng ký. |
| `serverRenewProhibited` | Không cho phép gia hạn (tranh chấp pháp lý). | Nhà đăng ký phải làm việc với cơ quan cấp phát. |
| `serverTransferProhibited` | Không cho phép chuyển đổi nhà đăng ký. | Liên hệ nhà đăng ký nếu muốn gỡ bỏ. |
| `serverUpdateProhibited` | Không cho phép cập nhật thông tin tên miền. | Liên hệ nhà đăng ký để được hỗ trợ. |
| `transferPeriod` | Sau khi chuyển nhà đăng ký xong, chờ xác nhận. | Nếu không yêu cầu chuyển, hãy kiểm tra lại với nhà đăng ký ban đầu. |

### Trạng thái tên miền tại Nhà đăng ký tên miền (Registrar)

#### 📄 Trạng Thái "Client" Của Tên Miền

| STT | Trạng thái | Ý nghĩa | Hành động |
|-----|------------|--------|-----------|
| 1 | `clientDeleteProhibited` | Cấm hủy tên miền, ngăn việc xóa trái phép. | Nếu cần xóa, liên hệ nhà đăng ký. |
| 2 | `clientHold` | Tạm ngừng hoạt động tên miền, DNS không hoạt động. | Liên hệ nhà đăng ký để hoàn thành hồ sơ hoặc yêu cầu gỡ. |
| 3 | `clientRenewProhibited` | Cấm gia hạn tên miền (liên quan tranh chấp). | Liên hệ nhà đăng ký để xử lý. |
| 4 | `clientTransferProhibited` | Cấm chuyển đổi nhà đăng ký. | Nếu muốn chuyển, cần yêu cầu gỡ trạng thái. |
| 5 | `clientUpdateProhibited` | Cấm cập nhật thông tin tên miền. | Liên hệ nhà đăng ký nếu cần thay đổi thông tin. |

### Subdomain là gì?
**Subdomain** là phần mở rộng, xuất hiện trước tên miền chính. Nó hoạt động như một website độc lập và thường được tạo miễn phí, giúp tiết kiệm chi phí đăng ký tên miền mới. Subdomain hữu ích khi bạn muốn phân tách các nội dung hoặc dịch vụ trên cùng một domain.

### Virtual Hosts là gì?
**Virtual Hosts** là tính năng của web server cho phép nhiều trang web hoạt động trên cùng một máy chủ hoặc địa chỉ IP. Điều này giúp tối ưu tài nguyên máy chủ, giảm chi phí và dễ quản lý hosting nhiều website.
