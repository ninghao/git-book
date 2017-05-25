# 冲突

小雪在 pull 的时候，发生了冲突：

```
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/ninghao/ninghao-git
   b9f3ba9..b5fd9fb  master     -> origin/master
First, rewinding head to replay your work on top of it...
Applying: 为说明文档章节添加描述文字
Using index info to reconstruct a base tree...
M    README.md
Falling back to patching base and 3-way merge...
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
error: Failed to merge in the changes.
Patch failed at 0001 为说明文档章节添加描述文字
The copy of the patch that failed is found in: /Users/wanghao/desktop/xiaoxue-git/.git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```

她查看了状态：

```
git status
```

返回：

```
rebase in progress; onto b5fd9fb
You are currently rebasing branch 'master' on 'b5fd9fb'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

    both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```



