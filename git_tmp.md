# 笔记

[https://github.com/pcottle/learnGitBranching](https://github.com/pcottle/learnGitBranching)

```shell
# 提交
git commit -m "commment"

# ============== 分支 =================
# 创建分支
git branch <branch_name>
# 切换分支
# 切换分支时最好保证git的状态是clean，否则可能会出现如下几种情况：
# 未管理/未添加到暂存区/未提交 的修改与切换的目的分支有冲突，切换失败
# 未管理/未添加到暂存区/未提交 的修改与切换的目的分支无冲突，切换成功。如果在新分支上放弃了上述修改，切回原分支后，这些修改也会丢失。简而言之，切换分支只会恢复目的分支提交过的修改。
git checkout <branch_name>
# 创建并切换分支
git checkout -b <branch_name>
# 当前分支合并其他分支
git merge <branch_name>
# 将当前分支的修改以线性的方式合并到其他分支
git rebase <branch_name>

# ================== 移动分支 ==============
# HEAD
# HEAD 是一个对当前检出记录的符号引用 —— 也就是指向你正在其基础上进行工作的提交记录。
# HEAD 一般指向当前的分支
# HEAD 也可以直接指向提交记录，我们称为 分离的 HEAD
# 让 HEAD 直接指向提交记录
git checkout <commit_id>

# 相对引用
# 使用 ^ 向上移动 1 个提交记录， ^^ 向上移动 2 个提交记录，以此类推
# 使用 ~<num> 向上移动多个提交记录，如 ~3
# 可以应用到分支名和 HEAD 上，不可以应用到提交记录
git checkout <branch_name>^
git checkout HEAD^
git checkout <branch_name>~<num>
git checkout HEAD~<num>
# ^ 的另一种用法，一个分支branch如果有2个父节点，branch^ 默认选择第一个，如果要选择另一个需要 branch^2
git checkout <branch_name>^2
# 链式操作
git checkout <branch_name>^2~3^

# 强制修改分支位置
git branch -f <branch_name> <location>
git branch -f main HEAD~3


# ============= 撤销修改 ===================
# 本地
git reset <location>
# 远程
git revert <location>


# 查看日志
git log



# ================= 整理提交记录 =====================
# cherry-pick 把若干个指定的提交记录提交到当前记录之下
git cherry-pick <location>...
# 交互式rebase
git rebase -i


# ================ 标签 =============================
git tag <tag_name> <location>




# ===================== 远程仓库 ======================
# 本地的远程分支只能代表远程分支的状态，
# 在本地无法修改远程分支的位置，除非改变了远程的分支。

# 克隆远程仓库
git clone
# 下载远程仓库数据
git fetch
# 合并远程分支
git merge <origin_branch_name>
# 下载并合并远程分支
git pull <origin_branch_name>
# 推送本地记录
git push

# 追踪远程分支
git checkout -b <local_branch_name> <origin_branch_name>
git branch -u <origin_branch_name> <local_branch_name>

# push/fetch 参数
git push <remote> <place>
git push origin <source(local)>:<destination(local)>
git fetch <remote> <place>
git fetch origin <source(remote)>:<destination(remote)>
git fetch # 下载所有分支
# 不指定source
git push origin :side      # 删除远程分支
git fetch origin :bugFix   # 在本地创建一个分支


```



