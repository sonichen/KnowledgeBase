---
title: 还原原仓库内容到修改的fork仓库
date: 2023-08-20 18:12:38
permalink: /pages/c336d3/
---




本地撤回上一个commit

```
git reset HEAD~1 --hard
```

如果已经 fork 了一个仓库并且进行了修改，但现在想将仓库内容还原成原始仓库的状态，可以按照以下步骤操作：

**注意：在进行以下操作之前，请确保已经备份了修改，因为还原操作将会丢失修改。**

1. **获取原始仓库的 URL：** 首先，需要获取原始仓库的 URL。可以在 GitHub 页面上找到该仓库，并复制其 URL。

2. **添加原始仓库作为远程仓库：** 本地仓库中，打开命令行终端，进入项目目录。运行以下命令来添加原始仓库作为一个远程仓库：

   ```
   git remote add upstream <原始仓库的URL>
   ```
   
   替换 `<原始仓库的URL>` 为您在步骤 1 中复制的原始仓库的 URL。
   
3. **获取原始仓库的内容：** 运行以下命令来获取原始仓库的内容：

   ```
   git fetch upstream
   ```
   
4. **切换到主分支并合并内容：** 运行以下命令来切换到主分支（通常是 `main` 或 `master` 分支），并合并原始仓库的内容：

   ```
   git checkout main  # 或者 git checkout master
   git merge upstream/main  # 替换为原始仓库的分支名
   ```

   这会将原始仓库的内容合并到您的主分支中。

5. **推送更改到您的仓库：** 最后，如果希望将还原后的内容推送到远程仓库（GitHub），运行以下命令：

   ```
   git push origin main  # 或者 git push origin master
   ```
   
这会将合并后的内容推送到远程仓库。