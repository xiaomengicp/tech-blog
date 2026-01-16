# Tech Blog - 技术博客

一个简洁优雅的静态技术博客，基于 Jekyll + GitHub Pages，支持从 Obsidian 直接发布。

## 🎨 特性

- **Editorial Minimalism 设计风格**：像高质量技术期刊的排版
- **深浅模式切换**：支持 Light/Dark 主题，自动记忆偏好
- **标签分类系统**：支持多标签，可点击筛选
- **Obsidian 集成**：直接在 Obsidian vault 中写作
- **自动部署**：Push 到 GitHub 自动发布
- **响应式设计**：完美支持移动端阅读

## 🚀 快速开始

### 1. 创建 GitHub Repository

1. 在 GitHub 创建新仓库，命名为 `tech-blog`（或其他名称）
2. Clone 这个博客项目到本地
3. 推送到你的 GitHub 仓库

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/tech-blog.git
git push -u origin main
```

### 2. 配置 GitHub Pages

1. 进入仓库的 Settings → Pages
2. Source 选择 "GitHub Actions"
3. 等待第一次构建完成（约 1-2 分钟）
4. 访问 `https://YOUR_USERNAME.github.io/tech-blog`

### 3. 修改配置

编辑 `_config.yml`：

```yaml
title: Tech Notes  # 你的博客名称
description: 技术笔记与思考  # 博客描述
url: "https://YOUR_USERNAME.github.io"  # 你的 GitHub Pages URL
baseurl: "/tech-blog"  # 如果部署在子目录

author:
  name: Your Name
  email: your.email@example.com
```

## ✍️ 写作工作流

### 在 Obsidian 中写作

1. **创建文件夹**：在你的 Obsidian vault 中创建 `03-Writing/01-Tech-Blog/`

2. **写文章**：在该文件夹中创建 Markdown 文件，使用以下 frontmatter：

```yaml
---
title: "你的文章标题"
date: 2026-01-16  # 发布日期
tags: [技术, 代码, AI]  # 标签（可选）
published: true  # 设置为 true 才会发布
---

你的文章内容...
```

3. **控制发布状态**：
   - `published: true` → 文章会在博客上显示
   - `published: false` 或不写 → 保持草稿状态

### 发布到 GitHub

有两种方式：

#### 方式 1：手动复制（推荐初学者）

1. 将 Obsidian 中写好的文章复制到 `_posts/` 文件夹
2. 文件命名格式：`YYYY-MM-DD-title.md`（例如：`2026-01-16-welcome.md`）
3. 推送到 GitHub：

```bash
git add _posts/
git commit -m "Add new post"
git push
```

#### 方式 2：符号链接（高级用户）

在 `_posts/` 创建指向 Obsidian 文件夹的符号链接：

```bash
# macOS/Linux
ln -s /path/to/your/obsidian/vault/03-Writing/01-Tech-Blog _posts

# Windows (需要管理员权限)
mklink /D _posts "C:\path\to\obsidian\vault\03-Writing\01-Tech-Blog"
```

然后只需：

```bash
git add _posts/
git commit -m "Update posts"
git push
```

## 📝 Frontmatter 字段说明

```yaml
---
title: "文章标题"          # 必需
date: 2026-01-16           # 必需，格式 YYYY-MM-DD
tags: [标签1, 标签2]       # 可选，用于分类
published: true            # 必需，控制是否发布
excerpt: "简短摘要"        # 可选，首页显示的摘要
---
```

## 🎨 自定义样式

### 修改颜色

编辑 `assets/css/style.css` 中的 CSS 变量：

```css
:root {
  --accent: #2563eb;  /* 强调色 */
  --bg-primary: #fafaf8;  /* 背景色 */
  /* ... 其他颜色 */
}
```

### 修改字体

在 `_layouts/default.html` 中修改 Google Fonts 引入：

```html
<link href="https://fonts.googleapis.com/css2?family=YOUR_FONT&display=swap" rel="stylesheet">
```

然后在 `style.css` 中更新 `--font-serif` 或 `--font-sans` 变量。

## 📂 项目结构

```
tech-blog/
├── _config.yml           # Jekyll 配置
├── _layouts/             # 页面布局
│   ├── default.html      # 主布局
│   └── post.html         # 文章布局
├── _posts/               # 文章目录（从 Obsidian 同步）
├── assets/               # 静态资源
│   ├── css/
│   │   └── style.css     # 主样式表
│   └── js/
│       └── theme-switcher.js  # 主题切换
├── index.html            # 首页（文章列表）
├── .github/
│   └── workflows/
│       └── deploy.yml    # 自动部署配置
├── Gemfile               # Ruby 依赖
└── README.md             # 本文件
```

## 🔧 本地预览

如果想在本地预览博客：

1. 安装 Ruby 和 Bundler
2. 安装依赖：

```bash
bundle install
```

3. 启动本地服务器：

```bash
bundle exec jekyll serve
```

4. 访问 `http://localhost:4000`

## 💡 使用技巧

### 1. 使用草稿

在 Obsidian 中写作时，默认不设置 `published` 或设置为 `false`，这样文章不会发布到博客上。完成后再改为 `true`。

### 2. 批量管理标签

在首页可以点击标签筛选文章，URL 会变成 `#标签名`，可以分享特定标签的文章列表。

### 3. 定时发布

文章的 `date` 字段可以设置未来日期，Jekyll 会自动隐藏未来的文章。

### 4. 自定义域名

在 GitHub 仓库根目录添加 `CNAME` 文件，内容为你的域名：

```
blog.yourdomain.com
```

然后在你的域名 DNS 设置中添加 CNAME 记录指向 `YOUR_USERNAME.github.io`。

## 🐛 常见问题

### Q: Push 后博客没有更新？

A: 查看 GitHub Actions 的构建日志（仓库页面的 Actions 标签），看是否有错误。

### Q: 样式没有加载？

A: 检查 `_config.yml` 中的 `baseurl` 是否正确设置。

### Q: 文章没有显示？

A: 确认：
1. 文件名格式是否正确（`YYYY-MM-DD-title.md`）
2. frontmatter 中 `published` 是否为 `true`
3. `date` 是否为过去或今天的日期

## 📄 许可证

MIT License - 自由使用和修改

---

享受写作！如有问题，欢迎提 Issue。
