# Chapter 0. 常用命令
1. 通过`git init`命令把这个目录变成Git可以管理的仓库：
2. 用命令`git add`告诉Git，把文件添加到仓库：
3. 用命令`git commit`告诉Git，把文件提交到仓库, `-m`后面输入的是本次提交的说明

 - `git status`命令可以让我们时刻掌握仓库当前的状态
 - `git diff`就是查看difference
 - `git log`命令显示从最近到最远的提交日志
 - Git中，用`HEAD`表示当前版本，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，往上100个版本`HEAD~100`。
 - 回退到上一个版本，就可以使用`git reset`命令
 ```plain
git reset --hard HEAD^
`--hard`会回退到上个版本的已提交状态
`--soft`会回退到上个版本的未提交状态
`--mixed`会回退到上个版本已添加但未提交的状态。
```
- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`
- 用`git reflog`查看命令历史，以便确定要回到未来的哪个版本


## Git 版本库

- Git和其他版本控制系统如SVN的一个不同之处就是有暂存区的概念
- Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

1. 第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；
2. 第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。
![[repo.png]]
- 我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。

# Chapter 1. Repositories and Branches
- The best way to get one is by using the **git-clone** command to download a copy of an existing repository.
```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```

- The clone command creates a new directory named after **the project** . 
- After you cd into this directory, you will see that it contains a copy of the project files, called the [working tree](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_working_tree), together with a special top-level directory named `.git`, which contain**s all the information about the history of the project**.

- Git is best thought of as a tool for **storing the history of a collection of files**. It stores the history **as a compressed collection of interrelated snapshots of the project’s contents**. In Git each such version is called a [commit](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_commit).
- Those snapshots aren’t necessarily all arranged in a single line from oldest to newest; instead, work may simultaneously proceed along parallel lines of development, called [branches](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_branch), which may merge and diverge.
- A single Git repository can track development on multiple branches. It does this by keeping a list of [heads](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_head) which reference **the latest commit on each branch**; the [git-branch(1)](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-branch.html) command shows you **the list of branch heads**:
```
$ git branch
* master
```

- Most projects also use [tags](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_tag). Tags, like heads, are references into the project’s history, and can be listed using the [git-tag(1)](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-tag.html) command:
```
$ git tag -l
v2.6.11
v2.6.11-tree
v2.6.12
v2.6.12-rc2
v2.6.12-rc3
v2.6.12-rc4
v2.6.12-rc5
v2.6.12-rc6
v2.6.13
...
```

- Create a new branch head pointing to one of these versions and check it out using [git-switch(1)](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-switch.html)
```
$ git switch -c new v2.6.13
```

