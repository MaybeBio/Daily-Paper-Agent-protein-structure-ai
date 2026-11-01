## 01 基本信息
- **标题**：Building from the ground up: augmentation strategies to improve protein language model performance on protein sets
- **作者**：Emily Stump; Hayden Dennison; Pietro Strobbia; George Stan; Ruxandra I. Dima（¶ 标注 Stump 与 Dennison 为共同第一作者）
- **单位**：未在提供材料中明确列出（仅致谢提及 NSF/NIH 资助与 ACCESS 计算资源分配）
- **期刊/预印本平台**：bioRxiv
- **年份**：2026-10-25（预印本日期）
- **论文类型**：方法学/实证研究（数据集消融 + 主动学习增强实验）
- **领域**：蛋白质语言模型（pLM）、蛋白质-蛋白质复合物接触图预测、数据增强、主动学习
- **关键词**：未提供（原文无关键词列表）
- **DOI/arXiv 号**：10.64898/2026.10.20.760553
- **代码**：https://github.com/DimaUClab/protein-complex-ml
- **数据**：Zenodo 10.5281/zenodo.23453970；预测接触图（>1.5 TB）需向作者索取
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI」中的**数据效率与数据增强**分支——用 pLM（ESM-2、AminoBERT、ProtBERT）做残基-残基接触图预测，研究训练集**规模 vs 分布范围（size vs scope）**的权衡，并用生成式 pLM（ESM-3）做主动学习式数据增强。与结构预测（接触图是结构预测的中间表征）、构象/复合物生成（ESM-3 生成复合物序列）直接相关，但**不涉及 MD/对接/物理模拟**。

## 02 一句话总结
在 DIPS-Plus 蛋白质-蛋白质复合物数据集上，通过按界面面积或接触残基对数做「均匀消融」与「定向（窄分布）消融」并训练三种 BERT 式 pLM 预测接触图，发现缩小数据分布范围可在仅保留 20% 数据时维持甚至提升训练/验证 MCC（但测试 MCC 下降、过拟合），且用 ESM-3 基于模型分歧（CKA）选种生成复合物做增强，仅在初始集规模较大（50%/80%）时带来小幅一致的 MCC 提升，在 20% 极端消融下增强反而有害。

## 03 研究问题
- **具体问题**：在生物/化学领域标注数据稀缺的约束下，(1) 训练集**规模**与**分布范围（scope）**如何分别影响 pLM 的学习与泛化？(2) 能否用基于不确定性的主动学习（AL）+ 生成式 pLM（ESM-3）合成数据来补偿被移除的数据？
- **为何重要**：化学/生物数据生成成本高（需实验材料与人力），而现代模型参数量达百万至十亿级，数据需求与可获得性之间存在结构性矛盾；理解「小数据下如何构建数据集」对 pLM 落地至关重要。
- **现有方法为何不足**：SMOTE/ADASYN 依赖最近邻插值，难以处理**变长样本**（如蛋白质复合物）；AL 在化学 ML 中多用于小分子/寡肽，尚未系统检验 pLM 场景；LLM 合成数据在 NLP 中有效，但蛋白质「语言」由随机进化压力驱动，与人类文本语料不同。
- **精确研究问题**：Can uncertainty-based active learning with generative pLMs produce useful synthetic protein complexes that improve contact-map prediction, and how does this depend on the size and scope of the initial training set?

## 04 背景与发展脉络
**注：以下脉络为「仅本文框架」梳理，未做外部独立核验。**
- **阶段 1：数据稀缺与 AL**。AL 是 model-agnostic 方法，假设存在有限标注预算的 oracle，优先标注模型低置信度样本。代表：Smith & Roitberg 用 MLIP 集成分歧选分子训练可迁移势；An et al. 结合遗传算法与 AL 研究生物分子凝聚体。
- **阶段 2：自适应采样（adaptive sampling）**。MD 采样不足时，先跑随机轨迹，再定位欠采样区域构造新轨迹种子；Li et al. 用 MLIP 集成预测标准差排序构象做量子计算并加入训练集。本文将其类比为 AL 的迭代扩集。
- **阶段 3：过采样**。SMOTE、ADASYN 通过最近邻插值平衡类别；局限是变长样本不适用、ADASYN 不支持纯类别数据。
- **阶段 4：生成式模型作为数据增强器**。AlphaFold、ESM-3 在进化记录上训练，可模仿天然蛋白结构/序列分布，甚至充当 oracle；LLM 作为通用数据增强器（Li et al. 发现小原始集 + 合成数据有一致提升，但纯合成不如纯原始）。
- **本文主张的位置**：把 AL 从「小分子/寡肽」推进到「蛋白质复合物接触图预测」，用 CKA 度量模型分歧选种，用 ESM-3 生成新复合物，并系统扫描数据集 size × scope 的二维条件。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 化学/生物标注数据稀缺 | 无法像 NLP 那样利用互联网级语料 | 数据生成需实验室材料与熟练人力，成本高 | Introduction 引文 3、4 |
| 大模型在小数据上失效 | ProtBERT（420M）训练 MCC 难超 0.2，而 ESM-2（8M）/AminoBERT（87M）可达 ~0.5 | 作者推断 DIPS-Plus 对该规模模型太小 | Results 图 4 及正文 |
| 过采样方法不适用于变长样本 | SMOTE/ADASYN 依赖最近邻插值 | 蛋白质复合物样本尺寸可变，插值困难 | Introduction |
| 合成数据可能偏离目标分布 | ESM-3 生成复合物偏向其自身训练分布中心，而非 DIPS-Plus 或消融后分布 | 作者推断 ESM-3 在全部已知结构上训练，DIPS-Plus 是其子集；微调使其把「重建已有蛋白」当作通用标准 | Results 图 9、图 10；引 Hou et al. 39 |
| 增强在极小数据集上有害 | 20% 消融增强后 MCC 不升反降（targeted 20% 甚至下降） | 作者推断数据太少时模型对不确定性的估计不可靠，选种误导 | Results 图 11；Conclusions |
| 定向消融严重过拟合 | 训练/验证 MCC 可超全量数据集，但测试 MCC 显著低 | 缩小分布方差、提高偏差，模型只学到窄空间 | Results 图 4、图 5 |

## 06 核心思想
1. **表面方法**：用双塔 BERT 编码器 + 逐位置 MLP 预测复合物接触图；对 DIPS-Plus 做两种消融（uniform 保分布 / targeted 窄分布）× 三种保留比例（20/50/80%）；用 AminoBERT 与 ESM-2 的 CKA 分歧挑出「难例」，掩码 ~20% 序列后用 ESM-3（pTM 引导、温度 0.3、每步解掩 3 token）生成新复合物，加入训练集再训练。
2. **核心洞察**：数据集的**分布范围（scope）**与**规模（size）**是两个可独立调节的轴；当只要求 in-distribution 泛化时，缩小 scope 可换取一个数量级的规模缩减；但一旦要求 out-of-distribution 泛化，窄分布反而有害。增强的有效性存在**下界**：初始集太小则不确定性估计不可靠，合成数据有害。
3. **可能的普适教训 [Analysis]**：在数据稀缺的科学领域，「先建一个窄而密的可信核心集，再向外扩展」可能优于「在全空间均匀稀疏采样」；生成式模型的增强能力受其自身训练分布偏置限制，需刻意设计 prompt 才能越出预训练分布。

## 07 方法总览
- **输入**：复合物两条链的氨基酸序列（忽略 DIPS-Plus 的残基/原子级特征）。
- **输出**：L₁ × L₂ 的残基-残基接触图（Cα-Cα ≤ 6 Å 定义为接触），逐位置二分类概率，阈值 0.5 二值化。
- **模块**：① 双塔预训练 BERT 编码器（ESM-2 8M / AminoBERT 87M / ProtBERT 420M）；② 拼接数组 M_ij = concat(emb_i, emb_j)，尺寸 L₁×L₂×2D；③ 逐位置 MLP（单 sigmoid 输出）。
- **训练**：BCE 损失 + position weight（应对接触图稀疏）；MCC 评估；Optuna 做 HPO（架构超参仅作用于 MLP），HPO 在全量训练集上做一次，最优参数复用于所有消融试验。
- **工具**：Python（Pandas/NumPy/SciPy/scikit-learn）、PyTorch、Optuna、Hugging Face（ESM-2/ProtBERT 权重）、AminoBERT GitHub、ESM-3（生成）、ESM-C 6B（隐空间嵌入）。
- **反馈回路**：训练 → 计算验证集 CKA 分歧 → 取最低 20 百分位复合物 → 掩码 → ESM-3 生成 → 加入训练集 → 重训。
- **假设**：界面面积（或接触残基对数）可作为界面复杂度的代理；CKA 分歧可标识「数据缺失区域」；ESM-3 生成物质量足够（pTM > 0.2）可作训练数据。
- **文字流程**：DIPS-Plus → 去重 → 消融（uniform/targeted × 20/50/80%）→ 训练 pLM 接触图预测器 → 验证集 CKA 分歧排序 → 取 bottom 20% 作种子 → 掩码 ~20% → ESM-3 引导生成 → 5 候选/种子选 1 → 加入训练集 → 重训并比较 MCC。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 双塔 BERT 编码器 | 提取两条链的残基级上下文嵌入 | 利用预训练 pLM 的进化知识 | 序列 → L_k × D 嵌入 | Methods「Models」节 | 无预训练则退化为从头训练，预期性能大幅下降（未实测） |
| 逐位置 MLP | 将残基对嵌入映射为接触概率 | 建模跨链残基对交互 | 2D 向量 → 标量概率 | Methods「Models」节 | 未做消融（预期无法输出接触图） |
| Position weight BCE | 缓解接触图类别不平衡 | 接触图稀疏 | 损失加权 | Methods「Models」节 | 未做消融（预期少数类被忽略） |
| 消融方案（uniform/targeted） | 控制数据集 size 与 scope | 分离两个变量 | 全量集 → 子集 | Results 图 4、图 5 | 实测：targeted 提升 train/val MCC 但降 test MCC |
| CKA 分歧度量 | 量化两模型预测一致性 | 作为不确定性/难例代理 | 两张接触图 → [0,1] 分数 | Methods「Measuring the similarity of contact maps」；图 S1 对比四种度量 | 若换用其他度量，作者称 CKA 在 train/val/test 分布重叠最小（图 S1） |
| ESM-3 生成 | 合成新复合物 | 无需实验即可扩集 | 掩码序列 + SASA/二级结构 track → 新序列/结构 | Methods「Generating novel protein complexes by unmasking」；图 1、图 3 | 实测：增强效果依赖初始集规模（图 11） |
| ESM-C 6B 嵌入 | 隐空间距离分析 | 检验生成物是否靠近被移除样本 | 复合物 → 嵌入向量 | Methods「Measuring distances...」；图 8、图 9 | 未做消融 |

**实测消融效应 vs 预期效应**：消融方案与增强的效应为**实测**（图 4、5、11）；编码器/MLP/position weight 的移除影响为**预期**（文中未做对应消融）。

## 09 关键公式符号
1. **CKA 分数（Eq. 1）**：CKA(A_i, E_i) = ⟨K_A, K_E⟩_F / (‖K_A‖_F ‖K_E‖_F)，其中 K 为线性核 K = CΩ_iΩ_iᵀC，C 为按列均值中心化矩阵，Ω_i = {A_i, E_i}，1 为全 1 矩阵。**用途**：度量 AminoBERT 与 ESM-2 对同一复合物预测的一致性；**直觉**：0 = 无对齐，1 = 完全相同；**来源**：Methods「Measuring the similarity of contact maps」。
2. **pTM 分数（Eq. 2）**：pTM = (1/L_N) Σ_i 1/(1 + (d_i/d_0)²)，其中 L_N 为生成/天然结构残基数，L_T 为与模板对齐的残基数，d_i 为对齐残基间距离（Å），d_0 为归一化常数（Å）。**用途**：引导 ESM-3 生成高质量结构；**直觉**：<0.2 表示与任何模板匹配差（随机两结构平均 0.17）；**来源**：Methods「Generating novel protein complexes by unmasking」。
3. **余弦距离**：distance(v₁, v₂) = 1 − cos(v₁, v₂)。**用途**：在 ESM-C 隐空间度量复合物间距离；**来源**：Methods「Measuring distances between protein complexes in latent space」。

## 10 实验设计与证据链
- **数据集**：DIPS-Plus（>40,000 复合物），目标为 Cα-Cα ≤ 6 Å 的残基接触图；使用作者提供的 train/val 划分，额外去除跨 split 重复（序列与接触图均重复才算重复），从训练集删除。
- **消融规模**：20%/50%/80%（extensive/moderate/limited）；每种规模 × 两种风格（uniform/targeted）× 5 次独立消融 = 30 个子集（界面面积），另 30 个（接触残基对数）。
- **测试集**：从验证集随机留出一小部分作为固定 unseen test set，不做任何消融。
- **指标**：MCC（逐位置二分类后全图平均）；CKA；余弦距离；JS 散度。
- **基线**：全量 DIPS-Plus 训练；未增强的消融集。
- **预算/骨干**：ESM-2 8M、AminoBERT 87M、ProtBERT 420M；ESM-3 生成；ESM-C 6B 嵌入；ACCESS 计算资源（BIO210094、MCB170020）。
- **oracle 输入**：AL 中 ESM-3 充当生成式 oracle；实验中已知全量 DIPS-Plus 与被移除样本（真实场景不可得）。
- **评测协议**：HPO 在全量训练集上做一次，最优超参复用于所有消融试验。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 全量 vs 消融训练 | 数据 size/scope 如何影响 MCC | ESM-2/AminoBERT/ProtBERT × uniform/targeted × 20/50/80% | ProtBERT 训练 MCC <0.2；ESM-2/AminoBERT 全量 val/test ~0.5；targeted train/val 更高但 test 更低 | 分布比规模更重要；大模型在小数据上失效 | 不能推广到其他数据集/模型族 | 图 4、图 S3 |
| CKA 分布分析 | 分歧是否反映数据缺失 | train/val/test 的 CKA 分布 | targeted 下 train/val CKA 更接近 1，test 相反；消融越轻分布越趋同 | 分歧与分布覆盖相关 | 不能证明 CKA 是唯一/最优不确定性度量 | 图 5、S4–S6 |
| 相似/相异复合物表征 | 分歧复合物的界面面积特征 | 高/低 CKA 复合物的界面面积密度 | 全范围消融中相异复合物落在 DIPS-Plus 众数之间/长尾；窄范围消融中落在采样区间两端 | 分歧由底层分布驱动 | 不能排除其他界面特征的作用 | 图 6、图 7、S7、S8 |
| 隐空间距离 | 相异复合物是否更靠近被移除样本 | 相异 vs 相似复合物到被移除复合物的余弦距离 | 相异分布中位数 0.195 < 相似 0.320 < 全量 0.212 | 低 CKA 可定位数据缺失区域 | 不能证明生成物也落在该区域 | 图 8、S10 |
| 生成物分布 | 生成物是否匹配目标分布 | 生成 vs 原始界面面积分布、JS 散度 | 生成物偏向 ESM-3 训练分布中心；extensive 消融下 JS 大，moderate/limited 下显著缩小；生成物不占据被移除样本的隐空间区域 | 生成模型有自身分布偏置 | 不能说明偏置不可通过 prompt 缓解 | 图 9、图 10、S9 |
| 增强后重训（10% 子采样） | 合成数据能否提升 MCC | 800 元素 ± 166 生成物 | targeted 50%/80% 提升；uniform 仅 80% 提升；20% 不提升甚至下降 | 增强存在最小数据量下界 | 不能推广到其他 AL 协议 | 图 11、S11 |

## 11 结论正确解读
- **任务范围**：仅接触图预测（非全结构预测、非对接、非 MD）；仅 DIPS-Plus 一个数据集；仅三种 pLM，其中仅两种进入 AL 流程。
- **oracle/真值输入**：实验中已知全量 DIPS-Plus 及被移除样本，真实场景不可得；ESM-3 作为生成 oracle 有其自身偏置。
- **端到端状态**：增强实验在 10% 子采样（800 元素）上进行，MCC 尺度显著低于真实 20/50/80% 消融，属小规模验证而非端到端生产流程。
- **算力成本**：未量化报告；依赖 ACCESS 分配。
- **历史数据依赖**：DIPS-Plus 偏向结构解析良好的稳定复合物，不覆盖全部复合物多样性。
- **模型依赖**：结论依赖 ESM-2/AminoBERT/ESM-3/ESM-C 的具体版本与训练数据。
- **最难情形**：extensive（20%）消融下增强有害；targeted 消融严重过拟合，test MCC 低。
- **群体/领域边界**：作者称结论「likely applicable beyond protein sets to wide varieties of LLMs and datasets」，但这是**推测**，未在本文验证。
- **不确定性**：AminoBERT 在 uniform 消融上偶发训练失败（换初始化后成功）；生成过程随机（5 候选选 1）。
- **有边界的复述**：在 DIPS-Plus 接触图预测任务上，缩小训练分布范围可在 in-distribution 场景下以 20% 数据达到甚至超过全量训练/验证 MCC，但损害 out-of-distribution 泛化；ESM-3 增强在初始集 ≥50% 时带来小幅一致提升，在 20% 时无效或有害。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 仅一个数据集、三种 pLM | 仅两种能 finetune 到可用于 AL | 在其他数据集、问题类型、AL 协议上做更多研究 | Limitations and Future Directions |
| DIPS-Plus 覆盖不全 | 主要含结构解析良好的稳定复合物 | 同上 | Limitations and Future Directions |
| AL 协议较简单 | 存在更复杂的 AL 协议，本文无法对其低数据表现下结论 | 同上 | Limitations and Future Directions |
| 生成模型有内置偏置 | 需额外小心才能成功使用 | 同上 | Limitations and Future Directions |

**作者提及的相关约束（非正式局限）**：预测接触图总量 >1.5 TB，需向作者索取；增强实验因规模问题改用 10% 子采样。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 增强实验在 10% 子采样（800 元素）上做，MCC 尺度远低于主实验 | 增强结论可能只在极小数据 regime 成立，与主实验的 20/50/80% 不可直接比较 | 影响「增强何时有效」结论的可迁移性 | 在真实 20/50/80% 消融集上做增强（需更大生成量） | 图 11 与图 4 对比 |
| 生成物不落在被移除样本的隐空间区域 | 增强提升可能来自正则化/多样性而非「补回缺失数据」 | 若如此，AL 选种机制的必要性被削弱 | 用随机种子生成等量复合物做对照增强 | 图 9 |
| 界面面积与接触残基对数两种消融变量结论不一致 | 作者归因于 SASA track 偏置，但未做无 SASA track 的对照 | 决定增强协议是否依赖特定输入 track | 关闭 SASA track 重跑 residue-count 消融增强 | 图 S11 与图 11 |
| CKA 被选为分歧度量，但仅与三种替代度量比较（图 S1） | 其他不确定性度量（如 ensemble 方差、MC dropout）可能更优 | 影响 AL 选种质量 | 用多种不确定性度量并行做 AL 对比 | Methods；图 S1 |
| targeted 消融 train/val MCC 超全量但 test 低 | 可能是 HPO 在全量集上做、超参不匹配窄分布所致 | 影响「窄分布更优」的因果解释 | 对每个消融集单独做 HPO | Methods「Models」节 |
| 5 候选/种子选 1 的筛选标准未明确说明 | 选择可能引入乐观偏置 | 影响增强效果的可靠性 | 报告筛选标准并做随机选择对照 | Methods「Changes in Model Performance...」 |
| 作者称结论可推广到「wide varieties of LLMs and datasets」 | 仅在蛋白质接触图任务验证 | 过度推广风险 | 在 NLP/小分子任务上复现 | Conclusions |

## 14 学到什么
**Agent 提炼的知识候选**
- **可迁移概念：size vs scope 二维数据设计**。在蛋白质结构计算中（如构象采样训练集、对接打分训练集），可显式区分「数据量」与「分布范围」，先建窄而密的核心集再扩展，而非在全构象空间均匀稀疏采样。
- **可迁移方法：CKA 作为模型分歧/不确定性代理**。可用于 MD 自适应采样中「哪些构象区域采样不足」的判定，替代或补充 ensemble 标准差。
- **可迁移方法：生成式 pLM 作为 oracle 的 AL 回路**。ESM-3 掩码-解掩码 + pTM 引导生成，可迁移到「生成新构象/新复合物加入训练集」的主动学习流程；注意需 ≥50% 初始数据量。
- **可迁移实验设计：消融 × 分布 × 多模型 × 多随机种子**。30 个子集 × 5 次独立消融的设计，可作为结构计算中数据效率研究的模板。
- **可迁移警示：生成模型的分布偏置**。ESM-3 生成物偏向其预训练分布中心，提示在构象生成/结构设计中，生成样本可能无法覆盖目标分布尾部，需刻意设计 prompt 或引导。
- **可迁移公式**：CKA（Eq. 1）与 pTM（Eq. 2）可直接用于结构计算中的相似性度量与生成质量筛选。

## 15 与已有知识连接
- **相似**：Smith & Roitberg 的 MLIP 集成分歧选样（AL + 势函数）；Li et al. 的 MLIP 集成标准差排序构象做量子计算（自适应采样 + ML）；An et al. 的遗传算法 + AL 研究生物分子凝聚体。
- **组合**：AL + 生成式 pLM（ESM-3）的组合，将「不确定性选种」与「生成式扩集」串联，类似 LLM 作为通用数据增强器的思路。
- **冲突**：Li et al. 发现纯原始数据优于原始+合成混合，但小原始集 + 合成有一致提升——本文在蛋白质复合物上复现了「小集增强有效」的边界条件（≥50%）。
- **可迁移领域**：MD 自适应采样、分子对接训练集构建、构象生成模型的数据效率评估、结构/序列设计中的生成模型偏置研究。
- **候选方向（未核验）**：将 CKA 分歧用于 MD 轨迹的构象选择；用 ESM-3 生成复合物做对接训练集增强。

## 16 研究想法
**Agent 生成的研究候选**

1. **名称**：CKA-guided adaptive sampling for MD conformational ensembles
   - **来源局限**：本文 CKA 仅用于接触图预测的 AL 选种，未用于 MD 构象采样。
   - **核心假设**：两个独立训练的 pLM/MLIP 对同一构象的 CKA 分歧可标识 MD 采样不足的区域。
   - **相对本文增量**：把 CKA 从「复合物选种」迁移到「构象选种」，与自适应采样结合。
   - **初步方法**：训练两个 MLIP 集成，对 MD 轨迹构象计算 CKA，取低 CKA 构象做量子/高精度计算并加入训练集。
   - **验证方式**：对比随机采样与 CKA 选样的自由能面收敛速度。
   - **失败模式**：CKA 在构象空间区分度不足；MLIP 分歧与真实采样不足不相关。
   - **创新状态**：unverified

2. **名称**：Debiasing generative pLM augmentation via distribution-aware prompting
   - **来源局限**：作者发现 ESM-3 生成物偏向其预训练分布中心，且需刻意 prompt 才能越出。
   - **核心假设**：在生成时显式加入目标分布（如界面面积分位数）作为引导 track，可减小生成物与目标分布的 JS 散度。
   - **相对本文增量**：本文仅用 SASA/二级结构 track，未做分布引导。
   - **初步方法**：以界面面积分位数为条件，用 classifier guidance 或 rejection sampling 筛选生成物。
   - **验证方式**：测量生成物与目标分布的 JS 散度及增强后 test MCC。
   - **失败模式**：引导过强导致生成物质量下降（pTM < 0.2）。
   - **创新状态**：partially checked（作者已指出偏置存在）

3. **名称**：Minimum-data threshold for generative augmentation across structural tasks
   - **来源局限**：本文发现 20% 消融下增强有害，但仅在一个数据集/任务上。
   - **核心假设**：存在与任务复杂度、模型规模相关的增强最小数据量阈值，可用「模型在初始集上的 MCC」预测。
   - **相对本文增量**：把「下界」从定性观察变为可预测的定量关系。
   - **初步方法**：在多个结构任务（接触图、二级结构、对接打分）上扫描初始集规模，拟合阈值与初始 MCC 的关系。
   - **验证方式**：留出任务验证预测的阈值。
   - **失败模式**：阈值高度任务依赖，无法统一。
   - **创新状态**：unverified

4. **名称**：Ensemble-variance vs CKA as AL acquisition functions for protein complexes
   - **来源局限**：本文仅用 CKA，未与其他不确定性度量系统对比。
   - **核心假设**：在 pLM 场景下，CKA 与 ensemble 方差选种效果不同，且最优度量依赖消融风格。
   - **相对本文增量**：直接对比 acquisition function。
   - **初步方法**：同一 AL 回路下分别用 CKA、ensemble 方差、MC dropout 选种，比较增强后 MCC。
   - **验证方式**：多随机种子统计检验。
   - **失败模式**：差异不显著，度量选择无关紧要。
   - **创新状态**：unverified