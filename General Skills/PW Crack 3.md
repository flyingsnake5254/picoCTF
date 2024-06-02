# Description
```text
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
```


# 解題
可以看 level3.py 的最後一行 code , 直接把可能的密碼列出來，所以全部拿去試就可以得到 flag。  
但本題想要傳達的技能是另外一個。  
首先使用可以檢視 byte 檔案的 [網站](https://hexed.it/) 查看 `level3.hash.bin` 內容，得到如下
![hex editor](../assets/PW_Crack3__1.png) 
從 `level3.py` 的 `line 20` 知道是使用 `md5`，所以將 `level3.hash.bin` 內容丟到 [hash 破解網站](https://crackstation.net/) 即可得到密碼 `865e`
![password](../assets/PW_Crack3__2.png)

最後在執行 `level3.py` 並輸入 `865e` 即可得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{m45h_fl1ng1ng_2b072a90}
```
