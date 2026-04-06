# 大模型驱动的纯表格信用评分跨域冷启动研究体系
# LLM-Driven Tabular Cross-Domain Cold-Start Credit Scoring: Research Survey & Paper Blueprint

> 🌐 **在线预览 / Live Demo**: [点击打开 HTML 展示页面](https://wanglinhuide.github.io/tabular-foundation-model-credit-scoring/) | [GitHub Pages Link](https://wanglinhuide.github.io/tabular-foundation-model-credit-scoring/)

---

## 📌 项目简介 | Project Overview

本仓库系统整理了面向 **KDD / AAAI / NeurIPS / MISQ / ISR / DSS** 顶会顶刊的完整学术研究体系，聚焦于：

> **"大语言模型（LLM）驱动的纯表格信用评分跨域冷启动"**  
> 即在源域（公开Kaggle/UCI数据）与目标域（银行私有新客群数据）**列名完全异构、维度不匹配（$d_A \neq d_B$）、仅50条样本** 的极端约束下，实现高精度信用风险预测。

This repository organizes a complete academic research system targeting **KDD / AAAI / NeurIPS / MISQ / ISR / DSS**, focusing on:

> **"LLM-driven pure tabular credit scoring under cross-domain cold-start"**  
> Achieving high-precision credit risk prediction under extreme constraints: fully heterogeneous column names, dimension mismatch ($d_A \neq d_B$), and only ~50 target-domain samples.

---

## 🗂️ 仓库结构 | Repository Structure

```
tabular-foundation-model-credit-scoring/
├── index.html              # 双语交互式HTML展示页（推荐入口）
├── README.md               # 本文件
├── survey/
│   ├── literature.md       # 完整文献目录（25篇，含DOI/ArXiv链接）
│   └── review_text.md      # 800字学术综述正文（中英双语）
├── blueprints/
│   ├── paper1_HiTA.md      # 论文一蓝图：HiTA（KDD/AAAI方向）
│   └── paper2_TabularRAG.md # 论文二蓝图：Tabular-RAG（MISQ/ISR方向）
└── assets/
    └── framework_diagram.md # 方法论框架说明
```

---

## 🔥 核心研究命题 | Core Research Proposition

### The "A → B" Paradigm

```
源域 A (Source Domain)          目标域 B (Target Domain)
─────────────────────          ──────────────────────────
• Kaggle/UCI 公开数据           • 银行私有新客群数据
• 列名: {age, income, ...}     • 列名: {x1, x2, ...} ← 完全不同！
• 维度: d_A = 30               • 维度: d_B = 15  ← 不匹配！
• 样本: N_A = 100,000          • 样本: N_B = 50  ← 极少！
• 标签: 已知违约/正常           • 标签: 极少/无
```

**目标**：从 A → B，实现 Zero-shot/Few-shot 信用评分，KS ≥ 0.30

---

## 📚 文献体系 | Literature System

### 子方向分类 | Sub-direction Classification

| 编号 | 子方向 | 代表文献 | 会议/期刊 | 年份 |
|------|--------|----------|-----------|------|
| A-1 | TFM架构 | TabPFN v2 (Hollmann et al.) | NeurIPS | 2024 |
| A-2 | TFM架构 | TabForestPFN (den Breejen et al.) | arXiv | 2024 |
| A-3 | TFM架构 | UniTabE (Yang et al.) | NeurIPS | 2023 |
| A-4 | TFM架构 | TabuLa-8B (van Breugel et al.) | arXiv | 2024 |
| A-5 | TFM架构 | FT-Transformer (Gorishniy et al.) | NeurIPS | 2021 |
| B-1 | 异构对齐 | CARTE (Kim et al.) | ICML | 2024 |
| B-2 | 异构对齐 | GTL (Wen et al.) | KDD | 2024 |
| B-3 | 异构对齐 | Tree vs NN (Grinsztajn et al.) | NeurIPS | 2022 |
| B-4 | 异构对齐 | NN vs GBDT (McElfresh et al.) | NeurIPS | 2023 |
| B-5 | 异构对齐 | TabNet (Arik & Pfister) | AAAI | 2021 |
| C-1 | ICL表格 | TABLET (Gardner et al.) | NeurIPS WS | 2023 |
| C-2 | ICL表格 | AnyPredict (Li et al.) | arXiv | 2023 |
| C-3 | ICL表格 | LIFT (Dinh et al.) | NeurIPS | 2022 |
| C-4 | ICL表格 | SAINT (Somepalli et al.) | arXiv | 2021 |
| D-1 | 决策闭环 | XAI Credit (Lavesson et al.) | DSS | 2023 |
| D-2 | 决策闭环 | ML Credit Risk (Kriebel et al.) | ESWA | 2022 |
| D-3 | 检索增强 | RAG (Lewis et al.) | NeurIPS | 2020 |
| D-4 | 检索增强 | CoT (Wei et al.) | NeurIPS | 2022 |

---

## 🔬 论文蓝图一 | Paper Blueprint I

### HiTA: Heterogeneous-column-aware In-context Tabular Aligner

**目标投稿**: KDD 2025 / AAAI 2025  
**核心贡献**: 解决 $d_A \neq d_B$ 的跨域软对齐问题

#### 核心技术模块
1. **CSE (Column Semantic Embedder)** - 列级语义嵌入（列名 + 数值分布双通道）
2. **CSAN (Cross-Domain Soft Alignment Network)** - 最优传输软对齐
3. **HiTA Encoder** - 异构感知表格Transformer
4. **Meta-Learning Credit Prior** - MAML元学习先验蒸馏

#### 核心公式
$$\min_{\theta} \mathbb{E}_{A,B} \left[ \mathcal{L}_{CE}(f_\theta(T_B; \Pi_{A \to B}(T_A)), y_B) + \lambda \cdot \mathcal{W}_2(P_A, P_B) \right]$$

其中 $\Pi_{A \to B}$ 为最优传输对齐矩阵，$\mathcal{W}_2$ 为Wasserstein距离。

---

## 📈 论文蓝图二 | Paper Blueprint II

### Tabular-RAG: Dynamic Few-Shot Retrieval-Augmented Credit Decision Intelligence

**目标投稿**: MIS Quarterly (MISQ) / ISR / Decision Support Systems  
**核心贡献**: 冷启动信贷决策的结构化表格检索增强框架与管理价值评估

#### 四层系统架构
```
Layer 4: 人机协同反馈闭环 (HACF)
         ↕ 审核反馈
Layer 3: LLM-CoT 推理引擎（风险分析→决策→解释）
         ↑ 检索结果
Layer 2: 动态相似性检索引擎 (DSRE)
         ↑ 查询
Layer 1: 异构表格知识库 (HTKB)
         [源域A历史案例 × 跨域语义向量索引]
```

#### 管理价值三维评估
- 🧠 **认知负荷降低** (NASA-TLX量表)
- 📊 **决策质量提升** (AUC/KS + 信贷损失率经济价值)
- ⚖️ **监管合规性** (GDPR/ECOA合规评分)

---

## 🚀 快速开始 | Quick Start

直接打开 `index.html` 即可在浏览器中查看完整的交互式双语研究报告，支持：
- 🇨🇳 中文 / 🇺🇸 English 切换
- 🌓 暗色/亮色主题切换
- 📑 五个分标签页：研究概览、文献调研、综述正文、论文一蓝图、论文二蓝图

Open `index.html` directly in your browser for the full interactive bilingual research report featuring language toggle, dark mode, and tabbed navigation.

---

## 📖 引用 | Citation

如您使用本研究体系，请引用以下关键文献：

```bibtex
@inproceedings{hollmann2024tabpfnv2,
  title={TabPFN v2: Improved In-Context Learning for Tabular Data},
  author={Hollmann, Noah and M{\"u}ller, Samuel and Purucker, Lennart and others},
  booktitle={NeurIPS},
  year={2024}
}

@inproceedings{kim2024carte,
  title={CARTE: Context-Aware Representation of Table Entries},
  author={Kim, Myung Jun and Grinsztajn, L{\'e}o and Varoquaux, Ga{\"e}l},
  booktitle={ICML},
  year={2024}
}

@inproceedings{yang2023unitabe,
  title={A Universal Pretraining Protocol for Tabular Foundation Model in Data Science},
  author={Yang, Yazheng and Wang, Yuqi and Liu, Guang and others},
  booktitle={NeurIPS},
  year={2023}
}
```

---

## ⚠️ 免责声明 | Disclaimer

本仓库中的"论文蓝图"为学术研究规划，尚未发表。所有文献引用均来自公开发表的学术成果，不包含任何保密数据或专有算法。

---

*Generated by OpenClaw (内网版) · 工蜂 AI × AnyDev*
