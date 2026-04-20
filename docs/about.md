# 关于本站

## 这是什么

Financial & Tech News Archive 是一个 **自动化的日度报告归档站**，内容由 [Claude Cowork](https://claude.ai) 的定时任务每天生成并推送到本 GitHub 仓库，GitHub Pages 自动构建部署。

站点包含两条独立的 Routine：

| Routine | 频率 | 运行时间 (BJT) | 产出 |
|---|---|---|---|
| **港美股盘前脉搏** | 周一至周五 | 08:30 | 11 只港美股复盘 + 预测 + 持股建议 |
| **AI 大事件深度拆解** | 每天 | 09:00 | 1-2 条核心 AI 事件的产品+工程双视角分析 |

## 目录结构约定

```
docs/
├── index.md              # 站点首页
├── about.md              # 本页
├── finance/
│   ├── index.md          # 财经板块索引
│   └── posts/
│       └── YYYY-MM-DD-stock-pulse.md
└── ai-tech/
    ├── index.md          # AI 科技板块索引
    └── posts/
        └── YYYY-MM-DD-ai-deep-dive.md
```

每篇文章的文件名约定 `YYYY-MM-DD-<slug>.md`，以便排序与快速定位。

## 文章 Frontmatter 约定

每篇报告需要包含 Material Blog 插件规定的 frontmatter：

```yaml
---
date:
  created: 2026-04-21
categories:
  - 港股
  - 美股
  - 复盘
tags:
  - NVDA
  - 腾讯
authors:
  - claude-cowork
---
```

## 本地预览方式

```bash
# clone
git clone https://github.com/DMLayMan/Financial-TechNews.git
cd Financial-TechNews

# 安装依赖
pip install -r requirements.txt

# 本地预览
mkdocs serve
# 打开 http://127.0.0.1:8000
```

## 免责声明

本站所有内容由大语言模型生成，**不构成任何投资建议或专业咨询**。市场预测仅为模型基于公开信息的推断，可能存在事实错误或判断偏差。读者应自行判断并承担相应风险。
