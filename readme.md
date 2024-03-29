# git 笔记
## 基本概念

### 工作区（Working Directory）

本地可以直接看到的目录，即当前直接做出修改的目录。   

### 暂存区（stage 或者 index）

`git add 文件名`，就是将文件从工作区添加到暂存区  

### 分支

`git commit -m "注释"`，就是将工作区中的文件一起提交到当前分支，可以多次使用add向暂存区添加多个文件，然后使用commit一次将暂存区的文件提交到当前分支。  

### 版本库

即.git文件夹，包括暂存区（stage 或者 index）和分支和HEAD指针。 

## 基本用法

### `git init`

初始化仓库（会在当前目录下生成.git文件），将当前目录初始化为一个git仓库。

### `git add 文件名`

将文件从工作区添加到暂存区。

### `git commit -m "注释"`

将文件从暂存区提交到git仓库当前版本。

### `git status`

查看仓库状态  

### `git diff`

查看不同，默认比较工作区和暂存区

### `git rm 文件名`

相当于`rm 文件名` + `git add 文件名` ，即将本地文件删除之后，将这种修改从工作区提交到暂存区。

### `git rm --cached 文件名`

删除git中的文件，但是在本地保留该文件。

## 撤销修改

### `git restore 文件名`

撤销工作区的修改，如果暂存区有数据，就回退到暂存区，如果暂存区没有数据，就回退到当前分支最新的commit。  

### `git restore --staged  文件名`

撤销暂存区的修改，会直接丢弃。  

### `git reset --hard HEAD`

撤销工作区和暂存区的修改。  

### `git revert 位置`

远程。

## 版本回退

### `HEAD`

HEAD 是一个对当前检出记录的符号引用 —— 也就是指向你正在其基础上进行工作的提交记录。HEAD 一般指向当前的分支，HEAD 也可以直接指向提交记录，我们称为分离的 HEAD。

HEAD上一次commit（不包括reset）为 HEAD^ ，上上一次为 HEAD^^ ，上10次为 HEAD~10 。  

有时，提交记录会有2个父节点，HEAD^ 默认指向第一个父节点，HEAD^2 指向另一个。

此外还可以进行链式操作，如`git checkout <branch_name>^2~3^`。

### `git log`

显示从最近到最远的commit日志，参数--pretty=oneline（即使用git log --pretty=oneline）可以简洁的显示历史，每行显示一次提交，如下：  

```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) 将readme.md改回readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 将readme.txt换为readme.md并将编码方式设置为GBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 添加git的几个基本概念  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df 初次提交  
```
前边的一串数字和字母是commit id（版本号），是一个SHA1计算出来的一个非常大的数字，用十六进制表示。  

### `git reset`

更改到指定版本，工作区和版本库（版本库是通过更改HEAD指针）都会更改

### `git reset --hard HEAD`

是回退到版本库最新的一次提交

### `git reset --hard commit-id`

回退到指定commit id的版本commit-id不需要写全，写前几位就可以。也可以不是commit-id，只要是git可以识别出的位置即可。

### `git reflog`

显示版本更改的所有日志，包括commit和reset，如果我们回退到之前的版本又想要再回到在最新的版本，就可以使用这个命令来查找到对应的commit id并使用`git reset`命令换到指定版本。  

## 远程仓库
### SSH密钥

1. 创建SSH密钥（如果已经有了可以跳过）

   `ssh-keygen -t rsa -C "邮件地址"` ，该命令在用户主目录里生成.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

2. 登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容。github允许有多个SSH Key。

### 添加远程库

1. github上创建远程库（不使用github自建服务器也可以）

2. 在本地创建git仓库（已有仓库则可以跳过这一步）
   
   ```shell
   git init
   git add .
   git commit -m "注释"
   ```
   
3. 在本地git版本库中添加远程库网址，网址有多个，不同的网址对应不同的传输协议。

   ```shell
   git remote add origin 网址
   ```

4. 将本地库push到远程库

   ```shell
   # 初次push使用
   git push -u origin master
   # 之后使用
   git push origin master
   ```


### 从远程库克隆

1. `git clone 网址`

2. 将本地库push到远程库

   ```shell
   # 初次push使用
   git push -u origin master
   # 之后使用
   git push origin master
   ```

`git remote [-v]`，查看远程库信息。  


## 分支
### 分支管理基础

#### `git branch`

查看分支，当前所在分支前有一个*符号。

#### `git branch 分支名`

创建分支。

#### `git checkout 分支名`

切换分支。切换分支时最好保证git的状态是clean，否则可能会出现如下几种情况：

1. 未管理/未添加到暂存区/未提交 的修改与切换的目的分支有冲突，切换失败
2. 未管理/未添加到暂存区/未提交 的修改与切换的目的分支无冲突，切换成功。如果在新分支上放弃了上述修改，切回原分支后，这些修改也会丢失。
3. 简而言之，切换分支只会恢复目的分支提交过的修改。

#### `git checkout -b 分支名`

创建新的分支并切换到新的分支，等同于`git branch 分支名`  +  `git checkout 分支名`。

#### `git merge 分支名`

当前分支合并指定分支。

#### `git rebase 分支名`

将当前分支的修改以线性的方式合并到其他分支。

#### `git branch -d 分支名`

删除指定分支，如果还未合并就要删除，需要使用`git branch -D 分支名`。

### 移动分支

#### `git checkout <commit_id>`

让 HEAD 直接指向提交记录。

#### `git branch -f 分支名 位置`

强制修改分支位置，如`git branch -f main HEAD~3`。

### 处理冲突

两个分支如果出现冲突，那么执行`git merge 分支名`时会出现错误，可以执行`git merge --abort`放弃合并，也可以手动解决冲突后执行`git add 文件名`+`git commit -m "注释“`命令完成合并。
`git log --graph`命令可以看到分支合并图。

### 远程分支

#### `git fetch`

下载远程仓库数据。

#### `git merge 远程分支名`

合并远程分支。

#### `git pull 远程分支名`

下载并合并远程分支。

#### `git push`

推送本地记录。

#### `git push origin --delete 分支名`  

删除远程仓库的指定分支，不会删除本地的分支。  

#### `git checkout -b 本地分支名 远程分支名`

在本地新建远程分支并追踪远程分支。

#### `git branch -u 远程分支名 本地分支名`

指定本地分支追踪远程分支。

#### push/fetch 参数

##### git push 远程仓库名 位置

如`git push origin <source(local)>:<destination(local)>`。

如果没有`<source(local)>:`，表明将本地的同名分支推送到远程分支。如`git push origin master`就是将本地的master分支推送到远程仓库origin的master分支。

如果没有`<source(local)>`，则会删除远程的分支。如`git push origin :side`会删除远程仓库origin的side分支。

##### git fetch 远程仓库名 位置

如`git fetch origin <source(remote)>:<destination(remote)>`。

如果没有`<source(remote)>:`，表明将远程的的同名分支下载到到本地的远程分支。如`git fetch origin master`就是将远程的master分支下载到本地的origin/master分支。

如果没有`<source(remote)>`，则会在本地创建一个分支。

如果没有参数，即`git fetch`，则会下载所有分支。

### 整理提交记录

#### `git cherry-pick 位置 提交记录（1~n个）`

cherry-pick 把若干个指定的提交记录提交到当前记录之下。

#### `git rebase -i`

交互式rebase。

### BUG分支

当前分支任务未完成因此不能commit，但是需要切换到其他分支，可以使用`stash`命令。  

#### `git stash`

保存当前工作空间。  

#### `git stash list`  

查看当前所有的stash，序号0代表最新的stash。  

#### `git stash pop`  

默认恢复最新的stash并删除，相当于`git stash apply`（恢复stash） + `git stash drop`（删除stash）。也可以在该命令后添加stash序号恢复指定stash。

## 标签

### `git tag`

查看标签信息。  

### `git tag 标签名 [commit id]`  

为指定的commit打标签，默认打在最新的commit上。   

### `git tag -a 标签名 -m "注释" [commit id]`  

增加注释。  

### `git show 标签名`  

查看指定标签的信息。  

### `git tag -d 标签名`  

删除指定标签。  

### `git push origin 标签名`  

推送标签到远程，也可以使用`git push origin --tags`一次性推送所有标签。  

### `删除远程标签`  

首先使用`git tag -d 标签名`删除本地标签，然后使用`git push origin :refs/tags/标签名`删除远程标签。  


## 自定义git
1. .gitignore文件

   让git忽略指定文件。  

2. `cd > .gitignore`

   新建.gitignore文件。  

3. 编辑.gitignore文件

   每行一个或者一类文件，可以使用正则，可以参考该[网站](https://github.com/github/gitignore)。  

4. `git add -f 文件名`

   强制添加被忽略的文件。  

5. `git checkout-ignore -v 文件名`

   查看.gitinore中的哪个地方忽略了指定文件。  

6. `git config [--global] alias.别名 原命令`

   配置别名，不加`--global`则是只针对当前仓库，添加则是所有仓库。每个仓库的Git配置文件都放在.git/config文件中，别名就在[alias]后面，要删除别名，直接把对应的行删掉即可。  

## 参考资料

- [https://www.liaoxuefeng.com/wiki/896043488029600](https://www.liaoxuefeng.com/wiki/896043488029600)
- [https://github.com/pcottle/learnGitBranching](https://github.com/pcottle/learnGitBranching)