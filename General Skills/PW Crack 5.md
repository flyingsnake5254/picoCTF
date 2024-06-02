# Description
```text
Can you crack the password to get the flag? Download the password checker here and you'll need the encrypted flag and the hash in the same directory too. Here's a dictionary with all possible passwords based on the password conventions we've seen so far.
```


# 解題
從 `level5.py` `line 21` 可以發現是使用 md5，接下來使用可以檢視 byte 檔案的 [網站](https://hexed.it/) 查看 `level5.hash.bin` 內容
![byte](../assets/PW_Crack5__1.png)
將這段內容
將這段內容丟到 [hash 破解網站](https://crackstation.net/) 即可得到密碼 `9581`
![pqssword](../assets/PW_Crack5__2.png)
執行 `level5.py` 並輸入密碼 `9581` 就可以得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python level5.py 
Please enter correct password for flag: 9581
Welcome back... your flag, user:
picoCTF{h45h_sl1ng1ng_36e992a6}
```



<!-- flag -->
所以本題 FLAG 
```text
picoCTF{h45h_sl1ng1ng_36e992a6}
```
