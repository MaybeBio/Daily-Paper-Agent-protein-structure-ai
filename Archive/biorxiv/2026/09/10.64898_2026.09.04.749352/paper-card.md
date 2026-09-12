## 01 基本信息
- **标题**: AtlasFold: Protein structure prediction with metagenomic-scale language models
- **作者与单位**: Seonghwan Seo; Hyeongwoo Kim; Seokhyun Moon; Woo Youn Kim; Team KAIST (韩国科学技术院)
- **期刊/预印本平台**: bioRxiv
- **年份**: 2026
- **论文类型**: 方法学论文 (预印本)
- **领域**: 蛋白质结构预测 × 蛋白质语言模型 (PLM)
- **关键词**: 蛋白质语言模型, 蛋白质结构预测, 蛋白质复合物预测, 宏基因组, 扩散模型
- **DOI/arXiv 号**: 10.64898/2026.09.04.749352
- **代码**: https://github.com/SeonghwanSeo/atlasfold
- **数据**: 训练代码、数据、阶段检查点和模型权重以 MIT 许可证发布
- **阅读日期**: 2024-05-21
- **该文在「蛋白质结构相关计算研究 × AI 方法/物理模拟」方向中的位置**: 本文属于「蛋白质结构预测 × 深度学习」方向，具体是「基于蛋白质语言模型 (PLM) 的单序列结构预测」子方向。它通过训练一个大规模 PLM (AtlasLM) 来替代传统的多序列比对 (MSA)，并构建了一个蛋白质特异性的折叠主干 (folding trunk) 和扩散头 (diffusion head) 来预测全原子结构。该工作与 ESMFold、ESMFold2 等模型同属一个技术路线，但强调了模型的开放性、宏基因组数据的使用以及针对蛋白质单体的架构优化。

## 02 一句话总结
本文提出 Atlas 模型家族，通过在大规模宏基因组序列上预训练 3B 参数蛋白质语言模型 AtlasLM，并构建蛋白质特异性折叠架构 AtlasFold，实现了无需 MSA 的、在 PLM 基方法中达到 SOTA 的单体结构预测，并可通过微调 (AtlasFold-M) 实现与 AlphaFold3 相当的抗体-抗原复合物预测性能。

## 03 研究问题
- **具体问题**: 如何利用蛋白质语言模型 (PLM) 从单一序列中直接、高效、准确地预测蛋白质的单体结构和复合物结构，以替代依赖计算成本高昂的多序列比对 (MSA) 的方法？
- **为什么重要**: MSA 搜索是传统结构预测方法 (如 AlphaFold2) 的瓶颈，耗时且对孤儿序列 (orphan sequences) 效果差。PLM 基方法有望实现更快速、更通用的单序列结构预测。
- **现有方法为何不足**: 现有 PLM 基方法 (如 ESMFold) 在精度上仍落后于 MSA 基方法 (如 AlphaFold2)，且部分模型 (如 ESMFold2) 未完全开源。此外，PLM 基方法在复合物预测上的表现仍有提升空间。
- **精确的「Can ... ?」研究问题**: Can a protein language model trained on metagenomic-scale data, combined with a protein-specific folding architecture, achieve state-of-the-art accuracy among PLM-based methods for both monomer and complex structure prediction?

## 04 背景与发展脉络
- **脉络**: 蛋白质结构预测方法的发展 (经外部核验)
- **阶段 1: MSA 基方法**:
    - **代表性方法**: AlphaFold2 (Jumper et al., 2021), RoseTTAFold
    - **优点**: 精度高，是当前黄金标准。
    - **局限**: 依赖 MSA 搜索，计算成本高，对孤儿序列效果差。
- **阶段 2: PLM 基单序列方法**:
    - **代表性方法**: ESMFold (Lin et al., 2023)
    - **优点**: 无需 MSA，推理速度快。
    - **局限**: 精度低于 MSA 基方法，架构通用性不足。
- **阶段 3: PLM 基方法扩展到复合物**:
    - **代表性方法**: ESMFold2 (Candido et al., 2026), Protenix-Mini (Gong et al., 2025)
    - **优点**: 将 PLM 基预测扩展到分子相互作用。
    - **局限**: 部分模型未完全开源，性能仍有提升空间。
- **本文主张的位置**: 本文提出 Atlas 模型家族，通过使用宏基因组数据预训练更强的 PLM (AtlasLM)，并设计蛋白质特异性折叠架构 (AtlasFold)，在 PLM 基单体预测上达到 SOTA，并通过微调在复合物预测上达到与 AlphaFold3 相当的水平，同时强调模型的完全开源和高效推理。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
| :--- | :--- | :--- | :--- |
| **PLM 基折叠精度低于 MSA 基方法** | 在 CASP14/15 上，AtlasFold 的 TM-score 低于 AlphaFold2。 | 通过掩码语言建模学习的表征与三维结构预测的直接对齐程度，不如从 MSA 中提取的显式共进化约束。 | Section 3: "representations learned through masked language modeling therefore appear less directly aligned with three-dimensional structure prediction than the explicit coevolutionary constraints extracted from MSAs." |
| **PLM 基复合物预测性能不足** | AtlasFold-M 在 FoldBench 的 P-P 子集上表现低于其他共折叠模型。 | 可能归因于 AtlasLM-3B 的规模较小以及多聚体微调的规模有限。 | Section 2.3: "On the P–P subset, AtlasFold-M performs below the other co-folding models evaluated here, which may reflect the smaller size of AtlasLM-3B and the limited scale of multimer fine-tuning." |
| **无序区域产生假阳性结构 (幻觉)** | 模型在无序区域预测出紧凑的、有组织的结构，而非延伸的、无定形的构象。 | 该现象并非扩散模型特有，ESMFold (使用 IPA 模块) 也产生类似紧凑构象。低置信度区域的“堆积”行为在不同模型中表现不同，不能仅归因于坐标生成架构。 | Section 2.5: "These packed conformations resemble those produced by diffusion models, suggesting that this hallucination is not specific to diffusion-based coordinate generation." |
| **训练不稳定 (梯度爆炸)** | 在移除三角形注意力 (triangle attention) 后，训练在约 30,000 步时反复出现梯度爆炸。 | 架构变更 (移除三角形注意力) 与优化器或其他训练设置不兼容。 | Section 3: "Despite changes to the optimizer and other training settings, this configuration repeatedly encountered gradient explosions around 30,000 updates." |
| **置信度模块训练冲突** | 在共享的置信度模块中加入 PAE 监督后，pLDDT 的样本排序能力下降。 | 局部 (pLDDT) 和成对 (PAE) 置信度预测任务之间存在冲突，共享模块无法同时优化好两个目标。 | Section 3: "Adding PAE supervision degraded pLDDT-based sample ranking." |

## 06 核心思想
1.  **表面方法**: 训练一个 3B 参数的蛋白质语言模型 (AtlasLM)，然后将其表征输入到一个受 AlphaFold3 启发但专为蛋白质单体设计的折叠主干 (folding trunk) 和扩散头 (diffusion head) 中，以预测全原子结构。对于复合物，则对单体模型进行微调。
2.  **核心洞察**:
    - **宏基因组数据提升 PLM 表征**: 在包含宏基因组序列的大规模语料库上训练 PLM，可以学习到更广泛进化变异中的结构约束，从而在无监督接触预测上优于仅使用 UniRef 数据的同规模模型 (ESM2-3B)。
    - **蛋白质特异性架构提升效率**: 将预测问题限制在蛋白质单体，允许使用同质化的表征 (每个 token 对应一个氨基酸)，从而可以简化架构 (如减少扩散步数、降低注意力头数、使用残基距离掩码)，在保持精度的同时大幅提升推理速度和内存效率。
    - **PLM 基折叠的瓶颈在于表征对齐**: 实验表明，即使将训练集目标 (CASP14) 包含在 ESMFold2 的训练中，其性能提升也有限，暗示 PLM 表征与三维结构预测之间的对齐问题比泛化到未见目标的问题更根本。
3.  **可能的普适教训** [Analysis]:
    - **领域特化是提升效率的关键**: 在通用模型 (如 AlphaFold3) 的基础上，针对特定领域 (如蛋白质单体) 进行架构简化和参数调整，可以在不显著牺牲性能的情况下，大幅提升计算效率和降低资源需求。这为在其他生物分子系统 (如 RNA、小分子) 上设计高效模型提供了思路。
    - **数据规模与模型规模并非万能**: 对于 PLM 基折叠，单纯扩大 PLM 的规模 (如 ESM2-15B) 或训练数据 (如 ESMFold2 包含 CASP14 训练集) 可能无法弥合与 MSA 基方法的差距。更关键的是设计能够更好地将 PLM 表征“翻译”为三维结构信息的架构或训练目标 (如 folding-aware pretraining objectives)。
    - **开源生态的价值**: 完全开源 (代码、数据、权重、训练日志) 对于社区理解、复现和扩展模型至关重要，尤其是在发现模型局限性 (如无序区域幻觉) 和探索改进方向时。

## 07 方法总览
- **输入**: 单一蛋白质氨基酸序列 (单体) 或 多条蛋白质氨基酸序列 (复合物)。
- **输出**: 预测的全原子蛋白质结构 (PDB 格式) 及置信度指标 (pLDDT, pTM, PAE, ipTM)。
- **模块**:
    1.  **AtlasLM (蛋白质语言模型)**: 一个 3B 参数的 Transformer，在 UniRef、MGnify 和 MetaClust 上预训练，用于从输入序列生成单表征 (single representation) 和成对表征 (pair representation)。
    2.  **LMStack**: 四个 ESMFold 风格的模块，用于在单表征和成对表征之间交换信息。
    3.  **Folding Trunk (折叠主干)**: 一个 48 块的 Pairformer (受 AlphaFold3 启发)，用于迭代更新单表征和成对表征。
    4.  **Diffusion Head (扩散头)**: 一个蛋白质特异性的 EDM 扩散模型，用于从噪声坐标生成最终的全原子结构。
    5.  **Confidence Head (置信度头)**: 独立的残基置信度头 (预测 pLDDT) 和成对置信度头 (预测 PAE)。
- **训练**:
    - **AtlasLM**: 掩码语言建模 (MLM)，2.0M 步。
    - **AtlasFold**: 四阶段训练，使用 PDB 结构、MGnify-AF2 预测结构和无序 PDB 结构。损失函数包括扩散损失、distogram 损失和置信度损失。
    - **AtlasFold-M**: 从 AtlasFold 检查点微调 25,000 步，使用 PDB 复合物、无序 PDB 和单体蒸馏数据。损失函数遵循 AlphaFold3。
- **工具**: PyTorch, cuEquivariance, OpenStructure。
- **反馈回路**: 推理时使用 4 次回收 (recycling) 来迭代优化表征。
- **假设**: 大规模 PLM 可以从单一序列中学习到足够丰富的结构信息，以替代 MSA 提供的共进化信息；蛋白质特异性架构可以在不损失精度的情况下提高效率。
- **从输入到输出的文字流程**:
    1.  输入序列被送入冻结的 AtlasLM，生成单表征和成对表征。
    2.  这些表征与回收的 (recycled) 状态一起被送入 LMStack 和 48 块的 Pairformer 进行迭代更新。
    3.  最终的成对表征和单表征被送入扩散头。
    4.  扩散头通过 EDM 采样，从随机噪声坐标开始，逐步去噪生成全原子坐标。
    5.  同时，置信度头根据最终的表征和生成的坐标预测 pLDDT 和 PAE。
    6.  对于复合物，AtlasFold-M 在进入主干前会屏蔽链间成对特征，然后通过三角形更新模块进行细化。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **AtlasLM-3B** | 从单一序列生成富含结构信息的单表征和成对表征。 | 替代计算昂贵的 MSA 搜索，提供序列的结构先验知识。 | **输入**: 氨基酸序列。**输出**: 单表征 (R^L×768) 和成对表征 (R^L×L×128)。 | 在无监督接触预测中，P@L 和 P@L/5 优于 ESM2-3B (Fig. 2)。 | 模型将退化为无先验的从头折叠，性能会大幅下降，接近或低于传统能量函数方法。 |
| **Folding Trunk (Pairformer)** | 迭代更新单表征和成对表征，模拟结构折叠的推理过程。 | 将 PLM 的表征转化为更直接用于坐标生成的结构化表征。 | **输入**: 初始单/成对表征。**输出**: 更新后的单/成对表征。 | 这是 AlphaFold2/3 的核心架构，已被证明有效。文中提到移除三角形注意力导致训练不稳定 (Section 3)。 | 模型将无法有效整合序列和结构信息，预测精度会显著下降，甚至无法收敛。 |
| **Diffusion Head (蛋白质特异性)** | 从噪声坐标生成全原子结构。 | 提供一种强大的生成式建模方法，能够处理连续坐标空间中的复杂分布。 | **输入**: 噪声坐标、单/成对表征。**输出**: 去噪后的全原子坐标。 | 在 CAMEO22, CASP14/15 上达到 PLM 基 SOTA (Table 1)。 | 模型将无法生成原子坐标，需要替换为其他坐标生成器 (如 IPA 模块)，可能影响精度和效率。 |
| **Confidence Head (分离式)** | 预测局部 (pLDDT) 和全局 (PAE) 的结构置信度。 | 用于评估预测结构的可靠性，并作为样本选择的依据。 | **输入**: 最终表征和坐标。**输出**: pLDDT, PAE。 | pLDDT 与 lDDT-Cα 的 Pearson r=0.829, pTM 与 TM-score 的 r=0.909 (Fig. 4b)。 | 无法评估预测质量，样本选择将变得盲目，整体性能 (如 Top-1 成功率) 会下降。 |
| **LMStack** | 在单表征和成对表征之间进行信息交换。 | 增强 PLM 输出的表征，使其更好地适应后续的折叠主干。 | **输入**: 单/成对表征。**输出**: 更新后的单/成对表征。 | 继承自 ESMFold 的设计，用于桥接 PLM 和折叠主干。 | 表征可能无法有效融合，导致折叠主干接收到的信息质量下降，影响最终精度。 |

## 09 关键公式符号
- **不适用**: 论文正文和附录中未提供核心的数学公式，如损失函数的具体形式、扩散模型的噪声调度公式等。损失函数以文字描述 (如 "noise-weighted coordinate mean-squared error") 和伪代码形式给出，但未给出明确的数学表达式。

## 10 实验设计与证据链
- **数据集/群体**:
    - **无监督接触预测**: ESM structural superfamily split partition 4 (12,312 训练, 2,985 验证)。
    - **单体结构预测**: CAMEO22 (n=183), CASP14 (n=70), CASP15 (n=56)。
    - **复合物结构预测**: FoldBench 的 P-P (n=278) 和 Ab-Ag (n=172) 子集。
    - **置信度评估**: 10,000 个 2023-01-01 后发布的单体结构。
- **规模**: 如上所述。
- **指标**: P@L, P@L/5, TM-score, GDT-TS, lDDT, DockQ, Fnat, iRMSD, LRMSD, pLDDT, pTM, ipTM。
- **基线**: ESM2-3B, ESM2-15B, ESMC (300M, 600M, 6B), AlphaFold2, RoseTTAFold, RoseTTAFold2, ESMFold, SimpleFold, ESMFold2, AlphaFold3, AlphaFold-Multimer v2.3, Boltz-1, Protenix-v1。
- **预算**: 未提供具体算力 (如 GPU 小时数)。
- **骨干/仪器**: NVIDIA B200 GPU。
- **Oracle 输入**: 无 (所有方法均为无模板预测，除 AlphaFold3 等使用 MSA 外)。
- **评测协议**: 单体预测使用 5 个随机种子生成 5 个样本，选择最高平均 pLDDT 的结构。复合物预测使用 10 个种子，评估所有 252 个 5 种子组合的 Top-1, Oracle, Avg 性能。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **无监督接触预测** | AtlasLM-3B 学习到的注意力图能比 ESM2-3B 更好地恢复长程接触。 | 在 ESM superfamily split 上，使用 Rao et al. 的注意力探针协议。 | AtlasLM-3B 在 P@L 和 P@L/5 上均优于 ESM2-3B (Fig. 2)。 | AtlasLM 的表征编码了更强的结构约束。 | 不能证明 AtlasLM 在所有指标或所有数据集上都优于所有其他 PLM (如 ESMC-6B 表现更好)。 | Fig. 2, Section A.3 |
| **单体结构预测** | AtlasFold 是 PLM 基折叠模型中的 SOTA。 | 在 CAMEO22, CASP14, CASP15 上与 ESMFold, SimpleFold, ESMFold2 等比较。 | AtlasFold 在所有三个基准上均优于其他 PLM 基方法 (Table 1)。 | AtlasFold 在 PLM 基方法中达到了最高精度。 | 不能证明 AtlasFold 优于 MSA 基方法 (AlphaFold2 在 CASP14/15 上更强)。 | Table 1, Section 2.2 |
| **复合物结构预测** | AtlasFold-M 的抗体-抗原预测性能与 AlphaFold3 和 ESMFold2 相当。 | 在 FoldBench Ab-Ag 子集上，与 AlphaFold3, ESMFold2, Boltz-1 等比较。 | AtlasFold-M 的 Top-1 DockQ 成功率 (46.96%) 与 AlphaFold3 和 ESMFold2 相当 (Fig. 5)。 | AtlasFold-M 在 Ab-Ag 预测上具有竞争力。 | 不能证明 AtlasFold-M 在所有复合物类型上都达到 SOTA (在 P-P 子集上表现低于其他模型)。 | Fig. 5, Section 2.3 |
| **推理效率** | AtlasFold 比 ESMFold2 更快、更省内存。 | 在 NVIDIA B200 GPU 上，对不同长度序列进行推理时间和峰值内存分析。 | AtlasFold 在 1024 残基时比 ESMFold2 快 3.4 倍，在 2048 残基时内存使用少 4 倍 (Fig. 1c, 1d)。 | 蛋白质特异性架构带来了显著的效率优势。 | 不能证明 AtlasFold 在所有硬件或所有设置下都是最快的。 | Fig. 1c, 1d, Section D |
| **置信度评估** | AtlasFold 的 pLDDT 和 pTM 能准确反映结构质量。 | 在 10,000 个 holdout 结构上，计算 pLDDT 与 lDDT-Cα，pTM 与 TM-score 的相关性。 | Pearson r 分别为 0.829 和 0.909 (Fig. 4b)。 | 置信度指标是可靠的，可用于样本选择和结构评估。 | 不能证明置信度在所有情况下都完美校准，或在最难的目标上仍然有效。 | Fig. 4b, Section 2.2 |

## 11 结论正确解读
- **任务范围**: 本文的结论严格限定在 **蛋白质单体** 和 **蛋白质-蛋白质复合物** 的结构预测。模型不支持配体、DNA 或 RNA。
- **Oracle/真值输入**: 所有评估均基于 **无模板** 设置。对于复合物，AtlasFold-M 虽然引入了模板模块，但所有报告结果均未使用模板。
- **端到端状态**: 模型是端到端的，从单一序列直接预测结构，无需 MSA 搜索。
- **算力成本**: 论文未提供训练 AtlasLM 和 AtlasFold 的总算力成本，仅提供了推理效率数据。
- **历史数据依赖**: AtlasFold 的训练数据截止于 2020-05-01 (PDB) 和 MGnify 数据集。AtlasFold-M 的 PDB 复合物数据截止于 2021-09-30。模型性能可能受限于这些历史数据。
- **模型依赖**: AtlasFold 的性能高度依赖于 AtlasLM 的质量。作者也指出，使用更大的 PLM 骨干 (如 ESMC-6B) 可能会提升 AtlasFold-M 的性能。
- **最难情形**: 模型在具有高伪困惑度 (pseudo-perplexity) 的蛋白质上表现较差，这些蛋白质可能代表孤儿序列或具有复杂进化模式的序列。此外，在无序区域的“幻觉”问题也是一个已知的困难情形。
- **群体/领域边界**: 结论适用于 CAMEO22, CASP14, CASP15 和 FoldBench 基准测试所代表的蛋白质和复合物群体。对于与训练集分布差异很大的蛋白质 (如新折叠类型)，性能可能下降。
- **不确定性**: 作者明确指出，PLM 基折叠与 MSA 基折叠之间的差距仍然存在，尤其是在 CASP 靶标上。对于复合物预测，AtlasFold-M 在 P-P 子集上的性能落后于其他方法。
- **有边界的复述**: 本文提出的 Atlas 模型家族，通过在大规模宏基因组序列上预训练的 3B 参数语言模型和蛋白质特异性折叠架构，在 **无需 MSA 的单序列输入** 条件下，在 **CAMEO22、CASP14 和 CASP15 基准测试** 上达到了 **PLM 基单体结构预测方法中的最高精度**，并通过微调在 **FoldBench 的抗体-抗原子集** 上实现了与 AlphaFold3 和 ESMFold2 相当的预测性能，同时提供了比 ESMFold2 更快的推理速度和更低的内存占用。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
| :--- | :--- | :--- | :--- |
| **PLM 基折叠与 MSA 基方法的差距** | 在 CASP14/15 上，AtlasFold 的 TM-score 低于 AlphaFold2。 | 通过折叠感知的预训练目标、改进的成对表征或结构引导的适应来更好地对齐 PLM 特征与折叠。 | Section 4 |
| **复合物预测性能有限** | AtlasFold-M 在 FoldBench 的 P-P 子集上表现低于其他共折叠模型。 | 探索更大的 PLM 骨干 (如 ESMC-6B) 和更大、更多样化的复合物训练集。 | Section 2.3, Section 4 |
| **模型范围限制** | 当前框架仅限于蛋白质，不支持配体、DNA 或 RNA。 | 将在后续工作 K-Fold 中解决。 | Section 4 |
| **无序区域幻觉** | 模型在无序区域产生紧凑的、有组织的结构。 | 未明确提及，但暗示了这是一个开放问题，与坐标生成架构无关。 | Section 2.5 |
| **训练数据限制** | 用于微调复合物的 AlphaFold-Multimer 预测数据 (AFDB) 在抗体-抗原目标上导致性能下降。 | 探索更平衡的合成数据采样比例。 | Section 3 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
| :--- | :--- | :--- | :--- | :--- |
| **AtlasLM 的 SOTA 接触预测优势可能不直接转化为折叠优势** | 无监督接触预测 (P@L) 的提升可能主要来自对已知结构域的更好识别，而非对全新折叠的泛化能力。AtlasFold 在 CASP14/15 上仍落后于 AlphaFold2，表明接触预测的改进并未完全弥合与 MSA 基方法的差距。 | 这挑战了“更好的 PLM 表征必然导致更好的折叠”这一隐含假设。 | 1. 分析 AtlasLM 和 ESM2-3B 在孤儿序列或新折叠上的接触预测精度。2. 设计实验，将 AtlasLM 的表征替换为 ESM2-3B 的表征，观察 AtlasFold 性能变化。 | Section 2.2 (Table 1) 显示 AtlasFold 在 CASP 上落后于 AlphaFold2；Section 3 指出 PLM 表征与结构预测的对齐问题。 |
| **蛋白质特异性架构的效率提升可能部分源于更少的计算预算** | AtlasFold 使用 4 次回收和更少的扩散步数，而 AlphaFold3 使用 10 次回收和 200 步。这种效率提升可能部分是因为 AtlasFold 在训练时也使用了更少的计算资源，而非完全归功于架构创新。 | 公平比较需要控制计算预算。如果 AtlasFold 使用与 AlphaFold3 相同的计算量，其精度是否会进一步提升？ | 1. 将 AtlasFold 的回收次数和扩散步数增加到与 AlphaFold3 一致，重新评估精度和速度。2. 在相同计算预算下，比较 AtlasFold 和简化版 AlphaFold3 的性能。 | Section 2.2: "AtlasFold uses 4 recycles and a length-adaptive diffusion schedule, rather than the 10 recycles and fixed 200-step schedule used by AlphaFold3." |
| **复合物微调的数据和策略可能不是最优的** | AtlasFold-M 仅微调 25,000 步，且未使用 AFDB 数据 (因在 Ab-Ag 上性能下降)。这可能意味着微调策略 (如学习率、数据混合) 远未达到最优，而非 PLM 基方法本身的局限。 | 这为未来工作留下了巨大的改进空间，但也意味着当前 AtlasFold-M 的性能可能低估了该方法的潜力。 | 1. 系统性地探索微调步数、学习率、数据混合比例 (特别是 AFDB 数据) 对 P-P 和 Ab-Ag 性能的影响。2. 尝试使用更大的 PLM 骨干进行微调。 | Section 2.3: "AtlasFold-M performs below the other co-folding models... which may reflect the smaller size of AtlasLM-3B and the limited scale of multimer fine-tuning." Section 3: "we did not use the augmented-data configuration in the final AtlasFold-M release." |
| **置信度评估的 holdout 集可能不够严格** | 用于评估置信度的 10,000 个结构仅排除了与结构训练集 (PDB 2020-05-01) 匹配的目标，但未排除与 AtlasLM 预训练语料库 (可能包含更近期的序列) 匹配的目标。 | 如果预训练语料库包含了这些 holdout 序列的同源物，模型可能已经“见过”类似结构，导致置信度评估过于乐观。 | 1. 构建一个与 AtlasLM 预训练语料库无任何序列同源性的 holdout 集。2. 在这个更严格的 holdout 集上重新评估 pLDDT 和 pTM 的校准性能。 | Section 2.2: "This filter applies to the structural-training set but not to the AtlasLM pretraining corpus, which may contain related sequences." |

## 14 学到什么
**Agent 提炼的知识候选**

1.  **可迁移概念: 领域特化提升效率**
    - **概念**: 在通用模型基础上，通过限制预测范围 (如仅限蛋白质单体) 来简化架构 (如使用同质化表征、减少注意力头数、采用残基距离掩码)，可以在不显著牺牲精度的情况下大幅提升推理速度和内存效率。
    - **如何迁移到本课题**: 在设计针对特定蛋白质家族 (如 GPCRs、离子通道) 或特定任务 (如抗体设计、酶设计) 的预测模型时，可以借鉴此思路。例如，为膜蛋白设计一个专门的折叠主干，利用其跨膜螺旋的几何约束来简化扩散模型或注意力机制，从而在保持精度的同时实现更快的虚拟筛选。

2.  **可迁移方法: 分离式置信度模块**
    - **方法**: 将预测局部 (pLDDT) 和全局 (PAE) 置信度的模块分开训练，避免任务冲突导致性能下降。
    - **如何迁移到本课题**: 在开发用于蛋白质设计的生成模型时，可以设计分离的置信度或质量评估头。例如，一个头专门预测设计序列的局部结构合理性 (如 Ramachandran 偏好)，另一个头预测全局折叠的稳定性 (如能量评分)，从而为设计筛选提供更可靠的信号。

3.  **可迁移实验设计: 训练集暴露实验**
    - **实验设计**: 将测试集 (如 CASP14) 包含在训练集中，观察模型性能提升的边际效应，以判断模型的核心瓶颈是泛化能力还是表征对齐。
    - **如何迁移到本课题**: 在评估一个新的蛋白质表示学习方法 (如新的 PLM 或图神经网络) 时，可以设计类似的实验。如果即使在训练集上见过类似结构，模型性能仍无法超越基线方法 (如 MSA 基方法)，则表明当前表示学习范式的根本局限性在于其与下游任务 (如结构预测、功能预测) 的对齐方式，而非数据量或模型容量。

4.  **可迁移概念: 宏基因组数据提升 PLM 表征**
    - **概念**: 使用来自宏基因组的、进化多样性更广的序列数据预训练 PLM，可以学习到更普适的结构约束，从而在无监督任务上表现更好。
    - **如何迁移到本课题**: 在预训练用于蛋白质设计或功能预测的 PLM 时，应优先考虑包含宏基因组数据的训练集 (如 MGnify, MetaClust)，而不仅仅是 UniRef。这有助于模型学习到更丰富的序列-结构-功能关系，可能对设计具有新功能或适应极端环境的蛋白质特别有用。

## 15 与已有知识连接
- **相似工作**:
    - **ESMFold (Lin et al., 2023)**: 本文的 AtlasFold 直接继承并改进了 ESMFold 的范式 (PLM + folding trunk)。AtlasFold 使用更大的 PLM (3B vs. 3B) 和更先进的 AlphaFold3 风格主干，并引入了扩散头。
    - **ESMFold2 (Candido et al., 2026)**: 本文与 ESMFold2 是同期工作，都探索了 PLM 基的复合物预测。AtlasFold-M 在 Ab-Ag 上与之性能相当，但在 P-P 上落后，作者将此归因于模型规模和微调规模。
    - **AlphaFold3 (Abramson et al., 2024)**: AtlasFold 的折叠主干和扩散头深受 AlphaFold3 启发，但通过蛋白质特异性设计进行了简化和加速。
- **组合工作**:
    - 本文的 **AtlasLM** 可以作为其他下游任务的骨干网络，如蛋白质设计 (ProteinMPNN 的输入)、突变效应预测 (ESM-1v 的替代) 或功能注释。
    - 本文的 **AtlasFold** 的快速推理能力可以与其他工具 (如 **Foldseek** 进行结构比对) 结合，用于大规模蛋白质组的结构和功能注释。
- **冲突观点**:
    - 本文的 **核心洞察** 认为 PLM 基折叠的瓶颈在于表征对齐，而非泛化能力。这与一些认为“更大模型 + 更多数据”就能解决所有问题的观点形成对比。作者通过 ESMFold2 在 CASP14 上的训练集暴露实验支持了这一观点。
- **可迁移领域**:
    - **RNA 结构预测**: 本文的“领域特化”思路可以迁移到 RNA 结构预测。可以训练一个 RNA 语言模型 (如 RNA-FM)，然后构建一个 RNA 特异性的折叠主干 (考虑 RNA 的碱基配对和三级结构约束)，以实现快速、准确的单序列 RNA 结构预测。
    - **蛋白质-小分子对接**: 可以借鉴 AtlasFold 的“蛋白质特异性”设计思路，开发一个“蛋白质-小分子特异性”的对接模型。该模型可以针对蛋白质口袋和小分子的化学性质进行架构优化，例如使用等变图神经网络处理小分子，并设计专门的交互模块。

## 16 研究想法
**Agent 生成的研究候选**

1.  **名称**: 折叠感知的 PLM 预训练 (Folding-Aware PLM Pretraining)
    - **来源局限/观察**: 作者指出 PLM 表征与结构预测的对齐是核心瓶颈，且单纯扩大 PLM 规模或训练数据效果有限 (Section 3)。
    - **核心假设**: 在 PLM 预训练阶段引入结构相关的损失项 (如接触图预测、距离图预测或坐标回归)，可以强制模型学习更直接与三维结构对齐的表征，从而提升下游折叠任务的性能。
    - **相对本文的增量**: 本文的 AtlasLM 仅使用 MLM 目标进行预训练。本候选想法是在预训练阶段增加一个辅助的结构预测头，使 PLM 的表征学习过程与结构预测任务更紧密地耦合。
    - **初步方法**:
        1.  在 AtlasLM 的 MLM 训练基础上，增加一个轻量级的结构预测头 (如一个简单的 Transformer 或线性投影层)。
        2.  对于训练数据中具有已知结构的序列 (如 PDB)，计算辅助损失 (如 Cα 距离图的 MSE 或接触预测的交叉熵)。
        3.  联合优化 MLM 损失和结构辅助损失。
        4.  将预训练好的 PLM 作为 AtlasFold 的编码器，重新训练折叠主干，观察性能提升。
    - **验证方式**: 在 CAMEO22, CASP14/15 上比较使用折叠感知 PLM 的 AtlasFold 与原始 AtlasFold 的 TM-score 和 lDDT。同时，在无监督接触预测任务上评估新 PLM 的性能。
    - **可能的失败模式**: 辅助任务可能干扰 MLM 学习，导致 PLM 在序列理解任务上性能下降。或者，辅助任务带来的提升有限，无法弥合与 MSA 基方法的差距。
    - **创新状态**: unverified

2.  **名称**: 基于扩散模型的蛋白质-小分子共折叠 (Diffusion-based Protein-Ligand Co-folding)
    - **来源局限/观察**: AtlasFold 框架仅限于蛋白质，不支持小分子 (Section 4)。然而，蛋白质-小分子相互作用是药物发现的核心。
    - **核心假设**: 可以将 AtlasFold 的蛋白质特异性扩散架构扩展为蛋白质-小分子通用架构，通过为小分子设计专门的原子表征和交互模块，实现端到端的蛋白质-配体复合物结构预测。
    - **相对本文的增量**: 本文的 AtlasFold-M 仅处理蛋白质-蛋白质复合物。本候选想法将模型扩展到异质体系 (蛋白质 + 小分子)，需要处理小分子的原子类型、键连关系和构象灵活性。
    - **初步方法**:
        1.  **小分子编码器**: 使用一个图神经网络 (如 SchNet, DimeNet) 或 Transformer 编码小分子的原子类型、键连关系和初始三维坐标。
        2.  **交互模块**: 在 AtlasFold 的 Pairformer 中增加蛋白质-小分子之间的交叉注意力层，用于建模相互作用。
        3.  **扩散头**: 修改扩散头，使其能够同时生成蛋白质和小分子的全原子坐标。对于小分子，可能需要处理其内部自由度 (如键长、键角、二面角)。
        4.  **训练**: 使用 PDB 中的蛋白质-配体复合物结构进行训练。
    - **验证方式**: 在 PDBbind 或 PoseBusters 等基准上，比较预测的配体结合姿态与晶体结构的 RMSD。与 AutoDock Vina、DiffDock 等传统对接和深度学习方法进行比较。
    - **可能的失败模式**: 小分子的构象空间巨大，模型可能难以收敛。蛋白质-小分子相互作用的建模比蛋白质-蛋白质相互作用更复杂，需要更精细的物理化学先验。训练数据 (高质量共晶结构) 相对稀缺。
    - **创新状态**: unverified

3.  **名称**: 针对抗体 CDR 设计的条件生成模型 (Conditional Generation for Antibody CDR Design)
    - **来源局限/观察**: AtlasFold-M 在抗体-抗原预测上表现良好 (Section 2.3)，但该模型是预测模型，而非设计模型。抗体设计的关键是生成能够特异性结合抗原的 CDR 序列和结构。
    - **核心假设**: 可以将 AtlasFold-M 的架构改造为一个条件生成模型，以抗原结构和抗体框架区为条件，生成多样且高亲和力的 CDR 环区序列和结构。
    - **相对本文的增量**: 本文的 AtlasFold-M 是判别式模型 (给定序列预测结构)。本候选想法是生成式模型 (给定条件生成序列和结构)，需要引入变分自编码器 (VAE) 或流匹配 (Flow Matching) 等生成框架。
    - **初步方法**:
        1.  **条件编码器**: 使用 AtlasFold-M 的编码器处理抗原结构和抗体框架区序列，生成上下文表征。
        2.  **生成模块**: 在扩散头的基础上，增加一个序列预测头。可以采用自回归或非自回归的方式，以结构生成为条件，同时生成 CDR 的序列和坐标。
        3.  **训练**: 使用抗体-抗原复合物结构数据，训练模型在给定抗原和框架区的条件下，重建 CDR 的序列和结构。
        4.  **推理**: 采样生成多个 CDR 候选，并使用预训练的亲和力预测器或 Rosetta 能量函数进行筛选。
    - **验证方式**: 在抗体基准 (如 SAbDab) 上，评估生成 CDR 的结构多样性、与天然结构的 RMSD，以及通过体外实验或对接模拟评估其与抗原的结合能力。
    - **可能的失败模式**: 生成的 CDR 可能在结构上合理但缺乏结合亲和力。模型可能无法探索足够多样的序列空间。训练数据中 CDR 序列和结构的多样性可能不足以覆盖所有设计需求。
    - **创新状态**: unverified