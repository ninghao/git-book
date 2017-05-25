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



```
git remote add upstream https://github.com/ninghao/ninghao-git.git
```

```
→ git remote -v
origin    https://github.com/hulk8080/ninghao-git.git (fetch)
origin    https://github.com/hulk8080/ninghao-git.git (push)
upstream    https://github.com/ninghao/ninghao-git.git (fetch)
upstream    https://github.com/ninghao/ninghao-git.git (push)
```

```
git config --local user.name 'hulk8080'
git config --local user.email 'hulk@ninghao.net'
```

```
git checkout -b feature-branch
git pull upstream master
git push origin feature-branch
```

维护人

```
git fetch https://github.com/hulk8080/ninghao-git.git feature-branch
git checkout master
git merge FETCH_HEAD
git push origin master
```

所有人

```
git pull upstream master
```



