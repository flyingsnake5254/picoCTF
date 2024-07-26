# Description
```text
Unzip this archive and find the flag.
Download zip file
```


# 解題
解壓縮檔案後，使用 `grep -r <目標字串> <目錄路徑>` 指令遞迴搜尋旗下檔案內容是否包含目標字串
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ grep -r "picoCTF" big-zip-files
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}

```



<!-- flag -->
所以本題 FLAG 
```text
picoCTF{gr3p_15_m4g1c_ef8790dc}
```

# 相關指令
