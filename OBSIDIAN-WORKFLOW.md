# Obsidian → GitHub 工作流指南

这份文档详细说明如何在 Obsidian 中写作，并发布到 GitHub Pages。

## 📁 在 Obsidian 中设置

### 1. 创建文件夹结构

在你的 Obsidian vault 中创建：

```
03-Writing/
  └── 01-Tech-Blog/
```

### 2. 创建模板（可选）

在 Obsidian 中创建一个模板文件 `Templates/Tech-Blog-Template.md`：

```markdown
---
title: "{{ title }}"
date: {{ date }}
tags: []
published: false
---

# {{ title }}

正文内容...
```

使用 Templater 或 Core Templates 插件可以快速创建新文章。

## ✍️ 写作流程

### 每次写新文章

1. **创建文件**：在 `03-Writing/01-Tech-Blog/` 中创建新的 `.md` 文件
   
2. **添加 Frontmatter**：
   ```yaml
   ---
   title: "你的文章标题"
   date: 2026-01-16
   tags: [技术, 思考]
   published: false  # 先保持草稿状态
   ---
   ```

3. **写作**：使用 Obsidian 的所有功能
   - 双链 `[[链接]]` 在博客中会变成普通链接
   - 图片需要使用标准 Markdown 语法 `![](url)`
   - 代码块完全支持

4. **完成后**：将 `published` 改为 `true`

### 发布到 GitHub

#### 方法 A：手动复制（简单但重复）

每次发布时：

```bash
# 1. 进入你的 tech-blog 仓库
cd /path/to/tech-blog

# 2. 复制文章（手动或用脚本）
cp /path/to/obsidian/vault/03-Writing/01-Tech-Blog/*.md _posts/

# 3. 重命名为 Jekyll 格式（如果需要）
# 格式：YYYY-MM-DD-title.md

# 4. 提交并推送
git add _posts/
git commit -m "Add new post"
git push
```

#### 方法 B：符号链接（一次设置，永久使用）

**macOS/Linux:**

```bash
cd /path/to/tech-blog
rm -rf _posts  # 删除原来的 _posts 文件夹
ln -s /path/to/obsidian/vault/03-Writing/01-Tech-Blog _posts
```

**Windows (PowerShell，管理员权限):**

```powershell
cd C:\path\to\tech-blog
Remove-Item _posts
New-Item -ItemType SymbolicLink -Path _posts -Target "C:\path\to\obsidian\vault\03-Writing\01-Tech-Blog"
```

设置后，每次只需：

```bash
cd /path/to/tech-blog
git add _posts/
git commit -m "Update posts"
git push
```

#### 方法 C：自动化脚本（高级）

创建一个 shell 脚本 `sync-posts.sh`：

```bash
#!/bin/bash

OBSIDIAN_PATH="/path/to/obsidian/vault/03-Writing/01-Tech-Blog"
BLOG_PATH="/path/to/tech-blog/_posts"

# 同步所有 published: true 的文章
rsync -av --include="*.md" --exclude="*" "$OBSIDIAN_PATH/" "$BLOG_PATH/"

# 自动提交
cd /path/to/tech-blog
git add _posts/
git commit -m "Sync posts from Obsidian $(date +%Y-%m-%d)"
git push

echo "✅ Posts synced and pushed to GitHub!"
```

使用：

```bash
chmod +x sync-posts.sh
./sync-posts.sh
```

## 📝 文件命名规范

Jekyll 要求文章文件名格式为：`YYYY-MM-DD-title.md`

**在 Obsidian 中的建议：**

1. **简单方式**：直接用这个格式命名
   - `2026-01-16-my-first-post.md`
   - 优点：直接复制即可
   - 缺点：在 Obsidian 中排序不直观

2. **混合方式**：用友好的名称 + 脚本重命名
   - Obsidian 中：`我的第一篇文章.md`
   - 发布时用脚本根据 frontmatter 的 date 重命名

## 🖼️ 处理图片

### 方法 1：使用外部图床

在 Obsidian 中上传到：
- Imgur
- Cloudinary  
- GitHub Issues（免费图床）

然后使用完整 URL：

```markdown
![](https://i.imgur.com/xxxxx.png)
```

### 方法 2：使用 GitHub 仓库

1. 在 tech-blog 仓库创建 `assets/images/` 文件夹
2. 上传图片
3. 在文章中引用：

```markdown
![](/assets/images/my-image.png)
```

### 方法 3：Obsidian 本地图片

如果你的 Obsidian attachments 文件夹在 vault 内：

1. 设置符号链接：
   ```bash
   ln -s /path/to/obsidian/vault/attachments /path/to/tech-blog/assets/images
   ```

2. 在文章中使用相对路径：
   ```markdown
   ![](/assets/images/screenshot.png)
   ```

## 🏷️ 标签管理

建议建立一个标签系统：

- `技术` - 技术教程和笔记
- `代码` - 代码片段和解决方案
- `思考` - 技术思考和观点
- `工具` - 工具使用心得
- `项目` - 项目相关记录

在 Obsidian 中可以用 Dataview 查看所有技术博客文章：

```dataview
TABLE tags, date, published
FROM "03-Writing/01-Tech-Blog"
SORT date DESC
```

## ⚙️ Obsidian 插件推荐

### 必备插件

1. **Templater** - 快速创建文章模板
2. **Natural Language Dates** - 智能日期输入
3. **Tag Wrangler** - 批量管理标签

### 可选插件

1. **Dataview** - 查询和管理文章
2. **Calendar** - 日历视图
3. **Git** - 直接在 Obsidian 中推送（需要配合符号链接）

## 📊 Dataview 查询示例

查看所有已发布的文章：

```dataview
TABLE date, tags
FROM "03-Writing/01-Tech-Blog"
WHERE published = true
SORT date DESC
```

查看草稿：

```dataview
LIST
FROM "03-Writing/01-Tech-Blog"
WHERE published = false OR !published
```

## 🔄 更新现有文章

1. 在 Obsidian 中修改文章
2. 保存
3. 如果使用符号链接：直接 push
4. 如果手动复制：重新复制文件并 push

## 💡 最佳实践

1. **统一格式**：始终使用 YAML frontmatter
2. **先草稿后发布**：写作时 `published: false`，完成后改 `true`
3. **定期备份**：Obsidian vault 和 GitHub 仓库都要备份
4. **使用版本控制**：每次重要修改都 commit
5. **测试后发布**：可以先在本地预览（`bundle exec jekyll serve`）

## 🚨 注意事项

1. **文件名冲突**：确保文章标题唯一
2. **日期格式**：严格使用 `YYYY-MM-DD` 格式
3. **Obsidian 特有语法**：双链 `[[]]` 在博客中可能不工作
4. **图片路径**：使用绝对路径或外部链接
5. **YAML 格式**：冒号后必须有空格，字符串建议用引号

---

祝写作愉快！🎉
