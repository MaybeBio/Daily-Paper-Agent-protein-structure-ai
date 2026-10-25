## 01 基本信息
- **标题**: Energy Landscape Sampling Reveals Ligand-Dependent Structural Dynamics of the Protease-Activated Receptor 1
- **作者**: Schwerin, Inken Kaja; Jiang, Shihai; Staubert, Claudia; Isermann, Berend; Kunze, Georg
- **单位**: 未提供（推测为莱比锡大学，基于致谢信息）
- **期刊/平台**: Journal of Chemical Information and Modeling
- **年份**: 2026（在线日期 2026-10-23）
- **论文类型**: 研究论文（计算模拟 + 实验验证）
- **领域**: GPCR 结构生物学、增强采样分子动力学、构象能量景观
- **关键词**: PAR1, GPCR, string method with swarms of trajectories, free-energy landscape, enhanced sampling MD, biased signaling
- **DOI/arXiv**: 10.1021/acs.jcim.6c01315
- **代码**: stringmethod-swarms-trajectories (https://github.com/delemottelab/stringmethod-swarms-trajectories)
- **数据**: 未提供（PDB 结构引用：3VW7, 8XOR）
- **阅读日期**: 2026-11-04
- **在课题方向中的位置**: 本文属于「蛋白质结构相关计算研究 × 物理模拟 (MD)」交叉方向，具体为 GPCR 构象能量景观的增强采样研究。其核心方法（SMwST）与可迁移的「配体-受体-转导蛋白三体互作」分析框架，对蛋白质结构预测、构象采样与生成、分子对接等课题均有直接参考价值。

## 02 一句话总结
本文使用 string method with swarms of trajectories (SMwST) 增强采样 MD 模拟，以五个跨膜螺旋距离为集合变量，量化了五种配体状态下 PAR1 的构象自由能景观，揭示了拮抗剂 vorapaxar 和钠离子稳定非活性态、tethered agonist 稳定活性态并促进 TM6 位移达 ~1 nm 的配体依赖性构象调控机制，并通过 Gq-CASE BRET 实验验证了关键残基的功能。

## 03 研究问题
- **具体问题**: 不同细胞外配体（tethered agonist、TRAP、vorapaxar）及 G 蛋白结合如何调节 PAR1 的构象能量景观？配体信号如何从细胞外结合口袋传播至细胞内 G 蛋白偶联界面？
- **为什么重要**: PAR1 是血栓形成、炎症等过程中的关键 GPCR 靶点。理解其配体依赖性构象动力学是设计通路选择性（biased）PAR1 调节剂的基础，可区分有害（血栓）与有益（细胞保护）信号。
- **现有方法不足**: 静态晶体/cryo-EM 结构仅提供离散的活性/非活性快照，无法揭示中间态、能量壁垒及配体对构象系综的定量影响；常规 MD 模拟时间尺度不足以采样 GPCR 激活这类稀有事件。
- **精确研究问题 (Can ... ?)**: Can enhanced-sampling MD simulations with carefully selected collective variables quantitatively resolve how different extracellular ligands and Gαq binding reshape the conformational free-energy landscape of PAR1 and identify the structural pathway linking ligand engagement to G-protein coupling?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」的 GPCR 计算研究通用脉络，结合本文框架）*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|---|---|---|---|---|
| 静态结构解析 | X-ray 晶体学 (3VW7)、cryo-EM (8XOR) | 原子级分辨率、明确活性/非活性态 | 仅离散快照、无法反映动态系综 | 提供起止结构参考 |
| 常规 MD | 无偏模拟 (μs 级) | 原子级动力学、无需先验 | 采样不足、难以跨越能量壁垒 | 用于验证 SMwST 采样一致性 |
| 增强采样 MD | 靶向 MD (tMD)、伞形采样、元动力学 | 加速稀有事件采样 | 依赖 CV 选择、可能引入偏倚 | tMD 用于生成初始路径 |
| 路径采样方法 | String method with swarms of trajectories (SMwST) | 同时优化路径与自由能、适用于高维 CV 空间 | 计算成本高、需良好初始路径 | **本文核心方法** |
| 实验验证 | 定点突变 + BRET 报告系统 | 功能相关性验证 | 间接、无法提供原子级机制 | Gq-CASE BRET 实验 |

**本文主张的位置**: 首次将 SMwST 系统应用于 PAR1，在五种配体状态下比较自由能景观，并整合实验验证，填补了 PAR1 构象动力学研究的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 构象景观未知 | PAR1 的配体依赖性构象能量景观此前未被量化 | 缺乏适用于 GPCR 激活的增强采样方案；PAR1 特有的 tethered agonist 机制增加建模复杂度 | Abstract: "the ligand-dependent conformational energy landscape governing PAR1 activation remains poorly understood" |
| 静态结构局限 | 现有结构仅显示非活性与活性态，中间态未知 | 晶体/cryo-EM 捕获的是热力学稳定态，无法反映动态过渡 | Introduction: "existing structures have revealed inactive and active conformations" |
| 配体效应难以区分 | 不同配体（拮抗剂 vs 激动剂）对构象系综的影响不明确 | 缺乏系统比较多种配体状态的自由能景观研究 | Results: 五种配体状态的系统比较 |
| 信号传播路径不明 | 从细胞外配体结合到细胞内 G 蛋白偶联的结构传导通路未定义 | 中间态和过渡路径未被采样 | Results: "continuous activation pathway linking extracellular ligand engagement to intracellular motifs" |
| 计算预测缺乏验证 | 模拟预测的残基功能未经过实验检验 | 计算与实验方法之间的整合不足 | Results: Gq-CASE BRET 实验验证 |

## 06 核心思想
1. **表面方法**: 使用 SMwST 增强采样 MD，以五个跨膜螺旋 Cα-Cα 距离为集合变量，对 PAR1 的六种系统（apo、tethered agonist、TRAP、VPX、VPX+Na⁺、TRAP+Gαq）进行构象采样，计算自由能景观，并通过 Gq-CASE BRET 实验验证关键残基。

2. **核心洞察**: 
   - PAR1 在 apo 状态下具有内在构象灵活性，可同时采样非活性、中间和活性样状态——GPCR 的激活不是「开关」而是「系综重分布」。
   - 配体通过**差异化调节特定微开关基序**（而非整体稳定/去稳定）来重塑能量景观：VPX 主要限制 TM5/TM6 重排，钠离子消除中间态盆地，tethered agonist 则通过稳定 TM6 位移和 ICL3 重组织来锁定活性态。
   - **氯离子协调**在非活性态稳定中起重要作用，提示离子可作为 GPCR 构象调节的「第四配体」。
   - Gαq 结合通过约束 TM6 动力学来「选择」活性样构象，体现受体-转导蛋白的双向别构效应。

3. **可能的普适教训** [Analysis]: 
   - 对 GPCR 或其他构象动态蛋白，**单一静态结构不足以描述功能**；能量景观视角可解释 biased signaling 等复杂现象。
   - **集合变量的选择决定采样质量**：本文基于 GPCR 保守激活机制（TM5/TM6/TM7 重排）选择 CV，而非任意几何量，是方法成功的关键。
   - **计算-实验闭环**（模拟预测 → 突变验证）是建立机制可信度的有效范式，可迁移至其他蛋白系统的功能研究。

## 07 方法总览
- **输入**: 
  - 起始结构：VPX 结合 PAR1 晶体结构 (PDB: 3VW7, 中间态)、PAR1-Gαq-TRAP cryo-EM 结构 (PDB: 8XOR, 活性态)、AlphaFold2 预测结构 (GPCRdb, 非活性态)
  - 配体：tethered agonist（SFLLRN 序列）、TRAP 肽、vorapaxar (VPX)、Na⁺、Cl⁻
  - Gαq 亚基（核苷酸-free 状态）
- **输出**: 
  - 六种系统的自由能景观（投影到 a100 指数和 Y-Y 距离等）
  - 最小自由能路径上的构象系综
  - 关键残基/基序的构象分布
  - 实验验证的突变效应数据
- **模块**:
  1. 结构准备（PDB 处理、质子化、AlphaFold2-Multimer 建模 tethered agonist）
  2. MD 系统构建（CHARMM-GUI, POPC 膜, TIP3P 水, 0.15 M NaCl, charmm36m 力场, CGenFF 参数化 VPX）
  3. 靶向 MD (tMD) 生成初始路径（250 ns, 10,000 kJ·mol⁻¹·nm⁻² 力常数）
  4. SMwST 迭代优化（42 images, 30 swarms/image, 10 ps/swarm, 300 次迭代）
  5. 自由能计算（转移概率矩阵 → 平稳分布 → Boltzmann 关系）
  6. PCA 特征重要性分析（1320 构象, Cα-Cα 距离矩阵）
  7. 实验验证（定点突变 + Gq-CASE BRET）
- **工具**: GROMACS 2021, PLUMED 2.7.1, CHARMM-GUI, mdTraj, pyEMMA, MDAnalysis, Demystify
- **假设**: 
  - 所选 5 个 CV 足以描述 PAR1 激活的主要慢运动
  - AlphaFold2 模型可作为合理的非活性态代表
  - 核苷酸-free Gαq 能近似生理相关的受体-G 蛋白相互作用
- **流程**: 结构准备 → 系统构建 → tMD 初始路径 → SMwST 迭代 → 自由能景观分析 → PCA 特征识别 → 突变验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 结构准备与 AlphaFold2-Multimer 建模 | 生成 tethered agonist 共价连接模型、补齐缺失结构 | 实验结构缺乏 tethered agonist 结合构象；需一致的非活性参考态 | 输入：3VW7, 8XOR, AlphaFold2 模型；输出：六种 MD 起始结构 | Methods: "AlphaFold2-Multimer was employed, using the PAR1-Gαq structure (PDB: 8XOR) as an input template" | 无法模拟 tethered agonist 状态；非活性参考态不准确 |
| tMD 初始路径生成 | 产生连接非活性与活性态的初始构象链 | SMwST 需要合理的初始路径以避免局部最优 | 输入：非活性/活性端结构；输出：40 个均匀分布的初始构象 | Methods: "tMD employed a biasing force based on the rmsd to a defined target conformation" | 初始路径偏差可能导致 SMwST 收敛到错误路径 |
| SMwST 迭代优化 | 在 CV 空间中优化路径并计算自由能 | 核心增强采样方法，克服稀有事件采样瓶颈 | 输入：初始路径 + 6 个 MD 系统；输出：收敛的路径 + 自由能景观 | Results: 300 次迭代收敛；与无偏 MD 验证一致 | 无法获得定量自由能景观；仅能定性描述 |
| 自由能计算 (pyEMMA) | 从转移矩阵计算平稳分布和自由能 | 将轨迹数据转化为热力学量 | 输入：swarm 轨迹；输出：ΔG 景观 | Methods: "Transition probability matrices, free-energy surfaces, and error estimates... calculated using the pyEMMA package" | 无法定量比较配体效应 |
| PCA 特征重要性分析 | 识别激活过程中贡献最大的残基/距离 | 从高维数据中提取关键结构基序 | 输入：1320 构象的 Cα-Cα 距离矩阵；输出：特征贡献排序 | Results: "identified ECL2, TM5, TM6, TM7, and ICL3 as the regions undergoing the most pronounced conformational changes" | 无法系统识别关键残基，实验验证缺乏靶点 |
| Gq-CASE BRET 实验 | 验证模拟预测的残基功能 | 建立计算预测与功能的相关性 | 输入：突变体构建；输出：Gq 激活效力/效能 | Results: 突变显著改变 Gq 激活（图 6, 表 S2） | 计算预测缺乏功能验证，机制可信度降低 |

## 09 关键公式符号
| 公式 | 符号含义 | 用途 | 直觉 | 来源指针 |
|---|---|---|---|---|
| T_ij = N_ij / Σ_k N_ik | T_ij: 状态 i→j 转移概率; N_ij: 转移计数 | 构建转移概率矩阵 | 从 swarm 轨迹中统计状态间转移频率 | Methods: Free-Energy Calculation |
| ΔG_i = -k_B · T · log(ρ_i) | ΔG_i: 状态 i 自由能; k_B: 玻尔兹曼常数; T: 温度; ρ_i: 平稳分布 | 从平稳分布计算自由能 | 高概率状态对应低自由能 | Methods: Free-Energy Calculation |
| a100 index = 线性组合(5 个 Cα-Cα 距离) | 5 个跨膜螺旋间距离的加权和 | 量化 GPCR 激活状态 | 基于 GPCR 保守激活机制的复合几何描述符 | Methods: "the a100 index is defined as a linear combination of five interhelical Cα–Cα distances" |
| Frobenius norm | 矩阵范数 | 量化相邻迭代路径间差异，判断收敛 | 路径变化小于阈值即收敛 | Methods: "Convergence between consecutive strings was assessed by computing the Frobenius norm" |

## 10 实验设计与证据链
- **数据集/群体**: 
  - 计算：6 个 MD 系统（apo, +tethered agonist, +TRAP, +VPX, +VPX+Na⁺, +TRAP+Gαq），每个系统 42 个 image × 30 swarms × 10 ps/迭代 × 300 迭代
  - 实验：HEK293T PAR1-KO 细胞，8 个突变体 + WT
- **指标**: 
  - 计算：自由能差 (ΔΔG)、a100 指数分布、Y-Y 距离分布、TM6 位移、关键距离变化
  - 实验：Gq 激活的 E_max 和 pEC50
- **基线**: 
  - 计算：apo 状态作为配体效应的基线；无偏 MD (14.2 μs) 验证 SMwST 采样一致性
  - 实验：WT PAR1 作为突变体比较的基线
- **评测协议**: 
  - 计算：自由能景观比较、构象系综重叠度、路径收敛性
  - 实验：3 次独立实验，3 个技术重复，95% CI 统计
- **骨干/仪器**: GROMACS 2021 + PLUMED 2.7.1（计算）；BMG VANTAstar 读板器（实验）
- **oracle 输入**: 实验结构 (3VW7, 8XOR) 作为 MD 起始/目标构象；AlphaFold2 模型作为非活性参考

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 五种配体状态自由能景观比较 | 配体差异调节 PAR1 构象景观 | apo vs tethered agonist vs TRAP vs VPX vs VPX+Na⁺ | VPX+Na⁺ 消除中间态；tethered agonist 稳定活性态 | 配体通过不同机制重塑能量景观 | 未直接比较所有配体的结合亲和力 | Results 图 2 |
| TM6 位移分析 | tethered agonist 促进 TM6 位移 | apo vs tethered agonist 的 TM6 位移分布 | tethered agonist 使 TM6 位移达 ~1 nm | tethered agonist 稳定活性态 TM6 构象 | 未量化位移的动力学时间尺度 | Results: "promotes TM6 displacement of up to ∼1 nm" |
| 氯离子协调分析 | Cl⁻ 稳定非活性态 | 有无 Cl⁻ 的 KRK 基序构象比较 | Cl⁻ 协调与 KRK 紧凑构象相关 | Cl⁻ 可能作为非活性态稳定因子 | 未直接突变 Cl⁻ 结合位点验证 | Results: "intracellular chloride ion coordination contributing to inactive-state stabilization" |
| Gαq 结合效应 | Gαq 约束 TM6 动力学 | TRAP vs TRAP+Gαq 的 TM6 柔性 | Gαq 降低 TM6 柔性并稳定活性样构象 | 转导蛋白反向稳定受体活性态 | 未测试 Gαi/Gα12/13 等替代转导蛋白 | Results 图 5 |
| 无偏 MD 验证 | SMwST 采样与无偏模拟一致 | SMwST 构象 vs 14.2 μs 无偏 MD 构象 | 构象空间显著重叠 | SMwST 采样可靠 | 无偏 MD 仅从活性态出发 | Results: "substantial overlap in the space defined by the first two principal components" (图 S5) |
| 突变 + Gq-CASE BRET | 模拟预测残基的功能相关性 | 8 个突变体 vs WT 的 Gq 激活 | Y3507.32A, S2995.67A, S3156.37A 显著降低 E_max | 模拟识别的残基确实参与激活/G 蛋白偶联 | 未测试对 Gi 或 arrestin 通路的选择性 | Results 图 6, 表 S2 |

## 11 结论正确解读
- **任务范围**: 本研究聚焦 PAR1 的 TM 区构象重排，未覆盖胞外 N-端 tethered agonist 的完整折叠动力学、脂质环境异质性、以及 Gαq 之外转导蛋白（Gαi, Gα12/13, arrestin）的竞争性结合。
- **oracle/真值输入**: 使用实验结构 (3VW7, 8XOR) 和 AlphaFold2 模型作为参考；AlphaFold2 模型虽经 GPCRdb 验证，但仍是计算预测，可能引入非活性态偏差。
- **端到端状态**: 计算模拟 + 实验验证已形成闭环，但实验仅验证了 Gq 通路，未覆盖 PAR1 的其他信号通路（如 β-arrestin）。
- **算力成本**: 6 个系统 × 42 images × 30 swarms × 10 ps × 300 迭代 ≈ 22.7 μs 总采样时间（不含 tMD 和无偏 MD），属于中等规模增强采样计算。
- **历史数据依赖**: 依赖 GPCRdb 的 AlphaFold2 模型和已有实验结构；CV 选择基于 β2AR 的保守激活机制，可能不完全适用于 PAR1 特有构象。
- **模型依赖**: 力场 (charmm36m)、水模型 (TIP3P)、膜组成 (POPC) 均为简化；未包含胆固醇、PI(4,5)P2 等可能调节 GPCR 构象的脂质。
- **最难情形**: 中间态构象的精确自由能值、氯离子结合的自由能贡献、Gαq 结合引起的构象变化幅度。
- **群体/领域边界**: 结论限于 PAR1 在 POPC 膜、0.15 M NaCl、310.15 K 条件下的构象行为；外推至其他 GPCR 或体内环境需谨慎。
- **有边界的复述**: 在 POPC 膜环境中，PAR1 的 apo 状态具有内在多构象性；VPX 通过限制 TM5/TM6 重排和维持 KRIT-Cl⁻ 协调来稳定非活性态；tethered agonist 通过促进 TM6 位移和 ICL3 重组织来稳定活性态；Gαq 结合进一步约束 TM6 动力学。这些预测得到了 Gq 通路突变实验的部分验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 有限采样时间 | 增强采样依赖预定义 CV，可能遗漏正交慢运动 | 更长采样时间、更全面的 CV 集 | Conclusion: "rely on predefined CVs and finite string resolution, which may bias the explored pathways and overlook slower orthogonal motions" |
| 力场精度 | charmm36m 可能无法完全准确描述 GPCR 构象平衡 | 多力场交叉验证 | Conclusion: "Force-field limitations" |
| AlphaFold2 模型偏差 | 非活性态参考结构为计算预测 | 更多实验非活性态结构 | Conclusion: "the use of an AlphaFold-modeled inactive structure" |
| 缺乏完整细胞环境 | 未包含膜异质性、翻译后修饰、竞争性转导蛋白 | 更复杂的膜/细胞环境模拟 | Conclusion: "absence of full cellular context, including membrane heterogeneity, additional post-translational modifications, and competing transducers" |
| Gαq 模型简化 | 使用核苷酸-free 单体 Gαq，未包含 Gβγ 和完整异源三聚体 | 全异源三聚体模拟 | Conclusion: "performed in the nucleotide-free state and with a monomeric Gαq subunit" |
| 实验验证范围有限 | 仅验证了 Gq 通路，未覆盖其他信号通路 | 扩展至 Gi、G12/13、arrestin 通路 | Results: 仅 Gq-CASE BRET 实验 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| CV 选择基于 β2AR 保守机制 | PAR1 可能有独特的激活构象变化未被所选 CV 捕捉 | CV 偏差是增强采样方法的核心风险 | 使用机器学习方法（如 VAMPnets）自动识别 CV；或与无偏 MD 的构象分布对比 | Methods: "This CV set was previously derived by Fleetwood et al. based on feature importance analysis of long unbiased (de)activation simulations of the β2AR" |
| AlphaFold2 模型作为非活性参考 | AlphaFold2 可能偏向中间态或非天然构象 | 非活性端点的准确性影响整个路径和自由能景观 | 与更多实验非活性结构（如突变体、不同拮抗剂结合态）交叉验证 | Methods: "an AlphaFold2-predicted PAR1 structure provided by GPCRdb, which adopts a more strongly inactive conformation" |
| 氯离子作用为相关性而非因果性 | Cl⁻ 协调可能只是非活性态的伴随现象而非稳定因素 | 若 Cl⁻ 是因果性稳定因子，则可能是药物设计靶点 | 突变 Cl⁻ 配位残基 + 无 Cl⁻ 条件的 MD 模拟 + 实验验证 | Results: "intracellular chloride ion coordination contributing to inactive-state stabilization" |
| Gαq 模型缺少 Gβγ 和核苷酸状态 | Gβγ 可能影响受体-Gα 界面构象；核苷酸状态改变 Gα 构象 | 转导蛋白结合效应可能被高估或低估 | 全异源三聚体模拟；不同核苷酸状态比较 | Methods: "nucleotide-free Gαq subunit" |
| 实验验证仅覆盖 Gq 通路 | 模拟预测的残基可能对 Gi 或 arrestin 通路有不同贡献 | PAR1 的 biased signaling 机制需要多通路验证 | 扩展至 Gi-CASE、arrestin 招募实验 | Results: 仅 Gq-CASE BRET |
| 无偏 MD 仅从活性态出发 | 无偏 MD 验证可能遗漏从非活性态出发的转变 | 验证 SMwST 采样完整性的证据不充分 | 从多个起始构象（非活性、中间）运行无偏 MD | Results: "starting from the equilibrated active-state PAR1 structure" (图 S5) |
| 未报告力场参数验证 | charmm36m 对 GPCR 的适用性未在本文中验证 | 力场误差可能影响自由能定量 | 与实验突变效应、药理学数据对比 | Methods: "The charmm36m force field was used" |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **SMwST 工作流**（可迁移至其他构象动态蛋白）: tMD 生成初始路径 → 迭代优化路径 → 转移矩阵计算自由能 → PCA 特征识别。该流程适用于任何具有明确非活性/活性端点的蛋白系统，尤其适合 GPCR、激酶等构象开关蛋白。

2. **CV 选择策略**: 基于保守激活机制（TM5/TM6/TM7 重排）而非任意几何量选择 CV，是采样成功的关键。可迁移至其他 GPCR 或同源蛋白：先通过序列/结构比对识别保守功能基序，再设计 CV。

3. **配体效应比较框架**: 在相同 CV 空间下系统比较多种配体状态的自由能景观，可定量区分「系综重分布」vs「单一构象稳定化」机制。该框架可迁移至任何配体-受体系统的 biased signaling 研究。

4. **计算-实验闭环设计**: 模拟预测关键残基 → 定点突变 → 功能实验验证。该范式可迁移至其他蛋白系统，尤其适合验证计算模型预测的「非直观」残基（如本文的 Y3507.32、S3156.37）。

5. **离子作为构象调节因子**: Cl⁻ 在 KRK 基序的协调与非活性态稳定相关，提示在 MD 模拟中应显式包含生理相关离子，而非仅用中和盐。可迁移至其他含正电荷簇的蛋白系统。

6. **AlphaFold2 模型的合理使用**: 将 AF2 预测结构作为非活性参考态，但需通过 GPCRdb 等工具验证其激活状态分类。可迁移至其他缺乏实验非活性结构的蛋白系统。

7. **Gαq 单体的计算可行性**: 使用核苷酸-free Gαq 单体（而非全异源三聚体）即可捕捉受体-转导蛋白界面的关键相互作用，大幅降低计算成本。可迁移至其他 GPCR-G 蛋白或 GPCR-arrestin 复合物研究。

8. **多投影分析策略**: 将自由能景观投影到多个互补描述符（a100、Y-Y 距离、TM6 位移等），可揭示单一投影可能遗漏的构象子状态。可迁移至任何高维自由能景观分析。

## 15 与已有知识连接
- **相似方法**: Fleetwood et al. 在 β2AR 上开发的 SMwST 工作流和 CV 集（本文直接继承）；Delemotte lab 的 stringmethod-swarms-trajectories 代码库。
- **相似系统**: PAR1 的 cryo-EM 结构 (PDB: 8XOR, 与 Gαq 复合)；VPX 结合结构 (PDB: 3VW7)；其他 GPCR 的增强采样研究（如 β2AR、A2AR 的 metadynamics 研究）。
- **组合/互补**: 本文的 SMwST 自由能景观可与 Markov state models (MSMs) 结合，获得更长时间尺度的动力学信息；与机器学习势函数（如 AlphaFold 3 或 MACE）结合可提高采样效率。
- **冲突/竞争**: 本文的 Cl⁻ 稳定非活性态假说与经典「Na⁺ 作为负别构调节剂」模型（Na⁺ 稳定非活性态）存在张力，提示不同离子可能在不同 GPCR 中扮演不同角色。
- **可迁移领域**: 
  - 结构预测: AF2 模型作为非活性参考态的策略可迁移至其他 GPCR 或膜蛋白
  - 构象采样/生成: SMwST 工作流可迁移至其他构象动态蛋白
  - 分子对接: 配体对构象系综的调节效应可指导诱导契合对接策略
  - MD 模拟: 离子显式包含、Gαq 单体建模策略可迁移至其他 GPCR 研究
  - 序列/结构设计: 识别的关键残基（Y3507.32, S3156.37 等）可作为设计 biased 调节剂的靶点

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**: 基于机器学习的 PAR1 集合变量自动发现
   - **来源局限/观察**: 本文 CV 基于 β2AR 保守机制，可能遗漏 PAR1 特有构象变化
   - **核心假设**: 使用 VAMPnets 或 SRV 从无偏 MD 轨迹中自动学习的 CV 能更全面描述 PAR1 激活
   - **初步方法**: 运行长无偏 MD → 训练 VAMPnet → 与本文 CV 集对比 → 用 SMwST 验证新 CV
   - **验证方式**: 新 CV 下的自由能景观与实验突变数据一致性
   - **创新状态**: unverified

2. **候选名称**: 氯离子作为 GPCR 构象调节因子的系统研究
   - **来源局限/观察**: 本文发现 Cl⁻ 与非活性态稳定相关，但未系统验证
   - **核心假设**: Cl⁻ 通过静电屏蔽 KRK 基序正电荷来稳定非活性态，该机制在其他 GPCR 中保守
   - **初步方法**: 对多个 GPCR 进行 Cl⁻ 浓度梯度 MD 模拟 → 比较 KRK 基序构象 → 突变验证
   - **验证方式**: 实验测量不同 Cl⁻ 浓度下的 G 蛋白激活效率
   - **创新状态**: unverified

3. **候选名称**: PAR1 偏向信号的结构决定因素图谱
   - **来源局限/观察**: 本文仅验证了 Gq 通路，未覆盖 Gi/arrestin 通路
   - **核心假设**: 不同配体（tethered agonist vs TRAP vs 合成肽）通过稳定不同构象子状态来偏向不同下游通路
   - **初步方法**: 对多种配体状态进行 SMwST 采样 → 比较构象系综差异 → 识别通路特异性微开关 → 设计偏向性配体
   - **验证方式**: 多通路 BRET 实验（Gq, Gi, arrestin）
   - **创新状态**: unverified

4. **候选名称**: AlphaFold 3 预测的 PAR1-配体复合物与增强采样 MD 的交叉验证
   - **来源局限/观察**: 本文使用 AF2 单体模型作为非活性参考，未利用 AF3 的复合物预测能力
   - **核心假设**: AF3 预测的 PAR1-配体复合物可作为 SMWST 的初始路径端点，提高采样效率
   - **初步方法**: AF3 预测 PAR1 与 tethered agonist/VPX/TRAP 的复合物 → 与实验结构对比 → 作为 SMWST 端点
   - **验证方式**: 预测复合物与实验结构的 RMSD、自由能景观一致性
   - **创新状态**: unverified

5. **候选名称**: 膜脂环境对 PAR1 构象景观的调节
   - **来源局限/观察**: 本文使用 POPC 单一膜成分，未考虑胆固醇、PIP2 等
   - **核心假设**: 胆固醇通过调节 TM 区疏水匹配来影响 PAR1 的构象平衡
   - **初步方法**: 不同膜组成（POPC, POPC/胆固醇, POPC/PIP2）下的 SMWST 采样 → 比较自由能景观
   - **验证方式**: 与实验膜流动性数据、突变体功能数据对比
   - **创新状态**: unverified

6. **候选名称**: 基于能量景观的 PAR1 偏向性激动剂虚拟筛选
   - **来源局限/观察**: 本文揭示了配体对构象景观的调节机制，但未用于药物设计
   - **核心假设**: 能稳定特定构象子状态的化合物可产生偏向性信号
   - **初步方法**: 虚拟筛选 → 对候选化合物进行 SMWST 采样 → 评估构象偏好 → 实验验证
   - **验证方式**: 多通路功能实验
   - **创新状态**: unverified