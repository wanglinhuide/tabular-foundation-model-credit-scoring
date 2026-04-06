# 学术综述正文 | Academic Literature Review
# 纯表格基础模型、异构对齐与跨域冷启动信用评分

---

## 中文版（约800字）

学术界对大模型处理纯表格数据的形式化界定已形成基本共识。Gorishniy 等（NeurIPS 2021）通过大规模系统实验指出，一个完备的深度表格模型应当能够克服三大归纳偏置缺陷：对无关特征的不鲁棒性、无法保持数据方向性以及难以学习不规则函数。在此基础上，FT-Transformer 将每列特征映射为连续 Token 向量，建立了"列级 Token 化→Transformer 上下文融合→分类/回归"的原生表格深度学习范式，成为后续所有表格基础模型的方法论起点。Yang 等（NeurIPS 2023，UniTabE）进一步将其抽象为"任意 Schema 无关预训练"框架：将每个基本表格元素（列名-数值对）封装为可迁移的 TabUnit 模块，经统一 Transformer 编码后形成与具体列结构解耦的潜在表示，从而支持增量列学习与跨数据集迁移，为解决 $d_A \neq d_B$ 的跨域异构问题奠定了结构性基础。

Hollmann 等（NeurIPS 2024，TabPFN v2）则将整个表格推断过程等价为贝叶斯最优预测器在合成先验下的后验推断：通过在数百万合成数据集上离线拟合先验分布，TabPFN v2 在测试阶段以单次前向传播即可完成"元学习式"预测，无需任何梯度更新。McElfresh 等（NeurIPS 2023）通过对比 19 种算法跨 176 个数据集的最大规模表格 Benchmark 测试，以实证方式验证了 TabPFN 在小样本场景（≤3000 条训练数据）下全面领先所有对手的事实，直接为信用评分冷启动场景中的算法选型提供了量化依据。

在异构特征对齐方向，Kim 等（ICML 2024，CARTE）针对跨表迁移中的"无结构对应"痛点，提出将关系型表格表示为图结构，利用图注意力网络同步编码列名语义与条目值，从而无需任何预设的 Schema 匹配即可实现异构表格间的联合预训练——这直接对标了源域 A 与目标域 B"列名完全不同"的核心工程挑战。Wen 等（KDD 2024，GTL）则以生成式范式为切入点，将 LLaMA-2 在 384 个真实表格数据集上进行跨领域预训练，赋予其捕捉数值序列依赖性与跨域统计关系的能力，并在有限数据场景下展现出显著的少样本泛化优势，从实证层面论证了"通过生成式预训练构建跨域通用信贷先验"的可行性。

在大模型表格 ICL 方向，Gardner 等（NeurIPS 2023 Workshop，TABLET）系统性评估了 GPT 系列模型在纯表格预测任务上的 ICL 能力，发现通过精心设计的特征描述注入与少样本示例选择策略，LLM 可在无文本特征的条件下实现有效的表格分类，同时将数值推理能力的不足界定为当前 LLM 表格处理的核心瓶颈。van Breugel 等（2024，TabuLa-8B）进一步将 Llama 3-8B 在包含 21 亿行、400 万张异构表格的 TabLib 语料上进行微调，在 329 个测试集上实现了超越随机猜测 15 个百分点的零样本准确率，从大规模实验角度证明了语言模型在不依赖任何文本特征的条件下仍能从纯数值结构中习得通用表格先验。

在决策闭环与金融应用方向，Lewis 等（NeurIPS 2020）提出的 RAG 框架以"检索-读取-生成"三阶段流水线为表格样本检索增强提供了方法论原型；Wei 等（NeurIPS 2022）发现的 CoT 涌现能力表明 LLM 可通过中间推理步骤展示逻辑链条，为信贷决策的规制可解释性提供了内生机制。Lavesson 等（DSS 2023）系统梳理了信用评分领域的可解释 AI 方法，明确指出未来信用评分模型必须提供面向监管的逻辑一致性证明，为系统框架的合规设计提供了规范性标准。

综合而言，以 UniTabE、CARTE、GTL 为代表的"异构对齐-联合预训练-跨域微调"序列化逻辑，与 TabPFN v2、TabuLa-8B 所代表的"大规模合成/真实先验拟合-零样本 ICL 推断"路径，共同构成了当前表格基础模型领域的两大主流技术范式。前者的核心优势在于能够通过显式的结构对齐机制跨越异构 Schema 边界；后者的核心优势在于无需任何目标域梯度更新即可完成高质量冷启动预测。本文所提出的两篇论文分别在这两条路径上寻找交叉创新空间：论文一（HiTA）将最优传输引入隐空间软对齐，打通了"异构投影-元学习先验"的贯通路径；论文二（Tabular-RAG）则将检索增强与 CoT 推理内嵌于金融决策系统中，构建了"检索增强-推理生成-人机协同-监管合规"的完整决策闭环。二者相互呼应，共同构成面向信用风控冷启动挑战的完整解决方案体系。

---

## English Version (~800 words)

The academic community has reached a basic consensus on formalizing LLM-based processing of pure tabular data. Gorishniy et al. (NeurIPS 2021) identified through large-scale systematic experiments that a complete deep tabular model must overcome three fundamental inductive bias flaws: non-robustness to uninformative features, failure to preserve data orientation, and difficulty learning irregular functions. Building on this, FT-Transformer established the paradigm of "column-level tokenization → Transformer contextual fusion → prediction," creating the canonical native tabular deep learning baseline. Yang et al. (NeurIPS 2023, UniTabE) further abstracted this into a "schema-agnostic universal pretraining" framework: encapsulating each (column-name, value) pair into transferable TabUnit modules, forming column-structure-decoupled latent representations that support incremental column learning and cross-dataset transfer — providing a structural foundation for resolving d_A ≠ d_B cross-domain heterogeneity.

Hollmann et al. (NeurIPS 2024, TabPFN v2) equated the entire tabular inference process with Bayesian-optimal posterior inference under a synthetic prior: by offline fitting the prior distribution over millions of synthetic datasets, TabPFN v2 accomplishes "meta-learning style" prediction via a single forward pass at test time — no gradient updates required. McElfresh et al. (NeurIPS 2023) empirically validated, through the largest tabular benchmark (19 algorithms × 176 datasets), that TabPFN comprehensively outperforms all competitors in small-data settings (≤3000 training samples), directly quantifying the algorithm selection rationale for cold-start credit scoring.

In heterogeneous feature alignment, Kim et al. (ICML 2024, CARTE) tackled the "no structural correspondence" challenge in cross-table transfer by representing relational tables as graphs, using graph-attentional networks to simultaneously encode column-name semantics and entry values — enabling joint pretraining across heterogeneous tables without any predefined schema matching, directly targeting the "completely different column names" engineering challenge between source domain A and target domain B. Wen et al. (KDD 2024, GTL) pre-trained LLaMA-2 across 384 real tabular datasets in a generative paradigm, capturing numerical sequence dependencies and cross-domain statistical relationships. Their remarkable few-shot generalization in limited-data scenarios empirically validates the feasibility of building universal credit priors through generative cross-domain pretraining.

In the LLM tabular ICL direction, Gardner et al. (NeurIPS 2023 Workshop, TABLET) systematically evaluated GPT models' ICL capabilities on pure tabular prediction, finding that carefully designed feature description injection and few-shot example selection enable effective tabular classification without text features, while identifying numerical reasoning as the primary bottleneck. van Breugel et al. (2024, TabuLa-8B) fine-tuned Llama 3-8B on 2.1B rows from 4M heterogeneous tables, achieving zero-shot accuracy 15pp above random on 329 test datasets — demonstrating that LLMs can learn universal tabular priors from raw numerical structure without any text features.

In the decision loop and FinTech applications direction, the RAG framework proposed by Lewis et al. (NeurIPS 2020) provides the methodological prototype for tabular sample retrieval augmentation via its "retrieve-read-generate" three-stage pipeline. The CoT emergence capability discovered by Wei et al. (NeurIPS 2022) demonstrates that LLMs can surface logical reasoning chains through intermediate steps — providing intrinsic explainability mechanisms for regulatory credit decision interpretation. Lavesson et al. (DSS 2023) systematically mapped explainable AI methods in credit scoring, explicitly establishing that future credit scoring models must provide regulatory logical consistency proofs — defining normative standards for system compliance design.

Collectively, the "heterogeneous alignment → joint pretraining → cross-domain fine-tuning" sequential logic represented by UniTabE, CARTE, and GTL, and the "large-scale synthetic/real prior fitting → zero-shot ICL inference" pathway represented by TabPFN v2 and TabuLa-8B, constitute the two dominant paradigms in tabular foundation model research. The former excels at crossing heterogeneous schema boundaries through explicit structural alignment; the latter excels at high-quality cold-start prediction without any target-domain gradient updates. The two proposed papers seek cross-innovation opportunities at the intersection of these pathways: Paper I (HiTA) introduces optimal transport into latent-space soft alignment, establishing a through-path from "heterogeneous projection to meta-learning prior"; Paper II (Tabular-RAG) embeds retrieval augmentation and CoT reasoning into financial decision systems, constructing a complete decision loop of "retrieval augmentation → reasoning generation → human-AI collaboration → regulatory compliance." Together, they form a comprehensive solution framework for the cold-start challenge in credit risk control.

---

*综述编写时间 | Compiled: 2025 · For KDD/AAAI (Paper I) + MISQ/ISR (Paper II)*
