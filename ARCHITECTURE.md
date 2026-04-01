# 网站架构说明

> 付文鑫个人学术网站 · https://tsinglann.github.io

## 技术栈

| 层级 | 技术 |
|------|------|
| 静态站点生成 | Jekyll (academicpages 模板) |
| 部署 | GitHub Pages (`main` 分支自动构建) |
| 样式 | SCSS（`_sass/`）+ 自定义 CSS（`assets/css/anime-academic.css`） |
| 视觉风格 | Apple Liquid Glass（毛玻璃效果，Inter/Noto Serif SC 字体） |
| 数学公式 | MathJax 3（CDN，支持 `$...$` 行内公式） |
| 图表 | Mermaid、Plotly（按需加载） |

---

## 目录结构

```
/
├── _config.yml              # 站点全局配置（locale、作者信息、插件等）
├── _data/
│   ├── navigation.yml       # 导航菜单（含 title/title_en 双语字段）
│   └── ui-text.yml          # Jekyll 内置 UI 文本多语言库
├── _includes/
│   ├── head/
│   │   └── custom.html      # ★ 核心：暗黑模式 IIFE + 语言 IIFE + 全局函数
│   ├── footer/
│   │   └── custom.html      # ★ 移动端 FAB 按钮 + MathJax/Mermaid 脚本
│   ├── masthead.html         # 顶部导航栏（含语言/主题切换按钮）
│   ├── head.html             # <head> 基础（meta、main.css）
│   └── scripts.html          # 加载 main.min.js（type="module"）
├── _layouts/
│   └── default.html          # 基础页面布局（html > head + body + footer）
├── _pages/
│   ├── about.md              # 首页（中英双语，用 lang-zh/lang-en div 包裹）
│   └── research.md           # 研究页（中英双语）
├── _posts/                   # Blog 帖子（纯中文，无语言 wrapper div）
├── assets/
│   ├── css/
│   │   ├── anime-academic.css  # ★ 主要自定义样式（Liquid Glass 设计）
│   │   └── main.scss           # 入口，导入 _sass/ 下所有 SCSS
│   └── js/
│       ├── _main.js            # JS 源文件（编译后产物为 main.min.js）
│       └── main.min.js         # ★ 实际运行的 JS（type="module"，已预编译）
└── images/                   # 图片资源（头像、背景图、favicon 等）
```

---

## 核心系统详解

### 1. 暗黑模式系统

```
触发链路：
head/custom.html IIFE（立即）
  └─ 读 localStorage['theme']，或检测 OS 偏好
  └─ 写 html[data-theme="dark"]（第一帧前完成，无闪白）

切换：
  PC   → #theme-toggle 按钮 → main.min.js 的 toggleTheme()（模块作用域）
  移动 → FAB #fab-theme-btn → footer/custom.html 自包含逻辑（直接操作 data-theme）

持久化：localStorage['theme'] = 'dark' | 'light'

CSS 依赖：_sass/theme/_default_dark.scss
  html[data-theme="dark"] { --global-bg-color: ...; ... }
```

**注意**：`main.min.js` 以 `type="module"` 加载，其内部 `var toggleTheme` 是模块作用域，不暴露到 `window`。移动端 FAB 因此使用独立实现，不调用模块内函数。

### 2. 语言切换系统

```
触发链路：
head/custom.html IIFE（立即）
  └─ 读 localStorage['site-lang']，默认 'zh'
  └─ 写 html[data-lang="zh" | "en"]

切换：
  PC   → masthead.html [data-lang-btn] 按钮 → onclick="siteToggleLang()"
  移动 → FAB #fab-lang-btn               → onclick="siteToggleLang()"

CSS 控制显示/隐藏：
  html[data-lang="en"] .lang-zh { display: none !important; }
  html[data-lang="zh"] .lang-en { display: none !important; }

导航栏翻译：
  navigation.yml 中 title（中文）/ title_en（英文）
  masthead.html 渲染为 data-zh / data-en 属性
  siteToggleLang() 读属性更新文本
```

**Blog 帖子**：帖子内容**不受语言切换控制**，直接裸写中文 Markdown，无 lang-zh/lang-en wrapper。

**其他页面**（about、research 等）：内容用 `<div class="lang-zh">` / `<div class="lang-en">` 包裹，切换时自动显隐。

### 3. 移动端 FAB（浮动按钮）

```
HTML 位置：footer/custom.html 内的 #mobile-fab-group
运行时位置：被脚本移到 document.body（避免 footer backdrop-filter 破坏 position:fixed）
CSS：position:fixed; bottom:24px; right:16px; z-index:9000
显示条件：@media (max-width: 924px)
```

### 4. 导航响应式

`assets/js/plugins/jquery.greedy-navigation.js`：空间不足时自动将导航项收入下拉菜单（`#site-nav .hidden-links`）。PC 端语言/主题按钮有 `.persist.tail` class，始终保留在可见区域不被收起。

---

## 新内容添加指南

### 添加 Blog 帖子

在 `_posts/` 新建 `YYYY-MM-DD-slug.md`：

```markdown
---
title: '帖子标题'
date: YYYY-MM-DD
permalink: /posts/YYYY/MM/slug/
tags:
  - 标签1
---

正文（纯中文 Markdown，无需 lang wrapper）
```

### 添加双语页面内容

在 `_pages/` 或其他页面中：

```html
<div class="lang-zh" markdown="1">
中文内容
</div>

<div class="lang-en" markdown="1">
English content
</div>
```

### 修改导航菜单

编辑 `_data/navigation.yml`，添加条目时同时填写 `title`（中文）和 `title_en`（英文）。

---

## 部署流程

```
本地修改 → git commit → git push origin main → GitHub Actions 构建 → 自动发布
```

GitHub Pages 仅从 `main` 分支构建（`username.github.io` 仓库限制）。

---

## 已知限制

- `main.min.js` 是预编译文件，修改 `_main.js` 源码后需手动重新 minify 并提交
- Jekyll 不支持 `type="module"` 脚本中的变量自动暴露到全局，跨脚本通信需通过 `window.*` 或 DOM 属性
- iOS Safari 不支持 `background-attachment: fixed`，已通过 `@supports (-webkit-touch-callout: none)` fallback 处理
