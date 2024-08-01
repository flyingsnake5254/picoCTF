# Description
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer. ssh -p 59829 ctf-player@saturn.picoctf.net. The password is af86add3

# 解題
使用 `ssh` 連線後進到遠端 shell
```bash
ssh -p 59829 ctf-player@saturn.picoctf.net
```
先按兩次 `Tab` 查看目前可以使用的指令
```bash
Specialer$      
!          cd         else       hash       pwd        times
./         command    enable     help       read       trap
:          compgen    esac       history    readarray  true
[          complete   eval       if         readonly   type
[[         compopt    exec       in         return     typeset
]]         continue   exit       jobs       select     ulimit
alias      coproc     export     kill       set        umask
bash       declare    false      let        shift      unalias
bg         dirs       fc         local      shopt      unset
bind       disown     fg         logout     source     until
break      do         fi         mapfile    suspend    wait
```
沒 `ls`、`cat`，但這兩個指令可以使用 `echo` 替代，如下：
```bash
# 發現有三個目錄
Specialer$ echo *
abra ala sim

# abra 目錄下有兩個 txt
Specialer$ echo abra/*
abra/cadabra.txt abra/cadaniel.txt

# ala 目錄下有兩個 txt
Specialer$ echo ala/*
ala/kazam.txt ala/mode.txt

# sim 目錄下有兩個 txt
Specialer$ echo sim/*
sim/city.txt sim/salabim.txt
```

使用 `echo $(<filename)` 取代 `cat` (這部分可以參考 [Shell Expansion](../Info/Shell%20Expansions.md))，最後在 `ala/kazam.txt` 得到 flag
```bash
Specialer$ echo $(<ala/kazam.txt)
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_a8567b6f}
```

# 延伸討論
其實這題我一開始是使用以下方式取代 `cat`( 可以參考 [read 指令](../Info/read.md))：
```bash
Specialer$ while read line; do echo "$line"; done <ala/kazam.txt
Specialer$
```
但卻沒輸出任何東西，原因是 `ala/kazam.txt` 的檔案內容可能**沒有換行字符**，所以 `while read` 無法正確讀到這行。

以下示範在無換行符號下，`while read`、`echo $(<file)` 的輸出差異
```bash
# 先使用 echo -n 建立一個不含換行符號的檔案
┌──(kali㉿kali)-[~/Downloads]
└─$ echo -n "conan" > test.txt

# 使用 `cat` 可以正確輸出內容
┌──(kali㉿kali)-[~/Downloads]
└─$ cat test.txt
conan

# 使用 `echo $(<test.txt) 可以正確輸出內容
┌──(kali㉿kali)-[~/Downloads]
└─$ echo $(<test.txt)
conan

# 使用 `while read` 無法輸出內容
┌──(kali㉿kali)-[~/Downloads]
└─$ while read line; do echo "$line"; done < test.txt
```

# 相關學習資源
[Shell Expansion](../Info/Shell%20Expansions.md)