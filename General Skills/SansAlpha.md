# Description
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols. ssh -p 50772 ctf-player@mimas.picoctf.net Use password: 84b12bae

# 解題
先使用 `ssh` 連線後進到遠端 shell
```bash
ssh -p 50772 ctf-player@mimas.picoctf.net
```

題目表示這個 shell 只能輸入**符號**和**數字**，所以先利用以下方式探勘各個目錄底下有什麼檔案
```bash
# 輸入 `*` 發現底下有一個 blargh
SansAlpha$ *
bash: blargh: command not found

# 進一步使用 `*` 探勘，發現 blargh 底下有個 flag.txt
SansAlpha$ */*
bash: blargh/flag.txt: Permission denied

# 接下來因為不能使用任何英文字輸入指令，故去 `/bin` 底下探勘有哪些指令可用
# 最後發現有 `base64`
SansAlpha$ /???/??????
/bin/base32: extra operand '/bin/base64'
Try '/bin/base32 --help' for more information.

# 制定策略：利用 base64 加密 flag.txt 讓它顯示 encode 結果
# 卻發現有其他同樣是 6 個字元的指令（base3）
SansAlpha$ /???/?????? */*
/bin/base32: extra operand '/bin/base64'
Try '/bin/base32 --help' for more information.

# 進一步指定 64
# 發現還有另一個同樣是 6 個字元並且 64 結尾的指令（x86_64）
SansAlpha$ /???/????64 */*
/bin/base64: extra operand '/bin/x86_64'
Try '/bin/base64 --help' for more information.

# 利用 `[^]` 過濾字元
# 但似乎 flag.txt 指定的不夠明確
SansAlpha$ /???/?[^8]??64 */*
/bin/base64: extra operand 'blargh/flag.txt'
Try '/bin/base64 --help' for more information.

# 以 `?` 取代 `*` 明確指定字元數量
# 即可得到 encode 後的 flag.txt
SansAlpha$ /???/?[^8]??64 ??????/????.???
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=

# 複製 encode 的 flag.txt，退出遠端 shell 回到自己的終端
# 將 encode 的內容 保存到 flag.txt
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=" > flag.txt

# 利用 `base64` 指令 decode 即可得到 flag
┌──(kali㉿kali)-[~/Downloads]
└─$ base64 -d flag.txt
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_b0d5e855}

```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{7h15_mu171v3r53_15_m4dn355_b0d5e855}
```

# 相關指令、技能
[base64](../Info/base64.md)  
[正則表達式](../Info/regular%20expression.md)