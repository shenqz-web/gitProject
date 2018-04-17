# gitProject
git 学习中

学习地址https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E5%8F%96%E5%BE%97%E9%A1%B9%E7%9B%AE%E7%9A%84-Git-%E4%BB%93%E5%BA%93

克隆远程仓库：git  clone  [url] 克隆远程仓库到本地
全局配置用户名： git config --global  user.name 全局配置用户名和邮箱
全局配置邮箱： git config --global user.email
查看所有配置项：git config --list 

	Git diff
　　 　　用于比较两次修改的差异

　　　　1.1 比较工作区与暂存区

　　　　　　git diff 不加参数即默认比较工作区与暂存区

　　　　1.2 比较暂存区与最新本地版本库（本地库中最近一次commit的内容）

　　　　　　git diff --cached  [<path>...] 

　　　　1.3 比较工作区与最新本地版本库

　　　　　　git diff HEAD [<path>...]  如果HEAD指向的是master分支，那么HEAD还可以换成master

　　　　1.4 比较工作区与指定commit-id的差异

　　　　　　git diff commit-id  [<path>...] 

　　　　1.5 比较暂存区与指定commit-id的差异

　　　　　　git diff --cached [<commit-id>] [<path>...] 

　　　　1.6 比较两个commit-id之间的差异

　　　　　　git diff [<commit-id>] [<commit-id>]

　　　　1.7 使用git diff打补丁

　　　　　　git diff > patch //patch的命名是随意的，不加其他参数时作用是当我们希望将我们本仓库工作区的修改拷贝一份到其他机器上使用，但是修改的文件比较多，拷贝量比较大，

　　　　　　此时我们可以将修改的代码做成补丁，之后在其他机器上对应目录下使用 git apply patch 将补丁打上即可

　　　　　　git diff --cached > patch //是将我们暂存区与版本库的差异做成补丁

　　　　　　  git diff --HEAD > patch //是将工作区与版本库的差异做成补丁

　　　　　　git diff Testfile > patch//将单个文件做成一个单独的补丁

　　　　拓展：git apply patch 应用补丁，应用补丁之前我们可以先检验一下补丁能否应用，git apply --check patch 如果没有任何输出，那么表示可以顺利接受这个补丁

　　　　　　　另外可以使用git apply --reject patch将能打的补丁先打上，有冲突的会生成.rej文件，此时可以找到这些文件进行手动打补丁　 



本地初始化一个Git仓库: git init

查看当前状态： git status

添加到暂存区： git add (file1 file2 file3)

全部添加到暂存区： git add .  负责把工作区的新增或修改的文件添加到暂存区

添加到仓库： git commit -m "注释" 负责把暂存区的文件添加到版本库

工作区直接添加到仓库：  git commit -a -m "注释"

查看工作区和版本库的区别: git diff HEAD (file)  命令可以查看工作区和版本库里面最新版本的区别

输出仓库版本记录： git log

版本回退：git reset --hard HEAD^ 上一个版本就是HEAD^，上上一个版本就是HEAD^^ 100个版本写100个^比较容易数不过来，所以写成HEAD~100

指定回到那个版本： git reset --hard (commit id)   git reset --hard 3628164

查看命令历史： git reflog  以便确定要回到未来的哪个版本

查看分支：git branch

创建分支：git branch (name)

切换分支：git checkout (name)

创建+切换分支：git checkout -b (name)

合并某分支到当前分支：git merge (name)

删除分支：git branch -d (name)