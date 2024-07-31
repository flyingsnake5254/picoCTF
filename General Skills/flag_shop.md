# Description
There's a flag shop selling stuff, can you buy a flag? Source. Connect with nc jupiter.challenges.picoctf.org 9745.

# 解題
先利用 `netcat` 連接
```bash
nc jupiter.challenges.picoctf.org 9745
```
收到以下訊息
```bash
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
```
選擇選項 `2`，收到以下
```bash
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
```
選擇選項 `1`，收到以下
```bash
These knockoff Flags cost 900 each, enter desired quantity
```
先隨機輸入數量`2`得到以下
```bash
The final cost is: 1800
Not enough funds to complete purchase
```
發現會計算花費的金額，再比對目前擁有的錢是否足夠，故推測可以利用溢位來增加自己擁有的錢  
也就是再輸入數量時，刻意輸入一個很大的數字，如下：
```bash
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
100000000000

The final cost is: -1039687680

Your current balance after transaction: 1039688780
```
發現 cost 確實溢位變成負數，並且自己的錢也因為 cost 變成負數，相減後數值反而增加了。
接著就可以選擇選項 `1337 Flag` 買真正的 flag 如下：
```bash
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_65d67a74}
```

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{m0n3y_bag5_65d67a74}
```