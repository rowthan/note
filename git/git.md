# 全局设置
```sh
$ git config user.email "rhran@travelsky.com"
$ git config user.name ranronghua
$ git config --global credential.helper store
$ git config --global core.autocrlf false
```
>以上分别是邮箱，用户名，密码自动保存，禁止自动换行的设置  

# 克隆远程仓库

```sh
$ git clone url
Cloning into 'efront'...
warning: You appear to have cloned an empty repository.
Checking connectivity... done.
```

# 查看状态
```sh
$ cd efront

$ git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```

# 创建文件夹及文件
```sh
$ mkdir git

$ cd git

$ vi git.basic.md
```


    ```

# 再次查看状态    
```sh
$ cd ../

$ ll
total 0
drwxr-xr-x 1 Andy 197121 0 十月 19 01:53 git/

$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        git/

nothing added to commit but untracked files present (use "git add" to track)
```


# 将文件添加到git暂存区，以便git跟踪
```sh
$ git add git

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   git/git.basic.md
```
# 提交文件到本地仓库
```sh
$ git commit -m "add files"
[master d55df17] add files
 1 file changed, 75 insertions(+)
 create mode 100644 git/git.basic.md

 $ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
 ```
 > `-m` 后面是提交的文件注释

# 推送文件到远程仓库
```sh
$ git push --set-upstream origin master
Username for 'url': name
Password for 'url':
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 965 bytes | 0 bytes/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To http://172.26.3.245/qintao/efront.git
   ba49dca..d55df17  master -> master
Branch master set up to track remote branch master from origin.
```
> - `--set-upstream` 第一次需要，以后就不需要   
- 推送后，在gitlab网站上可以查看文件

# 查看历史
```sh
$ git log
commit d55df17b52a972c0d59f8c1d9549581617de2bef
Author: TSKY.tao.qin <qintao@travelsky.com>
Date:   Mon Oct 19 10:52:17 2015 +0800

    add files

```

# 在gitlab上增加一个文件
> 使用页面编辑器在efront库的git目录下增加一个 `README.md`,里面的内容是： `git pull`

# 从远程仓库抓取数据
```sh
$ git pull
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (4/4), done.
From http://172.26.3.245/qintao/efront
   d55df17..13290fc  master     -> origin/master
Updating d55df17..13290fc
Fast-forward
 git/README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 git/README.md
 $ ls git
 git.basic.md  README.md
```
> 通过ls指令可以发现获取到了README.md文件


# 在本地git目录下修改一个文件
> 在本地git目录下修改 `README.md`,增加的内容是： `git diff HEAD`

# 查看工作空间与本地库之间的差异
```sh
$ git diff HEAD
diff --git a/git/README.md b/git/README.md
index bddc158..8fd58d8 100644
--- a/git/README.md
+++ b/git/README.md
@@ -1 +1,2 @@
-git pull
\ No newline at end of file
+git pull^M
+git diff HEAD^M
```

# 将修改的文件添加到暂存区，以便跟踪
```sh
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   git/README.md

no changes added to commit (use "git add" and/or "git commit -a")
$ git add -A
```

# 查看暂存区与本地库之间的差异
```sh
$ git diff --staged
diff --git a/git/README.md b/git/README.md
index bddc158..8fd58d8 100644
--- a/git/README.md
+++ b/git/README.md
@@ -1 +1,2 @@
-git pull
\ No newline at end of file
+git pull^M
+git diff HEAD^M
```

# 重置暂存区中的文件
```sh
$ git reset git/README.md
Unstaged changes after reset:
M       git/README.md
```
> 执行该操作后，文件将从暂存区移出

# 将工作区的文件还原到修改之前
```sh
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   git/README.md

no changes added to commit (use "git add" and/or "git commit -a")
$ git checkout -- git/README.md
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

# 创建并切换分支
```sh
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
```

# 推送新的分支到远程仓库
```sh
$  git push --set-upstream origin dev
Username for 'http://172.26.3.245': qintao
Password for 'http://qintao@172.26.3.245':
Total 0 (delta 0), reused 0 (delta 0)
To http://172.26.3.245/qintao/efront.git
 * [new branch]      dev -> dev
Branch dev set up to track remote branch dev from origin.
```
> 推送后可以在gitlba发现有新的分支

# 删除当前分支上的文件
```sh
$ git rm '*.md'
rm 'git/README.md'
rm 'git/git.basic.md'
```

# 提交修改到当前分支
```sh
$ git commit -m "Remove all the cats"
[dev 22a0318] Remove all the cats
 2 files changed, 76 deletions(-)
 delete mode 100644 git/README.md
 delete mode 100644 git/git.basic.md
```

# 切换到master分支
```sh
$  git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
```

# 合并dev分支
```sh
$ git merge dev
Updating 13290fc..22a0318
Fast-forward
 git/README.md    |  1 -
 git/git.basic.md | 75 --------------------------------------------------------
 2 files changed, 76 deletions(-)
 delete mode 100644 git/README.md
 delete mode 100644 git/git.basic.md
$ ls
```
> ls查看，文件全部删除了


# 删除分支
```sh
$  git branch -d dev
Deleted branch dev (was 22a0318).
```

# 推送文件到远程仓库
```sh
$ git push
```
> 推送后，在gitlab网站中查看文件已经被删除

# 回退2次提交
```sh
$ git revert HEAD^2
[master a2518b1] Revert "Remove all the cats"
 2 files changed, 76 insertions(+)
 create mode 100644 git/README.md
 create mode 100644 git/git.basic.md
$ ll
total 0
drwxr-xr-x 1 Andy 197121 0 十月 19 06:46 git/
```
> 回退后发现已经删除的文件回来了

# 再次推送到远程仓库
```sh
$ git push
Username for 'url': name
Password for 'url':
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 758 bytes | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To http://172.26.3.245/qintao/efront.git
   22a0318..a2518b1  master -> master
```
>  推送之后在gitlba上发现文件回来了
