# Shell Expansions
Shell Expansions 會對我們輸入的指令做一連串處理，然後才執行指令。
例子 1：
```bash
name="sherlock"
echo "Hello, $name"
```
`line 2` 的 `$name` 會先被替換成 "sherlock" ，才會執行 `echo` 指令
```bash
echo "Hello, sherlock"
```

## Shell Expansions 處理順序
1. [大括號擴展 (Brace Expansions)](#1-大括號擴展-brace-expansions)
2. [波浪符擴展 (Tilde Expansions)](#2-波浪符擴展-tilde-expansions)
3. [參數和變數擴展 (Parameter and Variale Expansion)](#3-參數和變數擴展-parameter-and-variale-expansion)
4. [命令替換 (Command Substitution)](#4-命令替換-command-substitution)
5. [算術擴展 (Arithmetic Expansion)](#5-算術擴展-arithmetic-expansion)
6. [進程替換（Process Substitution）](#6-進程替換process-substitution)
7. [字符串分割 (Word Splitting)](#6-字符串分割-word-splitting)
8. [檔名擴展 (Filename Expansion)](#7-檔名擴展-filename-expansion)

### 1. 大括號擴展 (Brace Expansions)
#### 數字範圍擴展
```bash
{1..5}
```
被擴展為
```bash
1 2 3 4 5
```
範例
```bash
echo {1..5}
1 2 3 4 5
```

#### 字母範圍擴展
```bash
{a..f}
```
被擴展為
```bash
a b c d e f
```
範例
```bash
echo {a..f}
a b c d e f
```

#### 簡單字符串擴展
```bash
a{b,c,d}e
```
被擴展為
```bash
abe ace ade
```
範例
```bash
echo a{b,c,d}e
abe ace ade
```

#### 組合字符串擴展
```bash
{a,b}{1,2}
```
被擴展為
```bash
a1 a2 b1 b2
```
範例
```bash
echo {a,b}{1,2}
a1 a2 b1 b2
```


### 2. 波浪符擴展 (Tilde Expansions)
#### 表示主目錄
```bash
~
```
被擴展為
```bash
/home/username
```
範例
```bash
echo ~
/home/username
```

#### 特定用戶的主目錄
```bash
~other_user
```
被擴展為
```bash
/home/other_user
```

#### 表當前工作目錄
```bash
~+
```
被擴展為
```bash
$PWD
```

#### 表前一個工作目錄
```bash
~-
```
被擴展為
```bash
$OLDPWD
```


### 3. 參數和變數擴展 (Parameter and Variale Expansion)
#### 變數替換 (Variable Substitution)
```bash
name="Sherlock"
echo "Hello, $name"
```
被替換成
```bash
echo "Hello, Sherlock"
```

#### `${Parameter-Word}`
若 `Parameter` **尚未設置** 或等於 **null**，就將 `Parameter` **替換**成 `Word`。(Parameter 本身的數值並**不會被改變**)
範例 1：假設 Parameter **尚未被賦值**
```bash
echo ${name-sherlock}
# 輸出 
sherlock

# 再次輸出 name 會為空，因為 Parameter 本身的數值並不會被改變
echo $name
# 輸出為空

```
範例 2：假設 Parameter **已被賦值**
```bash
name=holmes
echo ${name-sherlock}
# 輸出
holmes
```

#### `${Parameter:=Word}`
若 `Parameter` **尚未設置** 或等於 **null**，就將 `Parameter` **賦值**成 `Word`。(Parameter 本身的數值並**會被改變**)
範例 1：假設 Parameter **尚未被賦值**
```bash
echo ${name-sherlock}
# 輸出 
sherlock

# 再次輸出 name 會為 sherlock，因為 Parameter 本身的數值並會被改變
echo $name
# 輸出
sherlock
```

#### `${Parameter:+Word}`
若 `Parameter` **有賦值**，就將 `Parameter` **替換**成 `Word`。(Parameter 本身的數值並**不會被改變**)
範例 1：假設 Parameter **尚未被賦值**
```bash
echo ${name:+sherlock}
# 輸出為空 

# 再次輸出 name 會為空，因為 Parameter 本身的數值並不會被改變
echo $name
# 輸出為空

```
範例 2：假設 Parameter **已被賦值**
```bash
name=holmes
echo ${name:+sherlock}
# 輸出
sherlock

# 再次輸出 name 會為 holmes，因為 Parameter 本身的數值並不會被改變
echo $name
# 輸出
holmes
```

#### `${Parameter:?Word}`
若 `Parameter` **尚未設置** 或等於 **null**，就會報錯（並且 `Word` 會被加在錯誤訊息後方）並中止執行
```bash
echo ${name:?name is unset or null}
# 輸出
zsh: name: name is unset or null
```

#### 獲取字串長度
```bash
name="sherlock holmes"
echo ${#name}
# 輸出
15
```

#### 字串提取
```bash
string=0123456789876543210

echo ${string:7}
# 輸出
789876543210

echo ${string:7:2}
# 輸出
78

echo ${string:7:-2}
# 輸出
7898765432
```

#### 字串替換
單純進行**替換**，而不會**賦值**（變數的數值**不會被更改**）。
```bash
filename="document.txt"

echo ${filename/.txt/.docx}
# 輸出
document.docx

echo $filename
# 輸出（變數的數值不會被更改）
document.txt
```

#### 字串全局替換
```bash
string="a a b a b c d e a b c"
echo ${string//a/A}
# 輸出
A A b A b c d e A b c
```

#### 移除前綴 (Remove Prefix)
```bash
string="aaa&bbb&ccc&ddd"

# 移除最短前綴
echo ${string#*&} 
# 輸出
bbb&ccc&ddd

# 移除最長前綴
echo ${string##*&} 
# 輸出
ddd
```

#### 移除後綴 (Remove Suffix)
```bash
string="aaa&bbb&ccc&ddd"

# 移除最短後綴
echo ${string%&*}
# 輸出
aaa&bbb&ccc

# 移除最長後綴
echo ${string%%&*}
# 輸出
aaa
```

### 4. 命令替換 (Command Substitution)
#### 使用反引號 (\`)
```bash
show_file=`ls -R` 
echo "show dir file:$show_file"
# 輸出
show dir file:.:
dir1

./dir1:
test.sh
```

#### 使用括號 $()
範例 1：
```bash
show_file=$(ls -R)
echo "show dir file:$show_file"
# 輸出
show dir file:.:
dir1

./dir1:
test.sh
```
範例 2：
```bash
echo "i am $(whoami)"
# 輸出
i am sherloxk
```


### 5. 算術擴展 (Arithmetic Expansion)
#### 基本語法
```bash
$((expression))
```
範例
```bash
a=5
b=8

echo $((a+b))
# 輸出 
13
```

### 6. 進程替換（Process Substitution）
#### 語法
`<(command)`：將 `command` 的結果作為**輸入文件**，提供給另一個命令





### 7. 字符串分割 (Word Splitting)
### 8. 檔名擴展 (Filename Expansion)

# 參考資料
[Shell Expansions](https://www.gnu.org/software/bash/manual/html_node/Shell-Expansions.html "Shell Expansions")