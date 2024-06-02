# Description
```text
Files can always be changed in a secret way. Can you find the flag? cat.jpg
```


# 解題
利用  `exiftool` 輸出圖片詳細資訊
```bash
 exiftool cat.jpg
```
得到以下輸出
```bash
ExifTool Version Number         : 12.76
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2024:06:02 01:58:13-04:00
File Access Date/Time           : 2024:06:02 01:58:14-04:00
File Inode Change Date/Time     : 2024:06:02 01:58:13-04:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
發現有兩串看起來像是亂碼，分別是 `7a78f3d9cfb1ce42ab5a3aa30573d617` 、`cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9` ，使用 `echo <密文> | base64 -d` 指令 decode
```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "7a78f3d9cfb1ce42ab5a3aa30573d617" | base64 -d            
���w}q��q�6i�Zݦ�Ӟ�w�{                                                                                   
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d
picoCTF{the_m3tadata_1s_modified}
```


<!-- flag -->
所以本題 FLAG 
```text
picoCTF{the_m3tadata_1s_modified}
```
