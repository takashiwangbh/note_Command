# git基本理论
四个工作区域：working directory、stage/index、repository/git directory、remote directory    (工作目录，暂存区，资源库，远程仓库) 

隐藏文件:.git：index和head指向的本地仓库  

git工作流程：*1*在工作目录中添加和修改文件*2*将需要进行版本管理的文件放入暂存区域（git add）*3*将暂存区域的文件提交到git仓库(git commit)；所以git管理有三种状态：已修改(modified)、已暂存（staged）、已提交（committed）  

# git的四种状态
untracked：未跟踪，没有加到git库，通过git add状态变为staged
unmodify：入库未修改，如果被修改则变为modified，如果使用git rm移出版本库，则成为untracked文件
modified：文件已修改，通过git add可进入staged状态，使用git checkout则丢弃修改返回到unmodify
staged：暂存状态，git commit则将文件修改同步到库中，git reset HEAD filename取消暂存，文件状态变为modified 

# git基本操作
#### 配置基本用户信息
```code
git config --global user.name <username>
git config --global user.email <emailaddress>
```

#### 创建一个新仓库
```code
git init
```

#### 从远程服务器克隆一个仓库
```code
git clone<远程仓库的url>
```

#### 显示当前的工作目录下的提交文件状态
(类似gitkraken)中右方窗口显示的信息
```code
git status
```

#### 查看修改记录
```code
git diff
```

#### 将指定文件Stage（标记为将要被提交的文件）
```code
git add<文件路径>
```

#### 将指定文件Unstage（取消标记为将要被提交的文件）
```code
git reset<文件路径>
```

#### 创建一个提交并提供提交信息
```code
git commit -m "提交信息"
```

#### 显示一个提交历史
 （类似于gitkraken中间窗口中显示的提交历史）
```code
git log
```

#### 向远程仓库推送（push）
```code
git push
```

#### 从远程仓库拉取（pull）
```code
git pull
```

#### 修改上一个提交
```code
git commit --amend -m "新的提交信息"
``` 

#### 查看所有分支
```code
git branch
```
 
#### 创建分支
```code
git checkout -b <分支名字>
```
 
#### 切换分支
```code
git branch <分支名字>
```

#### 重命名分支 
```code
git branch -m <旧名字> <新名字>
```
 
 #### 删除分支
 ```code
git branch -d <分支名字>
```

#### 将分支变基（rebase）到master（注：变基需要先切换到分支）
```code
git checkout <分支名字>
git rebase master
```

#### 使用快进（fast-forward）将分支合并到master
```code
git checkout <分支名字>
git merge --ff-only master
```

#### 中止这一次提交的合并（当遇到冲突）
```code
git merge --abort
```

#### 将未提交的修改暂存（stash）
```code
git stash save "输入信息"
```

#### 将上一个暂存的修改恢复并从暂存列表中删除
```code
git stash pop
```

#### 撤销指定的提交（在硬盘上）
```code
git checkout <文件名>
```

#### 撤销git add的操作把文件从暂存区移除
```code
git reset <文件名>
```

#### 撤销所有的修改（硬盘和暂存区的修改）（HEAD表示最近的一次commit）
```code
git、 checkout HEAD <文件名>
```

#### 撤销回退一个git commit 操作
```code
git reset --soft HEAD~1
```

#### 同时撤销回退一个git add 和git commit操作
```code
git reset HEAD~1
```

#### 撤销旧提交（revert不会修改旧提交历史，而是在工作树中生成与之前提交完全相反的修改）
```code
git revert <旧提交的hash>
```

#### 查看本地仓库中的所有操作
```code
git reflog
```

#### 强迫push(个人分支可以使用，公有分支尽量别使用)
```code
git push -f
```


________________
_____________
# git bash
```code
cd ..   /退回上一级
cd      /改变目录
pwd     /显示路径
is      /列出当前目录所有文件
touch   /新建文件
rm      /删除文件
mkdir   /新建文件夹
rm -r   /删除文件夹
mv      /移动文件
reset   /初始化终端（清屏）
clear   /清屏
history /查看命令历史
help    /帮助
exit    /退出
#       /注释
``` 
 
  # 忽略文件
在主目录下建立.gitignore文件，有如下规则
  ```code
#为注释
*.txt       #忽略所有.txt文件
!lib.txt    #但lib.txt除外
/temp       #仅忽略项目根目录下的todo文件，但是不包括其他目录temp
build/      #忽略build/目录下的所有文件
doc/*.txt   #会忽略doc/notes.txt但不包括doc/server/arch.txt

  ```
   
# git 分支
```code
git branch                            #列出所有本地分支
git branch -r                         #列出所有远程分支
git branch [branchname]               #新建一个分支，但仍然停留在当前分支
git checkout -b [branch]              #新建一个分支并切换到该分支
git merge [branch]                    #合并指定分支到当前分支
git branch -d [branchname]            #删除分支
git push origin --delete [branchname] #删除远程分支
git branch -dr [remote/branch]        #删除远程分支
``` 

# 实操1
```code
cd ss 
git clone https://github.com/takashiwangbh/c-.git
cd c-
touch test.md
git add .   #添加所有文件到暂存区
git status  #显示文件信息，显示 有文件新添加到暂存区
git commit -m "just a test"     #提交暂存区中的内容到本地仓库
git push        #提交到远程仓库
``` 

# 实操2
```code
//在项目里创建自己的分支
git clone https://github.com/takashiwangbh/code_learning.git
git checkout -b my-test
git diff
git add test.md
git commit -m "just a test 2"
git push origin my-test
//如果main远端有更新，同步到我的分支,将我的支线的更新合并到最新的main里
git checkout main
git pull origin master
git checkout my-test
git rebase main
git push -f origin my-test
//删除本地分支
git checkout main
git branch -D my-test
//将远端和本地代码同步
git pull origin master

``` 

 -f 强行推送

 # 0526