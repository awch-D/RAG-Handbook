# RAG-Handbook · 检索增强生成工程手册

> A practical Chinese handbook on advanced Retrieval-Augmented Generation — from Naive RAG to Multimodal visual retrieval, Agentic self-reflection, GraphRAG community detection, and declarative prompt tuning.

[![License](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Active-brightgreen.svg)](https://awch-D.github.io/RAG-Handbook/)

## 简介

当前大语言模型的落地最核心的瓶颈在于如何让模型精确、可靠地访问组织内部的海量异构知识。

`RAG-Handbook` 是一份开源的、零构建依赖的单文件 HTML 中文教学手册与工程指南。它围绕检索增强生成（RAG）的演进脉络，系统解释如何将朴素的语义搜索，升级为融合多模态版面、智能体自主控制、知识图谱拓扑聚合以及工程化声明调参的工业级认知系统。

---

## 💡 核心范式：比喻、本质与工程痛点

为了帮您和团队快速理清技术路线，以下提炼了 4 种 RAG 的核心维度对比：

| RAG 范式 | 形象类比 (Analogy) | 一句话本质 (Core Essence) | 核心工程痛点 / 踩坑点 (Hard Truths) |
| :--- | :--- | :--- | :--- |
| **传统 RAG** *(Naive / Advanced)* | **开卷考试 (Open-book)**<br>翻书后目录索引，定位到相关页面后抄写答案。 | 基于局部语义相似度的**分块检索与上下文拼接**。 | 1. **Lost in the Middle**：长上下文中间信息易丢失。<br>2. **表格塌陷**：解析时表格结构错乱，向量匹配失效。 |
| **多模态 RAG** *(以 ColPali 为代表)* | **带插图的绘本考试**<br>不仅读文字，还要结合图片版面、图表位置和视觉细节作答。 | 基于文档图像的**补丁级多向量对齐与晚期交互**检索。 | 1. **显存黑洞**：极其消耗 GPU 显存。<br>2. **存储空间爆炸**：每个页面产生上千向量，数据库**存储开销膨胀 10-100 倍**。 |
| **Agentic RAG** *(智能体 RAG)* | **带侦探思维的学术助理**<br>检索不够就多步规划、自我反思、更换工具，确认无误再交卷。 | 将检索作为 **Tool** 调用，通过**规划、路由与反思纠错环路**实现自主闭环。 | 1. **执行漂移与死循环**：极易陷入无限循环检索。<br>2. **高时延与 Token 爆炸**：多次调用 LLM 导致单次首字返回（TTFT）高达数十秒。 |
| **GraphRAG** *(图谱 RAG)* | **线索墙思维导图考试**<br>建立人物和事件的蛛网连线，划分案卷，总结全局宏观隐患。 | 基于图提取实体关系，运行 **Leiden 聚类算法**，对多级社区报告执行 **Map-Reduce 全局提炼**。 | 1. **建图账单陷阱**：建索引阶段要提取数十万实体，LLM 费用极高。<br>2. **Leiden 分辨率极难调**。<br>3. **增量更新极困难**。 |

---

## 🛠️ 快速选型决策树

在实际业务落地中，您可以通过以下逻辑快速定型：

```text
您的查询属于哪种类型？
 ├── 1. 具体的事实查询 (如 "A产品的退货率是多少")
 │    └── 是否有大量复杂图表、PDF 扫描件？
 │         ├── 是  --> 【多模态 RAG (ColPali/视觉多向量)】
 │         └── 否  --> 【传统高级 RAG (混合检索 + 重排器)】
 │
 ├── 2. 跨文档/全局主旨总结 (如 "总结今年公司供应链的主要隐患")
 │    └── --> 【GraphRAG (基于 Leiden 社群多级摘要 & Map-Reduce)】
 │
 └── 3. 复杂、需跨多系统求证 (如 "对比甲乙两公司财务数据并生成对比分析邮件")
      └── --> 【Agentic RAG (LangGraph 状态图 / LlamaIndex Workflows 事件流)】
```

---

## 📖 12章手册目录

| # | 章节 | 核心内容 |
|---|---|---|
| 00 | RAG 演进路线 | 纵览 RAG 从 Naive 到 Advanced，再到 Agentic/Graph 的发展大图 |
| 01 | RAG 到底是什么 | 经典学术定义（Lewis, 2020）与企业工程定义，解构四位一体公式 |
| 02 | 为什么需要演进 | Naive RAG 的四大崩溃点：噪声干扰、长文丢失、全局 summaries 失灵 |
| 03 | 演进全景与技术栈 | RAG 三次技术浪潮，划分“应用-编排-检索-索引-基础”五层技术架构 |
| 04 | 传统/高级 RAG 架构 | 查询重写、HyDE 伪文档、混合检索、双塔 Rerank 与上下文压缩 |
| 05 | 多模态 RAG 架构 | 传统 OCR 文本转换路径 vs ColPali 视觉多向量晚期交互（Late Interaction） |
| 06 | Agentic RAG 架构 | Planner-Tool 结构，LangGraph 状态机与 LlamaIndex EDA 异步事件机制对比 |
| 07 | GraphRAG 架构 | 实体抽取、Leiden 社群聚类、Global (Map-Reduce) 与 Local 图谱检索原理 |
| 08 | 架构对比与决策 | 整理四大架构在延迟、建库成本、运行成本与适用场景的对比矩阵 |
| 09 | 工业级工具链 | Milvus、Neo4j、PGVector、LlamaIndex 框架与声明式 Prompt 优化（DSPy） |
| 10 | 落地误区与反模式 | 规避暴力切片、图膨胀、时延灾难、长窗口注意力滑坡等六大反模式 |
| 11 | 成熟度与验收 | L0—L5 认知演进模型、10 项上线前 Checklist 及验收证据标准 |
| 12 | 术语、自测与资料 | 10 个核心术语、基于网页 JS 的 3 道交互式自测题与一手开山文献 |

---

## 🚀 本地开发与预览

手册采用零构建、无 Node.js、完全独立单文件 HTML 架构设计，支持完全无网/离线查看。

直接使用浏览器打开即可：
```bash
open index.html        # macOS
# xdg-open index.html  # Linux
# start index.html     # Windows
```

---

## 📦 项目结构

```text
RAG-Handbook/
├── .github/
│   └── workflows/
│       └── pages.yml   # GitHub Pages 自动部署工作流
├── .gitignore          # 忽略系统与编辑器临时文件
├── LICENSE             # Apache-2.0 许可证文件
├── README.md           # 项目详细说明（本文件）
└── index.html          # 无依赖交互式前端原型与手册正文
```

---

## 📝 许可证

本项目基于 [Apache-2.0 License](LICENSE) 协议开源。
