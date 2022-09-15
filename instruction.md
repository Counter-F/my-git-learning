git 多人控制和版本控制

初始化

git init  % 把文件夹变成repository

下载网上的repository
git clone 【url】

提交
commit 对于仓库修改提交之后

分支
branch 不同人可以分别开发同一个repository部分，每个branch合并到main中就可以得到更新的main/master
branch可以有子branch，因此组织成树形结构
main
|_branch1
|       |_branch11
|_branch2
|
提交时候是向上提交（提交汇入到父节点）



## 修改并管理历史记录

修改并提交的流程

文件 -> [git add] -> 暂存区 -> [git commit] -> 仓库

1. git add <file>/ -A                |  vs code中更改栏点 '+'号
    - -A 表示全部修改过的文件都

2. git commit -m '本次修改的注解信息'   |  vscode 中输入message注解，并点击提交 

查看commit日志                         | vscode中点击COMMITS查看每次的提交历史记录
git log --stat


git add <file> 之后，想要撤回          | vscode更改栏中点击-号

1. git checkout <file>


git commit 之后，想要撤回             | vscode中COMMITS，选择要删掉的某一次提交，右键单击选择undo commit； 之后在提交栏中点击-号

1. git reset Head^1 重定位到head的上1个（head就是当前，因此要定位到head的上x个位置），并放回暂存区
2. git checkout -A

提交半年了，还想找某一个找某一个内容               | 从 FILE HISTORY中找到某一次的历史记录记录，复制粘贴到最近的文件夹（即覆盖掉现有记录），然后重新修改


## 分支（协同开发） Branch

从当前节点新建分支
git checkout -b <branchname>

列举所有分支
git branch

单纯的切换到某个分支
git checkout <branchname>

删掉特定分支
git branch -D <branchname>

合并分支（分支注入到父节点，需要从父节点分支（master分支）中执行此命令，branchname为子节点的分支名）
git merge <branchname>

修改当前分支名字
git branch -M <new_branchname>

## 涉及到问题冲突以及管理
1. 主分支是一切的起点和终点，建议branch都是以主分支作为父节点，新建一个branch
2. 不同分支之间是隔离的
    - 子分支创建时复制父分支的所有内容（深拷贝）
    - 父分支修改之后子分支内容不会改变
    - 子分支汇入修改后的父分支，可能导致部分地方产生冲突
3. 不同子分支之间涉及的内容
4. git merge --abort 当出现冲突时（其他子节点和该子节点修改了同一行内容），如果不知道应该使用哪个版本，那就用此命令放弃此次合并操作
5. merge一个子分支之后，该子分支就没有用了，就可以删掉了。 
6. 每次新的协同任务出现后，都是根据最新的master分支或者某个子分支重新进行创建子分支来分配工作的。


## 推送和拉取

1. 需先在GitHub上建立一个仓库，并将本地仓库和远程的仓库用命令建立一个连接

    git remote add origin https://github.com/Counter-F/my-git-learning.git  # 和远程的repository建立连接
    git branch -M main  [当前分支名字修改位main，美国人权运动，master有主人的意思，因此GitHub不许用master了]
    git push -u origin main  第一次推送使用的命令

2. 建立好连接之后，以后的操作不需要重复建立连接了，直接执行

    git push 推送当前最新的分支，提交到远程服务器上

    git pull 拉取远程最新的分支，更新本地仓库

    这两个命令都不需要任何其他参数了！！！


推送