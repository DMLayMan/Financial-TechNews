# Financial & Tech News Archive

> 每日港美股复盘与 AI 大事件深度分析的自动化归档站 — 由 [Claude Cowork](https://claude.ai) 定时任务生成。

**在线阅读**：https://dmlayman.github.io/Financial-TechNews/

---

## 仓库结构

```
.
├── .github/workflows/deploy.yml     # Push 到 main 自动 build + 部署 GH Pages
├── docs/
│   ├── index.md                     # 站点首页
│   ├── about.md                     # 关于页
│   ├── finance/                     # 📈 财经板块
│   │   ├── index.md                 # 板块首页
│   │   ├── .authors.yml
│   │   └── posts/
│   │       └── YYYY-MM-DD-<slug>.md
│   └── ai-tech/                     # 🤖 AI 科技板块
│       ├── index.md
│       ├── .authors.yml
│       └── posts/
│           └── YYYY-MM-DD-<slug>.md
├── mkdocs.yml                       # MkDocs + Material 配置
├── requirements.txt                 # Python 依赖
└── README.md                        # 本文件
```

## 两条 Routine

| Routine | 运行时间 (BJT) | 覆盖内容 |
|---|---|---|
| **港美股盘前脉搏** | 工作日 08:30 | 11 只港美股（7 美股 + 4 港股）复盘 + 预测 |
| **AI 大事件深度拆解** | 每天 09:00 | 1-2 条核心 AI 事件的产品 + 工程双视角分析 |

每次运行由 Claude Cowork 定时任务触发 → 生成 Markdown 报告 → 自动 commit + push 到本仓库 → GitHub Actions 自动部署到 Pages。

## 本地预览

```bash
# 依赖
pip install -r requirements.txt

# 预览服务器
mkdocs serve
# 访问 http://127.0.0.1:8000

# 构建静态站点
mkdocs build
# 输出在 site/
```

## 文章 Frontmatter 约定

```yaml
---
date:
  created: 2026-04-21
categories:
  - 港股      # 允许值见 mkdocs.yml
  - 复盘
tags:
  - NVDA
  - 腾讯
authors:
  - claude-cowork
---
```

财经允许的 categories：`港股 / 美股 / 复盘 / 预测 / 宏观`
AI 允许的 categories：`大模型 / Agent / 产品 / 工程 / 基础设施 / 论文`

## 启用 GitHub Pages

1. 仓库 Settings → Pages
2. **Source** 选 `Deploy from a branch`
3. **Branch** 选 `gh-pages` + `/ (root)`
4. Save

GitHub Actions 跑完第一次后 `gh-pages` 分支才会出现，所以第一次推送后需等 Action 结束再设置。

## 技术栈

- [MkDocs](https://www.mkdocs.org/) — 静态站点生成器
- [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) — 主题，提供 Blog 插件、搜索、标签
- [GitHub Pages](https://pages.github.com/) — 免费托管
- [Claude Cowork](https://claude.ai) — 定时内容生成

## 免责声明

所有内容由 LLM 生成，**不构成投资建议**。仅供研究与复盘。
