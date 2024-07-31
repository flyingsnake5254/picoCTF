# Description
Python scripts are invoked kind of like programs in the Terminal... Can you run this Python script using this password to get the flag?

# 解題
```bash
# 這題給了三個檔案
└─$ ls
ende.py  flag.txt.en  pw.txt

# 先使用 `cat` 看內容
┌──(kali㉿kali)-[~/Downloads]
└─$ cat pw.txt   
6008014f6008014f6008014f6008014f
# 可以發現 flag 似乎被 encode
└─$ cat flag.txt.en 
gAAAAABgUAIVI-r3OTKrDSgUJ8i3N9OzjacXZ1w4Hua00I_-Bg7gZu9Fld-TFYRiUiZlkLkChceqqpL9XnGOMO-W2-lRXpFhTkrqk9fHAvDfNkZHuZcjGPpG4xaR4mPnagzSNIrtL9tK

# 執行 `ende.py` 可以看到使用方式的提示
# 根據提示可以猜測 -e 跟 -d 分別代表 encode、decode
┌──(kali㉿kali)-[~/Downloads]
└─$ python ende.py               
Usage: ende.py (-e/-d) [file]

# 因為 flag 是 encode ，所以這裡參數選擇 decode
# 接者輸入 `pw.txt` 紀錄的密碼即可取得 flag
┌──(kali㉿kali)-[~/Downloads]
└─$ python ende.py -d flag.txt.en 
Please enter the password:6008014f6008014f6008014f6008014f
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```
