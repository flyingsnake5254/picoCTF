# sudo (superuser do)
用於以超級用戶（通常是 root）的身份執行命令。在 Unix 類操作系統中，sudo 提供了一種安全的方式來臨時獲取系統管理權限，而無需知道 root 的密碼。

# 基本用法
## 切換到超級用戶模式
切換到超級用戶模式，這樣你就可以以 root 用戶的身份執行多個命令
```bash
sudo -i
```
或
```bash
sudo su
```

## 列出當前用戶可用的 sudo 命令
這會顯示當前用戶在 sudoers 文件中被允許執行的命令列表。S
```bash
sudo -l
```