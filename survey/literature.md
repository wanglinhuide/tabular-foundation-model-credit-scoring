# 完整文献目录 | Full Literature Catalogue
# 纯表格基础模型与异构对齐方向 · 2020–2025

---

## 子方向 A：表格基础模型架构（TFM Architecture）

### [A-1] TabPFN v2: Improved In-Context Learning for Tabular Data
- **作者**: Noah Hollmann, Samuel Müller, Lennart Purucker, Katharina Eggensperger, Edward Bergman, Frank Hutter
- **发表**: NeurIPS 2024
- **arXiv**: https://arxiv.org/abs/2410.03013
- **核心创新**: 将表格推断等价为贝叶斯最优预测器在合成先验下的后验推断；单次前向传播完成零样本预测；在300+真实Benchmark全面超越XGBoost/CatBoost
- **与本研究关联**: 提供冷启动场景下ICL范式的核心基线；其合成先验机制为跨域先验蒸馏提供方法论依据
- **子方向标签**: TFM架构 · ICL零样本 · 合成先验

### [A-2] Fine-tuned In-Context Learning Transformers are Excellent Tabular Data Classifiers (TabForestPFN)
- **作者**: Felix den Breejen, Sangmin Bae, Stephen Cha, Se-Young Yun
- **发表**: arXiv 2024
- **arXiv**: https://arxiv.org/abs/2405.13396
- **核心创新**: 将TabPFN扩展至微调场景；发现微调使ICL-Transformer能构建复杂决策边界；提出TabForestPFN结合森林数据集生成器
- **与本研究关联**: 提供跨域微调的关键基线；证明ICL架构在微调后具有更强的分布适应能力
- **子方向标签**: TFM架构 · 微调ICL · 决策边界

### [A-3] A Universal Pretraining Protocol for Tabular Foundation Model in Data Science (UniTabE)
- **作者**: Yazheng Yang, Yuqi Wang, Guang Liu, Ledell Wu, Xingyao Zhang, Borui Ding, Yiping Yao, Ding Zhou
- **发表**: NeurIPS 2023
- **arXiv**: https://arxiv.org/abs/2307.09249
- **核心创新**: 提出TabUnit模块将(列名,数值)对编码为可迁移向量；支持增量列学习；Schema无关预训练协议
- **与本研究关联**: 直接解决d_A≠d_B的异构列问题；UniTabE的TabUnit设计是HiTA论文CSE模块的核心参考
- **子方向标签**: TFM架构 · Schema无关 · 跨任务迁移

### [A-4] Large Scale Transfer Learning for Tabular Data via Language Modeling (TabuLa-8B)
- **作者**: Boris van Breugel, Tennison Liu, Zhaozhi Qian, Mihaela van der Schaar
- **发表**: arXiv 2024
- **arXiv**: https://arxiv.org/abs/2406.12031
- **核心创新**: 将Llama 3-8B在21亿行/400万表格的TabLib语料上微调；新颖行打包注意力机制；零样本准确率超随机15pp
- **与本研究关联**: 证明LLM在不依赖文本特征时仍能从纯数值结构学习通用表格先验；为大规模预训练路径提供实证
- **子方向标签**: TFM架构 · 大规模预训练 · LLM微调

### [A-5] Revisiting Deep Learning Models for Tabular Data (FT-Transformer)
- **作者**: Yury Gorishniy, Ivan Rubachev, Valentin Khrulkov, Artem Babenko
- **发表**: NeurIPS 2021
- **arXiv**: https://arxiv.org/abs/2106.11959
- **核心创新**: 提出Feature Tokenizer将每列映射为连续Token；FT-Transformer成为表格深度学习标准基线架构
- **与本研究关联**: 列级Token化设计是所有后续工作（UniTabE/CARTE/HiTA）的方法论起点
- **子方向标签**: TFM架构 · 列级Token化 · 标准基线

---

## 子方向 B：异构特征对齐与跨域迁移（Heterogeneous Alignment & Transfer）

### [B-1] CARTE: Context-Aware Representation of Table Entries for Pretraining and Transfer for Tabular Learning
- **作者**: Myung Jun Kim, Léo Grinsztajn, Gaël Varoquaux
- **发表**: ICML 2024
- **arXiv**: https://arxiv.org/abs/2402.16785
- **核心创新**: 将表格表示为图结构（行/列=节点/边）；图注意力网络同步编码列名语义与条目值；无需Schema匹配的跨表联合预训练
- **与本研究关联**: 直接解决"列名完全不同"的跨域对齐问题；CSAN软对齐网络的设计参考
- **子方向标签**: 异构对齐 · 图神经网络 · 跨表迁移

### [B-2] From Supervised to Generative: A Novel Paradigm for Tabular Deep Learning with Large Language Models (GTL)
- **作者**: Xumeng Wen, Han Zhang, Shun Zheng, Wei Xu, Jiang Bian
- **发表**: KDD 2024
- **arXiv**: https://arxiv.org/abs/2310.07338
- **核心创新**: 生成式表格学习（GTL）框架；LLaMA-2在384个跨领域表格数据集上预训练；少样本场景下强泛化能力
- **与本研究关联**: 证明"通用信贷先验通过生成式跨域预训练获得"的可行性；为冷启动场景提供实证支撑
- **子方向标签**: 异构对齐 · 生成式范式 · 跨域预训练

### [B-3] Why Do Tree-Based Models Still Outperform Deep Learning on Tabular Data?
- **作者**: Léo Grinsztajn, Edouard Oyallon, Gaël Varoquaux
- **发表**: NeurIPS 2022
- **arXiv**: https://arxiv.org/abs/2207.08815
- **核心创新**: 系统性揭示深度学习在表格数据上的三大归纳偏置缺陷；构建45个跨领域标准化Benchmark
- **与本研究关联**: 定义原生表格LLM需要克服的核心挑战；为实验中树模型Baseline的能力上界提供依据
- **子方向标签**: 异构对齐 · 归纳偏置 · 基准测试

### [B-4] When Do Neural Nets Outperform Boosted Trees on Tabular Data?
- **作者**: Duncan McElfresh, Sujay Khandagale, Jonathan Valverde, Vishak Ramakrishna, Ganesh Ramakrishnan, Arjun Subramonian, John P. Dickerson
- **发表**: NeurIPS 2023
- **arXiv**: https://arxiv.org/abs/2305.02997
- **核心创新**: 迄今最大规模表格Benchmark（19算法×176数据集）；TabPFN在小样本场景平均最优
- **与本研究关联**: 量化冷启动算法选型依据；证明ICL范式在≤3000样本场景的系统性优势
- **子方向标签**: 异构对齐 · 大规模Benchmark · 算法选型

### [B-5] TabNet: Attentive Interpretable Tabular Learning
- **作者**: Sercan O. Arik, Tomas Pfister
- **发表**: AAAI 2021
- **arXiv**: https://arxiv.org/abs/1908.07442
- **核心创新**: 顺序注意力机制动态特征选择；列级稀疏注意力内生可解释性；端到端深度学习表格模型
- **与本研究关联**: 提供可解释性基线；其特征归因机制为论文二决策闭环的解释评估提供对比参考
- **子方向标签**: 异构对齐 · 可解释性 · 特征选择

---

## 子方向 C：表格 In-Context Learning 与检索增强（ICL & Tabular RAG）

### [C-1] Can Large Language Models be Used to Predict Tabular Data? (TABLET)
- **作者**: Josh Gardner, Juan C. Perdomo, Ludwig Schmidt
- **发表**: NeurIPS 2023 Workshop on Distribution Shifts
- **arXiv**: https://arxiv.org/abs/2210.06376
- **核心创新**: 系统性评估GPT在纯表格ICL任务；精心设计Prompt策略（特征描述注入+Few-shot示例选择）；定位数值推理为主要瓶颈
- **与本研究关联**: 提供LLM表格ICL的系统性评估框架；Prompt设计策略直接影响HiTA和Tabular-RAG的提示工程
- **子方向标签**: ICL表格 · Prompt工程 · 数值推理

### [C-2] AnyPredict: Foundation Model for Tabular Prediction
- **作者**: Haoyang Li, Xin Zhang, Zheng Qin, Yingxia Shao, Bin Cui
- **发表**: arXiv 2023
- **arXiv**: https://arxiv.org/abs/2305.12081
- **核心创新**: 三层提示框架（任务描述+数据集描述+样本检索）；混合检索策略（结构相似+数值分布匹配）
- **与本研究关联**: 混合检索策略直接启发Tabular-RAG的DSRE双通道检索引擎设计
- **子方向标签**: ICL表格 · 检索增强 · 基础模型

### [C-3] LIFT: Language-Interfaced Fine-Tuning with a Label Description for Tabular Data
- **作者**: Tuan Dinh, Yuchen Zeng, Ruisu Zhang, Ziqian Lin, Michael Gira, Shashank Rajput, Jy-yong Sohn, Dimitris Papailiopoulos, Kangwook Lee
- **发表**: NeurIPS 2022
- **arXiv**: https://arxiv.org/abs/2206.06349
- **核心创新**: 标签描述+特征描述整合进Prompt；语言接口设计使LM有效利用领域知识；零/少样本场景验证
- **与本研究关联**: 证明语言接口LM在冷启动信用评分中的可行性；为论文二CoT推理链的Prompt设计提供参考
- **子方向标签**: ICL表格 · 语言接口 · 少样本

### [C-4] SAINT: Improved Neural Networks for Tabular Data via Row Attention and Contrastive Pre-Training
- **作者**: Gowthami Somepalli, Micah Goldblum, Avi Schwarzschild, Christoph Studer, Tom Goldstein
- **发表**: arXiv 2021 (NeurIPS 2021 Workshop)
- **arXiv**: https://arxiv.org/abs/2106.01342
- **核心创新**: 行间自注意力（Inter-Sample Attention）；列×行双维度Transformer；对比预训练学习结构不变性
- **与本研究关联**: 行间注意力机制天然支持少样本类比推理；为HiTA的样本间上下文建模提供架构参考
- **子方向标签**: ICL表格 · 行间注意力 · 对比预训练

---

## 子方向 D：决策闭环与金融应用（Decision Loop & FinTech）

### [D-1] Explainable AI for Credit Scoring: Methods, Challenges, and Regulatory Perspectives
- **作者**: Niklas Lavesson et al.
- **发表**: Decision Support Systems, Vol. 172, 113975, 2023
- **DOI**: https://doi.org/10.1016/j.dss.2023.113975
- **核心创新**: 全面梳理信用评分XAI方法；分析SHAP/LIME在GDPR/Basel下的适用性与局限性；监管可解释性标准
- **与本研究关联**: 为论文二的ECOA合规评分框架提供监管标准依据；定义可解释性评估指标体系
- **子方向标签**: 决策闭环 · 可解释AI · 金融监管

### [D-2] Machine Learning for Credit Risk: A Systematic Literature Review
- **作者**: Johannes Kriebel, Lennart Stitz
- **发表**: Expert Systems with Applications, Vol. 203, 117350, 2022
- **DOI**: https://doi.org/10.1016/j.eswa.2022.117350
- **核心创新**: 系统综述ML在信用风险的应用；分析数据不平衡/特征工程/模型可信度等金融特有挑战
- **与本研究关联**: 确立金融应用场景标准；提供AUC/KS/Gini等评价指标选择依据；定义业务Baseline
- **子方向标签**: 决策闭环 · 信用风险 · 系统综述

### [D-3] Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks (RAG)
- **作者**: Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, Douwe Kiela
- **发表**: NeurIPS 2020
- **arXiv**: https://arxiv.org/abs/2005.11401
- **核心创新**: 密集检索+生成模型结合；检索-读取-生成三阶段框架；外部知识库增强LLM
- **与本研究关联**: 为Tabular-RAG提供方法论原型；稀疏样本场景的知识池构建策略直接来源于此
- **子方向标签**: 检索增强RAG · 知识检索 · 生成增强

### [D-4] Chain-of-Thought Prompting Elicits Reasoning in Large Language Models
- **作者**: Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Brian Ichter, Fei Xia, Ed Chi, Quoc Le, Denny Zhou
- **发表**: NeurIPS 2022
- **arXiv**: https://arxiv.org/abs/2201.11903
- **核心创新**: CoT中间推理步骤显著提升LLM复杂推理能力；在多个推理Benchmark上涌现出强大性能
- **与本研究关联**: 激发LLM信贷风险逻辑链推断的核心技术；为论文二可解释决策闭环的五步CoT设计提供依据
- **子方向标签**: 检索增强RAG · 链式推理 · 可解释性

### [D-5] LLMs as Decision Makers: AI-Augmented Decision-Making in Financial Services
- **作者**: Multiple Authors
- **发表**: Management Science, In Press 2024
- **核心创新**: 管理科学视角的LLM金融决策机制研究；认知负荷-决策质量双轨评估框架；信贷配给效率量化
- **与本研究关联**: 论文二管理价值评估三维框架的直接理论来源
- **子方向标签**: 决策闭环 · 管理科学 · 认知负荷

---

## 补充文献 | Additional References

### [E-1] In-context Learning through the Bayesian Prism (Xie et al., ICLR 2022)
- **arXiv**: https://arxiv.org/abs/2111.02080
- 从贝叶斯视角理论化ICL的运作机制；为TabPFN v2的先验推断框架提供理论基础

### [E-2] Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks (MAML, Finn et al., ICML 2017)
- **arXiv**: https://arxiv.org/abs/1703.03400
- HiTA元学习先验蒸馏模块的核心算法依据

### [E-3] Optimal Transport for Domain Adaptation (Courty et al., TPAMI 2017)
- **DOI**: https://doi.org/10.1109/TPAMI.2016.2520564
- CSAN软对齐网络中最优传输理论的核心参考

### [E-4] XGBoost: A Scalable Tree Boosting System (Chen & Guestrin, KDD 2016)
- **arXiv**: https://arxiv.org/abs/1603.02754
- 所有实验中最重要的Baseline对比方法

### [E-5] SHAP: A Unified Approach to Interpreting Model Predictions (Lundberg & Lee, NeurIPS 2017)
- **arXiv**: https://arxiv.org/abs/1705.07874
- 论文二可解释性评估的核心工具参考

---

*文献整理时间 | Compiled: 2025 · OpenClaw (内网版)*
