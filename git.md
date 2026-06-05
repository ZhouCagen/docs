# Git 常用操作笔记

## 1. 初始化仓库

使用 Git 前，需要先建立一个仓库，也就是 repository。

可以使用一个已经存在的目录作为 Git 仓库，也可以创建一个空目录。

### 使用当前目录作为 Git 仓库

```text
git init
```

### 使用指定目录作为 Git 仓库

```text
git init newrepo
```

从现在开始，默认假设命令都是在 Git 仓库根目录下执行。

---

## 2. 添加新文件

仓库刚初始化时，Git 还没有追踪文件。

可以使用 `add` 命令添加文件到暂存区。

```text
git add filename
```

也可以添加当前目录下所有修改：

```text
git add .
```

注意：`git add` 不是提交，只是把文件加入本次提交的准备区。

---

## 3. 提交版本

添加文件后，需要使用 `commit` 真正保存到 Git 仓库。

```text
git commit -m "Adding files"
```

如果不使用 `-m`，Git 会打开编辑器，让你手动写提交说明。

---

## 4. 自动提交已追踪文件的修改

当修改了很多文件，不想每个都手动 `add`，可以使用 `-a` 参数：

```text
git commit -a -m "Changed some files"
```

`-a` 会自动提交：

- 已经被 Git 管理的文件
- 被修改的文件
- 被删除的文件

注意：`-a` 不会提交新文件。

新文件必须先执行：

```text
git add filename
```

或者：

```text
git add .
```

---

## 5. 克隆远程仓库

可以从服务器克隆一个已有仓库：

```text
git clone ssh://example.com/~/www/project.git
```

克隆后，本地就会生成一个 Git 仓库目录。

---

## 6. 推送到远程仓库

修改并提交之后，可以推送到远程服务器：

```text
git push ssh://example.com/~/www/project.git
```

如果已经配置好远程仓库，一般直接：

```text
git push
```

---

## 7. 取回远程更新

如果当前分支已经关联远程分支，可以直接：

```text
git pull
```

`git pull` 会从远程取回更新，并尝试合并到当前分支。

也可以从指定地址拉取：

```text
git pull http://git.example.com/project.git
```

更推荐保持提交历史干净的写法：

```text
git pull --rebase
```

---

## 8. 删除文件

如果想从 Git 仓库中删除文件，可以使用：

```text
git rm file
```

然后提交删除操作：

```text
git commit -m "Delete file"
```

如果只是想让 Git 不再追踪这个文件，但本地文件还保留：

```text
git rm --cached file
```

---

## 9. 分支与合并

Git 的分支操作是在本地完成的，速度很快。

### 创建新分支

```text
git branch test
```

这个命令只会创建分支，不会自动切换过去。

### 切换分支

传统写法：

```text
git checkout test
```

现在更推荐：

```text
git switch test
```

### 创建并切换到新分支

```text
git switch -c test
```

---

## 10. 主分支

早期 Git 默认主分支叫：

```text
master
```

现在更常见的是：

```text
main
```

切换回主分支：

```text
git switch main
```

或者传统写法：

```text
git checkout master
```

---

## 11. 合并分支

假设现在有一个 `test` 分支，想把它的修改合并到主分支。

先切回主分支：

```text
git switch main
```

然后合并：

```text
git merge test
```

意思是：

> 把 `test` 分支的修改合并进当前所在的 `main` 分支。

注意：`merge` 不会自动删除 `test` 分支。

---

## 12. 删除分支

如果分支已经没用了，可以删除：

```text
git branch -d test
```

如果 Git 不让删除，说明它认为这个分支还没有安全合并。

确定不要这个分支时，可以强制删除：

```text
git branch -D test
```

---

## 13. 常用流程总结

### 第一次初始化仓库

```text
git init
git branch -m main
git add .
git commit -m "初始化仓库"
```

### 平时写完代码

```text
git status
git add .
git commit -m "描述本次修改"
```

### 创建分支试代码

```text
git switch -c test
```

### 试完后合并回 main

```text
git switch main
git merge test
```

### 删除试验分支

```text
git branch -d test
```
