# RAG-Handbook · 检索增强生成工程手册

> A practical Chinese handbook on advanced Retrieval-Augmented Generation — from Naive RAG to Multimodal visual retrieval, Agentic self-reflection, GraphRAG community detection, and declarative prompt tuning.

## 简介

当前大语言模型的落地最核心的瓶颈在于如何让模型精确、可靠地访问组织内部的海量异构知识。

本仓库是一份零依赖、单文件 HTML 中文教学手册，围绕检索增强生成（RAG）的演进脉络，系统解释如何将朴素的语义搜索，升级为融合多模态版面、智能体自主控制、知识图谱拓扑聚合以及工程化声明调参的工业级认知系统。

## 核心公式

```text
现代 RAG 系统 = 混合检索与重排 + 多模态空间对齐 + 智能体自纠错环路 + Leiden 拓扑社区总结
```

它不仅回答“如何定位相关片段”，还回答：

- 复杂的非文本排版与图表如何检索
- 如何避免大模型因检索噪音而产生幻觉
- 智能体如何动态调整检索策略并自主纠正
- 如何针对全域知识生成跨实体的主旨总结

## 特性

- 12 章完整中文技术体系，全景呈现 RAG 的演进脉络
- 传统 RAG、多模态 RAG、Agentic RAG、GraphRAG 四大架构深度拆解
- 详尽的四大架构横向对比决策矩阵（包括延迟、建索引成本、运行成本等）
- Microsoft GraphRAG（Leiden 社群检测）与 ColPali 原生多模态晚期交互检索的核心原理解析
- LangGraph 状态机与 LlamaIndex Workflows 事件驱动的智能体编程范式对比
- 工业级技术栈及声明式 Prompt 优化（DSPy 编译）介绍
- 10 项上线前核心检查清单与验收证据标准
- 滚动联动导航目录、默认展开释义、交互式标签页、自测题和打印样式
- 单文件、零构建、完全响应式、无远程 UI 依赖

## 章节目录

| # | 章节 | 核心内容 |
|---|---|---|
| 00 | RAG 演进路线 | 纵览 RAG 从 Naive 到 Agentic/Graph 的发展大图 |
| 01 | RAG 到底是什么 | 经典论文定义、企业级工程定义与核心组件 |
| 02 | 为什么需要演进 | Naive RAG 的崩溃点：噪音、碎片化、无法全局总结 |
| 03 | 演进全景与技术栈 | RAG 1.0、2.0 与 3.0+ 发展浪潮与模块化分层 |
| 04 | 传统/高级 RAG 架构 | 查询重写、HyDE、混合检索、双塔 Rerank 与上下文压缩 |
| 05 | 多模态 RAG 架构 | 文本化转换 vs 原生共享向量空间 (ColPali/MaxSim) |
| 06 | Agentic RAG 架构 | Planner-Tool 角色、LangGraph 状态机与 LlamaIndex EDA |
| 07 | GraphRAG 架构 | 实体提取、Leiden 社群聚类、Global (Map-Reduce) vs Local 搜索 |
| 08 | 架构对比与决策 | 延迟、建索引成本、API成本及适用场景对比矩阵 |
| 09 | 工业级工具链 | Milvus、Neo4j、PGVector、LlamaIndex 与 DSPy 编译 |
| 10 | 落地误区与反模式 | 规避上下文迷失、暴力切片、图膨胀、时延灾难等反模式 |
| 11 | 成熟度与验收 | L0—L5 成熟度等级、10 项上线检查点与合格证据标准 |
| 12 | 术语、自测与资料 | 10个核心术语、3道交互式自测题与学术开山文献汇总 |

## 本地查看

无需安装任何依赖或执行构建，直接打开 HTML 文件即可：

```bash
open index.html        # macOS
# xdg-open index.html  # Linux
# start index.html     # Windows
```

## GitHub Pages 部署

本仓库配置了自动化构建流水线。推送到 `main` 分支后，`.github/workflows/pages.yml` 会自动将该手册发布到 GitHub Pages。

若要开启，请在你的 GitHub 仓库 **Settings → Pages** 中将 Build and deployment 的 Source 设置为 **GitHub Actions** 即可。

## 技术实现

- HTML5
- 原生 CSS：变量、Grid、Flexbox、响应式与打印样式
- 原生 JavaScript：滚动联动（IntersectionObserver）、标签页切换与答题交互
- 内嵌 SVG favicon，支持完全离线无网运行
- 无 Node.js、无包管理器、无任何远程 UI 或 JS 资源依赖

## 项目结构

```text
RAG-Handbook/
├── .github/
│   └── workflows/
│       └── pages.yml
├── .gitignore
├── index.html
└── README.md
```

## 许可证

本项目采用 MIT 协议授权。
