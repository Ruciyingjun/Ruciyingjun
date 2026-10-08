## Hi there 👋

# 👋 你好，我是郭炳勋

### AI Agent · Reliable Multi-Agent · Agentic RAG

🎓 中国科学院大学 · 计算机技术硕士在读  
🔬 目前主要关注 **Reliable Multi-Agent / Agent Systems**

我希望构建的不只是“能运行”的 AI Agent，
而是能够真正进入工程环境的：

**可靠、可控、可恢复、可追溯、可评测的 Agent 系统。**

目前主要关注：

- 🤖 Agent Runtime / Harness
- 🧩 Multi-Agent 协作
- 🧠 Context Engineering & Memory
- 📚 Agentic RAG
- 🧪 Agent Evaluation
- 🔍 Citation / Provenance
- 🔄 Feedback-driven Agent Optimization

---

# 🧭 About Me

本科就读于 **人工智能专业**。

本科阶段主要围绕：

- 机器学习与深度学习
- 模型微调与 AI 应用
- 算法 / AI 类竞赛
- 小型 AI 工程项目
- 技术博客与知识总结

进行过比较广泛的实践。

研究生阶段，我逐渐把关注点从：

**训练模型 → 构建 AI 应用 → 构建可靠 Agent 系统**

转向 Agent Systems。

相比单纯关注“模型能不能完成任务”，
我现在更感兴趣的是一些偏系统的问题：

> Agent 执行一个长任务时，服务中断了怎么办？

> Multi-Agent 为什么一定比 Single-Agent 更好？

> Agent 的中间执行过程如何被观察和复现？

> 如何控制 Agent 的上下文和 Token Budget？

> 如何建立可靠的 Agent Evaluation？

> RAG 生成的答案，如何证明它真的有证据支持？

这些问题也是我目前两个主要项目的出发点。

---

# 🚀 Featured Projects

## 🛡️ [TraceGuard](https://github.com/Ruciyingjun/TraceGuard)

### 面向 PR 风险治理的可信 Multi-Agent Runtime

TraceGuard 是一个面向研发过程 PR 风险治理和安全修复场景的
**Multi-Agent 代码审查系统**。

它不只是简单串联多个 LLM，而是尝试从 Runtime、协作、上下文、
评测和反馈优化几个层面，提高 Agent 系统的可靠性。

### 🏗️ Multi-Agent Architecture

`Lead Agent`

↓  

`Security Worker + Reliability Worker`

↓  

`Critic`

↓  

`Lead Final Decision`

其中：

- **Lead Agent**
  - 风险判断
  - 任务拆分
  - Worker 调度
  - 最终决策

- **Security Worker**
  - 安全风险调查

- **Reliability Worker**
  - 可靠性问题调查

- **Critic**
  - 对候选 Findings 进行独立证据复核
  - 尽量减少错误确认和误报

---

### ⚙️ Recoverable Agent Runtime

围绕长任务执行，实现了一套可恢复 Agent Runtime：

- Task State 管理
- Execution Budget
- Node Retry
- Persistent Checkpoint
- 断点续跑
- Run Trace
- 任务回放
- 失败归因
- Evaluation Reproduction

并基于：

`Plan → Tool → Observe → Final`

构建有界执行循环。

---

### 🧠 Context Engineering & Memory

针对长 Diff 和有限上下文问题：

- 基于 Risk Hunk 构建局部上下文
- 根据 Token Budget 动态压缩
- 保留关键历史 Observation
- 管理任务级 Memory

目前将 Memory 按用途划分为：

- Working Memory
- Episodic Memory
- Semantic Memory
- Procedural Memory

---

### 🔄 Feedback-driven Optimization

将系统运行过程中的：

- False Positive
- False Negative
- Bad Fix
- Runtime Exception

沉淀为失败案例。

基于失败案例生成候选 Prompt / Skill，
并通过：

`Candidate Generation`

↓

`Validation`

↓

`Holdout Non-regression Gate`

↓

`Activate / Rollback`

形成受控优化流程。

---

### 🧪 Evaluation Harness

搭建了 **100 个受控 PR Diff** 的端到端 Evaluation Harness：

- 40 个风险样本
- 60 个干净样本

实验结果：

- **Finding F1：81.9% → 91.3%**
- **High-risk Recall：84.2% → 94.7%**
- **Clean PR Accuracy：91.7%**

---

### 🛠️ Tech Stack

`Python`

`Agent Runtime`

`Multi-Agent`

`Redis Streams`

`PostgreSQL`

`SQLite`

`Docker`

`Prometheus`

`Webhook`

---

# 📊 [FinSight](https://github.com/Ruciyingjun/FinSight)

### 金融研报 Agentic RAG 智能问答系统

FinSight 最开始来源于我自己阅读金融研报时遇到的一些问题：

- 文档很长
- 表格经常跨页
- 普通 Chunking 容易破坏上下文
- 向量检索并不总能找到正确证据
- LLM 回答存在幻觉
- 回答正确与否难以验证

所以我希望构建一套：

> **可靠、可追溯、可降级的金融资料智能问答流水线。**

---

## 🏗️ Pipeline

整体链路：

`Document Parsing`

↓

`Cleaning & Pagination`

↓

`Cross-page Semantic Chunking`

↓

`Embedding & Indexing`

↓

`Agentic Query Planning`

↓

`BM25 + Embedding Retrieval`

↓

`RRF Fusion`

↓

`Second-stage Reranking`

↓

`Evidence Gate`

↓

`Grounded Generation`

↓

`Citation Provenance`

↓

`原文定位与高亮`

---

### 📄 Cross-page Structured Chunking

将文档处理拆分为：

- 解析
- 清洗
- 分页
- 语义切块
- 向量化
- 索引构建

支持：

- 10+ 文档格式
- 并发调度
- 状态追踪
- 失败重试
- 服务重启恢复

重点处理长研报以及跨页结构信息。

---

### 🧠 Agentic Query Planning

用户 Query 并不会默认进入 RAG。

Agent 首先完成：

- 意图识别
- 策略选择
- 动态路由

目前支持：

`User Query`

├── `Direct Answer`

├── `Clarification`

└── `Fact Retrieval`

希望避免简单问题产生无效检索，
同时避免复杂问题进入错误执行路径。

---

### 🔍 Hybrid Retrieval

检索阶段同时使用：

**BM25 Sparse Retrieval**

+

**Embedding Dense Retrieval**

然后通过：

**RRF（Reciprocal Rank Fusion）**

完成两路结果融合。

之后综合：

- Query Coverage
- Matching Density
- Relative Score
- Absolute Threshold

进行二阶段重排与 Evidence Gate。

实验中：

**Recall@5 相较 BM25 Baseline 提升 17.8%。**

---

### 📌 Citation & Provenance

FinSight 不希望只告诉用户：

> “根据研报显示……”

而是希望回答能够真正追溯到原始证据。

因此建立：

`Answer Claim`

↓

`Citation`

↓

`Supporting Chunk`

↓

`Document Metadata`

↓

`Page / Paragraph`

↓

`Original Document`

的端到端溯源链路。

目前支持：

- 回答句级 Citation
- 元数据绑定
- 原文页码定位
- 段落位置定位
- 前端一键高亮原文

实验中：

**Citation 支持准确率达到 89.6%。**

---

### 🛠️ Tech Stack

`Java`

`Spring Boot 3`

`Spring MVC`

`Spring Data JPA`

`Hibernate`

`Apache PDFBox`

`BM25`

`Embedding`

`Agentic RAG`

`Maven`

---

# 🧠 What I'm Exploring

目前比较感兴趣的方向：

### Agent Systems

- Reliable Agent
- Agent Runtime
- Agent Harness
- Multi-Agent Systems
- Agent Coordination
- Agent Memory
- Context Engineering
- Agent Evaluation

### RAG & Knowledge Systems

- Agentic RAG
- Hybrid Retrieval
- Reranking
- Evidence Gate
- Citation
- Provenance

### AI Engineering

- LLM Application Engineering
- Model Fine-tuning
- AI System Evaluation
- Failure Analysis
- Feedback-driven Optimization

目前最感兴趣的问题是：

> **如何把一个“看起来很聪明的 Agent Demo”，
> 真正变成一个可以长期运行、可以失败恢复、
> 可以评测、可以解释、可以信任的工程系统？**

---

# 🧬 From Model to Agent System

我的技术经历大致经历了这样一个变化：

```text
Machine Learning
       ↓
Deep Learning
       ↓
Model Fine-tuning
       ↓
AI Applications
       ↓
RAG / LLM Applications
       ↓
Agent Systems
       ↓
Reliable Agent Systems
