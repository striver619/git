# [Git](https://git-scm.com/)

how to use git from zero to one?

## 0. register an email account if you do not have

+ [qq mail](https://mail.qq.com)
+ [126 mail](https://mail.126.com)
+ [163 mail](https://mail.163.com)
+ [aliyun mail](https://mail.aliyun.com)

## 1. register an github/gitee account if you do not have

+ [GitHub](https://github.com)

sign up

+ [Gitee](https://gitee.com)

register

## 2. configure your account Settings in SSH Public key

+ generate ssh public/private keys from your localhost

```shell
ssh-keygen -t rsa
```

windows environment by git client (Git for Windows)

+ cat and copy your localhost's public key all contents

eg.

```shell
cat ~/.ssh/id_rsa.pub
```

or

```powershell
# windows environment
/Users/Administrator/.ssh/id_rsa.pub
```

+ paste them to set github/gitee SSH Public key

set your title
paste public key to SSH keys

## 3. by GitHub/Gitee Dashboard '+' to New repository

## 4. from your repository's index page, copy repository's address

+ click on [Code]

you will look at this repository's address

eg.
   https://github.com/striver619/git.git

then copy it

## 5. configure your localhost git client account and email

+ way1

```shell
git config --global user.name "your-account"
git config --global user.email "your-email@xxx.com"
```

+ way2

```shell
[git@github github]$ vim ~/.gitconfig 
[user]
	name = your-account
	email = your-email@xxx.com
[git@github github]$ 
```

then, Test whether it can be connected

```shell
ssh -T git@github.com
```

eg.

```shell
[git@github github]$ ssh -T git@github.com
Hi striver619! You've successfully authenticated, but GitHub does not provide shell access.
[git@github github]$ 
```

## 6. git clone GitHub/Gitee repository

+ fork team's/someone's repository

you should [fork] from your repository at first!

+ clone your repository

eg.

```shell
git clone https://github.com/striver619/git.git
```

show all effect

```shell
[git@github github]$ git clone https://github.com/striver619/git.git
Cloning into 'git'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 619 bytes | 619.00 KiB/s, done.
[git@github github]$ ls -la
total 16
drwxr-xr-x.  4 qc qc 4096 Jun 12 14:52 .
drwx------. 26 qc qc 4096 Jun 12 14:28 ..
drwxr-xr-x.  3 qc qc 4096 Jun 12 14:52 git
[git@github github]$
```

## 7. edit your repository's files on your localhost

+ change directory tou your localhost's repository

```shell
[git@github github]$ cd git/
[git@github git]$
```

+ look at this repository's includings

```shell
[git@github git]$ ls -la
total 16
drwxr-xr-x. 3 qc qc 4096 Jun 12 14:52 .
drwxr-xr-x. 4 qc qc 4096 Jun 12 14:52 ..
drwxr-xr-x. 8 qc qc 4096 Jun 12 14:52 .git
-rw-r--r--. 1 qc qc   39 Jun 12 14:52 README.md
[git@github git]$
```

+ you can new files or update files from this directory

## 8. git status

+ when you edit finished, use this command look at difference

```shell
git status
```

eg.

```shell
[git@github git]$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.en.md

nothing added to commit but untracked files present (use "git add" to track)
[git@github git]$
```

## 9. git add

+ add your update's files to local repository

you can use this command

```shell
git add filename
```

or you can also use this command

```shell
git add .
```

eg.

```shell
[git@github git]$ git add README.en.md 
[git@github git]$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   README.en.md

[git@github git]$
```

## 10. git commit

+ commit, by property '-m' to add notes

```shell
git commit -m "your commit changes"
```

eg.

```shell
[git@github git]$ git commit -m "append README.en.md"
[main 4e24b1b] append README.en.md
 1 file changed, 140 insertions(+)
 create mode 100644 README.en.md
[git@github git]$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
[git@github git]$
```

by the way, you can also use this way

```shell
git commit
```

but, you should edit the commit changes, which changelog

then save just like use Vim editor

## 11. git pull

before you git push, you have to 'git pull' to update your repository
just to avoid code repository conflicts

```shell
git pull
```

eg.

```shell
[git@github git]$ git pull
warning: Pulling without specifying how to reconcile divergent branches is
discouraged. You can squelch this message by running one of the following
commands sometime before your next pull:

  git config pull.rebase false  # merge (the default strategy)
  git config pull.rebase true   # rebase
  git config pull.ff only       # fast-forward only

You can replace "git config" with "git config --global" to set a default
preference for all repositories. You can also pass --rebase, --no-rebase,
or --ff-only on the command line to override the configured default per
invocation.

Already up to date.
[git@github git]$ 
```

if you want to never look at warning logs, set as follows

```shell
[git@github git]$ git config --global pull.rebase false
[git@github git]$ git pull
Already up to date.
[git@github git]$
```

## 12. git push

+ before 'git push', you should set 'set-url' to the git remote

first look at local repository's remote

```shell
git remote -v
```

```shell
git remote set-url origin git+ssh://git@github.com/striver619/git.git
```

eg.

```shell
[git@github git]$ git remote -v
origin	https://github.com/striver619/git.git (fetch)
origin	https://github.com/striver619/git.git (push)
[git@github git]$ 
[git@github git]$ git remote set-url origin git+ssh://git@github.com/striver619/git.git
[git@github git]$ git remote -v
origin	git+ssh://git@github.com/striver619/git.git (fetch)
origin	git+ssh://git@github.com/striver619/git.git (push)
[git@github git]$
```

if you do not set 'set-url', when you 'git push' you will look at this,
when you input Username, Password then "fatal: Authentication failed"
as you can see, this is the GitHub's/Gitee's bug

```shell
[git@github git]$ git push -u origin main
Username for 'https://github.com': striver619
Password for 'https://striver619@github.com': 
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/striver619/git.git/'
[git@github git]$ 
```

by looking at logs, you can find answer

+ when you 'git push', you should appoint your repository 'main' branch

```shell
git push -u origin main
```

```shell
[git@github git]$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 267 bytes | 267.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To git+ssh://github.com/striver619/git.git
   0c0fd9b..4e24b1b  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
[git@github git]$
```

you can also directly use 'git push', but we do not suggest this way

```shell
git push
```

## 13. git log

+ you can use this command to look at commit changes logs

```shell
git log
```

## 14. new PR

from your GitHub/Gitee repository, you can look at 'Pull requests'

then click on that button, you will see "Welcome to pull requests!"

then you can click on the right direction "New pull request"

by this, your code branch will be merge if you fix bugs or updates

So, as you can see, this is the most popular styles of IT programmers and coders.

Contributing your code to opensource is just so easy.

## 15. follow your email

if the repository maintainer merged your branch,
your email will receive an email.

eg.

Merged #01 into master.

## 16. you can also new a issue or discussion on GitHub's/Gitee's Dashboard

## 17. git's others

+ solve rebase error

```shell
git pull --rebase

error: cannot pull with rebase: Your index contains uncommitted changes.
error: please commit or stash them.
```

```shell
git stash
git pull --rebase
git stash pop
```

+ about git's blog

[git submits code to ones own repository](https://blog.csdn.net/frdevolcqzyxynjds/article/details/117598717)


+ demo case

```
git status
git pull
vim file-demo
git add file-demo
git commit
git push
git status
```

## [About Git](https://git-scm.com/about)

## [Git Document](https://git-scm.com/doc)

+ [Git Book](https://git-scm.com/book/en/v2)

+ [What is Git?](https://git-scm.com/video/what-is-git)
