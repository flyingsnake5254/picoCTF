# interencdec

## Description
Can you get the real meaning from this file. Download the file here. 

## 解題
```bash
# 使用 `cat` 列出 enc_flag
# 發現應該使用 base64 加密了
└─$ cat enc_flag 
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==
                                                                           
# 使用 base64 decode 後發現似乎是用 base64 多重加密
└─$ base64 -d enc_flag
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='
                                                                           
# 再用一次 base64 decode
# 可以看到類似 flag 的密文了，推測是用凱薩加密
└─$ echo -n "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ==" | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
```

接者寫一隻 python 解 `wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}` 這個凱薩密碼 ( 只對英文字做轉換 )。轉換策略：
**wpjvJAM** 會對應 **picoCTF**，w 的 ASCII 減 7 會等於 p，故可知差值是 7。
```python
enc = 'wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}'
dec = ''
for char in enc:
    # 判斷是否為英文字
    if char.isalpha():
        # 判斷大小寫
        if ord(char) >= ord('a'):
            dec += chr(ord('a') + ((ord(char) - ord('a') - 7) % 26))
        else:
            dec += chr(ord('A') + ((ord(char) - ord('A') - 7) % 26))
    else:
        dec += char
print(dec)
```
執行後會輸出
```bash
picoCTF{caesar_d3cr9pt3d_890d2379}
```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{caesar_d3cr9pt3d_890d2379}
```

# 相關學習資源
[base64](../Info/base64.md)  