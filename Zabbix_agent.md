* Zabbix agent

Zabbix agent, được phát triển bằng ngôn ngữ C, có thể chạy trên nhiều nền tảng được hỗ trợ khác nhau , bao gồm Linux, UNIX và Windows và thu thập dữ liệu như CPU, bộ nhớ, disk và network interface sử dụng từ thiết bị.

<img src="/img/3.png">

Do footprint nhỏ, agent có thể chạy trên các thiết bị có tài nguyên hạn chế.

Các cấu hình giám sát được tập trung trong Zabbix server, giúp quản lý Zabbix agent dễ dàng hơn, có thể sử dụng một tệp cấu hình duy nhất trên tất cả các máy chủ.

Zabbix agent chạy trên linux:

<img src="/img/4.png">

Zabbix agent chạy trên Windows:

<img src="/img/5.png">

* Polling và trapping

Zabbix agent hỗ trợ cả 2 dạng  passive (polling) và active checks (trapping). Zabbix có thể thực hiện kiểm tra dựa trên một khoảng thời gian, tuy nhiên, nó cũng có thể lên lịch thời gian cụ thể cho item polling.

<img src="/img/6.png">

Passive checks (polling):

Zabbix server(hoặc proxy) yêu cầu một giá trị từ Zabbix agent.

Agent xử lý yêu cầu và trả về giá trị cho Zabbix server(hoặc proxy).

Active checks (trapping):

Zabbix agent yêu cầu từ Zabbix server(hoặc proxy) một danh sách kiểm tra hoạt động.

Agent gửi kết quả theo định kỳ.

### Agent functions

Danh sách kiểm tra sau đây được Zabbix agent hỗ trợ.

|Name              |Function             |
|------------------|---------------------|
|Network|Packets/bytes transfered|
|		| Errors/dropped packets|
|		| Collisions|
|CPU|Load average|
|		|CPU idle/usage|
|		|CPU utilization data per individual process|
|Disk|Space free/used|
|		|Read and write I/O|
|Service|Process status|
|		|Process memory usage|
|		|Service status (ssh, ntp, ldap, smtp, ftp, http, pop, nntp, imap)|
|		|Windows service status|
|		|DNS resolution|
|		|TCP connectivity|
|		|TCP response time|	
|File|File size/time|
||File exists|
||Checksum|
||MD5 hash|
||RegExp search|	
|Log|Text log|
||Windows eventlog|
|Other|System uptime|
||System time|
||Users connected|
||Performance counter (Windows)|	

Xem thêm list support tại đây: https://www.zabbix.com/documentation/3.0/manual/config/items/itemtypes/zabbix_agent

### Extending Zabbix agent

Chức năng mở rộng zabbix agent có thể được mở rộng bằng phương pháp:

* loadable modules

* user parameters

* Zabbix sender 

### Log monitoring

Hỗ trợ cho việc theo dõi các text log và Windows Event Log là một hàm gốc của Zabbix agent, bao gồm hỗ trợ xoay vòng.

Có thể vẽ đồ thị dữ liệu từ các log item, khi các khả năng trích xuất nội dung cụ thể được sử dụng.

Các log được phân tích liên tục bởi Zabbix agent và khi tìm thấy mục tìm kiếm đã xác định, Zabbix server được thông báo và thậm chí có thể thực hiện một số hành động hoặc tự động gửi thông báo tới người dùng hoặc nhóm.

### WMI support

Zabbix agent hỗ trợ tính năng Windows Management Instrumentation (WMI), nâng cao khả năng dễ dàng thu thập và giám sát các thông tin hệ thống thời gian thực và các chỉ số hiệu suất từ ​​ Windows servers và workstations.

Các truy vấn WMI có thể được thực hiện bằng khóa wmi.get [] để lấy ra một chuỗi ký tự, số nguyên hoặc thuộc tính dấu chấm động từ lớp không gian tên WMI được chỉ định.

Để biết thêm thông tin về Windows Management Instrumentation, các lớp có sẵn và các thuộc tính của chúng sẽ thấy tài liệu MSDN(http://msdn.microsoft.com/en-us/library/aa394582(v=vs.85).aspx).

Zabbix agent supports IPv4 and IPv6 addresses.








































































