# 高级 RAG 技术：检索增强生成系统进阶实践

这是对原项目 [NirDiamant/RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) 的中文化整理版本，目标是帮助中文读者更顺畅地学习和实践 Retrieval-Augmented Generation（RAG）相关技术。

项目中包含大量 notebook、可运行脚本、辅助函数和评估示例，覆盖从基础 RAG 到更复杂的检索增强、重排、图结构、评估与 Agentic RAG 等方向。

## 项目定位

这个仓库适合：

- 想系统学习 RAG 工作流的初学者
- 想比较不同切块、检索、重排和评估策略的开发者
- 想把 notebook 中的实验思路迁移到自己业务场景的实践者

你可以把它理解为一个“RAG 技术样例库”：

- 前半部分偏基础与核心流程
- 中间部分偏检索增强与上下文优化
- 后半部分偏高级架构、评估与更复杂的系统设计

## 仓库结构

- [all_rag_techniques](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques)：主要 notebook 教程
- [all_rag_techniques_runnable_scripts](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques_runnable_scripts)：部分 notebook 对应的可运行 `.py` 脚本
- [evaluation](/home/test/Desktop/code/RAG_Techniques/evaluation)：RAG 评估相关 notebook 与代码
- [helper_functions.py](/home/test/Desktop/code/RAG_Techniques/helper_functions.py)：多个 notebook 共用的辅助函数
- [data](/home/test/Desktop/code/RAG_Techniques/data)：示例数据文件
- [images](/home/test/Desktop/code/RAG_Techniques/images)：README 和 notebook 使用的图片资源

## 快速开始

1. 克隆你自己的 fork 或本仓库。
2. 创建虚拟环境并安装依赖。
3. 根据所使用的 notebook 准备对应的 API key 或本地模型。
4. 从 [all_rag_techniques](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques) 中挑选一个 notebook 开始运行。

示例：

```bash
git clone https://github.com/githubyounik/RAG_Techniques.git
cd RAG_Techniques
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

说明：

- 某些 notebook 默认依赖 OpenAI、Cohere 或 Bedrock 等在线模型服务
- 如果你没有对应 API key，可以优先阅读 notebook 思路，或者把 embedding / LLM 替换为本地模型
- 在 VS Code 本地运行 notebook 时，路径问题通常与“当前工作目录”有关，而不一定和 notebook 文件所在位置相同

## 学习路径建议

如果你第一次接触这个仓库，推荐按下面顺序学习：

1. [simple_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/simple_rag.ipynb)
2. [choose_chunk_size.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/choose_chunk_size.ipynb)
3. [reliable_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/reliable_rag.ipynb)
4. [query_transformations.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/query_transformations.ipynb)
5. [reranking.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/reranking.ipynb)
6. [graph_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/graph_rag.ipynb)
7. [evaluation](/home/test/Desktop/code/RAG_Techniques/evaluation) 目录下的评估 notebook

## 主要技术目录

下面是仓库中较核心的一批主题，便于你快速定位：

| 类别 | 技术 | 说明 |
|---|---|---|
| 基础 | Basic RAG | 最基础的加载、切块、向量化、检索与回答流程 |
| 基础 | RAG with CSV | 面向结构化表格数据的简单 RAG |
| 基础 | Reliable RAG | 引入校验与更稳健的回答流程 |
| 基础 | Choose Chunk Size | 比较不同 chunk size 对效果与速度的影响 |
| 基础 | Proposition Chunking | 以命题粒度切块，提升知识抽取与精细检索 |
| 查询增强 | Query Transformations | 查询改写、拆分、step-back 等策略 |
| 查询增强 | HyDE | 先生成假设文档，再用其辅助检索 |
| 查询增强 | HyPE | 使用假设提示增强 embedding 检索 |
| 上下文增强 | Contextual Chunk Headers | 为 chunk 加入上下文标题 |
| 上下文增强 | Relevant Segment Extraction | 抽取更相关的局部文本片段 |
| 上下文增强 | Context Window Enhancement | 为命中 chunk 补充前后窗口上下文 |
| 上下文增强 | Semantic Chunking | 按语义而不是固定长度切块 |
| 上下文增强 | Contextual Compression | 先检索，再压缩上下文 |
| 上下文增强 | Document Augmentation | 通过补充文档信息改善检索效果 |
| 高级检索 | Fusion Retrieval | 融合多个检索结果 |
| 高级检索 | Reranking | 对召回结果进行重排 |
| 高级检索 | Hierarchical Indices | 分层索引，兼顾摘要层与细节层 |
| 高级检索 | Dartboard Retrieval | 基于中心与边界思想改进召回 |
| 迭代技术 | Retrieval with Feedback Loop | 把反馈纳入后续检索 |
| 迭代技术 | Adaptive Retrieval | 根据问题动态调整检索策略 |
| 可解释性 | Explainable Retrieval | 让检索结果更容易解释 |
| 高级架构 | Graph RAG | 将图结构与 RAG 结合 |
| 高级架构 | Microsoft GraphRAG | 微软 GraphRAG 相关实践 |
| 高级架构 | RAPTOR | 递归摘要与树结构索引 |
| 高级架构 | Agentic RAG | 用 Agent 驱动更复杂的 RAG 工作流 |
| 高级架构 | Self-RAG | 让模型对检索与回答过程进行自反思 |
| 高级架构 | CRAG | Corrective RAG，强调纠错与校正 |
| 评估 | DeepEval / GroUSE / End-to-End Eval / Open-RAG-Eval | 对 RAG 系统质量进行系统化评估 |

## 推荐从这些 notebook 开始

### 基础入门

- [simple_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/simple_rag.ipynb)
- [simple_rag_with_llamaindex.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/simple_rag_with_llamaindex.ipynb)
- [simple_csv_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/simple_csv_rag.ipynb)
- [choose_chunk_size.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/choose_chunk_size.ipynb)
- [reliable_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/reliable_rag.ipynb)

### 检索增强

- [query_transformations.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/query_transformations.ipynb)
- [HyDe_Hypothetical_Document_Embedding.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/HyDe_Hypothetical_Document_Embedding.ipynb)
- [HyPE_Hypothetical_Prompt_Embeddings.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/HyPE_Hypothetical_Prompt_Embeddings.ipynb)
- [fusion_retrieval.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/fusion_retrieval.ipynb)
- [reranking.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/reranking.ipynb)

### 上下文处理

- [contextual_chunk_headers.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/contextual_chunk_headers.ipynb)
- [context_enrichment_window_around_chunk.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/context_enrichment_window_around_chunk.ipynb)
- [semantic_chunking.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/semantic_chunking.ipynb)
- [contextual_compression.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/contextual_compression.ipynb)

### 更复杂的架构

- [graph_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/graph_rag.ipynb)
- [Microsoft_GraphRag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/Microsoft_GraphRag.ipynb)
- [raptor.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/raptor.ipynb)
- [Agentic_RAG.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/Agentic_RAG.ipynb)
- [self_rag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/self_rag.ipynb)
- [crag.ipynb](/home/test/Desktop/code/RAG_Techniques/all_rag_techniques/crag.ipynb)

### 评估

- [evaluation_deep_eval.ipynb](/home/test/Desktop/code/RAG_Techniques/evaluation/evaluation_deep_eval.ipynb)
- [evaluation_grouse.ipynb](/home/test/Desktop/code/RAG_Techniques/evaluation/evaluation_grouse.ipynb)
- [evalute_rag.py](/home/test/Desktop/code/RAG_Techniques/evaluation/evalute_rag.py)

## 运行时注意事项

### 1. API 依赖

仓库中的许多 notebook 默认依赖以下一类或多类服务：

- OpenAI
- Cohere
- Amazon Bedrock
- LlamaIndex / LangChain 对应集成包

如果你本地没有这些 API key：

- 可以先阅读 notebook 逻辑
- 可以把在线 embedding 模型替换为本地 HuggingFace embedding
- 可以先跳过依赖 LLM 评估的部分

### 2. 路径问题

很多 notebook 最初是按 Colab 场景写的，因此你在本地 VS Code 中运行时要特别注意：

- `sys.path.append(...)` 是相对于当前工作目录生效
- `os.makedirs("data")` 也是相对于当前工作目录
- notebook 文件位置和运行目录不一定一致

如果遇到 `No module named 'helper_functions'`，通常是因为 Python 搜索路径没有包含仓库根目录。

### 3. README 与 notebook 的关系

README 用来帮助你快速导航；真正的技术细节和代码实现主要在 notebook 中。如果你想深入理解某项技术，优先打开对应 notebook。

## 与上游仓库的关系

本仓库是原项目的中文化 fork，建议保留与上游仓库的同步能力。常见做法是：

```bash
git remote add upstream https://github.com/NirDiamant/RAG_Techniques.git
git fetch upstream
git merge upstream/main
```

如果你对 notebook 做了中文翻译或本地化修改，建议每次同步上游后检查：

- README 是否出现新的技术目录
- 新增 notebook 是否需要中文化
- 导入路径、依赖版本、工作流文件是否有变化

## 致谢

感谢原作者和所有贡献者维护这个高质量的 RAG 技术仓库。这个中文版本主要服务于中文学习和实践场景，核心技术内容与灵感均来自上游项目及其社区贡献。
