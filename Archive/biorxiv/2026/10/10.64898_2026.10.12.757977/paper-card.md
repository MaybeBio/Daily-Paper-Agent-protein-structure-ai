## 01 基本信息

- **标题**：Generative design of functional disordered regions in a developmental transcription factor
- **作者**：Denes LT; Emenecker R; Wang N; Chirumamilla D; Mohotti R; Holehouse AS; Holt LJ; Lionnet T
- **单位**：NYU Grossman School of Medicine（纽约大学格罗斯曼医学院，含 Lionnet、Holt、Holehouse 实验室）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（研究论文）
- **领域**：蛋白质计算设计 × 固有无序区域（IDR）功能设计 × 转录因子 × 干细胞分化
- **关键词**：intrinsically disordered regions (IDRs), generative design, transcription factor, RUNX2, conformational ensemble, chromatin binding, osteogenesis, coarse-grained MD simulation, FINCHES, GOOSE
- **DOI/ID**：10.64898/2026.10.12.757977
- **代码**：GitHub (timotheelionnet/RUNX2_generative_design)
- **数据**：测序数据已提交 GEO；MD 和单分子追踪数据通过 Zenodo 提供
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文是「IDR 功能设计 × 构象系综 × 转录因子染色质结合」交叉方向的代表性工作。它将蛋白质结构设计中的「以构象为设计目标」思路推广到无序蛋白区域，用粗粒化 MD 模拟（Mpiri 力场）刻画构象系综，以 FINCHES 交互图作为可微设计代理，结合 GOOSE 序列优化器实现 de novo IDR 生成。对「蛋白质结构相关计算研究 × AI/物理模拟」课题的启示在于：IDR 功能可由系综级特征（而非线性基序）编码，且构象系综可作为生成设计的可计算目标。

---

## 02 一句话总结

本文以 RUNX2 的 C 端 IDR（CIDR）为模型，证明转录因子 IDR 的成骨分化功能不依赖线性基序而依赖构象系综特征（吸引/排斥亚结构域组织），并基于粗粒化 MD 模拟（Mpiri）与 FINCHES 交互图相似性作为设计目标，用 GOOSE 序列优化器生成 de novo 功能性 IDR，其中 2/6 的合成变体完全恢复了 RUNX2 驱动的矿化表型。

---

## 03 研究问题

- **具体问题**：IDR 的序列如何编码生物学功能？能否基于生物物理原理（而非线性基序）对功能性 IDR 进行 de novo 生成设计？
- **为什么重要**：约 35% 的人类蛋白质组为无序区域，转录因子中 IDR 占比更高（约 55%）。现有 AI 结构设计方法对 IDR 无效，IDR 功能设计远落后于折叠蛋白设计。若能建立 IDR 序列→构象系综→功能的映射，将极大扩展可设计蛋白质空间。
- **现有方法为何不足**：
  - AlphaFold 等结构预测工具对 IDR 给出低置信度或无结构预测，无法提供设计目标；
  - 现有 IDR 设计工具（如 SLiM 基序设计、统计序列生成）多针对线性基序或单一物化参数（如电荷、疏水性），缺乏对构象系综的系统刻画；
  - 报告基因筛选（如 VP16、ZIM3 等）在异源环境中评估 IDR 活性，无法捕捉细胞类型/染色质环境依赖的功能。
- **精确研究问题**：Can conformational ensemble features of an IDR serve as a sufficient design target to generate de novo sequences that recapitulate the native IDR's biological function in its endogenous cellular context?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」+「本文框架」混合标注。

1. **IDR 功能编码的早期模型（2010s）**：IDR 功能被认为主要由 SLiMs（短线性基序）介导，通过基序氨基酸在折叠结合口袋中的配位实现特异性结合（Davey et al., 2012; Van Roey et al., 2014）。代表性方法：SLiM 预测与突变扫描。局限：无法解释无基序 IDR 的功能。
2. **分子语法与组成驱动模型（2015-2020）**：提出 IDR 的氨基酸组成和排列模式（"molecular grammar"）决定相分离、结合等行为（Lin et al., 2015; Martin et al., 2020）。代表性方法：基于组成的 IDR 设计（如酸性/疏水性富集）。局限：缺乏对构象系综的直接刻画，预测精度有限。
3. **粗粒化 MD 模拟用于 IDR 系综（2018-2023）**：Mpiri、CALVADOS 等残基级粗粒化力场可快速生成 IDR 构象系综，提供半径回旋、接触图等系综级描述符（Mittal et al., 2018; Joseph et al., 2021）。局限：模拟与功能之间的映射关系尚未建立。
4. **IDR 生成设计工具的出现（2022-2024）**：GOOSE（Emenecker et al., 2024）支持多目标序列优化；FINCHES（Emenecker et al., 2024）提供基于平均场相互作用的快速交互图预测。局限：设计目标多为物化参数而非功能。
5. **本文位置（2026）**：首次将「构象系综相似性」作为 IDR 生成设计的目标函数，在 RUNX2 内源细胞环境中验证 de novo IDR 的功能，建立「系综→功能」的直接因果链。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| IDR 功能设计缺乏明确目标 | 现有设计工具以线性基序或单一物化参数为目标，无法捕捉 IDR 的多体、分布式相互作用 | IDR 功能由构象系综的集体特征编码，而非单一序列特征 | Results 图 2（LocScr 实验）；Discussion 第 1 段 |
| 报告基因筛选无法捕捉内源功能 | VP16、ZIM3、ARGFX 等异源激活/抑制结构域均无法替代 CIDR 驱动矿化 | IDR 功能依赖细胞类型/染色质环境，异源报告系统无法反映 | Results 图 1F；Discussion 第 2 段 |
| 序列保守性 ≠ 功能保守性 | 高度保守的 CIDR 中线性基序可被扰乱而不影响功能 | 功能由系综级化学性质编码，而非特定氨基酸序列 | Results 图 2C（28 个 tile 扰乱均保留功能） |
| 粗粒化模拟与功能之间缺乏桥梁 | MD 模拟可生成系综但无法直接指导设计 | 需要将系综压缩为可优化的目标（如 FINCHES 交互图） | Results 图 5A-D；Methods「Generative IDR design」 |
| 现有 IDR 设计成功率低 | 多数 de novo IDR 无功能 | 仅匹配物化参数不足以编码功能；需要匹配系综级交互模式 | Results 图 5E（6 个设计中 2 个完全功能） |

---

## 06 核心思想

**1) 表面方法**：
- 以 RUNX2 CIDR 为模型，通过 28 个 tile 扰乱、亚结构域删除/替换、以及 de novo 生成设计，系统测试 IDR 序列特征与功能的关系。
- 使用粗粒化 MD（Mpiri 力场）生成构象系综，计算接触图/距离图作为系综描述符。
- 使用 FINCHES 交互图作为快速代理，以「与 WT 交互图相似性」为设计目标，结合 GOOSE 序列优化器生成 de novo IDR。
- 功能读出：hMSC 成骨分化矿化表型、ChIP-seq 染色质结合、RNA-seq 基因表达、单分子追踪（SMT）染色质结合动力学。

**2) 核心洞察**：
- **IDR 功能由系综级化学性质编码，而非线性基序**：28 个 tile 全部扰乱（LocScr1）仍保留功能，说明无单一基序是必需的。
- **吸引/排斥亚结构域组织是功能的关键**：MD 模拟揭示 CIDR 内存在吸引性 patch（芳香族富集）和排斥性 linker（带电/甘氨酸-丝氨酸富集）交替的架构；扰乱 linker 或 patch 均导致功能丧失。
- **构象系综可作为生成设计的目标**：以 FINCHES 交互图相似性为目标生成的 de novo 序列，尽管与 WT 无序列同源性，仍能恢复染色质结合和成骨功能。
- **IDR 介导染色质结合是功能的核心机制**：CIDR 缺失导致 RUNX2 无法结合染色质，而 de novo 设计恢复结合。

**3) 可能的普适教训 [Analysis]**：
- 对 IDR 功能设计而言，「系综级描述符」比「序列级描述符」更接近功能决定因素；这提示本课题方向（蛋白质结构计算 × AI）可考虑将构象系综（而非单一结构）作为设计/预测的目标。
- FINCHES 交互图作为 MD 系综的快速代理，展示了「慢速精确模拟 → 快速可微代理 → 生成设计」的三级范式，可迁移到其他 IDR 设计问题。
- 内源细胞环境的功能验证（而非异源报告基因）是 IDR 设计的关键评估标准；这提示计算设计需与细胞/体内验证闭环。

---

## 07 方法总览

**输入**：
- RUNX2 CIDR 序列（残基 230–521，292 残基）
- 15 个突变/扰乱变体序列（tile 扰乱、linker/patch 突变、de novo 设计）

**输出**：
- 各变体的成骨分化矿化表型（定量）
- ChIP-seq 染色质结合谱、RNA-seq 基因表达谱
- SMT 单分子结合动力学参数
- MD 模拟构象系综（接触图、距离图）
- de novo 设计序列（6 个候选）

**模块**：
1. **功能筛选平台**：RUNX2 KO hMSC + 稳定表达 iRUNX2 变体 → 14 天成骨分化 → 矿化定量
2. **序列扰动策略**：tile 扰乱（28 个 8-11 aa tile）、局部扰乱（LocScr1-4）、linker/patch 突变
3. **粗粒化 MD 模拟**：Mpiri 力场，LAMMPS，300K，3 µs/复制 × 3 复制
4. **系综分析**：接触概率图、距离图、亚结构域划分（patch/linker）
5. **生成设计**：GOOSE + FINCHES 交互图相似性目标，固定/自由组成两种模式
6. **基因组学验证**：ChIP-seq（FLAG 标签）、RNA-seq、SMT

**文字流程**：
1. 构建 RUNX2 KO hMSC 克隆 → 验证无法成骨分化
2. 稳定表达 WT/突变 RUNX2 → 诱导分化 → 定量矿化
3. 对功能丧失的突变体进行 MD 模拟 → 识别系综特征差异
4. 以 WT 系综特征为设计目标 → GOOSE 生成 de novo 序列 → 筛选
5. 对 de novo 设计进行功能验证（矿化、ChIP-seq、RNA-seq、SMT）

**假设**：
- Mpiri 粗粒化模拟能捕捉 IDR 系综的功能相关特征
- FINCHES 交互图与 MD 系综特征足够相关，可作为快速设计代理
- 成骨分化矿化表型是 CIDR 功能的忠实读出

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| RUNX2 KO hMSC 平台 | 建立 CIDR 功能缺失背景 | 在内源环境中评估 CIDR 变体功能 | 输入：RUNX2 KO 克隆；输出：可诱导表达 RUNX2 变体的稳定细胞系 | Results 图 1C-E；Methods「Cell culture」「Generation of RUNX2 knockout lines」 | 无法在内源环境中评估 CIDR 功能；异源报告系统可能遗漏染色质依赖功能 |
| 矿化定量读出 | 定量成骨分化表型 | 提供 CIDR 功能的高通量定量读出 | 输入：分化 14 天细胞；输出：BoneTag 荧光定量 | Results 图 1D-E；Methods「Mineralization assay」 | 无法区分部分功能丧失；需要更精细的分子读出 |
| Tile 扰乱策略 | 测试线性基序必要性 | 区分基序依赖 vs 系综依赖功能 | 输入：28 个 tile 扰乱变体；输出：功能表型 | Results 图 2C；Methods「Generation of iRUNX2 rescue lines」 | 无法排除基序冗余；需要组合扰乱 |
| 粗粒化 MD 模拟（Mpiri） | 生成构象系综 | 提供系综级结构描述符 | 输入：CIDR 序列；输出：接触图、距离图、亚结构域划分 | Results 图 3A-B；Methods「Molecular dynamics simulations」 | 无法获得原子级分辨率；粗粒化模型可能遗漏关键相互作用 |
| FINCHES 交互图 | 快速预测系综交互特征 | 作为 MD 的快速代理，使生成设计可行 | 输入：候选序列；输出：交互图（ε 矩阵） | Results 图 5C-D；Methods「Generative IDR design」 | 生成设计不可行（MD 太慢）；或设计目标不准确 |
| GOOSE 序列优化器 | 生成 de novo IDR 序列 | 在序列空间中搜索满足系综约束的候选 | 输入：目标交互图 + 约束；输出：候选序列 | Results 图 5D-E；Methods「Generative IDR design」 | 无法生成候选序列；或生成序列不满足约束 |
| ChIP-seq + RNA-seq | 验证染色质结合和基因表达 | 建立 CIDR 功能与染色质结合的因果链 | 输入：分化 4 天细胞；输出：全基因组结合谱和表达谱 | Results 图 4D-G；Methods「CHIPseq」「RNAseq」 | 无法区分直接/间接效应；需要 SMT 补充动力学信息 |
| SMT 单分子追踪 | 测量染色质结合动力学 | 区分稳定结合 vs 瞬时扫描 | 输入：HaloTag-RUNX2 细胞；输出：结合分数、扩散系数 | Results 图 4C；Methods「Single molecule tracking」 | 无法获得空间分辨率；需要 ChIP-seq 补充位置信息 |

---

## 09 关键公式符号

**1) Mpiri 力场非键相互作用（Wang-Frenkel 势）**：
\[
E_{WF}(r) = \epsilon \left( \frac{\sigma}{r} \right)^{2\mu} - \epsilon \left( \frac{\sigma}{r} \right)^{\mu} + \epsilon/4
\]
- \( r \)：残基间距离
- \( \sigma \)：残基对特征距离
- \( \epsilon \)：相互作用强度（由残基类型决定）
- \( \mu = 2, \nu = 1 \)：固定指数
- 用途：描述 IDR 残基间非键相互作用
- 直觉：短程吸引 + 排斥核，参数由氨基酸类型决定
- 来源：Methods「Molecular dynamics simulations」

**2) 接触概率**：
\[
P(i,j) = \frac{1}{T} \sum_{t=1}^{T} \mathbb{1}[d_{ij}(t) < 8\,Å]
\]
- \( d_{ij}(t) \)：第 \( t \) 帧残基 \( i, j \) 间距离
- \( T \)：总帧数
- 用途：构建接触图
- 来源：Methods「Molecular dynamics simulations」

**3) 超额接触（excess contacts）**：
\[
\Delta P(i,j) = P(i,j) - B(|i-j|)
\]
- \( B(s) \)：序列间隔为 \( s \) 的所有残基对的平均接触概率
- 用途：去除序列间隔对接触概率的基线影响，识别富集/贫乏接触的残基
- 来源：Methods「Molecular dynamics simulations」

**4) FINCHES 交互图（ε 矩阵）**：
\[
\epsilon_{ij} = f(a_i, a_j)
\]
- \( a_i, a_j \)：残基 \( i, j \) 的氨基酸类型
- \( f \)：由 Mpiri 力场参数化的平均场交互强度
- 用途：作为 MD 系综的快速代理，用于生成设计目标
- 来源：Methods「Generative IDR design」

**5) 设计目标函数（GOOSE）**：
\[
\mathcal{L} = w_1 \cdot \text{corr}(\epsilon_{\text{cand}}, \epsilon_{\text{WT}}) + w_2 \cdot \text{disorder}(\text{cand}) + w_3 \cdot \text{identity}(\text{cand}, \text{WT})
\]
- 具体权重未在文中给出，但目标包含：与 WT 交互图的相关性、无序性、序列同一性上限
- 来源：Methods「Generative IDR design」

---

## 10 实验设计与证据链

**数据集/群体**：
- hMSC（ASC52telo 永生化人骨髓间充质干细胞）
- RUNX2 KO 克隆（CRISPR-Cas9 靶向外显子 6）
- 15 个 CIDR 变体（28 个 tile 扰乱、4 个局部扰乱、linker/patch 突变、6 个 de novo 设计）

**规模**：
- 每个变体 3 个独立克隆 × 3 次独立分化实验
- ChIP-seq：每变体 3 个克隆，约 41-50.5M read pairs/文库
- RNA-seq：18 个文库（6 变体 × 3 克隆）
- MD 模拟：每变体 3 个复制 × 3 µs

**指标**：
- 矿化定量（BoneTag 荧光）
- ChIP-seq 峰数、峰强度、差异结合
- RNA-seq 差异表达基因数
- SMT 结合分数（bound fraction）、扩散系数
- MD 接触图/距离图相似性（Pearson 相关）

**基线**：
- WT RUNX2（阳性对照）
- RUNX2 KO（阴性对照）
- R193G（DBD 功能丧失突变）
- ΔCIDR（CIDR 缺失）

**评测协议**：
- 矿化：第 14 天 BoneTag 染色定量
- ChIP-seq：FLAG 标签 IP，对照为 KO 或 IgG
- SMT：PA-JF549 光激活，6000 帧/细胞，≥4 细胞/变体/天 × 3 天

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| RUNX2 KO 验证 | CIDR 对成骨分化必需 | KO vs WT vs ΔCIDR | KO 和 ΔCIDR 均无矿化 | CIDR 是成骨分化所必需 | 不能区分 CIDR 在哪个步骤（结合/激活）起作用 | Results 图 1E |
| 异源效应结构域替换 | CIDR 功能可被通用激活/抑制结构域替代 | VP16/ZIM3/ARGFX 替换 CIDR | 均无法完全恢复矿化 | CIDR 功能超出简单转录激活/抑制 | 不能排除 CIDR 有多个功能域 | Results 图 1F |
| 28-tile 扰乱 | 线性基序是否必需 | 每个 tile 单独扰乱 | 所有 28 个变体均保留功能 | 无单一线性基序是必需的 | 不能排除多个冗余基序 | Results 图 2C |
| 局部扰乱（LocScr1-4） | 局部序列顺序是否必需 | 4 个局部扰乱变体 | LocScr1 功能保留；其他部分丧失 | 局部序列顺序在部分区域重要 | 不能确定哪些区域关键 | Results 图 2F |
| 全扰乱（FullScr） | 全局序列顺序是否必需 | 全序列扰乱 | 功能丧失 | 全局序列顺序对功能重要 | 不能区分是组成还是顺序 | Results 图 2F |
| MD 模拟 + 系综比较 | 功能与系综特征相关 | WT vs 功能/非功能变体 | 功能变体系综相似，非功能变体偏离 | 系综特征是功能预测因子 | 相关性不等于因果性 | Results 图 3A-B |
| linker/patch 突变 | 亚结构域功能 | L1-4mut, P1-4mut | L2mut, P3mut 功能丧失 | 特定 linker/patch 对功能必需 | 不能排除间接效应 | Results 图 3C-D |
| SMT 结合分数 | CIDR 影响染色质结合 | WT vs ΔCIDR vs L2mut vs P3mut | 功能丧失变体结合分数降低 | CIDR 介导染色质结合 | 不能区分直接结合 vs 间接稳定 | Results 图 4C |
| ChIP-seq 峰分析 | CIDR 影响全基因组结合 | WT vs 变体 | 功能丧失变体峰减少，尤其在低可及性区域 | CIDR 促进不可及染色质结合 | 不能排除 DBD 间接效应 | Results 图 4D-J |
| de novo 设计 | 系综目标可生成功能 IDR | 6 个设计 vs WT | 2/6 完全功能 | 系综目标足以指导功能设计 | 成功率低，需优化 | Results 图 5E |

---

## 11 结论正确解读

- **任务范围**：本文结论限于 RUNX2 CIDR 在 hMSC 成骨分化中的功能；不适用于所有 IDR 或所有转录因子。
- **Oracle/真值输入**：功能真值为矿化表型（BoneTag 定量），这是成骨分化的终端读出，但非直接分子活性测量；ChIP-seq 和 SMT 提供中间分子证据。
- **端到端状态**：设计流程是「MD 模拟 → FINCAES 代理 → GOOSE 优化 → 实验验证」的闭环，但 MD 模拟和 FINCHES 代理均非端到端可微；设计目标（交互图相似性）是系综特征的代理，非直接功能目标。
- **算力成本**：MD 模拟（3 µs × 3 复制 × 16 序列）计算量较大；FINCHES 代理显著加速设计迭代，但文中未报告具体加速比。
- **历史数据依赖**：设计依赖 WT CIDR 的 MD 系综作为目标；对无已知功能 IDR 的 de novo 设计需额外策略。
- **模型依赖**：结论依赖 Mpiri 粗粒化力场的准确性；更精细的力场或显式溶剂模拟可能改变系综特征。
- **最难情形**：文中承认 de novo 设计成功率仅 2/6，且功能丧失的设计仍可能匹配 WT 系综（说明系综相似性非充分条件）。
- **群体/领域边界**：结论基于 hMSC 体外分化模型；体内成骨或其他细胞类型中 CIDR 功能可能不同。
- **有边界的复述**：在 hMSC 成骨分化模型中，RUNX2 CIDR 的功能不依赖任何单一线性基序，而依赖其构象系综中吸引/排斥亚结构域的组织；以 FINCHES 交互图相似性为目标的 de novo 设计可生成功能性 IDR，但成功率有限，且系综相似性不足以完全预测功能。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 仅测试了体外分化模型 | 结论限于 hMSC 成骨分化，未在体内验证 | 未明确提及 | Discussion 第 3 段 |
| de novo 设计成功率有限 | 6 个设计中仅 2 个完全功能 | 需要更好的系综模型和设计目标 | Discussion 第 4 段 |
| 系综相似性非功能充分条件 | 部分功能丧失变体仍匹配 WT 系综 | 需要更高分辨率的系综描述符 | Discussion 第 4 段 |
| 粗粒化模型精度有限 | Mpiri 力场可能遗漏原子级相互作用 | 未明确提及 | Methods「Molecular dynamics simulations」 |
| 无法排除冗余基序 | 28 个 tile 单独扰乱均保留功能，但可能存在冗余基序 | 未明确提及 | Results 图 2C 讨论 |
| CIDR 功能机制未完全阐明 | 染色质结合是重要机制，但具体分子互作未完全解析 | 未明确提及 | Discussion 第 2 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 矿化表型作为功能读出的粒度 | 矿化是终端表型，可能掩盖中间步骤（如 DNA 结合、转录激活）的差异 | 若 CIDR 变体在中间步骤有差异但最终矿化相同，会低估系综-功能关系 | 增加中间读出：ChIP-seq 峰强度、RNA-seq 特定基因表达、SMT 结合动力学 | Results 图 1D-E |
| 28 个 tile 扰乱均保留功能 | 可能因为 tile 扰乱未充分破坏局部序列特征（如疏水簇） | 若扰乱策略不够彻底，会高估「基序不必要」的结论 | 使用更激进的扰乱（如随机化整个 CIDR）或计算预测基序后定向突变 | Results 图 2C |
| MD 模拟与功能的相关性 | 系综相似性可能反映的是序列组成相似性而非构象特征 | 若系综差异主要由组成驱动，则「构象设计」的增量价值有限 | 控制组成的随机序列对照；比较组成相同但系综不同的序列 | Results 图 3A-B |
| FINCHES 代理的准确性 | FINCHES 交互图与 MD 系综的相关性未在文中充分验证 | 若代理不准确，设计目标可能偏离真实系综 | 系统比较 FINCHES 预测与 MD 模拟的交互图 | Methods「Generative IDR design」 |
| de novo 设计成功率低 | 2/6 的成功率可能受限于设计目标（交互图相似性）而非系综本身 | 若目标不充分，需要更好的系综描述符或功能代理 | 尝试其他系综描述符（如半径回旋分布、接触序）作为设计目标 | Results 图 5E |
| SMT 和 ChIP-seq 的样本量 | 每变体 3 个克隆、≥4 细胞/变体，统计功效可能有限 | 若样本量不足，可能错过中等效应 | 增加克隆数和细胞数；使用混合效应模型 | Methods「Single molecule tracking」 |
| 未报告阴性 de novo 设计的系综特征 | 功能丧失的 de novo 设计是否偏离 WT 系综？ | 若阴性设计也匹配 WT 系综，说明系综相似性非充分条件 | 对阴性设计进行 MD 模拟和系综比较 | Results 图 5E |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **系综级描述符可作为 IDR 设计目标**：本文证明「构象系综相似性」（通过 FINCHES 交互图近似）可作为 IDR 生成设计的可计算目标。可迁移到本课题：对任意 IDR，可先通过 MD 模拟（Mpiri/CALVADOS 等）建立 WT 系综特征，再以交互图相似性为约束进行序列生成。

2. **吸引/排斥亚结构域组织是 IDR 功能的关键编码维度**：RUNX2 CIDR 的功能依赖 patch（芳香族富集）和 linker（带电/甘氨酸-丝氨酸）的交替组织，而非线性基序。可迁移：在设计 IDR 时，应关注残基类型的空间分布模式（patch/linker 架构），而非仅序列组成或单一物化参数。

3. **内源细胞环境是 IDR 功能评估的必要条件**：异源报告基因（VP16、ZIM3、ARGFX）无法替代 CIDR 功能，说明 IDR 功能依赖细胞类型/染色质环境。可迁移：在 IDR 设计验证中，应优先使用内源/生理相关读出，而非通用报告系统。

4. **粗粒化 MD + 快速代理 + 生成优化的三级范式**：MD 模拟（慢速精确）→ FINCHES 代理（快速近似）→ GOOSE 优化（生成设计）的流程，可推广到其他 IDR 设计问题。可迁移：对计算资源有限的研究，可先训练/验证代理模型，再用于大规模序列搜索。

5. **功能丧失突变体的系综差异可定位关键区域**：通过比较功能/非功能变体的 MD 系综，可识别对功能重要的亚结构域。可迁移：在 IDR 功能映射中，结合 MD 模拟和功能筛选可高效定位关键区域。

6. **IDR 设计成功率有限，需多目标优化**：6 个设计中仅 2 个完全功能，说明系综相似性非充分条件。可迁移：IDR 设计需结合多个目标（系综、组成、基序、可溶性等），并可能需要实验筛选闭环。

7. **ChIP-seq + SMT 可建立 IDR-染色质结合的因果链**：本文通过 ChIP-seq（位置）和 SMT（动力学）互补验证 CIDR 对染色质结合的作用。可迁移：在研究 IDR 介导的染色质结合时，应同时测量空间（ChIP-seq）和时间（SMT）维度。

8. **序列保守性 ≠ 功能保守性**：高度保守的 CIDR 中线性基序可被扰乱而不影响功能，提示 IDR 的进化约束可能作用于系综级特征而非序列。可迁移：在 IDR 保守性分析中，应关注系综特征（如交互图）的保守性而非序列同一性。