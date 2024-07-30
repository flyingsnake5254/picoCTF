# grep
用於在文件中搜索文本字符串或正則表達式。

# 基本用法
```bash
# 語法
grep "pattern" <file>

# 範例
grep "hello" example.txt
```

# 常用參數
## 多文件搜索
```bash
grep "pattern" <file1> <file2>
```

## -i 忽略大小寫
```bash
grep -i "pattern" <file>
```

## -n 顯示匹配行的行號
```bash
grep -n "pattern" <file>
```

## -r 在目錄及其子目錄中遞歸搜索
```bash
# 語法
grep -r "pattern" <directory>

# 範例
# 在當前目錄及其子目錄中搜索 "hello"
grep -r "hello" .
```

# 進階用法
## -C 顯示匹配行的上下文（前後幾行）
```bash
# 語法
grep -C <number> "pattern" <file>

# 範例
# 顯示 "hello" 所在行及其上下各 3 行
grep -C 3 "hello" example.txt
```

## -l 顯示包含匹配字符串的文件名
```bash
# 語法
grep -l "pattern" <file1> <file2>
```

## -v 顯示不包含匹配字符串的行
```bash
# 語法
grep -v "pattern" <file>

# 範例
# 顯示不包含 "hello" 的行
grep -v "hello" example.txt
```

# 使用正則表達式
```bash
# 搜索包含 "hello" 或 "world" 的行
grep "hello\|world" example.txt

# 使用 -E 選項啟用擴展正則表達式（等同於 egrep）
grep -E "hello|world" example.txt
```