# read
用於從標準輸入讀取一行並將其賦值給變量。在腳本中，read 指令通常用於獲取用戶輸入或從文件中讀取數據。

# 基本用法
最基本的用法是從用戶獲取輸入並將其存儲在一個變量中。
```bash
#!/bin/bash
echo "input your name:"
read name
echo "your name is $name"
```
在這個示例中，read 等待用戶輸入並將輸入存儲在變量 name 中，然後使用 echo 打印出來

## 一次讀取多個變量
```bash
#!/bin/bash
echo "input 3 words:"
read word1 word2 word3
echo "$word1 $word2 $word3"
```

## `-p` 在讀取輸入前提供提示
```bash
#!/bin/bash
read -p "Enter your age: " age
echo "Your age is $age"
```

## `-s` 隱藏用戶輸入
```bash
#!/bin/bash

read -s -p "Enter your password: " password
echo
echo "Your password is: $password"
```

## `-r` 讀取包含反斜杠的字符串
`-r` 選項防止反斜杠轉義，這對於讀取文件路徑等包含反斜杠的字符串非常有用
```bash
#!/bin/bash

read -r -p "Enter a file path: " filepath
echo "You entered: $filepath"
```

## 從文件讀取
```bash
#!/bin/bash

while read line; do
  echo "Line: $line"
done < myfile.txt
```