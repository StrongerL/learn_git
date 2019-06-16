# 一个简洁的git教程  
https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664   
  
## 重要概念
git的几个重要概念  
工作区（Working Directory）  
本地可以直接看到的目录，即当前直接做出修改的目录。   
  
暂存区（stage 或者 index）  
`git add 文件名`，就是将文件从工作区添加到暂存区  
  
分支  
`git commit -m "注释"`，就是将工作区中的文件一起提交到当前分支，可以多次使用add向暂存区添加多个文件，然后使用commit一次将暂存区的文件提交到当前分支。  
  
版本库  
即.git文件夹，包括暂存区（stage 或者 index）和分支和HEAD指针。 
  
## 基本用法
`git init`  
初始化仓库（会在当前目录下生成.git文件），将当前目录初始化为一个git仓库。    
  
`git add 文件名`  
将文件从工作区添加到暂存区。  
  
`git commit -m "注释"`  
将文件从暂存区提交到git仓库当前版本。  
  

## 常用命令
`git status`  
查看仓库状态  
  
`git diff`  
查看不同，默认比较工作区和暂存区  
  
## 版本回退
`HEAD`  
在git中使用HEAD代标版本库中当前版本，HEAD上一次commit（不包括reset）为HEAD^，上上一次为HEAD^^，上10次为HEAD~10。  
  
`git log`  
显示从最近到最远的commit日志，参数--pretty=oneline（即使用git log --pretty=oneline）可以简洁的显示历史，每行显示一次提交
如下：  
```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) 将readme.md改回readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 将readme.txt换为readme.md并将编码方式设置为GBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 添加git的几个基本概念  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df 初次提交  
```
前边的一串数字和字母是commit id（版本号），是一个SHA1计算出来的一个非常大的数字，用十六进制表示。  
  
`git reset`  
更改到指定版本，工作区和版本库（版本库是通过更改HEAD指针）都会更改  
`git reset --hard HEAD`是回退到版本库最新的一次提交  
`git reset --hard commit id`回退到指定commit id的版本commit id不需要写全，写前几位就可以。
  
`git reflog`  
显示版本更改的所有日志，包括commit和reset，如果我们回退到之前的版本又想要再回到在最新的版本，就可以使用这个命令来查找到对应的commit id并使用`git reset`命令换到指定版本。  
  
## 撤销修改
`git checkout -- 文件名`  
撤销工作区修改，两种情况：  
暂存区不为空，回退到暂存区的状态；   
暂存区为空，回退到版本库当前状态。  
  
`git reset HEAD 文件名`  
丢弃暂存区的修改。  
  
`git reset --hard HEAD`  
已经提交到版本库，可以使用`git reset`回退到之前版本。  
  
## 删除文件
`git rm 文件名`  
相当于`rm 文件名` + `git add 文件名` ，即将本地文件删除之后，将这种修改从工作区提交到暂存区。  

`git rm --cached 文件名`  
删除git中的文件，但是在本地保留该文件。  
  
## 远程仓库
**SSH密钥**  
1. 创建SSH密钥（如果已经有了可以跳过）  
`ssh-keygen -t rsa -C "邮件地址"` ，该命令在用户主目录里生成.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
2. 登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容。github允许有多个SSH Key。
  
**添加远程库**  
1. github上创建远程库（不使用github自建服务器也可以也可以）
2. 在本地创建git仓库（已有仓库则可以跳过这一步）
   `git init`  
   `git add .`  
   `git commit -m "注释"`    
3. 在本地git版本库中添加远程库网址，网址有多个，不同的网址对应不同的传输协议。   
   `git remote add origin 网址 `  
4. 将本地库push到远程库
   初次push使用`git push -u origin master`  
   之后使用`git push origin master`  
  
**从远程库克隆**  
1. `git clone 网址`  
2. 将本地库push到远程库
   初次push使用`git push -u origin master`  
   之后使用`git push origin master`   
  
`git remote [-v]`  
查看远程库信息。  

  
## 分支管理
**分支管理基础**  
`git branch`  
查看分支，当前所在分支前有一个*符号。  
  
`git checkout -b 分支名`  
创建新的分支并切换到新的分支，等同于`git branch 分支名`（创建新的分支） + `git checkout 分支名`（切换到指定分支）。  
  
`git merge 分支名`  
将当前分支和指定分支合并。  
  
`git branch -d 分支名`  
删除指定分支，如果还未合并就要删除，需要使用`git branch -D 分支名`   
  
  
**分支冲突处理**  
两个分支如果出现冲突，那么执行`git merge 分支名`时会出现错误，可以执行`git merge --abort`放弃合并，也可以手动解决冲突后执行`git add 文件名`+`git commit -m "注释“`命令完成合并。
`git log --graph`命令可以看到分支合并图。  
  
  
**分支合并的方式**  
默认为Fast Forward，即无冲突的话直接更改指针，不会产生commit。  
可以使用`git merge --no-ff`强制禁用Fast Forward，在合并时会产生一次commit。  
  
  
**BUG分支**  
当前分支任务未完成因此不能commit，但是需要切换到其他分支，可以使用`stash`命令。  

`git stash`  
保存当前工作空间。  

`git stash list`  
查看当前所有的stash，序号0代表最新的stash。  

`git stash pop`  
默认恢复最新的stash并删除，相当于`git stash apply`（恢复stash） + `git stash drop`（删除stash）。也可以在该命令后添加stash序号恢复指定stash。


