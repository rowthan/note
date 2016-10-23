# ȫ������
```sh
$ git config user.email "rhran@travelsky.com"
$ git config user.name ranronghua
$ git config --global credential.helper store
$ git config --global core.autocrlf false
```
>���Ϸֱ������䣬�û����������Զ����棬��ֹ�Զ����е�����  

# ��¡Զ�ֿ̲�

```sh
$ git clone url
Cloning into 'efront'...
warning: You appear to have cloned an empty repository.
Checking connectivity... done.
```

# �鿴״̬
```sh
$ cd efront

$ git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```

# �����ļ��м��ļ�
```sh
$ mkdir git

$ cd git

$ vi git.basic.md
```


    ```

# �ٴβ鿴״̬    
```sh
$ cd ../

$ ll
total 0
drwxr-xr-x 1 Andy 197121 0 ʮ�� 19 01:53 git/

$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        git/

nothing added to commit but untracked files present (use "git add" to track)
```


# ���ļ���ӵ�git�ݴ������Ա�git����
```sh
$ git add git

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   git/git.basic.md
```
# �ύ�ļ������زֿ�
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
 > `-m` �������ύ���ļ�ע��

# �����ļ���Զ�ֿ̲�
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
> - `--set-upstream` ��һ����Ҫ���Ժ�Ͳ���Ҫ   
- ���ͺ���gitlab��վ�Ͽ��Բ鿴�ļ�

# �鿴��ʷ
```sh
$ git log
commit d55df17b52a972c0d59f8c1d9549581617de2bef
Author: TSKY.tao.qin <qintao@travelsky.com>
Date:   Mon Oct 19 10:52:17 2015 +0800

    add files

```

# ��gitlab������һ���ļ�
> ʹ��ҳ��༭����efront���gitĿ¼������һ�� `README.md`,����������ǣ� `git pull`

# ��Զ�ֿ̲�ץȡ����
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
> ͨ��lsָ����Է��ֻ�ȡ����README.md�ļ�


# �ڱ���gitĿ¼���޸�һ���ļ�
> �ڱ���gitĿ¼���޸� `README.md`,���ӵ������ǣ� `git diff HEAD`

# �鿴�����ռ��뱾�ؿ�֮��Ĳ���
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

# ���޸ĵ��ļ���ӵ��ݴ������Ա����
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

# �鿴�ݴ����뱾�ؿ�֮��Ĳ���
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

# �����ݴ����е��ļ�
```sh
$ git reset git/README.md
Unstaged changes after reset:
M       git/README.md
```
> ִ�иò������ļ������ݴ����Ƴ�

# �����������ļ���ԭ���޸�֮ǰ
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

# �������л���֧
```sh
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
```

# �����µķ�֧��Զ�ֿ̲�
```sh
$  git push --set-upstream origin dev
Username for 'http://172.26.3.245': qintao
Password for 'http://qintao@172.26.3.245':
Total 0 (delta 0), reused 0 (delta 0)
To http://172.26.3.245/qintao/efront.git
 * [new branch]      dev -> dev
Branch dev set up to track remote branch dev from origin.
```
> ���ͺ������gitlba�������µķ�֧

# ɾ����ǰ��֧�ϵ��ļ�
```sh
$ git rm '*.md'
rm 'git/README.md'
rm 'git/git.basic.md'
```

# �ύ�޸ĵ���ǰ��֧
```sh
$ git commit -m "Remove all the cats"
[dev 22a0318] Remove all the cats
 2 files changed, 76 deletions(-)
 delete mode 100644 git/README.md
 delete mode 100644 git/git.basic.md
```

# �л���master��֧
```sh
$  git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
```

# �ϲ�dev��֧
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
> ls�鿴���ļ�ȫ��ɾ����


# ɾ����֧
```sh
$  git branch -d dev
Deleted branch dev (was 22a0318).
```

# �����ļ���Զ�ֿ̲�
```sh
$ git push
```
> ���ͺ���gitlab��վ�в鿴�ļ��Ѿ���ɾ��

# ����2���ύ
```sh
$ git revert HEAD^2
[master a2518b1] Revert "Remove all the cats"
 2 files changed, 76 insertions(+)
 create mode 100644 git/README.md
 create mode 100644 git/git.basic.md
$ ll
total 0
drwxr-xr-x 1 Andy 197121 0 ʮ�� 19 06:46 git/
```
> ���˺����Ѿ�ɾ�����ļ�������

# �ٴ����͵�Զ�ֿ̲�
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
>  ����֮����gitlba�Ϸ����ļ�������
