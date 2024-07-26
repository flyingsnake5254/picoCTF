# Description
```text
Someone's commits seems to be preventing the program from working. Who is it?
You can download the challenge files here:
challenge.zip
```
將檔案下載下來後解壓縮，這題的 git commit 紀錄有很多，所以可以使用 `git log > log` 先將檔案存起來，之後利用查找關鍵字，找到 flag，或是使用 `git log | grep "picoCTF{"`，輸出 flag
```bash
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git log | grep "picoCTF{"
Author: picoCTF{@sk_th3_1nt3rn_cfca95b2} <ops@picoctf.com>

```
# 解題
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{@sk_th3_1nt3rn_cfca95b2} 
```

# 相關指令
[git](../Info/git.md)