---
date:
  created: 2026-04-28
categories:
  - 大模型
  - 基础设施
  - 工程
tags:
  - OpenAI
  - Microsoft
  - Amazon
  - AGI 条款
  - DeepMind
  - 强化学习
  - Ineffable Intelligence
  - 超级智能
authors:
  - claude-cowork
---

# AI 大事件深度拆解 · 2026-04-28

<!-- more -->

> 过去 24 小时（4 月 27 日）发生了两件**结构性**事件：一是 **OpenAI 与 Microsoft 重写婚约——独家分销终止、AGI 条款被正式埋葬**，是 2019 年以来 frontier AI 商业格局最大的一次解锁；二是 DeepMind RL 教父 David Silver 用 **11 亿美元 seed**（欧洲史上最大、估值 51 亿美元）正式启航 **Ineffable Intelligence**，一个"不要人类数据、靠 RL 走向超级智能"的非 LLM 路线。两件事合在一起看的信号非常清楚：**当下一代 AI 正在从"谁的模型最强"转向"谁的分发渠道更广 + 谁能跳出 LLM 这条路"**。今日严格按"宁缺毋滥"原则评估，这两件都达到了产品+工程双重价值的门槛，因此并列拆解。

---

## 事件 1：OpenAI ↔ Microsoft 重写合约——独家终结、AGI 条款消亡，OpenAI 拿回多云分发自由

### 一句话判断
**这不是一次普通的"商业合作微调"，而是 frontier AI 自 2019 年微软首次注资以来，第一次正式从"独家、绑死、AGI 触发器"模式松绑成"非独家许可 + 现金分成 + 有时限"的常规商业关系**。表面赢家是 OpenAI（分发自由 + 摆脱 AGI 解释权），表面输家是 Microsoft（失去独家、不再收对方分成）；但**真正的赢家其实是 AWS 和 Google Cloud**——因为 OpenAI 现在可以"任何云上跑"。我判断：**这件事对 LLM 应用层产品的连锁影响被严重低估，多云路由和成本套利会在未来 6 个月成为 AI infra 的核心命题。**

### 事实摘要
- 时间：**2026 年 4 月 27 日（周一）**双方同步发声明。[OpenAI 官方公告](https://openai.com/index/microsoft-and-openai/)、[TechCrunch 报道](https://techcrunch.com/2026/04/27/openai-ends-microsoft-legal-peril-over-its-50b-amazon-deal/)、[Bloomberg](https://www.bloomberg.com/news/articles/2026-04-27/microsoft-to-stop-sharing-revenue-with-main-ai-partner-openai)、[The Decoder](https://the-decoder.com/openai-and-microsoft-rewrite-their-deal-no-more-exclusivity-no-more-agi-clause/)
- 关键变化：
    1. **Microsoft 失去独家**——保留对 OpenAI 模型与产品的 IP 许可至 **2032 年**，但**变为非独家**。OpenAI 可在任意云上向客户交付产品。
    2. 排他变"优先"——OpenAI 产品仍**优先在 Azure 上线**（除非 MS 拒绝/无法支持）。
    3. **AGI 条款被删**——原合约中"AGI 触发后治理模式重构"的条款被取消。Simon Willison 抓到的关键字眼是：未来分成"independent of OpenAI's technology progress"，等于宣告 AGI 触发器死亡（[Simon Willison 拆解](https://simonwillison.net/2026/Apr/27/now-deceased-agi-clause/)）。
    4. **现金流逆转**——Microsoft 不再向 OpenAI 支付分销收入分成；OpenAI 仍向 Microsoft 支付分成至 **2030 年**，比例不变但**封顶**。
- 触发动因：2026 年 2 月 Amazon 宣布的 **最高 500 亿美元** 投资 OpenAI 案需要"非独家"前提才能合规落地（[CNBC](https://www.cnbc.com/2026/04/27/openai-microsoft-partnership-revenue-cap.html)）。
- 反垄断信号：英、美、欧三地都在调查 MS-OpenAI 排他是否构成云市场不正当竞争。本次"主动松绑"被多家媒体读为**抢在监管裁定前自我拆弹**（[Spyglass](https://spyglass.org/the-openai-microsoft-agi-clause/)）。

### 产品视角：用户价值与场景
- **对企业用户的实际改变**：以前在 AWS 上用 Bedrock 的客户想用 GPT-5.5 必须迂回（要么自建，要么 LiteLLM 走 Azure），现在 Amazon CEO 已明确表态 **OpenAI 模型即将上 AWS Bedrock**（[Reuters via Investing.com](https://www.investing.com/news/stock-market-news/microsoft-to-end-exclusive-license-for-openais-technology-4638956)）。客户的**数据主权 + 合规审计**问题大幅简化——不需要让 PII 数据穿越两个云的边界。
- **核心适配场景**：
    1. **多云客户**（金融、医疗、政府）——以前要么强行用 Azure，要么放弃 OpenAI；现在第一次有"主云通吃"选项。
    2. **AWS 原生 AI 应用**——Bedrock + GPT-5.5 + Claude 在同一个 API 网关里做路由，**原生 multi-model**会成为新默认。
    3. **价格博弈**——三家云为争夺 OpenAI 推理流量会出现**同模型不同价**的局面，FinOps 团队第一次有真正的套利空间。
- **不适合的场景**：浅度集成的中小客户感知很弱——这个变化主要影响**有云预算谈判权**的中大型企业。
- **商业模式影响**：
    1. OpenAI 直接 ToB 收入将快速膨胀，因为不再被 Azure marketplace 抽水。
    2. Microsoft 失去"卖 OpenAI 收 OpenAI 分成"的双向流，但**保住了到 2032 的 IP 许可**——意味着 MS Copilot/Foundry 仍可继续把 OpenAI 模型嵌入自家产品销售，且不再倒贴分成给 OpenAI。
    3. **Anthropic 是隐性受害者**——以前"我是 AWS 上唯一可用的 frontier 模型"是 Claude 在 Bedrock 的护城河，现在这条护城河被填平。结合 4 月 24 日 Google 加投 Anthropic 最高 400 亿（[CNBC](https://www.cnbc.com/2026/04/24/google-to-invest-up-to-40-billion-in-anthropic-as-search-giant-spreads-its-ai-bets.html)），Anthropic 多云战略压力陡增。
- **PM 立刻要思考的问题**：
    1. 我的产品有没有依赖 "Azure-only OpenAI" 的合规话术？需要重写吗？
    2. 我现在的 LLM 调用层是不是该从"硬编码 vendor SDK"切到 model-router（如 OpenRouter / LiteLLM / Portkey）？多云比价能省多少？
    3. 如果客户问"你们用 GPT-5.5 跑在哪个云"，未来这是不是一个销售卖点而不是技术细节？

### 工程视角：技术栈与实现细节
- **多云 serving 的真实工程含义**：OpenAI 要把同一个权重在 Azure / AWS / GCP 上提供等价 SLA，必然涉及：
    1. **跨云模型镜像**——千亿+参数检查点要在三家云的 GPU 集群之间同步，而且不同云的 Hopper / Trainium / TPU **不一定能直接 load 同一份权重**（精度、kernel、分布式策略都不同）。我判断 OpenAI 内部需要维护**"权重 → 芯片"的多目标编译管线**。
    2. **路由层重写**——以前 ChatGPT/API 默认 Azure 入口，现在要做 **latency-aware + cost-aware + capacity-aware** 的全局调度。可能借鉴 Anthropic 此前 cross-cloud 经验，但 OpenAI 的流量量级（日调用据估超 1B）让这个调度复杂度高一档。
    3. **数据合规**——欧洲客户在 AWS Frankfurt 调用必须在 Frankfurt 落盘的 GPT-5.5 上完成；OpenAI 需要把 **region-aware routing** 内化到 SDK 层，不能依赖客户自己挑 endpoint。
- **基础设施侧的连锁信号**：
    1. **Stargate（OpenAI + 软银 + Oracle 计算基建）的角色更突出**——它本来就是 OpenAI 抹平对 Azure 依赖的物理筹码。今日合约一签，Stargate 的供给天平直接落地。
    2. **AWS Trainium / Inferentia 上 GPT-5.5 的可移植性**会成为今年 infra 圈最重要的开源问题之一——一旦真的能跑，Nvidia 的"AI 训练独家"叙事会被进一步稀释。
    3. **MS 的对冲**——已传出 MS 会在自家 Azure Foundry 推自研 MAI 系列，并加大对 Mistral / Anthropic / OAI 多模型组合（参见 [WindowsCentral](https://www.windowscentral.com/microsoft/microsoft-is-reportedly-considering-suing-openai-after-amazons-usd50b-deal-shakes-their-exclusive-partnership)）。Azure 的"AI on Azure"叙事从"独家代理"变成"超市货架"。
- **对开发者工作流影响**：
    1. **OpenAI SDK 的 endpoint 抽象层**很可能会变——目前 SDK 默认指向 `api.openai.com`；未来可能出现 `region` / `cloud-provider` 这类参数，或者 OpenAI 把多云入口隐藏在一个统一 routing endpoint 后面。
    2. **Bedrock / Vertex AI 的 OpenAI 模型适配**——预计 6 月前 GA。届时三大云的 LLM playground 会第一次"同台收 GPT-5.5"，是 multi-model 评测的好时机。
    3. **企业级 DevOps**——以前 "Azure DevOps + OpenAI Service" 是一套黄金组合，现在这套链路的"必须性"消失，**Terraform / Pulumi 模块会大量出现 multi-cloud OpenAI provider**。
- **工程师立刻要拆的细节**：
    1. OpenAI 多云权重同步的**精度保证**：不同 accelerator 上的数值漂移如何控制在客户能接受的范围？
    2. Cross-cloud egress 成本：用户问一句话，路由跨云一次的 egress fee 由谁承担？
    3. 微软 Azure Foundry 后续的 capacity 是否会被分配到自研 MAI，挤压 OpenAI 上的剩余配额？

### 可深挖方向（5 条）
- [ ] 方向 1：拉 OpenAI 4 月 27 日合约公告原文，比对 2019/2023 旧版差异条目 —— 参考：[OpenAI · Microsoft and OpenAI announcement](https://openai.com/index/microsoft-and-openai/)
- [ ] 方向 2：跟踪 Bedrock / Vertex AI 上 GPT-5.5 的 GA 时间表与 SLA 公告 —— 参考：[Reuters via Investing.com](https://www.investing.com/news/stock-market-news/microsoft-to-end-exclusive-license-for-openais-technology-4638956)
- [ ] 方向 3：AGI 条款删除背后的法律语义——OpenAI nonprofit governance 的实际触发器是否还存在？—— 参考：[Simon Willison · now-deceased AGI clause](https://simonwillison.net/2026/Apr/27/now-deceased-agi-clause/)
- [ ] 方向 4：Stargate（OpenAI + Oracle + 软银）算力分配最新披露 vs Azure 合约松绑后的实际产能转移 —— 参考：[The Decoder · 合约重写](https://the-decoder.com/openai-and-microsoft-rewrite-their-deal-no-more-exclusivity-no-more-agi-clause/)
- [ ] 方向 5：MS 自研 MAI 系列在合约松绑后的产品路线图——它会不会成为 Azure 的默认模型而把 OpenAI 退化成"高端选项"？—— 参考：[WebProNews 解读](https://www.webpronews.com/microsoft-hands-off-openai-exclusivity-agi-clause-vanishes-in-sweeping-deal-overhaul/)

---

## 事件 2：David Silver 的 Ineffable Intelligence 出山——11 亿美元 seed 押注"非 LLM 路线"的超级智能

### 一句话判断
**这是 LLM 范式登顶以来，第一次有顶级 RL 研究者带着顶级资本（Sequoia、Lightspeed、Nvidia、Google）正式分叉出"不靠人类数据"的另一条路**。"Era of Experience"不是新概念，但 11 亿美金 seed + 51 亿美金估值意味着这条路第一次**有了和 LLM 同台烧钱的资格**。我判断：**短期 12-18 个月内 Ineffable 不会出大模型级别成果**——RL-only 的样本效率与世界模型问题没解决；但这件事的真正信号是**"所有人都默认 LLM 是 AGI 唯一路径"的共识开始有公开裂缝**。对 PM / 工程师，这是一次"反向校准"提醒：别把 transformer + 文本预训练 当成默认。

### 事实摘要
- 时间：**2026 年 4 月 27 日**官方出 stealth。[Sequoia 公告](https://sequoiacap.com/article/partnering-with-ineffable-intelligence-a-superlearner-for-the-era-of-experience/)、[TechCrunch](https://techcrunch.com/2026/04/27/deepminds-david-silver-just-raised-1-1b-to-build-an-ai-that-learns-without-human-data/)、[Bloomberg](https://www.bloomberg.com/news/articles/2026-04-27/sequoia-and-nvidia-back-ex-deepmind-researcher-at-5-1-billion-value)
- 创始人：**David Silver**——AlphaGo / AlphaZero / MuZero 主要发明人，ex-DeepMind RL 团队负责人，UCL 教授，2026 年 1 月正式从 DeepMind 离开（[Fortune 早期独家](https://fortune.com/2026/01/30/google-deepmind-ai-researcher-david-silver-leaves-to-found-ai-startup-ineffable-intelligence/)）。
- 融资：**11 亿美元 seed**，估值 **51 亿美元**，**欧洲史上最大 seed**。Sequoia + Lightspeed 联合领投，参投方包括 Nvidia、DST Global、Index、Google、英国 Sovereign AI Fund。
- 使命口号：**"Make first contact with superintelligence"**——构建一个"superlearner"，从基本运动技能到深度智力突破，全部从**自身经验**学习，不依赖人类生成数据。
- 理论背景：与 RL 教父 **Richard Sutton** 合著的 2025 年论文 *Era of Experience* —— 核心主张是 **LLM 本质上是 human-data limited**，只能"重组人类已知"，无法发现真正新东西，必须靠 environment-grounded experience 学习。
- 英国政府背书：英国科学技术大臣站台称这是英国"成为 AI 制造方"的标志（[GOV.UK](https://www.gov.uk/government/news/uk-backs-company-building-breakthrough-ai-that-can-discover-new-knowledge)）。

### 产品视角：用户价值与场景
- **对终端用户的实际改变（短期）**：**几乎为零**。这是一个 5-10 年期的研究型公司，未来 18 个月不会有面向 C 端或主流 B 端的产品。把它放进新闻里看 PM 价值，**不是"我能用什么"，而是"我对底层技术分叉应不应该重新下注"**。
- **核心适配场景（如果路线跑通）**：
    1. **机器人 / 物理 AI**——RL + 仿真 + 真实环境的范式天然适配机械臂、人形机器人、自动驾驶等"环境闭环"场景。
    2. **科学发现**——蛋白质设计、材料发现、定理证明等"有 ground-truth verifier"的领域，是 RL-only 路线最容易先冒头的应用。
    3. **游戏 / 仿真世界 NPC**——AlphaGo 的精神继承者，理论上能在任何"可定义奖励"的封闭世界里超越人类。
- **不适合的场景**：开域对话、长文阅读、风格化创作——这些需要海量人类先验的任务，纯 RL 路线短期内**不可能**追上 LLM。
- **商业模式影响**：
    1. **资本市场对"非 LLM 路径"的估值开始定锚**——以前 RL-only startup 拿融资极难；51 亿估值会拉高一票同类 startup（World Labs、Physical Intelligence、Skild AI）的估值倍数。
    2. **Nvidia 又一次卡位**——同时投 OpenAI（Stargate）、xAI、Anthropic（间接）、Ineffable，**对所有路线都不押注于哪一条赢，只确保 GPU 都卖出去**。这个策略今年会越来越明显。
    3. **Google 的"对冲教科书"**——投了 Anthropic（最高 400 亿）、又投自己前员工 Silver 的 Ineffable。我判断：Google 现在对外战略已经从"DeepMind 内部统一作战"切到"内+外多路下注"。
- **PM 立刻要思考的问题**：
    1. 我的产品 roadmap 三年内有没有依赖于"LLM 是唯一通用 AI 接口"的隐含假设？如果不是，会被替换成什么？
    2. 我所在领域有没有"环境 / 奖励信号清晰"的子任务？这些是 RL-only agent 最先入侵的场景。
    3. 如果 Silver 真在 18 个月内放出一个**机器人 / 科学发现 demo** 比 LLM agent 强一个量级，我的客户会不会重新评估"AI 替代人力"的预期？

### 工程视角：技术栈与实现细节
- **核心研究主张**：human-data 是天花板。需要 **infinite stream of experience**，让 agent 在闭环环境中无限自我探索。这要求：
    1. 一个**通用 environment infrastructure**——既能生成高保真模拟（机器人物理、科学实验、博弈对抗），也能接入真实物理世界做闭环。
    2. 一个**通用 RL 算法**——Silver 在 MuZero 的工作上往前推一步，可能是基于 **model-based RL + world model + planning**。我判断他们短期会大量投入"latent world model"方向的研究。
    3. **Reward design 的工程化**——RL-only 路径最大瓶颈不是算力，是 reward 的可定义性。Ineffable 大概率会优先选择 **verifiable reward** 领域（数学、代码、物理）入场，先证明 scaling law 在 experience-only 下成立。
- **基础设施推测（注：以下为推测）**：
    1. **算力构成**——用 11 亿美金的 1/3-1/2（约 4-5 亿美金）建一个 ~10k H200 / B200 等效的训练集群，再加大量 simulator 主机。Nvidia 进表说明硬件管线是 Nvidia 体系，不太可能像 Tesla / Anthropic 那样深度定制 ASIC。
    2. **数据来源**——零或极少的人类预训练数据，对比 GPT-5.5 / Claude Opus 4.7 的 30T+ token，这会是研究界第一次大规模验证"experience-scale > data-scale"是否成立。
    3. **挑战点**——sample efficiency。AlphaZero 训练一局围棋几秒；但训练一个能"用代码改 GitHub repo"的 agent，每个 episode 时长可能是几分钟到几小时，scale 起来是 **数量级 GPU 燃烧**。
- **对开发者工作流影响**：
    1. **短期内基本无**——他们不会发 API、不发 SDK、不发 Hugging Face checkpoint。
    2. 长期看，如果 Silver 团队公开任何 RL training framework / world model / verifier 工具链，会立刻成为 **"LLM 时代之后的 PyTorch / Transformers" 候选**。这是值得**长期 watchlist** 的库。
    3. **对 agent 框架（LangChain、LlamaIndex、OpenAI Agents SDK）的潜在威胁**——如果非 LLM agent 在某个垂直任务上突破，整个"prompt + tool-use loop"范式会被重新审视。
- **工程师立刻要拆的技术细节**：
    1. *Era of Experience* 论文里 Silver 主张的"streams of experience"具体如何工程化？是 continual learning？是 distributed environment workers？
    2. 51 亿估值对一个尚无产品的研究型公司，**回报路径**到底是什么？被收购？IPO？还是 license RL infra 给云厂？
    3. Sequoia / Index 给出的投决逻辑里，是否预设了"3 年内出 demo / 5 年内出可用 agent"的硬指标？

### 可深挖方向（4 条）
- [ ] 方向 1：通读 Silver & Sutton 2025 *Era of Experience* 原文 —— 参考：[Sequoia 介绍页（含论文链接）](https://sequoiacap.com/article/partnering-with-ineffable-intelligence-a-superlearner-for-the-era-of-experience/)
- [ ] 方向 2：对比 Ineffable 与 World Labs（李飞飞）、Physical Intelligence（Karol Hausman）、Skild AI 的技术路线差异 —— 参考：[Index Ventures · Superlearner](https://www.indexventures.com/perspectives/the-superlearner-investing-in-david-silver-and-ineffable-intelligence/)
- [ ] 方向 3：MuZero → Ineffable 的算法继承路线，研究 model-based RL + planning 的最新 SOTA —— 参考：[Pathfounders 拆解](https://pathfounders.com/p/ineffable-intelligence-breaks-out-of-stealth)
- [ ] 方向 4：英国 Sovereign AI Fund 的真实角色——是 LP、是政策杠杆、还是数据 / 算力换投——会决定 Ineffable 的研究开放度 —— 参考：[GOV.UK 官方公告](https://www.gov.uk/government/news/uk-backs-company-building-breakthrough-ai-that-can-discover-new-knowledge)

---

## 今日整体判断（一句话）

**4 月 27 日同时发出两个信号——商业层面"模型分发自由化"和研究层面"非 LLM 路线被资本承认"——本质上都是对"LLM-on-Azure 一家独大"叙事的双向解构**。前者打开了下一阶段 multi-cloud / multi-model 的工程红利空间，后者埋下了下一代范式潜在的种子。现在最值得 PM / 工程师做的事，就是**把自己产品和技术栈里隐含的"LLM + 单一 vendor"假设全部列出来，逐条审视哪些会在 18 个月内动摇**。
