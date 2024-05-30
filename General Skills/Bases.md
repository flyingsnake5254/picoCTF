# Description
```text
What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.
```
# 解題
`bDNhcm5fdGgzX3IwcDM1` 看起來像是明文經過 base64 加密後的密文，故使用 base64 decode  
可以直接去 [base64 encode decode 網站](https://www.base64decode.org/ "base64 encode decode 網站")  
或是撰寫 python code 如下
```python
import base64

# 密文
encode_string = "bDNhcm5fdGgzX3IwcDM1"
# 明文
decode_string = base64.b64decode(encode_string).decode('utf-8')
print(decode_string)
```
輸出
```text
l3arn_th3_r0p35
```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{l3arn_th3_r0p35}
```