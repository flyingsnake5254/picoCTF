# Description
There is a nice program that you can talk to by using this command in a shell: $ nc mercury.picoctf.net 22342, but it doesn't speak English...


# 解題
先使用 `netcat` 連線，可以看到一堆數字，推測是 ASCII
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ nc mercury.picoctf.net 22342
112 
105 
99 
111 
67 
84 
70 
...
```
寫一支 python 將這些 ASCII 轉 CHAR
```python
ascii_flag = '''112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
53 
102 
98 
53 
101 
53 
49 
100 
125 
10'''
flag = ''
for char in ascii_flag.split():
    flag += chr(eval(char))
print(flag)
```

輸出
```text
picoCTF{g00d_k1tty!_n1c3_k1tty!_5fb5e51d}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{g00d_k1tty!_n1c3_k1tty!_5fb5e51d}
```
