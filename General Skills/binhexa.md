# Description
How well can you perfom basic binary operations? Start searching for the flag here nc titan.picoctf.net 62292

# 解題
先使用 `netcat` 連線，會出一些二進位計算題目，完成計算後就可以拿到 flag
```bash
┌──(kali㉿kali)-[~]
└─$ nc titan.picoctf.net 62292

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10011100
Binary Number 2: 10101001


Question 1/6:
Operation 1: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10001000
Incorrect. Try again
Enter the binary result: ^C
                                                              
┌──(kali㉿kali)-[~]
└─$ nc titan.picoctf.net 62292

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11010111
Binary Number 2: 10010111


Question 1/6:
Operation 1: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10010111
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 10101110
Incorrect. Try again
Enter the binary result: 10101111
Incorrect. Try again
Enter the binary result: 110101110
Correct!

Question 3/6:
Operation 3: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: ^C^X^X^S

Incorrect input. Provide the right input
Enter the binary result: ^C
                                                              
┌──(kali㉿kali)-[~]
└─$ nc titan.picoctf.net 62292

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10110000
Binary Number 2: 10000110


Question 1/6:
Operation 1: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10000000
Correct!

Question 2/6:
Operation 2: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 1000011
Correct!

Question 3/6:
Operation 3: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 101100000
Correct!

Question 4/6:
Operation 4: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 101110000100000
Correct!

Question 5/6:
Operation 5: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10110110
Correct!

Question 6/6:
Operation 6: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 100110110
Correct!

Enter the results of the last operation in hexadecimal: 136

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}
```




<!-- flag -->
所以本題 FLAG 
```text
picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}
```
# 相關指令
[netcat](../Info/netcat.md)