## 01 基本信息
- 标题：GroScore: Automated Scoring of Protein-Protein Interactions Using Bidirectional Steered Molecular Dynamics
- 作者与单位：Perthold, Jan Walther; Petrov, Drazen; Oostenbrink, Chris（单位未在提供材料中列出）
- 期刊/预印本平台：Journal of Chemical Information and Modeling
- 年份：2026-10-26（按提供日期）
- 论文类型：方法/软件工具论文（open-source toolkit + benchmark validation）
- 领域：计算生物物理 / 分子模拟 / 蛋白质–蛋白质相互作用打分
- 关键词：protein–protein interactions; steered molecular dynamics; bidirectional pulling; Crooks Gaussian Intersection; interface cutout; force fields; molecular glues; PROTACs（部分为 [Analysis] 归纳）
- DOI/arXiv 号：10.1021/acs.jcim.6c01771
- 代码：https://github.com/jwperthold/GroScore （MIT License）
- 数据：HADDOCK protein–protein affinity benchmark（46 complexes）；PPB-Affinity aggregate（2529 complexes）；CAPRI Score_set；19 ternary complexes（14 MGs + 5 PROTACs）
- 阅读日期：未提供
- 在「蛋白质结构相关计算研究 × AI 方法/物理模拟」方向中的位置：属于物理模拟一侧的 post hoc 打分/重排序方法，定位为 AI co-folding/docking 生成候选结构后的物理复核环节（hybrid workflow 中的 physics-based re-evaluation）。

## 02 一句话总结
针对 AI co-folding/docking 生成的蛋白复合物候选结构难以可靠打分的问题，GroScore 用双向（unbinding + rebinding）steered MD 在显式溶剂中计算 work 分布，并通过简单平均或 Crooks Gaussian Intersection 估计结合分数，在 HADDOCK benchmark 上得到 Pearson r = 0.51–0.66，在更大更异质的 PPB-Affinity 上仅得到弱相关（r ≈ 0.16–0.40），作者明确将其定位为 scoring scheme 而非严格结合自由能方法。

## 03 研究问题
- 具体问题：如何对蛋白–蛋白复合物结构（实验或计算预测）进行自动化、可迁移、基于物理的打分，以区分近天然 pose 与非天然 pose，并量化结合强度。
- 为什么重要：AI co-folding（AlphaFold-Multimer、AlphaFold 3、RoseTTAFold all-atom、Boltz 等）可快速生成大量候选复合物，但其内部置信度指标（ipTM、pDockQ）存在假阳性、抗体–抗原/瞬态界面可靠性下降、数据泄漏导致相关性虚高等问题；采样不再是瓶颈后，可靠打分成为持续开放问题（CAPRI scoring、CASP15-CAPRI joint assessment）。
- 现有方法为何不足：AI/ML 打分快但继承训练集偏倚、泛化差；经验/统计势参数化于窄 benchmark、对输入 pose 几何敏感；端点自由能方法（MM/PBSA）只采样输入附近窄构象区并依赖连续溶剂近似；显式溶剂 MD 原则上可迁移但计算昂贵、需大量手工设置。
- 精确研究问题（[Analysis] 归纳）：Can bidirectional steered MD with interface cutout produce protein–protein scores that correlate with experimental binding affinities across diverse system classes at tractable computational cost?

## 04 背景与发展脉络
（该脉络主要依据本文 Introduction 叙述；标注为「仅本文框架」，未做外部核验）
- 阶段 1：AI co-folding 革命——AlphaFold-Multimer、AlphaFold 3、RoseTTAFold all-atom、Boltz 等从序列直接生成复合物模型，并以 ipTM/pDockQ 作为 de facto scoring function。优点：快、广覆盖；局限：假阳性、抗体–抗原/瞬态界面可靠性下降、可能记忆训练数据、benchmark 相关性受数据泄漏影响。
- 阶段 2：专用 post hoc scoring functions——经验/力场组合（HADDOCK、pyDock）、知识统计势（SOAP-PP）、整合方法（iScore）、深度学习（DeepRank 家族）、端点自由能（MM/PBSA）。优点：各有针对性；局限：参数化窄、几何敏感、连续溶剂近似。
- 阶段 3：path-sampling MD-based scoring——Hou 等粗粒化 equilibrium umbrella sampling；Kingsley 等原子级 steered MD + PMF；Zacharias 组沿解离坐标 umbrella sampling 与 repulsive-scaling replica-exchange；Wang 等 ensemble metadynamics 沿分子间距离坐标解离并平均自由能面。优点：显式采样解离/结合过程、力场可迁移；局限：计算成本高。
- 本文主张的位置：在阶段 3 脉络中，将此前单向 SMD 版本升级为双向 pulling + interface cutout + 多力场 + 杂原子自动化，定位为 AI 快速生成/打分与物理严格复核之间的 hybrid workflow 组件。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 单向 pulling 的指数平均统计偏倚 | 估计量被稀有低 work 轨迹主导 | 作者解释为 exponential work averaging 的已知统计偏倚 | Introduction 对原版 GroScore 局限 (i) 的陈述 |
| 分数与 buried surface area 强相关 | 几何大小与结合强度混淆 | 作者归因于单向 pulling 协议 | Introduction 局限 (ii)；双向方法「substantially reduces the anticorrelation」 |
| 全溶剂原子级 SMD 计算成本高 + 手工设置多 | 只能处理少量结构，难以常规采用 | 作者归因于全复合物显式溶剂模拟与手工工作流 | Introduction 局限 (iii) |
| AI 置信度指标不可靠 | 非相互作用对假阳性；抗体–抗原、瞬态界面可靠性下降 | 作者归因于训练集偏倚/冗余、共进化信号有限 | Introduction 对 ipTM/pDockQ 的评述 |
| benchmark 相关性可能被数据泄漏抬高 | 蛋白–配体 benchmark 相关性虚高；ΔΔG 模型在序列一致性 cutoff 下相关性下降约 63% | 作者引用近期工作 | Introduction 引用性陈述 |
| 大而异质的 PPB-Affinity 上相关性弱 | 总体 Pearson r = 0.16, Spearman ρ = 0.24 | 作者归因于打分方案近似、力场限制、非平衡采样有限时间尺度、文献亲和数据异质性 | Validation 节；Conclusion |
| 抗体–抗原与 TCR–pMHC 子集信号弱 | SAbDab r = 0.17；ATLAS 仅 9 个复合物、亲和跨度约 2 pKd、CI 跨零 | 作者归因于 CDR（尤其 H3）环缺失/无序、结合构象差异、动态范围窄 | Validation 节 |
| 输入几何 vs 形成自由能 | 报告的是解离输入几何的自由能，而非从单体形成复合物的自由能 | 作者以 brefeldin-A/ARF1/Sec7 为例说明 | Validation 节第二类非显著案例 |

## 06 核心思想
1) 表面方法：用 GROMACS 自动化执行双向（unbinding 5 ns + rebinding 5 ns）steered MD，对界面非氢原子对施加距离限制并逐步拉开/推回，从 work 分布用简单平均或 CGI 估计结合分数；可选 interface cutout 只保留界面 2.0 nm 内残基以降低计算量。
2) 核心洞察：双向 pulling 同时采样解离与结合过程，可克服单向指数平均的统计偏倚并降低分数与 buried surface area 的反相关；界面附近才是打分关键区域，cutout 可在几乎不损失分数的情况下大幅省算力；显式溶剂 MD 原则上跨系统类可迁移，适合作为 AI 生成候选的物理复核。
3) 可能的普适教训 [Analysis]：在非平衡采样打分中，forward/reverse 双向采样 + 分布交点估计（CGI）比单向指数平均更稳健；对昂贵物理模拟，用「只模拟关键区域 + 弹性网络维持结构完整性」可在保持排序能力的同时换取吞吐；物理打分器应被定位为相对排序/复核工具而非绝对 ΔG 预测器。

## 07 方法总览
- 输入：PDB 文件（实验测定或计算预测的蛋白–蛋白复合物结构）。
- 输出：每个复合物的 binding affinity score（pull/push work 的简单平均或 CGI 估计），含 bootstrap CI（N = 50,000 resamples）；score 文件每完成一个 cycle 更新以监控收敛。
- 模块：结构准备与 GROMACS topology 生成；可选 interface cutout（默认 2.0 nm）；溶剂化（0.15 M NaCl，dodecahedron box，最小 protein-wall 距离 1.5 nm）+ 能量最小化；初始平衡生成距离限制；N 个独立 pull/push cycles（默认 5），每 cycle 从新平衡 + 新随机速度开始。
- 训练：不适用（无机器学习训练）。
- 工具：GROMACS（模拟）、SLURM（HPC 调度）、OpenFF Sage 2.2.1 + Open Babel（小分子参数化）、Vienna-PTM（GROMOS 54A8 翻译后修饰）。
- 反馈回路：score 文件随 cycle 更新，可据收敛情况决定是否增加 cycle（如 CGI 推荐 ≥20 cycles）。
- 假设：复合物具有明确、可分离的界面；短 re-equilibration（100 ps）足以让水–蛋白相互作用平衡；界面非氢原子对限制可限制相对旋转并允许短时正确 rebinding。
- 文字流程：输入 PDB → 结构准备/topology →（可选）interface cutout + 弹性网络限制 → 溶剂化 + 最小化 → 平衡生成距离限制 → 重复 N 次 {新平衡 → 5 ns unbinding（0.0002 nm/ps，位移至 1.0 nm）→ 100 ps re-equilibration → 5 ns rebinding} → 汇总 work 分布 → 简单平均或 CGI → 分数 + bootstrap CI。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| Bidirectional pulling | 同时模拟 unbinding 与 rebinding | 克服指数平均偏倚、降低与 buried surface area 的反相关 | 输入：平衡后复合物；输出：forward/reverse work 分布 | Introduction；Implementation「Bidirectional Pulling」 | 实测：CAPRI Score_set 上双向 Top-10 近天然 pose 49 个 vs 单向 40 个（含高质量 13 vs 9，中等 23 vs 21） |
| Interface cutout | 只保留界面 2.0 nm 内残基 | 降低 box 尺寸与计算成本 | 输入：全复合物；输出：截短体系 + 人工断链处 Cα 弹性网络限制（0.4–0.9 nm，250 kJ·mol⁻¹·nm⁻²） | Implementation「Interface Cutout」；Validation | 实测：cutout vs no-cutout 的 per-complex 分数强相关（r = 0.93, 0.96, 0.93, 0.87）；聚合相关性几乎相同；≥95% 轨迹 rebound RMSD 在 5 Å 内 |
| 多力场支持 | AMBER19SB/OPC3（默认）、AMBER19SB/OPC、CHARMM36m/TIP3P、GROMOS 54A8/SPC | 跨力场可迁移性 | 输入：体系；输出：topology + 模拟 | Implementation「Force Field Support」；Validation | 实测：所有力场均得显著正相关（r = 0.51–0.66），性能相似 |
| 杂原子处理 | 自动检测结构金属离子（topology 级谐振限制）、小分子（OpenFF Sage 2.2.1）、非标准氨基酸（capped tripeptide + OpenFF 侧链 + 母残基骨架）、晶体水保留 | 扩大适用范围 | 输入：含杂原子 PDB；输出：参数化 topology | Implementation「Heteroatom Handling」 | 预期：移除后含小分子/修饰残基体系无法处理（未提供消融） |
| 两种打分估计 | 简单平均；CGI（拟合 forward/reverse 高斯并取交点） | 分布等方差时简单平均无偏；不等方差时 CGI 更有效 | 输入：work 分布；输出：ΔG 估计 + bootstrap CI | Implementation「Scoring Methods」；Validation | 实测：TIR1/auxin/IAA7（2P1O）与 CRBN/lenalidomide/CK1α（5FQD）5 cycles 简单平均不显著，30 cycles CGI 显著；CGI CI 有时更宽 |

## 09 关键公式符号
- 简单平均：score = mean of pull and push works across all cycles。符号：pull work（unbinding）、push work（rebinding）。用途：在 forward/reverse work 分布为等方差高斯时无偏。直觉：双向平均抵消单向偏倚。来源：Implementation「Scoring Methods」。
- Crooks Gaussian Intersection (CGI)：对 unbinding 与 rebinding work 分布分别拟合独立高斯，取其交点作为 ΔG。符号：forward 分布、reverse 分布、交点 ΔG。用途：分布不等方差时统计效率更高，推荐 ≥20 cycles。直觉：利用 forward/reverse 分布的不对称性。来源：Implementation「Scoring Methods」。
- Bootstrap CI：N = 50,000 resamples。用途：给出分数不确定性。来源：Implementation「Scoring Methods」。
- 注：文中未给出显式数学表达式（如 Jarzynski 等式或 Crooks 关系的完整公式），仅以文字描述；具体公式形式未提供。

## 10 实验设计与证据链
数据集/规模/指标/基线/预算/骨干/评测协议：
- HADDOCK protein–protein affinity benchmark：46 个复合物，实验亲和力跨度约 8 pKd 单位；三力场 × cutout/no-cutout；5 cycles；指标 Pearson r。
- PPB-Affinity aggregate：2529 个复合物，2431 成功（96%）；仅 cutout + AMBER19SB + OpenFF Sage/OPC3；5 cycles；指标 Pearson r、Spearman ρ；按 5 个来源数据集分层。
- CAPRI Score_set：单 cycle；比较双向 vs 单向 Top-10 近天然 pose 数；硬件 NVIDIA RTX 5080 GPU，单 cycle 吞吐 56 poses/day（T32 目标）与 53 poses/day。
- 小分子/三元复合物：19 个三元复合物（14 MGs + 5 PROTACs），有/无 inducer；5 cycles 简单平均与 30 cycles CGI。
- 基线：原版单向 GroScore（CAPRI 对比）；无其他外部打分器直接对比（未提供）。
- oracle 输入：使用实验测定或计算预测的输入结构；未使用 oracle 亲和力作为输入。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| HADDOCK benchmark 三力场 | 双向 SMD 分数与实验亲和力相关 | 三力场 × cutout/no-cutout，5 cycles | Pearson r = 0.51–0.66，均显著 | 跨力场可迁移 | 不支持绝对 ΔG 定量 | Validation；SI Figures S1–S4 |
| cutout vs no-cutout | cutout 不损失精度 | 同力场对比 | per-complex 分数 r = 0.93/0.96/0.93/0.87；聚合相关性几乎相同；≥95% 轨迹 RMSD < 5 Å | cutout 可行省算力 | 不支持 cutout 在所有体系均无损 | Validation；SI Figure S9 |
| PPB-Affinity 总体 | 大规模异质数据上仍相关 | cutout + AMBER19SB/OPC3，5 cycles | Pearson r = 0.16，Spearman ρ = 0.24 | 弱但显著相关 | 不支持强相关或绝对预测 | Validation；Table |
| PPB-Affinity 分层 | 性能随数据来源变化 | 5 个来源子集 | Affinity Benchmark v5.5 r = 0.40；PDBbind v2020 PPI r = 0.20；SKEMPI v2.0 WT r = 0.20；SAbDab r = 0.17；ATLAS 9 个复合物、跨度约 2 pKd、CI 跨零 | 数据质量与动态范围影响性能 | 不支持 ATLAS 负相关为真实信号 | Validation；Table；SI Figure S10 |
| CAPRI Score_set | 双向优于单向 | 单 cycle，双向 vs 单向 | Top-10 近天然 49（13 high + 23 medium）vs 40（9 high + 21 medium） | 双向改善近天然 pose 排序 | 不支持在所有目标均改善 | Validation；SI Figure S11、Table S1 |
| 三元复合物 | 小分子实现可用 | 5 cycles 简单平均 vs 30 cycles CGI | CGI 下 19 中 13 显著负移（稳定化）；6 个非显著分三类 | 小分子/glue 可处理 | 不支持 PROTAC linker 桥接体系无歧义 | Validation；Figure |
| CGI vs 简单平均 | CGI 更有效 | 2P1O、5FQD | 5 cycles 简单平均不显著，30 cycles CGI 显著 | CGI 推荐 ≥20 cycles | 不支持 CGI CI 总是更窄 | Validation |

## 11 结论正确解读
- 任务范围：post hoc scoring/重排序，不是绝对结合自由能预测；作者明确「by design a scoring scheme rather than a rigorous binding free-energy method」，省略了绝对标准态 ΔG 所需的 restraint corrections。
- oracle/真值输入：输入为实验或预测结构，非 oracle 亲和力；但打分对象是输入几何的解离自由能，而非从单体形成复合物的自由能（brefeldin-A/ARF1/Sec7 案例）。
- 端到端状态：从 PDB 到分数的自动化流程已实现；但依赖 GROMACS + SLURM + HPC/GPU 资源。
- 算力成本：单 cycle 在 RTX 5080 上 53–56 poses/day；CGI 推荐 ≥20 cycles，成本相应上升。
- 历史数据依赖：benchmark 亲和力来自文献，异质；PPB-Affinity 子集性能差异大。
- 模型依赖：结果依赖力场（三力场性能相似但非等价）、水模型、cutout 设置。
- 最难情形：intertwined interfaces（需更大分离与不同反应坐标）、抗体–抗原（CDR 环缺失/无序、动态范围窄）、TCR–pMHC（动态范围极窄）、linker-bridging PROTACs（分配歧义）。
- 群体/领域边界：结论基于 HADDOCK、PPB-Affinity、CAPRI Score_set、19 个三元复合物；未覆盖膜蛋白、多聚体、大幅构象变化体系。
- 不确定性：CGI CI 有时比简单平均更宽；ATLAS 子集 CI 跨零。
- 有边界的复述：GroScore 在受控 benchmark 上给出与实验亲和力显著但绝对偏弱的相关，能改善近天然 pose 排序并处理小分子/修饰残基，但不应被解读为通用绝对亲和力预测器。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 是 scoring scheme 而非严格结合自由能方法 | 采样仅限直接相互作用贡献，省略绝对标准态 ΔG 所需 restraint corrections | 以可处理性与广适用性换取定量亲和力 | Conclusion |
| PPB-Affinity 子集相关性绝对偏弱 | Pearson r ≈ 0.2–0.4 | 归因于打分近似、力场限制、非平衡采样有限时间尺度、文献亲和数据异质性；motivate 改进采样与结合诱导构象变化处理 | Conclusion |
| 分离策略适用于界面明确可分离的复合物 | intertwined interfaces 需更大分离与不同反应坐标 | 类比 center-of-mass pulling | Implementation「Bidirectional Pulling」 |
| 报告解离输入几何的自由能 | 非从单体形成复合物的自由能 | 以 brefeldin-A/ARF1/Sec7 为例说明 | Validation |
| PROTAC linker 桥接体系分配歧义 | 方差更大 | 未明确 | Validation |
| CGI CI 有时更宽 | 依赖 forward/reverse 分布方差，收敛慢 | 未明确 | Validation |

作者提及的相关约束（非正式局限）：AI 仅用于语言编辑与文本扩写，未生成科学结果（Acknowledgements）。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| PPB-Affinity 总体 r = 0.16 的弱相关可能部分来自数据集异质性而非方法本身 | 分层后 Affinity Benchmark v5.5 达 r = 0.40，提示数据质量主导 | 影响方法适用边界的判断 | 在统一 curated 数据集上重测，或对异质数据做分层建模 | Validation；Table |
| 5 cycles 简单平均在 HADDOCK 已「converged」，但 CGI 需 ≥20 cycles 才能分辨小效应 | 收敛判据依赖指标与体系；小效应可能被 5 cycles 掩盖 | 影响常规使用成本与灵敏度权衡 | 系统扫描 cycles 数 vs 效应量检测力 | Validation；SI Figures S5–S8 |
| cutout 的 per-complex 分数相关高，但仅验证了 RMSD < 5 Å 的结构完整性 | 5 Å 阈值较宽松，局部界面重排可能未被捕捉 | 影响 cutout 在柔性界面体系的可靠性 | 对界面残基做更细粒度 RMSD/接触分析 | Validation；SI Figure S9 |
| 三元复合物中 inducer 被分配给一个 partner，PROTAC linker 桥接时歧义 | 分配规则可能系统性影响 PROTAC 结果 | 影响小分子打分推广性 | 对同一 PROTAC 尝试不同分配并比较 | Validation |
| 未与其他 post hoc scoring functions（如 MM/PBSA、DeepRank、iScore）直接对比 | 无法判断相对优势 | 影响方法选择 | 在同一 benchmark 上做 head-to-head | 未提供 |
| CAPRI 对比仅单 cycle，且仅报告 Top-10 计数 | 单 cycle 可能未发挥双向全部优势；Top-10 计数对目标数敏感 | 影响双向优势的稳健性 | 多 cycle + 多指标（如 I-RMSD 分布） | Validation；SI Table S1 |
| 力场性能相似但未报告统计检验 | 「similar」缺乏显著性支撑 | 影响力场选择建议 | 对力场间相关性差异做配对检验 | Validation |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念：双向非平衡采样（unbinding + rebinding）可缓解单向指数平均偏倚；CGI 估计利用 forward/reverse 分布不对称性，在 ≥20 cycles 时更有效。
- 可迁移方法：interface cutout + 人工断链处 Cα 弹性网络限制（0.4–0.9 nm，250 kJ·mol⁻¹·nm⁻²）作为降低显式溶剂模拟成本的通用策略，可迁移到蛋白–配体、蛋白–核酸打分。
- 可迁移实验设计：用 per-complex 分数相关（而非仅聚合相关）验证近似方法的保真度；用 bootstrap CI 报告分数不确定性；按数据来源分层报告性能。
- 可迁移工程实践：score 文件随 cycle 更新以监控收敛；SLURM + GROMACS 自动化；OpenFF + capped tripeptide 混合参数化处理非标准残基。
- 面向本课题的迁移：在「AI 生成候选结构 → 物理复核」hybrid workflow 中，GroScore 可作为重排序器；其 cutout 思路可用于 AlphaFold 生成复合物的快速物理打分；其分层 benchmark 分析提醒在评估 AI 结构预测/设计方法时需注意数据来源异质性与动态范围。

## 15 与已有知识连接
- 相似：Hou 等 coarse-grained equilibrium umbrella sampling；Kingsley 等原子级 steered MD + PMF；Zacharias 组 umbrella sampling 与 repulsive-scaling replica-exchange；Wang 等 ensemble metadynamics（均见 Introduction）。
- 组合：与 AI co-folding（AlphaFold-Multimer、AlphaFold 3、RoseTTAFold all-atom、Boltz）形成 hybrid workflow；与 ipTM/pDockQ 互补。
- 冲突：作者指出 AI 置信度指标在抗体–抗原、瞬态界面可靠性下降，且 benchmark 相关性可能受数据泄漏抬高；与「AI 打分已足够」的观点存在张力。
- 可迁移领域：小分子相对自由能计算中「只模拟关键区域」的思路（Introduction 引用）；蛋白突变 ΔΔG 计算。
- 注：以上连接均基于本文 Introduction 的引用性陈述，未做外部核验。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：GroScore-CGI 自适应 cycle 调度
   - 来源局限/观察：CGI 推荐 ≥20 cycles，但 5 cycles 在 HADDOCK 已收敛；固定 cycle 数可能浪费或不足。
   - 核心假设：基于 bootstrap CI 宽度或 forward/reverse 分布方差比的自适应停止准则，可在保持 CGI 灵敏度的同时降低平均算力。
   - 相对本文的增量：将固定 cycle 数改为自适应。
   - 初步方法：在 PPB-Affinity 子集上扫描 cycle 数，拟合 CI 宽度 vs 效应检测力曲线。
   - 验证方式：与固定 5/30 cycles 比较算力–灵敏度权衡。
   - 可能的失败模式：CI 宽度与效应检测力关系不稳定。
   - 创新状态：unverified。
2. 名称：cutout 阈值与界面柔性联合评估
   - 来源局限/观察：cutout 仅用 RMSD < 5 Å 验证结构完整性。
   - 核心假设：对柔性界面体系，2.0 nm cutout 可能截断关键变构/界面重排区域。
   - 相对本文的增量：系统扫描 cutout 阈值 × 界面柔性指标。
   - 初步方法：在 HADDOCK + PPB-Affinity 上比较 1.5/2.0/2.5/3.0 nm。
   - 验证方式：per-complex 分数相关 + 界面残基接触分析。
   - 可能的失败模式：阈值效应被体系异质性掩盖。
   - 创新状态：unverified。
3. 名称：GroScore 与 AI 打分器的混合重排序
   - 来源局限/观察：AI 置信度指标有假阳性；GroScore 计算贵但物理可迁移。
   - 核心假设：先用 ipTM/pDockQ 粗筛，再用 GroScore 单 cycle 重排序 Top-K，可在有限算力下优于任一单独方法。
   - 相对本文的增量：明确 hybrid 协议与算力分配。
   - 初步方法：在 CAPRI Score_set 上比较纯 AI、纯 GroScore、混合。
   - 验证方式：Top-10 近天然 pose 数 + 算力。
   - 可能的失败模式：AI 粗筛漏掉近天然 pose。
   - 创新状态：partially checked（本文已提出 hybrid workflow 概念但未做该实验）。
4. 名称：PROTAC linker 分配歧义的多假设打分
   - 来源局限/观察：linker-bridging PROTACs 分配歧义导致大方差。
   - 核心假设：对同一 PROTAC 枚举多种 inducer 分配并聚合分数，可降低方差并提高显著性。
   - 相对本文的增量：从单一分配改为多假设聚合。
   - 初步方法：在 5 个 PROTAC 上枚举分配并比较。
   - 验证方式：与实验亲和力/降解活性比较。
   - 可能的失败模式：分配枚举成本高且仍无法覆盖真实结合模式。
   - 创新状态：unverified。
5. 名称：结合诱导构象变化的双向 SMD 扩展
   - 来源局限/观察：作者指出 GroScore 报告解离输入几何的自由能，非形成自由能；结合诱导构象变化未处理。
   - 核心假设：在 rebinding 阶段允许界面侧链/环区松弛（如降低限制强度或分段释放），可更好捕捉结合诱导构象变化。
   - 相对本文的增量：从刚性限制到部分柔性。
   - 初步方法：在抗体–抗原子集上比较不同限制强度。
   - 验证方式：与实验亲和力及 unbound–bound 构象变化比较。
   - 可能的失败模式：松弛导致 rebinding 失败或分数噪声增大。
   - 创新状态：unverified。