## 配置基本用户信息
```code
git config --global user.name <username>
git config --global user.email <emailaddress>
```

## 创建一个新仓库
```code
git init
```

## 从远程服务器克隆一个仓库
```code
git clone<远程仓库的url>
```

## 显示当前的工作目录下的提交文件状态
#### (类似gitkraken)中右方窗口显示的信息
```code
git status
```

## 将指定文件Stage（标记为将要被提交的文件）
```code
git add<文件路径>
```

## 将指定文件Unstage（取消标记为将要被提交的文件）
```code
git reset<文件路径>
```

## 创建一个提交并提供提交信息
```code
git commit -m "提交信息"
```

## 显示一个提交历史
#### （类似于gitkraken中间窗口中显示的提交历史）
```code
git log
```

## 向远程仓库推送（push）
```code
git push
```

## 从远程仓库拉取（pull）
```code
git pull
```
