# Gitflow 工作流

Gitflow 工作流，扩展了集中式工作流与功能分支工作流。

> Gitflow 是 Vincent Driessen 在他的博客 [nvie](http://nvie.com/posts/a-successful-git-branching-model/) 上介绍的一种 Git 工作流程。

## 开发分支

在开发中使用 Gitlfow 工作流。开发者们都要在本地创建一个开发分支，一般叫 develop。开发者创建的功能分支（feature branch）要基于这个开发分支（develop），功能分支完成以后，要合并到这个开发分支上。也就是这个 develop 记录了项目的开发历史。

## 功能分支

开发者要为项目添加新功能，就在自己本地创建功能分支。一般分支可以使用 `feature-` 作为分支名的前缀。方法跟功能分支工作流里介绍的一样，只不过在 Gitflow 工作流里，功能分支要基于 develop 分支创建，并且最终要合并到 develop 分支上。

## 发行分支

项目开发的差不多了，就可以去准备一个发行分支，一般用 `release-` 作为前缀。在发行分支上不添加新功能了，只修复 bug ，还有为项目发行做准备。准备好以后，把发行分支全并到主分支（master）上，然后打个标签（tag），比如 v1.1，v1.2 之类的。

## 维护分支

突然发现有需要立即解决的问题，可以创建 hotfix 分支，这个分支你可以直接基于 master 分支创建。然后修复问题，再把 hotfix 分支合并到 master 与 develop 分支上。

## 练习

走一遍使用 Gitflow 的开发流程。还是继续用之前我们一起开发的项目，项目的开发者有两个人，王皓（wanghao8080），他是项目的发起人，还有另外一个开发者叫小雪（xiaoxue8080）。

### 创建开发分支

项目的发起人在最初创建项目的时候，就应该去创建一个开发分支（develop），然后把这个分支也推送到项目的远程，这样项目的协作开发者在克隆项目到本地的时候，也都可以有一个 develop 分支。

现在我们才决定要使用 Gitflow 的流程去开发，所以可以先去创建一个 develop 分支。这个任务让项目的发起人去做，王皓进入到了他的项目所在的目录 ninghao-git，然后执行了：

```
git branch develop
git push origin develop
```

创建了一个 develop 分支，又把这个分支推送到了远程 。平时工作的时候，创建的功能分支都应该基于 develop 分支，可以把当前分支切换到 develop ：

```
git checkout develop
```

小雪之前已经克隆了仓库，她做这件事儿的时候，远程那里还没有 develop 分支。她进入到了在本地存储的项目目录（xiaoxue-git），然后执行了一下：

```
git fetch
```

然后再执行：

```
git checkout -b develop origin/develop
```

现在小雪的本地也有了 develop 分开。

### 小雪有了新任务

现在小雪有了新任务或者新的想法，她想去试一下。可以先去创建一个功能分支，方法与流程在功能分支工作流里介绍到了，不太一样的是，Gitflow 里面， 功能分支要基于 develop 分支创建。其它的跟功能分支工作流差不多，创建新的功能分支，修改项目，提交，推送到远程，完成了功能以后可以发起一个 pull request ，大家讨论以后可以把功能分支合并到 develop 分支上。

小雪要去写一个关于介绍 Git 远程仓库的文档，她先去创建了一个分支：

```
git checkout -b remote-doc develop
```

接着创建了一个 Markdown 文档：

```
touch remote.md
```

做了一次提交：

```
git add .
git commit -m '添加介绍远程仓库的文档'
```

又这样修改了一下 remote.md：

```
# 远程
Remote，指的是项目的远程仓库。
```

又做了一次提交：

```
git commit -am '添加介绍远程仓库的内容'
```

### 小雪完成了任务

小雪觉得文档已经写完了，她可以把功能分支 push 到远程，然后发起 pull request，或者也可以直接把功能分支合并到 develop 分支。

她先看看远程的 develop 有啥新东西没：

```
git pull origin develop
```

切换到 develop：

```
git checkout develop
```

把 remote-doc 这个功能分支合并到 develop：

```
git merge remote-doc
```

把合并之后的 develop 推送到远程：

```
git push origin develop
```

现在，功能分支可以删除掉了：

```
git branch -d remote-doc
```

### 准备发行

这个项目做的差不多了，可以准备一次正式的发行。这个任务还是小雪去做，她先要去创建一个为发行准备的发行分支，分支名一般可以使用 release- 作为前缀。执行：

```
git checkout -b release-0.1 develop
```

她把发行分支推送到了项目的中央远程仓库：

```
git push origin release-0.1
```

本次发行任务的小组成员里还有王皓，他可以往这个发行分支里做自己的提交。新功能不要放到发行分支了，你可以留着下一次发行用，发行分支主要就是为项目的发行做准备，比如修复 bug 之类的。

### 完成发行

大家共同的努力，项目现在已经可以正式发行了。这件事还是小雪去做：

```
git checkout master
git merge release-0.1
git push
git checkout develop
git merge release-0.1
git push
git branch -d release-0.1
```

打个标签：

```
git tag -a v0.1 -m '项目的首次发行'
git push --tags
```





