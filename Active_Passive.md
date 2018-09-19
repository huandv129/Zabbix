### Zabbix Passive Check

Đây là kiểu kiểm tra tương ứng với Item Zabbix Passive (bị động), kiểu này có đặc tính là công việc yêu cầu thông tin cần giám sát thuộc về Zabbix Server.

Zabbix Server sẽ request thông tin cần tìm kiếm đến các Agent theo các khoảng thời gian (interval time) đã được cấu hình trong item tương ứng, lấy thông tin monitor và báo cáo lại về hệ thống ngay lập tức. Server khởi tạo kết nối, Agent luôn ở chế động lắng nghe kết nối từ Server

Zabbix item
<img src="/img/19.png">

1.	Kiểu Item (Zabbix agent = Zabbix Passive Item)

2.	Key tương ứng với kiểu Passive

<img src="/img/20.png">

###  Zabbix Active Check

Đây là kiểu kiểm tra tương ứng với Item Active (chủ động), đặc tính của kiểu này là công việc chủ động request thông tin cần giám sát thuộc về Zabbix Agent. Kiểu kiểm tra này hay dùng khi Zabbix Server không thể kết nối trực tiếp đến Zabbix Agent (có thể do chính sách firewall).

Zabbix Agent sẽ chủ động gửi request đến Zabbix Server nhằm lấy thông tin về các item được Server chỉ định sẵn. Sau khi lấy được danh sách item thì Agent sẽ xử lý động lập rồi gửi tuần tự thông tin về cho Server. Server sẽ không khởi tạo kết nối nào mà chỉ trả lời request item list và nhận lại thông tin được trả về. Tuy nhiên nếu Agent chết thì Server sẽ không nhận được bất kỳ kết nối nào.

Sơ đồ Zabbix item (active)
<img src="/img/21.png">

<img src="/img/22.png">

1.	Zabbix agent (active) = Zabbix Active Item

2.	Key tương ứng với kiểu Active










