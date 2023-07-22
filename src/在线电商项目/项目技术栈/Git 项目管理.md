# Git 项目管理


## 1. 基本操作(一个分支master)

```shell
## 1). 创建本地仓库(代码在本地仓库中)
    //  创建.gitignore文本, 并配置好忽略文件 
    git init   //工作台
    git add .  //暂存区
    git commit -m "init app"  //版本区 

## 2). 创建远程仓库
    New Repo
    指定仓库名
    创建		

## 3). 将本地仓库的代码推送到远程仓库
    git remote add origin url (在本地记录远程仓库的地址)   //用http的方式容易成功 还可以用GitHub Desktop
    git push -u origin main

## 4). 如果本地代码有修改, 要提交到本地仓库, 推送到仓库
    git add .
    git commit -m "xxx"
    git push

   (记住用户和密码)

## 5). 如果远程代码有修改, 要拉取到本地仓库
    git pull

## 6). 将远程仓库的代码clone到本地(生成仓库)
    git clone url
```

## 2. 多分支操作

```shell
## 1). 创建本地个人开发分支, 并推送到远程
    git checkout -b ph
    git push -u origin ph

## 3). 在个人开发分支上开发, 并推送到远程
    git add .
    git commit -m "xxx"
    git push

## 4). 根据远程个人开发分支创建本地个人开发分支
    git pull  (如果分支是在clone后创建的才需要执行)
    git checkout -b ph origin/ph //根据远程的分支 生成本地的分支

## 5). 将个人开发分支合并到main
    git checkout main
    git merge ph
    git push
```


