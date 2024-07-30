# Description
```text
Unzip this archive and find the file named 'uber-secret.txt'
Download zip file
```


# 解題
解壓縮檔案後，使用 `grep -r <目標字串> <目錄路徑>` 指令遞迴搜尋旗下檔案內容是否包含目標字串
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ grep -r "picoCTF" files
files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt:picoCTF{f1nd_15_f457_ab443fd1}
```



<!-- flag -->
所以本題 FLAG 
```text
picoCTF{f1nd_15_f457_ab443fd1}
```


# 相關指令
[grep](../Info/grep.md)