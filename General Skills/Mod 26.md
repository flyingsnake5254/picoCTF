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
故所求的 flag 可以透過 (encode + 13) mod 26 的方式求出，如下
```python

encode = "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}"

for i in encode:
  if i == '{' or i == '}' or i == '_' or i == "'" or not i.isalpha():
    print(i, end='')
  elif ord(i) >= 97:
    print(chr((ord(i) - 97 + 13) % 26 + 97), end='')
  else:
    print(chr((ord(i) - 65 + 13) % 26 + 65), end='')
```


<!-- flag -->
所以本題 FLAG 
```text
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```
