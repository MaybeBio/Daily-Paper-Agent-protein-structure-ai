## 01 基本信息
- **标题**：Dark energy: the cost of function in protein evolution
- **作者与单位**：Galpern, Ezequiel A; Caamano, Federico; Sanchez, Ignacio E; Ferreiro, Diego U（单位未提供）
- **期刊/预印本平台**：Current Opinion in Structural Biology
- **年份**：2026
- **论文类型**：综述（Review / Opinion）
- **领域**：蛋白质进化、蛋白质折叠稳定性与功能约束、深度学习在蛋白质序列-结构-功能关系中的应用
- **关键词**：dark energy（暗能量）、protein evolution、folding stability、biological function、deep mutational scanning、protein language models、inverse-folding models
- **DOI/arXiv 号**：10.1016/j.sbi.2026.103417
- **代码**：未提供
- **数据**：未提供
- **阅读日期**：2026-05-14（按当前日期推算）
- **该文在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI/物理模拟」方向中的**概念框架与量化方法综述**。它提出并系统化「dark energy」这一概念——即序列的进化能量与物理折叠能量之差——作为连接蛋白质进化、功能约束与结构稳定性的桥梁。文中重点评述了 deep mutational scanning (DMS)、protein language models (PLMs) 和 inverse-folding models 在量化该能量差方面的进展，为结构预测、序列设计和功能预测提供了新的理论视角和可迁移的量化框架。

## 02 一句话总结
本文提出并综述了「dark energy」概念——蛋白质序列的进化能量与物理折叠能量之差——用以量化功能约束对蛋白质进化施加的额外代价，并评述了 DMS、PLMs 和 inverse-folding models 等计算与实验方法如何在大规模上分离折叠稳定性与功能贡献。

## 03 研究问题
- **具体问题**：蛋白质进化同时受折叠稳定性与生物学功能双重约束，二者常相互冲突（frustration），导致功能代价超出稳定性代价。如何量化这一「功能代价」？如何在大规模（蛋白质组/蛋白质宇宙尺度）上将其与稳定性贡献分离？
- **为什么重要**：理解功能代价是连接序列-结构-功能关系的核心，对蛋白质设计（需在稳定性与功能间权衡）、进化机制解析（frustration 的起源）以及突变效应预测（区分稳定性效应与功能效应）均有直接意义。
- **现有方法为何不足**：传统方法主要聚焦于折叠稳定性（如 ΔΔG 预测、热稳定性实验），难以单独刻画功能约束的贡献；而功能测定通常低通量、难以规模化。缺乏一个统一的量化框架来同时捕捉两种约束及其相互作用。
- **精确研究问题**：Can the difference between evolutionary energy and physical folding energy of protein sequences be systematically quantified across the protein universe, thereby revealing a distinct 'dark energy' component attributable to functional constraints?

## 04 背景与发展脉络
*（标注：以下脉络主要基于本文框架，部分经外部核验）*
- **阶段一：稳定性中心范式**。早期蛋白质进化研究以折叠稳定性为核心，认为序列进化主要受稳定性选择驱动。代表方法：热稳定性实验、ΔΔG 计算。优点：可量化、可实验验证。局限：忽略功能约束的独立贡献。
- **阶段二：frustration 与功能约束的引入**。认识到功能位点（活性位点、结合界面）的序列保守性不能仅由稳定性解释，frustration（局部能量冲突）被提出作为功能-稳定性权衡的物理表现。代表方法：局部 frustration 分析（Ferreiro 等）。优点：将功能与物理能量联系起来。局限：难以全局量化。
- **阶段三：高通量突变扫描（DMS）**。DMS 技术可同时测定大量突变的适应度（fitness），提供序列-功能关系的实验数据。优点：大规模、定量。局限：覆盖序列空间有限，且 fitness 混合了稳定性与功能效应。
- **阶段四：深度学习模型（PLMs 与 inverse-folding）**。蛋白质语言模型（如 ESM 系列）从序列数据中学习进化约束，inverse-folding 模型（如 ProteinMPNN）学习序列-结构映射。这些模型可提供「进化能量」的近似，与物理折叠能量（如 Rosetta、AlphaFold 能量项）对比，从而分离出 dark energy。优点：可扩展至蛋白质宇宙。局限：模型偏差、进化能量与物理能量的可比性需谨慎。
- **本文主张的位置**：本文提出 dark energy 作为统一框架，将上述阶段的方法整合，主张通过「进化能量 - 物理折叠能量」的差值来系统量化功能代价，并认为当前 DMS + PLM + inverse-folding 的组合已使这一量化在蛋白质组尺度上成为可能。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 稳定性与功能约束难以分离 | 突变效应同时受稳定性和功能影响，无法单独归因 | 两种约束在序列上耦合，frustration 是物理表现 | 摘要：dual constraints that often conflict, creating frustration and imposing functional costs beyond stability |
| 功能代价缺乏统一量化框架 | 缺乏一个标量/能量量来刻画功能对进化的额外代价 | 传统方法聚焦稳定性，功能测定低通量 | 摘要：These costs can be captured by a 'dark energy' |
| 大规模量化困难 | 蛋白质组尺度上无法逐一实验测定功能 | 实验通量限制，计算模型可扩展但需校准 | 摘要：Recent advances ... have enabled the quantification of dark energy across the protein universe |
| 进化能量与物理能量的可比性 | 两类能量来源不同（序列统计 vs 物理力场），直接相减需谨慎 | 模型假设与标定问题 | 摘要：the difference between the evolutionary energy of protein sequences and their physical folding energy（作者隐含承认需 disentangle） |

## 06 核心思想
1. **表面方法**：提出 dark energy 概念，定义为进化能量（从序列数据/模型中提取）与物理折叠能量（从结构/力场中计算）之差；综述 DMS、PLMs、inverse-folding 三类方法如何分别或联合估计这两类能量，从而在蛋白质组尺度上量化 dark energy。
2. **核心洞察**：蛋白质序列的进化能量不仅反映折叠稳定性，还编码了功能约束的「额外代价」。当进化能量显著高于物理折叠能量时，差值即代表功能对序列施加的、超出稳定性需求的约束——这就是 dark energy。它揭示了序列-结构-功能关系中「信息流」的闭环：功能需求通过进化压力写入序列，而序列又通过折叠实现功能。
3. **可能的普适教训 [Analysis]**：任何「预测」任务（如结构预测、序列设计）若只优化单一目标（如稳定性），可能忽略功能维度的独立贡献。dark energy 框架提示：在蛋白质设计中，需显式考虑「进化能量」与「物理能量」的差异，以捕捉功能位点的约束；类似地，在 MD 模拟或对接中，功能相关构象可能对应能量景观中「非最稳定但功能必需」的区域，dark energy 可作为选择这些构象的判据。

## 07 方法总览
- **输入**：蛋白质序列数据集（用于 PLM 训练/推断）、蛋白质结构（用于物理能量计算）、DMS 实验数据（用于功能适应度标定）。
- **输出**：dark energy 的量化值（每个序列/位点的进化能量与物理折叠能量之差），以及其在蛋白质组中的分布图谱。
- **模块**：
  1. 进化能量估计模块：PLMs（如 ESM）或序列统计模型，从序列分布中提取 log-likelihood 作为进化能量代理。
  2. 物理折叠能量估计模块：基于结构的能量函数（如 Rosetta、FoldX）或 AlphaFold 的 pLDDT/能量项。
  3. 功能适应度模块：DMS 数据提供突变的功能效应，用于校准或验证 dark energy 的生物学意义。
  4. 差值计算与可视化模块：逐位点/逐序列计算差值，映射到结构上识别功能热点。
- **训练**：PLMs 在无标注序列上预训练；inverse-folding 模型在结构-序列对上训练；DMS 数据用于下游验证而非训练（或用于微调）。
- **工具**：ESM 系列、ProteinMPNN、Rosetta、FoldX、AlphaFold 等（文中提及，具体版本未提供）。
- **假设**：① 进化能量可从序列统计中近似；② 物理折叠能量可从结构计算中近似；③ 两者之差可归因于功能约束（而非模型误差或统计噪声）。
- **流程**：收集序列 → PLM 计算进化能量 → 获取/预测结构 → 计算物理折叠能量 → 逐位点相减得 dark energy → 用 DMS 数据验证 dark energy 与功能效应的相关性 → 在蛋白质组尺度上绘制 dark energy 图谱。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 进化能量估计（PLM/序列统计） | 从序列分布中提取进化约束的代理能量 | 提供「进化能量」项，反映序列在进化中的可接受程度 | 输入：序列；输出：位点/序列 log-likelihood | 摘要：protein language models ... enabled the quantification | 预期影响：无法估计进化能量，dark energy 无法计算（核心模块） |
| 物理折叠能量估计（Rosetta/FoldX/AlphaFold） | 从结构计算折叠稳定性相关能量 | 提供「物理能量」项，作为稳定性基线 | 输入：结构；输出：能量值/稳定性分数 | 摘要：physical folding energy | 预期影响：无法分离功能贡献，dark energy 退化为纯进化能量 |
| DMS 功能适应度数据 | 提供突变的功能效应，用于校准/验证 | 验证 dark energy 是否真实反映功能代价 | 输入：突变体功能数据；输出：适应度分数 | 摘要：deep mutational scanning | 预期影响：dark energy 的生物学解释力无法验证（验证模块） |
| 差值计算与结构映射 | 逐位点计算 dark energy 并映射到结构 | 识别功能热点位点，可视化功能代价分布 | 输入：两类能量；输出：dark energy 图谱 | 摘要：revealing a dark energy component | 预期影响：无法定位功能位点，dark energy 仅剩全局标量 |

## 09 关键公式符号
- **dark energy 定义**（概念性公式，文中未给具体数学形式，以下为基于摘要的重构）：
  \[
  E_{\text{dark}} = E_{\text{evo}} - E_{\text{fold}}
  \]
  - \( E_{\text{dark}} \)：dark energy，功能约束的进化代价
  - \( E_{\text{evo}} \)：进化能量，从序列统计/PLM 中提取
  - \( E_{\text{fold}} \)：物理折叠能量，从结构/力场中计算
  - **直觉**：若序列仅受稳定性约束，则 \( E_{\text{evo}} \approx E_{\text{fold}} \)，dark energy 接近零；显著正差值表明功能约束额外抬高了序列的进化要求。
  - **来源**：摘要中「the difference between the evolutionary energy of protein sequences and their physical folding energy」；具体数学形式未提供。

## 10 实验设计与证据链
*（本文为综述，无原始实验；以下基于文中评述的方法与主张）*
- **数据集/群体**：未提供具体数据集；文中提及「across the protein universe」暗示蛋白质组/蛋白质宇宙尺度的序列与结构数据。
- **规模**：未提供具体数字。
- **指标**：未提供统一指标；推测包括序列 log-likelihood、结构能量值、DMS 适应度相关性等。
- **基线**：未提供。
- **预算**：未提供。
- **骨干/仪器**：未提供。
- **oracle 输入**：未提供。
- **评测协议**：未提供。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|------------|------------------|------|
| DMS 数据与 dark energy 相关性分析（文中评述） | dark energy 反映功能代价 | 比较 DMS 适应度与进化-物理能量差 | 未提供具体数值 | dark energy 与功能效应相关（作者主张） | 无法确认因果性；未提供效应量 | 摘要：revealing a dark energy component |
| PLM 进化能量与结构能量对比（文中评述） | 两类能量可分离 | 同一序列集上分别计算两类能量 | 未提供具体数值 | 差值可计算且具有生物学意义（作者主张） | 未提供误差分析或模型偏差评估 | 摘要：disentangle folding and function at scale |
| 蛋白质组尺度 dark energy 图谱（文中展望） | dark energy 可规模化量化 | 大规模序列-结构数据 | 未提供 | 方法可扩展（作者主张） | 未提供实际图谱或验证 | 摘要：across the protein universe |

## 11 结论正确解读
- **任务范围**：本文是概念综述，不提出新算法或新实验，而是整合现有方法提出 dark energy 框架。
- **oracle/真值输入**：无实验真值；依赖 DMS 数据作为功能真值的代理，但未讨论 DMS 覆盖偏差。
- **端到端状态**：框架尚未端到端验证；各模块（PLM、物理能量、DMS）独立成熟，但整合后的 dark energy 量化缺乏统一基准。
- **算力成本**：未讨论；PLM 推理和结构计算均有显著算力需求，但文中未量化。
- **历史数据依赖**：PLM 依赖大规模序列数据库，其进化能量估计受训练数据分布影响。
- **模型依赖**：dark energy 数值高度依赖所选 PLM 和物理能量函数的标定，不同组合可能产生不同结果。
- **最难情形**：功能与稳定性强耦合的位点（如活性位点同时贡献稳定性）难以分离； intrinsically disordered regions 可能不适用。
- **群体/领域边界**：主要适用于 globular proteins 的序列-结构-功能关系；对膜蛋白、多结构域蛋白的适用性未讨论。
- **不确定性**：dark energy 的生物学解释（是否真实反映功能代价）缺乏直接实验验证。
- **有边界的复述**：本文提出 dark energy 作为量化功能进化代价的概念框架，并综述了 DMS、PLM 和 inverse-folding 方法使其在蛋白质组尺度上可计算；但该框架的数值可靠性、生物学解释力及跨蛋白类型适用性仍需进一步验证。

## 12 作者自认局限
*（在提供的材料中未发现作者明确承认的局限）*
- 注：本文为摘要级材料，未提供全文，作者可能在正文中讨论局限，但当前材料不可得。
- **作者提及的相关约束**（非正式局限）：
  - 摘要中「disentangle folding and function at scale」暗示两类能量的分离是挑战性任务，隐含承认方法学困难。
  - 「revealing a dark energy component」的措辞表明 dark energy 是「揭示」而非「证明」，隐含解释的不确定性。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| dark energy 定义为两类能量之差，但两类能量来源不同（统计 vs 物理），量纲和标度可能不可比 | 差值可能反映模型偏差而非真实功能代价 | 若不可比，dark energy 数值无物理意义 | 在已知功能位点（如酶活性位点）上检验 dark energy 是否显著高于非功能位点，并控制稳定性效应 | 摘要：difference between evolutionary energy and physical folding energy |
| PLM 的进化能量隐含假设序列数据库反映纯进化选择，但数据库包含功能与稳定性混合信号 | 进化能量可能已部分包含功能信息，dark energy 被低估 | 若进化能量已编码功能，dark energy 的「额外」含义被削弱 | 比较 PLM 在功能位点与稳定性位点的 log-likelihood 差异 | 摘要：protein language models ... enabled quantification |
| 综述主张「across the protein universe」，但 DMS 数据仅覆盖少量蛋白 | 蛋白质组尺度的 dark energy 图谱可能缺乏实验验证 | 规模化主张可能超出数据支撑 | 检查文中是否提供跨蛋白家族的 DMS 验证案例 | 摘要：across the protein universe（未提供具体覆盖） |
| dark energy 概念与 frustration 的关系未明确 | frustration 是局部物理现象，dark energy 是全局序列统计量，两者可能不直接对应 | 若概念混淆，框架内部一致性受损 | 在已知 frustration 位点上检验 dark energy 是否富集 | 摘要：creating frustration and imposing functional costs |

## 14 学到什么
**Agent 提炼的知识候选**（面向蛋白质结构相关计算研究 × AI/物理模拟）：
1. **可迁移概念——dark energy 作为多目标约束的量化指标**：在蛋白质设计中，可计算「进化能量（PLM log-likelihood）- 物理折叠能量（Rosetta/AlphaFold 能量）」之差，作为功能位点识别的先验。迁移方式：在序列设计任务中，对候选序列同时优化稳定性和 dark energy 最小化，以保留功能约束。
2. **可迁移方法——DMS 作为功能真值的校准工具**：DMS 数据可用于校准 PLM 或 inverse-folding 模型的输出，使其从「序列统计」转化为「功能相关」的预测。迁移方式：在 MD 模拟或对接中，用 DMS 适应度加权构象采样，优先采样功能相关构象。
3. **可迁移思路——能量差而非绝对能量**：dark energy 的核心是「差值」而非绝对能量，这提示在结构预测或构象采样中，可关注「预测能量与实验/进化能量的偏差」作为误差或功能信号的指标。迁移方式：在 AlphaFold 预测中，pLDDT 与进化保守性的联合分析可能揭示功能热点。
4. **可迁移框架——序列-结构-功能-序列的闭环**：本文强调信息流从功能到序列再回到功能，提示在蛋白质设计中应迭代使用「设计 → 功能预测 → 序列再设计」的闭环，而非单次优化。迁移方式：结合 PLM 生成和 MD 验证的迭代设计流程。

## 15 与已有知识连接
- **相似概念**：与「frustration」概念（Ferreiro 等早期工作）直接相关，dark energy 可视为 frustration 的全局序列层面量化；与「进化保守性」分析（如 ConSurf）相似，但 dark energy 提供能量学解释。
- **组合方法**：与 AlphaFold 的 pLDDT 结合——pLDDT 反映结构置信度，dark energy 反映功能约束，两者联合可区分「结构不确定但功能重要」的位点。
- **冲突观点**：传统观点认为序列进化主要由稳定性驱动（如「neutral evolution」理论），dark energy 框架挑战这一观点，主张功能约束独立贡献；需在具体蛋白上检验。
- **可迁移领域**：分子对接中，dark energy 高的位点可能对应结合界面热点；MD 模拟中，dark energy 可作为选择功能相关构象的偏置势。
- **候选方向（未验证）**：dark energy 是否与 intrinsically disordered regions 的功能相关？是否可用于预测 allosteric 位点？这些在文中未讨论，但框架可扩展。

## 16 研究想法
**Agent 生成的研究候选**：

1. **名称**：Dark energy 引导的蛋白质功能位点预测器
   - **来源局限/观察**：dark energy 概念提出但缺乏具体预测工具；现有功能位点预测（如 ConSurf）仅用保守性，未结合能量学。
   - **核心假设**：dark energy 高值位点富集于实验已知功能位点（活性位点、结合界面）。
   - **初步方法**：在标准数据集（如酶功能位点数据库）上，计算 PLM log-likelihood 与 Rosetta 能量之差，训练分类器区分功能/非功能位点，与 ConSurf 基线对比。
   - **验证方式**：交叉验证 AUC；在 DMS 数据上检验 dark energy 与适应度的相关性。
   - **创新状态**：unverified（概念来自本文，具体实现未提供）。

2. **名称**：Dark energy 偏置的构象采样（MD/对接）
   - **来源局限/观察**：MD 模拟和对接通常以物理能量为目标，忽略功能约束；dark energy 可提供功能偏置。
   - **核心假设**：在构象采样中引入 dark energy 作为偏置势，可优先采样功能相关构象（如活性构象、结合构象）。
   - **初步方法**：在已知蛋白-配体体系上，计算各构象的 dark energy，用 metadynamics 或 replica exchange 加入偏置，比较功能构象的采样效率。
   - **验证方式**：与无偏置模拟对比，功能构象的种群比例或首次命中时间。
   - **创新状态**：unverified（本文未提出此应用）。

3. **名称**：Dark energy 与 AlphaFold 置信度的联合分析
   - **来源局限/观察**：AlphaFold 的 pLDDT 反映结构置信度，但未编码功能信息；dark energy 可补充功能维度。
   - **核心假设**：pLDDT 低但 dark energy 高的位点可能是功能关键但结构动态的区域。
   - **初步方法**：在蛋白质组数据上计算 pLDDT 与 dark energy 的联合分布，识别「低置信度-高功能代价」位点，与已知功能注释（如 UniProt）比对。
   - **验证方式**：富集分析（如 GO 注释富集）。
   - **创新状态**：unverified（本文未提出此联合分析）。

4. **名称**：Dark energy 指导的序列设计迭代框架
   - **来源局限/观察**：现有序列设计（如 ProteinMPNN）主要优化稳定性或结构恢复率，忽略功能约束。
   - **核心假设**：在设计中加入 dark energy 最小化项，可生成既稳定又保留功能位点约束的序列。
   - **初步方法**：在酶或结合蛋白上，用 inverse-folding 生成序列，计算 dark energy，过滤或重排候选，用实验或 DMS 验证功能保留。
   - **验证方式**：与仅优化稳定性的设计对比，功能活性保留率。
   - **创新状态**：unverified（本文未提出此设计流程）。