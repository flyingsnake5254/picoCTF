# John the Ripper
密碼破解工具，支持多種哈希類型和攻擊模式。

# 基本使用
使用默認的字典攻擊來破解哈希。John the Ripper 會自動檢測哈希類型並開始破解。
```bash
# 語法
john <hash-file>

# 要顯示已經破解的密碼，使用以下命令
john --show <hash-file>
```

# 常用參數
## --wordlist 指定字典文件
```bash
# 語法
john --wordlist=<字典路徑> <hash-file>

# 範例
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

## --format 指定 hash 類型
```bash
# 語法
john --format=<hash-type> <hash-file>

# 範例
john --format=raw-md5 hashes.txt

# 顯示所有支持的 hash type
john --list=formats
```

## --incremental 暴力破解
會嘗試所有可能的字符組合。這是最耗時的攻擊方式，但可以破解更強的密碼。
```bash
john --incremental <hash-file>
```

## --fork 使用多核 CPU
John the Ripper 支持使用多核 CPU 來加速破解過程。
```bash
john --fork=<number_of_processes> <hash-file>
```
