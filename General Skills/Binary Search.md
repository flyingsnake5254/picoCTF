# Description
```text
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.
Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!
You can download the challenge files here:
challenge.zip
Additional details will be available after launching your challenge instance.
```


# 解題
先使用 `ssh` 連線
```bash
ssh -p 60816 ctf-player@atlas.picoctf.net
```
每次猜的數字，根據提示，選擇範圍中間點，即可猜到數字
```bash
┌──(kali㉿kali)-[~]
└─$ ssh -p 60816 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Higher! Try again.
Enter your guess: 375
Lower! Try again.
Enter your guess: 312
Higher! Try again.
Enter your guess: 343
Lower! Try again.
Enter your guess: 327
Lower! Try again.
Enter your guess: 319
Congratulations! You guessed the correct number: 319
Here's your flag: picoCTF{g00d_gu355_2e90d29b}
Connection to atlas.picoctf.net closed.
```


<!-- flag -->
所以本題 FLAG 
```text
picoCTF{g00d_gu355_2e90d29b}
```

# 解題相關知識
[ssh 指令使用說明](../Info/ssh.md)