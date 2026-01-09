# bill bai's blog

🐸 Where I share my thoughts on random stuff.

个人博客，使用 Hugo + PaperMod 主题搭建，部署在 GitHub Pages。

## 🚀 在线访问

**https://blog.billbai.me/**

## 🛠️ 技术栈

- **静态站点生成器**: [Hugo](https://gohugo.io/) (Extended)
- **主题**: [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **部署**: GitHub Pages
- **CI/CD**: GitHub Actions
- **字体**: [霞鹜文楷 (LXGW WenKai)](https://github.com/lxgw/LxgwWenKai)
- **数学公式**: KaTeX

## 📦 本地开发

### 克隆仓库

```bash
git clone --recurse-submodules https://github.com/billbai/billbai.github.io.git
cd billbai.github.io
```

如果忘记使用 `--recurse-submodules`，可以手动初始化主题：

```bash
git submodule update --init --recursive
```

### 启动开发服务器

```bash
hugo server -D
```

访问 http://localhost:1313 查看博客。

### 创建新文章

```bash
hugo new content/posts/my-new-post.md
```

### 构建站点

```bash
hugo --minify
```

生成的静态文件位于 `public/` 目录。

## 📁 目录结构

```
.
├── .github/workflows/   # GitHub Actions 自动部署
├── archetypes/          # 内容模板
├── assets/             
│   └── css/extended/    # 自定义 CSS（字体、样式）
├── content/
│   ├── posts/           # 博客文章
│   ├── archives.md      # 归档页面
│   └── search.md        # 搜索页面
├── layouts/
│   └── partials/        # 自定义部分模板（KaTeX）
├── static/              # 静态资源（favicon, avatar）
├── themes/PaperMod/     # 主题（Git submodule）
└── hugo.toml            # Hugo 配置文件
```

## ✨ 特性

- 📱 响应式设计，支持深色/浅色模式
- 🔍 全文模糊搜索
- 🏷️ 标签和归档页面
- 📊 阅读时间和字数统计
- 📋 代码高亮和一键复制
- 🧮 数学公式支持（KaTeX）
- 🌐 多平台字体优化
- 🎨 霞鹜文楷中文字体

## 🚀 部署

每次推送到 `main` 分支，GitHub Actions 会自动构建并部署到 GitHub Pages。
