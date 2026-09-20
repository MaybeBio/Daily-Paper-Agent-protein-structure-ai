## 01 基本信息

- **标题**：Combining AI Structure Prediction and Integrative Modeling for Nanobody-Antigen Complexes
- **作者**：Sanchez-Marin, Miguel; Giulini, Marco; Bonvin, Alexandre M J J
- **单位**：未提供（Bonvin 隶属 Utrecht University，依据其长期 affiliation，但原文未提供）
- **期刊/平台**：Journal of Chemical Information and Modeling
- **年份**：2026（在线日期 2026-09-14）
- **论文类型**：方法评估与流程基准测试（benchmarking study）
- **领域**：蛋白质结构预测 × 信息驱动分子对接（AI 结构预测 + 整合建模）
- **关键词**：Nanobody、AlphaFold2-Multimer、AlphaFold3、ImmuneBuilder、HADDOCK、Docking、CDR3
- **DOI/arXiv**：10.1021/acs.jcim.6c01301
- **代码**：https://github.com/haddocking/nanobodies（数据集）
- **数据**：40 个 nanobody-antigen 复合物基准数据集；226 个 Paratope 数据集（来自 SAbDab）
- **阅读日期**：2026-09-14
- **在课题方向中的位置**：本文处于「蛋白质结构相关计算研究 × AI/物理模拟」交叉点，系统评估 AI 结构预测方法（AlphaFold2-Multimer、AlphaFold3、ImmuneBuilder 等）作为输入，结合信息驱动对接（HADDOCK）预测 nanobody-antigen 复合物结构。核心贡献在于：(1) 构建非冗余基准数据集；(2) 系统比较多种 AI 预测方法；(3) 提出 ensemble 对接流程与框架感知（framework-aware）的 paratope 定义，显著提升对接成功率。

---

## 02 一句话总结

本文构建了 40 个非冗余 nanobody-antigen 复合物基准数据集，系统评估多种 AI 结构预测方法，并提出将 AlphaFold2-Multimer 与 ImmuneBuilder 预测的 nanobody 结构 ensemble 作为 HADDOCK 信息驱动对接的输入，在具备部分表位信息时，该流程的成功率超过 AlphaFold2-Multimer 基线，与 AlphaFold3 相当。

---

## 03 研究问题

**具体问题**：Nanobody-antigen 复合物结构预测中，由于缺乏共进化信号且 CDR3 环构象空间巨大，现有 AI 方法（如 AlphaFold2-Multimer）成功率有限。能否通过将 AI 结构预测与信息驱动对接（HADDOCK）相结合，在仅有部分表位信息（如 loose interface 或两个关键残基）的条件下，获得更高的预测成功率？

**为什么重要**：Nanobody 在治疗和诊断应用中具有重要价值，其抗原结合亲和力与传统抗体相当，但体积小、稳定性高。准确预测 nanobody-antigen 复合物结构对 nanobody 工程改造、表位识别和药物设计至关重要。

**现有方法不足**：
- AlphaFold2-Multimer 依赖共进化信号，而 nanobody-antigen 复合物缺乏这种信号，导致成功率有限（Top 1 仅 25% acceptable）。
- AlphaFold3 虽表现更好，但需要大量采样（1000 seeds/5000 models），计算成本极高，且服务器版限制下游建模使用。
- 传统对接方法需要准确的单体结构输入，而 nanobody CDR3 预测精度不足。

**精确研究问题**：Can an ensemble docking pipeline, combining AI-predicted nanobody structures with information-driven HADDOCK docking, achieve higher success rates than AlphaFold2-Multimer baseline on nanobody-antigen complexes when partial epitope information is available?

---

## 04 背景与发展脉络

> 注：此脉络基于本文框架整理，部分经外部核验（标注）。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 传统抗体建模 | 同源建模 + CDR 环库 | 可解释、物理合理 | 精度有限，CDR3 构象采样不足 | 背景 |
| 深度学习方法（单体） | AlphaFold2、ImmuneBuilder、NanoNet、RaptorX-Single | 快速、无需共进化信号（部分方法） | CDR3 精度仍有限（RMSD > 3 Å） | 本文评估对象 |
| 深度学习方法（复合物） | AlphaFold2-Multimer、AlphaFold3 | 端到端预测复合物 | 缺乏共进化信号时成功率低；AF3 计算成本极高 | 本文基线 |
| 信息驱动对接 | HADDOCK（抗体-抗原流程） | 可整合实验信息、物理评分 | 依赖输入结构质量与表位信息 | 本文核心方法 |
| 整合流程（本文） | AI 预测 ensemble + HADDOCK 对接 | 结合 AI 速度与物理对接精度，成功率超过 AF2M | 需要部分表位信息；评分仍具挑战 | **本文贡献** |

**经外部核验的脉络**：AlphaFold2 在无共进化信号（孤儿蛋白）上表现下降已有广泛报道；HADDOCK 在抗体-抗原复合物预测中的成功已有先例（Ambrosetti et al.）；AlphaFold3 的高采样需求在 Abramson et al. 中有明确报告。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 缺乏共进化信号 | AF2M 在 nanobody-antigen 复合物上 Top 1 acceptable 仅 25% | Nanobody-antigen 相互作用缺乏足够的 MSA 共进化信息 | Results 节 "AlphaFold Has Moderate Accuracy..." |
| CDR3 构象空间巨大 | 所有方法 CDR3 RMSD 均值 > 3 Å | CDR3 长度可变（6-24 残基）、柔性高、缺乏模板 | Results 节 Table 1 |
| 抗原建模误差 | 9/40 抗原全局 RMSD > 5 Å，3 个表位 RMSD > 5 Å | AF2M 对多链抗原或非 globular 抗原建模困难 | Results 节 "The Quality of Antigen Structure Prediction..." |
| 多链抗原相对取向错误 | PDB 7QNE 中链 A/E 相对取向错误，导致所有对接失败 | AF2M 对多链复合物的链间取向预测不可靠 | Results 节，7QNE 案例分析 |
| 评分函数无法识别近天然模型 | Top 1 成功率远低于 Top 200 成功率 | HADDOCK 评分函数在 nanobody-antigen 上区分度不足 | Results 节 图 2、图 3 |
| 计算成本高 | AF3 需 1000 seeds/5000 models 才能达到 60% acceptable | AF3 的扩散采样策略需要大量样本 | Introduction 节 |
| Paratope 定义不完整 | 仅用 CDR 环定义 paratope 时，部分案例 F_para < 60% | Nanobody 的框架区（FR）也参与抗原结合 | Results 节 图 4b、Discussion 节 |

---

## 06 核心思想

### 1) 表面方法

构建一个多阶段流程：(a) 用多种 AI 方法（AF2M、AF2、IB、NN、RXS）预测 nanobody 单体结构；(b) 将不同方法的预测结果合并为 ensemble，通过 CDR3 RMSD 层次聚类去冗余；(c) 用 HADDOCK3 信息驱动对接，将 nanobody ensemble 对接到抗原表位区域；(d) 用 HADDOCK 评分函数排序并评估。

### 2) 核心洞察

- **Ensemble 优于单模型**：不同 AI 方法在不同案例上各有优劣，合并 ensemble 后最佳可用模型的 CDR3 RMSD 中位数降至 1.23 Å（远低于任何单一方法），说明方法间误差互补。
- **信息驱动对接可弥补 AI 复合物预测不足**：当有部分表位信息（loose interface 或两个关键残基）时，HADDOCK 对接成功率超过 AF2M 基线，与 AF3 相当，但计算成本远低于 AF3 的 1000 seeds 采样。
- **Paratope 定义是关键**：nanobody 的框架区（FR）在抗原结合中贡献显著，仅用 CDR 环定义 paratope 会遗漏重要结合残基。基于 226 个实验结构分析，提出 CDR+FR 的 paratope 定义，提升对接成功率。
- **评分是瓶颈**：Top 200 成功率远高于 Top 1/Top 10，说明正确模型已生成但难以被评分函数识别。

### 3) 可能的普适教训 [Analysis]

- **AI 预测 + 物理对接的互补性**：AI 方法擅长从序列预测结构，但缺乏对相互作用物理化学的显式建模；信息驱动对接擅长在约束下搜索结合模式，但依赖输入结构质量。两者结合可互补短板。
- **Ensemble 策略的普适性**：在单一方法不确定性高时，合并多种方法的输出并聚类去冗余，可显著提高"最佳可用模型"的质量——这一思路可迁移到其他蛋白质结构预测任务。
- **信息分级与鲁棒性**：本文系统评估了从"全表位已知"到"仅两个关键残基"的信息级别，展示了信息驱动方法在不同信息可用性下的表现边界，为实际应用提供了选择依据。

---

## 07 方法总览

**输入**：
- Nanobody 氨基酸序列（FASTA）
- 抗原氨基酸序列（FASTA）
- 可选信息：表位残基（不同信息级别：TI/LI/2I/AS）

**输出**：
- Nanobody-antigen 复合物结构模型（按 HADDOCK 评分排序）
- 按 CAPRI 标准分类的模型质量（acceptable/medium/high）

**模块**：

1. **Nanobody 结构预测**：6 种方法（AF2M、AF2、IB、NN、RXS、AF3），每种生成多个模型
2. **Ensemble 构建与聚类**：合并所有方法模型，基于 CDR3 RMSD 层次聚类（阈值 2.5 Å），每簇选置信度最高模型
3. **抗原结构准备**：优先使用实验同源结构；否则用 AF2M 预测，按 pLDDT 选择最佳模型
4. **HADDOCK3 对接**：
   - 刚性对接（rigid-body docking）
   - Top 200 模型进入柔性细化（flexible refinement）
   - 能量最小化
   - FCC 聚类，每簇选 Top 4
5. **评分与评估**：HADDOCK 评分函数（HS = 1.0·Evdw + 0.2·Eelec + 1.0·Edesolv + 0.1·Eair − 0.01·BSA），CAPRI 标准分类

**工具**：ColabFold v1.5.3（AF2M）、AlphaFold3 服务器、ImmuneBuilder（NanoBodyBuilder2）、NanoNet、RaptorX-Single、HADDOCK3、pdb-tools、MDAnalysis、Profit v3.3

**流程**（文字描述）：
序列输入 → 各 AI 方法独立预测 nanobody 结构 → 合并所有预测为 ensemble → CDR3 RMSD 层次聚类去冗余 → 每簇选代表模型 → 与抗原结构（实验或预测）一起输入 HADDOCK3 → 按信息场景生成 ambiguous restraints → 刚性对接 → 柔性细化 → FCC 聚类 → 评分排序 → CAPRI 分类评估

**假设**：
- 实验结构中的抗原构象与溶液状态一致（bound 实验中使用结合态抗原）
- 对接评分函数（HADDOCK score）能近似反映结合自由能
- 表位信息（即使不完整）能有效引导对接搜索

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|---------------------|
| AI 结构预测（多方法） | 生成 nanobody 单体结构候选 | 单一方法 CDR3 精度不足，多方法可互补 | 输入：序列；输出：结构模型集合 | Results 图 1a：各方法 CDR3 RMSD 分布 | 预期影响：ensemble 多样性降低，最佳可用模型质量下降 [预期效应] |
| Ensemble 聚类 | 去冗余、保留多样性 | 大量模型直接对接计算成本高，且相似模型无信息增益 | 输入：所有模型；输出：聚类代表模型 | Results 图 1a：聚类后 ensemble 中位数 CDR3 RMSD 1.23 Å | 预期影响：计算成本降低但可能丢失稀有构象 [预期效应] |
| 抗原结构选择 | 获取高质量抗原结构 | 抗原建模误差直接限制对接精度 | 输入：AF2M 预测或 PDB 同源结构；输出：抗原结构 | Results 节：9/40 抗原全局 RMSD > 5 Å | 实测影响：7QNE 因抗原多链取向错误导致所有对接失败 [实测] |
| HADDOCK3 对接（刚性+柔性） | 搜索结合模式并优化 | 信息驱动对接可利用表位信息引导搜索 | 输入：nanobody ensemble + 抗原 + restraints；输出：复合物模型 | Results 图 2：TI 场景 Top 10 达 80-87.5% | 预期影响：无信息引导时成功率大幅下降 [预期效应] |
| 信息场景定义（TI/LI/2I/AS） | 模拟不同信息可用性 | 实际应用中表位信息完整度不同 | 输入：表位残基集合；输出：ambiguous restraints | Results 图 2：TI > LI ≈ 2I >> AS | 实测影响：AS 场景成功率仅 7.5-20% [实测] |
| Paratope 定义（CDR vs CDR+FR） | 定义 nanobody 侧可能的结合残基 | 仅 CDR 环无法覆盖全部 paratope | 输入：结构/序列；输出：活性残基集合 | Results 图 4b：F_para 与 docking 成功率相关 | 实测影响：CDR+FR 定义提升 LI 场景 Top 10 SR 12.5% [实测] |
| FCC 聚类 + Top N 选择 | 从大量模型中提取代表性预测 | 对接产生大量模型，需聚类排序 | 输入：所有对接模型；输出：Top N 代表模型 | Results 节：FCC 聚类提升 Top 10 SR | 预期影响：无聚类时 Top N 冗余度高 [预期效应] |
| 评分函数（HADDOCK score / VoroIF-jury） | 排序模型质量 | 识别近天然模型是当前瓶颈 | 输入：模型集合；输出：排序列表 | Results 节：Top 200 远高于 Top 1/Top 10 | 实测影响：评分函数区分度不足，是主要瓶颈 [实测] |

---

## 09 关键公式符号

**1. HADDOCK 评分函数**（Methods 节）：

HS = 1.0·E_vdw + 0.2·E_elec + 1.0·E_desolv + 0.1·E_air − 0.01·BSA

- HS：HADDOCK score，用于模型排序
- E_vdw：分子间范德华能
- E_elec：分子间静电相互作用能
- E_desolv：经验去溶剂化能
- E_air：ambiguous interaction restraints（AIR）能量项
- BSA：埋藏表面积（buried surface area）

**2. CAPRI 分类标准**（Methods 节）：

基于 i-RMSD、L-RMSD、F_nat 三个指标：
- High：F_nat ≥ 0.5 且 (i-RMSD ≤ 1 Å 或 L-RMSD ≤ 1 Å)
- Medium：F_nat ≥ 0.3 且 (i-RMSD ≤ 2 Å 或 L-RMSD ≤ 5 Å)
- Acceptable：F_nat ≥ 0.1 且 (i-RMSD ≤ 4 Å 或 L-RMSD ≤ 10 Å)
- Incorrect：不满足上述任何条件

**3. F_para**（Results 节）：

F_para = 用于 restraints 的活性残基中属于实验 paratope 的残基数 / 实验 paratope 总残基数

**4. DockQ**（Results 节）：

连续评分，综合 F_nat、i-RMSD、L-RMSD，范围 0-1，用于评估模型质量。

---

## 10 实验设计与证据链

**数据集**：
- 基准数据集：40 个 nanobody-antigen 复合物晶体结构，来自 SAbDab Nano，2021-09-30 后发布（避免与训练集重叠），CDR3 序列非冗余（60% 同源性阈值），CDR3 长度 6-24 残基，抗原来源包括病毒（17）、人（8）、细菌（7）、啮齿类（4）、植物（3）、原生动物（1）
- Paratope 数据集：226 个 nanobody-antigen 实验结构，无截止日期限制

**评估指标**：
- 可接受成功率（acceptable SR）：至少一个 acceptable 或更高质量模型的案例百分比
- 中等等成功率（medium SR）：至少一个 medium 或更高质量模型的案例百分比
- DockQ：连续质量评分
- CDR3 RMSD：nanobody 预测精度
- F_para：paratope 覆盖率

**基线**：
- AF2M 复合物预测（Top 1/Top 10）
- AF3 复合物预测（25 模型）
- HADDOCK 对接（不同信息场景、不同 nanobody 输入）

**实验列表**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|-----------|----------------|------|
| AF2M 复合物预测 | AF2M 在 nanobody-antigen 上成功率有限 | 40 个案例，Top 1/Top 10 | Top 1 acceptable 25%，Top 10 27.5% | AF2M 基线成功率有限 | 不能推广到所有复合物类型 | Results 图 2 |
| AF3 复合物预测 | AF3 优于 AF2M | 25 模型/复合物 | Top 1 acceptable 32.5%，Top 10 52.5% | AF3 是强基线 | 25 模型远少于 1000 seeds 设置 | Results 图 2 |
| 单体预测精度比较 | 各方法 CDR3 预测精度 | 6 种方法，CDR3 RMSD | AF3 最佳（均值 2.48 Å），NN 最差（4.60 Å） | 方法间存在显著差异 | 均值受离群值影响 | Results 表 1 |
| Ensemble 聚类效果 | 合并多方法 ensemble 提升最佳可用模型 | 合并 vs 单一方法 | 聚类后 ensemble 中位数 CDR3 RMSD 1.23 Å | Ensemble 策略有效 | 最佳模型仍需下游筛选 | Results 图 1a |
| HADDOCK TI 场景 | 全表位信息下对接成功率 | bound/unbound 抗原 | Top 10 达 80-87.5% | 信息驱动对接有效 | 依赖完整表位信息 | Results 图 2 |
| HADDOCK LI/2I 场景 | 部分信息下仍优于 AF2M | 与 AF2M/AF3 对比 | LI/2I Top 10 约 40-55%，高于 AF2M | 部分信息足够 | 低于 TI 场景 | Results 图 2 |
| HADDOCK AS 场景 | 无信息时对接困难 | 仅 CDR 活性 | Top 10 仅 20% | 无信息时成功率低 | 仅测试了 1 个 ensemble | Results 图 S3 |
| F_para 分析 | paratope 覆盖率影响成功率 | 226 个结构分析 | F_para < 60% 时成功率显著下降 | Paratope 定义关键 | 相关性非因果 | Results 图 4b |
| CDR+FR paratope | 框架感知 paratope 提升成功率 | 原 CDR vs CDR+FR | LI 场景 Top 10 SR 提升 12.5% | 框架区参与结合 | 仅 LI 场景测试 | Results 图 S9 |
| 失败案例分析 | 识别失败原因 | 7QNE 等多链抗原 | 多链抗原相对取向错误导致失败 | 抗原建模是瓶颈 | 案例数有限 | Results 节 |

---

## 11 结论正确解读

**任务范围**：本文仅针对 nanobody-antigen 复合物，不涉及抗体-抗原或其他蛋白-蛋白复合物。基准数据集限于晶体结构，未包含冷冻电镜或溶液状态结构。

**oracle/真值输入**：所有评估均以实验晶体结构为真值。信息场景中，表位残基来自实验结构注释（TI 场景为全表位，LI 为 loose 定义，2I 为两个关键残基）。这代表"理想化"的信息可用性，实际应用中表位信息可能更不精确。

**端到端状态**：本文流程并非全自动端到端——需要人工选择信息场景、设定 restraints 参数、判断聚类阈值。AF3 服务器版本限制了下游建模使用，因此未纳入 ensemble。

**算力成本**：HADDOCK 流程平均运行时间 37-45 分钟（12 核），远低于 AF3 的 1000 seeds 设置。但 ensemble 方法需要运行多个 AI 预测，总成本需累加。

**历史数据依赖**：基准数据集刻意选择 2021-09-30 后发布的结构，避免与 AI 方法训练集重叠。但 AI 方法仍在更新，新方法可能改变结论。

**模型依赖**：结论基于当前版本的 AF2M、AF3、ImmuneBuilder 等。这些方法持续更新，性能变化可能影响结论的时效性。

**最难情形**：多链抗原（如 7QNE）中链间相对取向预测错误是当前流程的致命弱点；无任何表位信息时（AS 场景）成功率极低。

**群体/领域边界**：结论适用于 nanobody-antigen 复合物，且限于晶体结构可解析的构象。对于柔性抗原、膜蛋白抗原或翻译后修饰抗原，结论可能不成立。

**有边界的复述**：在 40 个非冗余 nanobody-antigen 复合物上，当提供 loose interface 或两个关键残基的表位信息时，以 AI 预测 nanobody ensemble 为输入的 HADDOCK 对接流程，其 acceptable 成功率（Top 10 约 40-55%）显著高于 AF2M 基线（27.5%），与 AF3 的 25 模型设置相当（52.5%），且计算成本远低于 AF3 的 1000 seeds 设置。该结论不适用于无表位信息场景，也不适用于多链抗原中链间取向严重错误的情况。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 数据集规模有限 | 仅 40 个复合物，统计功效有限 | 扩展数据集以包含更多样化的 nanobody-antigen 复合物 | Discussion 节 |
| 数据集偏倚 | 主要来自晶体结构，可能偏向稳定、易结晶的复合物 | 纳入冷冻电镜、溶液状态结构 | Discussion 节 |
| 表位信息理想化 | 信息场景中的表位残基来自实验结构注释，实际应用中可能不精确 | 结合表位预测工具自动生成 restraints | Discussion 节 |
| 多链抗原建模失败 | 7QNE 等案例中 AF2M 对链间相对取向预测错误 | 开发专门的多链抗原建模策略 | Results 节 |
| 评分函数是瓶颈 | Top 200 成功率远高于 Top 1/Top 10，正确模型难以被识别 | 开发更好的评分函数或 ML-based 排序方法 | Discussion 节 |
| AF3 未纳入 ensemble | AF3 服务器版限制下游建模使用 | 等待 AF3 开放本地运行或开发替代方案 | Results 节 |
| AlphaFlow 无优势 | 在 nanobody CDR3 上 AlphaFlow 未提供显著改进 | 进一步探索生成式方法在 CDR3 采样中的应用 | Results 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 基准数据集刻意排除训练集重叠案例 | 可能高估了 AI 方法在"新"nanobody 上的表现；实际应用中 nanobody 可能部分相似于训练数据 | 影响结论的生态效度 | 在包含训练集重叠案例的数据集上重新评估 | Methods 节数据集构建 |
| TI 场景代表"理想化"信息 | 实际应用中全表位已知的情况很少，TI 场景的成功率可能高估了流程上限 | 影响实际应用预期 | 在真实应用场景（如仅知突变数据）中测试 | Results 节 |
| Ensemble 聚类阈值（2.5 Å）为经验选择 | 不同阈值可能改变 ensemble 组成和下游对接结果 | 影响流程鲁棒性 | 进行阈值敏感性分析 | Methods 节 |
| 仅测试了 1 个 ensemble（IBMu）用于 AS 场景 | AS 场景结论可能不适用于其他 ensemble 组合 | 影响无信息场景的结论 | 在多个 ensemble 上测试 AS 场景 | Results 节 |
| HADDOCK 评分函数与实验结合自由能相关性未验证 | 高 HADDOCK score 不一定对应高结合亲和力 | 影响模型排序可靠性 | 与实验结合亲和力数据对比 | Methods 节 |
| 未报告各方法的运行时间/资源消耗 | 实际应用中计算资源是重要考量 | 影响方法选择 | 补充基准测试 | 未提供 |
| 与 AF3 的比较不公平（25 vs 1000 模型） | AF3 在 1000 seeds 下可能表现更好 | 影响"与 AF3 相当"的结论 | 在相同采样规模下比较 | Results 节 |
| Paratope 分析基于 226 个结构，但分类标准（kinked/extended）可能过于简化 | 实际 paratope 分布可能更连续 | 影响 paratope 定义普适性 | 使用更细粒度的分类标准 | Results 节 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移概念

1. **多方法 ensemble 优于单一方法**：在蛋白质结构预测中，不同方法（AF2M、IB、NN 等）的误差具有互补性，合并后聚类去冗余可显著提升"最佳可用模型"质量。这一策略可迁移到其他结构预测任务（如抗体 CDR 环预测、酶活性位点预测）。

2. **信息分级评估框架**：本文系统定义了 TI/LI/2I/AS 四个信息场景，模拟从"全表位已知"到"无信息"的梯度。这种评估框架可迁移到其他 docking 或结构预测任务，帮助研究者理解方法在不同信息条件下的适用边界。

3. **框架感知的 paratope 定义**：仅用 CDR 环定义 paratope 会遗漏框架区（FR）的结合贡献。这一发现提示在 nanobody 对接中应纳入 FR 残基，也可迁移到抗体-抗原对接中重新审视 paratope 定义。

4. **聚类 + 置信度选择策略**：在大量预测模型中，基于结构相似性聚类后选择置信度最高的代表模型，是平衡计算成本与多样性的有效策略。

### 可迁移方法

1. **HADDOCK 信息驱动对接流程**：将 AI 预测结构作为 ensemble 输入，结合表位信息生成 ambiguous restraints，经刚性对接→柔性细化→聚类→排序的完整流程，可直接迁移到其他蛋白-蛋白复合物预测任务。

2. **CDR3 RMSD 作为质量指标**：以 CDR3 环的 RMSD 作为 nanobody 预测精度的核心指标，比全局 RMSD 更能反映功能相关精度。

3. **F_para 分析**：通过计算 restraints 中活性残基对实验 paratope 的覆盖率，定量评估 paratope 定义的质量，可用于优化对接输入。

### 对课题方向的启示

1. **AI 预测与物理对接的互补性**：本文证明，当 AI 端到端预测（AF2M）失败时，AI 预测单体 + 信息驱动对接可以成功。这提示在蛋白质结构预测研究中，混合策略（AI 生成构象 + 物理方法筛选/优化）可能比单一方法更鲁棒。

2. **评分函数是共同瓶颈**：无论是 AI 方法还是 docking 流程，"生成正确模型但无法识别"是普遍问题。这指向了开发更好的模型排序/评分方法的重要性，是值得投入的研究方向。

3. **数据泄漏控制**：本文严格选择训练截止日期后的结构作为基准，这种"时间分割"策略值得在类似 benchmark 研究中推广，以避免高估 AI 方法性能。

4. **多链抗原建模缺口**：AF2M 在多链抗原上的失败提示，当前 AI 方法对多链复合物的链间取向预测不足，是值得关注的技术缺口。