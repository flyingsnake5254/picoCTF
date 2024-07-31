# Description
Fix the syntax error in this Python script to print the flag. Download Python script

# 解題
使用 `python fixme1.py` 出現錯誤
```bash
  File "/home/kali/Downloads/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
```
發現錯誤出現在 line 20  
使用 `vim` 開啟檔案後，可以在輸入指令的模式輸入 `:set number` 讓 vim 顯示行號
```python
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)
```
發現 line 20 的縮行不正確，所以將縮行修正如下，再執行腳本，就可以得到 flag
```python
flag = str_xor(flag_enc, 'enkidu')
print('That is correct! Here\'s your flag: ' + flag)
```
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python fixme1.py 
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_182342f7}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{1nd3nt1ty_cr1515_182342f7}
```
