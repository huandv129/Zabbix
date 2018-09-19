### Tổng quan Zabbix

<img src="/img/29.jpg">

Theo dõi bất kỳ số liệu hiệu suất và sự cố nào có thể xảy ra trong mạng của bạn:


|Network performance|Network health|Configuration changes|
|---------------------|--------------------|-------------------|
|Bandwith sử dụng|Link is down|Thêm, xóa thiết bị|
|Tỉ lệ mất package|Trạng thái của hệ thống cảnh báo warning/critical state|Module mạng được thêm, xóa hoặc thay thế|
|Interface errorrate|Nhiệt độ thiết bị quá cao/quá thấp|Firmware đã được nâng cấp|
|High CPU or memory utilization|Nguồn điện ở trạng thái quan trọng|Số serial của thiết bị đã thay đổi|
|Số lượng kết nối tcp cao bất thường cho ngày trong tuần|Dung lượng đĩa trống thấp|Giao diện đã thay đổi thành tốc độ thấp hơn hoặc chế độ bán song công|
|Thông lượng tổng hợp của các bộ định tuyến lõi thấp|Không thu thập dữ liệu SNMP||

Đây là danh sách mẫu các chỉ số và sự cố liên quan đến mạng, được giám sát bởi Zabbix. Xem danh sách đầy đủ trong các mô tả mẫu. Bạn có thể mở rộng / tùy chỉnh phạm vi của đối tượng được giám sát bằng cách thêm các mục mới, viết kịch bản thu thập dữ liệu tùy chỉnh, tạo mẫu tùy chỉnh, v.v.

<img src="/img/7.jpg">

### Các tính năng và lợi ích khi lựa chọn Zabbix

* Các phương thức và giao thức thu thập số liệu khác nhau:

+ SNMP , IPMI

+ Active / Passive chế độ

+ Hỗ trợ IPv6

### Tự động tìm kiếm và phát hiện

+ Tự động phát hiện thiết bị mạng .

+ Tự động thay đổi cấu hình thiết bị .

### Định nghĩa sự cố linh hoạt

+ Tạo các biểu thức logic phức tạp liên quan đến số liệu thống kê được giám sát của các thiết bị mạng

+ Tránh false positives bằng cách xác định trễ

### Sự cố phụ thuộc

+ Xác định phụ thuộc nhiều cấp giữa các nút mạng có liên quan. Phát hiện lỗi nguyên nhân gốc.

### Thông báo linh hoạt

+ Nhiều phương thức cảnh báo: email, sms, jabber, tập lệnh tùy chỉnh hoặc messenger

+ Tùy chỉnh nội dung tin nhắn dựa trên lịch sử người nhận và báo cáo leo thang

### Sự tương quan sự kiện

+ Giảm nhiễu thông báo với sự tương quan sự kiện

### Tích hợp với phần mềm của bên thứ 3

+ Helpdesks, ticketing systems (tích hợp 2 chiều)

+ Hệ thống quản lý cấu hình

+ Messengers, ứng dụng di động

+ Hệ thống kiểm kê

### Khả năng mở rộng không giới hạn

+ Quy mô bằng cách tải xuống máy chủ Zabbix bằng proxy Zabbix

+ Zabbix không có giới hạn hoặc hạn chế ẩn. Dù kích thước mạng là bao nhiêu.

### Tính sẵn sàng cao

+ Sử dụng proxy Zabbix để thu thập dữ liệu giám sát trong trường hợp xảy ra sự cố mạng

+ Xây dựng giải pháp giám sát sử dụng các thành phần Zabbix. 

### Thu thập dữ liệu linh hoạt và có thể mở rộng

+ Chỉ số được tính và tổng hợp . Ví dụ: tổng lưu lượng giữa hai cổng trên một switch mạng.

+ Preprocess thu thập dữ liệu. Ví dụ: sử dụng regexp để trích xuất một số chỉ số cụ thể từ thiết bị cũ. 

### Templating

+ Bắt đầu theo dõi tất cả các số liệu ngay lập tức bằng cách sử dụng các out-of-the-box templates.

+ Sao chép và cập nhật hàng loạt các thiết bị mạng tương tự bằng cách sử dụng các templates cấu hình thiết bị.














