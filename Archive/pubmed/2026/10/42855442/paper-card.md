## 01 基本信息
- **标题**: InstructPLM-mu: protein fitness prediction from structure instructions
- **作者与单位**: Xu, Junde; Shi, Yapin; Lang, Lijun; Cui, Taoyong; Zhang, Zhiming; Chen, Guangyong; Qiu, Jiezhong; Heng, Pheng-Ann（单位未提供）
- **期刊/预印本平台**: Briefings in Bioinformatics
- **年份**: 2026（在线日期 2026-10-09）
- **论文类型**: 方法学研究（fine-tuning 框架 + 系统比较）
- **领域**: 蛋白质突变效应预测 × 多模态蛋白质语言模型
- **关键词**: 蛋白质适应度预测、突变效应、多模态融合、ESM2、结构指令、参数高效微调
- **DOI/arXiv 号**: 10.1093/bib/bbag400
- **代码**: https://github.com/ssyypp1/InstructPLM-mu
- **数据**: CATH 4.3（训练）、ProteinGym（217 assays，筛选后 201 个用于评测）；模型权重 https://huggingface.co/ssyypp111/ESM2-150M-TokenWise
- **阅读日期**: 未提供
- **在该方向中的位置**: 该文处于「蛋白质结构相关计算研究 × AI 方法」交叉点，聚焦于如何将结构信息高效注入预训练序列 PLM（ESM2），以零样本突变效应预测为下游任务。其核心贡献在于系统比较三种结构-序列融合策略（Cross Attention、Channel-wise Concat、Token-wise Concat），并证明 Token-wise Concat 能以远低于端到端多模态模型（如 ESM3）的训练成本达到可比性能。该工作为「结构指令注入预训练 PLM」这一技术路线提供了实证支持，属于参数高效多模态蛋白质建模方向。

## 02 一句话总结
该文提出 InstructPLM-mu 微调框架，通过在 ESM2 的输入层将结构嵌入作为额外 token 拼接（Token-wise Concat），以约 4 小时 A100 训练成本达到与 1.4B 参数 ESM3 相当的零样本突变效应预测性能（平均 Spearman 0.469 vs 0.468），并系统证明融合策略与微调方案（LoRA+Adapter 最优）对最终性能有显著影响。

## 03 研究问题
- **具体问题**: 能否通过微调预训练的序列-only PLM（ESM2）并注入结构信息，达到与端到端训练的多模态 PLM（如 ESM3）相当的突变效应预测性能？哪种结构-序列融合策略和微调方案最优？
- **为什么重要**: 端到端训练多模态 PLM 需要大量算力和数据（如 ESM3 为 1.4B 参数），对大多数研究组不可及。若能以微调方式将结构信息注入已有 PLM，可大幅降低计算门槛，使结构感知的突变预测普惠化。
- **现有方法不足**: 已有工作（如 SaProt、ProSST、S3F）虽引入结构信息，但多采用端到端训练或冻结 ESM2 嵌入后训练独立编码器，缺乏对「融合策略」和「微调方案」的系统比较；且对「如何在不破坏预训练知识的前提下注入结构信息」缺乏实证指导。
- **精确研究问题**: Can a pretrained sequence-only PLM, augmented with structural information during fine-tuning, match the performance of end-to-end trained multimodal models?

## 04 背景与发展脉络
（标注：以下脉络基于本文 Introduction 与 Related Works 的叙述框架，未经外部系统核验，标注为「仅本文框架」）

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 经典能量/物理方法 | Rosetta、ABACUS2 | 可解释、基于物理 | 采样限制、势函数偏差 |
| 序列-only 深度方法 | ESM-1v、ESM2 | 大规模预训练、泛化强 | 忽略结构信息 |
| 结构感知深度方法 | ProSST、Pythia、SaProt、S3F | 引入结构信息、精度提升 | 多需端到端训练或额外编码器，算力成本高 |
| 多模态 PLM | ESM3 | 统一序列-结构-功能建模 | 1.4B 参数、训练成本极高 |
| 本文位置 | InstructPLM-mu | 微调 ESM2 + 结构 token 拼接，成本低、性能可比 ESM3 | 依赖已有结构编码器（ESM-IF/ProteinMPNN） |

**本文主张的位置**: 在「序列-only PLM + 结构微调」这一中间路线中，Token-wise Concat 是最优融合策略，且参数高效微调（LoRA+Adapter）优于全量微调，为多模态 PLM 的高效构建提供了新范式。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 端到端多模态 PLM 训练成本过高 | ESM3 为 1.4B 参数，需大量算力 | 从零训练多模态模型需大规模数据和计算资源 | Introduction: "training such models from scratch demands substantial computational resources" |
| 结构信息注入方式缺乏系统比较 | 已有工作采用不同融合策略，但无统一比较 | 融合策略（Cross Attention、Channel-wise、Token-wise）对性能影响未被系统评估 | Methods 节三种策略对比；Results 表 2 |
| 微调方案不当导致知识遗忘 | 全量微调在较大模型上性能下降 | 过度调整预训练参数破坏已学知识 | Results 表 4: "overly aggressive training recipe may lead to knowledge forgetting" |
| 简单拼接多编码器不产生增益 | ESM-IF + ProteinMPNN 联合不如单 ESM-IF | 编码器信息重叠，简单拼接引入噪声 | Results 表 5: "concatenating both encoders does not produce additive gains" |

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 端到端多模态 PLM 训练成本过高 | ESM3 为 1.4B 参数，需大量算力 | 从零训练多模态模型需大规模数据和计算资源 | Introduction: "training such models from scratch demands substantial computational resources" |
| 结构信息注入方式缺乏系统比较 | 已有工作采用不同融合策略，但无统一比较 | 融合策略（Cross Attention、Channel-wise、Token-wise）对性能影响未被系统评估 | Methods 节三种策略对比；Results 表 2 |
| 微调方案不当导致知识遗忘 | 全量微调在较大模型上性能下降 | 过度调整预训练参数破坏已学知识 | Results 表 4: "overly aggressive training recipe may lead to knowledge forgetting" |
| 简单拼接多编码器不产生增益 | ESM-IF + ProteinMPNN 联合不如单 ESM-IF | 编码器信息重叠，简单拼接引入噪声 | Results 表 5: "concatenating both encoders does not produce additive gains" |

## 06 核心思想
1. **表面方法**: 提出 InstructPLM-mu 微调框架，将预训练 ESM2 与结构编码器（ESM-IF 或 ProteinMPNN）结合，通过三种融合策略（Cross Attention、Channel-wise Concat、Token-wise Concat）注入结构信息，并在 CATH 4.3 上用 MLM 目标微调，最后在 ProteinGym 上零样本评估突变效应预测。
2. **核心洞察**: 
   - 结构信息可以以「指令 token」的形式（Token-wise Concat）注入 PLM，让模型通过自注意力机制动态决定何时、如何利用结构线索，而非强制融合。
   - 微调策略比模型规模更关键：参数高效微调（LoRA+Adapter）在较大模型上优于全量微调，避免知识灾难性遗忘。
   - 结构编码器的质量比数量重要：单一强编码器（ESM-IF）优于简单拼接两个编码器。
3. **可能的普适教训** [Analysis]: 
   - 对于「预训练大模型 + 新模态注入」问题，将新模态作为额外 token 而非修改模型架构，可能是更通用、更高效的路线。
   - 「少调参、精调参」在 PLM 微调中可能优于全量微调，尤其当预训练知识本身已很强时。
   - 多模态融合并非越多越好，信息重叠的编码器简单拼接可能引入噪声，需设计选择性融合机制。

## 07 方法总览
- **输入**: 蛋白质序列（氨基酸序列）+ 对应结构（由结构编码器处理）
- **输出**: 突变效应预测分数（零样本，通过 masked-marginals 计算）
- **模块**:
  1. 序列编码器: ESM2（35M/150M/650M 三种规模）
  2. 结构编码器: ESM-IF 或 ProteinMPNN（输出结构嵌入）
  3. 投影层: 可学习 MLP（将结构嵌入维度映射到序列嵌入维度）
  4. 融合模块: 三种策略之一（Cross Attention / Channel-wise Concat / Token-wise Concat）
  5. 微调方案: Full Fine-tune / LoRA+Adapter / Adapter-only
- **训练**: CATH 4.3 数据集，MLM 目标，序列裁剪至 512 tokens，4×A100 GPU
- **推理**: ProteinGym 零样本突变效应预测，masked-marginals 打分
- **文字流程**: 
  1. 输入序列经 ESM2 embedding 层得序列嵌入 X_seq ∈ R^{L×d_s}
  2. 输入结构经结构编码器得结构嵌入 H_str ∈ R^{L×d_t}
  3. 投影层 W_str 将结构嵌入映射到 R^{L×d_s}
  4. 按所选融合策略将结构信息注入序列嵌入
  5. 微调后的 ESM2 处理融合表示，输出每个位置的 token 概率
  6. 对突变位点 masked-marginals 打分，得到突变效应分数

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| 序列编码器 ESM2 | 提取序列语义表示 | 预训练 PLM 已编码进化约束 | 输入: 序列；输出: 序列嵌入 | 表 2 中所有融合策略均优于序列-only 基线 | 移除则退化为纯结构方法，性能显著下降（表 2 对比） |
| 结构编码器 ESM-IF | 从结构提取残基级嵌入 | 提供序列中缺失的结构约束 | 输入: 结构；输出: 结构嵌入 | 表 5: ESM-IF 优于 ProteinMPNN | 替换为 ProteinMPNN 性能下降（表 5） |
| 投影 MLP | 维度对齐 | 结构嵌入维度 ≠ 序列嵌入维度 | 输入: 结构嵌入；输出: 投影后结构嵌入 | Methods 节公式 (3) | 无法融合，维度不匹配 |
| 融合策略（三种） | 决定结构信息如何注入 | 不同融合方式影响信息流动 | 输入: 序列+结构嵌入；输出: 融合表示 | 表 2: Token-wise 最优 (0.469) | 换用其他策略性能下降 0.03-0.04（表 2） |
| 微调方案（三种） | 控制预训练参数更新程度 | 过度更新导致知识遗忘 | 输入: 预训练模型+新参数；输出: 微调后模型 | 表 4: LoRA+Adapter 最优 | 全量微调在 650M 上性能不稳定（表 4） |
| masked-marginals 打分 | 零样本突变效应预测 | 无需监督标签即可评估突变 | 输入: 微调后模型+突变序列；输出: 突变分数 | Methods 节公式 (11) | 移除则无法进行零样本评估 |

## 09 关键公式符号
1. **序列嵌入**: X_seq ∈ R^{L×d_s}，其中 L 为序列长度，d_s 为序列嵌入维度
2. **结构嵌入**: H_str ∈ R^{L×d_t}，其中 d_t 为结构嵌入维度
3. **投影层**: Ẋ_str = H_str · W_str，其中 W_str ∈ R^{d_t×d_s} 为可学习投影矩阵
4. **Cross Attention 融合**: H^(T) = CrossAttn(H^(T-1), Ẋ_str)，在最终 transformer block 中插入交叉注意力子层
5. **Channel-wise Concat**: Z = X_seq + Ẋ_str（逐元素相加，即 channel-wise 融合）
6. **Token-wise Concat**: Z = [X_seq; Ẋ_str]（沿序列维度拼接，长度变为 2L）
7. **MLM 训练目标**: L = -Σ_{i∈M} log p_θ(x_i | X_mask, Z)，其中 M 为掩码位置集合
8. **突变分数**: S = Σ_{i∈M} [log p_θ(x_i^mut | X_mask, Z) - log p_θ(x_i^wt | X_mask, Z)]

## 10 实验设计与证据链
- **数据集**: 
  - 训练: CATH 4.3（蛋白质结构分类数据库）
  - 评测: ProteinGym 基准（217 assays，排除 >1000 残基后 201 个）
- **指标**: Spearman 秩相关系数（突变效应预测 vs 实验值）
- **基线**: ESM2（不同规模）、ESM-1v、SaProt、S3F、ProSST、ProtSSN
- **骨干/仪器**: 4×NVIDIA A100 GPU
- **评测协议**: 零样本（zero-shot），无监督微调后直接预测

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|-----------|----------------|------|
| 融合策略对比 | Token-wise Concat 最优 | 三种策略 × ESM2 35M/150M/650M | Token-wise 平均 0.469，优于 Channel-wise (0.435) 和 Cross Attention (0.440) | 融合策略显著影响性能 | 未证明 Token-wise 在所有 backbone 和任务上均最优 | 表 2 |
| 与序列-only 基线对比 | 结构注入提升性能 | 三种策略 vs ESM2 各规模 | 所有融合策略均优于 ESM2 基线 | 结构信息对突变预测有增益 | 未分离结构编码器质量与融合策略的贡献 | 表 2 |
| 与端到端多模态模型对比 | 微调可达可比性能 | InstructPLM-mu vs ESM3、SaProt、S3F、ProSST | Token-wise (0.469) ≈ ESM3 (0.468)，优于 SaProt (0.461) 和 S3F (0.460) | 微调可匹配端到端训练 | 未在更大规模 backbone 上验证 | 表 3 |
| 微调方案对比 | LoRA+Adapter 最优 | Full Fine-tune / LoRA+Adapter / Adapter-only × 三种融合策略 | LoRA+Adapter 在 Token-wise 上最优 | 参数高效微调优于全量微调 | 最优方案依赖融合策略和模型规模 | 表 4 |
| 结构编码器消融 | ESM-IF 优于 ProteinMPNN | ESM-IF vs ProteinMPNN vs 两者拼接 | ESM-IF 单独最优，拼接无增益 | 编码器质量比数量重要 | 未测试其他结构编码器 | 表 5 |
| MLP 深度消融 | 浅层 MLP 足够 | 2/3/4 层 MLP | 2 层和 3 层接近，4 层略降 | 浅层投影足够 | 未测试更深 MLP | 表 5 |

## 11 结论正确解读
- **任务范围**: 该结论仅适用于零样本突变效应预测任务（ProteinGym 基准），不直接推广到其他下游任务（如结构预测、设计）。
- **oracle/真值输入**: 评测使用实验测定的突变效应值（DMS 数据）作为真值；结构输入来自已知实验结构（非预测结构）。
- **端到端状态**: 该方法并非端到端训练多模态模型，而是微调预训练序列 PLM + 注入结构嵌入，结构编码器本身未在训练中更新（仅投影层和 PLM 参数更新）。
- **算力成本**: 训练成本约 4 小时（4×A100），远低于端到端训练（如 ProSST 需 1 个月），但未报告推理成本。
- **历史数据依赖**: 依赖 CATH 4.3 的结构-序列配对数据；依赖 ESM2 和 ESM-IF 的预训练知识。
- **模型依赖**: 结论基于 ESM2 和 ESM-IF/ProteinMPNN 的组合，换用其他 PLM 或结构编码器可能改变结论。
- **最难情形**: 未报告在低同源性蛋白、多突变组合、非点突变等困难情形下的表现。
- **群体/领域边界**: 评测覆盖 201 个 DMS 数据集，涵盖多种蛋白质功能类别，但未覆盖所有蛋白质家族。
- **不确定性**: 未报告置信区间或多次运行的标准差；统计显著性分析在补充材料中。
- **有边界的复述**: 在 ProteinGym 零样本突变效应预测任务上，以 ESM2 为 backbone、ESM-IF 为结构编码器、Token-wise Concat 为融合策略、LoRA+Adapter 为微调方案，可以达到与 1.4B 参数 ESM3 相当的性能（Spearman 0.469 vs 0.468），且训练成本仅为 4 小时（4×A100）。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 仅测试 ESM2 backbone | 未在更大或更新的 PLM 上验证 | 探索更强 backbone（如 ESM3、SaProt） | Discussion: "Leveraging stronger backbones (e.g. ESM3, SaProt, etc.)" |
| 结构编码器选择有限 | 仅测试 ESM-IF 和 ProteinMPNN | 探索更多结构编码器及编码器级融合 | Discussion: "more sophisticated multi-encoder fusion strategies" |
| 简单拼接多编码器无增益 | ESM-IF + ProteinMPNN 联合不如单 ESM-IF | 设计门控或注意力机制的选择性融合 | Discussion: "per-encoder gating or attention-based fusion" |
| 微调方案不稳定 | 全量微调在 650M 上性能不稳定 | 研究分阶段训练、逐层解冻等更细粒度方案 | Discussion: "staged training schedules, layer-wise unfreezing" |
| 未探索额外模态 | 仅使用序列+结构 | 引入 MSA 等多模态信息 | Discussion: "extra modalities (e.g. multiple sequence alignments (MSAs))" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| Token-wise Concat 的优势可能来自参数增加而非融合策略本身 | Token-wise 将序列长度翻倍，模型可学习参数和注意力计算量增加，可能带来隐式正则化或容量提升 | 若优势来自容量而非融合设计，则结论需重新解读 | 控制参数量的对比实验（如增加 Channel-wise 的模型宽度） | 表 2 中三种策略未控制总参数量 |
| 与 ESM3 的比较可能不公平 | ESM3 是通用多模态模型，未针对突变预测微调；InstructPLM-mu 在 CATH 上微调过 | 微调本身可能贡献了大部分性能提升 | 对比「未微调的 ESM2 + 结构 token」与「微调后的」 | 表 3 未报告 ESM3 在相同微调条件下的表现 |
| 零样本评估的局限性 | masked-marginals 打分可能对某些突变类型（如插入/缺失）不适用 | 限制了方法在更广泛突变场景的适用性 | 在 indel 突变、多突变组合上测试 | Methods 节仅描述点突变场景 |
| 结构输入的来源未明确 | 若使用实验结构，实际应用中需预测结构，性能可能下降 | 影响方法的实际可用性 | 使用 AlphaFold 预测结构作为输入重测 | 全文未明确结构输入来源 |
| 统计显著性报告不充分 | 仅报告平均 Spearman，未报告方差或置信区间 | 无法判断性能差异是否显著 | 补充多次运行的标准差和显著性检验 | 补充表 S3 提及但正文未展开 |

## 14 学到什么
**Agent 提炼的知识候选**:

1. **可迁移概念 - 「指令 token」注入**: 将新模态（结构）作为额外 token 拼接到序列输入，而非修改模型架构，是一种极简且有效的多模态融合方式。可迁移到其他「预训练模型 + 新模态」场景（如序列 + 进化信息、序列 + 功能注释）。

2. **可迁移方法 - 参数高效微调优先**: LoRA+Adapter 在多数设置下优于全量微调，且计算成本更低。对于蛋白质结构相关计算研究，当 backbone 较大时，应优先考虑参数高效微调而非全量微调。

3. **可迁移实验设计 - 融合策略 × 微调方案的系统比较**: 本文通过 3×3 网格（3 种融合 × 3 种微调）系统比较，揭示了「融合策略」和「微调方案」的交互效应。这种系统消融设计值得在类似研究中借鉴。

4. **可迁移洞察 - 结构编码器质量 > 数量**: 单一强编码器（ESM-IF）优于简单拼接两个编码器，提示多模态融合应注重编码器质量而非数量，且需设计选择性融合机制。

5. **对蛋白质结构预测/设计的启示** [Analysis]: 本文证明结构信息可以「软性」注入 PLM（作为可被注意力机制动态调用的 token），而非「硬性」约束。这一思路可迁移到结构感知的蛋白质设计任务——将结构约束作为条件 token 而非强制损失项，可能保留更多序列多样性。

6. **对 MD 模拟/构象采样的启示** [Analysis]: 本文的「指令 token」思想可类比为在序列模型中注入构象状态信息——将 MD 模拟中的构象状态编码为 token 注入 PLM，可能实现「序列-构象」联合建模，但需注意计算开销（token 数量翻倍）。

## 15 与已有知识连接
- **ESM2 (Lin et al., 2023)**: 本文 backbone，序列-only PLM 的代表。本文证明其可通过微调吸收结构信息，支持「PLM 作为通用序列编码器」的观点。
- **ESM-IF (Hsu et al., 2022)**: 逆折叠模型，本文用作结构编码器。其残基级结构嵌入被证明对突变预测有效，支持「结构感知表示可提升功能预测」的已有结论。
- **ProteinMPNN (Dauparas et al., 2022)**: 消息传递网络，本文用作结构编码器。与 ESM-IF 的对比显示，预训练 PLM 类结构编码器（ESM-IF）优于非预训练方法（ProteinMPNN）。
- **ESM3 (Hayes et al., 2024)**: 端到端多模态 PLM，本文主要对比对象。本文证明微调 ESM2 可达到 ESM3 性能，挑战了「更大模型必然更好」的假设。
- **ProteinGym (Notin et al., 2023)**: 标准突变效应基准，本文评测平台。与 SaProt、S3F、ProSST 等方法的对比，定位了本文方法在现有技术谱系中的位置。
- **LoRA (Hu et al., 2021)**: 参数高效微调方法，本文验证其在 PLM 多模态微调中的有效性，与 NLP 领域的结论一致。
- **候选方向** [Analysis]: 本文与「结构感知 PLM」这一活跃方向相关，可连接至 ESM3、SaProt 等近期工作；其「指令 token」思想与多模态 LLM 中的「软提示」（soft prompt）技术有相似性，但本文未明确讨论这一联系。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: 结构指令 token 的注意力模式分析
   - **来源局限/观察**: 本文证明 Token-wise Concat 有效，但未解释「模型如何利用结构 token」——是作为全局上下文还是局部约束？
   - **核心假设**: 模型在预测突变效应时，对结构 token 的注意力权重集中在突变位点附近残基。
   - **初步方法**: 对微调后模型进行注意力权重可视化，统计结构 token 与序列 token 的注意力分布；对比不同融合策略的注意力模式差异。
   - **验证方式**: 在 ProteinGym 子集上分析注意力模式与预测精度的相关性。
   - **创新状态**: unverified

2. **候选名称**: 结构 token 注入的泛化性——跨 backbone 与跨任务验证
   - **来源局限/观察**: 本文仅测试 ESM2 backbone 和突变预测任务，Token-wise Concat 的优势是否普适未知。
   - **核心假设**: Token-wise Concat 的优势可迁移到其他 PLM（如 ESM3、ProtT5）和其他任务（如稳定性预测、结合亲和力预测）。
   - **初步方法**: 在 ESM3 和 ProtT5 上复现三种融合策略，在 ProteinGym 和额外基准（如 ThermoMutDB）上评测。
   - **验证方式**: 比较不同 backbone 上融合策略的相对排名是否一致。
   - **创新状态**: unverified

3. **候选名称**: 结构 token 的噪声鲁棒性——预测结构 vs 实验结构
   - **来源局限/观察**: 本文未明确结构输入来源；实际应用中常需使用预测结构（如 AlphaFold）。
   - **核心假设**: Token-wise Concat 对结构噪声的鲁棒性优于 Channel-wise Concat 和 Cross Attention。
   - **初步方法**: 使用 AlphaFold 预测结构替代实验结构，比较三种融合策略的性能下降幅度。
   - **验证方式**: 在 ProteinGym 子集上对比实验结构与预测结构的 Spearman 差异。
   - **创新状态**: unverified

4. **候选名称**: 结构 token 的动态门控机制
   - **来源局限/观察**: 本文发现简单拼接多编码器无增益，提示需要选择性融合；但未设计门控机制。
   - **核心假设**: 可学习的门控机制（如 per-token 或 per-layer 门控）能比静态拼接更好地平衡序列与结构信息。
   - **初步方法**: 在 Token-wise Concat 基础上增加可学习门控向量，控制每个位置结构 token 的贡献权重。
   - **验证方式**: 与静态拼接对比，在 ProteinGym 上评测性能提升。
   - **创新状态**: unverified

5. **候选名称**: 结构指令 token 用于蛋白质设计
   - **来源局限/观察**: 本文聚焦突变预测（判别任务），但「结构指令」思想可迁移到生成任务。
   - **核心假设**: 将结构 token 注入 PLM 后，模型可生成满足特定结构约束的序列。
   - **初步方法**: 在 CATH 上微调 InstructPLM-mu 后，用条件生成方式设计满足目标结构的序列，评测序列恢复率和结构有效性。
   - **验证方式**: 与 ESM-IF 逆折叠基线对比，在 CATH 测试集上评测。
   - **创新状态**: unverified