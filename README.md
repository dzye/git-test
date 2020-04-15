## 查看分支

### 查看本地分支

```
git branch
* master
```

master 分支前的 \* 字符，它表示当前所在的分支。

### 查看远程所有分支

```
git branch -r
origin/HEAD -> origin/master
origin/master
```

### 列出本地分支和远程分支

```
git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

## 创建本地 dev1 分支

### 直接创建本地分支

```
git checkout -b dev1
Switched to a new branch 'dev1'
```

等同于

```
git branch dev1
git checkout dev1
```

### 从远程分支 dev(远程有该分支)创建本地分支

```
git checkout -b dev1 origin/dev
Switched to a new branch 'dev1'
```

## 修改本地分支名字

```
git branch -m dev1 dev2
```

## 修改远程分支名字

不能直接修改，思路：

1. 在本地的 clone 版本中重命名分支
2. 删除远程待修改的分支名
3. push 本地的新分支名到远程

