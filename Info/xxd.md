# xxd
xxd 是一個 Unix 程序，用於創建二進制文件的十六進制表示，並且可以反向操作（即從十六進制表示重建二進制文件）。

# 基本使用方式
### 查看文件的十六進制表示
```bash
# 語法
xxd <file-name>

# 範例
xxd file.bin
```

### 將十六進制表示轉換回二進制文件
```bash
# 語法
xxd -r -p hexfile.txt > binaryfile.bin
```

