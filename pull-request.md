# Pull Request

## 练习

小雪登录到了 Github ，打开了项目仓库。新建一个 pull request，比较的是 master 与小雪推送上来的 workflow-doc 分支，可以给这个 pull request 写个标题与介绍。

创建以后，项目的其他开发者会收到通知，他们可以查看这个 pull request 包含的提交，也可以把这些提交 pull 到自己的本地，仔细检查一下。然后可以留下自己的评论。

### 小雪继续修改项目

小雪收到团队成员的评论，她决定再去修改一下 workflow.md 这个文档。内容如下：

```
# 工作流

* 集中式工作流
* 功能分支工作流
* Gitflow 工作流

## 集中式工作流
一个中央远程仓库，一个主分支。

## 功能分支工作流
一个中央远程仓库，一个主分支，多个功能分支。

## Gitflow 工作流
一个中央远程仓库，一个主分支，一个开发分支，多个功能分支。

```

做一次提交：

```
git commit -m '添加几种工作流的介绍'
```

Push：

```
git push origin workflow-doc
```

新 push 上来的提交会显示在 pull request 里面，团队成员可以继续交流。确定没什么问题，就可以合并到主分支上了。

### 合并 pull request

小雪很开心，她写的文档大家都很满意，现在可以去合并了。执行：

```
git checkout master
git pull
git pull origin workflow-doc
git push
```

成功！pull request 会自动关闭。

