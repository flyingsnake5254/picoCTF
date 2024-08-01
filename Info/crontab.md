# crontab
用於在 Unix 和類 Unix 系統中定時執行任務的指令。cron 是系統上的一個守護進程，它定期檢查並執行用戶和系統定義的計劃任務，而 crontab 則是用來管理這些計劃任務的工具。


# crontab 的時間格式
```bash
* * * * * <command or file.sh to be executed>
- - - - -
| | | | |
| | | | +---- 星期幾 (0 - 7) (星期日=0或7)
| | | +------ 月份 (1 - 12)
| | +-------- 日期 (1 - 31)
| +---------- 小時 (0 - 23)
+------------ 分鐘 (0 - 59)
```
以下舉例說明
```bash
# 每天凌晨2:30執行 example.sh
30 2 * * * example.sh

# 每小時的第15分鐘執行 example.sh
15 * * * * example.sh

# 每週一和週三的早上8:00執行 example.sh
0 8 * * 1,3 example.sh

# 每月1號和15號的中午12:00執行 example.sh
0 12 1,15 * * example.sh

# 每隔5分鐘執行 example.sh
*/15 * * * * example.sh
```

# `-e` 編輯 crontab 文件
編輯當前用戶的 crontab 文件
```bash
crontab -e
```

# `-l` 列出當前用戶的 crontab 任務
```bash
crontab -l
```

# `-r` 刪除當前用戶的 crontab 任務
刪除當前用戶的所有定時任務
```bash
crontab -r
```

# 從文件載入 crontab
如果你有一個預先寫好的 crontab 文件，可以使用 `crontab filename` 將其載入
```bash
crontab <file-name>
```

# crontab 設定檔
### 用戶專用的 crontab 設定檔
- **Debian/Ubuntu 系統**
/var/spool/cron/crontabs/username
- **Red Hat/CentOS 系統**
/var/spool/cron/username

### 系統範圍的 crontab 設定檔
通常位於以下位置：
- **/etc/crontab**
這是系統範圍的 crontab 文件，它與用戶的 crontab 文件略有不同。除了常見的時間欄位外，它還包括一個用戶欄位，用來指定以哪個用戶身份執行任務。其格式如下：
```bash
# 分  小時  日期  月份  星期  用戶  命令
0 2 * * * root /usr/bin/backup.sh
```
- **/etc/cron.d/**
這個目錄包含了許多單獨的 crontab 文件，每個文件可以包含多個計劃任務。這些文件的格式與 /etc/crontab 一樣，也包含用戶欄位。例如：
```bash
# 在 /etc/cron.d/example 中
0 5 * * * root /usr/local/bin/daily_job.sh
```

### 系統範圍的目錄
此外，還有一些專用的目錄存儲了特定頻率執行的腳本：
- **/etc/cron.hourly/**
存放每小時執行的腳本。
- **/etc/cron.daily/**
存放每天執行的腳本。
- **/etc/cron.weekly/**
存放每週執行的腳本。
- **/etc/cron.monthly/**
存放每月執行的腳本。
