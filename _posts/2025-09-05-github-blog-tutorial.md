---
layout: post
title:  "如何使用 GitHub Pages 和 Jekyll 搭建免费个人博客"
date:   2025-09-05 22:00:00 +0800
categories: tutorial tech
---

# 如何使用 GitHub Pages 和 Jekyll 搭建免费个人博客

本教程将指导您完成从零开始，使用 Jekyll 和 GitHub Pages 搭建一个完全免费、功能强大且易于维护的个人静态博客的完整过程。

## 为什么选择 Jekyll + GitHub Pages？

*   **完全免费**: 托管在 GitHub Pages 上，无需任何服务器费用。
*   **简单高效**: 您只需要用 Markdown 格式写作，Jekyll 会自动生成整个网站。
*   **无缝集成**: GitHub Pages 原生支持 Jekyll，您只需将代码推送到仓库，网站就会自动更新，无需复杂的部署流程。
*   **高度可定制**: 您可以轻松更换主题、修改样式，完全掌控您的博客外观。

---

## 第一步：准备本地开发环境

为了能在发布前在自己电脑上预览效果，我们需要安装必要的工具。对于 macOS 用户，强烈建议使用版本管理器 `rbenv` 来安装一个现代化的 Ruby，以避免与系统自带的旧版 Ruby 产生冲突。

### 1. 安装 rbenv (Ruby 版本管理器)

```bash
brew install rbenv
```

### 2. 配置 rbenv

将 `rbenv` 的初始化脚本添加到您的终端配置中，这样每次打开终端它都能正常工作。

```bash
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
```

然后，**关闭并重新打开一个新的终端窗口**以让配置生效。

### 3. 安装新版 Ruby

我们将安装一个现代、稳定的 Ruby 版本（例如 3.3.0）。

```bash
# 安装 Ruby 3.3.0 (此过程会从源码编译，可能需要几分钟)
rbenv install 3.3.0

# 将 3.3.0 设置为全局默认版本
rbenv global 3.3.0
```

验证一下是否成功，运行 `ruby -v`，应该会显示 `ruby 3.3.0`。

### 4. 安装 Jekyll 和 Bundler

在全新的 Ruby 环境中，安装 Jekyll 和它的依赖管理器 Bundler。

```bash
gem install bundler jekyll
```

至此，您的本地环境已准备就绪。

---

## 第二步：创建并预览您的博客

### 1. 创建一个新的 Jekyll 站点

进入您想存放博客代码的目录，运行以下命令。它会创建一个名为 `my-blog` 的文件夹，并包含博客所需的所有模板文件。

```bash
jekyll new my-blog
```

### 2. 进入项目目录

```bash
cd my-blog
```

### 3. 本地预览

在发布到网上前，先在本地启动一个服务器来实时预览效果。

```bash
bundle exec jekyll serve
```

命令运行后，打开您的浏览器，访问 `http://localhost:4000`。您应该能看到一个默认主题的博客网站。

---

## 第三步：撰写第一篇文章

1.  **找到文章目录**: 您的所有博文都存放在 `_posts` 文件夹中。
2.  **创建文章文件**: 在 `_posts` 目录下创建一个新的 Markdown 文件。**文件名必须遵循 `年-月-日-文章标题.md` 的格式**。
    *   例如: `2025-09-05-how-to-build-a-blog.md`
3.  **添加头信息 (Front Matter)**: 每篇文章的开头，都必须有一个 YAML 格式的“头信息”，用来告诉 Jekyll 这篇文章的标题、布局、日期等元数据。请务必将其放在文件的最顶端。

    ```yaml
    ---
    layout: post
    title:  "这是我的第一篇文章"
    date:   2025-09-05 20:30:00 +0800
    categories: tech life
    ---

    (从这里开始，用 Markdown 格式写您的正文...)

    # 这是一个一级标题

    这是段落内容。
    ```

---

## 第四步：部署到 GitHub Pages

这是最后一步，将您的博客发布到全世界。

### 1. 创建 GitHub 仓库

*   登录您的 GitHub 账户。
*   创建一个 **新的、公开的 (Public)** 仓库。
*   **仓库的名称必须使用一个特殊的格式**：`<your-github-username>.github.io`
    *   例如，如果您的 GitHub 用户名是 `octocat`，那么仓库名就必须是 `octocat.github.io`。

### 2. 关联并推送代码

回到您本地的 `my-blog` 文件夹，在终端里依次执行以下 `git` 命令，将您的博客代码推送到刚刚创建的 GitHub 仓库。

```bash
# 初始化 Git
git init -b main

# 添加所有文件到暂存区
git add .

# 创建第一次提交
git commit -m "Initial blog setup"

# 关联到您的远程 GitHub 仓库 (请将地址替换为您自己的)
git remote add origin https://github.com/your-github-username/your-github-username.github.io.git

# 推送到 GitHub
git push -u origin main
```

### 3. 访问您的线上博客

代码推送成功后，请耐心等待一两分钟。GitHub Pages 会在后台自动构建您的网站。

之后，您就可以通过 `https://<your-github-username>.github.io` 这个网址，看到您线上部署好的博客了。

---

## 第五步：如何更新博客

您的博客已经上线了！之后更新网站的流程非常简单：

1.  在本地的 `_posts` 文件夹里，创建一个新的 Markdown 文件来写新文章。
2.  写完后，在 `my-blog` 目录下，依次运行三条命令：
    ```bash
    git add .
    git commit -m "Post a new article"
    git push
    ```
3.  等待几分钟，您的线上博客就会自动出现新文章。