# Description
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with nc jupiter.challenges.picoctf.org 29956.

# 解題
先使用 `netcat` 連線  
```bash
nc jupiter.challenges.picoctf.org 29956
```
連線後顯示  
``` bash
Let us see how data is stored
animation
Please give the 01100001 01101110 01101001 01101101 01100001 01110100 01101001 01101111 01101110 as a word.
...
you have 45 seconds.....

Input:
```
推測這題應該是要將各種進位法轉成 ASCII  
先寫一隻 python function ，將各個進位轉 ASCII，如下
```python
def base_to_ascii(input, base):
  input = input.split(' ')
  for word in input:
    print(chr(int(word, base)), end='')
  print()


while True:
  base_to_ascii(input('input words:'), eval(input('input base:')))
```
執行這隻程式後，將題目的字串輸入，如下：
```bash
input words:01100001 01101110 01101001 01101101 01100001 01110100 01101001 01101111 01101110
input base:2
```
得到輸出  
```bash
animation
```
將 animation 輸入至題目後，又得到以下內容：
```bash
Please give me the  164 145 163 164 as a word.
```
看起來是 base 8 ，將 `164 145 163 164` 輸入到剛剛執行的 python 程式，得到：  
```bash
input words:164 145 163 164
input base:8
test
```
將 test 輸入至題目後，又得到以下內容：
```bash
Please give me the 6e75727365 as a word.
```
看起來是 base 16 ，並且兩個 base 16 字元構成一個 byte，故先將`6e75727365` 切隔成 `164 145 163 164` 並輸入到剛剛執行的 python 程式，得到：
```bash
input words:6e 75 72 73 65
input base:16
nurse
```
將 nurse 輸入至題目後，得到以下內容：
```bash
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_b375bb16}
```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{learning_about_converting_values_b375bb16}
```