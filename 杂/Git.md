# Git

#### 分布式版本控制

每个人都有全部代码，本子看到历史记录，不会因为服务器损坏导致不能工作

![image-20220926085547269](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926085547269.png)

![image-20220926085607886](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926085607886.png)

Repository本地的代码库，存放数据的地方，版本数据

workspace工作区，平时存放代码的地方

index（stage），存放临时改动

remote，顾名思义

![image-20220926090018679](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926090018679.png)

![image-20220926090221208](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926090221208.png)

#### 命令

```
git init//初始化
ls
```

![image-20220926091741583](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926091741583.png)

```
git init//初始化
git clone [url]//克隆一个到本地
git status//看看文件有没有被跟踪，添加到暂存区里面，就变成跟踪
git add . //添加所有文件到暂存区
git commit -m"注释消息内容" //提交暂存区的内容到本地仓库
git log//看一看commit的记录
git reset -hard commit_id//恢复到之前
git pull//从远层把代码拿过来

使用分支
git branch//显示分支
git branch new_branch_Id//创建一个分支，带主分支上进行更改
git checkout -b new_branch_Id//，创建一个分支，并转移到新分支
git checkout name//转换分支
//回到主分支之后代码是一样的
git merge new_feature//把新的代码改到主分支
git checkout -D id //删除分支
git checkout //检测不同的分支
```

主目录下面建立.gitignore文件

![image-20220926092351125](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926092351125.png)

![image-20220926092545630](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926092545630.png)

