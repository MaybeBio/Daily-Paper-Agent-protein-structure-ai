## 01 基本信息
- 标题：Evaluation of Physics-Based Pose Prediction and the Role of Receptor Flexibility in a Community Antiviral Blind Challenge
- 作者与单位：Khoualdi, Asma Feriel; Clark, Finlay; Horton, Joshua T; Cole, Daniel J（单位未在提供材料中列出）
- 期刊/预印本平台：Journal of Chemical Information and Modeling
- 年份：2026-10-26（在线日期）
- 论文类型：方法评估 / 盲挑战赛参赛报告（prospective + retrospective 分析）
- 领域：计算机辅助药物设计；protein–ligand pose prediction；physics-based docking / molecular growth；ML/MM 势能；side-chain flexibility
- 关键词：未提供（正文未列关键词）
- DOI/arXiv 号：10.1021/acs.jcim.6c02582
- 代码：https://github.com/cole-group/polaris-fegrow ；https://github.com/jthorton/polaris_fegrow_mcs ；https://github.com/AsmaFeriel000/ASAP-polaris-data ；FEgrow: https://github.com/cole-group/FEgrow ；ApoDock: https://github.com/ld139/ApoDock_public ；修改版: https://github.com/AsmaFeriel000/ApoDock_public
- 数据：挑战赛数据 https://zenodo.org/records/15582067
- 阅读日期：未提供
- 在「蛋白质结构相关计算研究 × AI 方法/物理模拟」方向中的位置：本文处于 physics-based pose prediction（模板化分子生长 + ML/MM 势能）与 AI 侧链构象生成（ApoDock）交叉点，并以盲挑战赛为评测框架，直接关联 docking、构象采样、受体柔性、以及用深度学习打分函数/ABFE 从构象集合中挑选 native pose 的问题。

## 02 一句话总结
在 ASAP-Polaris-OpenADMET 抗病毒盲挑战的 pose prediction 赛道中，作者用基于模板化分子生长与 ML/MM 势能的 FEgrow 提交物理方法参赛，并通过回顾性引入 MCS 核心选择、训练集受体结构与 ApoDock 侧链集合，将 SARS-CoV-2/MERS-CoV Mpro 的 <2 Å RMSD 成功率提升到 74%，但发现所测试的打分函数（ApoScore、gnina）与短时 ABFE 均无法显著优于随机挑选来从生成集合中选出 native pose。

## 03 研究问题
- 具体问题：在受体结构已知、训练数据有限或分布不均的盲挑战设定下，physics-based 的模板化分子生长方法能达到多高的 pose prediction 成功率？受体侧链柔性对成功率有多大影响？能否用打分函数或短时 ABFE 从生成的受体–配体复合物集合中可靠地挑出接近晶体结构的 pose？
- 为什么重要：pose prediction 是 physics-based 亲和力预测与 alchemical free energy 计算的前置步骤，错误 pose 会限制下游精度；同时盲挑战提供客观、统一数据与指标的横向比较。
- 现有方法为何不足：cofolding 方法（AlphaFold3、Boltz-1 等）在挑战中表现最好（>80%），但可能依赖训练数据中 Mpro 的充分代表性，泛化到新靶标存疑；deep-learning docking 表现最差（0–29%）；physics-based 方法成功率 16–67%，且多数依赖模板对齐；刚性受体近似在部分案例中根本无法恢复 native pose。
- 精确研究问题（Can ... ?）：Can a template-based physics workflow, combined with ligand-conditioned side-chain ensemble generation, generate and then reliably select native-like binding poses (RMSD < 2 Å) for SARS-CoV-2 and MERS-CoV Mpro ligands when only limited target-specific training data are available?

## 04 背景与发展脉络
（注：以下脉络主要依据本文 Introduction 的叙述，属「仅本文框架」；未做外部独立核验。）
- 阶段 1：传统实验筛选——劳动与资源密集，难以快速响应突发卫生事件。
- 阶段 2：physics-based docking / scoring——可快速探索化学空间，但打分函数与刚性受体近似限制精度。
- 阶段 3：模板化对接与分子生长（如 POSIT、FlexX、FEgrow）——利用晶体结构信息约束核心，提升 pose 质量；本文的 FEgrow 属此类，采用 ML/MM（ANI-2x + 经典力场）描述配体内部能量。
- 阶段 4：cofolding 方法（AlphaFold3、Boltz-1、Chai、OpenFold）——在挑战中表现最佳，但依赖训练数据中近缘同源物；配体-only 基线（约束 3D embedding）也达约 70%，提示训练集中存在大量近缘配体 pose。
- 阶段 5：侧链构象生成方法（DLPacker、AttnPacker、ApoDock）——在已知 backbone 下生成侧链集合；DLPacker/AttnPacker 为 ligand-agnostic，ApoDock 为 ligand-conditioned。
- 本文主张的位置：physics-based 方法在新靶标、低数据场景仍有价值，且可用于扩充 cofolding 训练数据；但需正视刚性受体近似与从集合中挑选 pose 的困难。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 刚性受体近似导致无法恢复 native pose | 某些案例中预测 pose 与晶体结构差异大，且 native pose 会与参考结构侧链（如 Q189）冲突 | 参考结构侧链取向与真实 holo 构象不符；刚性受体无法诱导契合 | Results「Rigid Receptor Approximation Limits Achievable Accuracy」及 Figure 3c |
| 训练数据分布不均导致 MERS-CoV 表现差 | 手动核心提交中 SARS-CoV-2 约 60%、MERS-CoV 约 40% <2 Å | MERS-CoV 仅提供单一参考结构，训练信息少 | Results 及 Figure 2a/2b |
| 从生成集合中挑选 native pose 困难 | ApoScore、gnina 在 SARS-CoV-2 上均与随机挑选相当（约 40%）；ABFE 亦无显著改善 | 打分函数忽略相对蛋白能量学；短时 ABFE 采样不足、配体/侧链应变未充分弛豫 | Results「Scoring Functions Cannot Reliably Sort Binding Poses from Decoys」及 Figure 5、Figure 6 |
| 用户对齐错误 | 11 个 MCS 提交结构被错误对齐到受体错误链，RMSD 异常高 | 操作/流程错误 | Methods「Prospective Submission: Maximum Common Substructure Core Selection」 |
| 部分分子无法用 FEgrow 构建 | SARS-CoV-2 8 个、MERS-CoV 7 个无法构建 | 未明确说明具体成因 | Methods 各小节 |

## 06 核心思想
1) 表面方法：用 FEgrow 在固定核心约束下将配体生长进 Mpro 结合口袋，配体内部能量用 ANI-2x ML 势、分子间作用用经典力场（OpenFF-Sage + AMBER FF14SB）；回顾性引入 MCS 自动核心选择、训练集受体结构、以及 ApoDock 生成的侧链集合，再用 ApoScore/gnina/ABFE 排序。
2) 核心洞察：模板化分子生长能生成大量低 RMSD pose（top-1 约 90% SARS-CoV-2、80% MERS-CoV <2 Å），但「生成」与「挑选」是两个独立瓶颈；受体侧链柔性对 MERS-CoV 这类更柔性的靶标尤其重要，但现有打分函数无法可靠挑出 native pose。
3) 可能的普适教训 [Analysis]：在 physics-based pose prediction 中，扩大受体构象集合可提高 native pose 的「可及性」，但若没有与蛋白能量学耦合的打分方法，集合扩大反而可能降低 top-1 表现（SARS-CoV-2 上集合方法劣于原始提交）；训练数据的丰富程度同时惠及 cofolding 与 physics-based 模板方法。

## 07 方法总览
- 输入：配体结构/SMILES；受体结构（参考结构或训练集结构）；用户定义或 MCS 选出的核心。
- 输出：配体在受体口袋中的 pose（复合物结构）；以及用于排序的分数（ApoScore、gnina、ABFE）。
- 模块：RDKit ETKDG 构象生成 + UFF 预优化（核心施加 10^4 kcal mol⁻¹ Å⁻² 谐波约束）→ 过滤（RMSD <0.5 Å 重复、原子间距 <1 Å 冲突）→ OpenMM 优化（蛋白固定，AMBER FF14SB + OpenFF-Sage/AM1-BCC，LJ 半径与电荷缩放）→ ANI-2x 计算配体内部能量 → 取最低能量构象为最佳 pose；回顾性加入 ApoDock 生成 20 个侧链重构受体结构；排序用 ApoScore/gnina/短时 ABFE。
- 训练：无模型训练；ANI-2x 为预训练 ML 势；ApoDock/ApoScore/gnina 为预训练模型。
- 工具：FEgrow、RDKit、OpenMM、AmberTools、ANI-2x、ApoDock、ApoScore、gnina、PyMOL。
- 反馈回路：无显式反馈回路；回顾性分析为事后调整。
- 假设：配体内部低能构象比蛋白同源物间结构差异更重要（用于 MERS-CoV 映射回参考结构）；短时 ABFE 可将配体动力学困在初始 pose 附近。
- 文字流程：配体构象生成 → 核心约束预优化 → 冲突过滤 → 固定蛋白下 ML/MM 优化 → 取最低能量 pose → （回顾性）在 ApoDock 侧链集合上重复 → 用打分函数/ABFE 排序选 top-1。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| FEgrow 模板化生长 | 在固定核心约束下生长配体 | 最大化利用晶体结构信息 | 输入：核心+配体+受体；输出：pose | Methods；Results Figure 2 | 实测：无核心约束的 gnina 对接仅 ≤20% <2 Å（Figure 5 紫线） |
| ANI-2x ML/MM 势 | 高精度配体内部能量 | 接近 QM 精度但成本低 | 输入：配体构象；输出：能量 | Methods | 预期：替换为 OpenFF-Sage 用于 14 个失败分子（Methods），未单独消融 |
| MCS 核心选择 | 自动从训练集选核心 | 减少人工任意性、更多利用训练数据 | 输入：训练集+测试配体；输出：核心 | Results Figure 2a；54% vs 47% | 实测：SARS-CoV-2 提升至约 70%，但依赖训练数据量 |
| 训练集受体结构 + SARS-CoV-2 数据映射到 MERS-CoV | 用最近 MCS 匹配的受体结构 | 同源配体可能对应同源受体构象 | 输入：训练集；输出：改进的 MERS-CoV pose | Results Figure 2（MCS-based retrospective） | 实测：MERS-CoV 提升至约 80%，总体 74% |
| ApoDock 侧链集合 | 生成 20 个侧链重构受体 | 引入受体柔性 | 输入：backbone+SMILES；输出：20 个复合物 | Methods；Results Figure 4 | 实测：增加低 RMSD pose 数量（MERS-CoV pocket RMSD <2 Å 从 32% 升至 59%），但 top-1 挑选困难 |
| ApoScore / gnina 排序 | 从集合中选 pose | 需要前瞻性挑选 | 输入：复合物；输出：分数 | Results Figure 5 | 实测：SARS-CoV-2 上与随机相当；MERS-CoV gnina 约 60% |
| 短时 ABFE | 物理严谨排序 | 理论上最严谨 | 输入：复合物；输出：ΔG | Results Figure 6；Section S1 | 实测：27 个中性 MERS-CoV 配体上不优于随机 |

## 09 关键公式符号
- 未提供显式公式。文中提及的度量与概念：
  - symmetry-corrected heavy-atom RMSD < 2 Å：成功判据（Results）。
  - FBL（Bayly's fraction of best ligand）：衡量低 RMSD pose 在低预测自由能 pose 中的富集（Results）。
  - 平均 intercomplex spread 14.7 kcal mol⁻¹；平均 inter-replicate standard error 1.5 kcal mol⁻¹（Results）。
- 其余公式：不适用。

## 10 实验设计与证据链
- 数据集/群体：训练集 770 个 SARS-CoV-2 Mpro 晶体结构；测试集 98 个 SARS-CoV-2 Mpro 配体 + 97 个 MERS-CoV Mpro 配体；MERS-CoV 仅 1 个参考复合物结构。
- 规模：挑战赛共 381 份提交、66 位参与者；physics-based 类别 13 份提交。
- 指标：symmetry-corrected heavy-atom RMSD < 2 Å 成功率；FBL；pocket RMSD。
- 基线：随机挑选（重复 100 次平均）；gnina 无偏对接；POSIT、FlexX、Glide、EasyDock/AutoDock、Vina+片段约束等。
- 预算：挑战赛 8 周；ABFE 为 0.1 ns/window 短时计算，每个复合物 5 次独立平衡。
- 骨干/仪器：Comet HPC（Newcastle University）。
- oracle 输入：回顾性分析使用了 released 晶体结构（hindsight），但作者声明除 hindsight 外未使用盲挑战开始时不可得的信息。
- 评测协议：挑战赛官方 blinded 评测；回顾性分析为事后重算。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 手动核心 FEgrow 提交 | 模板化生长可竞争 | vs 其他 physics-based | SARS-CoV-2 约 60%、MERS-CoV 约 40% <2 Å | 方法有竞争力 | 不能说明优于模板对接 | Results Figure 2a/2b |
| MCS 核心选择 | 自动核心提升成功率 | vs 手动核心 | 54% vs 47%（校正对齐后） | MCS 有用但依赖训练数据 | 不能说明低数据场景同样有效 | Results |
| 回顾性训练集受体 + 跨靶标映射 | 利用训练集受体提升 MERS-CoV | vs 单一参考结构 | MERS-CoV 约 80%，总体 74% | 训练数据丰富度惠及 physics-based | 不能说明无训练数据时可行 | Results Figure 2 |
| ApoDock 侧链集合 | 侧链柔性增加低 RMSD pose | vs 单一参考结构 | MERS-CoV pocket RMSD <2 Å 从 32% 升至 59%；top-1 约 90%/80% | 集合富集 native-like pose | 不能说明可直接挑选 | Results Figure 4 |
| ApoScore/gnina 排序 | 打分函数可挑 native pose | vs 随机 | SARS-CoV-2 均约 40%，与随机相当；MERS-CoV gnina 约 60% | 打分函数不可靠 | 不能说明所有打分函数都失败 | Results Figure 5 |
| 短时 ABFE | ABFE 可挑 native pose | vs 随机；27 个中性 MERS-CoV 配体 | 无显著改善（paired bootstrap） | 短时 ABFE 不足以排序 pose | 不能说明长时 ABFE 无效 | Results Figure 6；Section S1 |
| gnina 无偏对接 | 无约束对接基线 | vs 模板生长 | ≤20% <2 Å | 模板约束重要 | — | Results Figure 5 紫线 |

## 11 结论正确解读
- 任务范围：仅针对 SARS-CoV-2 与 MERS-CoV Mpro 的 pose prediction，非亲和力或 ADMET。
- oracle/真值输入：回顾性分析使用了 released 晶体结构；前瞻性提交未使用。
- 端到端状态：生成与挑选未打通；生成可，挑选不可靠。
- 算力成本：ABFE 为短时（0.1 ns/window），非长时收敛计算。
- 历史数据依赖：MCS 与训练集受体方法依赖 770 个 SARS-CoV-2 结构；MERS-CoV 仅 1 个参考结构。
- 模型依赖：ANI-2x、ApoDock、ApoScore、gnina 均为特定版本/预训练模型。
- 最难情形：native pose 与参考结构侧链冲突的案例（如 Q189、L49）。
- 群体/领域边界：Mpro 结合口袋相对刚性；结论不宜直接外推到其他靶标。
- 不确定性：ABFE 失败原因未完全确定（采样不足 vs 应变未弛豫）。
- 有边界的复述：在 Mpro 盲挑战设定下，模板化 physics-based 生长配合训练集受体与侧链集合可生成高比例 native-like pose（回顾性 74%），但所测试的打分函数与短时 ABFE 无法可靠挑选 top-1。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 打分函数无法挑选 native pose | ApoScore/gnina 在 SARS-CoV-2 上与随机相当 | 需要更好的挑选方法或更小的物理合理集合 | Discussion and Conclusions |
| 短时 ABFE 采样不足 | 未显著优于随机；配体/侧链应变可能未弛豫 | 进一步工作 | Results；Discussion |
| ApoDock 未按配体逐一条件化 | 为简化未对每个测试配体重复完整 ApoDock 流程 | 可能按配体逐一条件化可提升精度 | Methods |
| MCS 方法依赖训练数据 | 早期药物发现可能无足够数据 | — | Discussion |
| 用户对齐错误 | 11 个结构对齐到错误链 | 已校正 | Methods |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 回顾性 74% 使用了 released 晶体结构与训练集受体 | 可能高估前瞻性可达到的成功率 | 影响对方法实际可用性的判断 | 在真正 blinded 设定下重跑 | Results；Methods |
| ApoDock 集合仅 20 个结构且未按配体条件化 | 集合可能未覆盖真实侧链构象 | 限制生成上限 | 增大集合或按配体条件化后重评 | Methods |
| ABFE 失败归因于采样不足 | 也可能是力场/质子化/应变处理问题 | 影响后续方法选择 | 长时 ABFE 或应变校正后对比 | Results |
| SARS-CoV-2 上集合方法劣于原始提交 | 集合扩大引入噪声，打分无法过滤 | 提示「生成更多」不等于「更好」 | 控制集合大小与多样性 | Results Figure 5 |
| 随机挑选基线重复 100 次平均 | 随机基线方差可能影响显著性判断 | 影响结论稳健性 | 报告置信区间 | Results |
| MERS-CoV 仅 1 个参考结构 | 训练信息极少，结论外推受限 | 影响泛化性 | 增加同源靶标测试 | Methods |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念：模板化分子生长（核心约束）在受体结构已知时可作为 physics-based pose prediction 的强基线；训练集受体结构本身是重要信息源，不仅配体核心。
- 可迁移方法：MCS 自动核心选择；将同源靶标训练数据映射到目标靶标（backbone 对齐后映射配体）；ligand-conditioned 侧链集合生成（ApoDock）。
- 可迁移实验设计：用 top-1 与 top-N 累积分布区分「生成能力」与「挑选能力」；用随机挑选作为排序基线；用 FBL 评估富集。
- 可迁移到本课题：在蛋白质结构预测/构象采样中，可借鉴「生成集合 + 挑选」分离评估框架；在 docking/MD 中，可借鉴受体侧链集合与刚性受体近似的对照设计；在 AI 结构设计中，可借鉴「训练数据丰富度同时惠及 physics-based 与 learning-based 方法」的观察。

## 15 与已有知识连接
- 相似：FEgrow 与 CACHE Challenge 2 的 Nsp13 设计工作（本文 Introduction 自述）；Vina + 片段约束方法（本文引用）。
- 组合：ApoDock（ligand-conditioned 侧链生成）+ FEgrow（模板生长）+ ApoScore/gnina/ABFE（排序）。
- 冲突：cofolding 方法在挑战中表现最佳（>80%），但本文主张 physics-based 在新靶标/低数据场景仍有价值；配体-only 基线约 70% 提示训练集近缘配体丰富。
- 可迁移领域：CASP（蛋白结构预测盲挑战）、D3R（pose/affinity 盲挑战）；DLPacker/AttnPacker 侧链 packing。
- 外部核验状态：以上连接均来自本文 Introduction/Results 的引用，未做独立外部核验。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：蛋白能量学耦合的 pose 排序函数
   - 来源局限/观察：ApoScore/gnina/ABFE 均无法从集合中挑出 native pose；作者指出打分函数忽略相对蛋白能量学。
   - 核心假设：将受体侧链应变能与配体–受体相互作用能联合建模可提升 top-1 挑选。
   - 相对本文的增量：从「配体中心打分」转向「复合物能量学打分」。
   - 初步方法：在 ApoDock 集合上用 ML/MM 或短 MD 计算受体侧链应变 + 相互作用能，训练/拟合排序器。
   - 验证方式：在 ASAP 回顾性集合上比较 top-1 <2 Å 成功率与随机基线。
   - 可能的失败模式：应变计算噪声大、集合多样性不足。
   - 创新状态：unverified。
2. 名称：按配体逐一条件化的侧链集合生成
   - 来源局限/观察：本文为简化未对每个测试配体重复完整 ApoDock 流程。
   - 核心假设：ligand-specific 侧链条件化可提高 native-like pose 比例。
   - 相对本文的增量：从「一套集合用于所有配体」到「每配体一套集合」。
   - 初步方法：对每个配体运行 ApoDock，生成 20–50 个结构，再用 FEgrow 生长。
   - 验证方式：比较 top-1 与 top-N 累积分布。
   - 可能的失败模式：计算成本高、集合仍不覆盖真实构象。
   - 创新状态：partially checked（基于本文 Methods 的明确提示）。
3. 名称：训练数据丰富度对 physics-based pose prediction 的定量缩放律
   - 来源局限/观察：SARS-CoV-2（770 结构）与 MERS-CoV（1 结构）表现差异大。
   - 核心假设：成功率随训练集同源结构数量呈可预测的饱和曲线。
   - 相对本文的增量：从定性观察走向定量缩放。
   - 初步方法：对 SARS-CoV-2 训练集做下采样，测量成功率 vs 训练集大小。
   - 验证方式：拟合饱和曲线并外推到 MERS-CoV。
   - 可能的失败模式：下采样不模拟真实低数据分布。
   - 创新状态：unverified。
4. 名称：生成–挑选联合优化的端到端 pose 预测
   - 来源局限/观察：生成与挑选分离导致 top-1 差。
   - 核心假设：联合训练生成器与挑选器可优于两阶段。
   - 相对本文的增量：从 pipeline 到端到端。
   - 初步方法：用 FEgrow/ApoDock 生成数据训练挑选器，再反馈指导生成。
   - 验证方式：盲挑战式前瞻评测。
   - 可能的失败模式：过拟合训练集、泛化差。
   - 创新状态：unverified。