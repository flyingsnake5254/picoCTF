# git
Git 是一個分散式版本控制系統，用於追踪文件的更改，協同開發項目

# 基本配置
- 配置使用者名稱和電子郵件
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

- 檢查配置
```bash
git config --list
```

# 基本操作
- 初始化新的 Git repo
```bash
git init
```

- 克隆現有的 repo
```bash
git clone <repository_url>
```

- 查看 repo 狀態
```bash
# 指令
git status

# Output
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Info/git.md

nothing added to commit but untracked files present (use "git add" to track)
```

- 添加文件到暫存區
```bash
# 語法
git add <file_name>

# 範例
# 添加當前目錄下的所有更改
git add . 
```

- 提交更改
```bash
git commit -m "Your commit message"
```

# 分支操作
- 查看分支
```bash
git branch
```

- 創建新分支
```bash
git branch <branch_name>
```

- 切換分支
```bash
git checkout <branch_name>

# 創建並切換到新分支
git checkout -b <branch_name>
```

- 合併分支
切換到需要合併的目標分支，然後運行：
```bash
git merge <branch_name>
```

- 刪除分支
```bash
git branch -d <branch_name>
```

# 遠端操作
- 添加遠端 repo
```bash
git remote add origin <repository_url>
```

- 查看遠端 repo
```bash
git remote -v

# Output
origin  https://github.com/flyingsnake5254/picoCTF.git (fetch)
origin  https://github.com/flyingsnake5254/picoCTF.git (push)
```

- 推送更改到遠端
```bash
git push origin <branch_name>
```

- 從遠端 repo 拉取更改
```bash
git pull origin <branch_name>
```

# 撤銷更改
- 撤銷未 commit 的更改
```bash
git checkout -- <file_name>
```

- 重置暫存區的文件
```bash
git reset <file_name>
```


- 撤銷 commit
```bash
git revert <commit_hash>
```

- 強制重置到特定 commit
```bash
git reset --hard <commit_hash>
```


# 查看提交歷史
`git log` 用於查看提交歷史，顯示 repo 中所有的 commit 記錄
- 基本用法
```bash
# 語法
git log

# Output
commit 379f1fda55c483123a288d5bbe729450a9aacf02
Author: sherloxk <sherloxk5254@gmail.com>
Date:   Fri Jul 26 21:08:24 2024 +0800

    [add] <info> Tool Website

commit 88ae2de489192ecc6ae0526deebf41e1c198c7d5
Author: sherloxk <sherloxk5254@gmail.com>
Date:   Fri Jul 26 21:08:09 2024 +0800

    [add] <info> ssh
```

- 顯示 commit 歷史的圖形表示
```bash
git log --graph

# Output
*   commit 2996e7d9e596a8aef5fa8465194fc26dfd10fc1f (origin/optimization, master)
|\  Merge: 753cbb1 a5a7f87
| | Author: lupeichun <holmesflying222@gmail.com>
| | Date:   Thu May 9 13:23:06 2024 +0800
| |
| |     Merge branch 'dev'
| |
| * commit a5a7f87b11ded637ec2ce9c91a75bd31f936e385
| | Author: lupeichun <holmesflying222@gmail.com>
:...skipping...
```

- 顯示每個 commit 的完整差異
```bash
# 語法
git log -p

# Output
commit 379f1fda55c483123a288d5bbe729450a9aacf02
Author: sherloxk <sherloxk5254@gmail.com>
Date:   Fri Jul 26 21:08:24 2024 +0800

    [add] <info> Tool Website

diff --git a/Info/Tool Website.md b/Info/Tool Website.md
index 5fddfb3..b7e58bc 100644
--- a/Info/Tool Website.md
+++ b/Info/Tool Website.md
@@ -1 +1,2 @@
-##Hash 爆破工具(https://github.com/flyingsnake5254/picoCTF.git)
\ No newline at end of file
+## Hash 爆破工具
+- [Crack Station](https://crackstation.net/)
\ No newline at end of file

...
```

- 顯示簡短摘要
```bash
git log --oneline

# Output
760466a (HEAD -> master, origin/master, origin/HEAD) [update] binary search
69d95a7 [update] binary search
379f1fd [add] <info> Tool Website
88ae2de [add] <info> ssh
b8c1c3b update
d98b551 update
```

- 限制顯示的 commit 數量
```bash
# 語法
git log -n <number>

# 範例
# 只顯示最近的 3 次提交
git log -n 3
```

- 顯示指定作者的 commit
```bash
# 語法
git log --author=<author_name>

# 範例
git log --author=Alice
```

- 按日期範圍顯示 commit
```bash
# 語法
git log --since=<date> --until=<date>

# 範例
# 顯示從 2021-01-01 到 2021-12-31 的 commit
git log --since=2021-01-01 --until=2021-12-31
```

# 查看差異
