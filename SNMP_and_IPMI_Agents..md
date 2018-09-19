### Các phương pháp thu thập dữ liệu

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


### Tự động tìm kiếm 

Giám sát các môi trường lớn có thể là một cơn ác mộng mà không cần tự động hóa. Zabbix cung cấp một số cách tự động hóa việc quản lý các môi trường như vậy. Các thiết bị và phần tử của thiết bị, chẳng hạn như hệ thống tệp và giao diện mạng, có thể được thêm và xóa tự động khi chúng đến và rời khỏi một tổ chức.

Có 3 phương pháp chính để phát hiện và quản lý tự động các yếu tố môi trường trong Zabbix: phát hiện mạng, khám phá cấp thấp và đăng ký tự động agent, mỗi trường phục vụ trường riêng của mình.


### Network discovery

Chức năng này cho phép định kỳ quét network cho các dịch vụ bên ngoài hoặc các tác nhân Zabbix (passive) và thực hiện các hành động được xác định trước khi phát hiện ra chúng.

<img src="/img/8.png">

Quá trình disovery bắt đầu với các quy tắc phát hiện mạng đang chạy , dựa trên các thông tin sau:

* Phạm vi IP cần quét;

* Dịch vụ bên ngoài nào cần tìm (FTP, SSH, WEB, POP3, IMAP, TCP, v.v.);

* Thông tin nhận được từ một đại lý Zabbix;

* Thông tin nhận được từ một đại lý SNMP.

Hàm khám phá sau đó sẽ tạo ra một sự kiện khám phá, có thể là cơ sở cho một hành động có liên quan, được xác định trước, chẳng hạn như:

* Gửi thông báo cho người dùng;

* Thêm hoặc xóa máy chủ;

* Bật và tắt máy chủ;

* Thêm hoặc xóa máy chủ lưu trữ vào một nhóm;

* Liên kết hoặc hủy liên kết máy chủ với mẫu;

* Thực thi tập lệnh từ xa.

Các hành động có thể được cấu hình để tính đến loại thiết bị, IP, trạng thái, thời gian hoạt động / thời gian ngừng hoạt động và các thông số khác.

Low-level discovery (LLD)

Low-level thu thập tự động, tạo items, triggers và biểu đồ cho các thành phần khác nhau trên thiết bị.

<img src="/img/10.jpg">

|Zabbix supports|
|---------------|
|Discovery of file systems.|
|Discovery of network interfaces.|
|Discovery of CPUs and CPU cores.|
|Discovery of multiple SNMP OIDs.|
|Discovery using SQL queries.|
|Discovery of Windows Services.|

Hơn nữa, người dùng có thể tạo các quy tắc tìm hiểu cấp thấp tùy chỉnh hoàn toàn, khám phá bất kỳ loại thực thể nào - ví dụ, các cơ sở dữ liệu trên một máy chủ cơ sở dữ liệu.

### Auto-registration of active agent

Chức năng này cho phép Zabbix server tự động bắt đầu theo dõi thiết bị mới nếu thiết bị này có một Zabbix agent (active) được cài đặt. Điều này cho phép thêm các máy chủ mới để giám sát mà không cần bất kỳ cấu hình máy chủ Zabbix thủ công nào cho server host. Khi thêm một máy chủ mới vào môi trường được giám sát, chỉ cần cài đặt một Zabbix agent(active) và trỏ nó đến một Zabbix server.

<img src="/img/11.jpg">

Chức năng đăng ký tự động rất tiện dụng để theo dõi tự động các node cloud. Ngay khi bạn có một node mới trong cloud, Zabbix sẽ tự động bắt đầu thu thập dữ liệu hiệu suất và tính khả dụng của nodes đó.

### Phát hiện sự cố

Ngay sau khi dữ liệu được thu thập, sử dụng các phương pháp khác nhau có sẵn trong Zabbix, quá trình đánh giá dữ liệu thu thập được bắt đầu. Các quy tắc đánh giá dữ liệu hoặc biểu thức kích hoạt , về mặt Zabbix, cung cấp các định nghĩa logic của trạng thái vấn đề cho dữ liệu nhận được từ các máy chủ được giám sát. Khi đạt đến ngưỡng kích hoạt, trình kích hoạt sẽ thay đổi trạng thái của nó từ OK thành PROBLEM và cũng quay lại khi dữ liệu ở dưới ngưỡng.

### Dự đoán

Mặc dù rất tốt khi có ngưỡng để phát hiện tình huống có vấn đề, nó thậm chí còn đẹp hơn để có thể dự đoán được các vấn đề. Đối với mục đích đó chức năng dự đoán có sẵn trong Zabbix. Zabbix phân tích xu hướng của dữ liệu đến và xây dựng dự báo về cách mọi thứ có khả năng xảy ra, mang lại cho người dùng khả năng chủ động.

Dự đoán thời gian
<img src="/img/12.png">
Dự báo khi chúng tôi đạt được một giá trị nhất định

Giá trị dự đoán
<img src="/img/14.png">
Dự báo giá trị số liệu sau một khoảng thời gian nhất định


### Định nghĩa ngưỡng cực kỳ linh hoạt

Zabbix cung cấp cho người dùng các tùy chọn định nghĩa ngưỡng rất linh hoạt, thông minh. Mặc dù ngưỡng cho trình kích hoạt có thể đơn giản như "lớn hơn x", có thể sử dụng tất cả các biểu thức logic, chẳng hạn như chia, nhân, không bằng nhau, logic AND và OR.

### Tham chiếu một hoặc nhiều mục hoặc máy chủ

Sử dụng nhiều mục khác nhau thu được từ các máy chủ khác nhau để tạo biểu thức trình kích hoạt. Điều này cho phép xây dựng các ngưỡng rất thông minh, phức tạp, trong đó giảm thiểu các kết quả dương tính giả và do đó cho phép các quản trị viên tập trung vào các vấn đề thực sự.

### Phân tích dữ liệu lịch sử

Kiểm tra trạng thái dữ liệu hiện tại so với trạng thái đã nhận được một số thời gian trước đây . Có thể so sánh các khoảng thời gian tương tự, giả sử Thứ Hai này với Thứ Hai trước hoặc chiều nay với 2 tuần trước. Điều này cực kỳ tiện dụng khi một tải về môi trường không đồng đều và so sánh sáng thứ Hai đến chiều thứ ba chỉ không tạo ra bất kỳ thông tin giá trị nào.

So sánh với định mức, trong đó tiêu chuẩn là trạng thái hệ thống trong quá khứ. Ví dụ: tải CPU trung bình cho giờ cuối cùng cao hơn gấp 2 lần tải CPU cho cùng một khoảng thời gian tuần trước.

Phát hiện dị thường
<img src="/img/15.png">


Phân tích dữ liệu lịch sử

Kiểm tra trạng thái dữ liệu hiện tại so với trạng thái đã nhận được một số thời gian trước đây . Có thể so sánh các khoảng thời gian tương tự, giả sử Thứ Hai này với Thứ Hai trước hoặc chiều nay với 2 tuần trước. Điều này cực kỳ tiện dụng khi một tải về môi trường không đồng đều và so sánh sáng thứ Hai đến chiều thứ ba chỉ không tạo ra bất kỳ thông tin giá trị nào.

### Hysteresis

Độ trễ là một chức năng tuyệt vời cho phép tránh bị văng, điều này có thể xảy ra khi dữ liệu đến dao động xung quanh một ngưỡng đơn giản. Độ trễ có giới hạn trên và dưới, đặt kích hoạt trong trạng thái vấn đề khi đạt đến giới hạn trên và trả về trigger ở trạng thái bình thường khi dữ liệu thu được nằm dưới ngưỡng.


<img src="/img/16.jpg">

### Phụ thuộc (Dependencies)

Trong bất kỳ môi trường CNTT nào cũng có rất nhiều phụ thuộc, khi sự thất bại trong một nút chịu trách nhiệm cho sự thất bại của hoạt động trong nhiều phần khác của môi trường. Phụ thuộc có thể phát triển đến đa cấp, khi thiếu không gian đĩa dẫn đến lỗi của hệ điều hành mà cơ sở dữ liệu đang chạy. Tại thời điểm này, người dùng CRM, CMS, BPMS và nhiều ứng dụng doanh nghiệp khác sẽ không thể thực hiện nhiệm vụ của mình. Một hệ thống giám sát không có phụ thuộc được cấu hình sẽ tạo ra hàng chục hoặc hàng trăm thông báo và gửi hàng trăm hoặc hàng ngàn e-mail thông báo về tất cả các hệ thống này đang hoạt động. Thay vào đó, việc sử dụng khôn ngoan chức năng phụ thuộc sẽ chỉ dẫn đến một thông báo thông báo về việc thiếu dung lượng đĩa, trong khi ẩn tất cả các thông báo khác.


<img src="/img/17.jpg">

### Mức độ nghiêm trọng

Xác định mức độ nghiêm trọng của trình kích hoạt dựa trên mức nhập. Vì không phải tất cả các trigger đều có cùng mức độ quan trọng, một trong sáu mức độ nghiêm trọng có thể được gán cho một trigger. Mức độ nghiêm trọng sau đó được áp dụng cho các đại diện trực quan của gây nên, và có thể được sử dụng để finetune phản ứng với các sự kiện vấn đề.

Mức độ nghiêm trọng được sử dụng cho:

Biểu diễn trực quan của trình kích hoạt

Âm thanh trong báo thức toàn cầu

Chọn kênh thông báo (mức độ nghiêm trọng cao - SMS, email khác)

<img src="/img/18.jpg">



























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
























