# hexdump
hexdump 是另一個用於顯示二進制文件的十六進制表示的工具。

# 基本使用方式

### 顯示文件的十六進制表示
```bash
# 語法
hexdump <filename>

# 範例
└─$ hexdump level3.hash.bin 
0000000 181b 31e1 926f cc18 055b 1c3e 28ea 2ee0
0000010
```

### 使用 `-C` 選項顯示更可讀的格式
這會顯示十六進制和 ASCII 表示
```bash
# 語法
hexdump -C <filename>

# 範例
└─$ hexdump -C level3.hash.bin 
00000000  1b 18 e1 31 6f 92 18 cc  5b 05 3e 1c ea 28 e0 2e  |...1o...[.>..(..|
00000010
```
