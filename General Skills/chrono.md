# Description
```text
How to automate tasks to run at intervals on linux servers?
Additional details will be available after launching your challenge instance.
```
start instance
```text
How to automate tasks to run at intervals on linux servers? Use ssh to connect to this server:

Server: saturn.picoctf.net
Port: 49447
Username: picoplayer 
Password: ENAFb6zfzn
```

# 解題
先使用 `ssh` 連線
```bash
ssh picoplayer@saturn.picoctf.net -p 49447
```
輸入密碼後，根據題目得知與 `crontab` 有關，嘗試各種 crontab 指令後發現沒有權限，然後 crontab 的設定檔會位於 `/etc/crontab`，所以使用 `cat` 輸出設定檔內容，即可拿到 flag
```bash
picoplayer@challenge:/$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}
```



<!-- flag -->
所以本題 FLAG 
```text
picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}
```
