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
|------------------|---------------------|
|CPU|Load average|
|		|CPU idle/usage|
|		|CPU utilization data per individual process|



















































































