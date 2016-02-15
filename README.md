# 实践 GitHub Flow

我在上一篇「今天让我们忘记 git-flow」中，提到了 GitHub Flow。但该如何进行，从哪里开始对于不少人可能仍然存在疑问，今天就尝试从头开始完成一个 GitHub Flow 的流程。

假定你已经知道了

- Git 的基本命令
- 有了一个 GitHub 账号

在本文中，你将学到

- GitHub Flow 完整流程
- 只通过命令行完成 GitHub Flow
- 真实的 GitHub repo 现场

## GitHub Flow 怎么玩

> GitHub Flow 是一个轻量级，分支为基础的工作流。

- 创建一个分支
- 在分支上提交更改，并写好 commit 说明
- 发起一个 Pull Request
- 讨论和审核代码
- 合并并发布

在创建分支前，你可以在自己的 fork 进行也可以在 repo 中进行，也可以不实用，我们现在假定你不使用 fork，更改都在同一个 repo 中进行。

## 用 hub 来玩的更爽

在使用 GitHub 中，常常因为要发起 Pull Request 等操作要打开 web 页面，产生切换工具的中断。你要么忍受，要么升级你的工具链，让自己编码过程更流畅，更爽些。

现在有两个相对成熟的工具可以帮助到你

- hub
- github-gem

这两个都是你的选择，我更倾向于使用 hub，因为它可以通过 homebrew 安装，让环境更为清爽和便于维护。

```
$ brew install hub
```

哦了，你现在就可以使用 hub 完成很多 GitHub 相关的操作了。

## 来玩一次

现在就让我们来玩一次 GitHub Flow。

先创建一个 repo

```
$ mkdir github-flow-practice
$ cd github-flow-practice
$ hub init
$ hub create github-flow-practice
```
>*注：第一次运行 hub create 时会需要输入你的 GitHub 用户名和密码*

你没看错，根本不需要打开网页，直接在你的终端就创建了一个 GitHub 的 repo。

创建成功后，你就可以看到如下的信息（你会发现你甚至不需要输入你的 GitHub username）

```
origin	git@github.com:p2p-pub/github-flow-practice.git (fetch)
origin	git@github.com:p2p-pub/github-flow-practice.git (push)
created repository: 0dayZh/github-flow-practice
```

你可以先添加一个 `.gitignore` 文件并推到远程的 master 分支，确保 master 分支创建成功了。

为了便于描述，我们创建一个新的分支，用来添加 README.md

```
$ git checkout -b add-readme-markdown
```

将你本地的新分支推送到 GitHub 的 repo

```
$ git push origin add-readme-markdown
```

在新分支添加一个新的 README.md 文件到当前的 repo

```
$ vim README.md
```

创建成功后，提交一个 commit 保存 README.md 文件，并提交到到远程分支

```
$ git add .
$ git commit -m "Add README.md"
$ git push origin add-readme-markdown
```

在实际工作流中，你如果想看到其他人在改什么，你只需要运行 `$ git fetch` 就拉取到所有的远端分支，其他人在什么分支工作就一目了然了。

你想看下当前分支和主分支的对比时，随时都可以看，只需要运行

```
$ hub compare
```

会带在你的默认浏览器中打开了 compare 的页面，一目了然。

好了，更改完成后，我们就可以发起 Pull Request 了。

```
$ hub pull-request -m "Init and add README.md"
```

和你的伙伴展开愉快的讨论，并确保没有问题后，就可以将这个 pr 做 merge 了。

一切看起来就是这么轻松和自然，按照人可以读懂的方式书写你的 commit message 会有很大的帮助。

## 参考

- [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/)
- [hub repo](https://github.com/github/hub)
- [今天让我们忘记 git-flow](http://mp.weixin.qq.com/s?__biz=MzIwMTIzMzIzMg==&mid=409814682&idx=1&sn=f3ce47fbd13a070e74809c81a2038f19#rd)
- [github-flow-practice repo](https://github.com/0dayZh/github-flow-practice)
