# git rebase

不解释了，直接练：）

## 练习

**1**，我们的项目是一本 git-book，现在我们要去添加一个新文档，介绍一下 Git 的 “仓库”。创建一个分支，执行：

```
git checkout -b repo-doc
```

在 git checkout 命令里用了 -b 选项，这样如果要查看的分支不存在，就会给我们创建一个。查看分支，显示当前是在 repo-doc 这个分支上。

```
  master
* repo-doc
```

在项目下面新建一个 Markdown 文件：

```
touch repository.md
```

做一次提交：

```
git add .
git commit -m '添加介绍 Git 仓库的文档'
```

打开 repository.md，在文档里添加一个标题：

```
# 仓库
```

再做一次提交：

```
git commit -am '添加仓库文档的大标题'
```

**2**，现在假设项目有个突发状况，可能是一个要立即修复的 bug，或者添加一个功能。不管是什么吧，反正是要立即完成的事儿。先切换回 master 分支：

```
git checkout master
```

为修复的 bug，或添加的功能创建一个分支：

```
git checkout -b 'add-bottom-text'
```

打开项目下的 resources.md，把文档修改成这样：

```
# 相关资源 :)
* 宁皓网《Git》课程包

---
by ninghao.net
```

执行一次提交：

```
git commit -am '为 resouces.md 添加底部文字'
```

把 add-bottom-text 合并到 master：

```
git checkout master
git merge add-bottom-text
```

再把 add-bottom-text 删除掉：

```
git branch -d add-bottom-text
```

现在 master 分支上会有一个来自 add-bottom-text 的提交：

```
→ git log --oneline --graph

* 40670e5 为 resouces.md 添加底部文字
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

**3**，修复了 bug，切换回 repo-doc，继续完成仓库文档的编写：

```
git checkout repo-doc
```

打开 repository.md，把文档修改成这样：

```
# 仓库
Repository，仓库，简称 Repo。
```

做一次提交：

```
git commit -am '为仓库文档添加一段描述'
```

查看历史，现在 repo-doc 的历史应该是这样：

```
 → git log --oneline --graph

* 5db5973 为仓库文档添加一段描述
* 9908ffb 添加仓库文档的大标题
* e8204c5 添加介绍 Git 仓库的文档
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

里面没有刚才合并到 master 上的 add-bottom-text 分支里做的提交：

```
40670e5 为 resouces.md 添加底部文字
```

现在，假设仓库文件已经写完了，我们要把它合并到 master 分支上。执行：

```
git checkout master
git merge repo-doc
```

合并以后，查看 master 的历史，应该像这样：

```
→ git log --oneline --graph

*   cee6891 Merge branch 'repo-doc'
|\  
| * 5db5973 为仓库文档添加一段描述
| * 9908ffb 添加仓库文档的大标题
| * e8204c5 添加介绍 Git 仓库的文档
* | 40670e5 为 resouces.md 添加底部文字
|/  
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

**4**，git reflog

```
→ git reflog

cee6891 HEAD@{0}: merge repo-doc: Merge made by the 'recursive' strategy.
40670e5 HEAD@{1}: checkout: moving from repo-doc to master
5db5973 HEAD@{2}: checkout: moving from master to repo-doc
40670e5 HEAD@{3}: checkout: moving from repo-doc to master
5db5973 HEAD@{4}: commit: 为仓库文档添加一段描述
9908ffb HEAD@{5}: checkout: moving from master to repo-doc
40670e5 HEAD@{6}: merge add-bottom-text: Fast-forward
8d26980 HEAD@{7}: checkout: moving from add-bottom-text to master
40670e5 HEAD@{8}: commit: 为 resouces.md 添加底部文字
8d26980 HEAD@{9}: checkout: moving from master to add-bottom-text
8d26980 HEAD@{10}: checkout: moving from repo-doc to master
9908ffb HEAD@{11}: commit: 添加仓库文档的大标题
e8204c5 HEAD@{12}: commit: 添加介绍 Git 仓库的文档
8d26980 HEAD@{13}: checkout: moving from master to repo-doc
```

重置到这个状态：

```
40670e5 HEAD@{6}: merge add-bottom-text: Fast-forward
```

执行：

```
git reset 40670e5 --hard
```

查看 master 上的历史：

```
 → git log --oneline --graph
 
* 40670e5 为 resouces.md 添加底部文字
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

又回到了合并 add-bottom-text 分支以后的样子了。

**5**，git rebase。切换到 repo-doc：

```
git checkout repo-doc
```

查看历史：

```
→ git log --oneline --graph
* 5db5973 为仓库文档添加一段描述
* 9908ffb 添加仓库文档的大标题
* e8204c5 添加介绍 Git 仓库的文档
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

执行：

```
git rebase master
```

返回：

```
First, rewinding head to replay your work on top of it...
Applying: 添加介绍 Git 仓库的文档
Applying: 添加仓库文档的大标题
Applying: 为仓库文档添加一段描述
```

再查看一下历史：

```
 → git log --oneline --graph
 
* a102dba 为仓库文档添加一段描述
* 0944475 添加仓库文档的大标题
* 655881c 添加介绍 Git 仓库的文档
* 40670e5 为 resouces.md 添加底部文字
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

观察历史跟之前的区别，“为 resouces.md 添加底部文字” 这个提交在 repo-doc 的历史中出现了，我们在 repod-doc 上做的提交都会在这个 “为 resouces.md 添加底部文字” 之上出现。这就是 git rebase 做的事情。

**6**，合并。再切换到 master 分支，然后执行合并：

```
git checkout master
git merge repo-doc
```

返回：

```
Updating 40670e5..a102dba
Fast-forward
 repository.md | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 repository.md
```

这回合并是一次 Fast-forward 合并。查看 master 的历史：

```
→ git log --oneline --graph

* a102dba 为仓库文档添加一段描述
* 0944475 添加仓库文档的大标题
* 655881c 添加介绍 Git 仓库的文档
* 40670e5 为 resouces.md 添加底部文字
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

对比一下之前我们没在 repo-doc 里做 rebase ，然后直接合并 master 以后的历史：

```
*   cee6891 Merge branch 'repo-doc'
|\  
| * 5db5973 为仓库文档添加一段描述
| * 9908ffb 添加仓库文档的大标题
| * e8204c5 添加介绍 Git 仓库的文档
* | 40670e5 为 resouces.md 添加底部文字
|/  
*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```



