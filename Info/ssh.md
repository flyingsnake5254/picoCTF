# ssh
安全外殼協定（Secure Shell Protocol，簡稱SSH）是一種加密的網路傳輸協定，可在不安全的網路中為網路服務提供安全的傳輸環境。
## 基本使用

- 連接到遠程伺服器
```bash
# 語法
ssh <username>@<hostname>

# 範例
ssh user@example.com
```

- 指定端口
```bash
# 語法
ssh -p <port> <username>@<hostname>

# 範例
ssh -p 2222 user@example.com
```

- 遠程執行命令
```bash
# 語法
ssh <username>@<hostname> <command>

# 範例
ssh user@example.com ls /var/log
```

- 使用私鑰進行身份驗證
```bash
# 語法
ssh -i <path_to_private_key> <username>@<hostname>

# 範例
ssh -i ~/.ssh/id_rsa user@example.com
```

## 端口轉發
- 本地端口轉發
將本地機器的某個端口轉發到遠程伺服器
```bash
# 語法
ssh -L <local_port>:<remote_host>:<remote_port> <username>@<hostname>

# 範例
ssh -L 8080:localhost:80 user@example.com
```

- 遠程端口轉發
將遠程伺服器的某個端口轉發到本地機器
```bash
# 語法
ssh -R <remote_port>:<local_host>:<local_port> <username>@<hostname>

# 範例
ssh -R 8080:localhost:80 user@example.com
```

- 動態端口轉發
使用 SOCKS 代理進行動態端口轉發
```bash
# 語法
ssh -D <local_port> <username>@<hostname>

# 範例
# 將本地機器的 1080 端口設置為 SOCKS 代理
ssh -D 1080 user@example.com
```

## 公鑰認證
- 生成 SSH 密鑰對
使用 `ssh-keygen` 命令生成 SSH 密鑰對
```bash
# 語法
# 生成一個 RSA 密鑰對，默認保存在 ~/.ssh/id_rsa 和 ~/.ssh/id_rsa.pub
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- 將公鑰添加到遠程伺服器
將公鑰添加到遠程伺服器的 `~/.ssh/authorized_keys` 文件中
```bash
# 語法
ssh-copy-id <username>@<hostname>

# 範例
# 將公鑰添加到 example.com 的 user 帳戶
ssh-copy-id user@example.com
```

## SSH 配置
- 禁用 root 登錄
編輯 `/etc/ssh/sshd_config` 文件，將 `PermitRootLogin` 設置為 `no`
```bash
PermitRootLogin no
```

- 設置 SSH 使用的端口
修改 `/etc/ssh/sshd_config` 文件中的 `Port` 設置以改變 SSH 服務使用的默認端口
```bash
Port 2222
```

- 僅允許特定用戶登錄
在 `/etc/ssh/sshd_config` 文件中添加 `AllowUsers` 設置
```bash
AllowUsers user1 user2
```

- 重啟 SSH 服務
完成修改後，重啟 SSH 服務
```bash
sudo systemctl restart ssh
```

## SSH 配置文件
在 `~/.ssh/config` 文件中配置 SSH 連接，簡化日常使用
```plaintext
# 範例
Host example
    HostName example.com
    User user
    Port 22
    IdentityFile ~/.ssh/id_rsa
```
之後可以使用簡單的命令連接到伺服器
```bash
ssh example
```

## 參考資料
- [[Security] 你該知道所有關於 SSH 的那些事](https://medium.com/starbugs/security-%E4%BD%A0%E8%A9%B2%E7%9F%A5%E9%81%93%E6%89%80%E6%9C%89%E9%97%9C%E6%96%BC-ssh-%E7%9A%84%E9%82%A3%E4%BA%9B%E4%BA%8B-76b3518cb747)
- [SSH Essentials: Working with SSH Servers, Clients, and Keys](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#generating-and-working-with-ssh-keys)
