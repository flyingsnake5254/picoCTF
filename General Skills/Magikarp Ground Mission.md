# Description
```text
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `481e7b14`
```
# 解題
先使用 `ssh` 連線
```bash
ssh ctf-player@venus.picoctf.net -p 53080
```
使用 `pwd` 指令查看目前位置
```bash
ctf-player@pico-chall$ pwd
/home/ctf-player/drop-in
```
使用 `ls` 指令輸出目錄下的檔案
```bash
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
```
使用 `cat` 輸出 `1of3.flag.txt` 和 `instructions-to-2of3.txt`：
```bash
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
```
可以發現輸出 flag 的第一部分
```bash
ctf-player@pico-chall$ cat instructions-to-2of3.txt 
Next, go to the root of all things, more succinctly `/`
```
可以發現輸出下一個 flag 的提示，在 `/` 的位置，所以使用 `cd` 前往 `/`，並使用 `ls` 輸出目錄下的檔案
```bash
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  dev   instructions-to-3of3.txt  media  proc  sbin  tmp
bin            etc   lib                       mnt    root  srv   usr
boot           home  lib64                     opt    run   sys   var
```
使用 `cat` 輸出 `2of3.flag.txt` 和 `instructions-to-3of3.txt`：
```bash
ctf-player@pico-chall$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
```
可以發現輸出 flag 的第二部分

```bash
ctf-player@pico-chall$ cat instructions-to-3of3.txt 
Lastly, ctf-player, go home... more succinctly `~`

```
可以發現輸出下一個 flag 的提示，在 `~` 的位置，所以使用 `cd` 前往 `~`，並使用 `ls` 輸出目錄下的檔案
```bash
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
```
使用 `cat` 輸出 `3of3.flag.txt`
```bash
ctf-player@pico-chall$ cat 3of3.flag.txt 
1118a9a4}
```
可以發現輸出 flag 的第三部分

<!-- flag -->
所以本題 FLAG 
```text
picoCTF{xxsh_0ut_0f_\/\/4t3r_1118a9a4}
```
