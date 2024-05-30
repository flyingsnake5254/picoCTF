# Description
```text
What is 0x3D (base 16) in decimal (base 10)?
```
# 解題
base 16 表示法對應成 base 10 表示法如下：
| base 16 | base 10 |
| ---- | ---- |
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| 5 | 5 |
| 6 | 6 |
| 7 | 7 |
| 8 | 8 |
| 9 | 9 |
| A | 10 |
| B | 11 |
| C | 12 |
| D | 13 |
| E | 14 |
| F | 15 |

本題 base 16 轉成 base 10 的計算如下：
base 16 的 `D` = base 10 的 `13`
16<sup>0</sup> x 13 + 16<sup>1</sup> x 3
= 48 + 13
= 61
所以本題 FLAG 
<!-- flag -->
```text
picoCTF{61}
```
# 補充
可以撰寫 code 輸出 base 10 數字，以 python 為例：
```python
print(0x3D)
```
輸出
```text
61
```
