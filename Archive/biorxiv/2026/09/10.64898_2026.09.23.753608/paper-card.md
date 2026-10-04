## 01 基本信息

- **标题**：AtomWeaver: Multi-Component Flow Matching with a Structured Geometric Prior Facilitates Non-Canonical Peptide Design
- **作者**：Kitaygorodsky A; Hostallero DE; Broom A; Layne E; Hwang S; Kanawaty AK; Babej T; Butterfoss GL; Fingerhuth M
- **单位**：ProteinQure Inc.（所有作者均受雇于或曾受雇于 ProteinQure Inc.）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学 + 基准评测）
- **领域**：蛋白质 inverse folding × 非天然氨基酸（NCAA）设计 × flow matching
- **关键词**：inverse folding, non-canonical amino acids (NCAAs), flow matching, geometric prior, peptide design, atom-level generation
- **DOI/arXiv**：10.64898/2026.09.23.753608
- **代码**：https://github.com/ProteinQure/atomweaver（含模型权重、推理代码、300残基参考库）；PeptideArena 基准：https://github.com/ProteinQure/peptidearena
- **数据**：未提供独立数据集下载链接（训练数据来自 PDB，具体处理见补充材料）
- **阅读日期**：2026-10-05
- **在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI 方法」中的 inverse folding 子方向，核心创新在于将残基身份（identity）从生成过程中解耦——先以 flow matching 生成原子坐标云，再在解码时通过几何匹配赋予残基身份。这使得 NCAA 的扩展不需要重训生成模型，仅需在参考库中增加一个结构模板。与 ProteinMPNN、PeptideMPNN、FAMPNN 等身份先验方法形成对比，与 NCFlow、UNAAGI 等原子级方法同属一个技术谱系。

---

## 02 一句话总结

AtomWeaver 将多肽 inverse folding 重构为坐标优先问题：以 flow matching 从嵌套壳先验（nested shell prior）生成侧链原子云（含坐标、元素、占据状态），再在解码时通过几何匹配从 300 残基参考库（20 规范 + 280 NCAA）中赋予残基身份，从而在不重训生成模型的前提下实现 NCAA 的开放词汇设计。

---

## 03 研究问题

- **具体问题**：固定骨架的 inverse folding 能否从 20 个规范氨基酸扩展到包含 NCAA 的开放词汇空间，且不需要为每个新残基重训生成模型？
- **为什么重要**：多肽治疗药物中 NCAA 可赋予蛋白酶抗性、膜通透性、药代动力学调节等性质，但现有 inverse folding 方法（ProteinMPNN、PeptideMPNN、FAMPNN 等）的输出空间被锁定在 20 个规范氨基酸上。NCAA 的引入目前依赖劳动密集的 medicinal chemistry 迭代，缺乏计算方法的系统支持。
- **现有方法不足**：
  - 基于分类的方法（ProteinMPNN 等）输出固定 20 类分布，无法表达 NCAA；
  - 潜在空间共生成方法（La-Proteina、PepGLAD、AnewOmni）虽可扩展，但 NCAA 可达性受限于训练时嵌入的覆盖范围；
  - NCFlow 需要用户预先枚举候选残基，不构成联合的位点分布；
  - UNAAGI 每次只采样一个局部侧链，不做全肽联合设计。
- **精确研究问题（Can ... ?）**：Can an atom-level generative model, conditioned only on backbone and target, produce side-chain atom clouds from which residue identity (including NCAA) can be read at decode time, without any identity information entering the trained generative state?

---

## 04 背景与发展脉络

> 注：此脉络基于本文框架 + 外部核验（标注如下）。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|---|---|---|---|---|
| 分类式 inverse folding | ProteinMPNN (Dauparas et al. 2022)、LigandMPNN、PeptideMPNN、FAMPNN | 高 WT recovery、训练稳定、推理快 | 输出空间锁定 20 类；FAMPNN 虽产坐标但身份仍为分类 | 本文明确对比对象 |
| 潜在空间共生成 | La-Proteina (Cα flow + VAE embedding)、PepGLAD（多模态扩散）、AnewOmni（block-level latent + NCAA 化学图 prompt） | 可扩展词汇、联合建模 | NCAA 可达性受嵌入训练覆盖限制；AnewOmni 需用户提供化学图 prompt | 本文的「身份不进入生成状态」与之形成关键差异 |
| 原子级局部替换 | NCFlow（固定位点打分）、UNAAGI（单侧链替换） | 原子级精度、支持 NCAA | 非全肽联合设计；NCFlow 需用户枚举候选 | 本文做全肽联合设计，且身份在解码时决定 |
| 坐标优先 + 解码时身份（本文） | **AtomWeaver** | 词汇可扩展（+1 NCAA = +1 参考结构，无重训）；身份与几何解耦；支持 D-氨基酸、β-氨基酸 | 原子几何精度受限于 flow 质量；身份读取依赖参考库质量 | — |

**本文主张的位置**：在「身份先验 vs 坐标优先」的谱系中，AtomWeaver 位于坐标优先一端——生成过程完全不接触残基身份，身份是解码时的自由选择。这使得词汇表成为推理时的属性而非训练时的属性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 固定 20 类词汇限制 | 现有 inverse folding 无法提出 NCAA | 输出层为 20 类分类分布，训练目标为 WT recovery | Introduction 第 1 段；Table 2 对比 |
| NCAA 扩展需重训 | 新残基需要重新训练模型 | 身份作为分类 token 或潜在嵌入的一部分被学习 | Introduction 第 2 段（RareFold 每残基一个 token） |
| 潜在空间 NCAA 可达性差 | 嵌入未覆盖的 NCAA 无法生成 | 潜在嵌入在训练时被规范数据主导 | Introduction 第 2 段（La-Proteina、PepGLAD、AnewOmni 的讨论） |
| 非全肽联合设计 | NCFlow、UNAAGI 只做局部替换或打分 | 方法设计上不产生全序列联合分布 | Introduction 第 2 段（NCFlow、UNAAGI 描述） |
| 原子几何误差累积 | 侧链原子离 Cα 越远误差越大 | 训练数据偏向近端原子；flow 在远端自由度上约束弱 | Results 4.1 图 2B（角度偏差随键序增加） |
| 非规范残基数据稀疏 | NCAA 在 PDB 中稀少，训练信号弱 | PDB 以 WT 蛋白为主 | Results 4.3（ withheld NCAA 零样本性能下降） |

---

## 06 核心思想

### 1) 表面方法

AtomWeaver 是一个双轨（two-track）生成模型：
- **坐标轨（coordinate track）**：以 conditional flow matching (CFM) 训练连续归一化流，将侧链原子作为无标签点云在 R³ 中从先验分布流向数据分布。先验不是各向同性高斯，而是**嵌套壳先验（nested shell prior）**——每个 slot 从以 Cα 为球心、沿骨架衍生的伪 Cβ 射线方向、具有特征半径 r_k 和厚度 σ_k 的球壳中采样。
- **元素轨（element track）**：以 absorbing masked diffusion（D3PM/SEDD 风格）在离散元素词汇 {GHOST, C, N, O, X} 上运行，其中 GHOST 表示该 slot 无原子，X 表示非 C/N/O 元素。
- **耦合机制**：两轨共享时间表 t ∈ [0, 250]，在每一步通过 FiLM 调制将 GHOST/REAL 状态注入坐标轨的每 slot 表示。GHOST slot 流向 Cα，REAL slot 流向真实坐标。
- **解码时身份读取**：采样完成后，将每个残基的预测原子云与参考库（300 残基的 rotamer 模板）做几何匹配（距离矩阵相关 + 元素/手性惩罚），输出残基身份分布。

### 2) 核心洞察

- **身份是解码时的选择，而非生成时的约束**：将「这个位置是什么残基」从生成过程中完全剥离。生成器只负责回答「这个位置的原子如何排列」，身份由几何匹配决定。这使得词汇表成为参考库的属性，而非模型权重的属性。
- **先验应该携带结构信息**：各向同性高斯先验对原子位置没有任何结构提示，导致 GHOST/REAL 决策和坐标生成必须从完全无信息的状态开始。嵌套壳先验让每个 slot 从它「应该」在的位置附近开始，把结构信息注入生成起点。
- **GHOST/REAL 是元素轨的一部分，而非独立存在轨**：将原子存在性编码为元素词汇中的一个特殊 token，使存在性决策与元素类型决策共享同一个离散扩散过程，避免额外的存在性预测头。

### 3) 可能的普适教训 [Analysis]

- **生成与识别解耦**：当目标空间（残基类型）远大于训练时可见空间时，将生成目标从识别目标中分离是一种通用策略——生成器学习物理上可行的几何，识别器在推理时匹配到任意词汇。
- **先验分布是超参数而非默认值**：flow matching 对先验分布的选择比通常认为的更敏感。嵌套壳先验的收益提示，在生成任务中，先验应该反映数据的粗粒度结构（如原子距 Cα 的典型距离），而不是无信息的高斯。
- **解码时词汇扩展**：任何「生成几何 + 匹配模板」的框架都天然支持词汇扩展——新残基只需一个参考结构，不需要重训。这对数据稀疏的化学空间（NCAA、非天然聚合物）尤其有价值。

---

## 07 方法总览

**输入**：
- 固定多肽骨架（N、Cα、C、O 原子坐标）
- 目标蛋白结构（作为上下文，通过交叉注意力和图节点直接参与）
- 每残基原子预算 K（slot 数）

**输出**：
- 每残基的身份分布（20 规范 + 280 NCAA）
- 每残基的侧链原子坐标（点云形式）

**模块**：
1. **编码器**：残基级编码器处理骨架和靶蛋白序列/结构，输出每残基上下文向量
2. **坐标轨**：SE(3)-等变 denoiser（10 个等变块），预测 CFM 速度场 v_θ(x, t)
3. **元素轨**：absorbing masked diffusion，预测元素类型分布 p_θ(e₀ | e_t, ctx)
4. **FiLM 耦合**：每步将 GHOST/REAL 状态注入坐标轨
5. **解码时读取器**：距离矩阵相关 + 元素/手性惩罚的几何匹配

**训练**：
- 三阶段：小分子预训练 → 多肽迁移 → 联合微调（含 NCAA 增强数据）
- 损失：CFM 速度场 MSE + 离散扩散交叉熵 + 辅助几何匹配损失（软版本）

**推理流程**：
1. 从嵌套壳先验采样初始原子云
2. 坐标轨和元素轨联合反向扩散 250 步
3. 对每个残基的最终原子云，与参考库 rotamer 做几何匹配
4. 输出残基身份分布

**关键假设**：
- 侧链原子数 ≤ K（原子预算）
- 参考库 rotamer 覆盖目标 NCAA 的构象空间
- 骨架固定（不做 backbone 生成）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| **嵌套壳先验** | 从以 Cα 为中心、沿伪 Cβ 射线的球壳采样初始原子位置 | 各向同性高斯对原子位置无结构提示，GHOST/REAL 决策和坐标生成需从无信息状态开始；壳先验让每 slot 从特征半径处开始 | 输入：骨架坐标、每 slot 半径 r_k、厚度 σ_k；输出：初始原子云 | Results 4.1 图 1A,B；作者称「substantially more tractable」；σ_k=0 时原子钉在射线上 | [预期] 移除后退化为高斯先验，GHOST/REAL 决策和坐标生成难度显著增加，可能降低原子计数恢复精度 |
| **SE(3)-等变 denoiser** | 在 10 个等变块中预测 CFM 速度场 | 坐标生成必须对旋转/平移等变，且需在稀疏图上传播信息 | 输入：带噪原子云 + 上下文；输出：速度场 v_θ(x, t) | Results 4.1 表 1（原子 RMSD 0.40 Å） | [预期] 替换为非等变网络将破坏坐标生成的物理合理性 |
| **元素轨（absorbing diffusion）** | 在 {GHOST, C, N, O, X} 上运行离散扩散 | 原子存在性（GHOST）和元素类型需联合决策，且需与坐标轨共享时间表 | 输入：带噪元素数组 + 上下文；输出：元素类型分布 | Results 4.1 表 1（原子计数 MAE）；Results 4.3（元素恢复） | [预期] 移除后需独立存在性预测头，增加模型复杂度且可能降低 GHOST/REAL 与坐标的耦合质量 |
| **FiLM 耦合** | 每步将 GHOST/REAL 状态调制坐标轨表示 | 坐标生成需感知哪些 slot 是真实的、哪些是 ghost | 输入：slot 表示 + GHOST/REAL 状态；输出：调制后的 slot 表示 | Results 4.1（「healthy operational coupling」） | [预期] 移除后坐标轨无法区分 ghost/real slot，原子计数恢复将显著退化 |
| **解码时几何匹配** | 将预测原子云与参考库 rotamer 匹配，输出残基身份 | 身份不进入生成状态，必须在解码时通过几何匹配赋予 | 输入：预测原子云 + 300 残基参考库；输出：残基身份分布 | Results 4.2 表 2；Results 4.3（NCAA 恢复） | [预期] 移除后无法从原子云得到残基身份，模型退化为纯几何生成器 |
| **辅助几何匹配损失** | 训练中软版本匹配，引导 flow 产生可区分的原子构型 | 纯速度场损失不保证原子云与参考 rotamer 可匹配 | 输入：预测原子云 + GT 身份；输出：软匹配损失 | Methods §S7 | [预期] 移除后生成原子云可能几何合理但无法映射到参考 rotamer |
| **三阶段训练** | 小分子预训练 → 多肽迁移 → 联合微调 | 小分子数据丰富，多肽 NCAA 数据稀疏；分阶段可充分利用数据 | 输入：各阶段数据集；输出：训练好的权重 | Methods §S10, §S14 | [预期] 移除预训练将降低 NCAA 泛化能力，尤其在 withheld 残基上 |

---

## 09 关键公式符号

> 注：原文 Methods 部分指向补充材料，以下基于正文可推断内容 + 标准 CFM 框架。

**CFM 目标**（标准形式，Lipman et al. 2023）：
L_CFM = E_{t, x₀, x_T} ‖ v_θ(x_t, t) − u_t(x_t | x₀, x_T) ‖²

- x_t = (1 − s(t)) x₀ + s(t) x_T：插值路径
- s(t)：时间表，s(0) = 0, s(T) = 1
- v_θ：学习的速度场
- u_t：条件速度场，闭式可得

**嵌套壳先验**：
x_T^(l,k) = r_k · d^(l) + σ_k · η^(l,k)，η ~ N(0, I₃)

- r_k：slot k 的特征半径（训练数据中 slot k 距 Cα 的 RMS 距离）
- d^(l)：残基 l 的伪 Cβ 单位方向（由骨架 N、Cα、C 解析计算）
- σ_k：slot k 的壳厚度（训练数据中径向方差）
- 推理时 σ_k 缩放 0.25

**元素轨（absorbing diffusion）**：
- 前向：e_t ~ q(e_t | e₀)，以概率 t/T 将已解析 token 替换为 MASK
- 反向：p_θ(e₀ | e_t, ctx)，从后验采样 e_{t−1}

**解码时匹配**：
score(c, r) = ρ(D_c, D_r) + λ_e · 1[e_c = e_r] + λ_chiral · 1[χ_c = χ_r]

- D_c, D_r：预测原子云和参考 rotamer 的距离矩阵
- ρ：相关函数
- λ_e, λ_chiral：元素和手性惩罚权重

---

## 10 实验设计与证据链

**数据集/群体**：
- 训练：PDB 子集（多肽-蛋白复合物），经聚类划分；小分子预训练数据（蛋白结合小分子）
- 评测 1（DMS）：两个多肽-靶标系统——PUMA BH3 结合 MCL1（PDB 2ROC）和环肽 CP2 结合 KDM4A（PDB 5LY1），来自 Rogers et al. 的非蛋白源 DMS 扫描
- 评测 2（PeptideArena）：12 个靶蛋白，353 个 de novo 多肽骨架（BoltzGen 生成），长度 8/16/24
- 评测 3（Hirulog-3）：PDB 1ABI，20 残基凝血酶抑制剂

**指标**：
- WT recovery（规范残基恢复率）
- 与 DMS 实验 ΔΔG 的 Spearman 相关（符号反转，越大越好）
- 自洽性 RMSD（scRMSD，<2Å 和 <5Å 阈值）
- pDockQ2（界面置信度）
- NCAA 恢复率（按残基类别分层）

**基线**：
- ProteinMPNN、PeptideMPNN、ESM-IF1 (causal)、LM-Design、FAMPNN（规范残基比较）
- NCFlow（NCAA 比较，参考性）

**评测协议**：
- DMS：单点突变，每个位置独立打分，与实验 ΔΔG 比较
- PeptideArena：每个骨架采样 10 个序列设计，用 OpenDDE 重折叠，计算 scRMSD
- Hirulog-3：从固定复合物生成原子云，用 AtomWeaver-open（300 残基）和 AtomWeaver-DBeta（43 残基：20 规范 + 19 D-氨基酸 + 4 β-氨基酸）读取身份

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| DMS 单点（CAA-only） | 规范残基排名与实验功能一致 | AtomWeaver-open vs ProteinMPNN/PeptideMPNN/ESM-IF1/LM-Design/FAMPNN | AtomWeaver-open 数值最高（0.274 等权平均） | 坐标优先方法在规范残基排名上不逊于分类方法 | 差异未做统计显著性检验；置信区间重叠 | Results 4.5 表 3 |
| DMS 单点（CAA+NCAA） | 混合残基排名 | AtomWeaver-DMS vs AtomWeaver-open | AtomWeaver-DMS 在所有列数值最高 | 针对实验残基集定制的读取器优于通用 300 残基读取器 | 非零样本场景；读取器拟合了 DMS 残基集 | Results 4.5 表 3 |
| PeptideArena 自洽性 | de novo 骨架上的序列设计可重折叠 | 8 方法 × 353 骨架 × 10 采样 | AtomWeaver 与基线相当；<5Å 成功率最高 | 坐标优先方法在自洽性上不牺牲 | scRMSD 是计算指标，非实验验证 | Results 4.4 图 3A |
| NCAA 多样性 | 开放词汇产生多样 NCAA 设计 | AtomWeaver-open 在 PeptideArena 上 | 168 种独特 NCAA，覆盖 60% 允许集；中位 2 NCAA/序列 | 开放词汇确实被利用，非装饰性 | 未验证这些 NCAA 设计的实验功能 | Results 4.4 图 3B |
| 零样本 NCAA | withheld 残基可被提出 | 6 种 withheld NCAA | 中位百分位 ≈63 | 零样本 NCAA 恢复可行但有限 | 远低于 seen NCAA（95.7 百分位） | Results 4.3 补充表 S2 |
| Hirulog-3 恢复 | 临床相关多肽的 NCAA 恢复 | AtomWeaver-open vs AtomWeaver-DBeta | DBeta 读取器恢复 HMR 和 DPN 更好 | 聚焦读取器对已知化学更有效 | 单案例，非泛化结论 | Results 4.6 补充图 S5 |
| Hirulog-3 类似物 | 开放词汇产生可解释设计 | AtomWeaver-open 联合设计 | β-高色氨酸替换 HMR，Asn-Arg-Asp 基序，D-Ala 引入 | 开放词汇可产生结构可解释的协同设计 | 未实验验证；pDockQ2 是预测置信度 | Results 4.6 图 4 |

---

## 11 结论正确解读

**任务范围**：
- 本文解决的是**固定骨架**的侧链设计（inverse folding），不涉及 backbone 生成或环区设计。
- 多肽长度限制为 ≤32 残基（训练语料上限）。
- 靶标为蛋白质（非核酸、非膜环境）。

**输入/真值依赖**：
- 需要固定的多肽骨架和目标蛋白结构作为输入。
- DMS 基准使用实验测定的 ΔΔG 作为真值；PeptideArena 使用 OpenDDE 重折叠作为自洽性代理。
- 身份读取依赖参考库 rotamer 质量；rotamer 用 RDKit 构建。

**端到端状态**：
- 本文是计算方法论文，**无湿实验验证**。所有结论基于计算指标（recovery、scRMSD、pDockQ2、DMS 相关性）。
- 「设计」指序列建议，非合成或功能验证。

**算力成本**：
- 未提供训练/推理的具体算力数据。
- 推理时需为每个残基匹配 300 个 rotamer 模板，计算成本与词汇表大小线性相关。

**历史数据依赖**：
- 训练数据来自 PDB，以 WT 蛋白为主，可能继承 PDB 的偏差（如可溶性蛋白偏好、晶体构象偏好）。
- NCAA 数据通过合成增强生成，非实验来源。

**最难情形**：
- 零样本 NCAA（训练中从未见过的残基）恢复率显著低于 seen NCAA（中位百分位 63 vs 95.7）。
- 芳香环（需多原子协同排列）和长侧链（远端原子误差累积）是几何生成的主要挑战。
- 溶剂暴露位点的身份不确定性最高（recovery ≈0.13）。

**有边界的复述**：
AtomWeaver 在计算层面证明了「坐标优先 + 解码时身份」的 inverse folding 范式可行：在规范残基的 DMS 功能排名上与现有方法相当，在 NCAA 开放词汇上提供了无需重训的扩展路径，并在 de novo 骨架上保持了自洽性。但该方法尚未经过实验验证，其 NCAA 设计的实际功能性和可合成性未知；零样本 NCAA 恢复仍是短板；所有结论限于 ≤32 残基的固定骨架多肽-蛋白复合物。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 原子几何误差随键距累积 | 侧链远端原子角度偏差约为近端的两倍；芳香环组装困难 | 直接惩罚角度误差的损失函数；更平衡的训练数据 | Results 4.1 图 2B,C；Discussion |
| 零样本 NCAA 恢复有限 | 6 种 withheld NCAA 中位百分位 ≈63，远低于 seen NCAA 的 95.7 | 改进参考库构建；更好的 rotamer 覆盖 | Results 4.3；补充表 S2 |
| 多肽长度限制 | 训练语料上限 32 残基 | 扩展训练语料 | Discussion（「Peptide length is capped at 32 residues」） |
| X 元素类别模糊 | X 作为非 C/N/O 的统称，无法区分硫、磷、卤素 | 未来版本增加元素类别判别 | Discussion（「sparse data coverage preventing confident separation」） |
| 计算指标未经实验验证 | 所有结论基于 recovery、scRMSD、pDockQ2 等计算指标 | 湿实验验证 NCAA 设计的合成与功能 | Discussion（「not experimentally validated analogues」） |
| 读取器非零样本 | DMS 基准中的 AtomWeaver-DMS 读取器拟合了实验残基集 | 真正的零样本读取器 | Results 4.5（「does not imply that the discriminative readout itself is zero-shot」） |

**作者提及的相关约束**（非正式局限）：
- 所有作者受雇于 ProteinQure Inc.，存在利益冲突。
- PeptideArena 基准为本文新引入，未经第三方独立验证。
- 与 baselines 的比较使用了不同的采样/解码协议（baselines 为分类分布采样，AtomWeaver 为几何匹配），严格可比性有限。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| DMS 基准中 AtomWeaver 的数值优势未做统计显著性检验 | 置信区间重叠；位点数量有限（39 位点） | 数值优势可能是噪声 | 自助法重采样或更多 DMS 数据集 | Results 4.5；补充表 S5 |
| 与 baselines 的比较协议不对称 | baselines 输出分类分布，AtomWeaver 输出几何匹配；baselines 的 T=1.0 采样可能不是其最优配置 | 比较公平性影响结论强度 | 对 baselines 做超参数扫描；统一评估协议 | Results 4.5；Methods §S17 |
| 「嵌套壳先验贡献」缺乏消融实验 | 作者称先验使优化「substantially more tractable」，但未提供量化消融（如高斯先验 vs 壳先验的 recovery 对比） | 核心创新点的证据强度不足 | 运行高斯先验对照实验，比较收敛速度和最终指标 | Discussion（「ablations ... are ongoing」） |
| 零样本 NCAA 的「零样本」定义有限 | 6 种 withheld NCAA 的 rotamer 仍由 RDKit 构建并加入参考库；模型虽未见过其身份标签，但参考库包含其几何 | 真正的零样本应连 rotamer 也不提供 | 测试完全不提供 withheld NCAA rotamer 的场景 | Results 4.3；补充表 S2 |
| PeptideArena 基准的区分度 | 8 种方法在 scRMSD 上高度一致；区分度主要来自 <5Å 成功率的细微差异 | 基准可能不足以区分方法优劣 | 增加更难的靶标/更长的多肽；引入实验验证 | Results 4.4 图 3A |
| 读取器与生成器的耦合度未量化 | 读取器是 logistic regression + 几何匹配的简单组合；更复杂的读取器（如学习式）可能显著提升性能 | 读取器可能是性能瓶颈 | 替换读取器为学习式模型，比较 DMS 相关性 | Methods §S5 |
| 训练数据中 NCAA 的分布未知 | 作者称「synthetic NCAA-augmented」数据，但未报告 NCAA 类型和数量的分布 | 数据分布决定泛化边界 | 报告训练数据中 NCAA 的详细分布 | Methods §S10, §S14（未提供细节） |
| 计算成本未报告 | 训练和推理的具体算力需求未提供 | 影响方法的实际可用性评估 | 报告训练时间、GPU 数量、推理延迟 | 全文未提供 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移的概念

1. **身份-几何解耦（Identity-Geometry Decoupling）**：将「残基是什么」从「原子如何排列」中分离。生成器只建模几何，身份由解码时的参考库匹配决定。这一范式可迁移到任何「生成结构 → 赋予身份」的任务，如核酸适体设计（碱基身份 vs 原子坐标）、配体设计（原子类型 vs 坐标）。

2. **结构化先验（Structured Prior）**：flow matching 的先验不必是各向同性高斯。嵌套壳先验利用「原子距 Cα 的典型距离」这一粗粒度结构信息，让每个 slot 从信息量更高的起点开始。这提示：**先验应编码数据的粗粒度几何约束**，而非默认无信息分布。可迁移到 loop 建模（先验从 Ramachandran 偏好区域采样）、侧链 packing（先验从 rotamer 库采样）。

3. **解码时词汇扩展（Decode-time Vocabulary Expansion）**：新残基 = 一个新参考结构 + 读取器重拟合，不触碰生成模型权重。这一「词汇是库的属性而非权重的属性」的思想，可迁移到任何数据稀疏的化学空间扩展任务。

4. **双轨耦合（Two-Track Coupling）**：连续坐标轨和离散元素轨共享时间表，通过 FiLM 在每步耦合。这种「连续 + 离散联合生成」的架构可迁移到其他需要同时决定「有无/类型」和「位置」的生成任务。

### 可迁移的方法

1. **伪 Cβ 射线（Pseudo-Cβ Ray）**：从骨架 N、Cα、C 解析计算 Cβ 位置，作为侧链方向的先验锚点。这一几何构造不依赖侧链身份，可迁移到任何基于骨架的侧链生成任务。

2. **辅助几何匹配损失（Auxiliary Geometric Matching Loss）**：训练中引入软版本的距离矩阵匹配损失，引导 flow 产生可区分的原子构型，但不作为采样时的条件。这种「训练时引导、推理时自由」的策略可迁移到其他生成-匹配联合任务。

3. **PeptideArena 基准设计**：用 BoltzGen 生成 de novo 骨架，用 OpenDDE 重折叠计算 scRMSD，以靶标对齐方式测量多肽-蛋白复合物的自洽性。这一「生成 → 重折叠 → 对齐 → 评分」的流程可迁移到任何多肽/蛋白设计方法的评估。

4. **读取器组合策略**：几何匹配（距离矩阵相关）为主 + 学习式组件（logistic regression）为辅，按残基类别混合权重。这种「可解释几何 + 数据驱动」的混合评分可迁移到其他结构-序列映射任务。

### 对课题方向的启示

- **对 inverse folding 研究**：本文提供了一个「坐标优先」的替代范式，与「身份优先」的分类方法形成互补。可探索将两者结合——用分类方法提供先验分布，用坐标优先方法探索分类方法无法表达的化学空间。
- **对 NCAA 设计**：本文的「参考库 + 解码时匹配」框架是 NCAA 设计的高效路径，但零样本性能仍是瓶颈。可探索更好的 rotamer 库构建（如用生成模型预测 NCAA rotamer）或读取器架构（如图神经网络匹配）。
- **对 MD/对接研究**：嵌套壳先验的思想可迁移到 MD 模拟的初始构象采样——从 rotamer 库或已知构象的壳分布中采样，而非均匀随机。
- **对 AlphaFold 类方法**：本文的「身份不进入生成状态」与 AlphaFold 的「序列 → 结构」方向相反。可探索「结构 → 序列」的逆问题是否也能从身份-几何解耦中受益。