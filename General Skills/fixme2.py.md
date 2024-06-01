# Description
```text
Fix the syntax error in the Python script to print the flag. Download Python script
```

# 解題
使用 `python fixme2.py` 執行出現錯誤
```bash
  File "/home/kali/Downloads/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```
發現 line 22 的 if 判斷 `=` 只有一個，故修正成 `==` 再執行腳本，即可得到 flag
```python 
if flag == "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)
```
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python fixme2.py 
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
```
