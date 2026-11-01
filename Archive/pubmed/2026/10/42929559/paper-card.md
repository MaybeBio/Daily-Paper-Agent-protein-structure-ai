## 01 基本信息
- **标题**: Mapping Functional Transitions across Protein Homologues from a Single Simulation: Application of gEDES-HM to Adenylate Kinases
- **作者**: Kurt, Han; Athar, Mohd; Basciu, Andrea; Reys, Victor; Bonvin, Alexandre M J J; Vargiu, Attilio V
- **单位**: 未提供（根据致谢推测涉及意大利 University of Cagliari、Angelini Pharma、荷兰 Utrecht University 等，但原文未明确列出单位列表）
- **期刊/平台**: Journal of Chemical Information and Modeling
- **年份**: 2026（在线日期 2026-10-26）
- **论文类型**: 方法学验证研究
- **领域**: 蛋白质构象采样 × 同源建模 × 集合对接
- **关键词**: gEDES-HM, enhanced sampling, homology modeling, ensemble docking, adenylate kinase, metadynamics, conformational ensemble transfer
- **DOI/arXiv**: 10.1021/acs.jcim.6c02521
- **代码**: 未提供
- **数据**: 22 个 ADK 同源物结构（PDB），26 个蛋白-配体复合物；PDB ID 列表见原文 Table 1（未在摘要中列出）
- **阅读日期**: 2026-10-26
- **在本课题方向中的位置**: 该文属于「蛋白质结构相关计算研究 × 物理模拟（增强采样）+ 同源建模 + 对接」交叉方向，核心贡献在于将单一蛋白的增强采样构象集合通过同源建模迁移至整个蛋白家族，避免对每个同源物单独进行昂贵模拟，属于构象集合迁移/共享策略的代表性工作。

## 02 一句话总结
该文提出 gEDES-HM 协议，利用 gEDES 增强采样（metadynamics）对单一参考蛋白（E. coli ADK）生成多样化构象集合，通过多模板同源建模将该集合迁移至 22 个 ADK 同源物，并在 26 个蛋白-配体复合物上以 HADDOCK3 集合对接验证，成功复现 92% 复合物的近天然结合模式。

## 03 研究问题
- **具体问题**: 能否将单一蛋白通过增强采样获得的构象集合（含配体结合态/类结合态）迁移至同源家族成员，从而避免对每个同源物分别进行昂贵的增强采样模拟？
- **为什么重要**: 蛋白质功能依赖构象集合而非单一结构；同源蛋白家族成员众多，逐一进行增强采样计算成本极高；若构象集合可迁移，则能大幅加速家族尺度的构象-功能关系研究和基于结构的药物发现。
- **现有方法不足**: (1) AI 生成式方法（如 AlphaFlow、BioEmu、Str2Str）受限于训练数据多样性，常低估高能区域和谱系特异性状态，且缺乏物理热力学精度；(2) 传统 MD 增强采样虽物理上严谨，但计算成本高，难以在家族尺度推广；(3) 传统同源建模通常使用单一静态模板，丢失构象多样性。
- **精确研究问题**: Can a conformational ensemble generated from enhanced sampling of a single reference protein be transferred to homologous family members via multi-template homology modeling, such that the resulting ensembles contain binding-competent conformations sufficient for native-like docking pose recovery?

## 04 背景与发展脉络
*（标注：以下脉络部分基于本文框架，部分经外部核验，具体见各条目）*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 静态结构预测 | AlphaFold2 等 | 单结构精度高 | 输出单一构象，忽略构象集合 | 本文不依赖单结构，而是利用构象集合 |
| 构象集合生成（AI） | AlphaFlow, BioEmu, Str2Str | 可生成多样构象 | 受训练数据限制，高能态/稀有态欠采样，缺乏物理热力学一致性 | 本文采用物理增强采样（metadynamics），保留热力学信息 |
| 构象集合生成（物理） | MD, metadynamics, gEDES | 物理严谨，可采样功能相关构象 | 计算成本高，难以家族尺度推广 | 本文核心：将单一蛋白的 gEDES 集合迁移至家族 |
| 同源建模 | MODELLER 单模板 | 简单快速 | 单模板丢失构象多样性 | 本文使用 101 个构象模板的多模板同源建模 |
| 集合对接 | HADDOCK3 等 | 利用受体柔性 | 需要高质量构象集合 | 本文验证迁移集合在对接中的有效性 |

*（注：AI 方法局限性的描述来自本文 Introduction 的作者主张，经外部核验部分——AlphaFold2 输出单结构、MD 计算成本高——为领域共识。）*

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 构象集合生成成本高 | 每个蛋白需独立增强采样模拟 | 增强采样计算昂贵，家族尺度不可行 | Introduction: "removing the need to perform individual simulations for all of them and thus speeding up the whole process by orders of magnitude" |
| AI 方法欠采样功能相关状态 | 高能态、谱系特异性状态缺失 | 训练数据多样性有限，缺乏物理约束 | Introduction: "constrained by the conformational diversity of their training data, often underrepresenting high-energy regions... lack the physical rigor" |
| 传统同源建模丢失构象多样性 | 单模板只能生成单一构象 | 静态模板无法反映构象集合 | Introduction: "Traditional homology modeling typically uses a single static template structure, potentially missing the conformational diversity essential for function" |
| 构象集合与功能关联难建立 | 集合中哪些构象是功能相关的难以判断 | 需要实验结构或对接验证 | 本文通过 26 个实验复合物验证迁移集合的功能相关性 |
| 同源物间构象差异 | 不同同源物可能具有不同功能状态 | 谱系特异性演化、配体差异 | "both failures reported here belong to the AK3-type GTP:AMP phosphotransferases, that is to the subfamily whose triphosphate substrate differs from that of the reference enzyme" |

## 06 核心思想

### 1) 表面方法
gEDES-HM 是一个三阶段流水线：(a) 对单一参考蛋白（E. coli ADK 无配体 apo 态）运行 gEDES 增强采样（metadynamics 偏置口袋形状和体积描述符）；(b) 从轨迹中提取 101 个构象聚类代表，作为多模板库；(c) 对每个同源物，以这 101 个构象为模板进行多模板同源建模（MODELLER），生成每个同源物的 101 个构象集合，用于 HADDOCK3 集合对接。

### 2) 核心洞察
**构象集合可迁移性**：蛋白质家族的构象空间（尤其是配体结合相关的口袋形状变化）在进化上保守，即使序列同一性低至 30%，单一参考蛋白的增强采样构象集合仍能覆盖家族成员的功能相关构象。关键在于：不是迁移单个结构，而是迁移整个构象多样性谱。

### 3) 可能的普适教训 [Analysis]
- **集合优于单点**：在结构预测和对接中，构象集合比任何单一结构（无论多精确）都更能捕捉功能相关状态。
- **物理采样 + 同源建模的组合**：物理增强采样提供热力学上合理的构象多样性，同源建模将其映射到序列不同的同源物上，两者互补——前者保证物理合理性，后者保证序列可迁移性。
- **"参考蛋白"策略**：在家族中选择一个代表性成员进行昂贵计算，其余成员通过映射获得构象集合，这种"计算一次、迁移多次"的策略可推广到其他蛋白家族。
- **选择瓶颈**：本文指出 DOPE 全局打分可能丢弃口袋局部最优的模型，提示在构象选择中需要局部（口袋级）与全局（全蛋白级）标准的平衡。

## 07 方法总览

**输入**：
- 参考蛋白：E. coli ADK apo 结构（PDB: 4AKE）
- 目标同源物：22 个 ADK 同源物序列（UniProt 获取），26 个蛋白-配体复合物实验结构（验证用）
- 配体：各复合物中的底物/抑制剂（AMP、ADP、AP5、G5P、GP5 等）

**输出**：
- 每个同源物的 101 构象集合（HMgEDES）
- 每个复合物的对接 pose 集合及 RMSD 评估

**模块**：
1. **gEDES 增强采样**：对 4AKE 运行 metadynamics，偏置口袋形状和体积描述符，生成多样化构象轨迹
2. **构象聚类**：从轨迹中提取 101 个最大化多样性的构象代表
3. **多序列比对**：Clustal Omega 进行目标序列与参考序列的比对
4. **多模板同源建模**：MODELLER v10.6，AutoModel 类，VTFM 优化，101 个模板 × 10 个随机种子 = 1010 模型/靶标
5. **模型选择**：DOPE 打分，每个模板选最优模型 → 101 模型/靶标
6. **集合对接**：HADDOCK3 v2026.3.0，配体保持实验构象（刚性），受体为 101 构象集合，ambiguous interaction restraints 基于实验结合位点残基
7. **评估**：RMSD_BS（结合位点重原子）、RMSD_prot（Cα）、RMSD_lig（配体）、RMSD_BM（结合模式）、F_nat（天然接触分数）

**流程**：
```
4AKE (apo) → gEDES metadynamics → 轨迹 → 聚类 → 101 构象模板
    ↓
22 个同源物序列 → 多序列比对 → MODELLER 多模板建模 → 101 模型/靶标
    ↓
DOPE 选择 → HMgEDES 集合 → HADDOCK3 集合对接 → RMSD 评估
```

**关键假设**：
- 参考蛋白的构象空间覆盖家族功能相关构象
- 同源物具有与参考蛋白相同的结构域组织（构象迁移的前提）
- 配体在对接中保持实验构象（评估受体模型质量，而非配体柔性）

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| gEDES 增强采样 | 生成参考蛋白的多样化构象集合 | 标准 MD 无法在可行时间内采样开放/闭合转变 | 输入：4AKE apo 结构；输出：构象轨迹 | 作者前期工作（引用 ref）；本文图 2 显示构象覆盖开放到闭合区间 | [预期] 移除后无构象多样性，同源建模只能生成单一构象，对接无法捕捉结合态 |
| 构象聚类 | 从轨迹中提取 101 个代表性构象 | 减少冗余，保证模板多样性 | 输入：轨迹；输出：101 构象 | Methods 节描述 | [预期] 聚类过粗会丢失中间态，过细则模板冗余增加计算量 |
| 多序列比对 | 建立参考与目标序列的残基对应关系 | 同源建模需要序列-结构比对 | 输入：目标序列 + 参考序列；输出：比对 | Methods 节：Clustal Omega | [预期] 比对错误直接导致建模错误，尤其影响口袋残基映射 |
| 多模板同源建模 | 将参考构象集合映射到目标序列 | 核心迁移步骤 | 输入：101 模板 + 比对；输出：1010 模型/靶标 | Methods 节：MODELLER AutoModel | [预期] 移除后无法生成同源物构象集合，整个协议失效 |
| DOPE 打分选择 | 每个模板选最优模型 | 过滤低质量模型 | 输入：1010 模型；输出：101 模型/靶标 | Methods 节 | [实测] 作者指出 DOPE 可能丢弃口袋局部最优模型（见 Limitations），但整体仍有效 |
| HADDOCK3 集合对接 | 验证构象集合的对接能力 | 评估迁移构象的功能相关性 | 输入：101 构象 + 配体 + 结合位点残基；输出：pose 集 | Results 图 3、表 S6 | [预期] 移除后无法评估构象集合的功能价值 |
| 构象集合投影分析 | 将构象投影到 (d1,d2) 和 (θ1,θ2) 坐标 | 验证构象覆盖范围 | 输入：构象集合；输出：投影图 | Results 图 2、S2、S3 | [预期] 移除后无法定量评估构象多样性 |

## 09 关键公式符号

本文核心方法为计算流程而非数学公式，未提供显式方程。以下为隐含的关键定义：

1. **d₁, d₂（质心距离）**：
   - d₁ = LID 域与 CORE 域质心间距离
   - d₂ = NMP 域与 CORE 域质心间距离
   - 残基范围：LID 118–160，NMP 30–67，CORE 1–29/68–117/161–214（E. coli 编号）

2. **θ₁, θ₂（域间角度）**：
   - θ₁ = LID(123–155)、hinge(161–165)、CORE(1–8, 79–85, 104–110, 190–198) 三质心形成的角
   - θ₂ = NMP(50–59)、CORE、hinge 三质心形成的角
   - 定义来自 Beckstein et al. 和 Li et al.

3. **RMSD 指标**：
   - RMSD_BS：结合位点重原子 RMSD（结合位点残基 = 实验结构中距配体 3.5 Å 内的残基）
   - RMSD_BM：结合位点 + 配体重原子的联合 RMSD
   - RMSD_lig：配体重原子 RMSD（无叠加）
   - RMSD_prot：全蛋白 Cα RMSD

4. **F_nat**：天然接触分数（native contacts fraction），对接 pose 中重现实验复合物残基-配体接触的比例

5. **Spearman 秩相关系数 ρ**：用于评估 RMSD_BS 与 productive conformer 数量之间的相关性（ρ = −0.86, p = 1.8 × 10⁻⁸）

## 10 实验设计与证据链

**数据集**：
- 22 个 ADK 同源物，序列同一性 31%–99%（相对 E. coli ADK）
- 26 个蛋白-配体复合物（部分同源物含多个配体复合物）
- 配体类型：AMP、ADP、AP5（二腺苷五磷酸）、G5P、GP5 等
- 参考蛋白：E. coli ADK（4AKE，apo 开放态；1AKE，holo 闭合态）

**基线/对照**：
- HM4AKE(apo)：以实验 apo 结构为单一模板的同源建模
- HM1AKE(holo)：以实验 holo 结构为单一模板的同源建模
- HOLOexpt：配体对接回自身实验 holo 受体（上限基准）

**评测协议**：
- 建模阶段：DOPE 打分选择
- 对接阶段：HADDOCK3 刚性配体对接，ambiguous interaction restraints 基于实验结合位点
- 成功标准：RMSD_BM ≤ 2.5 Å 视为天然结合模式恢复
- 统计：Spearman 相关性分析

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| gEDES 构象集合覆盖分析 | gEDES 采样覆盖开放到闭合转变 | 投影到 (d1,d2) 和 (θ1,θ2)，对比 4AKE/1AKE 实验结构 | 构象覆盖 17.5–32.0 Å (d1)，17.5–22.1 Å (d2)；θ₁ 55.9–120.9°，θ₂ 28.0–67.1° | gEDES 集合包含开放、闭合及中间态 | 不代表热力学权重正确（作者明确说明是 biased selection） | Results 图 2 |
| HMgEDES 集合建模 | 多模板同源建模可生成结合位点构象 | 对比 HM4AKE(apo) 和 HM1AKE(holo) | 22/26 复合物获得 RMSD_BS ≤ 2.5 Å 的模型 | 迁移构象集合可覆盖同源物结合态 | 不能证明对所有蛋白家族有效 | Results 图 3、表 S2 |
| HADDOCK3 集合对接 | 迁移构象可用于天然结合模式恢复 | HMgEDES vs HM4AKE(apo) vs HM1AKE(holo) vs HOLOexpt | 24/26 复合物获得 RMSD_BM ≤ 2.5 Å（HMgEDES）；HM4AKE(apo) 仅 2/26；HM1AKE(holo) 24/26；HOLOexpt 25/26 | HMgEDES 与 HM1AKE(holo) 相当，远优于 HM4AKE(apo) | HMgEDES 未超过 HOLOexpt（中位 RMSD_BM 2.1 Å vs 0.6 Å） | Results 图 3、表 S6 |
| 序列同一性 vs 成功率 | 迁移效果不依赖高序列同一性 | 按序列同一性分层分析 | 成功率与序列同一性无显著相关（图 S6） | 构象迁移在低同一性（~30%）下仍有效 | 样本量有限（22 个同源物） | Results 图 S6 |
| 失败案例分析 | 识别协议边界 | 系统 12、14 详细分析 | 两系统 RMSD_BS 最大；F_nat 仍较高（0.75、0.74） | 失败源于口袋局部构象偏差而非配体错位 | 无法区分是采样不足还是建模误差 | Results "Analysis of Unsuccessful Cases" |
| productive conformer 数量 vs RMSD_BS | 结合位点模型质量决定对接成功 | Spearman 相关分析 | ρ = −0.86, p = 1.8 × 10⁻⁸ | 结合位点保真度是对接成功的关键预测因子 | 相关性不等于因果 | Results 节 |

## 11 结论正确解读

**任务范围**：
- 仅验证于 ADK 家族（22 个同源物，26 个复合物），该家族以大规模域运动（LID/NMP 开闭）为特征
- 仅测试了配体保持实验构象的刚性对接，未测试柔性配体对接或虚拟筛选富集
- 仅使用无配体 apo 态参考蛋白（4AKE）的 gEDES 轨迹

**oracle/真值输入**：
- 对接使用了实验结合位点残基信息（ambiguous interaction restraints），这在实际前瞻性应用中可能未知
- 配体坐标来自实验结构（非对接预测）
- 评估基于实验复合物结构

**端到端状态**：
- 协议并非全自动端到端：需要实验结合位点知识、配体坐标、人工检查
- 从序列到功能构象的完整流程中，对接步骤依赖先验知识

**算力成本**：
- 作者声称"orders of magnitude"加速，但未提供具体基准测试数据
- 实际成本：1 次 gEDES 模拟（参考蛋白）+ 22 个同源物 × 1010 次同源建模 + 26 个复合物 × 101 构象对接

**历史数据依赖**：
- 依赖参考蛋白的 gEDES 轨迹（需预先计算）
- 依赖 UniProt 序列、PDB 结构

**模型依赖**：
- 依赖 MODELLER 的同源建模精度
- 依赖 HADDOCK3 的打分函数
- 依赖 DOPE 统计势的选择能力

**最难情形**：
- 短型 ADK（系统 15–20，缺失 63–72% LID 残基）：productive conformer 数量最少
- 系统 12、14：结合位点构象偏差最大，无法恢复天然结合模式
- 不同底物特异性亚家族（AK3 型 GTP:AMP 磷酸转移酶）：参考蛋白构象可能不覆盖

**群体/领域边界**：
- 结论仅对 ADK 家族有效，作者明确声明扩展到其他家族需验证
- 适用于以域运动为主的蛋白；对以局部侧链重排为主的蛋白可能不适用
- 要求同源物具有与参考蛋白相同的结构域组织

**不确定性**：
- 未提供置信区间或统计显著性检验（除 Spearman 相关性）
- 成功率（92%）基于单一阈值（RMSD_BM ≤ 2.5 Å），未报告分布宽度
- 未报告阴性对照（如随机构象集合的对接成功率）

**有边界的复述**：gEDES-HM 在 ADK 家族中，利用单一参考蛋白的增强采样构象集合，通过多模板同源建模和集合对接，能够为 92% 的测试复合物恢复天然结合模式，其效果与使用实验 holo 结构作为模板相当，且不依赖高序列同一性；但该结论受限于 ADK 家族、刚性配体对接、实验结合位点先验知识等条件。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 假设参考蛋白构象覆盖同源物相关状态 | "The protocol assumes that the conformational states relevant to every homologue are already represented in the reference ensemble" | 未明确提及 | "Analysis of Unsuccessful Cases and Limitations" 节 |
| 谱系特异性功能状态可能缺失 | 系统 12、14 属于 AK3 型 GTP:AMP 磷酸转移酶，底物与参考蛋白不同 | 未明确提及 | 同上 |
| 构象多样性依赖结构域保守性 | "The conformational diversity sampled across the reference ensemble is transferred to family members only insofar as they possess the domains whose motion generates that diversity" | 未明确提及 | 同上 |
| 短型 ADK 的 LID 缺失导致迁移受限 | 系统 15–20 缺乏 63–72% LID 残基，productive conformer 最少 | 未明确提及 | 同上 |
| 无 Mg²⁺ 的模拟条件 | gEDES 模拟在无 Mg²⁺ 条件下进行，而生理反应需要该离子 | "The inclusion of Mg²⁺ (and more generally, additional cofactors) in gEDES simulations will be addressed in follow-up projects" | 同上 |
| 选择步骤的脆弱性 | DOPE 全局打分可能丢弃口袋局部最优的模型 | "Future versions of the workflow could therefore combine global model quality with local criteria, such as pocket geometry, side-chain packing, and binding-site stereochemistry, in a pocket-aware or multicriteria selection score" | Concluding Remarks |
| 仅验证于单一蛋白家族 | "Validated so far within a single family" | 未明确提及，但暗示需跨家族验证 | Abstract / Concluding Remarks |
| 对接需要结合位点先验知识 | 使用了实验结合位点残基信息 | 提及可自动检测口袋（引用前期工作） | Methods / Concluding Remarks |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 92% 成功率可能受限于评估标准 | RMSD_BM ≤ 2.5 Å 阈值较宽松；F_nat 较高但未报告分布 | 成功率可能高估实际对接精度 | 使用更严格阈值（如 ≤ 1.0 Å）重新评估；报告 RMSD 分布而非仅二值化 | Results 节 |
| 使用实验结合位点残基作为 restraints 可能引入偏差 | 前瞻性应用中结合位点未知，需自动预测 | 实际应用效果可能低于论文报告 | 使用自动口袋预测工具（如 FPocket）替代实验信息重跑 | Methods 节 |
| 未与 AI 生成式构象采样方法直接对比 | 论文仅与实验结构模板对比，未与 AlphaFlow/BioEmu 等对比 | 无法判断 gEDES-HM 相对 AI 方法的优劣 | 在相同数据集上运行 AI 方法并对比构象质量和对接成功率 | Introduction 提及但未对比 |
| 无 Mg²⁺ 条件可能影响构象集合质量 | 作者承认此局限，但未评估影响程度 | 金属离子可能影响结合位点构象 | 在含 Mg²⁺ 条件下重跑 gEDES 并对比结果 | Limitations 节 |
| 构象多样性来源单一（仅一个参考蛋白） | 若参考蛋白本身构象空间有限，迁移效果受限 | 选择多个参考蛋白可能提高覆盖 | 使用多个参考蛋白（如不同亚家族代表）生成构象集合并对比 | 未提及 |
| DOPE 选择可能系统性偏向某些构象 | 作者承认 DOPE 可能丢弃口袋最优模型，但未量化 | 选择策略影响下游对接效果 | 对比不同选择策略（DOPE vs 口袋局部打分）的对接成功率 | Limitations 节 |
| 未报告计算成本的具体数据 | 声称"orders of magnitude"加速但无数值 | 无法评估实际性价比 | 提供 CPU/GPU 时间对比（gEDES-HM vs 直接增强采样） | 全文未提供 |
| 同源物选择可能存在选择偏差 | 22 个同源物是否代表 ADK 家族多样性未明确 | 可能高估泛化能力 | 在更广泛、更偏远的同源物上测试 | Table 1 未在摘要中展示 |

## 14 学到什么

**Agent 提炼的知识候选**

### 可迁移概念
1. **构象集合迁移（Ensemble Transfer）**：单一参考蛋白的增强采样构象集合可通过同源建模迁移至家族成员，避免重复昂贵模拟。适用于本课题中任何需要多同源物构象集合的场景（如家族规模的虚拟筛选、突变效应分析）。
2. **多模板构象库（Multi-template Conformational Library）**：以 101 个构象聚类代表作为同源建模模板，比单一模板（无论 apo 或 holo）更有效。可迁移至其他蛋白家族的构象建模。
3. **"计算一次、迁移多次"策略**：选择家族中一个代表成员进行昂贵计算，其余成员通过映射获得构象集合。适用于计算资源有限的大规模家族研究。
4. **全局打分 + 局部保真度的张力**：DOPE 全局打分可能丢弃口袋局部最优的构象，提示在构象选择中需要多尺度评价标准。

### 可迁移方法
1. **gEDES 协议**：metadynamics 偏置口袋形状/体积描述符，可迁移至其他靶标的口袋构象采样。
2. **构象聚类 + 多模板建模流水线**：从增强采样轨迹中提取多样化构象 → 多模板同源建模 → 集合对接，该流水线可复用于其他蛋白-配体系统。
3. **集合对接评估框架**：以 RMSD_BS、RMSD_BM、F_nat 多指标评估构象集合质量，并设置 HOLOexpt 作为上限基线、apo 单模板作为下限基线。
4. **失败案例分析范式**：对未恢复的复合物进行逐案分析，区分是采样不足、建模误差还是配体错位。

### 可迁移实验设计
1. **基线设置**：同时设置"实验 holo 单模板"（上限）和"实验 apo 单模板"（下限）作为对照，清晰界定方法增益。
2. **相关性分析**：用 Spearman 相关评估构象质量指标与对接成功率的关联，识别关键瓶颈。
3. **分层分析**：按序列同一性分层评估迁移效果，验证方法在低同一性下的鲁棒性。

### 对本课题的启示
- **AI 方法与物理采样的互补**：本文指出 AI 生成式方法受训练数据限制，而物理增强采样可补充高能态/稀有态；本课题可探索 AI 生成 + 物理精修（如 gEDES-HM 式迁移）的混合策略。
- **构象集合作为"可迁移资产"**：在蛋白质结构预测中，构象集合比单一结构更有信息量；可考虑将构象集合作为中间表示，用于下游对接、虚拟筛选或突变分析。
- **口袋级评价的重要性**：全局打分（DOPE）可能误导构象选择，提示在 AI 模型训练或评估中应加入口袋局部保真度指标。
- **家族规模的高通量构象生成**：gEDES-HM 为"一个家族一套构象"提供了范式，可结合 AlphaFold 家族预测结果作为模板库，进一步降低成本。