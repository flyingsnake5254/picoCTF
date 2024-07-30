# md5sum
md5sum 是一個命令行工具，用於計算文件的 MD5 散列值（雜湊值）。

# 基本使用方式

### 計算單個文件的 MD5 hash
```bash
# 語法
md5sum <file-name>
# 計算多個文件的 MD5 散列值
md5sum file1.txt file2.txt file3.txt


# 範例
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "sherlock" > test.txt                        

# 輸出一個32位的十六進制數字（MD5 散列值）和文件名                                                                              
┌──(kali㉿kali)-[~/Downloads]
└─$ md5sum test.txt 
3b1d790f0def96ca083e7a0064f0a9ea  test.txt
```


### 從標準輸入計算 MD5 hash
```bash
# 語法
echo "標準輸入" | md5sum

# 範例
# 這會計算字符串 "sherlock" 的 MD5 hash
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "sherlock" | md5sum  
3b1d790f0def96ca083e7a0064f0a9ea  -
```


### 檢查 MD5 散列值
先將 `hash-value` 和對應的 `file-name` 寫進一個檔案，內容如下：
```plaintext
3b1d790f0def96ca083e7a0064f0a9ea  file1.txt
717b3e4fdf10d194bd2637a7e369e99b  file2.txt
```
接著使用 `md5sum` + `-c` 檢驗
```bash
└─$ md5sum -c check.txt 
file1.txt: OK
file2.txt: OK
```