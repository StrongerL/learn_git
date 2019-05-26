# 一个简洁的git教程  
https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664   

## 基本用法
初始化仓库（会在当前目录下生成.git文件）  
```git init  ```
  
添加文件到git仓库  
`git add 文件名`   
`git commit -m "注释"`
  
## 重要概念
git的几个重要概念  
工作区（Working Directory）  
本地可以直接看到的目录，即当前直接做出修改的目录。  
  
版本库，即.git文件夹，包括暂存区（stage 或者 index）和分支和HEAD指针。  
  
暂存区（stage 或者 index）  
`git add 文件名`，就是将文件从工作区添加到暂存区  
  
分支  
`git commit -m "注释"`，就是将工作区中的文件一起提交到当前分支，可以多次使用add向暂存区添加多个文件，然后使用commit一次将暂存区的文件提交到当前分支。  
  
## 常用命令
查看仓库状态  
`git status` 
  
查看不同，默认比较工作区和暂存区  
`git diff`  
  
## 版本回退
`git log`  
显示从最近到最远的提交日志，参数--pretty=oneline（即使用git log --pretty=oneline）可以简洁的显示历史，每行显示一次提交
如下：  
```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) 将readme.md改回readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 将readme.txt换为readme.md并将编码方式设置为GBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 添加git的几个基本概念  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df 初次提交  
```
前边的一串数字和字母是commit id（版本号），是一个SHA1计算出来的一个非常大的数字，用十六进制表示  












<br /><br /><br /><br /><br /><br /><br /><br />
初次上传
git init
git remote add origin 网址
git add .
git commit -m "注释"
// git push 网址 分支名
git push origin master

普通上传
git add .
git commit -m "注释"
// git push 网址 分支名
git push origin master

从远程库克隆，远程仓库默认名origin
git clone 网址



…or create a new repository on the command line
echo "# learngit" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/StrongerL/learngit.git
git push -u origin master

…or push an existing repository from the command line
git remote add origin https://github.com/StrongerL/learngit.git
git push -u origin master

…or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.


hh 

