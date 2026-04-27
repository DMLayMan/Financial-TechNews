# AI 周报 · 2026-04-21 ~ 2026-04-27

## 0. 本周一句话摘要（TL;DR）

- **底层大移动**：TSMC Q1 利润增长 58%，HBM 产能 93% 转向 AI，CoWoS 瓶颈 4 倍扩产；Amazon 追加 25 亿美金投资 Anthropic，总承诺达 250 亿
- **模型新版本**：DeepSeek V4 (1.6T MoE / 1M tokens / $0.14-1.74) 于 4/24 开源发布；Claude Opus 4.7 (4/16) 支持 2576px 图像，Gemini 3 Flash 与 3.1 Flash-Lite 竞速；GPT-5.5 完成预训练待宣布
- **Agent 基建**：Microsoft Agent Framework 1.0 (4/3) 统一 Semantic Kernel + AutoGen，原生 MCP；OpenAI 发布 Workspace Agents (4/22) 支持后台执行与 Slack/Salesforce 集成
- **应用层分化**：ChatGPT DAU 跌至 38.7%（首次破 40%），Claude 功率用户日均 139 分钟 (↑41 分钟)；Meta 5/20 裁员 8000 人 (10%) 重配 135 亿美金至 AI 基建
- **融资空前**：Q1 2026 全球投融资 300 亿美金创纪录，AI 占 80% ($242B)，OpenAI/Anthropic/xAI/Waymo 合计 188 亿

---

## 1. 底层算力基建（Compute Infrastructure）

### GPU/ASIC 与芯片制造

**TSMC Q1 2026 财报记录高位**
- 2026 Q1 营收环比增长 35%（历史新高），净利润增长 58% YoY，驱动力主要来自 AI 芯片订单；2026 全年销售增长指引 30%+ ([CNBC 4/10](https://www.cnbc.com/2026/04/10/tsmc-q1-record-revenue-ai-chip-demand-strong.html), [4/16](https://www.cnbc.com/2026/04/16/tsmc-q1-profit-58-percent-ai-chip-demand-record.html))
- 资本开支 2026 目标 520-560 亿美金，重点扩产 3nm 与先进封装；计划在台湾、日本、美国推进新 3nm 产线，南台科学园新产线预计 H1 2027 投产 ([新华社 4/17](https://aninews.in/news/business/tsmc-to-expand-3nm-chip-production-taiwan-us-and-japan-as-ai-demand-surges20260417205537/))
- **CoWoS 瓶颈突出**：先进封装产能从 2024 年底 3.5 万片/月扩至 2026 年底预期 13 万片/月 (~4 倍)，但仍跟不上需求，截至 2026 年底前产能已售罄 ([Tom's Hardware, Network World](https://www.networkworld.com/article/3562856/nvidia-latest-news-and-insights.html))

**NVIDIA/Groq 推理加速**
- 2026 年 3 月 GTC：NVIDIA 发布 Groq 3 LPU 推理芯片，与 Vera Rubin NVL72 配对，1 万亿参数模型吞吐量比 Blackwell 提升 35 倍；单颗 LPU 提供 500MB SRAM、150TB/s SRAM 带宽 ([IEEE Spectrum](https://spectrum.ieee.org/nvidia-groq-3), [NVIDIA Newsroom](https://nvidianews.nvidia.com/news/latest))
- Groq 推理成本 $0.05-0.10/M tokens vs NVIDIA GPU $0.25/M tokens，吞吐量 800 tokens/s vs GPU 450 tokens/s (2026 年 3 月数据) ([WCCFTech](https://wccftech.com/nvidias-ai-chips-see-alternatives-emerge-amidst-pricing-model-shift-to-cost-per-million-tokens/))
- NVIDIA 2025 年 12 月同意收购 Groq 资产，交易金额 200 亿美金，创 NVIDIA 并购纪录

**HBM 内存供应危机**
- 三星、SK Hynix、美光合计产能 93% 转向 HBM 供应 AI 数据中心，消费电子 DRAM 供应严重受限 ([Tom's Hardware](https://www.tomshardian.com/pc-components/ram/hbm-is-eating-your-ram))
- DRAM 价格 Q1 2026 环比涨幅 90% (vs Q4 2025)；HBM 每晶圆收益是标准 DDR5 的 3-5 倍，成本/产能驱动制造商优先生产 HBM ([IEEE Spectrum](https://spectrum.ieee.org/dram-shortage), [Bloomberg](https://www.bloomberg.com/graphics/2026-ai-boom-memory-chip-shortage/))
- 供应缓解预期：2027-2028 年新产能上线；短期内云厂商已通过长期合同锁定产能

### 云厂商 CapEx 与数据中心

**Amazon + Anthropic 深度绑定**
- Amazon 新增 50 亿美金投资 Anthropic（总承诺 250 亿，其中 200 亿待里程碑触发），融资后 Anthropic 估值 380 亿；Anthropic 承诺 10 年内在 AWS 采购 1000 亿美金以上的 Trainium 计算力，年底前上线 1GW Trainium2/3 容量 ([CNBC 4/20](https://www.cnbc.com/2026/04/20/amazon-invest-up-to-25-billion-in-anthropic-part-of-ai-infrastructure.html))
- 此前 Amazon 对 OpenAI 的承诺为 500 亿美金（2 月）；两家投资形成竞争格局 ([The Motley Fool 4/21](https://www.fool.com/investing/2026/04/21/amazon-to-invest-25-billion-in-this-ai-start-up/))

**Meta 大幅资本重配**
- Meta CEO Mark Zuckerberg 宣布 2026 CapEx 指引上调至 1150-1350 亿美金 (vs 2025 年 722 亿)，翻近 1.8 倍，主要投向数据中心、GPU、Llama 模型与推荐系统 ([CNN 4/23](https://www.cnn.com/2026/04/23/tech/meta-layoffs-10-percent-staff-ai))
- 裁员 8000 人 (10%)、取消 6000 个已核准 headcount，于 5/20 启动；节省资金用于 AI 基建与特殊人才 ([The Next Web 4/23](https://thenextweb.com/news/meta-layoffs-may-2026-ai-restructuring-thousands))

---

## 2. 模型基建（Model Infrastructure）

### 基础模型新版本

**DeepSeek V4 (中国) 开源预览版 4/24 发布**
- **规模**：V4-Pro (1.6T 总参数 / 49B 激活参数)、V4-Flash (284B 总参数 / 13B 激活参数)，均为 Mixture-of-Experts 架构，双模式 (Thinking / Non-Thinking)
- **上下文**：1M token，V4-Pro 在 100M token 推理时 FLOPs 仅为 V3.2 的 27%，KV cache 降至 10%；V4-Flash 进一步降至 10% FLOPs、7% cache ([API Docs 4/24](https://api-docs.deepseek.com/news/news260424))
- **性能**：V4-Pro 在数学/STEM/编程超过所有开源模型，追平 Gemini 3.1-Pro，仅在世界知识上略低；V4-Flash 平衡性能与速度 ([Simon Willison 4/24](https://simonwillison.net/2026/Apr/24/deepseek-v4/))
- **定价**：Flash $0.14/$0.28 per M input/output tokens，Pro $1.74/$3.48；支持 MIT 开源权重 ([DeepSeek Docs](https://api-docs.deepseek.com/news/news260424))
- **遗留支持**：deepseek-chat 与 deepseek-reasoner 计划 7/24 弃用，自动映射至 V4-Flash 的 Non-Thinking/Thinking 模式

**Anthropic Claude Opus 4.7 (4/16 发布)**
- **能力**：相比 Opus 4.6 在高难度软件工程任务上显著进步，长视地平线推理与复杂工具依赖工作流可靠性提升；用户反馈可安心移交最难编码工作 ([GitHub Changelog 4/16](https://github.blog/changelog/2026-04-16-claude-opus-4-7-is-generally-available/))
- **多模态**：首次支持高分辨率图像输入，最大分辨率 2576px / 3.75MP (较前代显著扩展) ([Anthropic 4/16](https://www.anthropic.com/news/claude-opus-4-7))
- **定价 & 发布**：保持 Opus 4.6 价格 ($5/$25 per M input/output tokens)；全量覆盖 Claude 消费版、API、Amazon Bedrock、Google Vertex AI、Microsoft Foundry

**Google Gemini 3.1 系列 (3/20 - 4/20)**
- **Gemini 3 Flash**：Pro 级推理、Flash 级速度与成本，编码能力 SWE-bench Verified 78% (超 Gemini 2.5 与 3 Pro)；支持 thinking_level 参数微调推理深度 ([Google Blog 4/15](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-lite/))
- **Gemini 3.1 Flash-Lite**：最轻量版本，1M token 上下文全多模态支持 (图像/音频/视频/文件)；相比 2.5 Flash 首响延迟快 2.5 倍、生成速度提升 45% ([Google Cloud Docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-1-flash-lite))
- **Gemini 3.1 Flash TTS**：改进语音质量与控制，支持 70+ 语言音频标签调节音色与节奏 ([Google Blog 4/15](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-tts/))

### 商业模型更新 & 定价动向

**Claude ARR 与 Claude Code 爆炸式增长**
- Anthropic 3 月 ARR 超 300 亿美金 (vs 2025 初 10 亿、2024 晚 10 亿)；一年翻 30 倍 ([Early research sources](https://letsdatascience.com/news/anthropic-revises-claude-enterprise-pricing-structure-f3022a32))
- Claude Code 单独 ARR 约 25 亿美金 (2 月)，企业订阅环比 4x 增长，企业占比超 50% ([Business of Apps](https://www.businessofapps.com/data/claude-statistics/))
- API 定价结构调整：Opus/Sonnet/Haiku 4.5/4.6 代成本下降 67% vs 前代；Batch API 50% 折扣、Prompt Caching 10% input 缓存价格 ([Finout Blog](https://www.finout.io/blog/anthropic-api-pricing))

**定价战激化**
- 4 月期间 Cursor、GitHub Copilot、Claude Code 在 6 周内同时紧缩额度、缩短缓存、将前沿模型挪到付费倍数后，从"AI 队友"平价营销转向计量化经济学 ([Medium 4/2026](https://medium.com/activated-thinker/the-flat-rate-ai-coding-subscription-era-is-ending-what-github-copilot-claude-code-and-cursor-9763e043a63a))

---

## 3. Agent 层

### Agent 框架与协议

**Microsoft Agent Framework 1.0 (4/3 发布)**
- **统一 SDK**：合并 Semantic Kernel + AutoGen 两条线，提供稳定 API 与长期支持承诺 ([byteiota](https://byteiota.com/microsoft-agent-framework-1-0-ships-mcp-a2a-converge/))
- **原生 MCP 支持**：内置 Model Context Protocol 动态工具发现，DevUI 浏览器调试器可视化 agent 执行流 ([Microsoft Fabric Blog](https://blog.fabric.microsoft.com/en-us/blog/agentic-fabric-how-mcp-is-turning-your-data-platform-into-an-ai-native-operating-system))
- **Fabric 集成**：Microsoft Fabric 演进为 agent 原生平台，通过统一 MCP 实现数据库查询、SaaS 交互与跨云操作无需定制集成代码

**MCP / A2A 生态融合**
- **Google A2A 一周年里程碑 (4/9)**：150+ 组织参与，生产环境部署覆盖 Azure AI Foundry、Amazon Bedrock、企业平台；信号：MCP + A2A 架构成为生产 agentic 系统默认标准 ([epsilla Blog](https://www.epsilla.com/blogs/ai-agent-developments-april-18-2026))
- **Linux Foundation AAIF 宣布**：Model Context Protocol (Anthropic 创建，GitHub/Cloudflare/Stripe 采纳) 成为行业开放标准，统一 agent 与外部系统通信，无需自定义集成与多重身份验证 ([Linux Foundation](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation))
- **AWS MCP 深度集成**：Amazon 在 Bedrock 原生纳入 MCP，企业客户可安全查询数据库、与 SaaS 应用互动、跨基建执行操作 ([epsilla Blog](https://www.epsilla.com/blogs/ai-agent-developments-april-18-2026))

### Agent 应用与长程规划

**OpenAI Workspace Agents (4/22 发布)**
- **定义**：云端持续运行的团队级 AI agents，支持后台执行 (关闭浏览器后继续)、工作空间成员间共享、Slack/Gmail/Drive/Calendar/Docs/Sheets/Salesforce 直接集成 ([OpenAI 4/22](https://openai.com/index/introducing-workspace-agents-in-chatgpt/))
- **能力**：收集背景、遵循工作流、请求批准、迭代改进；初期研究预览仅限 Business/Enterprise/Edu/Teachers 计划，消费版 (Plus/Pro/Free) 暂未开放
- **商业模式**：5/6 前免费试用，之后按 credit 制计价；Custom GPT 相比 Workspace Agents 缺少后台执行与实时工作流集成
- **弃用计划**：OpenAI 宣布未来将弃用 Custom GPT，企业用户需迁移至 Workspace Agents ([VentureBeat](https://venturebeat.com/orchestration/openai-unveils-workspace-agents-a-successor-to-custom-gpts-for-enterprises-that-can-plug-directly-into-slack-salesforce-and-more/))

---

## 4. 应用层（Applications）

### 消费级 AI 产品 DAU 与竞争格局

**ChatGPT 市占率首次跌破 40%**
- 3 月 DAU 市占率 38.7%，连续 4 月环比下滑，创 2026 年新低；6 个月前曾占 52% ([eMarketer](https://www.emarketer.com/content/gemini-gains-ground-chatgpt-25-dau-share-claude-churn-drops), [Apptopia 4/2026](https://apptopia.com/en/insights/gen-ai-chatbots-april-2026-apptopia-data-brief-chatgpt-drops-below-40-market-share/))
- **竞争对手蚕食**：Gemini 稳定在 25% DAU；Claude 功率用户（日均 139 分钟，↑ 41 分钟 vs 2 月）、功率用户流失率降至 12%，留存改善明显 ([eMarketer](https://www.emarketer.com/content/gemini-gains-ground-chatgpt-25-dau-share-claude-churn-drops))
- **整体市场**：Gen AI Chatbot 市场 2-3 月环比增 5%、9 月对比增 22%，扩张驱动力主要来自挑战者抢食而非 ChatGPT 自身增长 ([Apptopia](https://apptopia.com/en/insights/gen-ai-chatbots-april-2026-apptopia-data-brief-chatgpt-drops-below-40-market-share/))

**Claude 消费与企业双轮驱动**
- 消费端月活 1890 万 (早 2026)；Claude 移动应用 2 月 MAU 1248 万，环比增 49% ([fatjoe](https://fatjoe.com/blog/claude-ai-stats/))
- 企业端：服务 Fortune 100 的 70%，30 万+ 商业客户，500+ 客户年花费 100 万+ ([Business of Apps](https://www.businessofapps.com/data/claude-statistics/))

### AI 编程工具

**Cursor vs GitHub Copilot vs Claude Code 三足鼎立**
- **Cursor**：Composer 2 (3/19) 采用 Moonshot Kimi K2.5 基座 + 强化学习微调 (3/22 核实)，约 1/4 计算来自基座、3/4 来自 Cursor 自有训练；定价 $0.50/$2.50 per M tokens；Cursor 估值 500 亿美金 ([TechCrunch 3/22](https://techcrunch.com/2026/03/22/cursor-admits-its-new-coding-model-was-built-on-top-of-moonshot-ais-kimi/), [Medium 3/23](https://thamizhelango.medium.com/cursor-composer-2-and-kimi-k2-5-f236ef41aac1))
- **GitHub Copilot**：4 月进入 3 大变化阶段 —— agent 模式 GA (VS Code + JetBrains)、agent 代码审查 (3 月)、语义搜索升级；付费用户超 470 万 ([Medium 4/2026](https://medium.com/activated-thinker/the-flat-rate-ai-coding-subscription-era-is-ending-what-github-copilot-claude-code-and-cursor-9763e043a63a))
- **Claude Code**：通过 Claude API 与独立订阅提供，ARR 25 亿美金；常见开发栈为"日常编辑用 Cursor + 复杂任务用 Claude Code"或"IDE 内 Copilot + 终端 Claude Code" ([digitalapplied Blog](https://www.digitalapplied.com/blog/ai-coding-assistants-april-2026-cursor-copilot-claude))

### 视频/内容生成

**Sora 关闭、Veo 加速竞争**
- **Sora 末日** (4/26)：OpenAI 关闭 Sora 应用，API 计划 9/24 断服；用户需在截止前导出内容 ([Resource.digen.ai](https://resource.digen.ai/sora-2-openai-shutdown-guide-2026/))
- **Veo 3.1 降价 (4 月)**：Google 进一步降低 Veo 3.1 Fast 定价，强势信号捕获 post-Sora 市场空缺；3.1 提供最佳 prompt 保真度与原生音视频同步 ([digitalapplied Blog](https://www.digitalapplied.com/blog/ai-video-market-after-sora-runway-kling-veo-2026))
- **Veo 4 待发 (预期 Google I/O 5 月)**：研究员 3/28 发出暗示表情，预测市场给出 18% 概率 4/30 前发布；Veo 4 架构采用"全局上下文窗口"追踪对象出框后的返回位置 ([digitalapplied Blog](https://www.digitalapplied.com/blog/veo-4-video-generator-guide-2026))

### 中文模型与应用

**国内模型融合竞争 (4 月)**
- **DeepSeek**：V4 发布后，2026 年 3 月 MAU 1.35 亿 (↑145% YoY) ([Zhihu 2026-04-24](https://zhuanlan.zhihu.com/p/2020939578454844541))
- **豆包 (ByteDance Doubao)**：2 月 Doubao-Seed-2.0 发布 (Lite/Mini 版)，3 月 MAU 2.26 亿 (↑172% YoY)；日常会话流畅度强，深层中文理解稍弱 ([jilo.ai review](https://jilo.ai/zh/reviews/best-chinese-ai-models))
- **通义千问 (Alibaba Qwen)**：Qwen3.6-plus (2026) 在 Agent 编程与代码仓级问题求解突破；Wanxiang Wan 2.7-Video 系列 (4 月) 支持文生视频、图生视频、参考指导与视频编辑，输出 720P/1080P ([Zhihu 2026-04-24](https://zhuanlan.zhihu.com/p/670574382))
- **Kimi (Moonshot)**：长文本中文理解领先，K2.5 成为 Cursor Composer 2 的技术基座

---

## 5. 跨层趋势研判

### 研判 1：算力供应链瓶颈从训练转向推理与封装

过去一年，GPU 训练芯片是 AI 基建核心约束；2026 年 4 月的数据显示**供应链压力点已向两端转移**：
1. **HBM 短缺**：三大内存厂 93% 产能已转向 AI，消费电子供应几近枯竭，2027-2028 才有缓解预期。这直接限制了 GPU 与 ASIC 的集成密度与功耗。
2. **推理芯片崛起**：Groq 3 LPU 成本/性能 5-10 倍优于 NVIDIA GPU，NVIDIA 收购 Groq ($200B) 是战略认输；未来推理成本下降会加速 AI 应用边缘化与行业落地。
3. **CoWoS 封装瓶颈**：TSMC 4 倍扩产仍不足，这意味着高端 GPU/ASIC 的最终交付节奏仍受限，制约了云厂商 CapEx 落地周期。

**传导影响**：云厂商不得不锁定长期合同 (Amazon-Anthropic 100B+ over 10y) 以确保产能，而成本压力反过来推动模型高效化与推理优化成为必选题。

### 研判 2：Agent 基建标准化与企业 Agent 爆发期临界点已过

Microsoft Agent Framework 1.0 + OpenAI Workspace Agents + MCP 生态融合，标志着**Agent 基层设施已具备生产就绪**：
- MCP 与 A2A 两大协议在 AWS/Azure/Google Cloud 全部原生化，消除了定制集成的技术与成本障碍
- Workspace Agents 的后台执行、工作流触发、多工具编排能力开放给 Business/Enterprise 用户，而不再仅限研究预览
- 企业采纳拐点：长程规划 + 记忆管理 + 多 Agent 协作已不再是 PoC，而是产品必配

**传导影响**：2026 下半年应看到 Agent 在金融、法律、供应链、客服等垂直行业的规模部署，SaaS AI 化的重点从"LLM 集成"升级为"Agent 工作流自动化"。

### 研判 3：消费 AI 市占率重组与功率用户价值创新

ChatGPT 从 52% 跌至 38.7% 的 6 个月是**市场结构调整的信号**，而非衰退：
- Gemini 保持 25%、Claude 功率用户日均 139 分钟、Claude Code ARR 25 亿，各自占据专业赛道
- 开发者与专业人士的多模型并用是新常态，单一锁定已终结
- 但总 DAU 增长仍强 (2-3 月 +5%, 9 月对比 +22%)，说明市场在扩大而非饱和

**传导影响**：模型厂商的竞争维度从"装机量"转向"专业价值"(编程、推理、长文本、多模态)；功率用户留存与深度使用时长比 DAU 数字更关键。

### 研判 4：融资极端两极化与初创寒冬的隐忧

Q1 2026 投融资 $300B (80% 聚焦 AI)，但 OpenAI ($122B) + Anthropic ($30B) + xAI ($20B) + Waymo ($16B) 四家合计 $188B，占全球 AI 融资 65%；而种子与 A 轮融资中，40% 以上已是 $100M+ 大额轮。

这意味着**融资极端集中于少数头部玩家** —— 中间层的中等规模初创 ($10-50M) 融资环境实际在恶化。小而精的专用 AI 公司更难获得规模融资，转向被收购或失败的概率上升。

---

## 6. 下周值得追踪的事件

- **Google I/O 2026** (5/19-20)：预期发布 Gemini 4、Project Astra 详情、Veo 4 宣布、Android 17 AI 特性、Firebase agent-native 演进 ([Google I/O 网站](https://io.google/2026/))
- **OpenAI 可能公告**：GPT-5.5 (Spud) 官方发布时间 (预训练已于 3/24 完成)
- **NVIDIA GTC 后续**：Groq LPU 芯片供应链与成本曲线实现情况
- **TSMC 3nm 产能**：H1 2027 南台新产线投产准备进展
- **Anthropic/OpenAI 企业 Agent** 大客户案例发布 (AI 基建投入转化为应用案例的窗口)

---

## Sources

### 底层算力基建
- [CNBC: TSMC posts 35% jump in revenue to new record high as AI chip demand stays strong (4/10/2026)](https://www.cnbc.com/2026/04/10/tsmc-q1-record-revenue-ai-chip-demand-strong.html)
- [CNBC: TSMC first-quarter profit rises 58%, beats estimates as AI demand fuels record run (4/16/2026)](https://www.cnbc.com/2026/04/16/tsmc-q1-profit-58-percent-ai-chip-demand-record.html)
- [ANINEWS: TSMC to expand 3nm chip production in Taiwan, US and Japan as AI demand surges (4/17/2026)](https://aninews.in/news/business/tsmc-to-expand-3nm-chip-production-taiwan-us-and-japan-as-ai-demand-surges20260417205537/)
- [IEEE Spectrum: Nvidia Groq 3 LPU: Speeding AI Inference Tasks](https://spectrum.ieee.org/nvidia-groq-3)
- [Tom's Hardware: HBM is eating your PC's RAM (2026)](https://www.tomshardware.com/pc-components/ram/hbm-is-eating-your-ram)
- [IEEE Spectrum: AI and the High Bandwidth Memory Shortage](https://spectrum.ieee.org/high-bandwidth-memory-shortage)
- [Bloomberg: AI Boom Fuels DRAM Shortage and Price Surge (2026)](https://www.bloomberg.com/graphics/2026-ai-boom-memory-chip-shortage/)
- [CNBC: Amazon to invest up to another $25 billion in Anthropic as part of AI infrastructure deal (4/20/2026)](https://www.cnbc.com/2026/04/20/amazon-invest-up-to-25-billion-in-anthropic-part-of-ai-infrastructure.html)
- [The Motley Fool: Amazon to Invest $25 Billion in This AI Start-Up (4/21/2026)](https://www.fool.com/investing/2026/04/21/amazon-to-invest-25-billion-in-this-ai-start-up/)
- [CNN: Meta to cut 10% of staff as it pours billions into AI (4/23/2026)](https://www.cnn.com/2026/04/23/tech/meta-layoffs-10-percent-staff-ai)
- [The Next Web: Meta to cut 8,000 jobs on 20 May with more layoffs planned for second half of 2026](https://thenextweb.com/news/meta-layoffs-may-2026-ai-restructuring-thousands)

### 模型基建
- [DeepSeek API Docs: DeepSeek V4 Preview Release (4/24/2026)](https://api-docs.deepseek.com/news/news260424)
- [Simon Willison: DeepSeek V4—almost on the frontier, a fraction of the price (4/24/2026)](https://simonwillison.net/2026/Apr/24/deepseek-v4/)
- [CNBC: China's DeepSeek rolls out a long-anticipated update of its AI model (4/24/2026)](https://www.cnbc.com/2026/04/24/chinas-deepseek-rolls-out-a-long-anticipated-update-of-its-ai-model)
- [GitHub Changelog: Claude Opus 4.7 is generally available (4/16/2026)](https://github.blog/changelog/2026-04-16-claude-opus-4-7-is-generally-available/)
- [Anthropic: Introducing Claude Opus 4.7 (4/16/2026)](https://www.anthropic.com/news/claude-opus-4-7)
- [Google Blog: Gemini 3.1 Flash-Lite: Our most cost-effective AI model yet (4/2026)](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-lite/)
- [Google Cloud Docs: Gemini 3.1 Flash-Lite](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-1-flash-lite)
- [Google Blog: Gemini 3.1 Flash TTS: the next generation of expressive AI speech (4/2026)](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-tts/)
- [Let's Data Science: Anthropic Revises Claude Enterprise Pricing Structure](https://letsdatascience.com/news/anthropic-revises-claude-enterprise-pricing-structure-f3022a32)
- [Finout Blog: Anthropic API Pricing in 2026: Complete Guide](https://www.finout.io/blog/anthropic-api-pricing)
- [Business of Apps: Claude Revenue and Usage Statistics (2026)](https://www.businessofapps.com/data/claude-statistics/)
- [Medium: The Flat-Rate AI Coding Subscription Era Is Ending (4/2026)](https://medium.com/activated-thinker/the-flat-rate-ai-coding-subscription-era-is-ending-what-github-copilot-claude-code-and-cursor-9763e043a63a)

### Agent 层
- [byteiota: Microsoft Agent Framework 1.0 Ships: MCP + A2A Converge (4/2026)](https://byteiota.com/microsoft-agent-framework-1-0-ships-mcp-a2a-converge/)
- [Microsoft Fabric Blog: Agentic Fabric: How MCP is turning your data platform into an AI-native operating system (4/2026)](https://blog.fabric.microsoft.com/en-us/blog/agentic-fabric-how-mcp-is-turning-your-data-platform-into-an-ai-native-operating-system)
- [epsilla Blog: The Rapid Evolution of AI Agent Infrastructure: April 2026 Roundup (4/18/2026)](https://www.epsilla.com/blogs/ai-agent-developments-april-18-2026)
- [Linux Foundation: Linux Foundation Announces the Formation of the Agentic AI Foundation (AAIF)](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation)
- [OpenAI: Introducing workspace agents in ChatGPT (4/22/2026)](https://openai.com/index/introducing-workspace-agents-in-chatgpt/)
- [VentureBeat: OpenAI unveils Workspace Agents, a successor to custom GPTs for enterprises (4/2026)](https://venturebeat.com/orchestration/openai-unveils-workspace-agents-a-successor-to-custom-gpts-for-enterprises-that-can-plug-directly-into-slack-salesforce-and-more/)

### 应用层
- [eMarketer: Gemini gains ground on ChatGPT with 25% US DAU share as Claude's churn drops (4/2026)](https://www.emarketer.com/content/gemini-gains-ground-chatgpt-25-dau-share-claude-churn-drops)
- [Apptopia: Gen AI Chatbots: April 2026 Apptopia Data Brief (4/2026)](https://apptopia.com/en/insights/gen-ai-chatbots-april-2026-apptopia-data-brief-chatgpt-drops-below-40-market-share/)
- [fatjoe: Claude AI Stats 2026 - Market Shares, Total Users, and More](https://fatjoe.com/blog/claude-ai-stats/)
- [digitalapplied Blog: AI Coding Assistants April 2026: Rankings and Review (4/2026)](https://www.digitalapplied.com/blog/ai-coding-assistants-april-2026-cursor-copilot-claude)
- [TechCrunch: Cursor admits its new coding model was built on top of Moonshot AI's Kimi (3/22/2026)](https://techcrunch.com/2026/03/22/cursor-admits-its-new-coding-model-was-built-on-top-of-moonshot-ais-kimi/)
- [Medium: Cursor Composer 2 and Kimi K2.5: What Happened (3/23/2026)](https://thamizhelango.medium.com/cursor-composer-2-and-kimi-k2-5-f236ef41aac1)
- [Resource.digen.ai: Sora 2 Guide: Release Date & 7 Best 2026 Alternatives](https://resource.digen.ai/sora-2-openai-shutdown-guide-2026/)
- [digitalapplied Blog: AI Video Market After Sora: Runway, Kling, and Veo (4/2026)](https://www.digitalapplied.com/blog/ai-video-market-after-sora-runway-kling-veo-2026)
- [Zhihu: 2026 国产AI大模型横评 (4/24/2026)](https://zhuanlan.zhihu.com/p/2020939578454844541)
- [jilo.ai: 2026 国产 AI 大模型横评：DeepSeek vs 豆包 vs 通义千问 vs 文心一言 vs Kimi](https://jilo.ai/zh/reviews/best-chinese-ai-models)
- [digitalapplied Blog: Veo 4 Video Generator Guide: Master AI Cinema in 2026 (4/2026)](https://resource.digen.ai/veo-4-video-generator-guide-2026/)

### 融资与生态
- [Crunchbase: Q1 2026 Shatters Venture Funding Records As AI Boom Pushes Startup Investment To $300B (4/2026)](https://news.crunchbase.com/venture/record-breaking-funding-ai-global-q1-2026/)
- [Crunchbase: Sector Snapshot: Venture Funding To Foundational AI Startups In Q1 Was Double All Of 2025 (4/2026)](https://news.crunchbase.com/venture/foundational-ai-startup-funding-doubled-openai-anthropic-xai-q1-2026/)

### 论文与研究
- [arXiv: A Comparative Study on Reasoning Patterns of OpenAI's o1 Model](https://arxiv.org/html/2410.13639v1)
- [Andrew Hansen: AI Reasoning Models in 2026: How o1-Like Advances Are Reshaping Enterprise Problem-Solving](https://www.andrewhansen.au/ai-reasoning-models-in-2026-how-o1-like-advances-are-reshaping-enterprise-problem-solving/)

### 大型活动与展望
- [Google I/O 2026](https://io.google/2026/)
- [Google Developers Blog: Get ready for Google I/O 2026](https://developers.googleblog.com/get-ready-for-google-io-2026/)
- [gHacks Tech News: Google I/O 2026 Sessions List Reveals Android 17, AI, and Chrome as Key Topics (4/15/2026)](https://www.ghacks.net/2026/04/15/google-i-o-2026-sessions-list-reveals-android-17-ai-and-chrome-as-key-topics-for-may-19-event)
