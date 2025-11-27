# 江斌 · GitHub Pages 个人主页

这是一个基于 GitHub Pages 的静态站点，用来展示我的个人简历、代表项目和技术博客。

## 结构说明

- `index.html`：网站首页，包含个人简介、技能栈、代表项目、工作经历、联系方式等内容，并提供 PDF 简历下载链接。
- `江斌-Python.pdf`：完整 PDF 简历。
- `assets/style.css`：站点的统一样式。
- `blog/`：技术博客页面与文章示例。
  - `blog/index.html`：博客列表页。
  - `blog/rag-backend-fastapi.html` 等：具体文章页面。

## 本地预览

在本地可以使用任意静态文件服务器进行预览，例如 Python 自带的：

```bash
python -m http.server 8000
```

然后在浏览器访问 `http://localhost:8000` 即可查看主页。

## 部署到 GitHub Pages（仓库：`jiangbingo.github.io`）

1. 在本地项目根目录执行下面命令，将代码推送到远程仓库：

   ```bash
   git init
   git branch -M main
   git remote add origin git@github.com:jiangbingo/jiangbingo.github.io.git

   git add .
   git commit -m "feat: initial personal site"
   git push -u origin main
   ```

2. 打开 GitHub 上的 `jiangbingo/jiangbingo.github.io` 仓库：进入 **Settings → Pages**，将 Source 设置为：
   - `Deploy from a branch`
   - Branch：`main`
   - Directory：`/ (root)`

3. 保存后等待 1～3 分钟，访问 `https://jiangbingo.github.io` 即可看到上线后的个人主页。
