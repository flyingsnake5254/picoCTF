# Description
```text
Know of little and big endian? Source

Additional details will be available after launching your challenge instance.
```
start instance
```text
Know of little and big endian? Source nc titan.picoctf.net 56675
```

# 解題
使用 `netcat` 連線後，會給一個 Word 然後要輸出他的 Big Endian, Little Endian。撰寫一個 python 輸出字串的 Big Endian , Little Endian
```python
while True:
  ans=[]
  for word in input('input:'):
    ans.append(hex(ord(word)).replace('0x',''))
  print('Big Endian :', end='')
  for element in ans:
    print(element, end='')
  print()
  ans.reverse()
  print('Little Endian :', end='')
  for element in ans:
    print(element, end='')
  print()
```
輸入給定的字串後，輸出
```bash
input:ubesr
Big Endian :7562657372
Little Endian :7273656275
```
將這兩個輸入到題目，即可得到 flag
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ nc titan.picoctf.net 56675
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: ubesr
Enter the Little Endian representation: 7273656275
Correct Little Endian representation!
Enter the Big Endian representation: 7562657372
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_25c5f083}

```



<!-- flag -->
所以本題 FLAG 
```text
picoCTF{3ndi4n_sw4p_su33ess_25c5f083}
```
