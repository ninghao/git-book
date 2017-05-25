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

走一遍使用 Gitflow 的开发流程。继续使用之前我们一直练习的项目，开发者一个是王皓（wanghao8080），一个叫小雪（xiaoxue8080）。你在练习的时候可以选择你自己喜欢的人 ：）

### 创建开发分支

项目的发起人一开始就应该基于 master 去创建一个开发分支，然后把它推送到远程。

```
git checkout -b develop master
```

基于 master 创建一个 develop 分支。



