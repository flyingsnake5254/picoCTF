# Description
Can you crack the password to get the flag? Download the password checker here and you'll need the encrypted flag in the same directory too.


# 解題
先執行 `python level1.py`，發現要求輸入密碼，先查看 level1.py，看到 line 19，得知密碼是 `691d`
```python
if( user_pw == "691d"):
```
所以執行腳本輸入密碼後，可以得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python level1.py 
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419};
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{545h_r1ng1ng_56891419}
```
