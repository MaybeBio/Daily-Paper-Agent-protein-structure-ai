## 01 基本信息
- **标题**：Quantum-accurate enhanced sampling and mini-protein folding through replica exchange for multiscale neural network potentials
- **作者**：Solazzo, Riccardo; Gordiy, Igor; Riniker, Sereina
- **单位**：未提供（推测为 ETH Zürich，Riniker 课题组）
- **期刊/平台**：Chemical Science
- **年份**：2026
- **论文类型**：方法学 + 应用验证
- **领域**：计算化学 / 生物物理 / 机器学习势函数 / 增强采样
- **关键词**：Neural network potentials (NNPs), ML/MM, REST2, enhanced sampling, mini-protein folding, chignolin, CLN025
- **DOI/arXiv**：10.1039/d6sc04555c
- **代码**：https://github.com/rinikerlab/rest2_ampmm
- **数据**：起始坐标、配置文件、运行代码在 GitHub；原始 MD 数据可向通讯作者索取
- **阅读日期**：2026-11-10
- **在本课题方向中的位置**：该文将经典增强采样方法 REST2 与 ML/MM 多尺度神经网络势（AMPv3-EE-BMS25）结合，实现了无需预定义反应坐标的 mini-protein 折叠模拟，处于「AI 势函数 × 增强采样 × 构象采样」交叉点，为蛋白质结构预测/构象生成提供了新工具。

## 02 一句话总结
该文提出一种与 ML/MM 框架兼容的 REST2 类副本交换增强采样算法（REST2-AMP/MM），通过直接缩放 NNP 能量项实现选择性溶质升温，在保持近 DFT 精度的同时，成功从伸展构象自主折叠 chignolin 和 CLN025 两个 mini-protein。

## 03 研究问题
- **具体问题**：如何将 REST2 类增强采样算法推广到 ML/MM 多尺度神经网络势框架中，以实现无需预定义反应坐标的高精度构象采样和 mini-protein 折叠？
- **为什么重要**：ML/MM 模拟虽具近 QM 精度，但计算成本仍高于经典力场，且生物相关构象转变（如蛋白质折叠）涉及高能垒，需要增强采样才能在实际时间尺度内完成。现有增强采样方法（如 metadynamics、umbrella sampling）需要预定义反应坐标，对未知折叠路径的系统不适用。
- **现有方法不足**：
  - 反应坐标类方法（metadynamics 等）需先验知识，不适用于未知构象空间。
  - 温度副本交换（TRE）需要大量副本，计算成本高。
  - 标准 QM/MM 哈密顿量不可分离，无法直接应用 REST2 的参数缩放策略。
  - 尚无 REST2 类方法被实现于 ML/MM 框架。
- **精确研究问题**：Can a REST2-like replica exchange scheme be implemented for ML/MM simulations by directly scaling the NNP energy terms, and can it enable reaction-coordinate-free folding of mini-proteins with near-DFT accuracy?

## 04 背景与发展脉络
> 注：此脉络基于本文引言及作者引用，经外部核验部分已标注。

1. **QM/MM 多尺度模拟（1976–至今）**：Levitt, Warshel, Karplus 提出 QM/MM 方案，在关键区域保持 QM 精度，环境用 MM 描述。局限：计算成本高，时间尺度受限。
2. **神经网络势（NNP）兴起（2011–至今）**：从 Behler-Parrinello 到等变架构（如 NequIP、MACE），NNP 以接近 QM 精度、远低于 QM 成本的优势成为 QM 替代方案。AMP 系列模型（Anisotropic Message Passing）支持静电嵌入，适合 ML/MM。
3. **增强采样方法发展**：
   - 反应坐标类：umbrella sampling、metadynamics、WE 等，需先验知识。
   - 广义系综类：TRE、REST/REST2 等，无需反应坐标，但 TRE 副本数多、成本高。
   - REST2 通过仅升温溶质、保持溶剂温度，大幅减少副本数，已在经典力场中广泛应用。
4. **ML/MM 增强采样现状**：已有工作将 metadynamics 等与 ML/MM 结合，但均需反应坐标；广义系综类方法在 ML/MM 中尚属空白。
5. **本文位置**：首次将 REST2 类算法实现于 ML/MM 框架，利用 AMP 模型哈密顿量的可分解性，直接缩放能量项而非力场参数，填补了「ML/MM × 广义系综增强采样」的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| ML/MM 模拟时间尺度受限 | 生物相关构象转变（如折叠）涉及高能垒，常规 MD 无法在可及时间内跨越 | NNP 虽比 QM 快，但仍比经典力场慢数个数量级；高能垒需要增强采样 | Introduction: "ML/MM MD simulations remain slower than those with classical force fields... will require the use of enhanced-sampling techniques" |
| 现有增强采样需反应坐标 | metadynamics、umbrella sampling 等需预定义集体变量，对未知折叠路径不适用 | 反应坐标类方法本质依赖先验知识 | Introduction: "a key limitation of these methods is the requirement for a priori knowledge of the process" |
| 标准 QM/MM 哈密顿量不可分离 | 无法将溶质/溶剂能量项独立缩放 | QM 区域的能量来自单一 SCF 计算，不可分解 | Introduction: "no such decomposition is available for a standard electrostatic-embedding QM/MM Hamiltonian" |
| REST2 参数缩放策略不适用于 NNP | NNP 无显式力场参数（电荷、LJ ε、扭转常数）可缩放 | NNP 的能量由网络内部表征，参数不可直接映射到物理量 | Results: "This parameter-level route is not available to AMP: all multipoles... are predicted internally by the NNP rather than assigned as fixed parameters" |
| 高缩放因子下结构不稳定 | 强升温可能导致键长/键角非物理畸变 | 溶质内能大幅降低后，缺乏维持几何完整性的机制 | Results: "U_r represents optional scaled harmonic bond and angle restraints, which are applied to prevent unphysical distortions" |

## 06 核心思想
**1) 表面方法**：
- 将 REST2 算法适配到 AMP/MM 框架，通过直接缩放 NNP 输出的能量项（EML 和 EML–MM）实现选择性溶质升温。
- 引入可选的缩放谐波键/角约束（Ur），在高缩放因子下维持结构完整性。
- 使用标准 Metropolis 判据进行副本交换，保持详细平衡。

**2) 核心洞察**：
- AMP 模型的哈密顿量天然可分解为 EML（ML 区内部）、EML–MM（ML-MM 相互作用）和 EMM（MM 区内部）三项，这为 REST2 所需的能量项独立缩放提供了物理基础。
- 与经典力场不同，NNP 没有可缩放的显式参数，但能量项本身是可微函数，可以直接缩放——这绕过了参数级缩放的限制。
- 缩放 EML 和 EML–MM 等价于降低溶质内能和溶质-溶剂相互作用，从而有效升温溶质，而溶剂保持物理温度。

**3) 可能的普适教训 [Analysis]**：
- 对于任意可分解哈密顿量的 ML 势（不仅是 AMP），只要能量项可分离，REST2 类方法即可推广。这为其他等变 NNP（如 MACE、NequIP）与增强采样的结合提供了通用路径。
- 自适应约束策略（随缩放因子增强）是维持高升温下结构完整性的通用技巧，可迁移到其他广义系综方法。
- 该方法不依赖反应坐标，意味着它可以作为「盲」探索工具，用于未知构象空间的采样——这对蛋白质结构预测/构象生成的初始阶段尤其有价值。

## 07 方法总览
- **输入**：溶质初始构象（PDB 或建模结构）、溶剂盒子（TIP4P-FB 水）、REST2 参数（缩放因子范围、副本数、交换频率）、AMP-BMS 模型权重
- **输出**：副本交换轨迹（含所有副本）、最低副本（λ=1）的构象系综、自由能景观、NOE 距离验证
- **模块**：
  1. **AMP-BMS 势函数模块**：计算 EML（ML 区）和 EML–MM（ML-MM 相互作用），支持静电嵌入
  2. **REST2 缩放模块**：对 EML 和 EML–MM 施加 γm 缩放，对 Ur 施加 ηm 缩放
  3. **副本交换模块**：相邻副本间按 Metropolis 判据尝试交换
  4. **约束模块**：可选的缩放谐波键/角约束，防止高缩放下结构畸变
  5. **分析模块**：Ramachandran 图、自由能景观、NOE 距离计算、RMSD 追踪
- **训练**：无训练过程，使用预训练的 AMP-BMS 全局模型（在 BMS25 数据集上训练）
- **工具**：OpenMM/8.1.2 + OpenMM-PyTorch/1.4.97，MDTraj/1.10.3 分析，PyEMMA/2.5.12 自由能计算
- **流程**：
  1. 构建溶质-溶剂体系，能量最小化
  2. NVT 平衡 100 ps，NPT 平衡 1 ns
  3. 运行 REST2-AMP/MM 生产模拟（副本间每 100 步尝试交换）
  4. 分析最低副本轨迹，计算构象系综和自由能景观
  5. 与实验 NOE 数据对比验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AMP-BMS 势函数 | 计算 ML 区能量和 ML-MM 相互作用 | 提供近 DFT 精度的能量和力 | 输入：原子坐标、元素类型；输出：EML、EML–MM | Table S1: 与 QM/MM 参考计算一致 | 无法进行 ML/MM 模拟，退回经典力场精度 |
| REST2 能量缩放 | 对 EML 和 EML–MM 施加 γm 缩放 | 等效升温溶质，降低能垒 | 输入：EML、EML–MM、γm；输出：缩放后能量 | Results 图 2C：高副本展示更广 ϕ/ψ 覆盖 | 退化为常规 ML/MM MD，无法跨越高能垒 |
| 副本交换 | 相邻副本间按 Metropolis 判据交换 | 实现构象在副本间的传递，最终在最低副本获得正确系综 | 输入：相邻副本能量差、温度；输出：交换接受/拒绝 | 平均交换接受率 17%（alanine dipeptide） | 副本间无通信，高副本采样无法传递到最低副本 |
| 谐波键/角约束 | 在高缩放因子下维持键长/键角 | 防止强升温导致结构非物理畸变 | 输入：键/角坐标、ηm；输出：约束能量 Ur | Results: "prevent unphysical distortions of bonds and angles in highly scaled replicas" | 高缩放副本可能产生非物理构象，导致交换接受率下降或结构破坏 |
| 自适应约束缩放 | ηm 随 γm 减小而增大 | 在升温增强时同步加强结构约束 | 输入：γm；输出：ηm | 图 S1 | 高缩放副本结构完整性无法保证 |

## 09 关键公式符号
**1. AMP/MM 哈密顿量分解**：
H(x) = EML(x) + EML–MM(x) + EMM(x)

- x：体系坐标
- EML：ML 区（溶质）内部能量，由 NNP 计算
- EML–MM：ML 区与 MM 区（溶剂）的相互作用能量
- EMM：MM 区内部能量（溶剂-溶剂）

**2. REST2 缩放哈密顿量**：
Hm(x) = γm·EML(x) + √γm·EML–MM(x) + EMM(x) + ηm·Ur(x)

- γm ∈ (0,1]：副本 m 的缩放因子，γ1 = 1 为未缩放参考副本
- √γm：对 EML–MM 的缩放（源自 REST2 理论，保证溶质有效温度 T/γm）
- ηm：约束缩放因子，随 γm 减小而增大
- Ur：谐波键/角约束能量

**3. 交换判据**（Metropolis 判据）：
Δmn = (γm − γn)·[EML(xn) − EML(xm)] + (√γm − √γn)·[EML–MM(xn) − EML–MM(xm)] + (ηm − ηn)·[Ur(xn) − Ur(xm)]

- 接受概率：min(1, e^(−Δmn))
- 该式确保详细平衡，是副本交换正确性的理论基础

**4. 距离 RMSD（RMSDdist）**：
RMSDdist = √[(1/N_pairs) · Σ_{i<j} (d_ij(t) − d_ij(ref))²]

- N_pairs：唯一原子对总数
- d_ij(t)：t 时刻原子 i、j 间距离
- d_ij(ref)：参考结构中对应距离

**5. NOE 距离计算**：
r_eff = ⟨r^(−6)⟩^(−1/6)

- r_i：第 i 帧的瞬时原子对距离
- N：总帧数
- 用于与实验 NOE 上界对比验证

## 10 实验设计与证据链
**数据集/体系**：
1. Alanine dipeptide（20 ns REST2，8 副本；对照 160 ns 常规 MD + 7×20 ns 独立常规 MD）
2. Cyclo-(Pro–Ser–Leu–Asp–Val)（cis/trans 两种异构体，各 50 ns REST2 和常规 MD，8 副本）
3. Polyproline（13 个脯氨酸，50 ns REST2，12 副本）
4. Trp-cage mini-protein（PDB: 1L2Y，50 ns REST2 和常规 MD，12 副本）
5. Chignolin（PDB: 1UAO，50 ns REST2，12 副本）
6. CLN025（PDB: 2RVD，50 ns REST2，12 副本）

**指标**：
- Ramachandran 图 ϕ/ψ 分布覆盖
- 副本交换接受率
- 往返分析（round-trip）
- Cα-RMSD 时间演化
- NOE 距离违反
- 自由能景观（Rg, RMSDdist）

**基线/对照**：
- 常规 AMP/MM MD（cAMP/MM）
- 实验 NMR 结构（PDB）
- 实验 NOE 距离

**评测协议**：
- 折叠模拟从完全伸展构象开始
- 最低副本（γ=1）用于系综分析
- NOE 分析使用 r^(−6) 平均

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| Alanine dipeptide 构象采样 | REST2 增强 ϕ/ψ 空间探索 | REST2（8 副本，20 ns）vs 常规 MD（160 ns + 7×20 ns） | REST2 在 1 ns 内采样到常规 MD 150 ns 才访问的区域；高副本覆盖更广 | REST2 显著提升构象采样效率 | 未证明系综完全收敛 | Results 图 2C,D；图 S4,S10 |
| Cyclo-peptide NOE 验证 | AMP-BMS 精度足以复现实验构象 | cis/trans 各 50 ns REST2 vs 常规 MD vs 实验 NOE | 两种模拟均满足实验 NOE 约束 | AMP-BMS 对环肽构象描述准确 | 未比较不同 NNP 架构 | Results 图 3C |
| Polyproline 结构修复 | REST2 可从错误折叠恢复天然构象 | α-螺旋起始 → 50 ns REST2 | PII 群体从 0 升至 ~0.90，αR 群体降至 ~0 | REST2-AMP/MM 可修复错误折叠结构 | 未证明 PII 是全局自由能最低态 | Results 图 4B,C |
| Trp-cage 部分重折叠 | REST2 可修复局部错误折叠 | 螺旋→线圈突变起始 → 60 ns REST2 | Cα-RMSD 从 >0.5 nm 降至 ~0.15–0.20 nm | 方法可恢复天然螺旋结构 | 未进行完整去折叠-重折叠循环 | Results 图 5C |
| Chignolin 自主折叠 | 无需反应坐标即可折叠 mini-protein | 伸展构象起始 → 50 ns REST2 | Cα-RMSD 降至 ~0.2 nm，达到天然态 | REST2-AMP/MM 实现无偏自主折叠 | 未证明折叠路径唯一性或系综收敛 | Results 图 7A |
| CLN025 自主折叠 | 同上（更快折叠突变体） | 伸展构象起始 → 50 ns REST2 | Cα-RMSD 降至 ~0.2 nm，NOE 满足 | 方法可重复折叠不同 mini-protein | 未比较折叠速率与实验值 | Results 图 6B,C,D |

## 11 结论正确解读
- **任务范围**：仅验证了肽类体系（二肽、环肽、多脯氨酸、mini-protein），未涉及大蛋白或核酸。
- **oracle/真值输入**：AMP-BMS 为预训练全局模型，未针对目标体系微调；实验 NMR 结构作为参考真值。
- **端到端状态**：方法端到端可用（输入序列/结构 → 输出折叠构象），但依赖预训练势函数的泛化能力。
- **算力成本**：作者未提供详细基准，但指出 NNP 比 QM/MM 快数个数量级；REST2 比 TRE 副本数少（8–12 vs 通常数十个）。
- **历史数据依赖**：AMP-BMS 在 BMS25 数据集上训练，对非肽类或非常规残基的适用性未验证。
- **模型依赖**：方法依赖 AMP 架构的哈密顿量可分解性；其他 NNP 需验证是否支持类似分解。
- **最难情形**：作者承认未实现完整折叠-去折叠循环，未证明热力学收敛；对慢折叠蛋白或大蛋白的适用性未知。
- **有边界的复述**：该文证明 REST2 类增强采样可与 ML/MM 结合，在近 DFT 精度下实现 mini-protein 的无偏折叠，但结论限于肽类体系、特定势函数和模拟时间尺度（50 ns）。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未证明热力学收敛 | 折叠模拟显示达到稳定平台，但未进行多次独立折叠-去折叠循环 | 需更长模拟和更多重复验证系综收敛 | Results: "should not be interpreted as convergence of the complete thermodynamic ensemble" |
| 选择性缩放受限于 ML 区定义 | 当前实现中，缩放区域与 ML 区绑定，无法对 ML 区内部子区域选择性升温 | 可扩展为类似 gREST 的局部升温策略 | Results: "the tempered region is tied to the ML region in the current implementation" |
| 大体系效率问题 | 全蛋白置于 ML 区时，升温自由度多，可能降低效率 | 建议对大体系采用选择性缩放策略 | Conclusions: "tempering the full protein may become inefficient for large systems" |
| 训练数据依赖 | AMP-BMS 在 BMS25 上训练，对非肽类体系适用性未知 | 未明确提及 | Conclusions: "dependence on the training set" |
| 计算成本仍高于经典力场 | NNP 比经典力场慢，增强采样进一步增加成本 | 未明确提及 | Conclusions: "NNPs remain computationally more demanding than classical force fields" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 折叠成功可能依赖势函数精度而非增强采样 | AMP-BMS 本身可能已足够准确，常规 MD 在更长时间内也可能折叠 | 需区分增强采样和势函数对折叠的贡献 | 用相同势函数运行更长常规 MD 对比折叠时间 | Results 图 6,7 未提供常规 MD 折叠对照 |
| 未报告副本交换的往返时间分布 | 仅报告平均接受率 17%，未分析副本遍历性 | 接受率高但遍历性差可能导致采样偏差 | 计算副本索引的自相关时间和往返分布 | Results 仅提及接受率 |
| 折叠判据依赖 Cα-RMSD 单一指标 | RMSD 达到 ~0.2 nm 可能不代表完整天然态（侧链 packing 未验证） | 折叠正确性需多维度验证 | 计算全原子 RMSD、接触图、二级结构含量 | Results 图 6,7 仅显示 Cα-RMSD |
| 未与实验折叠速率定量比较 | 未报告折叠时间常数与实验值对比 | 无法评估模拟时间尺度的物理真实性 | 用 Markov 状态模型估计折叠速率并与实验比较 | Results 未提及 |
| 未测试势函数对非天然构象的鲁棒性 | 伸展构象可能不在训练分布内，势函数外推行为未知 | 外推错误可能导致虚假折叠路径 | 检查伸展构象的能量分布和力一致性 | 未提供 |
| 未进行系综收敛的严格检验 | 未使用多重独立模拟或分块分析验证系综稳定性 | 单次轨迹可能陷入亚稳态 | 运行 3–5 次独立折叠模拟，检查系综间差异 | Results 仅报告单次轨迹 |

## 13 学到什么
**Agent 提炼的知识候选**：

1. **哈密顿量可分解性是 ML/MM 增强采样的关键**：选择或设计 ML 势时，优先考虑能量项可分离的架构（如 AMP 的 EML/EML–MM 分解），这为增强采样提供了天然接口。

2. **能量级缩放替代参数级缩放**：当 ML 势无可缩放的显式参数时，直接缩放能量项是可行替代方案——这为其他 NNP 架构（MACE、NequIP 等）与 REST2 结合提供了思路。

3. **自适应约束策略**：在高缩放因子下引入随升温强度增强的谐波约束，可有效防止结构畸变，且不扰动目标系综（约束仅作用于高副本）。

4. **无偏折叠验证协议**：从伸展构象出发的折叠模拟 + NOE 距离验证 + 自由能景观分析，是验证 ML/MM 增强采样方法有效性的可迁移实验设计。

5. **REST2 参数选择经验**：缩放因子范围（1 到 0.33–0.5）和副本数（8–12）在肽类体系中有效，可作为其他体系的起点。

6. **对蛋白质结构预测的启示**：该方法可作为 AlphaFold 等预测结构的「精修」工具，从低质量预测出发，通过无偏采样修复错误折叠区域。

7. **对构象生成的启示**：无需反应坐标的增强采样可用于生成多样化的构象系综，为下游对接或自由能计算提供输入。

## 15 与已有知识连接
- **REST2 原始方法**：Wang, L.; Friesner, R. A.; Berne, B. J. J. Phys. Chem. B 2011, 115, 9431–9438。本文将其从经典力场推广到 ML/MM 框架。
- **AMP 系列模型**：Anisotropic Message Passing (AMP) 系列，支持静电嵌入和极化，本文使用其 AMPv3-EE-BMS25 变体。
- **ML/MM 多尺度模拟**：与 QM/MM 类似，但用 ML 势替代 QM 计算；本文的 REST2 实现填补了该领域增强采样的空白。
- **mini-protein 折叠基准**：chignolin 和 CLN025 是常用的折叠模拟基准体系，已有大量经典力场和 ML 势研究（如 D.E. Shaw 组的 Anton 超算工作）。
- **无偏折叠模拟**：与 Lindorff-Larsen 等人的经典力场无偏折叠工作形成对比，本文展示了 ML/MM 精度下的无偏折叠可能性。
- **AlphaFold 精修**：本文提出的结构精修能力与 AlphaFold 预测结构的 MD 精修方向相关，可作为后续工作基础。
- **候选方向**：将 REST2-AMP/MM 扩展到酶催化反应（需排除反应中心约束）、IDP 构象采样、以及与其他 NNP 架构（MACE、NequIP）的结合。

## 16 研究想法
**Agent 生成的研究候选**：

1. **名称**：REST2-AMP/MM 在酶催化反应中的应用
   - **来源局限/观察**：作者指出约束可选择性施加，反应区域可保持未约束
   - **核心假设**：REST2-AMP/MM 可加速酶活性位点的构象搜索，同时保持反应坐标区域的 QM 精度
   - **初步方法**：以 AMP-BMS 描述酶-底物复合物，对反应中心原子不施加约束，对远端残基施加升温
   - **验证方式**：与 QM/MM 元动力学结果对比自由能面
   - **创新状态**：unverified

2. **名称**：REST2-AMP/MM 用于 IDP 构象系综生成
   - **来源局限/观察**：作者提到 AMP-BMS 对 IDP 熔解曲线有定性重现，但采样不足
   - **核心假设**：REST2 增强采样可改善 IDP 构象系综的收敛性
   - **初步方法**：对 IDP 进行 REST2-AMP/MM 模拟，与 SAXS/FRET 实验数据对比
   - **验证方式**：系综平均 SAXS 曲线与实验对比
   - **创新状态**：unverified

3. **名称**：选择性升温策略用于大蛋白结构精修
   - **来源局限/观察**：作者承认全蛋白升温对大体系效率低
   - **核心假设**：仅对预测结构的高不确定性区域（如 loop、domain 边界）升温，可提高精修效率
   - **初步方法**：结合 AlphaFold pLDDT 分数，对低置信区域施加升温，高置信区域保持未缩放
   - **验证方式**：精修后结构与实验结构 RMSD 对比
   - **创新状态**：unverified

4. **名称**：REST2-AMP/MM 与 metadynamics 的混合增强采样
   - **来源局限/观察**：REST2 无偏探索但效率有限，metadynamics 需反应坐标但定向高效
   - **核心假设**：两者结合可兼顾无偏探索和定向加速
   - **初步方法**：在 REST2 副本上叠加 metadynamics 偏置势
   - **验证方式**：与纯 REST2 和纯 metadynamics 对比折叠时间
   - **创新状态**：unverified

5. **名称**：REST2-AMP/MM 在配体结合自由能计算中的应用
   - **来源局限/观察**：REST2 在经典力场中已用于 alchemical 自由能计算
   - **核心假设**：ML/MM 精度下的 REST2 可提高结合自由能计算准确性
   - **初步方法**：对配体-蛋白复合物进行 REST2-AMP/MM alchemical 计算
   - **验证方式**：与实验结合亲和力数据对比
   - **创新状态**：unverified

6. **名称**：REST2-AMP/MM 折叠路径的 Markov 状态模型分析
   - **来源局限/观察**：作者未分析折叠路径，仅报告最终折叠成功
   - **核心假设**：REST2 副本交换数据可用于构建折叠路径的 Markov 状态模型
   - **初步方法**：将多副本轨迹投影到慢变量，构建 MSM，分析折叠路径和过渡态
   - **验证方式**：与实验折叠速率和 Φ 值对比
   - **创新状态**：unverified