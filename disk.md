- Node nhanh về cách discovery disk 

#### Thực hiện cài trên zabbix-agent

- Sử dụng chương trình python của mình để list ra các tên disk

```sh
vim /usr/local/bin/discover_disk.py

#!/usr/bin/python
import os
import json

if __name__ == "__main__":
    skippable = ("sr", "loop", "ram")
    devices = (device for device in os.listdir("/sys/class/block")
               if not any(ignore in device for ignore in skippable))
    data = [{"{#DISK}": device} for device in devices]
    print(json.dumps({"data": data}, indent=4))
```

- Cấp quyền: 

```chmod +x /usr/local/bin/discover_disk.py```

- Thêm Parameter vào file zabbix-agent.conf 

```sh
tail -1 /etc/zabbix/zabbix_agentd.conf

UserParameter=custom.disks.discovery_python,/usr/local/bin/discover_disk.py
```

- Khởi động lại zabbix-agent 

```systemctl restart zabbix-agent```

#### Thực hiện trên dashbroad 



