<img src="/img/3.png">
* SNMP support:

Zabbix server có thể thu thập dữ liệu từ các thiết bị với SNMP agent( version v1, v2, v3). SNMP không chỉ thống kê về network nó còn thống kê tất cả các thiết bị khác như máy in,NAS, UPS. Về cơ bản, tất cả các thiết bị mạng đều được giám sát qua SNMP agent.
	
Để cấu hình dễ dàng hơn, Zabbix hỗ trợ chuẩn SNMP MIB-2, cũng như thông tin cụ thể về MIB Enterprise MIB.

Bạn có thể thu thập dữ liệu bằng cách sử dụng chế độ SNMP polling hoặc nhận các bẫy SNMP thông qua trình tiện ích snmptrap daemon và công cụ zabbix_sender.
	
Ngoài ra, bạn có thể nhận sữ liệu SNMP với việc sử dụng dynamic indexes cung cấp khả năng giám sát linh hoạt và không có sự xuống cấp hiệu suất vì các truy vấn giải quyết được đưa lưu vào bộ nhớ cache.
	
* IPMI agent:

Để có được dữ liệu quan trọng từ phần cứng, Zabbix server hỗ trợ các IPMI agents, được trình bày theo mặc định trên các máy chủ kiến ​​trúc Intel như HP iLO và Dell DRAC.	
	
Các thông tin có sẵn IPMI agents về hardware:

+ Nhiệt độ của CPU và chasiss

+ Tốc độ quạt

+ Điện áp hệ thống

+ Trạng thái của đĩa vật lý

+ Trạng thái đèn LED bảo trì	
























