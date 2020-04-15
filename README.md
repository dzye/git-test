###  查看分支

## 查看本地分支

```
git branch
* master
```

master 分支前的 \* 字符，它表示当前所在的分支。

## 查看远程所有分支

```
git branch -r
origin/HEAD -> origin/master
origin/master
```

## 列出本地分支和远程分支

```
git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

###  创建本地 dev1 分支

## 直接创建本地分支

```
git checkout -b dev1
Switched to a new branch 'dev1'
```

等同于

```
git branch dev1
git checkout dev1
```

## 从远程分支 dev(远程有该分支)创建本地分支

```
git checkout -b dev1 origin/dev
Switched to a new branch 'dev1'
```

###  修改本地分支名字

```
git branch -m dev1 dev2
```

###  修改远程分支名字

不能直接修改，思路：

1. 在本地的 clone 版本中重命名分支
2. 删除远程待修改的分支名
3. push 本地的新分支名到远程

## 开发提交

###  add 文件

```
git add .
```

.所有更改 可换成指定文件名

###  commit 信息

```
git commit -m 'git test'
[dev1 3275e8a] git test
 1 file changed, 65 insertions(+), 1 deletion(-)
 rewrite README.md (100%)
```

###  合并到本地 master 分支

dev1 分支开发完成切换 master 分支

```
git checkout master
```

进行本地分支 dev1 合并：

```
git merge dev1
Updating 82951ea..444bb8e
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

Fast-forward 信息，“快进模式”合并，这种模式下，删除分支后，会丢掉分支信息，可以用 –no-ff 方式进行 merge ：

```
git merge --no-ff -m "merge with no-ff" dev1
```

如果分支很多，这个分支历史可能就会变得很复杂了，可以使用 rebase，提交的历史会保持线性：

```
git rebase dev1
```

也是进行本地分支 dev1 合并

## 删除本地分支

```
git branch -d dev1
```

这是删除，如果没有完成合并会有提示，以下是强删：

```
git branch -D dev1
Deleted branch dev1 (was 2c81027).
```

## 创建远程分支

```
git push origin master:dev
```
