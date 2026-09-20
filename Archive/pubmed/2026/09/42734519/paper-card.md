## 01 基本信息

- **标题**：Biasing Conformational Sampling in AlphaFold 3 and Boltz-2 via Pair Representation Scaling
- **作者**：Suzuki, Shosuke; Amagasa, Toshiyuki
- **单位**：未提供（根据作者信息推断为日本机构，具体单位未在材料中提供）
- **期刊/平台**：Journal of Chemical Information and Modeling (JCIM)
- **年份**：2026（在线日期 2026-09-14）
- **论文类型**：方法学研究（inference-time 方法）
- **领域**：蛋白质结构预测 × 构象采样 × 深度学习
- **关键词**：AlphaFold 3, Boltz-2, conformational sampling, pair representation, inference-time bias
- **DOI/ID**：10.1021/acs.jcim.6c02094
- **代码**：https://github.com/suzuki-2001/pair-representation-scaling
- **数据**：86 个双态靶标（39 个结构域运动 + 47 个膜转运蛋白），来自 BioEmu、OC23、IOMemP 和熵引导折叠基准
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质结构预测 × 构象采样」交叉方向，提出一种无需重训练、无需辅助模型的 inference-time 方法，通过缩放 AlphaFold 3 和 Boltz-2 共享的 pair representation 来偏置构象采样。与 MSA 操作类方法（AF-Cluster、AFsample）和生成式 ensemble 模型（BioEmu）形成互补，为「如何从静态结构预测器中提取动态构象信息」提供了新的轻量级工具。

---

## 02 一句话总结

本文提出 pair representation scaling——在扩散型结构预测器（AlphaFold 3 和 Boltz-2）的 Pairformer 输入端将 latent pair representation 乘以单一标量 (1+β)——在不重训练、不改输入 MSA 的前提下，于 86 个双态靶标上显著拓宽构象系综并恢复默认推理遗漏的替代态，且该增益在训练截止日期之后发布的靶标上依然成立。

---

## 03 研究问题

- **具体问题**：深度学习结构预测器（AlphaFold 3、Boltz-2）默认返回单一主导构象，如何在不重训练、不引入辅助模型的前提下，可控地偏置其构象采样以恢复功能性替代态？
- **为什么重要**：蛋白质功能往往依赖构象转换（如膜转运蛋白的内外朝向交替、激酶的结构域开合）。若预测器只能给出单一构象，则无法用于研究构象依赖的分子识别、别构调控和药物结合机制。
- **现有方法为何不足**：
  - MSA 操作类方法（AF-Cluster、subsampling、masking）依赖输入序列的进化信号，无 MSA 时失效，且成本随 MSA 深度增长；
  - Dropout 采样注入的是无方向随机噪声，不保证向替代态偏移；
  - 专门的 ensemble 生成模型（如 BioEmu）需要额外训练，且与现有预测器架构不共享。
- **精确研究问题**：Can a single scalar multiplication of the latent pair representation at the Pairformer input bias diffusion-based structure predictors toward experimentally observed alternative conformational states, without retraining or auxiliary models?

---

## 04 背景与发展脉络

> 注：此脉络基于本文引言与参考文献构建，标注为「仅本文框架」，未经外部系统核验。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 传统构象采样 | MD、增强采样 | 物理上严格 | 计算昂贵、需系统特异性参数化 |
| 深度学习单结构预测 | AlphaFold 2 | 精度高 | 返回单一构象，不编码系综 |
| MSA 操作类构象挖掘 | AF-Cluster、subsampling、masking | 可恢复替代态 | 依赖 MSA、成本随深度增长、无 MSA 时失效 |
| Inference-time 内部表示操作 | Dropout 采样、熵引导折叠 | 不依赖 MSA | 无方向性随机噪声或需优化辅助目标 |
| 专用 ensemble 生成模型 | BioEmu | 直接生成系综 | 需额外训练、与现有预测器不共享架构 |
| **本文位置** | **Pair representation scaling** | **单一标量、无重训练、无辅助模型、跨架构可迁移** | 增益部分靶标依赖、替代态占比小、无热力学权重 |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 预测器返回单一构象 | 默认推理的系综仅覆盖一个态，替代态完全缺失 | 训练目标为静态 PDB 结构，损失函数不鼓励多模态输出 | Results 图 2：默认推理 per-state success rate 仅 0.60（AlphaFold 3） |
| MSA 操作类方法依赖输入信号 | 无 MSA 时无法运行，成本随深度增长 | 方法作用于输入而非内部表示 | Introduction：MSA-based procedures act entirely through the input alignment, so they cannot run without one |
| 现有 inference-time 方法缺乏方向性 | Dropout 注入随机噪声，不保证向替代态偏移 | 随机扰动不携带构象偏好信息 | Introduction：dropout-based sampling injects stochastic noise |
| 替代态在系综中占比小 | 即使恢复替代态，也仅占系综的一小部分（中位 13/250） | 缩放是全局调制，不针对特定残基对 | Results 图 2 与 Discussion：median of 13 of 250 models |
| 无热力学权重 | 缩放后的系综无法给出各态的相对概率 | 方法为几何层面的偏置，不涉及自由能 | Discussion：method surfaces alternative states without assigning them equilibrium populations |
| 部分靶标对 β 方向敏感 | 不同靶标需要不同符号的 β | 替代态在 pair representation 中的编码方向因靶标而异 | Results：β 值因靶标而异，无单调依赖 |

---

## 06 核心思想

**1) 表面方法**：
在扩散型结构预测器（AlphaFold 3、Boltz-2）的推理阶段，将 Pairformer 输入端的 latent pair representation z_ij 乘以 (1+β)，其中 β 在固定范围内扫描（±0.15 至 ±0.75）。这是一个纯 inference-time 操作，不涉及重训练、不修改输入 MSA、不引入辅助模型。

**2) 核心洞察**：
- Pair representation 是进化约束（MSA）与几何约束（结构模块）之间的「瓶颈」——它聚合了 coevolutionary 信号并传递给结构生成模块，因此是干预构象采样的天然接口。
- 缩放 pair representation 的整体幅度等价于调制「残基-残基耦合场」的强度，从而改变结构模块对不同构象假设的偏好，而非注入无方向噪声。
- 该操作在 AlphaFold 3 和 Boltz-2 上无需修改即可迁移，说明 pair representation 的「幅度-构象偏好」关系是扩散型预测器的共享特性。
- 缩放的效果是**有方向的**：负 β 倾向于将系综推向替代态，且这种偏移在 pair representation 的 distogram 投影中可被直接观测到，说明模型在训练中已将替代态信息编码进 pair representation。

**3) 可能的普适教训 [Analysis]**：
- 深度学习模型的内部表示（latent representation）可能比输入（MSA）或输出（坐标）更适合作为干预接口——输入操作受数据可用性限制，输出操作受解码器约束，而内部表示操作可以「借用」模型已编码但未显式输出的信息。
- 单一标量缩放作为一种「全局调制」，其成功暗示：构象偏好可能以「整体幅度」而非「特定模式」的方式编码在 pair representation 中。这对理解扩散型预测器的表示学习机制有启发。
- 该方法与 MSA 操作类方法正交且可组合，提示「输入级干预 + 表示级干预」可能是挖掘预测器构象能力的通用策略。

---

## 07 方法总览

- **输入**：氨基酸序列（+ 可选 MSA，来自 AlphaFold 3 服务器）；靶标定义在 construct 级别，序列取自 UniProt，参考结构取自 PDB。
- **输出**：每个靶标在 β 扫描范围（±0.15, ±0.30, ±0.45, ±0.60, ±0.75）下的构象系综（每靶标 250 个模型），以 TM-score 和 Cα RMSD 相对于两个参考态评估。
- **核心模块**：
  1. **Pair representation scaling 模块**：在 Pairformer 输入端对 z_ij 乘以 (1+β)，每个 recycling iteration 均应用。
  2. **变体模块**（用于消融）：(a) 在 MSA 模块的 outer-product mean 之前缩放；(b) 在 Pairformer 之后缩放；(c) contact-localized scaling（仅缩放两个参考态间 Cα 距离变化 >4Å 的残基对）；(d) Gaussian noise control（方差匹配缩放的幅度变化）。
  3. **评估模块**：per-state success rate（系综内存在模型在 2Å Cα RMSD 内匹配某参考态）、worst-case minimum RMSD（两个参考态中较难恢复者的最小 RMSD）、fill ratio（系综沿两态间路径的覆盖比例）。
- **训练**：无（纯 inference-time 方法）。
- **工具**：AlphaFold 3 v3.0.1、Boltz-2 v2.2.1、BioEmu v1.3.1（作为参考生成器）；US-align 计算 TM-score/RMSD；ChimeraX 渲染；NVIDIA RTX A6000 和 H100 GPU。
- **文字流程**：序列 → 构建 MSA（或移除）→ 前向传播至 pair representation → 在 Pairformer 输入端应用 (1+β) 缩放 → 完成扩散采样 → 对每个 β 生成系综 → 与两个参考态比对 → 计算三项指标 → 与基线（默认推理、MSA 操作、dropout、MD-conditioned、BioEmu）比较。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Pair representation scaling（默认位置：Pairformer 输入端） | 以单一标量调制 pair representation 幅度 | 改变残基-残基耦合强度，偏置构象采样方向 | 输入：z_ij ∈ R^{N×N×d_P}；输出：(1+β)z_ij | Results 图 2：AlphaFold 3 per-state success rate 0.60→0.73；worst-case minimum RMSD 显著下降 | 移除后恢复默认推理，替代态无法恢复（实测：默认推理遗漏替代态） |
| 位置变体：MSA 模块 outer-product mean 之前 | 在 pair representation 组装前缩放 | 测试干预位置是否关键 | 输入：MSA 模块前的 pair 特征；输出：缩放后的特征 | Results 图 2F：此位置缩放不改善恢复，per-state success rate 保持默认水平 | 预期：outer-product mean 将缩放吸收，干预失效（实测确认） |
| 位置变体：Pairformer 之后 | 直接缩放结构模块的 conditioning | 测试是否需经 Pairformer 重处理 | 输入：Pairformer 输出的 pair representation；输出：缩放后的表示 | Results 图 2F：此位置缩放反而收窄系综，fill ratio 减半 | 预期：未经 Pairformer 重处理的静态缩放破坏结构模块的 conditioning（实测确认） |
| Contact-localized scaling | 仅缩放两态间移动的残基对 | 测试效果是否依赖空间定位 | 输入：z_ij + 二值掩码 M_ij；输出：z_ij(1+βM_ij) | Results 图 2E：不优于均匀缩放，未复现均匀缩放的增益 | 预期：效果来自全局幅度而非特定残基对（实测确认） |
| Gaussian noise control | 添加方差匹配的加性噪声 | 区分结构化调制与随机扰动 | 输入：z_ij；输出：z_ij + ε_ij，ε~N(0, σ²) | Results 图 2C,D：AlphaFold 3 中噪声导致结构崩溃，无恢复 | 预期：随机扰动不携带方向信息，无法偏置采样（实测确认） |
| Distogram bimodality 分析 | 检测 pair representation 中是否已编码双态分布 | 解释缩放为何能恢复替代态 | 输入：distogram 概率（64 bins，2-22Å）；输出：双峰分类 | Results 图 3A,B：默认推理下约 1/10 的 change-contact distograms 已双峰，且峰位对齐参考态距离 | 预期：模型在训练中已编码双态信息，缩放仅重加权（实测确认） |
| Denoising trajectory 分析 | 追踪缩放如何影响扩散采样路径 | 确认效应在扩散模块中的实现方式 | 输入：每步 denoised structure estimate；输出：状态归属（dominant/alternative） | Results 图 4：默认轨迹全程停留在 dominant 侧，缩放后轨迹在 backbone 解析后转向 alternative 侧 | 预期：缩放改变 conditioning，使扩散模块在结构解析阶段偏向替代态（实测确认） |

---

## 09 关键公式符号

**1. Pair representation scaling（均匀缩放）**：
z_ij^(scaled) = (1 + β) · z_ij

- z_ij ∈ R^{d_P}：残基对 (i, j) 的 pair embedding
- β：缩放标量，扫描范围 {±0.15, ±0.30, ±0.45, ±0.60, ±0.75}
- β = 0 恢复默认推理

**2. Contact-localized scaling**：
z_ij^(scaled) = z_ij · (1 + β · M_ij)

- M_ij ∈ {0, 1}：二值掩码，M_ij = 1 当且仅当残基对 (i, j) 在两个参考态间的 Cα–Cα 距离变化 > 4Å

**3. Gaussian noise control**：
z_ij^(noisy) = z_ij + ε_ij，ε_ij ~ N(0, σ²)

- σ² = |(1+β)² − 1| · Var(z)，其中 Var(z) 按 feature channel 估计
- 该方差匹配均匀缩放引起的元素方差变化，但丢弃方向信息

**4. Fill ratio**：
FR = N_occ / N

- N = 100：两参考态间路径 AB 的等分数
- N_occ：至少含一个模型的 bin 数
- 模型位置：x_m = (TM_1^m, TM_2^m)，投影到 AB 上的分数位置 t_m = ((x_m − A)·(B − A)) / ‖B − A‖² ∈ [0,1]
- A = (1, τ)，B = (τ, 1)，τ 为两参考态间的 TM-score

**5. Best-minimum TM-score**：
min(TM_ref1^max, TM_ref2^max)

- TM_ref1^max：系综中相对于参考态 1 的最高 TM-score

---

## 10 实验设计与证据链

**数据集**：
- 86 个双态靶标：39 个结构域运动蛋白（22 个来自 BioEmu + 17 个来自 OC23/AFsample2）+ 47 个膜转运蛋白（15 个来自 IOMemP + 32 个来自熵引导折叠基准，去除 5 个重复）
- 85 个独特蛋白（脂质 II 翻转酶 MurJ 贡献两个靶标，各用不同参考态对）
- 序列来自 UniProt，参考结构来自 PDB，construct 级别定义
- 训练截止分组：AlphaFold 3 截止 2021-09-30，Boltz-2 截止 2023-06-01，BioEmu 截止 2023-11-23；after-cutoff 组：AlphaFold 3 23 个靶标，Boltz-2 13 个靶标

**基线**：
- 默认推理（β = 0）
- MSA subsampling（随机保留固定数量序列）
- MSA random masking（40% 列掩码，AFsample3 最优比例）
- MSA clustering（AF-Cluster 方法，k = 10）
- Inference-time dropout（rate 0.25，AFsample 方法）
- Boltz-2 MD-conditioned mode
- BioEmu（ensemble 生成模型）

**评测协议**：
- 每靶标 250 个模型（消融实验 150 个）
- 指标：per-state success rate（2Å Cα RMSD 阈值）、worst-case minimum RMSD、fill ratio
- 统计检验：配对 Wilcoxon 符号秩检验，Holm 校正；二值指标用 McNair 精确检验；效应量 95% CI 来自 10,000 次配对 bootstrap

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| 主基准：β 扫描 vs 默认推理 | 缩放拓宽构象系综并恢复替代态 | 86 靶标，β ∈ {±0.15,...,±0.75}，250 模型/靶标 | AlphaFold 3：per-state success rate 0.60→0.73；worst-case minimum RMSD 显著下降；fill ratio 上升（转运蛋白 >2 倍） | 缩放有效恢复替代态，且对 harder state 改善最大 | 未声称对所有靶标均有效；部分靶标无 β 值可恢复替代态 | Results 图 2 |
| Boltz-2 主基准 | 同一操作跨架构有效 | 同上 | 三指标均改善，但效应小于 AlphaFold 3；fill ratio 增益达显著（p < 0.001 截止前，p = 0.04 截止后） | 方法可迁移至 Boltz-2 | 效应量较小，per-state 增益未达显著 | Results 图 2 |
| After-cutoff 分组 | 增益不依赖训练时见过替代态 | 23（AF3）/13（Boltz-2）个截止后靶标 | AlphaFold 3 worst-case minimum RMSD 改善 1.18Å（95% CI 0.47–2.03Å） | 替代态恢复非记忆效应 | 样本量小，未做多重校正 | Results 图 2 |
| 与 MSA 基线比较 | 缩放优于或等价于输入级操作 | 同 86 靶标，各基线 250 模型 | 缩放匹配最强 MSA 基线（clustering）的恢复率，且计算成本更低 | 内部表示操作可替代输入级操作 | 未系统比较所有 β 值与 MSA 基线的组合 | Results 图 2 |
| 与 BioEmu 比较 | 缩放接近专用 ensemble 模型 | BioEmu 默认设置，同靶标 | BioEmu fill ratio 最高（0.43 vs AF3 缩放 0.29），但 AF3 缩放恢复更多替代态 | 缩放是低成本替代方案，非完全替代 | BioEmu 在系综覆盖上仍领先 | Results 图 2 |
| 位置消融（38 靶标子集） | 缩放位置关键 | 缩放前移至 MSA 模块前 / 后移至 Pairformer 后 | 前移：无改善；后移：fill ratio 减半 | 必须作用于 Pairformer 输入端 | 未测试其他中间位置 | Results 图 2F |
| Contact-localized vs 均匀缩放 | 效果依赖全局幅度而非特定残基对 | 38 靶标，掩码仅覆盖移动残基对 | 局部缩放不优于默认推理 | 全局调制是必要机制 | 未测试不同掩码阈值 | Results 图 2E |
| Gaussian noise control | 效果非随机扰动 | 方差匹配，同 β 网格 | AlphaFold 3：结构崩溃，无恢复；Boltz-2：部分容忍 | 缩放是有方向的结构化调制 | 未测试其他噪声类型 | Results 图 2C,D |
| Distogram bimodality 分析 | 替代态信息已编码在 pair representation 中 | 86 靶标，11 β 值，change-contact pairs | 默认推理下约 1/10 distograms 已双峰且峰位对齐参考态；缩放后双峰比例上升 | 缩放重加权已存在的双峰分布 | 未追踪双峰比例随 β 的完整变化曲线 | Results 图 3A,B |
| Distogram 位移 vs 结构位移相关性 | distogram 变化有方向性 | 逐靶标相关分析 | 正相关：distogram 向替代态位移与结构向替代态位移一致 | 缩放方向性地调制距离预测 | 相关性中等，未报告具体 r 值分布 | Results 图 3E–G |
| Denoising trajectory 分析 | 缩放影响扩散采样路径 | 2 靶标，50 轨迹/条件，200 步 | 默认轨迹全程 dominant 侧；缩放后 40/50（FlgA）和 50/50（Q 蛋白）轨迹转向 alternative 侧 | 缩放改变 conditioning 使扩散模块偏向替代态 | 仅 2 个靶标，未推广 | Results 图 4 |
| 无 MSA 推理 | 缩放不依赖 coevolutionary 输入 | 移除 MSA，86 靶标 | 覆盖 <0.10，但缩放仍改善 worst-case minimum RMSD | 缩放效果独立于 MSA 信号 | 无 MSA 时整体精度过低，实际用途有限 | Results 图 5 |

---

## 11 结论正确解读

- **任务范围**：本文方法仅适用于扩散型结构预测器（AlphaFold 3、Boltz-2），不适用于回归型预测器（如 AlphaFold 2 的 structure module）。方法作用于 pair representation 的幅度，而非坐标或序列。
- **oracle/真值输入**：contact-localized scaling 变体使用了参考态结构（oracle 信息），但主方法（均匀缩放）不依赖任何参考态信息。评估本身需要两个参考态结构作为真值。
- **端到端状态**：方法为纯推理阶段操作，不涉及训练。但 β 的最优值因靶标而异，实际应用中若无参考态，需通过其他方式（如 distogram 熵、系综多样性）选择 β。
- **算力成本**：方法本身几乎零额外成本（一次标量乘法），但 β 扫描需要多次前向传播（11 个 β 值 × 每靶标 250 模型）。
- **历史数据依赖**：方法依赖模型在训练中已编码的构象信息。对训练集中无类似构象变化的蛋白，方法可能无效。
- **最难情形**：Boltz-2 上效应较弱（per-state 增益未达显著）；无 MSA 时整体精度过低；部分靶标在任何 β 下均无法恢复替代态。
- **群体/领域边界**：仅在双态蛋白（结构域运动 + 膜转运蛋白）上验证；未测试多态系统、 intrinsically disordered regions、复合物、配体诱导构象变化。
- **不确定性**：方法不提供构象间的相对概率或热力学权重；β 与构象偏置强度之间无单调关系；替代态在系综中占比小（中位 13/250）。
- **有边界的复述**：在 86 个双态蛋白靶标上，对扩散型结构预测器的 pair representation 施加单一标量缩放，可以在不重训练、不依赖 MSA 的情况下，将构象系综从默认的单一主导态拓宽至包含实验观测的替代态，且该效果在训练截止后发布的靶标上依然存在；但该效果是部分靶标、部分 β 值下的现象，而非对所有蛋白的普适保证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 替代态在系综中占比小 | 恢复的替代态仅占系综的一小部分（中位 13/250 模型） | 未明确提及 | Discussion 末段 |
| 无热力学权重 | 方法无法为系综中的构象分配相对概率或平衡常数 | 将方法与物理采样或热力学重加权结合 | Discussion 末段 |
| 部分靶标无效 | 部分靶标在任何 β 值下均无法恢复替代态 | 未明确提及 | Discussion 末段 |
| β 方向因靶标而异 | 不同靶标需要不同符号的 β，无统一规则 | 未明确提及 | Results 图 2 与 Discussion |
| 无 MSA 时精度过低 | 移除 MSA 后覆盖率 <0.10，实际用途有限 | 未明确提及 | Results 图 5 |
| 基准限于双态蛋白 | 未测试多态系统、IDR、复合物、配体诱导变化 | 扩展到更广泛的构象变化类型 | Discussion 末段 |
| 消融子集较小 | 位置消融和 contact-localized 实验仅用 38 个靶标 | 未明确提及 | Methods 节 Ablation Subset |
| 训练截止分组非严格 | after-cutoff 分组仅按参考结构释放日期，同源蛋白可能已在训练集中 | 以序列或结构相似性做更强控制 | Discussion 末段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| β 最优值因靶标而异且无选择规则 | 方法在无参考态的实际应用中缺乏可操作性；β 扫描本质上是隐式地利用参考态信息做模型选择 | 若 β 无法先验选择，方法的实用性受限 | 测试无参考态下的 β 选择策略（如基于 distogram 熵、系综多样性、自洽性） | Results 图 2 与 Discussion：helpful direction of β is target-specific |
| 替代态恢复可能源于模型对训练集构象的「记忆」而非泛化 | after-cutoff 分组仅按释放日期，同源蛋白或相似折叠可能在训练集中 | 决定方法是否真正发现新构象 | 用序列/结构相似性聚类做更严格的留出测试；测试人工设计的非天然构象 | Discussion 末段作者自认 |
| Gaussian noise control 在 AlphaFold 3 中导致结构崩溃，但 Boltz-2 中可容忍 | 两模型对 pair representation 扰动的鲁棒性差异可能源于架构或训练差异，而非缩放的特殊性 | 若 Boltz-2 对任意扰动都鲁棒，则其缩放增益可能部分来自「扰动容忍」而非「方向性调制」 | 在 Boltz-2 中测试更大方差噪声、其他结构化扰动（如旋转、裁剪） | Results 图 2C,D |
| Distogram 双峰分析仅覆盖 change-contact pairs（Cβ 距离变化 >4Å） | 该选择可能高估双峰比例；全残基对的 distogram 行为未知 | 影响对「模型已编码双态信息」这一解释的强度 | 对全残基对重复双峰分析；比较 change-contact 与非 change-contact pairs 的双峰率 | Methods 节 Distogram Bimodality Analysis |
| 与 MSA 基线比较未报告计算成本细节 | MSA clustering 需要额外聚类步骤，但缩放需要 11 次前向传播；两者成本比较不完整 | 影响「低成本」claim 的量化 | 报告各方法的端到端 wall-clock 时间和 GPU 小时数 | Results 图 2 与 Methods 节 Baselines |
| 与 BioEmu 比较中 BioEmu 的 fill ratio 更高 | 作者将 BioEmu 定位为「参考生成器」而非直接基线，但读者可能期待更系统的比较 | 影响对方法相对优势的判断 | 在相同靶标和评估协议下，系统比较系综质量（如 RMSD 分布、态间转换） | Results 图 2 |
| 消融实验仅 38 靶标且未报告 β 扫描的完整网格 | 位置消融的结论可能受靶标选择影响 | 影响对「Pairformer 输入端是唯一有效位置」这一结论的强度 | 在全部 86 靶标上重复位置消融；报告每个位置的完整 β 扫描结果 | Methods 节 Ablation Subset |
| 序列-only 实验中「覆盖率 <0.10」的绝对值极低 | 可能反映模型在无 MSA 时整体失效，而非缩放的特异性效果 | 影响对「缩放不依赖 coevolutionary 信号」这一 claim 的解释 | 比较无 MSA 时默认推理与缩放的绝对精度；测试单序列预测的其他增强策略 | Results 图 5 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

**可迁移概念**：

1. **内部表示作为干预接口**：与其修改输入（MSA）或输出（坐标），不如在 latent representation 层面施加干预。Pair representation 是进化信息与几何信息汇聚的瓶颈，缩放其幅度即可偏置构象采样。→ 可迁移到其他扩散型结构预测器（如 RFdiffusion、Chroma）或 latent diffusion 模型。

2. **全局标量 vs 局部模式**：单一标量缩放（全局调制）优于 contact-localized 缩放（局部模式），说明构象偏好在 pair representation 中以整体幅度编码。→ 对理解扩散模型表示学习机制有启发；在设计干预策略时优先考虑全局操作。

3. **「已编码但未输出」的信息**：模型在训练中已将替代态信息编码进 pair representation（distogram 双峰），只是默认解码路径不暴露它。→ 对任何「单输出」预测器，可尝试通过内部表示操作挖掘未显式输出的信息。

4. **跨架构可迁移性**：同一操作无需修改即可应用于 AlphaFold 3 和 Boltz-2，说明 pair representation 的「幅度-构象偏好」关系是扩散型预测器的共享特性。→ 方法可能迁移到未来基于 pair representation 的新架构。

5. **与 MSA 操作正交且可组合**：缩放与 MSA subsampling 组合在 Boltz-2 上恢复更难的态，说明输入级干预与表示级干预可叠加。→ 设计多层级干预策略时，输入与表示操作可并行使用。

**可迁移方法**：

1. **Gaussian noise control 的校准方式**：将噪声方差设为 |(1+β)²−1|·Var(z)，使噪声与缩放具有相同的二阶矩，从而分离「幅度变化」与「方向性调制」的效应。→ 任何表示扰动实验都可用此校准区分随机与结构化效应。

2. **Fill ratio 评估协议**：将系综中的每个模型投影到两参考态间的 TM-score 空间，统计覆盖路径的 bin 比例。→ 可迁移到任何双态构象采样的评估，比单一 RMSD 阈值更全面地刻画系综覆盖。

3. **After-cutoff 分组设计**：按参考结构释放日期相对训练截止分组，隔离「记忆效应」与「泛化能力」。→ 任何评估预测器构象能力的研究都可采用此设计。

4. **Denoising trajectory 分析**：记录扩散采样每一步的 denoised estimate 并追踪其状态归属，定位干预效应在采样时间轴上的出现时机。→ 可迁移到其他扩散模型的可解释性分析。

5. **位置消融协议**：在同一干预操作下系统改变作用位置（MSA 模块前 / Pairformer 输入 / Pairformer 输出），用 Cochran's Q 检验位置间差异。→ 任何内部表示干预研究都可用此协议定位有效作用点。

**对课题方向的启示**：

- 对「构象采样」研究：本文提供了一种零成本、无需重训练的系综拓宽手段，可作为 MD 或增强采样的初筛工具，或与 MSA 操作类方法组合。
- 对「构象生成」研究：pair representation 的幅度可作为可控生成的条件变量，类似 CFG（classifier-free guidance）中的 guidance scale。
- 对「结构预测 × 物理模拟」交叉：缩放后的系综可作为 MD 模拟的初始构象集，或与物理能量函数结合做重加权。
- 对「序列设计」：如果 pair representation 的幅度控制构象偏好，则可通过设计序列来内源性地调节这一幅度，实现「序列编码构象多样性」。