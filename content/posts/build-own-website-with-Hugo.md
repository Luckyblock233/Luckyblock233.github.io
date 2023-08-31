---
title: "Build Own Website With Hugo"
date: 2023-09-01T00:31:17+08:00
draft: false
---

[TOC]

### 写在最前面！

爆进爆进爆进！

让大家久等了！深受大家喜爱的学级委员长，樱花进王，参上！

其实委员长我刚刚在马乎上看到了一篇非常棒的文章！其名为《用 Hugo 30 分钟搭建静态博客》！世界最速！轻量化！灵活性！超友好！新手也能轻松使用的！如此……爆进的工具！简直就和时刻准备为了同学们的烦恼爆进的委员长我！一模一样！委员长我！深受感动！

为了更加爆进地解决同学们的烦恼，委员长我决定要用爆进的 Hugo 搭建一个烦恼商谈平台！然而委员长我不擅长这种步骤繁多的事情，于是委员长我立刻就爆进地找到了可靠的训练员先生并向他传达了我的想法！

于是！经过训练员先生一个下午的努力，终于有了这篇——！

——委员长也能轻松掌握！使用 Hugo 搭建个人网站并发布到 GitHub Pages 指南！

来吧！让我们一起爆进地搭建属于自己的个人网站吧！爆进爆进爆进！

### 写在前面

呃呃 git 我操

倒腾一下午好歹是把网站部署成功了、、、稍微记录一下自己踩过的坑。

上面是整活。

因为我对这种东西的原理一窍不通、、、下面只是记录自己的历程，写的是一坨，为了便于参考还会在每一章的开头列出自己查阅过的所有资料。

个性化什么的之后再说。

### HUGO 是什么？

参考：[https://gohugo.io/](https://gohugo.io/)

*The world’s fastest framework for building websites。*

一个基于 Go 语言开发的静态站点生成工具。

选择 Hugo 的原因主要有：
- 快。
- 快。
- 快。
- 简单易用。
- 主题丰富。

### 在 Windows 上安装 Hugo

参考：
- [https://gohugo.io/installation/windows/](https://gohugo.io/installation/windows/)
- [https://zhuanlan.zhihu.com/p/440175312](https://zhuanlan.zhihu.com/p/440175312)

法一：使用 Prebuilt binaries 安装：
- 前往官网下载 Windows 版（`hugo_xxxxx_windows-amd64`）并解压：[https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases)。
- 将解压后的可执行文件所在目录添加到环境变量中并重启计算机。

法二：使用软件包管理器：
- 因为我的电脑上有 Chocolatey[^1] 所以只需要在命令行中运行：
  
  ```txt
  choco install hugo-extended
  ```
- 若使用其他软件包管理器请参考上述链接。

完成安装后启动命令行并运行以下命令，如果成功得到了版本信息说明安装成功：

```txt
hugo version
```

### 安装 git 并学习一点基础用法

参考：
- 推荐观看的 git 教程：[https://www.bilibili.com/video/BV1FE411P7B3/](https://www.bilibili.com/video/BV1FE411P7B3/)  
- git 初次登陆使用：[https://www.cnblogs.com/crazytata/p/10083716.html](https://www.cnblogs.com/crazytata/p/10083716.html)
- Git bash 登录以及 clone、代码提交：[https://www.cnblogs.com/codeAndlearn/p/12298301.html](https://www.cnblogs.com/codeAndlearn/p/12298301.html)

### 对于 Windows 用户的一点建议

参考：
- [https://gohugo.io/getting-started/quick-start/](https://gohugo.io/getting-started/quick-start/)

- 不要使用命令提示符。
- 不要使用 Windows Powershell。
- 请使用 [PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows) 或者 Linux 终端（如 Git Bash）。
- PowerShell 和 Windows PowerShell 是不同的应用：[https://learn.microsoft.com/en-us/powershell/scripting/whats-new/differences-from-windows-powershell?view=powershell-7.3](https://learn.microsoft.com/en-us/powershell/scripting/whats-new/differences-from-windows-powershell?view=powershell-7.3)。

以下所有命令均在 Git Bash 中执行。

### 在本地生成站点文件

参考：
- [https://gohugo.io/getting-started/quick-start/](https://gohugo.io/getting-started/quick-start/)
- [https://zhuanlan.zhihu.com/p/440175312](https://zhuanlan.zhihu.com/p/440175312)
- [https://zhuanlan.zhihu.com/p/45457742](https://zhuanlan.zhihu.com/p/45457742)


首先创建一个用于存放博客文件的文件夹，在该文件夹中运行 Git Bash 并依次运行下列命令：
- `hugo new site myblog`：创建一个名为 `myblog` 的站点文件。运行后可以发现出现了一个名为 `mylobg` 的文件夹。
- `cd myblog`：将 Git Bash 的路径切换到该文件夹中。
- `git init`：初始化站点文件夹的 Git。
- `git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke`：为该站点文件下载主题 Ananke。Hugo 生成的站点必须配置一个主题才能够使用，这里以配置主题 Ananke 为例。
- `echo "theme = 'ananke'" >> hugo.toml` 将文件 `hugo.toml` 中的属性 `theme` 设置为 `ananke`，作用是设置该站点的主题为 Ananke，这个文件可以在文件夹 `myblog` 中找到，也可以手动修改该文件的属性来调整站点的设置。
- `hugo server`：在本地运行站点。

如果上述指令均成功运行，应该会得到类似下列信息：

```txt
Watching for changes in C:\Users\Luckyblock233\Desktop\work_station\blog\myblog\{archetypes,assets,content,data,layouts,static,themes}
Watching for config changes in C:\Users\Luckyblock233\Desktop\work_station\blog\myblog\hugo.toml, C:\Users\Luckyblock233\Desktop\work_station\blog\myblog\themes\ananke\config.yaml
Start building sites …
hugo v0.117.0-b2f0696cad918fb61420a6aff173eb36662b406e+extended windows/amd64 BuildDate=2023-08-07T12:49:48Z VendorInfo=gohugoio


                   | EN
-------------------+-----
  Pages            |  7
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  1
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Built in 101 ms
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

恭喜！此时在浏览器中访问 [http://localhost:1313/](http://localhost:1313/) 即可在本地浏览站点了。

此时再按 `Ctrl+C` 即可停止在本地运行。

在此过程中可能遇到的问题：
- 检查是否是以管理员身份运行 Git Bash。
- 安装主题时提示 `connect reset`：脸不好，试试挂个梯子。
- 挂了梯子之后出现 `Github port 443 : Timed out`：见 [https://zhuanlan.zhihu.com/p/636418854](https://zhuanlan.zhihu.com/p/636418854)。

### 添加内容

在 `myblog` 文件夹中运行 Git Bash 并执行下列指令：

```txt
hugo new content posts/my-first-post.md
```

即可在文件夹 `myblog/content/posts` 中创建一篇名为 `my-first-post.md` 的文章。使用文本编辑器打开：

```
---
title: "My First Post"
date: 2023-08-31T23:10:39+08:00
draft: true
---

```

上述被 `---` 框起来的内容为 Hugo 文章的表头元素。上述三行表头元素分别描述了这篇文章的标题、发布日期、是否为草稿。尝试在文章的正文部分添加一些内容，并将草稿元素设为 `false`，如下：

```txt
---
title: "My First Post"
date: 2023-08-31T23:10:39+08:00
draft: false
---

你好！我是樱花进王！

正如您所看到的，是一名优秀的委员长！

为了成为大家的榜样，上吧！爆进！
```

此时再执行指令 `hugo server` 在浏览器中访问 [http://localhost:1313/](http://localhost:1313/) 就可以看到刚才添加的内容了。

### 部署到 Github Page 并实现自动发布文章

参考：
- 主要参考：[https://gohugo.io/hosting-and-deployment/hosting-on-github/](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
- Git bash 登录以及 clone、代码提交：[https://www.cnblogs.com/codeAndlearn/p/12298301.html](https://www.cnblogs.com/codeAndlearn/p/12298301.html)

首先确保在上述安装 git 并学习一点基础用法章节中，完成了执行登陆用户名和密码命令与配置公钥私钥的操作，并学习了 git 的基本用法。

- 首先创建一个与 Github 的 username 同名的 空 `username.github.io` 仓库，不包含包括 `README.md` 的任何内容。比如我的该仓库名为：`Luckyblock233.github.io`。
- 打开该仓库，进入 `Settings->Pages`，并将该页面中的 `Build and deployment` 选项中 `Source` 改为 `GitHub Actions`。
- 在 `myblog` 文件夹中新建名为 `.github` 的文件夹，在 `.github` 文件夹中新建名为 `workflows` 的文件夹，在 `workflows` 文件夹中新建文件 `hugo.yaml`。此文件为实现自动发布文章的配置文件。
- 将下列内容复制到文件 `hugo.yaml` 中，注意可能需要对使用 `#########` 标出的部分进行修改：

```txt
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main #########修改为当前仓库 branch 的名称，默认为 main，一般不用修改

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.115.4  #########修改为当前使用的 Hugo 版本，可以通过 hugo version 指令进行查看
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb          
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v3
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"          
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

- 完成上述操作后，在某个文件夹中运行 Git Bash 并执行下列指令：
- `git clone https://github.com/Luckyblock233/Luckyblock233.github.io Luckyblock233.github.io`，表示将仓库内容克隆到本地文件夹 `Luckyblock233.github.io` 中。**这一部分中 `Luckyblock233.github.io` 是我的仓库的名称，仅用作示例，请务必记得改成自己仓库的名称。**
- 将个人站点中的内容复制到文件夹 `Luckyblock233.github.io` 中。
- 依次执行下列指令来将个人站点发布到 Github 中：
  - `cd Luckyblock233.github.io`。
  - `git add .` 将该文件夹中的内容添加到 git 的暂存区。
  - `git commit -m "Init the website"`：准备将本地仓库的内容合并到远程仓库中，将设置此次合并的信息设置为 `Init the website`。
  - `git push git@github.com/Luckyblock233/luckyblock233.github.io.git main`：将本地仓库内容 push 合并到远程仓库的 main 分支中。注意不要忘记第三个参数前后的 `git@` 和 `.git`。

完成上述步骤后进入 Github 对应仓库的 Actions 界面中即可查看当前部署的进度。当进度完成后使用浏览器访问 [luckyblock233.github.io](luckyblock233.github.io) 即可。

之后在本地仓库更新内容后，只需要重复上述最后三条指令 `add`、`commit` 和 `push` 即可更新个人站点。

恭喜！你已经成功地获得了自己的个人站点了！

在此过程中可能遇到的问题：
- 检查是否是以管理员身份运行 Git Bash。
- 安装主题时提示 `Recv failure: Connection was reset`：脸不好，试试挂个梯子。
- 挂了梯子之后出现 `Github port 443 : Timed out`：见 [https://zhuanlan.zhihu.com/p/636418854](https://zhuanlan.zhihu.com/p/636418854)。
- 将本地仓库 push 到 Github 中时失败：尝试在 push 之前先执行一句 `git pull git@github.com/Luckyblock233/luckyblock233.github.io.git main` 将远程仓库拉取到本地以同步版本。
- `git pull` 提示 `fatal: refusing to merge unrelated histories`：[https://zhuanlan.zhihu.com/p/152049408](https://zhuanlan.zhihu.com/p/152049408)。改为指令 `git pull xxxxx xxxxx --allow-unrelated-histories` 即可。

### 个性化网站

前往 [https://themes.gohugo.io/](https://themes.gohugo.io/) 即可下载多种主题。

在各主题 Github 主页中的 README 文档里均列出了主题的个性化指南。

刚才使用的 Ananke 主题的 Github 主页为：[https://github.com/theNewDynamic/gohugo-theme-ananke](https://github.com/theNewDynamic/gohugo-theme-ananke)。

~~因为很麻烦而且我还在摸索~~交给读者自行摸索。

之后可能会记录自己博客的个性化历程。

### 写在最后

欢迎访问：[https://luckyblock233.github.io/](https://luckyblock233.github.io/)！

一个月前看到了[【网站公告】园子被处罚，请大家不要发布/转载任何网络小说](https://www.cnblogs.com/cmt/p/17497412.html) 紧急下架了自己博客里的所有文学相关内容并把早就想干的捣鼓个人站点提上进程。然而时至今日才捣鼓好，令人感慨。

进王我真的好喜欢你啊为了你我要用你刷 9 力种马、、、

[^1]: [Chocolatey](https://chocolatey.org/) is a free and open source package manager for Windows.