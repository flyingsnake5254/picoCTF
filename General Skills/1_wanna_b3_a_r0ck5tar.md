# Description
I wrote you another song. Put the flag in the picoCTF{} flag format

# 解題
把 song 下載後，打開來可以看到以下內容
```text
Rocknroll is right              
Silence is wrong                
A guitar is a six-string        
Tommy's been down               
Music is a billboard-burning razzmatazz!
Listen to the music             
If the music is a guitar                  
Say "Keep on rocking!"                
Listen to the rhythm
If the rhythm without Music is nothing
Tommy is rockin guitar
Shout Tommy!                    
Music is amazing sensation 
Jamming is awesome presence
Scream Music!                   
Scream Jamming!                 
Tommy is playing rock           
Scream Tommy!       
They are dazzled audiences                  
Shout it!
Rock is electric heaven                     
Scream it!
Tommy is jukebox god            
Say it!                                     
Break it down
Shout "Bring on the rock!"
Else Whisper "That ain't it, Chief"                 
Break it down 
```
根據 [rockstart 官方文件](https://codewithrockstar.com/docs "rockstart 官方文件") 查看語法，以及使用 [rockstart 官方網站的 Try It](https://codewithrockstar.com/online "rockstart 官方網站的 Try It") 測試 song 裡面的變數數值，且關注如 say , shout 等輸出的語法，將內容分割研究其輸出，如下：
``` text
Rocknroll is right              
Silence is wrong                
A guitar is a six-string        
Tommy's been down               
Music is a billboard-burning razzmatazz!
Listen to the music             
If the music is a guitar                  
Say "Keep on rocking!"   
```
這段只是輸出 `Keep on rocking!`，故忽略即可
```text
Listen to the rhythm
If the rhythm without Music is nothing
Tommy is rockin guitar
Shout Tommy! 
```
這裡將 `Tommy` 給予數值 `rockin guitar`，所以將以下內容丟到官方 Try it
```bash
Tommy is rockin guitar
Shout Tommy! 
```
輸出
```text
66
```
接著關注以下內容並丟到官方 Try it
```text
Music is amazing sensation 
Jamming is awesome presence
Scream Music!                   
Scream Jamming!
Tommy is playing rock           
Scream Tommy!   
They are dazzled audiences                  
Shout it!
```
輸出
```text
79
78
74
79
```
接下來以下內容須注意，由於 rockstar 語法有所更改，Rock 變成一個關鍵字，故須修改這段歌詞，把 Rock 改成非關鍵字的字串就行了，再輸入到 Try it，如下
```text
sherlock is electric heaven                     
Scream it!
```
輸出
```text
86
```
再來將以下丟到 Try it
```text
Tommy is jukebox god            
Say it!
```
輸出
```text
73
```
最後整理輸出的順序如下：
```text
66 79 78 74 79 86 73
```
寫一隻 python 把這些數字轉字元
```python
words = '66 79 78 74 79 86 73'.split()
for word in words:
  print(chr(eval(word)), end='')
```
輸出
```text
BONJOVI
```
<!-- flag -->
所以本題 FLAG 
```text
picoCTF{BONJOVI}
```
