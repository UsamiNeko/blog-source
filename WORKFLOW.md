---
name: my-blog workflow reference
description: Hexo 博客 (hexo-theme-reimu) 的完整流程记录，包括本地构建、Obsidian 转换、KaTeX 修复、GitHub Actions 部署
type: project
---

# 我的博客工作流记录

## 仓库结构

| 仓库 | 用途 |
|------|------|
| `UsamiNeko/blog-source` | 博客源码（Hexo 源文件） |
| `UsamiNeko/UsamiNeko.github.io` | GitHub Pages 部署目标（自动生成） |

## 关键文件

| 文件 | 用途 |
|------|------|
| `C:\Users\86177\Desktop\my-blog\_config.yml` | Hexo 根配置（主题、部署目标） |
| `C:\Users\86177\Desktop\my-blog\_config.reimu.yml` | 主题配置（KaTeX、CDN、CSS 修复注入） |
| `C:\Users\86177\Desktop\my-blog\.github\workflows\deploy.yml` | GitHub Actions 自动部署配置 |
| `C:\Users\86177\Desktop\convert-obsidian.js` | Obsidian→Hexo 转换脚本 |

**Why:** 分离源码和产物，GitHub Actions 自动构建部署。
**How to apply:** 日常更新只需 `git push` 源码到 `blog-source`，不要手动改 Pages 仓库。

---

## 日常写作流程

### 1. 在 Obsidian 中写笔记
- 可以用 `$...$` / `$$...$$` LaTeX 公式
- 可以用 `> [!note]` callout 语法
- `[[wikilink]]` 会被转换脚本处理
- DataviewJS 等 Obsidian 插件语法不会被渲染

### 2. 转换笔记为 Hexo 格式
```bash
node C:\Users\86177\Desktop\convert-obsidian.js 笔记路径.md
```
输出文件在 `source/_posts/` 目录。

### 3. 本地预览（可选）
```bash
cd C:\Users\86177\Desktop\my-blog
npx hexo server
```
访问 http://localhost:4000 预览。

### 4. 推送到 GitHub（自动部署）
```bash
cd C:\Users\86177\Desktop\my-blog
git add -A
git commit -m "写清楚改了什么"
git push
```
GitHub Actions 自动构建并部署到 Pages。等待 1-2 分钟后访问 https://UsamiNeko.github.io。

---

## 部署方式

| 方式 | 命令 | 说明 |
|------|------|------|
| GitHub Actions（推荐） | `git push` 即可 | 自动构建，无需本地网络 |
| 本地部署（备用） | `npx hexo deploy` | 需要能访问 GitHub |

---

## 网络问题处理

国内访问 GitHub 不稳定。如果 `git push` 失败：
- 开启 VPN/代理软件
- 或配置 git 代理：`git config --global http.proxy http://127.0.0.1:7890`
- 或使用浏览器 VPN + GitHub 网页上传

---

## KaTeX 公式配置

在 `_config.reimu.yml` 中配置：
- `math.katex.enable: true` — 启用 KaTeX
- `math.katex.autoRender: true` — 浏览器端二次渲染（兜底）
- CDN: `npm.webcache.cn`（中国用户专用）

CSS 修复通过 `injector` 注入，覆盖主题自带的 flex 冲突：

```css
.katex-display > .katex { width: calc(100% - 2px); }
.katex-html:has(span.tag) { display: block !important; }
.katex-display>.katex>.katex-html>.tag { position: absolute !important; right: 0; }
```

**Why:** 主题给 `.katex-html:has(span.tag)` 加了 `display: flex`，导致带 `\tag{}` 的公式中，被等号切分的多个 `.base` 变成 flex 项目，间距被打散。
**How to apply:** 这些 CSS 在 `injector.head_end` 中，随源码一起提交，Actions 构建时自动生效。

---

## 转换脚本说明

`C:\Users\86177\Desktop\convert-obsidian.js`（v4，状态机方式）：
- 处理 frontmatter（YAML 头部）
- `> [!type]` callout → `{% alertBlockquote %}` 或 `<details>`
- `[[page]]` wikilink → 纯文本
- `^anchor-id` → `<span id="">`
- DataviewJS → 普通 JS 操作 DOM
- 保持 `$...$` / `$$...$$` 公式不变

不要把这个脚本放在 `scripts/` 目录下，否则 Hexo 会把它当作插件自动执行。
