# base64
是一種用於編碼和解碼數據的命令行工具。它可以將二進制數據轉換為可打印的 ASCII 字符串，這在傳輸二進制數據（如圖像或文件）時非常有用。

## encode 文件
```bash
# 語法
base64 <input_file> > <output_file>

# 範例
base64 example.txt > encoded.txt
```

## decode 文件
```bash
# 語法
base64 --decode <input_file> > <output_file>

# 範例
base64 --decode encoded.txt > decoded.txt
```

## encode 標準輸入
```bash
echo -n "Hello, World!" | base64

# Output
SGVsbG8sIFdvcmxkIQ==
```

## decode 標準輸入
```bash
echo -n "SGVsbG8sIFdvcmxkIQ==" | base64 --decode

# Output
Hello, World!
```