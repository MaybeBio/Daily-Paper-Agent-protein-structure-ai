## 01 基本信息
- **标题**: Structure-based discovery of inhibitors of Mac1 domain of nonstructural protein-3 of SARS-CoV-2 by machine learning-augmented screening of chemical space
- **作者与单位**: Ban, Fuqiang; Ravichandran, Rahul; Correy, Galen J; Herasymenko, Oleksandra; Silva, Madhushika; Ackloo, Suzanne; Bolotokova, Olga; Chau, Irene; Gibson, Elisa; Harding, Rachel; Hutchinson, Ashley; Loppnau, Peter; Fraser, James S; Schapira, Matthieu; Cherkasov, Artem; Gentile, Francesco（单位未提供，部分作者隶属加拿大渥太华大学及美国加州大学旧金山分校，据基金信息推断）
- **期刊/预印本平台**: Scientific Reports
- **年份**: 2026（在线日期 2026-11-12）
- **论文类型**: 研究论文（CACHE3 挑战赛参赛工作）
- **领域**: 计算药物发现 / 虚拟筛选 / 机器学习加速筛选 / 蛋白质-配体相互作用
- **关键词**: SARS-CoV-2, NSP3, Mac1, 虚拟筛选, 深度学习, Deep Docking, 结构生物学
- **DOI/arXiv 号**: 10.1038/s41598-026-65034-1
- **代码**: 未提供
- **数据**: 晶体结构 PDB 7HPW（CACHE3-HI_1706_56-Mac1 复合物）；Enamine REAL Diversity Subset 及 REAL Space 数据（商业数据库）
- **阅读日期**: 2026-05-13
- **在该方向中的位置**: 本文属于「AI 加速虚拟筛选 × 结构生物学验证」交叉方向，展示了将机器学习加速筛选（Deep Docking）与 X 射线晶体学验证相结合，在超大规模化学空间中高效发现新骨架抑制剂的工作流程。对蛋白质结构相关计算研究而言，其可迁移点在于：以蛋白晶体结构为靶标、以 docking score 为代理标签的主动学习筛选策略，以及结构验证闭环的设计。

## 02 一句话总结
本文针对 SARS-CoV-2 NSP3 Mac1 结构域，采用 Deep Docking 主动学习策略对 Enamine REAL Diversity Subset（约 2300 万分子）进行加速虚拟筛选，结合共识打分与人工视觉检查，发现并验证了一个新型中性抑制剂骨架 CACHE3-HI_1706_56（SPR KD = 20 µM），并通过 REAL Space 中 440 亿分子的类似物搜索获得 KD 达 12 µM 的衍生物，X 射线晶体学确认了其结合模式。

## 03 研究问题
- **具体问题**: 如何在超大规模化学空间（数千万至数百亿分子）中高效发现 SARS-CoV-2 NSP3 Mac1 的新型中性（非带电）抑制剂骨架？
- **为什么重要**: Mac1 是 SARS-CoV-2 免疫逃逸的关键毒力因子，其活性位点失活可使病毒在小鼠模型中减毒。中性抑制剂有望克服此前阴离子抑制剂细胞通透性差的瓶颈，为抗病毒药物开发提供新起点。
- **现有方法为何不足**: 传统 docking 对超大规模库的计算成本过高；基于片段的筛选需要大量晶体学工作；生成式方法在 Mac1 这类极性、浅口袋上的成功率有限。CACHE3 挑战赛各参与者的总体命中率仅 1.8%，说明该靶点的计算可处理性（computational tractability）较低。
- **精确研究问题**: Can a machine learning-augmented virtual screening workflow (Deep Docking) applied to a diverse subset of an ultra-large chemical library identify novel, neutral, crystallographically-validated inhibitors of SARS-CoV-2 NSP3 Mac1?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」——基于 CACHE 挑战赛系列及文中引用的 Mac1 抑制剂研究史）*

| 阶段 | 代表性方法 | 优点 | 局限 |
|---|---|---|---|
| 早期 Mac1 抑制剂发现 | 基于已知 ADP-ribose 底物的类似物设计 | 有明确起点 | 带电基团导致通透性差 |
| 片段筛选 + 结构引导设计（Gahbauer et al.） | 片段生长/连接，晶体学辅助 | 获得 Z8539_0072（IC50 0.4 µM）和 LRH-0003（IC50 1.7 µM） | 需要大量晶体结构；中性化改造后活性下降 |
| CACHE3 挑战赛（本文） | Deep Docking 主动学习 + 共识打分 + 视觉检查 | 仅 docking 1.5% 分子即保留 90% 高分分子；发现新骨架 | 命中率仍低（1.2%）；需要人工干预 |
| 超大规模类似物搜索 | REAL Space 440 亿分子 + Glide SP | 快速获得活性类似物（KD 12 µM） | 依赖初始 hit 质量；未探索中性氢键受体修饰 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 超大规模库 docking 计算成本过高 | 无法对全部 2300 万分子逐一 docking | 计算资源有限；Mac1 位点极性、柔性大 | Methods "Deep Docking" 节；Results 图 2b |
| Mac1 位点计算可处理性低 | 全体 CACHE3 参与者命中率仅 1.8% | 位点极性、浅、柔性（Phe132 构象变化） | Results "Discovery and characterization" 节；引用文献 10 |
| 带电抑制剂通透性差 | Z8539 系列细胞通透性仅 11 nm/s | 羧酸/磷酸基团 | Introduction 节；引用文献 7 |
| 中性化改造导致活性下降 | SRH-0015 仅 IC50 132 µM | 中性基团与 oxyanion hole 作用弱 | Results "Chemical series expansion" 节；引用文献 7 |
| 虚拟筛选命中率低 | 83 个测试化合物仅 1 个确认 hit（1.2%） | 打分函数误差、蛋白柔性、共识策略保守 | Results "Discovery and characterization" 节 |

## 06 核心思想
1. **表面方法**: 采用 Deep Docking 主动学习协议，以 Glide SP 为 docking 引擎，对 Enamine REAL Diversity Subset（2300 万分子）进行迭代筛选。每轮 docking 少量分子（5 万），训练一个二分类器（基于 Morgan 指纹）预测剩余库中分子的 docking score 是否优于阈值，逐步修剪低分分子。最终保留约 650 万分子，再以 Glide SP 全量 docking，经 ICM 重打分、RMSD 共识过滤、视觉检查，选出 83 个化合物进行实验测试。

2. **核心洞察**: 
   - **多样性子集 + 主动学习**：与其直接处理全库，不如先在一个代表性、结构多样的子集上训练，利用主动学习迭代修剪，以极小计算量保留绝大多数高分分子。
   - **共识策略优于单一打分**：Glide 与 ICM 两种 docking 程序 + RMSD 一致性过滤 + 人工视觉检查，可有效降低假阳性。
   - **结构验证闭环**：X 射线晶体学不仅确认结合，还揭示了 Phe132 的构象变化（closed → everted），为后续优化提供结构基础。

3. **可能的普适教训** [Analysis]: 
   - 对「难」靶点（极性、浅、柔性口袋），单一计算方法的命中率天然有限，**多方法共识 + 人工专家干预**仍是必要的质量控制环节。
   - 主动学习在**分子多样性高**的库上修剪效率会下降（本文中 reduction power 仅 3.5 倍，远低于全库场景），说明该方法更适合结构冗余的全库而非多样性子集。
   - 结构生物学反馈（晶体结构）不仅用于验证，更能揭示 docking 模型未预测到的构象变化，是改进打分模型的重要数据来源。

## 07 方法总览
- **输入**: 
  - 靶标结构：PDB 5SRY（LRH-0003-Mac1 复合物，1.05 Å）
  - 配体库：Enamine REAL Diversity Subset（约 8000 万分子，过滤后 2310 万）
  - 过滤条件：CACHE3 hit-like 标准（≤6 可旋转键、MW ≤400、fsp3 >0.25、logP 1–3.5、≤4 立体异构体）
- **输出**: 
  - 83 个候选化合物（实验测试）
  - 1 个确认 hit：CACHE3-HI_1706_56（SPR KD = 20 µM）
  - 17 个类似物（第二轮），其中 12 个经 SPR 确认，最佳 KD = 12 µM
  - 1 个晶体结构（PDB 7HPW）
- **模块**:
  1. 蛋白结构准备（Schrödinger Protein Prep Wizard）
  2. 配体库准备（RDKit 过滤、OpenEye 立体化学/优势电离态）
  3. Deep Docking 主动学习（4 轮迭代，每轮 5 万分子训练/验证/测试）
  4. Glide SP 全量 docking（保留 26,057 个 score ≤ −8.15 kcal/mol 分子）
  5. ICM 重 docking + RMSD 共识过滤（≤2 Å）
  6. 共识打分 + 视觉检查（29 + 77 = 93 个候选，去重后 83 个）
  7. 实验验证：HTRF 竞争性结合实验 → SPR 确认 → X 射线晶体学
  8. 类似物搜索：REAL Space（440 亿分子）相似性搜索 → Glide SP docking → 视觉检查 → 75 个候选 → 19 个合成 → 17 个成功 → 12 个 SPR 确认
- **工具**: Schrödinger Maestro (Glide SP)、ICM-Pro、RDKit、OpenEye（flipper, omega, tautomers）、BiosolveIT InfiniSee、PanDDA、CCP4、Refmac5、Phenix
- **假设**: 
  - 晶体结构（5SRY）的 apo 构象（Phe132 closed）适合 docking
  - Glide SP score 可作为结合亲和力的代理指标
  - 中性分子可在不牺牲活性的前提下获得更好通透性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| Deep Docking 主动学习 | 迭代修剪低分分子，减少 docking 计算量 | 2300 万分子无法全量 docking | 输入：Morgan 指纹 + 每轮 5 万 docking 结果；输出：保留 650 万分子 | Results 图 2b；Supplementary Fig. 1（库大小逐轮下降） | 需全量 docking，计算成本增加约 30 倍 |
| Glide SP docking | 对保留分子进行全量打分 | 主动学习仅提供分类，需精确打分排序 | 输入：650 万分子 + 5SRY 结构；输出：score ≤ −8.15 的 26,057 分子 | Methods "Docking" 节 | 无替代打分，无法排序 |
| ICM 重 docking + RMSD 共识 | 交叉验证 docking 姿势 | 单一 docking 程序可能系统偏差 | 输入：26,057 分子；输出：1,553 个 RMSD ≤2 Å 分子 | Methods "Hit selection" 节；引用文献 24 | 假阳性率预计上升 |
| 共识打分 + 视觉检查 | 最终人工筛选 | 自动打分无法捕捉化学合理性 | 输入：1,553 分子；输出：93 个候选（83 个测试） | Results "Discovery" 节 | 命中率可能进一步下降 |
| HTRF 竞争性实验 | 初筛配体是否竞争 ADP-ribose 结合 | 快速、低成本评估 | 输入：83 化合物；输出：11 个抑制率 >50% @100 µM | Results 图 3a | 无法区分竞争/别构 |
| SPR 结合实验 | 确认直接结合及亲和力 | 正交验证 HTRF 结果 | 输入：11 个初筛阳性；输出：1 个 KD = 20 µM | Results 图 3b | 无法确认功能活性 |
| X 射线晶体学 | 确定原子级结合模式 | 验证 docking 预测、揭示构象变化 | 输入：hit 化合物 + Mac1 晶体；输出：PDB 7HPW（1.02 Å） | Results 图 3d；引用文献 10 | 无法获得结合模式 |
| REAL Space 类似物搜索 | 扩展 hit 为系列 | 确认化学系列、优化亲和力 | 输入：hit 结构 + 440 亿分子库；输出：75 候选 → 17 合成 → 12 确认 | Results 表 1；图 4 | 系列无法确认 |

## 09 关键公式符号
**不适用** — 本文为实验性虚拟筛选工作，未提出新的数学公式或统计模型。核心方法（Deep Docking）的数学细节在引用文献 11 中，本文仅使用其实现。

## 10 实验设计与证据链
- **数据集/群体**: 
  - 虚拟库：Enamine REAL Diversity Subset（初始约 8000 万，过滤后 23,139,109 分子）
  - 测试集：83 个化合物（第一轮）+ 17 个类似物（第二轮）
  - 靶标蛋白：SARS-CoV-2 NSP3 Mac1（残基 205–380 用于 HTRF；206–374 用于 SPR/晶体学）
- **规模**: 83 个化合物 HTRF 初筛 → 11 个阳性 → 8 个剂量响应 → 1 个 SPR 确认 → 1 个晶体结构
- **指标**: 
  - 虚拟筛选：docking score（Glide SP）、RMSD 一致性
  - 实验：HTRF 抑制率（% displacement @100 µM）、SPR KD（µM）、IC50（µM）
- **基线/对照**: 
  - HTRF 阳性对照：ADP-ribose 肽（竞争剂）
  - 阴性对照：DMSO（4%）
  - 反筛靶标：人 PARP14 Macro2 结构域（选择性对照）
- **评测协议**: CACHE3 挑战赛独立委员会评估（结合活性、药物相似性、系列确认）
- **骨干/仪器**: Biacore 8K（SPR）、Synergy H1（HTRF）、ALS beamline 8.3.1（X 射线）
- **oracle 输入**: 晶体结构 5SRY（docking 靶标）；ADP-ribose 肽（HTRF 竞争剂）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| Deep Docking 筛选 | 主动学习可高效保留高分分子 | 4 轮迭代，每轮 5 万训练 | 库从 2310 万减至 650 万，保留 90% 的 top 0.1% 分子 | 主动学习有效降低计算量 | 未与全量 docking 直接对比 | Results 图 2b；Supplementary Fig. 1 |
| HTRF 初筛（83 化合物） | 虚拟筛选可富集 Mac1 结合剂 | 100 µM 单浓度 | 11/83 抑制 >50% | 筛选流程有富集能力 | 未报告 Z' 因子或阳性对照的 IC50 | Results "Discovery" 节 |
| HTRF 剂量响应（8 化合物） | 命中具有剂量依赖性 | 3 浓度（10/30/100 µM） | 8/11 显示剂量响应 | 初步确认活性 | 未报告完整 IC50 曲线 | Results "Discovery" 节 |
| SPR 验证（hit） | 直接结合 Mac1 | 多循环动力学，1:1 模型 | KD = 20 µM | 确认直接结合 | 未报告 k_on/k_off | Results 图 3b |
| SPR 反筛（PARP14） | 选择性 | 同条件 | 无结合 | 对 Mac1 有选择性 | 仅测试 1 个旁靶 | Results "Discovery" 节 |
| X 射线晶体学 | 结合模式与 docking 预测一致 | 1.02 Å 分辨率 | 预测姿势与晶体结构一致；Phe132 构象变化 | 验证计算预测；揭示诱导契合 | 配体占据率低（26%） | Results 图 3d；引用文献 10 |
| 类似物筛选（17 化合物） | 化学系列可扩展 | REAL Space 相似性搜索 + docking | 12/17 SPR 确认；最佳 KD = 12 µM | 系列确认；活性可优化 | 未报告细胞活性或体内数据 | Results 表 1；图 4 |

## 11 结论正确解读
- **任务范围**: 本文仅针对 SARS-CoV-2 NSP3 Mac1 一个靶点、一个特定化学库（Enamine REAL）子集。结论不适用于其他靶点或库。
- **oracle/真值输入**: 虚拟筛选以 5SRY 晶体结构为靶标，该结构代表 Phe132 closed 构象；实验验证使用 HTRF 竞争实验和 SPR，均以 ADP-ribose 结合为读出。
- **端到端状态**: 从虚拟筛选到晶体结构确认的完整闭环已完成，但**未进行**细胞水平抗病毒实验、动物实验、ADME/T 性质评估。作者明确声明这些是下一步工作。
- **算力成本**: 未报告具体 GPU 时数或计算资源。Deep Docking 仅 docking 了 1.5% 的库（35 万分子），但后续全量 docking 650 万分子的成本未量化。
- **历史数据依赖**: 依赖 Enamine REAL 库的分子多样性；依赖 5SRY 结构（LRH-0003 结合态）作为 docking 靶标。
- **模型依赖**: 依赖 Glide SP 和 ICM 打分函数；依赖 Morgan 指纹作为分子表示。
- **最难情形**: Mac1 位点本身计算可处理性低（CACHE3 全体命中率 1.8%），本文命中率 1.2% 略低于平均，但确认了新型骨架。
- **群体/领域边界**: 结论仅适用于 Mac1 抑制剂发现；「中性抑制剂」策略的普适性未验证。
- **不确定性**: 配体占据率仅 26%，晶体结构中的结合姿势可能不代表溶液中的主要结合模式；SPR KD 值未与功能实验关联。
- **有边界的复述**: 在 CACHE3 挑战赛框架下，本文的 Deep Docking + 共识筛选流程从 2300 万分子中识别出 1 个经晶体学确认的新型中性 Mac1 抑制剂骨架（KD = 20 µM），并通过 440 亿分子类似物搜索获得 KD = 12 µM 的衍生物。该流程的有效性限于该靶点、该库、该打分函数组合，且未评估细胞活性。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 未进行细胞实验 | 未评估化合物的细胞通透性、细胞毒性、抗病毒活性 | "evaluation of cellular activity for the newly identified series will be the primary next step for advancing toward lead optimization" | Conclusions 节 |
| 命中率低 | 83 个测试化合物仅 1 个确认 hit（1.2%） | 未明确说明改进方向 | Results "Discovery" 节 |
| 未探索中性氢键受体修饰 | 类似物筛选未包含在 oxyanion hole 中放置中性氢键受体的修饰 | "a modification that could be further explored to enhance target engagement" | Results "Chemical series expansion" 节 |
| Deep Docking 缩减效率有限 | 库仅缩减 3.5 倍（vs 全库场景通常更高） | 归因于多样性子集的结构冗余低 | Results "ML-accelerated virtual screening" 节 |

*（注：作者未明确讨论配体占据率低、打分函数误差、Phe132 构象选择等潜在局限，这些属于 [Analysis] 范畴。）*

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 命中率 1.2% 低于 CACHE3 全体平均（1.8%） | 共识策略可能过度保守，或 5SRY 结构（Phe132 closed）不适合 docking | 若共识策略系统性排除有效分子，则流程需调整 | 对 11 个 HTRF 阳性但未通过共识过滤的分子进行 SPR 测试 | Results "Discovery" 节；引用文献 10 |
| 配体占据率仅 26% | 晶体结构中的结合姿势可能不代表溶液中的主要结合模式；docking 预测的「验证」可能过度乐观 | 若结合姿势不确定，基于该结构的优化可能无效 | 进行 MD 模拟或 2D NMR 验证溶液中的结合模式 | Results 图 3d；引用文献 10 |
| 未报告 HTRF 阳性对照的 IC50 | 无法评估 HTRF 实验窗口和灵敏度 | 若实验窗口小，11 个「阳性」可能包含假阳性 | 报告 ADP-ribose 肽的 IC50 和 Z' 因子 | Methods "HTRF" 节（未提供细节） |
| 类似物筛选仅依赖 docking 评分 + 视觉检查 | 未使用 consensus scoring 或 MD 验证；视觉检查主观性强 | 12/17 的确认率可能高估了该流程的预测能力 | 对未确认的 5 个类似物进行晶体学或竞争实验分析失败原因 | Results 表 1 |
| 未报告计算资源消耗 | 无法评估 Deep Docking 的实际加速比 | 若加速比有限，方法可扩展性存疑 | 报告总 GPU 时数、每轮 docking 时间、与全量 docking 的对比 | Methods "ML-accelerated virtual screening" 节（未提供） |
| 仅使用一个蛋白构象（5SRY） | Mac1 的 Phe132 存在 open/closed 构象平衡；单一构象可能遗漏别构位点或诱导契合 | 若 hit 实际结合的是 open 构象，基于 closed 构象的优化可能失败 | 使用多构象 ensemble docking 或 MD 采样生成构象集合 | Methods "Protein structure preparation" 节 |

## 14 学到什么
**Agent 提炼的知识候选**（面向蛋白质结构相关计算研究 × AI/物理模拟方向）：
1. **主动学习 + 多样性子集策略**：当目标库过大无法全量 docking 时，可先在一个多样性子集上训练分类器，迭代修剪低分分子。但注意：**多样性子集的修剪效率低于结构冗余的全库**（本文仅 3.5 倍缩减），因为分类器难以泛化到多样化学空间。若你的课题涉及构象采样或序列设计，可借鉴此思路：先在小而多样的子集上训练代理模型，再逐步扩展。
2. **多 docking 程序共识 + RMSD 过滤**：单一 docking 程序可能有系统偏差，使用两个独立程序（Glide + ICM）并要求姿势一致性（RMSD ≤ 2 Å），可显著降低假阳性。这提示在结构预测或对接任务中，**多方法一致性**是简单有效的质量控制手段。
3. **结构验证闭环的价值**：晶体结构不仅确认了 hit 的结合，还揭示了 docking 模型未预测到的 Phe132 构象变化（closed → everted）。这说明**计算模型对蛋白柔性的处理不足**是虚拟筛选的重要误差来源。可迁移到 MD 模拟或 ensemble docking 中：在筛选前用 MD 或构象采样生成多个受体构象，而非依赖单一晶体结构。
4. **中性抑制剂策略**：Mac1 的带电抑制剂活性好但通透性差（11 nm/s），中性化改造是药物化学的重要方向。在结构设计中，**在保持关键氢键相互作用的同时去除电荷**，是提高类药性的通用策略。
5. **CACHE 挑战赛的评估框架**：前瞻性盲测（prospective benchmarking）是检验计算方法真实预测能力的金标准。本文的命中率（1.2%）远低于回顾性研究常见报告值，提示**回顾性 docking 验证可能严重高估方法性能**。在设计自己的计算流程时，应考虑前瞻性验证。
6. **hit 扩展的化学空间搜索**：从确认的 hit 出发，在 REAL Space（440 亿分子）中进行相似性搜索 + docking，可快速获得活性系列。这提示在蛋白质-配体相互作用研究中，**从单一 hit 到化学系列的扩展**可通过超大规模库的相似性搜索高效实现。

## 15 与已有知识连接
- **Deep Docking 方法**：本文使用的方法源自 Gentile et al. 2020 (Nature Communications) 的 Deep Docking 协议（引用文献 11, 22）。该方法已在多个靶点上验证，本文将其应用于多样性子集而非全库，是方法的新应用场景。
- **Mac1 抑制剂研究史**：Gahbauer et al. 2023 (引用文献 7) 通过片段筛选获得 Z8539_0072（IC50 0.4 µM）和 LRH-0003（IC50 1.7 µM），本文以 LRH-0003 复合物结构（5SRY）为 docking 靶标，发现的 CACHE3-HI_1706_56 含 pyrrolopyrimidine 骨架，与已知抑制剂系列相关但引入了溴代环己烯基团。
- **CACHE 挑战赛**：CACHE (Critical Assessment of Computational Hit-finding Experiments) 系列是计算药物发现的前瞻性基准测试（引用文献 9, 10）。本文为 CACHE3 的参赛工作，其结果已由独立委员会评估。
- **ADP-核糖基化与免疫逃逸**：Mac1 通过水解 ADP-核糖基化修饰逆转宿主 PARP 介导的抗病毒信号（引用文献 1-5），这一机制与更广泛的病毒免疫逃逸研究相关。
- **可迁移领域**：本文的「多样性子集 + 主动学习 + 多方法共识 + 结构验证」流程，可迁移至蛋白质结构预测中的构象筛选、分子对接中的化合物库筛选、以及蛋白质设计中的序列空间探索。特别是**结构验证闭环**的设计，与 AlphaFold 等预测方法需要实验验证的思路一致。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**: 多构象 ensemble docking 对 Mac1 虚拟筛选命中率的影响
   - **来源局限/观察**: 本文使用单一晶体结构（5SRY，Phe132 closed）进行 docking，但晶体结构显示 hit 诱导 Phe132 转变为 everted 构象。单一构象可能遗漏了结合所需的构象状态。
   - **核心假设**: 使用 MD 模拟或构象采样生成 Mac1 的 ensemble 结构进行 docking，可提高虚拟筛选命中率。
   - **初步方法**: 对 Mac1 进行 1 µs MD 模拟，提取代表性构象（如聚类分析），以 ensemble docking 重新筛选本文的 83 个化合物，比较命中率。
   - **验证方式**: 对 ensemble docking 新发现的候选进行 SPR 或晶体学验证。
   - **创新状态**: unverified

2. **候选名称**: 中性 Mac1 抑制剂的细胞活性评估与优化
   - **来源局限/观察**: 作者明确声明未进行细胞实验，且中性化改造（溴代环己烯替代带电基团）的细胞通透性优势未经验证。
   - **核心假设**: CACHE3-HI_1706_56 系列因中性电荷而具有优于 Z8539 系列的细胞通透性，且能在细胞水平抑制 Mac1 介导的免疫逃逸。
   - **初步方法**: 合成 CACHE3-HI_1706_56 及其类似物，进行 Caco-2 通透性实验、Vero-E6 细胞抗病毒实验、IFN-β 报告基因实验。
   - **验证方式**: 比较中性系列与已知阴离子抑制剂的 EC50 和通透性数据。
   - **创新状态**: unverified

3. **候选名称**: Deep Docking 在多样性子集上的最优采样策略
   - **来源局限/观察**: 本文中 Deep Docking 的缩减效率仅 3.5 倍，远低于全库场景。作者归因于多样性子集的结构冗余低，但未系统探索改进策略。
   - **核心假设**: 通过调整主动学习的采样策略（如基于分子聚类的分层采样、或使用图神经网络替代指纹），可提高多样性子集上的修剪效率。
   - **初步方法**: 在本文的 2300 万分子库上，对比不同采样策略（随机、聚类、贪心多样性）和不同分子表示（Morgan 指纹、GraphMVP、MolBERT）的 Deep Docking 性能。
   - **验证方式**: 以保留 top 0.1% 分子的召回率为指标，在多个靶点上交叉验证。
   - **创新状态**: unverified

4. **候选名称**: Mac1 的别构位点探索与变构抑制剂设计
   - **来源局限/观察**: 本文聚焦于 ADP-ribose 竞争性抑制剂，但 Mac1 的 Phe132 构象变化提示可能存在别构调控机制。
   - **核心假设**: Mac1 存在可药用的别构口袋，变构抑制剂可稳定非活性构象，且不涉及带电基团。
   - **初步方法**: 使用 MD 模拟和口袋检测（如 fpocket、SiteMap）识别 Mac1 的隐式口袋，对候选别构位点进行虚拟筛选。
   - **验证方式**: 对 hit 进行 NMR 或 HDX-MS 验证构象变化，SPR 确认结合。
   - **创新状态**: unverified

5. **候选名称**: 基于结构的 Mac1 抑制剂与 PARP14 选择性的计算预测
   - **来源局限/观察**: 本文仅测试了 Mac1 结合，未评估对 PARP14 Macro2 等旁靶的选择性。
   - **核心假设**: Mac1 与 PARP14 Macro2 的结构差异可用于计算预测选择性，指导设计高选择性抑制剂。
   - **初步方法**: 比较 Mac1 与 PARP14 Macro2 的晶体结构，识别选择性决定残基，使用 FEP 或 MM-GBSA 计算系列化合物的选择性。
   - **验证方式**: 对预测高选择性的化合物进行 SPR 交叉测试。
   - **创新状态**: unverified