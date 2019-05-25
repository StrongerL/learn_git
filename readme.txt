Git is a distributed version control system.
Git is free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.


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




