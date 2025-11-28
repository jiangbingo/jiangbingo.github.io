# Jiang Bin's Personal Site (Quarto)

这是一个基于 [Quarto](https://quarto.org/) 构建的个人简历与博客系统。

## 🚀 快速开始

### 1. 本地预览
确保已安装 Quarto，在项目根目录运行：
```bash
quarto preview
```

### 2. 自动化部署 (GitHub Pages)
本项目已配置 GitHub Actions 自动部署。
1.  将代码推送到 GitHub 的 `master` 分支。
2.  GitHub Actions 会自动构建并发布到 `gh-pages` 分支。
3.  在 GitHub 仓库设置 -> Pages 中，确保 Source 选择 `Deploy from a branch`，分支选择 `gh-pages` / `(root)`。

## 📝 如何编辑内容

### 编辑简历 (首页)
*   打开 `index.qmd`。
*   直接修改 Markdown 内容（如“个人简介”、“技能栈”、“代表项目”）。
*   **头像**：替换 `assets/avatar.jpg`。
*   **简历 PDF**：替换根目录下的 `江斌-Python.pdf`。

### 写新博客
1.  在 `posts/` 目录下创建一个新文件夹，例如 `posts/my-new-post/`。
2.  在其中新建 `index.qmd` 文件。
3.  文件头部需包含以下元数据：
    ```yaml
    ---
    title: "文章标题"
    description: "文章简介"
    author: "Jiang Bin"
    date: "2024-11-28"
    categories: [Python, AI]
    ---
    ```
4.  正文支持 Markdown、代码块和数学公式。

## 🔧 常见问题修复

### 评论区报错 "giscus is not installed"
这是因为 Giscus GitHub App 尚未安装到您的仓库。
1.  访问 [Giscus App](https://github.com/apps/giscus)。
2.  点击 **Install**，选择您的仓库 `jiangbingo/jiangbingo.github.io` 并安装。
3.  确保 `_quarto.yml` 中的 `repo-id` 和 `category-id` 是正确的（在 [giscus.app](https://giscus.app/zh-CN) 上生成）。

## 🎨 自定义样式
*   修改 `styles.css` 可以调整字体、颜色和布局细节。
*   `_quarto.yml` 控制全局导航栏和主题设置。
