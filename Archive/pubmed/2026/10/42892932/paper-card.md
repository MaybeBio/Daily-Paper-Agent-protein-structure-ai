## 01 基本信息
- **标题**：An inverse-protein-folding pre-trained model for predicting the mutational effects in protein-protein interactions
- **作者**：Mao, Sihong; Meng, Siwei; Xiang, Ye
- **单位**：未提供（通讯作者 Ye Xiang 邮箱为 yxiang@mail.tsinghua.edu.cn，推断为清华大学）
- **期刊/平台**：iScience
- **年份**：2026（在线日期 2026-10-18）
- **论文类型**：研究论文（含方法开发 + 实验验证）
- **领域**：蛋白质-蛋白质相互作用（PPI）突变效应预测 × 深度学习（图神经网络）
- **关键词**：inverse protein folding, protein-protein interaction, mutational effects, message-passing neural network, binding affinity, deep mutation scanning
- **DOI/ID**：10.1016/j.isci.2026.117693
- **代码**：https://github.com/MaoSihong/DGMPNN
- **数据**：SKEMPI v2.0、SARS-CoV-2 RBD-hACE2 DMS 数据（jbloomlab）、CtDock-CtCoh DMS 数据（MaveDB）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI 方法」中的 PPI 突变效应预测任务。其核心创新在于将 inverse protein folding（IPF）预训练任务与注意力池化机制结合，实现无需预计算特征/能量项的纯深度学习 ΔΔG 预测，并展示了在 SARS-CoV-2 RBD-hACE2 多突变体筛选中的实际应用价值。与 AlphaFold、MD 模拟等方法形成互补：不依赖构象采样，直接从结构+序列预测突变效应。

## 02 一句话总结
本文提出 DGMPNN——一个基于 IPF 预训练的 MPNN 框架，通过编码蛋白质复合物的骨架几何与序列信息，直接预测 ln(KD) 并计算 ΔΔG，在 SKEMPI 基准和 SARS-CoV-2 RBD-hACE2 DMS 数据上达到 SOTA 性能，且无需预计算特征或构象采样。

## 03 研究问题
- **具体问题**：如何准确、高效地预测蛋白质-蛋白质相互作用中突变引起的结合亲和力变化（ΔΔG）？
- **为什么重要**：PPI 是信号转导、免疫应答等核心生物过程的基础；准确预测突变效应对于蛋白工程（如抗体优化）、药物发现和病毒进化监测（如 SARS-CoV-2 变异株风险评估）至关重要。
- **现有方法不足**：
  - 实验方法（SPR、BLI）成本高、通量低；
  - 基于物理/经验力场的方法（FoldX、Rosetta）依赖构象采样，计算量大且精度受限于采样充分性；
  - 传统机器学习方法（mCSM-PPI、MutaBind）依赖预定义/预计算特征，特征工程繁琐且可能丢失关键信息；
  - 现有深度学习方法（如 GeoPPI、DiffAffinity）虽引入自监督学习，但多依赖侧链重构等任务，未充分利用 IPF 任务的优势。
- **精确研究问题（Can...?）**：Can an inverse-protein-folding pre-trained MPNN model, without any precomputed biochemical features or conformational sampling, achieve state-of-the-art accuracy in predicting mutation-induced changes in protein-protein binding affinity?

## 04 背景与发展脉络
> 注：此脉络基于本文框架整理，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 |
|------|----------|------|------|
| 实验方法 | SPR、BIL | 准确、直接 | 成本高、通量低 |
| 物理/经验力场 | FoldX、Rosetta | 可解释、有物理基础 | 依赖构象采样，计算量大，精度受采样限制 |
| 传统机器学习 | PoPMuSiC、mCSM-PPI、MutaBind、BindProfX | 速度快、可批量 | 依赖预定义特征，特征工程繁琐 |
| 拓扑数据分析 | PerSpect-EL、TopNetTree | 捕捉拓扑特征 | 特征提取复杂，泛化性有限 |
| 深度学习（自监督） | GeoPPI、RDE-Net、DiffAffinity | 自动特征学习 | 预训练任务与下游任务关联度有限 |
| 深度学习（IPF 预训练） | **DGMPNN（本文）** | 无需预计算特征，IPF 任务与结构-序列关系高度相关 | 依赖高质量结构输入，对多突变组合的泛化仍需验证 |

**本文主张的位置**：DGMPNN 位于深度学习方法的延伸点上，其独特贡献在于：(1) 采用 IPF 作为预训练任务，使模型学习残基在局部结构环境中的适配性；(2) 引入 SAG-like 注意力池化，保留全图信息的同时实现节点级加权；(3) 无需任何预计算特征或构象采样，纯端到端学习。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验方法通量低 | SPR/BLI 每次只能测少量突变体 | 成本高、耗时 | Introduction 节："often limited by high costs and low throughput" |
| 物理方法计算量大 | FoldX/Rosetta 需构象采样 | 依赖离散构象搜索，采样不充分导致不准确 | Introduction 节："rely on extensive conformation sampling, and thus, are time consuming and can be inaccurate due to the limitations of discrete conformation sampling" |
| 传统 ML 依赖预定义特征 | mCSM-PPI、MutaBind 需预计算特征 | 特征工程繁琐，可能遗漏关键信息 | Introduction 节："their accuracy depends on predefined and precalculated input features" |
| 现有 DL 预训练任务关联度有限 | GeoPPI 等使用侧链重构等任务 | 预训练任务与 PPI 突变效应预测的关联不够直接 | Introduction 节："methods that use protein reverse folding task as the main pre-training objective can be further explored" |
| 多突变组合效应难以评估 | 单点突变数据充足，多点突变数据稀疏 | 数据稀缺，且存在上位效应（epistasis） | Discussion 节："The current datasets assessing single-point mutation effects on protein binding affinity remain limited in scale. The entries containing multisite mutations are sparser" |
| 模型无法评估蛋白折叠稳定性 | DGMPNN 无法预测突变导致的折叠/聚集问题 | 训练数据缺乏相关标签 | Limitations 节："our model cannot predict essential functional attributes such as protein folding stability and aggregation propensity" |

## 06 核心思想
1. **表面方法**：构建一个 MPNN 编码器-解码器架构，先在 IPF 任务上预训练（给定骨架结构预测氨基酸序列），再在 PPI 突变效应预测任务上微调。输入为蛋白质复合物的图表示（节点=残基，边=骨架原子间距离+序列位置），输出为 ln(KD) 预测值，进而计算 ΔΔG。

2. **核心洞察**：
   - IPF 任务天然要求模型理解残基与其局部结构环境（包括与其他链残基的接触）的适配关系，这与 PPI 突变效应预测高度相关——突变改变局部化学环境，IPF 预训练使模型对此敏感。
   - 采用 SAG-like 注意力池化而非传统图池化，保留全图信息（不丢弃节点），通过注意力权重实现节点级贡献评估，既提升预测精度又提供可解释性。
   - 直接预测 ln(KD) 而非 ΔΔG，使模型学习绝对亲和力，ΔΔG 通过 WT 与突变体预测值之差计算，避免直接回归小数值的困难。

3. **可能的普适教训 [Analysis]**：
   - 预训练任务的选择应最大化与下游任务的知识重叠。IPF 与 PPI 突变效应共享「序列-结构适配」这一核心物理化学约束，因此迁移效果好。
   - 注意力机制不仅提升性能，还提供可解释的残基级贡献，有助于生物学发现（如关键残基识别）。
   - 纯结构+序列输入、无需预计算特征的端到端设计，简化了使用流程，提高了泛化潜力。

## 07 方法总览
- **输入**：蛋白质复合物的三维结构（骨架原子坐标）+ 序列信息。图表示中，节点=每个氨基酸残基，边=基于 Cα-Cα 距离的 k-NN 图（k=48），边特征包含 25 对骨架原子间距离（Cα, C, N, O, Cβ 的原子对）和相对序列位置编码。
- **输出**：ln(KD) 预测值；ΔΔG 通过 RT·ln(KD_mut/KD_wt) 计算。
- **模块**：
  1. **编码器**：3 层堆叠 MPNN 层，从零向量节点特征出发，通过消息传递更新节点和边表示，提取结构-序列联合表征。
  2. **解码器**：3 层堆叠 MPNN 层，用于 IPF 预训练任务（预测残基身份）。
  3. **注意力池化层**：SAG-like 自适应注意力池化，额外 MPNN 层生成节点级注意力分数，加权求和得到图级表示。
  4. **预测头**：2 层 MLP，将图级表示映射为 ln(KD)。
- **训练流程**：
  1. **预训练**：在 PDB 蛋白质复合物（2021-08-02 前沉积）上执行 IPF 任务，自回归方式预测残基身份，使用 teacher forcing。
  2. **微调**：在 SKEMPI v2.0 衍生的 S2462 数据集（2462 个单点突变，205 个复合物）上微调，损失为 ln(KD) 的 MSE。
- **工具**：PyTorch 等深度学习框架（具体版本未提供）；ProteinMPNN 代码库作为参考（https://github.com/dauparas/ProteinMPNN）。
- **推理流程**：输入突变体复合物结构 → 图构建 → 编码器提取特征 → 注意力池化 → MLP 预测 ln(KD) → 与 WT 预测值比较计算 ΔΔG。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 编码器（3 层 MPNN） | 从骨架几何+序列位置提取残基级结构-序列联合表征 | 将原始几何信息转化为可学习的特征表示，捕捉局部化学环境 | 输入：图（零向量节点特征+几何边特征）；输出：更新后的节点/边表示 | Results 图 2：S2462 上 ln(KD) PCC=0.93 | [预期] 减少层数会缩小感受野，可能降低对远距离残基相互作用的捕捉能力 |
| 解码器（3 层 MPNN） | IPF 预训练任务：预测残基身份 | 通过 IPF 任务学习序列-结构适配规则，为下游任务提供良好初始化 | 输入：编码器输出的结构表示+部分序列上下文；输出：残基身份 logits | Methods 节："pre-trained on an inverse protein folding (IPF) task" | [预期] 移除预训练将显著降低下游性能（IPF 是核心创新） |
| SAG-like 注意力池化 | 生成节点级注意力分数，加权聚合图表示 | 替代传统池化，保留全图信息并实现残基级贡献评估 | 输入：编码器+解码器输出的节点特征；输出：注意力分数+加权图级表示 | Results 图 3：注意力分数识别出已知关键残基（Q493、Q498、N501 等） | [实测] 消融实验（Table S1）显示注意力头数>8 时性能饱和；[预期] 移除注意力池化改用简单池化会降低精度和可解释性 |
| 全局池化（add + max） | 将注意力加权特征与全局最大池化特征拼接 | 结合加权聚合和全局极值信息，丰富图级表征 | 输入：注意力加权节点特征；输出：拼接后的图级特征 | Methods 节："concatenated with global max pooling" | [预期] 移除 max pooling 可能损失对极端残基贡献的捕捉 |
| 预测头（2 层 MLP） | 将图级表示映射为 ln(KD) | 实现从表征到亲和力数值的回归 | 输入：拼接后的图级特征；输出：ln(KD) 标量 | Results 图 2A：ln(KD) PCC=0.93 | [预期] 增加层数可能过拟合，减少层数可能欠拟合 |

## 09 关键公式符号
**1. ΔΔG 计算**：
$$\Delta\Delta G = RT \ln\left(\frac{K_D^{mut}}{K_D^{wt}}\right)$$
- $\Delta\Delta G$：突变引起的结合自由能变化（kcal/mol）
- $R$：气体常数
- $T$：温度（K）
- $K_D^{mut}$：突变体解离常数
- $K_D^{wt}$：野生型解离常数

**2. IPF 预训练损失（负对数似然）**：
$$\mathcal{L}_{IPF} = -\sum_{i} \log p(a_i | \text{structure}, a_{<i})$$
- $a_i$：第 i 个位置的氨基酸残基
- $a_{<i}$：已预测的序列上下文
- $p$：模型预测的残基概率分布

**3. 微调损失（MSE）**：
$$\mathcal{L}_{finetune} = \frac{1}{N}\sum_{j=1}^{N} (\ln K_D^{pred,j} - \ln K_D^{exp,j})^2$$
- $N$：批次中样本数
- $\ln K_D^{pred,j}$：第 j 个样本的预测 ln(KD)
- $\ln K_D^{exp,j}$：第 j 个样本的实验 ln(KD)

**4. 图构建中的边特征**：
- 25 对骨架原子间距离：$\{d_{ab}\}$，其中 $a, b \in \{C_\alpha, C, N, O, C_\beta\}$
- 相对序列位置编码：one-hot 向量（65 位，±32 范围）+ 1 位链间标志

## 10 实验设计与证据链
- **数据集**：
  - S2462：从 SKEMPI v2.0 筛选，2462 个单点突变，205 个双链复合物
  - S1131 和 S4169：SKEMPI 标准基准集
  - SARS-CoV-2 RBD-hACE2 DMS：jbloomlab 数据，BA.1 株 3880 个突变
  - CtDock-CtCoh：MaveDB，C. thermocellum 对接蛋白-共hesin 复合物，2609 个突变
- **指标**：PCC（Pearson 相关系数）、RMSE（均方根误差）
- **基线**：UniBind、MpbPPI、Hom-ML-V2、PerSpect-EL、GeoPPI、TopNetTree、mCSM-PPI2、MutaBind2、BindProfX、FoldX
- **评测协议**：10 折交叉验证；S1131/S4169 上重复 3 次取均值；SARS-CoV-2 子集上对比 SPR/DMS 实验值

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| S2462 10 折交叉验证 | DGMPNN 在内部数据集上的预测精度 | 无外部对比，报告绝对性能 | ln(KD) PCC=0.93, RMSE=2.04；ΔΔG PCC=0.80, RMSE=1.22 | DGMPNN 能高精度预测单点突变效应 | 内部数据集，需外部验证 | Results 图 2A-2B |
| S1131 基准测试 | DGMPNN 达到 SOTA | 对比 UniBind, MpbPPI, Hom-ML-V2, PerSpect-EL, GeoPPI, TopNetTree 等 | PCC=0.874（均值），高于所有对比方法 | DGMPNN 在标准基准上优于现有方法 | 对比方法的结果来自原论文，数据划分可能不同 | Table 1 |
| S4169 基准测试 | DGMPNN 在更大基准上保持 SOTA | 同上 | PCC=0.790（均值），与 MpbPPI+MODELER 相当，略低于 Hom-ML-V2 (0.800) | DGMPNN 在大基准上表现良好但非最优 | 与 Hom-ML-V2 的差距可能源于方法差异或数据划分 | Table 1 |
| 残基类型分层分析 | 模型对极性/带电残基突变预测更准 | 疏水 vs 极性/带电残基突变 | 极性/带电残基 PCC=0.87，疏水残基 PCC=0.74 | 模型对涉及氢键/静电相互作用的突变更敏感 | 分层标准可能影响结论 | Results 图 2C-2D |
| 界面位置分层分析 | 模型对核心界面残基预测更准 | 核心 vs 支撑 vs 边缘 vs 非界面残基 | 核心残基 PCC=0.83，支撑 0.66，边缘 0.63，非界面 0.65 | 模型能有效捕捉界面核心区域的相互作用 | 界面区域分类依赖结构注释 | Results 图 2E-2H |
| SARS-CoV-2 DMS 验证 | 模型在非标准数据上的泛化能力 | 对比 SPR 实验值（23 个突变） | woDMS PCC=0.45, wDMS PCC=0.63；优于其他方法（0.20-0.31） | 模型可迁移至新冠突变预测 | 样本量小（23 个），需更大规模验证 | Table 2 |
| 多突变体实验验证 | 模型筛选的多突变体具有实验可验证性 | 9 个多突变体，SPR/BLI 实验 | 6/9 保持或增强 RBD-hACE2 结合；部分突变体逃逸广谱中和抗体 | 模型可识别具有上位效应的多突变组合 | 样本量小，需更多重复 | Results 图 7 |
| 1R0R 同源排除实验 | 预训练数据中同源复合物不影响下游性能 | 排除 1R0R 同源复合物后重新预训练 | PCC=0.6870 vs 基线 0.6847，无显著差异 | 下游性能不依赖预训练中的同源记忆 | 仅测试了一个复合物 | Table S4 |

## 11 结论正确解读
- **任务范围**：DGMPNN 预测的是 PPI 结合亲和力变化（ΔΔG），基于静态结构输入，不涉及构象动态、变构效应或翻译后修饰。
- **Oracle/真值输入**：模型依赖输入复合物的三维结构（骨架原子坐标）。对于突变体，使用 WT 骨架结构（未对突变体进行结构预测或重建模），这是一个重要简化假设。
- **端到端状态**：模型是端到端训练的，但预训练（IPF）和微调（ΔΔG 预测）是两阶段过程。微调阶段仅更新池化和预测头参数（从 Methods 描述推断）。
- **算力成本**：预训练在单张 NVIDIA RTX 4090 GPU 上完成（具体时长未提供）；多突变体筛选约 21 天（3,200,000 个组合 × 205 种可能）。
- **历史数据依赖**：预训练数据截至 2021-08-02 的 PDB 结构，不包含后续解析的新结构；微调数据来自 SKEMPI v2.0。
- **模型依赖**：基于 ProteinMPNN 架构（v_48_020.pt checkpoint），不同初始化可能影响结果。
- **最难情形**：疏水残基突变（PCC=0.74）、非界面残基突变（PCC=0.65）预测精度较低；多突变体的折叠稳定性无法预测。
- **群体/领域边界**：训练数据以双链复合物为主，对多亚基复合物、膜蛋白复合物的泛化未验证；对非 SKEMPI 类型相互作用（如酶-底物瞬时相互作用）的适用性未知。
- **有边界的复述**：DGMPNN 在 SKEMPI 基准和 SARS-CoV-2 RBD-hACE2 数据上展示了无需预计算特征即可高精度预测单点突变 ΔΔG 的能力，并能通过注意力分数识别关键残基；但对多突变体的预测需结合实验验证，且无法评估折叠稳定性。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 无法预测蛋白折叠稳定性 | 实验验证中 7M、8B、14M 突变体出现异常寡聚状态，超出模型预测范围 | 需结合蛋白稳定性/聚集预测工具 | Limitations 节："our model cannot predict essential functional attributes such as protein folding stability and aggregation propensity" |
| 依赖结构输入质量 | 突变体使用 WT 骨架结构，未考虑突变引起的结构重排 | 引入精确结构建模或构象采样方法 | Limitations 节："the performance...can be hindered by the reliance on potentially inaccurate structural modeling of the mutant complexes" |
| 预训练数据时间限制 | 预训练数据截至 2021-08-02，不包含 Omicron 后续变异株结构 | 纳入更新结构数据 | Limitations 节："the pre-training dataset was restricted to PDB structures deposited before August 2, 2021" |
| 多突变体数据稀疏 | 训练数据以单点突变为主，多突变体预测依赖外推 | 建立多突变体基准数据集 | Discussion 节："The entries containing multisite mutations are sparser" |
| 模型无法评估抗体逃逸 | 多突变体筛选需结合文献中抗体逃逸数据 | 整合抗体-抗原共结构预测 | Results 节："The ability to escape antibody neutralization, as derived from statistics over different antibodies in the previous studies" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| S1131 上 PCC=0.874 与 Hom-ML-V2 的 0.857 差异较小 | 0.017 的 PCC 差异在统计上可能不显著；对比方法的结果来自原论文，数据划分可能不同 | 若差异不显著，则「SOTA」claim 需弱化 | 在统一数据划分下进行配对检验；报告置信区间 | Table 1 |
| 注意力分数与已知关键残基的一致性 | 注意力分数可能反映的是残基可预测性而非功能重要性；相关性分析（r=0.140）较弱 | 可解释性 claim 需谨慎；注意力分数可能受结构冗余影响 | 与随机残基的注意力分布对比；进行置换检验 | Results 图 3、Table S6 |
| 多突变体实验验证样本量小（9 个） | 6/9 成功可能受选择偏差影响；未报告阴性对照 | 模型的实际应用价值需更大规模验证 | 扩大验证集；预注册筛选标准 | Results 图 7 |
| 使用 WT 骨架预测突变体 | 突变引起的局部结构重排被忽略，可能系统性低估/高估某些突变效应 | 对构象变化大的突变（如脯氨酸替换）预测可能失效 | 与突变体实验结构对比；引入结构预测工具 | Limitations 节 |
| 训练数据中 SARS-CoV 相关数据极少（仅 4 个点） | 模型对新冠突变的预测可能依赖泛化而非领域知识 | 新冠应用场景的可靠性需更多验证 | 消融实验：排除所有冠状病毒数据后重新评估 | Table 2 上下文 |
| 未与 AlphaFold 突变扫描或基于 MD 的方法对比 | 这些方法可能在某些场景下更优；对比缺失使定位不清晰 | 用户无法判断何时选择 DGMPNN 而非其他工具 | 在相同基准上对比 AlphaFold2/3、MD+MM-PBSA 等 | 全文未提及此类对比 |
| 预训练数据过滤标准未详细说明 | 30% 序列同一性聚类可能不足以防止信息泄漏 | 若预训练数据包含测试集同源复合物，性能可能虚高 | 详细报告数据过滤流程；进行严格同源排除验证 | Methods 节 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **IPF 作为 PPI 预测的预训练任务是有效的**：IPF 任务（从骨架结构预测序列）迫使模型学习残基与局部化学环境的适配关系，这种知识可直接迁移到突变效应预测。可迁移到本课题：在蛋白质设计、对接 pose 评估等任务中，可考虑使用 IPF 预训练作为通用初始化。

2. **SAG-like 注意力池化的设计选择**：保留全图信息（不丢弃节点）的注意力池化优于传统图池化，且注意力分数提供残基级可解释性。可迁移到本课题：在构象采样或结构评估任务中，可用注意力分数识别关键残基/相互作用热点。

3. **直接预测 ln(KD) 而非 ΔΔG**：通过预测绝对亲和力再计算差值，避免了直接回归小数值（ΔΔG 通常 < 5 kcal/mol）的困难。可迁移到本课题：在预测其他热力学量（如折叠自由能、对接能）时，可考虑预测绝对量再求差。

4. **无需预计算特征的端到端设计**：仅使用骨架几何+序列位置作为输入，避免了特征工程的主观性和计算开销。可迁移到本课题：在构建结构相关预测模型时，优先考虑端到端设计，减少对第三方工具（如 DSSP、SASA 计算器）的依赖。

5. **多突变体筛选策略**：通过 patch-based 组合筛选 + 注意力分数引导，可高效探索巨大序列空间。可迁移到本课题：在蛋白质设计或突变体库构建中，可用注意力分数优先考虑关键位点，减少组合爆炸。

6. **跨数据集验证的重要性**：在 SKEMPI 基准、SARS-CoV-2 DMS、CtDock-CtDock 三个不同来源的数据上验证，增强了结论的可靠性。可迁移到本课题：在开发新方法时，应尽量在多个独立数据集上验证，而非仅依赖单一基准。

## 15 与已有知识连接
- **ProteinMPNN (Dauparas et al., 2022)**：DGMPNN 的编码器-解码器架构和 IPF 预训练任务直接继承自 ProteinMPNN。本文的贡献在于将 IPF 预训练模型适配到 PPI 突变效应预测任务，并引入注意力池化。可参考 ProteinMPNN 原始论文了解架构细节。
- **SKEMPI v2.0 (Jankauskaitė et al., 2019)**：PPI 突变效应预测的标准基准数据集，本文的 S2462、S1131、S4169 均源于此。该数据集包含 300+ 蛋白复合物的 3000+ 突变数据。
- **mCSM-PPI (Rodrigues et al., 2019)**：基于图签名（graph-based signatures）的传统 ML 方法，是本文的主要对比基线之一。其依赖预计算特征，与 DGMPNN 的端到端设计形成对比。
- **MutaBind2 (Zhang et al., 2020)**：结合分子力学（MM）和统计势的 ML 方法，同样依赖预计算特征。
- **GeoPPI (Liu et al., 2021)**：基于几何图神经网络的 PPI 预测方法，使用侧链重构作为预训练任务，与 DGMPNN 的 IPF 预训练形成对比。
- **AlphaFold2/3 (Jumper et al., 2021; Abramson et al., 2024)**：AlphaFold 系列可用于预测突变体结构，但直接用于 ΔΔG 预测的精度有限。DGMPNN 的轻量级设计（无需构象采样）在通量上具有优势。
- **深度突变扫描 (DMS) 技术**：本文使用的新冠 RBD DMS 数据来自 Bloom 实验室，该技术可高通量测量突变对结合的影响，为模型验证提供了宝贵资源。
- **上位效应 (Epistasis)**：本文的多突变体分析揭示了突变间的协同/拮抗效应，这与定量遗传学中的上位效应概念一致，提示 PPI 突变效应预测需考虑突变组合的非线性。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选：IPF 预训练 + 扩散模型的 PPI 突变体结构预测**
   - **来源局限/观察**：DGMPNN 使用 WT 骨架预测突变体效应，忽略突变引起的结构重排（作者自认局限）。
   - **核心假设**：在 IPF 预训练基础上，引入轻量级结构微调模块（如扩散模型或 flow matching），可同时预测突变体结构和结合亲和力变化。
   - **初步方法**：在 DGMPNN 编码器后添加结构生成头，以 WT 结构为条件，生成突变体局部结构；用生成结构与 WT 结构的差异作为额外特征输入预测头。
   - **验证方式**：在 SKEMPI 和 DMS 数据上对比 DGMPNN 与 DGMPNN+结构微调的性能；对结构变化大的突变（如脯氨酸替换）进行专门分析。
   - **创新状态**：unverified

2. **候选：注意力分数引导的 PPI 热点残基预测**
   - **来源局限/观察**：DGMPNN 的注意力分数与实验 ΔΔG 相关性较弱（r=0.140），但能识别已知关键残基。
   - **核心假设**：注意力分数可作为一种零样本（zero-shot）的热点残基预测器，且与基于序列的预测方法（如 EVcouplings）互补。
   - **初步方法**：在多个 PPI 复合物上提取注意力分数，与实验定义的热点残基（如丙氨酸扫描数据）对比；将注意力分数与共进化特征结合，训练热点预测模型。
   - **验证方式**：在 SKEMPI 热点数据库和丙氨酸扫描数据集上评估 AUC；与现有热点预测工具（如 KFC2、Robetta）对比。
   - **创新状态**：unverified

3. **候选：多突变体上位效应的可解释建模**
   - **来源局限/观察**：DGMPNN 对多突变体的预测隐含假设突变效应可加性，但实验显示存在显著上位效应（PCC=0.57 vs 单突变 0.80）。
   - **核心假设**：通过分析注意力分数在突变位点间的协同变化，可显式建模上位效应，提升多突变体预测精度。
   - **初步方法**：提取突变位点对的注意力分数协方差作为上位效应特征；训练一个二阶模型（如双线性层）预测多突变体 ΔΔG。
   - **验证方式**：在新冠 RBD 多突变体数据上对比加性模型与上位效应模型的预测精度；分析注意力分数协方差与实验上位效应的一致性。
   - **创新状态**：unverified

4. **候选：IPF 预训练模型用于抗体-抗原对接 pose 评估**
   - **来源局限/观察**：DGMPNN 的 IPF 预训练使模型对界面残基的序列-结构适配敏感，这一能力可用于评估对接 pose 的质量。
   - **核心假设**：IPF 预训练模型对正确对接 pose 的序列恢复率显著高于错误 pose，可作为排序/评分函数。
   - **初步方法**：在抗体-抗原对接基准（如 ZDOCK 测试集）上，用 DGMPNN 的 IPF 头对每个 pose 计算序列恢复率；将恢复率与现有评分函数（如 Rosetta、ZRANK）结合。
   - **验证方式**：在对接基准上评估 Top-1 成功率；与现有评分函数进行消融对比。
   - **创新状态**：unverified

5. **候选：结合 MD 模拟的 IPF 预训练增强**
   - **来源局限/观察**：DGMPNN 仅使用静态结构，未利用构象系综信息；MD 模拟可提供突变引起的构象变化。
   - **核心假设**：将 MD 模拟产生的构象系综作为 IPF 预训练的增强数据，可提升模型对构象敏感突变的预测能力。
   - **初步方法**：对 SKEMPI 中的复合物进行短 MD 模拟，提取多个构象快照；用这些快照扩充 IPF 预训练数据；在 ΔΔG 预测任务上对比增强前后性能。
   - **验证方式**：在 S1131 和 DMS 数据上对比增强前后 PCC/RMSE；分析模型对柔性界面残基突变的预测改进。
   - **创新状态**：unverified