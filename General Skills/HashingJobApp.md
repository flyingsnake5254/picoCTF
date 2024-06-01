# Description
```text
If you want to hash with the best, beat this test!

Additional details will be available after launching your challenge instance.
```
Start Instance 後
```text
If you want to hash with the best, beat this test! nc saturn.picoctf.net 58634
```

# 解題
先使用 `netcat` 連線，結果要求使用 md5 加密 kilts，
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ nc saturn.picoctf.net 58634
Please md5 hash the text between quotes, excluding the quotes: 'kilts'
Answer: 
```
可以使用 `echo -n <string> | md5sum` 輸出字串 hash
```bash
┌──(kali㉿kali)-[~]
└─$ echo -n "kilts" | md5sum
64cb30b3223e083fa0a2dad43fae9a0e  -
```
依此類推，回答所有問題後可以得到 flag


<!-- flag -->
所以本題 FLAG 
```text
picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}
```
