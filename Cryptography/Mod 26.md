# Description
```text
Cryptography can be easy, do you know what ROT13 is? cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}
```


# 解題
`cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}` 這段看起來是用凱薩加密，且 `cvpbPGS` 應該對應 `picoCTF` 。使用 python 確認兩者的差值 mod 26 皆為 13，如下
```python
encode = 'cvpbPGS'
decode = 'picoCTF'

for i in range(7):
  print(abs(ord(decode[i]) - ord(encode[i])) % 26)
```
輸出
```bash
13
13
13
13
13
13
13
```
撰寫一隻 python 解這個差值 13 的凱薩密碼
```python
enc = "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}"
dec = ''
for char in enc:
    # 判斷是否為英文字
    if char.isalpha():
        # 判斷大小寫
        if ord(char) >= ord('a'):
            dec += chr(ord('a') + ((ord(char) - ord('a') + 13) % 26))
        else:
            dec += chr(ord('A') + ((ord(char) - ord('A') + 13) % 26))
    else:
        dec += char
print(dec)
```
輸出
```bash
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```
