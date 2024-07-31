# Description
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?
You can download the challenge files here:
challenge.zip

# 解題
下載檔案解壓縮後，使用 `ls` 發現 `flag.py`，使用 `cat` 輸出內容，並無發現 flag，使用 `git branch` 發現有多個分支
```bash            
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git branch
  feature/part-1
  feature/part-2
  feature/part-3
* main   
```
使用 `git switch <branch name>` 切換分支，並輸出 flag.py 內容
```bash
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git switch feature/part-1
Switched to branch 'feature/part-1'
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls
flag.py                
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py 
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')      
```
發現 flag 的第一部分，依此類推，切換到其他分支並查看 flag.py
```bash
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git switch feature/part-2
Switched to branch 'feature/part-2'                               
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls         
flag.py                             
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py 
print("Printing the flag...")
print("m@k3s_th3_dr3@m_", end='')  
```
```bash
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git switch feature/part-3
Switched to branch 'feature/part-3'                           
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls                       
flag.py                         
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py 
print("Printing the flag...")
print("w0rk_e4b79efb}")
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_e4b79efb}
```

# 相關指令
[git](../Info/git.md)