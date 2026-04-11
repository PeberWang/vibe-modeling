# Vibe Modeling 🧮

> **通过与 AI 协作，将经济学直觉形式化为严谨模型的工作站**

Vibe Modeling 是 Vibe Coding 的姊妹项目。Vibe Coding 解决的是"如何把想法变成代码"，Vibe Modeling 解决的是"如何把直觉变成模型"。

**核心理念**: *先形式化，再计算。模型服务于直觉，不被形式绑架。*

## 什么是 Vibe Modeling？

经济学建模的真实过程往往不是教科书里展示的那样——先有清晰的假设，再一步步推导出优雅的结论。更多时候是：

1. 你有一个**模糊的经济学直觉**（"举报人好像在某种条件下会选择不举报"）
2. 你**尝试形式化**（写下一个博弈树或效用函数）
3. 你**求解或模拟**，看看均衡长什么样
4. 你发现均衡结果"经济学上说不通"——**回到第2步修改假设**
5. 重复直到模型行为与你的直觉（和经验证据）一致

这个过程跟 Vibe Coding 的核心体验一模一样：**在形式化的领域里，靠直觉和反复试错去逼近一个你自己还没完全想清楚的东西。**

## 本项目与 OpenClaw

本项目专为 [OpenClaw](https://github.com/openclaw/openclaw) 生态设计：

- **Skills** 遵循 OpenClaw 的 `SKILL.md` 格式，可直接挂载到 Agent
- **提示词** 针对 OpenClaw 的 session 上下文管理和工具调用优化
- **工作流** 融入 OpenClaw 的 memory 系统、cron 定时推进、session 溢出管理等机制

## 🧭 道

- **先形式化，再计算**——不要急于求解，先确保模型结构正确
- **模型服务于直觉**——均衡结果必须能回到经济学语言解释，否则模型有问题
- **一次只改一个假设**——多变量同时变化无法定位问题
- **上下文是第一性要素**——建模所需的文献、田野观察、理论背景，先喂给 AI
- **最小模型原则**——能用两期博弈说清楚的事，不要建模为无限期
- **目的主导**——建模过程中的一切动作围绕"你要回答的研究问题"展开

## 🧩 法

- **一句话目标 + 非目标**：建模前先写清楚"这个模型要解释什么，不解释什么"
- **模型设计文档先行**：先写设计文档，再动笔推导或编码
- **核心假设与简化假设分离**：明确哪些假设是论证的核心，哪些仅为了可解性
- **接口先行，求解后补**：先定义解概念和均衡类型，再考虑怎么算
- **切 session 保命**：模型推导一复杂就开新 session，别让 token 溢出吞掉你的工作

## 🛠️ 术

- **Debug 只给**：预期均衡 vs 实际均衡 + 最小可现示例
- **验证方法**：极端参数检验（参数趋0/趋∞时均衡是否退化到已知情形）
- **文献优先**：建模前先让 AI 检索相关文献，避免重复造轮子
- **数值模拟先行**：先写 Python 脚本数值探索参数空间，再尝试解析解

## 📋 器

### 建模工具
- **LaTeX (XeLaTeX)**：论文写作与排版
- **Python + NumPy/SciPy**：数值模拟与参数探索
- **Mathematica / Maple**：符号计算
- **Overleaf**：协作写作

### AI 工具
- **OpenClaw**：本项目的一站式 AI 协作平台
- **ChatGPT / Claude**：辅助建模讨论（当 OpenClaw session 溢出时切换）

### 辅助工具
- **TikZ / GeoGebra**：博弈树和相位图绘制
- **Stata / R**：数据处理与计量分析

---

## 📂 项目结构

```
vibe-modeling/
├── README.md                        # 本文件
├── AGENTS.md                        # OpenClaw Agent 行为规范
├── .gitignore
├── LICENSE
│
├── documents/                       # 知识库
│   ├── Methodology and Principles/  # 方法论与原则
│   │   ├── 元方法论.md              # 递归自优化的建模系统
│   │   ├── 模型构建原则.md          # 道·法·术·器 详解
│   │   └── 形式化写作规范.md        # LaTeX 论文写作最佳实践
│   ├── Tutorials and Guides/        # 教程与指南
│   │   ├── 从直觉到模型.md          # 核心工作流教程
│   │   ├── 均衡分析方法.md          # 博弈论常用工具
│   │   └── OpenClaw建模工作流.md    # 如何用 OpenClaw 高效建模
│   └── Templates and Resources/     # 模板与资源
│       ├── 模型设计文档模板.md       # 类比 game-design-document
│       ├── 实施计划模板.md           # 分步形式化计划
│       └── 进度追踪模板.md           # progress.md
│
├── prompts/                         # 提示词库（OpenClaw 优化）
│   ├── modeling_prompts/            # 建模专用
│   │   ├── 需求澄清.md              # 把模糊直觉转化为建模问题
│   │   ├── 形式化.md                # 将文字描述转化为数学表达
│   │   ├── 均衡分析.md              # 求解与验证均衡
│   │   └── 参数校准.md              # 从经验数据校准模型参数
│   ├── system_prompts/              # 系统级提示词
│   │   ├── 建模规范.md              # Agent 建模行为准则
│   │   └── 学术写作规范.md          # 论文写作风格与格式
│   ├── writing_prompts/             # 论文写作
│   │   ├── 摘要生成.md
│   │   ├── 引言撰写.md
│   │   ├── 文献综述.md
│   │   └── 模型章节.md
│   └── meta_prompts/                # 元提示词
│       └── 提示词优化器.md           # 优化其他提示词的元提示词
│
├── skills/                          # OpenClaw Skills
│   ├── game-theory/
│   │   └── SKILL.md                # 博弈论知识与建模技巧
│   ├── mechanism-design/
│   │   └── SKILL.md                # 机制设计
│   ├── formal-proofs/
│   │   └── SKILL.md                # 形式化证明技巧
│   ├── latex-writing/
│   │   └── SKILL.md                # LaTeX 写作与编译
│   └── literature-search/
│       └── SKILL.md                # 文献检索与综述
│
├── examples/                        # 示例项目
│   └── whistleblower-game/          # 举报人博弈模型
│       ├── 模型设计文档.md
│       ├── progress.md
│       └── references/
│
└── log/                             # 项目推进日志
```

---

## 🚀 快速开始

1. Clone 本仓库
2. 在 OpenClaw workspace 中创建指向本项目的 skills 链接
3. 阅读 `documents/Tutorials and Guides/从直觉到模型.md`
4. 用 `documents/Templates and Resources/模型设计文档模板.md` 开始你的第一个模型

---

## 🤝 参与贡献

欢迎通过 Issue 或 PR 贡献新的提示词、技能、教程和示例项目。

---

## 📜 许可证

MIT License

---

*Vibe Coding 把想法变成代码，Vibe Modeling 把直觉变成模型。*
