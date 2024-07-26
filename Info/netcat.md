# netcat
Netcat（通常簡稱為 nc）是一個功能強大的網絡工具，用於讀寫網絡連接。它可以用於多種用途，包括端口掃描、文件傳輸和簡單的聊天伺服器。
## 基本語法

### 建立 TCP 連接
- 作為客戶端連接到伺服器
```bash
# 語法
nc <hostname> <port>

# 範例
nc localhost 80
```

- 作為伺服器接收連接
```bash
# 語法
nc -l <port>

# 範例
nc -l 12345
```

### 文件傳輸
- 在伺服器上接收文件
```bash
# 語法
nc -l 12345 > received_file.txt
```

- 在客戶端發送文件
```bash
nc <server_ip> 12345 < file_to_send.txt
```


### 端口掃描
使用 Netcat 掃描開放端口
- 掃描單個端口
```bash
# 語法
nc -zv <hostname> <port>

# 範例
nc -zv localhost 80
```

- 掃描一範圍的端口
```bash
# 語法
nc -zv <hostname> <start_port>-<end_port>

# 範例
# 掃描本地機器的端口 20 到 25
nc -zv localhost 20-25
```
