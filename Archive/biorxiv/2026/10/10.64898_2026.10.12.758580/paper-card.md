## 01 基本信息
- **标题**：A high-resolution protein-RNA binding atlas for structure-aware interaction prediction and post-transcriptional regulatory modeling
- **作者**：Mehran Karimzadeh; Lisa Fish; Heather Karner; Johannes Linder; Ali Emadi; Aldo Hernandez-Corchado; Fatima Zohra Smaili; Khashayar Ghavami; Edna S. Stewart; David Kelley; Bo Wang; Hamed Shateri Najafabadi; Manuel D. Leonetti; Hani Goodarzi
- **单位**：未提供（作者所属机构未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：方法学 + 资源型论文（实验方法开发 + 数据集构建 + 深度学习建模）
- **领域**：RNA 结合蛋白（RBP）互作图谱；RNA 结构感知的深度学习预测；转录后调控建模
- **关键词**：eclair CLIP (ecCLIP)、RNA-binding protein (RBP)、RNA structure、deep learning、post-transcriptional regulation、variant effect prediction
- **DOI/ID**：10.64898/2026.10.12.758580
- **代码**：Pythia: https://github.com/goodarzilab/pythia ；Borzuki: https://github.com/calico/borzoi-paper/tree/main/extensions/borzuki
- **数据**：GEO 登录号 GSE349934
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-RNA 相互作用的结构感知预测」方向，核心贡献为：(1) 开发了高通量、高分辨率的 RBP-RNA 结合图谱实验平台 ecCLIP；(2) 构建了结构感知的深度学习模型 Pythia，显式编码 RNA 碱基配对特征；(3) 将 RBP 结合预测与 RNA 稳定性（半衰期）及 3' UTR 变异效应联系起来。与课题的关联在于：其「结构感知的深度学习架构」和「序列-结构解耦的归因分析」思路可迁移至蛋白质结构预测、构象采样及蛋白质-RNA 复合物相互作用建模。

## 02 一句话总结
本文开发了 eclair CLIP (ecCLIP) 高通量实验平台，对 67 个内源标记的 RNA 结合蛋白（RBP）在 HEK293T 细胞中生成转录组规模的结合图谱，并训练了结构感知的深度学习模型 Pythia（含固定碱基配对卷积层），在 RBP 结合位点预测、RNA 半衰期预测及 3' UTR 变异效应评估上优于或匹敌现有方法，且通过大规模平行报告基因 CLIP (MPRC) 实验验证了结构归因的生物学可解释性。

## 03 研究问题
- **具体问题**：如何生成足够高质量、高分辨率、跨多个 RBP 的转录组规模结合图谱，并利用这些图谱训练能够同时捕捉 RNA 序列和结构决定因素的预测模型，从而解释和预测 RBP 结合及其对 RNA 稳定性的调控？
- **为什么重要**：RBP 调控 RNA 加工、定位、稳定性和翻译，其结合位点的解析是理解转录后调控机制和解读非编码区遗传变异功能的关键。现有图谱在分辨率、覆盖 RBP 数量和实验一致性上存在不足。
- **现有方法不足**：(1) 传统 CLIP-seq 依赖特异性抗体，抗体质量差异大，难以规模化；(2) 现有图谱多来自 K562/HepG2 等细胞系，缺乏 HEK293T 背景；(3) 多数深度学习模型仅使用序列特征，未显式编码 RNA 二级结构信息；(4) 缺乏对序列 vs 结构贡献的系统性归因和实验验证。
- **精确研究问题**：Can a structure-aware deep learning model trained on a uniformly generated, high-resolution RBP binding atlas improve prediction of RNA stability and variant effects on RBP binding, compared to sequence-only models?

## 04 背景与发展脉络
> 注：此脉络基于本文框架，未经外部核验。
- **阶段一：CLIP-seq 技术发展**。从早期 CLIP (Ule et al., 2003)、HITS-CLIP、PAR-CLIP 到 eCLIP (Van Nostrand et al., 2016)，逐步提高灵敏度和分辨率。局限：依赖抗体、步骤繁琐、通量有限。
- **阶段二：规模化 RBP 图谱**。ENCODE eCLIP 在 K562/HepG2 中覆盖约 150 个 RBP，但抗体依赖和细胞类型限制明显。本文的 ecCLIP 通过内源 split-mNeonGreen 标签实现统一捕获，避免抗体差异，并扩展至 HEK293T。
- **阶段三：序列到功能的深度学习模型**。Borzoi (Linder et al., 2025) 和 Saluki (Agarwal & Kelley, 2022) 建立了从 DNA 序列预测 RNA 表达和稳定性的框架。局限：未显式建模 RNA 二级结构，且训练数据缺乏高分辨率 RBP 结合信息。
- **阶段四：结构感知的 RNA 建模**。传统 RNA 结构预测（如 RNAfold）和结构 motif 发现（如 RNApromo）提供了结构表示思路，但未与深度学习端到端结合。本文的 Pythia 通过固定碱基配对卷积层将 CFG 启发的结构先验嵌入神经网络，是该方向的新尝试。
- **本文位置**：处于阶段三与阶段四的交汇点，用 ecCLIP 图谱增强 Borzoi 类模型的训练数据，同时用 Pythia 引入显式结构归纳偏置。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 抗体依赖导致 CLIP 规模化困难 | 不同 RBP 的抗体质量差异大，部分 RBP 无可用抗体，难以统一比较 | 传统 CLIP 依赖特异性抗体进行免疫沉淀，抗体批次差异和可用性限制了通量和一致性 | 摘要及 Introduction 中关于现有 CLIP 资源局限的论述 |
| 图谱分辨率不足 | 峰值宽泛，难以精确定位 RBP 结合 motif | 连接酶依赖的文库制备和放射性标记可视化步骤导致信噪比低、分辨率受限 | Introduction 中关于 ligation-dependent library preparation 和 radioactive visualization 的讨论 |
| 现有模型忽略 RNA 结构 | 序列模型无法解释结构依赖的 RBP 结合（如 HNRNPC 对单链 poly-U 的偏好） | 多数深度学习模型仅编码序列，未显式编码碱基配对或结构可达性 | Pythia 设计动机（Introduction 及 Results 3.1） |
| 缺乏序列 vs 结构的归因验证 | 模型预测难以区分序列 motif 与结构背景的贡献 | 缺乏可独立操纵序列和结构的实验平台 | MPRC 实验设计（Results 3.4） |
| 变异效应预测缺乏实验校准 | 非编码变异对 RBP 结合的影响难以从序列直接推断 | 缺乏等位基因特异性的结合测量数据 | MPRC 等位基因实验（Results 3.5） |

## 06 核心思想
1. **表面方法**：
   - 实验端：开发 ecCLIP，利用内源 split-mNeonGreen 标签进行统一亲和捕获，结合红外可视化（替代放射性）和连接酶-free 文库制备，在 HEK293T 中对 67 个 RBP 生成高分辨率结合图谱。
   - 建模端：训练 Borzuki（Borzoi 扩展）整合 ecCLIP、RNA 降解、表达和 Perturb-seq 数据；训练 Pythia 双通道网络（序列通道 + 结构通道），结构通道使用固定碱基配对卷积层。
   - 验证端：开发 MPRC 大规模平行报告基因 CLIP，在细胞内直接测量序列和结构变体对 RBP 结合的影响。

2. **核心洞察**：
   - 内源标签 + 统一捕获协议可以消除抗体差异这一最大技术变量，使图谱在 RBP 间可比。
   - RNA 结构对 RBP 结合的影响可以通过「固定碱基配对卷积核」以归纳偏置形式注入网络，无需外部结构预测工具，且可端到端训练。
   - 将模型预测分解为序列和结构两个通道的归因，可以在实验上（MPRC）验证哪些位点真正依赖结构。

3. **可能的普适教训** [Analysis]：
   - 在生物序列建模中，将领域知识（如碱基配对规则）编码为固定初始化层而非可学习参数，可以在小数据 regime 下提供强先验，同时保留下游可学习性。
   - 实验平台的设计应优先考虑「跨样本一致性」而非单样本灵敏度，因为图谱类资源的最终价值在于可比较性。
   - 将模型归因与合成报告基因实验闭环，是验证可解释性声明的有效范式。

## 07 方法总览
- **输入**：DNA 序列（393,216 bp 窗口，Borzuki）；RNA 序列（256 nt，Pythia RBP 分类）；ecCLIP 峰序列及 dinucleotide-shuffled 阴性对照。
- **输出**：Borzuki 预测 RNA 表达、降解、RBP 结合覆盖度；Pythia 输出 RBP 结合概率及序列/结构通道归因分数；MPRC 输出等位基因特异性结合效应。
- **模块**：
  1. ecCLIP 实验流程（内源标签、交联、亲和捕获、红外可视化、连接酶-free 文库制备、测序）。
  2. 峰/位点定义与阴性对照生成（dinucleotide shuffling）。
  3. Borzuki 模型（Borzoi 架构扩展，多任务训练，集成 ecCLIP、eCLIP、RNA 降解、Perturb-seq）。
  4. Pythia 模型（双通道：序列通道 + 结构通道；结构通道含固定碱基配对卷积层；DeepLIFT 归因）。
  5. MPRC 实验（合成报告基因文库、慢病毒转导、CLIP 定量）。
- **训练**：Borzuki 为集成模型（6 个副本）；Pythia 为每个 RBP 单独训练二分类器；优化器、学习率、早停等细节未在摘要中提供。
- **工具**：CTK (CLIP Tool Kit)、bowtie2、UMI-tools、RNAfold (ViennaRNA)、ESM2、DeepLIFT、scikit-learn。
- **假设**：dinucleotide-shuffled 序列可作为「未结合」阴性对照；结构通道的固定卷积可捕捉碱基配对模式；MPRC 报告基因环境可反映内源结合偏好。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ecCLIP 实验平台 | 生成 67 个 RBP 的高分辨率结合图谱 | 提供统一、可比的训练数据，替代抗体依赖的 eCLIP | 输入：内源 mNG 标签 RBP 细胞系；输出：全基因组峰及 CIMS 位点 | Results 2.1 图谱质量评估（FRiP、与 eCLIP 比较） | 移除后 Borzuki 和 Pythia 缺乏核心训练数据，无法训练 |
| 固定碱基配对卷积层（Pythia 结构通道） | 显式编码 Watson-Crick 和摆动碱基配对模式 | 为网络提供结构归纳偏置，无需外部结构预测 | 输入：one-hot RNA 序列；输出：多通道碱基配对特征图 | Results 3.1-3.3 结构分类任务及消融 | 移除后 Pythia 退化为纯序列模型，结构归因能力丧失 |
| 双通道归因（DeepLIFT） | 将预测分解为序列和结构贡献 | 识别结构依赖的 RBP 结合位点，指导实验验证 | 输入：训练好的 Pythia 模型 + 峰序列；输出：每个位点的 log2 序列/结构归因比 | Results 3.4 MPRC 验证 | 移除后无法区分序列 vs 结构依赖位点 |
| MPRC 报告基因系统 | 在细胞内定量测量序列/结构变体对 RBP 结合的影响 | 为模型归因提供正交实验验证 | 输入：合成变体文库；输出：等位基因特异性 log2(IP/input) | Results 3.4-3.5 | 移除后模型归因缺乏实验验证，可解释性声明弱化 |
| Borzuki 多任务模型 | 整合 ecCLIP、eCLIP、降解、表达、Perturb-seq 预测 RNA 命运 | 验证 ecCLIP 数据对 RNA 稳定性预测的增量价值 | 输入：DNA 序列；输出：多轨道预测 | Results 2.2-2.3 消融实验 | 移除后无法证明 ecCLIP 数据的下游效用 |

## 09 关键公式符号
- **log2 富集分数（ecCLIP 峰）**：对每个 5-mer k，计算其在峰内 20-nt 窗口 vs 侧翼背景窗口的 log2 富集。符号：\( E_k = \log_2 \left( \frac{f_{k,peak} + \epsilon}{f_{k,background} + \epsilon} \right) \)，其中 \( f \) 为频率，\( \epsilon \) 为伪计数。用途：表征 RBP 序列偏好。
- **Mantel 检验 / 修正 RV 系数**：用于比较 ESM2 蛋白嵌入距离矩阵与 ecCLIP 结合偏好距离矩阵的相关性。符号：\( \rho_{Mantel} \)、\( RV_{mod} \)。用途：评估蛋白序列相似性与 RNA 结合偏好相似性的对应关系。
- **DeepLIFT 归因**：对每个输入特征 \( x_i \)，计算其对输出 \( y \) 的贡献分数 \( \Delta y / \Delta x_i \)。本文分别对序列通道和结构通道计算归因，并取 log2 比值：\( R = \log_2 \left( \frac{\text{DeepLIFT}_{seq}}{\text{DeepLIFT}_{str}} \right) \)。用途：定义序列主导 vs 结构主导位点。
- **MPRC 效应量**：对每个构建体，计算 log2(IP/input) 作为结合强度的度量。符号：\( L_{IP/input} = \log_2 \left( \frac{IP_{norm} + \epsilon}{input_{norm} + \epsilon} \right) \)。用途：比较参考、结构保持、结构破坏、阴性对照之间的结合差异。
- **Borzuki 变异效应评分**：对参考和替代等位基因，计算预测轨道差异的加权和（方法 1 使用 Saluki 回归权重，方法 2 使用 MPRAC 参考值回归权重）。符号：\( z = \frac{1}{K} \sum_{k=1}^{K} \sum_{t=1}^{T} w_{k,t} (u^{alt}_{k,t} - u^{ref}_{k,t}) \)。用途：将多轨道预测压缩为标量变异效应。

## 10 实验设计与证据链
- **数据集/群体**：
  - ecCLIP：67 个内源 mNG 标签 RBP，HEK293T 细胞，2 个生物学重复。
  - 训练/验证/测试：按染色体划分（测试染色体未在摘要中说明）。
  - 阴性对照：dinucleotide-shuffled 峰序列。
  - MPRC：5 个 RBP（EMG1, HNRNPC, PCBP1, HNRNPU, SFPQ），30 个结构验证位点 + 88 个变异位点。
  - Borzuki 训练：14 个人类 + 11 个小鼠 RNA 降解时间序列实验，31 个 ENCODE eCLIP，11 个 ecCLIP，10 个 Perturb-seq。
- **指标**：AUROC、AUPRC、Spearman 相关、FRiP、R²、F1。
- **基线**：DeepBind、DeepSEA、GraphProt、PRIESTTESS、6 个 RNA 语言模型（RNA-FM、RiNALMo、RNA-MSM、RNAErnie、UTR-LM-MRL、UTR-LM-TE_EL）、BEACON 17 个基线。
- **评测协议**：BEACON 官方协议（CMP: Top-L precision；DMP: R²；SSP: F1；SSI: R²）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| ecCLIP 图谱质量评估 | ecCLIP 产生高分辨率、可重复的结合图谱 | FRiP 分析、峰内信号集中度、重复间相关性 | 峰中心 FRiP 曲线集中，重复间高相关 | ecCLIP 图谱质量高，适合建模 | 未与 eCLIP 在同一细胞类型中直接比较 | Results 2.1, Fig. 2a |
| RBP 结合偏好与蛋白嵌入对应 | 蛋白序列相似性与 RNA 结合偏好相关 | ESM2 嵌入距离 vs ecCLIP 5-mer 富集距离 | Mantel ρ=0.083, RV=0.110, 距离相关=0.605, P≤0.002 | 存在弱但非随机的对应 | 对应关系弱，不能用于预测 | Results 2.1, Fig. 1c |
| Borzuki 消融（有无 ecCLIP） | ecCLIP 数据提升 RNA 半衰期预测 | 有/无 ecCLIP 训练数据对比 | 加入 ecCLIP 后半衰期预测提升 | ecCLIP 携带独立于 eCLIP 的稳定性相关信息 | 未报告提升幅度 | Results 2.2, Fig. 2e |
| Pythia vs 基线（RBP 结合预测） | 结构感知架构优于序列模型 | DeepBind, DeepSEA, GraphProt, PRIESTTESS | Pythia 在 AUROC/AUPRC 上优于所有基线 | 结构归纳偏置有效 | 未报告每个 RBP 的详细比较 | Results 3.1, Fig. 3d |
| Pythia vs RNA 语言模型 | 监督结构感知模型匹敌或优于预训练嵌入 | 6 个 RNA 语言模型线性探针 | Pythia 与最强嵌入相当 | 显式结构先验可替代大规模预训练 | 预训练模型可能在小样本 RBP 上更优 | Results 3.1, Fig. 3e |
| BEACON 结构任务 | Pythia 泛化到通用 RNA 结构预测 | 17 个 BEACON 基线 | CMP Top-L 66.6%, SSP F1 71.5%，优于所有基线 | 固定碱基配对卷积是通用结构先验 | DMP/SSI 未超越最佳语言模型 | Results 3.2, Fig. 3c |
| MPRC 结构验证 | 结构归因预测可被实验验证 | 结构保持 vs 结构破坏突变 | 11/11 预测结构依赖位点显示结构保持突变保留结合 | Pythia 结构归因具有生物学真实性 | 样本量小（11 个位点） | Results 3.4, Fig. 4c |
| MPRC 变异效应 | Pythia 可预测等位基因特异性结合变化 | 88 个变异位点，预测 vs 实测 | 预测与实测效应正相关（r=0.33, P=0.0019） | 模型可优先排序功能性变异 | 相关较弱，不能作为唯一依据 | Results 3.5, Fig. 5d |

## 11 结论正确解读
- **任务范围**：本文的结论限于 HEK293T 细胞背景下的 67 个 RBP；Pythia 的 RBP 结合预测任务为二分类（峰 vs 洗牌阴性），非回归结合强度预测。
- **oracle/真值输入**：ecCLIP 峰定义为「结合」，但未验证每个峰的功能后果；阴性对照为 dinucleotide-shuffled 序列，非实验验证的未结合区域。
- **端到端状态**：Borzuki 和 Pythia 均为监督模型，依赖实验标签；Pythia 的结构通道使用固定先验，但下游权重完全从数据学习。
- **算力成本**：未提供训练时间、GPU 数量等细节。
- **历史数据依赖**：Borzuki 依赖 Borzoi 预训练权重和公开 ENCODE 数据；Pythia 依赖 ecCLIP 新数据。
- **最难情形**：预测变异效应时，相关较弱（r=0.33），且仅 24/88 变异达到显著效应；结构依赖位点的验证仅覆盖 11 个位点。
- **群体/领域边界**：结论不适用于其他细胞类型、其他 RBP 家族、体内 RNA 结构动态变化或翻译后修饰影响的场景。
- **有边界的复述**：在 HEK293T 细胞中，ecCLIP 生成的 67 个 RBP 结合图谱可提升 RNA 半衰期预测；Pythia 的固定碱基配对卷积架构在 RBP 结合预测和 RNA 结构任务上优于传统序列模型，且其结构归因在 MPRC 实验中部分验证；但变异效应预测的准确性有限，需结合实验校准。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 图谱仅覆盖 HEK293T 细胞 | 67 个 RBP 在一个细胞类型中，缺乏细胞类型特异性 | 扩展至更多细胞类型和条件 | Discussion 末段 |
| 内源标签可能影响 RBP 功能 | mNG 标签可能改变部分 RBP 的定位或结合 | 对标签敏感 RBP 进行正交验证 | Discussion 中关于标签效应的讨论 |
| Pythia 结构通道编码的是「结构潜力」而非实测结构 | 固定卷积基于序列可配对性，非实验测定的 RNA 结构 | 整合 icSHAPE 等实测结构数据 | Discussion 中关于结构表示的讨论 |
| MPRC 报告基因环境简化了天然转录本上下文 | 报告基因缺乏天然 3' UTR 的完整序列和蛋白上下文 | 在天然位点进行 CRISPR 编辑验证 | Discussion 中关于 MPRC 局限的讨论 |
| 变异效应预测相关较弱 | r=0.33，且仅部分变异达到显著效应 | 改进模型架构和训练数据规模 | Results 3.5 末段 |
| 未验证所有 RBP 的功能后果 | 峰定义为结合事件，未连接至下游调控功能 | 结合功能实验（如 RNA 稳定性、翻译） | Discussion 中关于功能验证的讨论 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 阴性对照使用 dinucleotide-shuffled 序列 | 洗牌序列可能破坏 k-mer 组成以外的特征（如密码子偏倚、poly-A 尾），导致模型学习到非特异区分特征 | 若阴性对照不具代表性，模型可能高估真实区分能力 | 使用实验验证的未结合区域（如 RNA 干扰后的下调位点）作为阴性对照 | Methods 4.5 |
| Pythia 结构通道的固定卷积核仅覆盖有限距离（d=5-24） | 长程 RNA 结构相互作用（>24 nt）未被编码 | 长程假结或远距离配对可能对某些 RBP 重要 | 扩展距离范围并比较性能 | Methods 4.13 |
| MPRC 验证仅覆盖 5 个 RBP 和 30 个位点 | 样本量小，可能无法代表 67 个 RBP 的多样性 | 结构归因的普适性声明需要更大规模验证 | 扩展 MPRC 至更多 RBP 和位点 | Results 3.4 |
| Borzuki 的 ecCLIP 消融实验未报告效应量 | 仅报告「提升」，未给出具体数值 | 无法评估 ecCLIP 数据的边际贡献大小 | 报告具体 AUROC/AUPRC 差异及置信区间 | Results 2.2 |
| ESM2 嵌入与结合偏好的对应弱（ρ=0.083） | 作者将其解释为「非随机」，但实际预测价值有限 | 该分析可能过度解读弱相关 | 使用专门训练的 RBP-RNA 共嵌入模型重新评估 | Results 2.1 |
| 变异效应预测的验证集可能偏向高置信位点 | 88 个变异位点的选择标准未详细说明 | 若选择有偏，预测性能可能被高估 | 在随机选择的变异集上评估 | Results 3.5 |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **可迁移概念：固定先验卷积层作为结构归纳偏置**。Pythia 使用冻结的碱基配对卷积核，将 RNA 二级结构先验直接编码进网络，而非依赖外部结构预测或可学习结构模块。此思路可迁移至蛋白质结构预测：例如，在序列编码器中加入冻结的接触图先验卷积层（基于已知二级结构或进化耦合），或用于蛋白质-RNA 复合物界面预测。

2. **可迁移方法：双通道架构 + 归因分解**。Pythia 将序列和结构分为两个独立通道，并通过 DeepLIFT 归因计算每个位点的「序列 vs 结构依赖比」。此设计可直接迁移至蛋白质构象采样或结合位点预测：将序列特征与结构特征（如溶剂可及性、二级结构、接触图）分离，并用量化归因识别哪些残基/区域的功能依赖结构而非序列。

3. **可迁移实验设计：合成报告基因验证模型归因**。MPRC 通过设计结构保持/结构破坏突变对，直接检验模型的结构归因预测。此闭环验证范式可迁移至蛋白质设计：对模型预测的结构关键残基，设计保守替换（结构保持）与破坏性替换（结构破坏），通过实验验证设计规则。

4. **可迁移数据策略：内源标签统一捕获**。ecCLIP 通过内源 split-mNeonGreen 标签替代抗体，消除了抗体差异这一技术变量。在蛋白质结构研究中，类似思路可应用于：统一标签系统（如 ALFA-tag）进行跨蛋白的相互作用组学比较，或用于 MD 模拟中统一力场参数的验证。

5. **可迁移建模框架：多任务整合提升泛化**。Borzuki 将 ecCLIP、eCLIP、RNA 降解、表达和 Perturb-seq 整合到单一模型，通过多任务学习共享序列表示。此框架可迁移至蛋白质结构-功能联合预测：将结构预测、稳定性预测、结合亲和力预测整合为多任务模型，利用共享表示提升各任务泛化。

6. **可迁移评估思路：外部基准 + 消融双轨验证**。作者在 BEACON 基准上评估 Pythia 的结构泛化能力，同时通过消融实验证明 ecCLIP 数据的增量价值。在蛋白质结构研究中，应同时使用外部基准（如 CAMEO、CASP）和内部消融（移除特定数据/模块）来验证新方法贡献。

7. **可迁移分析：蛋白嵌入 vs 结合偏好弱对应的警示**。ESM2 嵌入与 RNA 结合偏好的弱相关（ρ=0.083）提示：通用蛋白语言模型嵌入不能直接作为 RBP 功能相似性的代理。在蛋白质结构研究中，类似地，通用蛋白嵌入（如 ESM2）可能不足以捕捉结构或功能相似性，需使用专门训练的结构感知嵌入或实验数据校准。