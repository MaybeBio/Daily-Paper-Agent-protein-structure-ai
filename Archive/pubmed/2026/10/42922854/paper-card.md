## 01 基本信息
- 标题：The physical foundation beneath protein generative modeling
- 作者与单位：Lu, Tianyu; Huang, Po-Ssu（单位未在提供材料中明确列出；致谢提及 Stanford Graduate Fellowship、Stanford Medicine Catalyst，暗示 Stanford 相关，但未提供正式单位字段）
- 期刊/预印本平台：ArXiv（PubMed 收录记录）
- 年份：2026-10-25（日期字段）
- 论文类型：Review / Perspective（综述与观点文章）
- 领域：蛋白质生成建模、蛋白质设计、物理建模、AI for Science
- 关键词：未提供（正文未列关键词）
- DOI/arXiv 号：DOI/ID 42922854（PubMed ID）；arXiv 号未提供
- 代码：未提供
- 数据：未提供（综述，无自有数据集）
- 阅读日期：未提供
- 在「蛋白质结构相关计算研究 × AI 方法/物理模拟」方向中的位置：本文是一篇立场性综述，主张在蛋白质生成建模（结构预测、构象生成、序列/结构设计）中重新重视物理基础，梳理了物理项在生成流程中「作为先验、作为过滤/引导、作为表示与架构约束、作为实验闭环」的现存位置，并指出未建模物理成分（溶剂、静电、质子化态、动力学、选择性等）带来的失效模式。对做结构预测、构象采样、分子对接、MD、结构/序列设计的读者，本文提供的是方法论地图与可迁移的设计原则，而非新算法或新基准。

## 02 一句话总结
本文通过综述蛋白质生成建模流程中物理仍然存在的位置与未建模物理成分导致的失效（如电荷反转突变不改变共折叠预测姿态、长度泛化下降、低温度采样几乎成为必需），主张以物理接地的学习表示、物理启发的架构正则化以及实验数据闭环更新生成模型，作为功能性蛋白质设计的基础，但结论为观点性、未给出统一量化验证。

## 03 研究问题
- 具体问题：当蛋白质建模从物理方程（force fields、energy functions、rotamer libraries、molecular mechanics）转向直接在结构数据上训练的生成模型时，物理在何处仍然必要？哪些物理相关成分被遗漏，遗漏后会产生什么可观察的失效？
- 为什么重要：生成模型采样效率远高于物理方法，但设计任务（binder design、酶设计）常要求采样到训练分布之外（out-of-distribution）的区域，模型泛化性决定设计成败。
- 现有方法为何不足：结构预测模型多只在正样本上训练，作为 oracle 排序时会把 false positive 排高；预测模型对物理期望不敏感（如电荷反转不改变预测姿态）；纯结构训练目标可被「记忆非泛化特征」满足。
- 精确研究问题（Can ... ?）：Can generative protein models, trained on deposited structures, reliably sample physically plausible and functionally valid designs outside the training distribution without explicit physical modeling or experimental feedback?（本文以观点与案例回应，未做受控实验回答）

## 04 背景与发展脉络
- 阶段一：物理方程主导。force fields、energy functions、rotamer libraries、molecular-mechanics terms；Rosetta energy function 含 van der Waals packing、hydrogen bonding、electrostatics、implicit solvation 及 PDB 数据驱动项，其项被部分调参以区分 decoys 与晶体结构（Introduction）。
- 阶段二：转向数据驱动生成模型。直接在结构数据上训练，学习 noise→data 映射，采样效率显著提升；网络权重可隐式学到与物理方程相关的信息（Introduction）。
- 阶段三：物理作为过滤/引导与架构约束。BindCraft 用 Rosetta 物理项过滤；Feynman-Kac resampling、beam search、RL 对不可微物理奖励引导去噪；RFdiffusion 由 RoseTTAFold 微调为生成模型；Potts 模型作为二阶架构正则化（TERMinator、ChromaDesign、Caliby）；SLAE 用非对称 encoder-decoder 以局部全原子表示编码全局折叠并做能量监督（正文各节）。
- 阶段四：实验闭环。design-build-test-learn、Bayesian optimization 更新先验、定向进化、以及高通量新实验（TMT 质谱、HDX、NMR、bead display）扩展可建模空间（正文各节）。
- 本文主张的位置：物理并未被取代，而是以隐式先验、过滤/引导、表示与架构约束、实验闭环等形式持续存在；尊重底层物理是功能蛋白设计的基础（Abstract、Conclusion）。
- 脉络标注：以上脉络为「仅本文框架」，基于本文 Introduction 与各节叙述整理，未经外部文献核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 生成模型学到非物理特征 | 在 out-of-distribution 设计场景下失效 | 训练数据为沉积结构经验分布，与溶液/天然细胞环境分布相关但不等价 | Introduction；"Generative models as physical priors" 节 |
| 结构预测 oracle 排序不可靠 | 电荷反转突变未改变预测配体结合姿态，置信度未显著下降 | 共折叠模型倾向在训练分布内插值，未充分捕捉物理期望 | "Limitations of structure prediction models for ranking designs" 节，引用 [17-19] |
| 预测派生指标排高 false positive | ipSAE 等按界面一般分布排序，无法区分样本内细微不兼容 | 指标继承 oracle 泛化极限 | 同节，Figure 2 |
| 长度泛化差 | 长蛋白在 designability 指标上表现更差 | 长度是训练集统计属性而非物理变量，物理未被充分捕捉 | 同节，引用 [8,21] |
| 低温度采样几乎必需 | 需在推理时集中概率密度到高置信区域才能产出可设计样本 | 集中到分布众数等价于平均掉未建模的隐变量 | "Implications of unmodeled physical components" 节 |
| 未建模物理成分 | 显式溶剂、去溶剂化能垒、熵/焓贡献、pH/温度稳定性、质子化态、off-target 竞争、静电长程、动力学 | 部分为有意省略（如氢原子仅在高分辨晶体中解析），部分对设计成败关键 | 同节；丝氨酸水解酶设计中活化水未显式建模 |
| 过度稳定化倾向 | 低温度采样加剧采样过度稳定设计，忽略生物学相关模式 | 未显式建模动力学，过度优化 designability | "Kinetics as an explicit design objective" 节，引用 [8] |

## 06 核心思想
1) 表面方法：综述并分类当前在生成建模流程中保留或注入物理的实践路径——物理项作后验过滤（BindCraft）、作去噪过程引导（Feynman-Kac resampling、beam search、RL）、作架构正则化（Potts 二阶项）、作表示组织（SLAE 全原子局部表示 + 能量监督）、作实验闭环（Bayesian optimization、定向进化、高通量新实验）。
2) 核心洞察：生成模型本质上是学习训练数据的经验分布，物理被隐式编码；但设计任务要求采样到分布外区域，此时隐式物理不足，未建模的物理成分（溶剂、静电、质子化、动力学、选择性）成为失效来源；因此需要物理接地的表示与架构，并用实验数据持续更新生成模型。
3) 可能的普适教训 [Analysis]：在数据驱动结构建模中，「哪些物理量被显式建模、哪些被平均掉」应作为设计决策显式记录；低温度采样等推理技巧可能是在补偿未建模隐变量，而非纯粹的采样优化；评估生成模型应看其能否高效把概率密度重新分配到高质量但分布外的样本上，而非仅看 designability 基线。

## 07 方法总览
- 输入：已解析的蛋白质结构数据（PDB 经验分布）、物理量（坐标、键几何）、可选物理计算（经典或量子预计算能量）、实验测量（稳定性、HDX、NMR、表达量、Kd）。
- 输出：观点性框架与策略分类；无新模型或新数据产物。
- 模块（本文讨论的流程组件）：生成先验（generative prior）、物理过滤/引导（filters/guidance）、结构预测 oracle、物理接地表示（all-atom latent space）、物理启发架构（Potts 参数化）、实验闭环（design-build-test-learn）、新实验测定。
- 训练：本文不训练模型；描述他人训练方式（如 SLAE 非对称 encoder-decoder 联合能量预测与全局重构；RFdiffusion 由 RoseTTAFold 微调；Boltz-2 affinity module 在训练中更新去噪模块表示）。
- 工具：Rosetta、BindCraft、RFdiffusion、RoseTTAFold、AlphaFold3、LASErMPNN、COMBS、Metal3D、Caliby、Protpardelle、PLACER、ChromaDesign、TERMinator、ProteinMPNN、SLAE、Boltz-2、AlloGen、autoguidance。
- 反馈回路：设计→实验测试→Bayesian optimization 更新先验；或设计作为定向进化起点，由突变与选择联合优化未建模隐约束。
- 假设：物理支配物理上合理的结构；二阶项对捕捉蛋白结构与功能必要且充分；实验数据可扩展可建模空间。
- 文字流程：结构数据训练生成先验 → 设计目标与先验分布存在 shift → 用物理项过滤或引导去噪 → 用结构预测 oracle 与物理指标排序 → 实验测试作为物理世界查询 → 数据回灌更新先验/能量项 → 迭代。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 生成先验（generative prior） | 学习结构经验分布，高效采样 | 采样效率远高于物理方法 | 结构数据 → 样本 | "Generative models as physical priors" 节 | 预期失去高效采样能力（预期效应，未实测） |
| 物理项作过滤（BindCraft + Rosetta terms） | 后验筛除物理不合理设计 | 先验与目标分布存在 shift | 生成设计 → 过滤后设计 | "Physical terms as filters and guidance" 节，引用 [10,11] | 预期保留更多非物理样本（预期效应） |
| 物理项作引导（Feynman-Kac resampling / beam search / RL） | 在去噪过程中朝物理有效性奖励偏移 | 过滤受限于生成器已提出的样本 | 去噪轨迹 + 不可微奖励 → 引导样本 | 同节，引用 [7,13,14] | 预期无法在生成中纠正物理不合理（预期效应） |
| 结构预测 oracle（ipSAE 等） | 排序设计置信度 | 快速筛选 | 序列/结构 → 置信度分数 | "Limitations..." 节，Figure 2 | 实测：排高 false positive，无法区分细微不兼容 |
| autoguidance | 用欠训练「坏」模型把采样推离失败模式 | 引入负样本 | 生成模型 + 坏版本 → 偏移样本 | 同节，引用 [20] | 预期减少失败模式（预期效应） |
| SLAE 非对称 encoder-decoder | 用局部全原子信息编码全局折叠，解码器预测能量 | 弥合局部原子特征与全局折叠的信息鸿沟，防记忆伪特征 | 局部原子表示 → 潜空间 → 重构 + 能量 | "Using physical energies to organize an all-atom latent space" 节，引用 [22,23] | 实测消融：解码器预测能量对局部表示在全局重构与下游任务（NMR 化学位移、功能预测、全原子侧链重构）上同时表现良好是必需的 |
| Potts 架构正则化（TERMinator/ChromaDesign/Caliby） | 限制序列分布到一阶与二阶项 | 二阶项被认为必要且充分，防高阶伪相关 | 网络输出 → Potts 参数 → 序列采样 | "Physics-inspired architectural regularization" 节，引用 [6,30-34] | 实测（引用）：ProteinMPNN 相比 ChromaDesign/Caliby 在长蛋白 designability 下降 |
| 实验闭环（Bayesian optimization / 定向进化） | 用实验数据更新先验 | 未建模成分难以纯计算捕捉 | 实验测量 → 更新后先验 | "Testing designs as plausibility queries..." 节，引用 [50-52] | 预期无实验则无法校正未建模约束（预期效应） |
| 新实验测定（TMT-MS、HDX、NMR、bead display） | 扩展可观测可建模性质 | 提高通量以支撑建模 | 蛋白库 → 稳定性/动力学/表达/Kd 数据 | "New assays to expand the modelable space" 节，引用 [53-57] | 预期扩大可建模空间（预期效应） |

## 09 关键公式符号
不适用（本文为综述/观点文章，未给出需理解的核心公式；仅提及 Potts 模型的一阶与二阶项概念、Rosetta energy function 的组成项，但未列出具体公式）。

## 10 实验设计与证据链
- 数据集/群体：本文无自有实验。引用他人数据包括：3,766 个实验表征 binders 的 meta-analysis；18,987 个蛋白结构域（TMT 质谱聚集测量，pH 4 / 50 °C / 75 °C，浓度归一至 10 mg/mL）；5,778 个蛋白结构域（HDX，pH 6 与 pH 9）；384 个设计蛋白（NMR，每周 224 个为瓶颈，表达体积可缩至 16 mL）；>100,000 蛋白/天表达纯化，3 天协议量化 18,000 变体的表达水平与平衡解离常数。
- 规模、指标、基线、预算、骨干/仪器、oracle 输入、评测协议：本文未提供统一评测协议；各引用工作指标各异（designability、ipSAE、置信度、速率提升倍数、解离速率等）。仪器包括质谱、NMR 谱仪、bead display。
- 表格：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 3,766 binders meta-analysis | 物理指标是否提供额外预测力 | 物理指标 vs 仅结构预测指标（如 ipSAE） | 物理指标提供额外预测力以区分 in silico binders 与非 binders | 物理项在排序中有增量价值 | 不支持「物理指标可完全替代 oracle」 | "Physical terms as filters and guidance" 节，引用 [12] |
| 电荷反转突变 | 共折叠模型是否捕捉静电物理期望 | 预期静电废除与带负电 ATP 的互作 | 预测配体结合姿态未扰动，置信度未显著下降 | 共折叠模型在训练分布内插值，未充分捕捉物理期望 | 不支持「所有共折叠预测都不可靠」 | "Limitations..." 节，引用 [17-19] |
| ipSAE 排序 | 预测派生指标能否区分细微不兼容 | 按界面一般分布排序 | 排高 false positive，无法区分样本内细微不兼容 | 指标继承 oracle 泛化极限 | 不支持「ipSAE 在所有场景无效」 | 同节，Figure 2 |
| 长蛋白 designability | 长度泛化 | 长 vs 短蛋白 | 长蛋白 designability 下降 | 物理未被充分捕捉，长度是统计属性 | 不支持「长度是唯一失效因素」 | 同节，引用 [8,21] |
| SLAE 消融 | 解码器能量预测是否必需 | 有/无能量监督 | 能量预测对局部表示同时做好全局重构与下游任务必需 | 物理监督组织潜空间，防记忆伪特征 | 不支持「能量监督对所有架构都必需」 | "Using physical energies..." 节，引用 [22,23] |
| ProteinMPNN vs ChromaDesign/Caliby | 二阶 Potts 正则化是否影响长蛋白 designability | 不同参数化 | ProteinMPNN 长蛋白 designability 下降 | 二阶项限制可防高阶伪相关 | 不支持「高阶项一律有害」 | "Physics-inspired architectural regularization" 节，引用 [31] |
| 丝氨酸水解酶设计 | 氧阴离子洞 motif 是否提升速率 | 模仿天然酯水解酶，用催化丝氨酸后一残基构建 | 五倍速率提升 | 电荷稳定（静电）对催化重要 | 不支持「该 motif 可普遍迁移到所有酶」 | "Implications of unmodeled physical components" 节，引用 [39] |
| Broerman et al. 应变中间体 | 动力学能否作为显式设计目标 | 有意设计冲突，沿二级结构轴剪切 vs 需旋转解决 | 沿轴剪切解离速率更快 | 动力学可被显式设计 | 不支持「生成模型可自动访问应变态」 | "Kinetics as an explicit design objective" 节，引用 [49] |

## 11 结论正确解读
- 任务范围：本文是观点/综述，不提供端到端新方法或基准；其结论是策略性主张，不是受控实验结论。
- oracle/真值输入：讨论的失效案例依赖结构预测 oracle 与物理指标作为代理真值，本身非实验真值。
- 端到端状态：所引设计案例（exatecan binder、锌依赖磷酸酶、丝氨酸水解酶）为端到端设计-实验案例，但本文未做统一复现或统计。
- 算力成本：未提供。
- 历史数据依赖：核心论点是生成模型逼近 PDB 沉积结构经验分布，该分布偏向可折叠、可结晶、常冷冻的蛋白，与溶液/细胞环境分布相关但不等价。
- 模型依赖：结论依赖所引具体模型（RFdiffusion、AlphaFold3、SLAE、Boltz-2 等）的行为，换模型可能改变具体表现。
- 最难情形：out-of-distribution 设计、长蛋白、需选择性、需动力学平衡、需显式静电与质子化态的场景。
- 群体/领域边界：主要面向蛋白质（含 binder、酶），未覆盖核酸、膜环境、翻译后修饰等。
- 不确定性：多数「移除后影响」为预期效应而非实测；物理指标增量价值仅由一项 meta-analysis 支持。
- 有边界复述：在本文所引证据范围内，物理项在生成设计流程中仍以过滤、引导、表示组织、架构正则化与实验闭环形式存在，且未建模物理成分与若干可观察失效相关；本文主张尊重物理是功能蛋白设计的基础，但未提供统一量化验证。

## 12 作者自认局限
在提供的材料中未发现作者明确承认的局限（本文为综述/观点，未设 Limitations 节）。

作者提及的相关约束（非正式局限）：
| 约束 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 未建模物理成分 | 显式溶剂、去溶剂化能垒、熵/焓、pH/温度稳定性、质子化态、off-target 竞争、静电长程、动力学 | 用物理接地表示与实验数据更新生成模型 | "Implications of unmodeled physical components" 节 |
| 生成模型无法访问应变态 | 需手动指定应变态 | 将动力学作为显式设计目标 | "Kinetics as an explicit design objective" 节 |
| 实验通量瓶颈 | NMR 每周 224 个为瓶颈 | 新实验方法扩展可建模空间 | "New assays to expand the modelable space" 节 |
| 数据驱动工具将剧变 | 依赖 lab-in-a-loop 与自动化成熟度 | 数据中心设计工具将发生显著转变 | Conclusion |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 「物理指标提供额外预测力」仅由一项 3,766 binders meta-analysis 支持 | 可能受数据集选择、指标阈值、binder 类型偏倚影响 | 若增量价值不稳健，过滤策略收益被高估 | 在多个独立 binder 数据集上重复，控制指标与阈值 | "Physical terms as filters and guidance" 节，引用 [12] |
| 电荷反转案例被用来论证共折叠模型不捕捉物理 | 也可能是该突变确实不显著改变结合姿态（物理上非关键），或预测置信度定义不敏感 | 结论方向影响是否应弃用 oracle 排序 | 系统扫描电荷突变并对照实验结合数据 | "Limitations..." 节，引用 [17-19] |
| 「低温度采样平均掉未建模隐变量」为机制性解释 | 也可能是低温度采样仅降低方差、提升可设计性，与隐变量无关 | 该解释决定是否应把低温度采样视为补偿手段 | 对比显式建模隐变量后是否仍需低温度采样 | "Implications of unmodeled physical components" 节 |
| 「二阶项必要且充分」被用作架构正则化依据 | 该结论可能依赖特定数据集与功能定义 | 若高阶项在部分功能中必要，Potts 瓶颈会限制表达力 | 在需高阶相关性的任务上对比 Potts 与自回归模型 | "Physics-inspired architectural regularization" 节，引用 [32-34] |
| 长度泛化差被归因于物理未被捕捉 | 也可能是位置编码/注意力长度外推等架构因素 | 归因决定改进方向（物理 vs 架构） | 控制架构与训练分布，分离长度与物理变量 | "Limitations..." 节，引用 [8,21] |
| 实验闭环被推荐为通用解法 | 高通量实验成本与可及性可能限制普适性 | 影响该方法对普通课题组的可行性 | 统计各实验方法的成本/通量与覆盖性质 | "New assays..." 节，引用 [53-57] |
| 综述未给出统一评测协议 | 各案例指标不可比，结论难以量化 | 读者无法判断物理注入的边际收益大小 | 建立统一 benchmark 比较各物理注入策略 | 全文 |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念：生成模型 = 训练数据经验分布的先验；设计 = 把先验朝 bespoke 分布偏移。对本课题（结构预测/构象采样/设计），应显式区分「先验覆盖区」与「目标采样区」，并评估分布外泛化。
- 可迁移方法一：物理项作过滤与作引导的二分。过滤受限于生成器已提出样本；引导（Feynman-Kac resampling、beam search、RL 对不可微奖励）可在生成中纠正。可迁移到构象采样：用物理有效性奖励引导扩散/流匹配去噪。
- 可迁移方法二：autoguidance 用欠训练「坏」模型把采样推离失败模式，动机类似 Rosetta 调参区分 decoy 与 native，但更灵活、不受物理方程表达力限制。可迁移到对接/构象生成中的负样本引导。
- 可迁移方法三：SLAE 非对称 encoder-decoder——用严格局部全原子信息编码全局折叠，解码器同时做能量预测与重构，使潜空间沿物理有意义轴组织，并支持物理平滑的线性插值。可迁移到构象采样：以局部表示为瓶颈 + 能量监督，可能获得更平滑的构象插值路径。
- 可迁移方法四：Potts 二阶参数化作为架构正则化瓶颈，防高阶伪相关。可迁移到序列设计：在自回归与二阶模型间做表达力-泛化权衡。
- 可迁移方法五：把实验数据作为物理世界查询，用 Bayesian optimization 更新先验；评估指标改为「多快能把概率密度重新分配到高质量但分布外样本」。
- 可迁移公式/符号：无具体公式；可迁移的是「一阶+二阶项必要且充分」这一假设及其检验方式。
- 可迁移实验设计：用消融（如 SLAE 有无能量监督）验证物理监督是否为必需；用长度分层评估泛化；用负样本/对抗突变检验 oracle 物理敏感性。
- 对本课题的迁移建议：在 MD/对接/AlphaFold 组合流程中，明确列出未建模成分（溶剂、质子化、长程静电、动力学），并判断哪些应由生成模型隐式承担、哪些必须显式注入或实验校正。

## 15 与已有知识连接
- 相似：Rosetta energy function 调参区分 decoy 与 native（Introduction，引用 [3]）与 autoguidance 引入负样本（引用 [20]）动机相似。
- 组合：物理过滤（BindCraft + Rosetta terms）与结构预测 oracle 置信度组合使用（引用 [10,11]）；SLAE 的局部表示 + 能量监督与 Boltz-2 affinity module 在训练中更新去噪表示（引用 [28]）思路相近。
- 冲突：自回归模型可表达任意阶分布 vs Potts 二阶项被认为必要且充分（引用 [32-34]）；结构预测 oracle 被广泛用作排序 vs 本文指出其物理不敏感与 false positive 排序问题。
- 可迁移领域：MLIP（machine learning interaction potential）以局部原子环境预测相互作用能（引用 [24,25]）可迁移到蛋白全原子能量建模；科学基础模型内部表示收敛（引用 [26,27]）提示跨模型共享物理结构。
- 外部核验状态：以上连接均来自本文引用，未由本 Card 独立核验；标注为「经本文引用、未外部核验」。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：物理隐变量显式化后低温度采样必要性检验
- 来源局限/观察：本文称低温度采样几乎总是必需，并解释为平均掉未建模隐变量（"Implications of unmodeled physical components" 节）。
- 核心假设：若在生成模型中显式建模质子化态与显式溶剂，则达到同等 designability 所需的最低采样温度会上升。
- 相对本文的增量：把机制性解释转为可证伪的受控实验。
- 初步方法：在扩散/流匹配结构生成模型中加入质子化态与隐式溶剂条件，扫描采样温度，比较 designability 与物理指标。
- 验证方式：温度-designability 曲线位移；实验验证少量样本。
- 可能的失败模式：designability 与温度关系由架构而非隐变量主导，无位移。
- 创新状态：unverified。

2. 名称：局部全原子瓶颈 + 能量监督用于构象集合采样
- 来源局限/观察：SLAE 用局部信息编码全局折叠并做能量监督，实现物理平滑线性插值（"Using physical energies..." 节）。
- 核心假设：将 SLAE 式非对称 encoder-decoder 用于构象集合生成，可得到比标准扩散更物理平滑的构象插值路径与更低的物理违规率。
- 相对本文的增量：把 SLAE 从单结构表示扩展到构象集合采样任务。
- 初步方法：以局部原子环境为 encoder 输入，decoder 联合重构与能量预测，在 MD 集合上训练与评估。
- 验证方式：插值路径的物理合理性（键长/冲突/能量）、与 MD 集合的覆盖度对比。
- 可能的失败模式：局部瓶颈丢失长程耦合信息，集合多样性不足。
- 创新状态：unverified。

3. 名称：oracle 物理敏感性对抗测试套件
- 来源局限/观察：电荷反转突变未改变共折叠预测姿态（"Limitations..." 节，引用 [17-19]）。
- 核心假设：可构建一套系统化对抗突变（电荷、质子化、去溶剂化）测试套件，量化结构预测 oracle 的物理敏感性，并据此加权排序。
- 相对本文的增量：把单案例扩展为可复用基准与排序校正。
- 初步方法：对已知结合数据生成对抗突变，测 oracle 置信度与姿态变化，拟合敏感性权重。
- 验证方式：在 binder 排序任务上比较加权前后 false positive 率。
- 可能的失败模式：对抗突变在物理上确实不关键，套件无区分度。
- 创新状态：unverified。

4. 名称：二阶 Potts 瓶颈与高阶项的按任务切换
- 来源局限/观察：二阶项被认为必要且充分，Potts 参数化提升长蛋白 designability（"Physics-inspired architectural regularization" 节，引用 [31-34]）。
- 核心假设：存在一类功能（如别构、长程耦合）需要高阶项，按任务自适应选择阶数优于固定二阶。
- 相对本文的增量：把「二阶充分」从全局假设变为任务条件假设。
- 初步方法：在 Potts 与自回归模型间插值阶数，按任务评估 designability 与功能保持。
- 验证方式：分层任务基准 + 实验验证少量设计。
- 可能的失败模式：高阶项仅增加过拟合，无功能增益。
- 创新状态：unverified。

5. 名称：以「分布外高质量样本重分配效率」为生成模型评估指标
- 来源局限/观察：本文建议以模型多快把概率密度重新分配到高质量但分布外样本上评估（"Testing designs as plausibility queries..." 节）。
- 核心假设：该指标比 designability 基线更能预测设计战役成功率。
- 相对本文的增量：把建议指标操作化并做预测力检验。
- 初步方法：定义分布外高质量集（实验验证的 novel binders），测模型采样命中率与所需样本数，与 designability 相关性比较。
- 验证方式：多模型多任务回溯分析。
- 可能的失败模式：指标与实验成功率无相关性。
- 创新状态：unverified。