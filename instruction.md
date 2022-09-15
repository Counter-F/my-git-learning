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


修改并提交的流程

文件 -> [git add] -> 暂存区 -> [git commit] -> 仓库

1. git add <file>/ -A 
    - -A 表示全部修改过的文件都

2. git commit -m '本次修改的注解信息'

查看commit日志
git log --stat


git add <file> 之后，想要撤回

1. git checkout <file>


git commit 之后