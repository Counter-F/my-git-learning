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

合并分支（分支注入到父节点）
git merge <branchname>

## 涉及到问题及冲突
1. 主分支
2. 不同分支之间是隔离的
    - 子分支创建时复制父分支的所有内容（深拷贝）
    - 父分支修改之后子分支内容不会改变
    - 子分支汇入修改后的父分支，可能导致部分地方产生冲突
3. 不同子分支之间涉及的内容




新增加内容真的好吗