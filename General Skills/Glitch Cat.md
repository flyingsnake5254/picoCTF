# Description
```text
Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.
```
start instance 後
```text
Our flag printing service has started glitching! $ nc saturn.picoctf.net 54263
```

# 解題
先使用 `netcat` 連線
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ nc saturn.picoctf.net 54263
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
```
發現回傳 python code，直接執行 `python`，並貼上該內容就可以得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ python          
Python 3.11.8 (main, Feb  7 2024, 21:52:08) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
'picoCTF{gl17ch_m3_n07_bda68f75}'
```


<!-- flag -->
所以本題 FLAG 
```text
picoCTF{gl17ch_m3_n07_bda68f75}
```
