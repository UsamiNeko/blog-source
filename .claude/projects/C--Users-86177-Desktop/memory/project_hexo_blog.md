---
name: Hexo blog workflow
description: Hexo blog with reimu theme on GitHub Pages. Source in blog-source repo, auto-deploy via GitHub Actions. KaTeX math with CSS fix injected via injector. Obsidian notes converted via script.
type: project
---

Hexo 博客 (UsamiNeko.github.io)：

- 源码仓库：`UsamiNeko/blog-source`，Pages 仓库：`UsamiNeko/UsamiNeko.github.io`
- 部署方式：GitHub Actions (`.github/workflows/deploy.yml`) + `peaceiris/actions-gh-pages`，需要 PAT secret
- 本地构建：`npx hexo generate` / `npx hexo deploy`
- KaTeX 公式修复通过 `_config.reimu.yml` 的 `injector.head_end` 注入 CSS，覆盖主题默认的 flex 冲突
- `autoRender: true` 启用浏览器端兜底渲染
- CDN: `npm.webcache.cn`（中国专用）
- Obsidian 转换脚本在桌面：`convert-obsidian.js`，不要在 `scripts/` 目录下放置

**Why:** 分离源码和产物，CI 自动部署避免本地网络依赖。
**How to apply:** 日常更新只需 `git push` 源码。修改公式相关配置时记得同步更新 injector CSS。
