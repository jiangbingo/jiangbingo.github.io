# Jiang Bin's Personal Site (Quarto)

这是一个基于 [Quarto](https://quarto.org/) 构建的个人简历与博客系统。

## 📂 项目结构

```
.
├── _quarto.yml          # Quarto 项目主配置文件 (导航栏、主题、Giscus 配置)
├── index.qmd            # 中文简历 (首页)
├── index.en.qmd         # 英文简历
├── blog.qmd             # 博客列表页
├── styles.css           # 自定义样式表 (配色、字体、动画)
├── posts/               # 博客文章目录
│   ├── hello-quarto/    # 示例文章目录
│   │   └── index.qmd    # 文章内容
│   └── ...
├── assets/              # 静态资源 (图片、头像)
└── .github/
    └── workflows/       # GitHub Actions 自动部署脚本
```

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

## 📝 内容编辑指南

### 编辑简历
*   **中文版**: 编辑 `index.qmd`。
*   **英文版**: 编辑 `index.en.qmd`。
*   **头像**: 替换 `assets/avatar.jpg` (建议尺寸 400x400)。
*   **简历 PDF**: 替换根目录下的 `江斌-Python.pdf`。

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

### 管理评论 (Giscus)
评论系统基于 GitHub Discussions。
*   **删除/隐藏评论**: 直接访问您 GitHub 仓库的 **Discussions** 标签页，找到对应的讨论帖进行管理。
*   **配置**: 在 `_quarto.yml` 中修改 `giscus` 部分的配置。

## 🔧 常见问题

### 评论区报错 "giscus is not installed"
这是因为 Giscus GitHub App 尚未安装到您的仓库。
1.  访问 [Giscus App](https://github.com/apps/giscus)。
2.  点击 **Install**，选择您的仓库 `jiangbingo/jiangbingo.github.io` 并安装。
3.  确保 `_quarto.yml` 中的 `repo-id` 和 `category-id` 是正确的（在 [giscus.app](https://giscus.app/zh-CN) 上生成）。

### 为什么不需要提交 `_site` 目录？
`_site` 目录是 Quarto 构建生成的静态网站文件。因为我们使用了 GitHub Actions 进行云端自动构建，所以不需要将这些生成的文件提交到源码仓库中，这样可以保持仓库整洁。
