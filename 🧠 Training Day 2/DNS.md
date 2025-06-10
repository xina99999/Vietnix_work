# DNS là gì ?
DNS viết tắt của Domain Name System có nghĩa là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.
DNS được phát minh vào năm 1984 cho Internet và đây là một trong số các chuẩn công nghiệp của các cổng bao gồm cả TCP/IP. Hệ thống phân giải tên miền chính là chìa khóa chủ chốt của nhiều dịch vụ mạng hiện nay như Internet, Mail server, Web server…

# Chức năng của DNS dùng để làm gì?
DNS đóng vai trò như một “biên dịch viên” giữa tên miền và địa chỉ IP. Tên miền là chuỗi ký tự dễ nhớ, trong khi địa chỉ IP là chuỗi số khó nhớ. DNS giúp chuyển đổi tên miền thành địa chỉ IP, từ đó giúp máy tính có thể truy cập vào các trang web trên internet.

Mỗi máy tính khi kết nối vào Internet sẽ được gán cho 1 địa chỉ IP (Ví dụ: 1414.1158.62462) riêng biệt và không trùng lẫn với bất kỳ máy tính nào khác trên thế giới. Cũng giống như vậy đối với website cũng có địa chỉ IP riêng biệt của website đó.

# Cách thức hoạt động của DNS
- Khi người dùng truy cập một website, máy tính sẽ gửi yêu cầu đến máy chủ DNS cục bộ để tìm địa chỉ IP của website đó. Máy chủ DNS cục bộ sẽ kiểm tra cơ sở dữ liệu của mình xem có chứa địa chỉ IP của website hay không. Nếu có, sẽ trả về địa chỉ IP cho máy tính của người dùng.
- Quá trình phân giải DNS bao gồm chuyển đổi tên máy chủ (chẳng hạn như www.example.com) thành địa chỉ IP thân thiện với máy tính (chẳng hạn như 192.168.1.1). Một địa chỉ IP được cung cấp cho mỗi thiết bị trên Internet và địa chỉ đó là cần thiết để tìm thiết bị Internet phù hợp. Giống như một địa chỉ đường phố được sử dụng để tìm một ngôi nhà cụ thể.
- Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ (example.com) và địa chỉ thân thiện với máy cần thiết để định vị trang web example.com.
- Nếu máy chủ DNS cục bộ không có địa chỉ IP của website, nó sẽ hỏi máy chủ DNS gốc. Máy chủ DNS gốc sẽ trả về địa chỉ IP của máy chủ DNS cấp cao nhất cho website.
- Máy chủ DNS cấp cao nhất sẽ trả về địa chỉ IP của máy chủ DNS quản lý website. Máy chủ DNS quản lý sẽ trả về địa chỉ IP của trang web cho máy chủ DNS cục bộ.
- Cuối cùng, máy chủ DNS cục bộ sẽ trả về địa chỉ IP của trang web cho máy tính của người dùng. Máy tính của người dùng sẽ sử dụng địa chỉ IP này để kết nối với website.

  # Các loại DNS bản ghi DNS thường sử dụng
  Hiện nay, DNS có bảy loại bản ghi, bao gồm:

- CNAME Record: Là một bản ghi tên quy chuẩn (Canonical Name Record). Đây là một dạng bản ghi tài nguyên trong hệ thống tên miền.
- A Record: Dùng để trỏ tên miền website tới một địa chỉ IP cụ thể. Đây được xem là bản ghi DNS đơn giản nhất.
- MX Record: Bản ghi này bạn có thể sử dụng để trỏ tên miền đến mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.
- AAAA Record: Dùng để trỏ tên miền đến địa chỉ IPv6 và cho phép thêm host mới, TTL và IPv6.
- TXT Record: Ngoài ra, có thể thêm giá trị TXT, Host mới, TTL và Point To để chứa các thông tin định dạng văn bản domain.
- SRV Record: Đây là bản ghi DNS đặc biệt, dùng để xác định chính xác dịch vụ nào đang chạy Port nào. Và thông qua bản ghi này bạn có thể thêm Priority, Port, Weight, TTL, Point to Point.
- NS Record: Bản ghi này có thể chỉ định Name Server cho từng tên miền phụ và bên cạnh đó có thể tạo tên Name Server, TTL hay host mới.

  # Các loại DNS Server
DNS Server gồm hai loại là Root Name Server và Local Name Server.
 ## Root Name Server
 Root Name Server là một dịch vụ phân giải tên miền gốc và trên thế giới có khoảng 12 DNS root Server.

DNS root Server quản lý tất cả các tên miền Top-level. Khi có yêu cầu phân giải một Domain Name thành một địa chỉ IP, client sẽ gửi yêu cầu đến DNS gần nhất (DNS ISP). DNS ISP sẽ kết nối tới DNS root Server để hỏi địa chỉ của Domain Name.

DNS root Server sẽ căn cứ và dựa vào các Top Level của tên miền và từ đó có những tài liệu hướng dẫn phù hợp để chuyển hướng cho khách hàng đến đúng địa chỉ cần truy vấn.

## Local Name Server
DNS Server này dùng để chứa thông tin để truy xuất và tìm kiếm máy chủ tên miền. Và thường được duy trì và phát triển bởi các doanh nghiệp hay các nhà cung cấp dịch vụ Internet.
## DNS Recursor
DNS Recursor là một máy chủ có nhiệm vụ chuyển đổi tên miền thành địa chỉ IP. Được hoạt động như một thư viện, lưu trữ thông tin về địa chỉ IP của các trang web và ứng dụng. Khi người dùng nhập một tên miền, DNS Recursor sẽ tìm kiếm thông tin đó trong cơ sở dữ liệu của mình. Nếu không tìm thấy, nó sẽ liên hệ với các DNS Recursor khác để tìm kiếm. DNS Recursor cũng sử dụng bộ nhớ đệm để lưu trữ thông tin về các tên miền mà nó đã từng truy cập. Điều này giúp tăng tốc độ phản hồi cho các truy vấn trong tương lai.
## TLD Name Server
TLD Name Server là máy chủ tên miền cấp cao nhất, chịu trách nhiệm lưu trữ thông tin về các tên miền có phần mở rộng chung (gTLD), chẳng hạn như .com, .org, .net. Trong quá trình tìm kiếm địa chỉ IP, máy chủ định danh sẽ liên hệ với TLD Name Server để lấy thông tin về tên miền.
## Authoritative Name Server
Authoritative Name Server lưu trữ thông tin về tên miền và địa chỉ IP tương ứng. Là điểm cuối của quá trình truy vấn và phân giải địa chỉ IP cần thiết cho DNS Recursor.

# Cách sử dụng DNS
Nếu bạn sử dụng DNS của nhà cung cấp mạng thì bạn sẽ không cần điền địa chỉ DNS. Nhưng nếu trường hợp bạn sử dụng DNS khác, thì bạn phải điền địa chỉ cụ thể của máy chủ đó để thay đổi DNS Server:

Bước 1: Nhấn vào Start Menu > Gõ Control Panel > Chọn Control Panel.

Bước 2: Truy cập vào View network status and task.

Bước 3: Truy cập vào mạng Internet đang sử dụng.

Bước 4: Vào phần Properties để bắt đầu thay đổi DNS máy tính.

Bước 5: Chọn vào Internet Protocol Version 4.

Bước 6: Chọn Use the following DNS server addresses > Đổi DNS nhấn OK để hoàn tất các bước thiết lập.

# Khác biệt giữa Public DNS và Private DNS
| Đặc điểm          | Private DNS                          | Public DNS                          |
|--------------------|--------------------------------------|-------------------------------------|
| **Phạm vi**        | Mạng nội bộ (LAN)                   | Internet                            |
| **Bảo mật**        | 🔒 Cao (có tường lửa bảo vệ)        | 🔓 Thấp hơn (tiếp xúc Internet)     |
| **Truy cập**       | Chỉ thiết bị trong mạng nội bộ       | Mọi người từ Internet               |
| **IP**             | IP nội bộ (192.168.x.x, 10.x.x.x...) | IP công cộng (public IP)            |
| **Mục đích**       | Nhận dạng máy chủ/dịch vụ nội bộ     | Truy cập dịch vụ từ Internet        |
| **Ví dụ**          | Active Directory Domain Services     | Google DNS (8.8.8.8), Cloudflare    |
| **Ưu điểm**        | - Tăng bảo mật<br>- Quản lý tập trung | - Dễ truy cập<br>- Phục vụ đối tượng rộng |
| **Nhược điểm**     | - Chỉ dùng nội bộ<br>- Cần cấu hình  | - Rủi ro tấn công<br>- Lộ thông tin |
| **Ứng dụng**       | Doanh nghiệp, tổ chức, trường học    | Web server, Mail server, CDN...     |

# Tìm hiểu về rò rỉ DNS
Khi bạn kết nối với Internet, có hai loại lưu lượng truy cập chính: Lưu lượng truy cập HTTP và lưu lượng truy cập DNS. Lưu lượng truy cập HTTP là lưu lượng truy cập được sử dụng để tải nội dung từ trang web, chẳng hạn như văn bản, hình ảnh và video. Lưu lượng truy cập DNS là lưu lượng truy cập được sử dụng để tìm địa chỉ IP của trang web mà bạn đang cố gắng truy cập.
Khi bạn sử dụng VPN, lưu lượng truy cập HTTP của bạn sẽ được mã hóa và định tuyến qua máy chủ VPN. Điều này giúp bảo vệ quyền riêng tư của bạn và ngăn ISP của bạn theo dõi hoạt động duyệt web của bạn. Tuy nhiên, nếu lưu lượng truy cập DNS của bạn không được định tuyến qua máy chủ VPN, thì ISP của bạn vẫn có thể thấy các trang web bạn đang truy cập.

## Tại sao lại xảy ra lỗi rò rỉ DNS?

Nguyên nhân chính của lỗi rò rỉ DNS là do cấu hình VPN không chính xác. Lỗi này có thể xảy ra trên bất kỳ hệ điều hành hoặc thiết bị nào kết nối với VPN.

Khi VPN được cấu hình chính xác, máy tính sẽ sử dụng DNS của VPN để truy vấn địa chỉ IP của các trang web. Điều này đảm bảo rằng lưu lượng DNS được mã hóa và ISP không thể theo dõi hoạt động trực tuyến của người dùng.

Tuy nhiên, nếu VPN được cấu hình không chính xác, lưu lượng DNS có thể thoát khỏi đường hầm VPN và được gửi đến các máy chủ DNS của ISP. Điều này khiến cho ISP có thể thấy được các trang web mà người dùng đang truy cập.

# Cách kiểm tra và khắc phục lỗi rò rỉ DNS
Kiểm tra rò rỉ DNS từ trình duyệt

Các dịch vụ VPN hiện nay thường cung cấp các công cụ riêng để giúp người dùng kiểm tra lỗi rò rỉ DNS. DNSleaktest.com là công cụ được đánh giá tốt nhất hiện nay. Công cụ này có cách sử dụng đơn giản, chỉ cần thực hiện một bài kiểm tra để biết các yêu cầu DNS có bị lộ ra ngoài hay không. Kết quả kiểm tra sẽ liệt kê tất cả các máy chủ, địa chỉ IP và chủ sở hữu mà công cụ nhìn thấy gửi đến người dùng.

Kiểm tra rò rỉ DNS bằng Torrent

So với việc truy cập thông tin lưu lượng bình thường, việc phát hiện rò rỉ DNS khi sử dụng Torrent yêu cầu phải dùng đến các phần mềm đặc biệt. Đa số người dùng thường sử dụng pMagnet như một giải pháp được đề xuất để kiểm tra địa chỉ IP của Torrent. Bằng cách sử dụng liên kết Magnet thông qua phần mềm này, người dùng có thể nhanh chóng biết được IP nào mà Torrent Client đang sử dụng.

# Các bước trong tra cứu DNS là gì?
Trong hầu hết các tình huống, DNS liên quan đến một tên miền được phân giải sang địa chỉ IP thích hợp. Để tìm hiểu cách thức hoạt động của quy trình này. Nó giúp theo dõi quá trình tra cứu DNS khi nó di chuyển từ trình duyệt web. Thông qua quy trình tra cứu DNS và quay lại. Chúng ta hãy xem các bước.
Bước 1: Truy vấn (Query)
Khi bạn nhập tên miền vào trình duyệt web, trình duyệt sẽ gửi một truy vấn DNS đến máy chủ DNS được cấu hình trong cài đặt mạng của bạn hoặc được cung cấp tự động bởi nhà cung cấp dịch vụ internet (ISP). Truy vấn này bao gồm tên miền bạn muốn truy cập.


Bước 2: Caching
Trước khi gửi truy vấn DNS đến máy chủ DNS, trình duyệt sẽ kiểm tra bộ nhớ cache DNS để xem nó có lưu trữ bản ghi DNS cho tên miền đó hay không. Bộ nhớ cache DNS là nơi lưu trữ tạm thời các bản ghi DNS đã được tra cứu trước đây để tăng tốc độ truy vấn DNS.

Nếu bộ nhớ cache DNS có chứa bản ghi DNS cho tên miền: Trình duyệt sẽ sử dụng bản ghi đó để truy cập website mà không cần gửi truy vấn DNS đến máy chủ DNS.
Nếu bộ nhớ cache DNS không có bản ghi DNS cho tên miền: Trình duyệt sẽ gửi truy vấn DNS đến máy chủ DNS.
Bước 3: Máy chủ DNS chính (DNS root server)
Truy vấn DNS đầu tiên được gửi đến máy chủ DNS chính (DNS root server). Máy chủ DNS chính lưu trữ thông tin về máy chủ DNS cấp cao nhất (TLD) cho tên miền được truy vấn.

Bước 4: Truy cấn đến máy chủ DNS cấp cao hơn (Top-level Domain server)
Tiếp theo, trình duyệt sẽ gửi truy vấn DNS đến máy chủ DNS cấp cao nhất (TLD server) cho tên miền được truy vấn. Máy chủ DNS cấp cao nhất lưu trữ thông tin về máy chủ DNS cụ thể (authoritative DNS server) cho tên miền.

Bước 5: Truy vấn Máy chủ DNS cụ thể (Authoritative DNS server)
Cuối cùng, trình duyệt sẽ gửi truy vấn DNS đến máy chủ DNS cụ thể (authoritative DNS server) cho tên miền được truy vấn. Máy chủ DNS cụ thể lưu trữ bản ghi DNS chính thức cho tên miền, bao gồm địa chỉ IP của website.


Bước 6: Truy vấn và phản hồi
Khi máy chủ DNS cụ thể nhận được truy vấn DNS, nó sẽ tra cứu bản ghi DNS cho tên miền được truy vấn trong cơ sở dữ liệu của mình. Nếu tìm thấy bản ghi DNS, máy chủ DNS cụ thể sẽ gửi phản hồi DNS cho trình duyệt, bao gồm địa chỉ IP của website.

# Các loại truy vấn DNS

Trong một truy vấn DNS thông thường, ba loại truy vấn xảy ra. Bằng cách sử dụng kết hợp các truy vấn này. Một quy trình được tối ưu hóa cho quá trình phân giải DNS có thể giúp giảm khoảng cách di chuyển. Trong một tình huống lý tưởng, dữ liệu bản ghi được lưu trong bộ nhớ cache sẽ khả dụng, cho phép máy chủ định danh DNS trả về truy vấn không đệ quy.
3 loại truy vấn DNS

Recursive query: DNS client yêu cầu máy chủ DNS (thường là recursive DNS resolver). Sẽ trả lời máy khách bằng bản ghi tài nguyên được yêu cầu. Hoặc thông báo lỗi nếu resolver không thể tìm thấy bản ghi.
Iterative query: Trong tình huống này, DNS client sẽ cho phép máy chủ DNS trả về câu trả lời tốt nhất có thể. Nếu máy chủ DNS được truy vấn không có kết quả trùng khớp với tên truy vấn. Nó sẽ trả về một giới thiệu đến máy chủ DNS có thẩm quyền cho mức thấp hơn. DNS client sau đó sẽ thực hiện một truy vấn đến địa chỉ được giới thiệu. Quá trình này tiếp tục với các máy chủ DNS bổ sung trong chuỗi truy vấn cho đến khi xảy ra lỗi hoặc hết thời gian.
Non-recursive query: Thông thường điều này sẽ xảy ra khi DNS resolver client truy vấn máy chủ DNS một record mà server có quyền truy cập hoặc bản ghi tồn tại bên trong bộ đệm của server. Thông thường, một máy chủ DNS sẽ lưu các bản ghi DNS để ngăn chặn việc tiêu thụ thêm băng thông và giảm tải cho các máy chủ DNS khác.
Trình duyệt sẽ sử dụng địa chỉ IP này để kết nối đến máy chủ lưu trữ website và hiển thị nội dung cho bạn.

Quá trình này diễn ra rất nhanh chóng, chỉ trong vài mili giây. Nhờ có DNS, bạn không cần phải nhớ địa chỉ IP phức tạp của website mà chỉ cần sử dụng tên miền dễ nhớ.

# Cách DNS Server giải quyết một DNS query?
Điển hình, trong một DNS query mà không có caching, có bốn server hoạt động cùng nhau để cung cấp địa chỉ IP cho client: Recursive Resolvers, Root Nameservers, TLD nameservers, và Authoritative Nameservers.

DNS recursor (còn được gọi là DNS resolver) là một máy chủ nhận truy vấn từ DNS client, sau đó tương tác với các DNS server khác để truy tìm IP chính xác. Khi resolver nhận được yêu cầu từ client, resolver sau đó thực sự hoạt động như một client, truy vấn ba loại DNS server khác để tìm kiếm đúng IP.

DNS Lookup
Đầu tiên, resolver truy vấn root nameservers. Root-server là bước đầu tiên trong việc phân giải các tên miền có thể đọc được thành địa chỉ IP. Sau đó, root server sẽ phản hồi lại resolver bằng địa chỉ của Top Level Domain (TLD) DNS server (chẳng hạn như .com hoặc .net) lưu trữ thông tin cho các miền của nó.

Tiếp theo, resolver truy vấn TLD server. TLD server phản hồi bằng địa chỉ IP Authoritative Nameserver của tên miền. Sau đó, recursor sẽ truy vấn authoritative nameserver. Sau đó máy chủ này sẽ respond bằng địa chỉ IP của origin server.

Resolver cuối cùng sẽ chuyển địa chỉ IP của origin server trở lại client. Sử dụng địa chỉ IP này, client sau đó có thể bắt đầu truy vấn trực tiếp đến origin server. Và origin server sẽ phản hồi bằng cách gửi dữ liệu trang web cho trình duyệt web để hiển thị.

DNS Caching
Ngoài quy trình được nêu ở trên, recursive resolver cũng có thể giải quyết các truy vấn DNS. Bằng cách sử dụng dữ liệu được lưu trong bộ nhớ cache. Sau khi truy xuất địa chỉ IP chính xác cho một trang web nhất định. Resolver sẽ lưu trữ thông tin đó trong bộ nhớ cache của nó trong một khoảng thời gian giới hạn. Trong khoảng thời gian này, nếu bất kỳ máy khách nào khác gửi yêu cầu cho tên miền đó, resolver có thể bỏ qua quy trình tra cứu DNS thông thường và chỉ cần trả lời client bằng địa chỉ IP được lưu trong bộ nhớ cache.

Khi thời gian lưu vào bộ nhớ đệm hết hạn, resolver phải truy xuất lại địa chỉ IP, tạo entry mới trong bộ nhớ cache của nó. Giới hạn thời gian này, được gọi là thời gian tồn tại (TTL) được đặt trong DNS Record cho mỗi trang web. Thông thường, thì TTL nằm trong khoảng 24-48 giờ. TTL là cần thiết vì máy chủ web đôi khi thay đổi địa chỉ IP của chúng. Do đó, các resolver không thể phân phát cùng một IP từ bộ nhớ cache vô thời hạn.

# DNS Server bị lỗi thì điều gì sẽ xảy ra?
DNS Server có thể bị lỗi vì nhiều lý do, chẳng hạn như mất điện, tấn công mạng và trục trặc phần cứng. Những ngày đầu của Internet, sự cố ngừng hoạt động của DNS Server có thể có tác động rất lớn. Tuy nhiên, ngày nay có rất nhiều dự phòng được tích hợp vào DNS.
Trong trường hợp DNS server chính bị ngừng hoạt động, một số người dùng có thể gặp phải sự chậm trễ do lượng yêu cầu được xử lý bởi các server dự phòng. Nhưng sẽ mất một lượng lớn DNS khiến một phần đáng kể Internet không khả dụng. (Điều này thực sự xảy ra vào năm 2016 khi nhà cung cấp DNS Dyn trải qua một trong những cuộc tấn công DDoS lớn nhất trong lịch sử).

# Nguyên nhân DNS dễ bị tấn công?
Vì hệ thống tên miền khá phức tạp và người tấn công có thể tận dụng điểm yếu trong DNS để tấn công với nhiều phương thức khác nhau. Đa số các cuộc tấn công đều tập trung vào việc lạm dụng DNS để ngăn người dùng không thể truy cập vào Internet.
Bên cạnh đó, DNS cũng có thể bị tấn công bằng phướng pháp tận dụng giao thức DNS để chuyển hướng người dùng truy cập vào các trang web độc hại nhằm đánh cắp dữ liệu nhạy cảm của cá nhân, doanh nghiệp.

Ngoài ra, việc sử dụng server đệ quy sẽ lưu phản hồi vào bộ nhớ tạm để tăng tốc độ của các truy vấn tiếp theo. Nhằm giảm số lượng request thông tin, nhưng khá nguy hiểm và dễ bị tấn công bởi Man-In-The-Middle. Những kẻ tấn công có thể truy cập vào Over IP (VoIP) để đánh cắp thông tin, mạo danh, trích xuất dữ liệu, thông tin,…

