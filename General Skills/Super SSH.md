# Description
Using a Secure Shell (SSH) is going to be pretty important. Can you ssh as ctf-player to titan.picoctf.net at port 59657 to get the flag? You'll also need the password 6dd28e9b. If asked, accept the fingerprint with yes. If your device doesn't have a shell, you can use: https://webshell.picoctf.org If you're not sure what a shell is, check out our Primer: https://primer.picoctf.com/#_the_shell

# 解題
使用 ssh 連接
```bash
ssh ctf-player@titan.picoctf.net -p 59657
```
並依照題目對之後的為應輸入 `yes` 以及題目提供的密碼 `6dd28e9b`，即可得到 FLAG
```text
The authenticity of host '[titan.picoctf.net]:59657 ([3.139.174.234]:59657)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:59657' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_5d09a462}
Connection to titan.picoctf.net closed.

```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{s3cur3_c0nn3ct10n_5d09a462}
```
# 相關指令
[ssh](../Info/ssh.md)