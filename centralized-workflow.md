# 集中式工作流

Centralized Workflow。项目的所有协作者把对项目的修改推送到统一的远程仓库，这就是集中式工作流。其它的 Git 工作流基本都是基于这种工作流程做了一些扩展。

项目的发起者在自己电脑上创建了一个本地仓库，他又为项目在远程创建了一个仓库，这个远程仓库就是所有协作者要把提交推送到的地方。这个远程仓库在谁家那创建都无所谓，可以用 Github，Coding.net，阿里云 Code，也可以是自建的远程仓库。

项目的协作者先要把远程仓库克隆到他们本地电脑上，然后对项目进行修改，提交。再把他们对项目做的修改提交推送到项目的远程仓库里。

项目的协作者可以从项目的远程那里不断重复地拉取（pull）大伙对项目做的提交。也就是协作者们都共享彼此对项目的开发成果。这就实现了协作开发。

## 练习

使用集中式工作流开发，很多事情我们之前已经做了。项目的发起人已经在本地创建好了仓库，为项目在远程也创建了仓库，把项目推送到了远程，为项目的远程仓库添加了协作者（wanghao8080，xiaoxue8080）。协作者（xiaoxue8080）也把项目克隆到了本地准备开发。

### 模拟准备

现在我再模拟一下使用集中式工作流，多协作者共同开发项目。介绍  git clone 的时候，我说用小雪的身份克隆了一份远程仓库，放到 xiaoxue-git 目录的下面。因为我是在同一台电脑上模拟多开发者，所以我需要单独配置一下 xiaoxue-git 这个项目，设置一下提交者的名字，还有邮件地址。

进入 xiaoxue-git 这个目录，执行：

```
cd ~/desktop/xiaoxue-git
git config --local user.name 'xiaoxue8080'
git config --local user.email 'xiaoxue@ninghao.net'
```

这样，在我的电脑桌面上的 xiaoxue-git 目录下对项目做的修改提交，用的就是 xiaoxue8080 的身份。

我的电脑桌面上还有一个 ninghao-git 目录，这是我最开始创建的项目所在的目录。我在全局配置的 Git，使用的用户是 wanghao8080，所以在 ninghao-git 目录下做的提交就是用 wanghao8080 这个用户身份做的。

### 项目发起人创建了项目

完成！

### 项目发起人为项目创建了远程仓库

完成！

### 为远程仓库添加协作者

完成！

### 协作者克隆项目远程仓库到本地

完成！

### 小雪开始对项目做修改

小雪打开了存储在她本地的项目目录（xiaoxue-git），修改了 README.md，内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程

## 分支

## 远程

## 协作

---
by ninghao.net
```

做了一次提交：

```
git commit -am '在说明文档里添加“协作”章节'
```

她把提交 push 到项目的远程，因为她已经是项目的协作开发者，所以有权限 push：

```
git push -u origin master
```

因为小雪在克隆仓库的时候用了 HTTPS 类型的地址，所以她 push 的时候需要输入用户名与密码验证她的身份。

```
Username for 'https://github.com': xiaoxue8080
Password for 'https://xiaoxue8080@github.com': 

Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 400 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/ninghao/ninghao-git.git
   4eeb8d7..70161b2  master -> master
Branch master set up to track remote branch master from origin.
```

![](/assets/github-multi-users-commits.png)

### 王皓也对项目做了修改

进入（ninghao-git），修改了 README.md，内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程
了解使用 Git 的基本流程。 

## 分支

## 远程

---
by ninghao.net
```

做了一次提交：

```
git commit -am '为“流程”章节添加描述'
```

他也要把做的提交 push 到项目的中心远程仓库：

```
git push
```

不过这次 push 出了点状况，提示：

```
To github.com:ninghao/ninghao-git.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:ninghao/ninghao-git.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

意思是说，远程仓库上有一些东西在王皓本地没有，可以先把远程上的新东西 pull 到本地。pull 的时候可以用一个 --rebase 选项，这样可以把他刚刚对项目做的修改放在最上面。

```
git pull --rebase
```

返回：

```
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), done.
From github.com:ninghao/ninghao-git
   4eeb8d7..70161b2  master     -> origin/master
First, rewinding head to replay your work on top of it...
Applying: 为“流程”章节添加描述
```

完成以后，再去 push 一下：

```
 → git push

Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 418 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:ninghao/ninghao-git.git
   70161b2..25e582e  master -> master
```

这回王皓也成功地把提交 push 到了项目的远程。

### 小雪继续修改项目

小雪没闲着，继续修改了项目的 README.md，现在内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程
介绍 Git 的使用流程。

## 分支
创建与管理项目的分支。

## 远程
为项目添加远程仓库。

## 协作
用 Git 协作开发项目。

---
by ninghao.net
```

她又做了一次提交：

```
git commit -am '为说明文档章节添加描述文字'
```

提交以后，她打算休息一下，逛逛淘宝。于是她决定要把自己做的提交推送到远程，让大家知道自己对项目做的修改。小雪知道，在 push 之前，最好先去 pull 一下，因为很可能别人也对项目做了修改。于是她执行了：

```
git pull --rebase
```

但是 ...

