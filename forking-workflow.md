# Forking 工作流

Fork 指的就是把在别人盘子里的菜（仓库）叉（Fork）到自己盘子里。假设你是一个项目的开维护者，一个发起人，你把项目推送到了一个公共的远程仓库上。其他的开发者相中了你的项目，他们可以把你的远程仓库 Fork 到自己的远程仓库里，然后再把自己的远程仓库克隆到本地。

比如有个叫 Hulk 的开发者就做了这件事，Fork 了你的远程仓库。Hulk 在本地创建功能分支，对项目做开发，完成以后他把功能分支推送到自己的远程仓库里，然后创建一个 pull request 通知你一下。

你是项目的维护人，收到 pull request 以后，你可以直接在网站上检查一下，或者可以 pull 到本地检查，看看 pull request 里的东西。如果觉得可以，你就可以把 Hulk 的 pull request 合并到项目的主分支上，再 push 到项目的远程仓库。其他的开发者可以把你新 push 上去的东西 pull 到他们各自的本地仓库里。

在 Forking 工作流中，每个开发者都有自己的独立的远程仓库。

## 练习

**1**，Hulk 觉得我们的项目不错，他在我们项目的远程仓库页面，点了 Fork 按钮，把仓库  Form 到了他自己在 Github 的帐户下。

**2**，Hulk 要把他 Fork 的远程仓库克隆到他的本地：

```
git clone https://github.com/hulk8080/ninghao-git.git hulk-git
```

进入到项目所在的目录 hulk-git，然后查看一下仓库的远程：

```
→ git remote -v

origin    https://github.com/hulk8080/ninghao-git.git (fetch)
origin    https://github.com/hulk8080/ninghao-git.git (push)
```

克隆以后自动会有个 origin 远程，观察 origin 远程的地址，是在 hulk8080 这个用户名下。开发者还得去添加一个远程，指向项目的官方仓库，这个远程的名字一般是 upstream：

```
git remote add upstream https://github.com/ninghao/ninghao-git.git
```

再查看一下远程：

```
→ git remote -v

origin    https://github.com/hulk8080/ninghao-git.git (fetch)
origin    https://github.com/hulk8080/ninghao-git.git (push)
upstream    https://github.com/ninghao/ninghao-git.git (fetch)
upstream    https://github.com/ninghao/ninghao-git.git (push)
```

再简单配置一下本地仓库：

```
git config --local user.name 'hulk8080'
git config --local user.email 'hulk@ninghao.net'
```

**3**，Hulk 开始为项目添加新功能了，他可以去创建一个功能分支：

```
git checkout -b help-doc
```

Hulk 想为项目添加一个 GIt 命令使用的帮助文档，创建一个 git-help.md：

```
touch git-help.md
```

做一次提交：

```
git add .
git commit -am '添加 Git help 文档'
```

继续修改 git-help.md：

```
# git --help
git 命令的帮助信息。
```

再做一次提交：

```
git commit -am '添加 Git help 文档内容'
```

Hulk 看一下项目官方那里有什么新东西吧：

```
git pull upstream master
```

然后把 help-doc 推送到自己的远程那里：

```
git push origin help-doc
```

```
Counting objects: 6, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 596 bytes | 0 bytes/s, done.
Total 6 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/hulk8080/ninghao-git.git
 ! [remote rejected] help-doc -> help-doc (permission denied)
error: failed to push some refs to 'https://github.com/hulk8080/ninghao-git.git'
```

**4**，维护人

```
git fetch https://github.com/hulk8080/ninghao-git.git feature-branch
git checkout master
git merge FETCH_HEAD
git push origin master
```

**5**，所有人

```
git pull upstream master
```



