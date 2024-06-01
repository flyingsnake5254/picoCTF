# Description
```text
Can you crack the password to get the flag? Download the password checker here and you'll need the encrypted flag in the same directory too.
```

# 解題
先使用 `python level2.py` 執行腳本，發現要輸入密碼，先查看 level2.py，發現 line 18 有密碼
```python
if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
```
使用 `python` 輸出該密碼，得到 `39ce`
```bash
>>> chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
'39ce'
```
執行腳本後輸入密碼就可以得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{tr45h_51ng1ng_502ec42e}
```
