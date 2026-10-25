## 01 基本信息

- **标题**：DEEP: Extracting Latent Energetic Landscapes from Protein Structure Predictors
- **作者**：Zsofia Borbala Rozsa; Gabor Erdos
- **单位**：未提供（推测为 ELTE，基于 GitHub 组织名 erdoslab-elte）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026-10-21
- **论文类型**：方法学（Method）论文，提出新框架 + 基准评测
- **领域**：蛋白质结构预测 × 能量景观提取 × 突变稳定性预测（zero-shot）
- **关键词**：DEEP, Distogram Encoded Energetic Potential, statistical potential, protein stability, mutation effect prediction, decoy discrimination, Boltz-2, AlphaFold2
- **DOI/arXiv 号**：10.64898/2026.10.15.759389
- **代码**：https://github.com/erdoslab-elte/DEEP-Boltz
- **数据**：ProteinGym（64 个稳定性 assay）、Rosetta decoys（>180,000 个）
- **阅读日期**：2026-10-21（预印本发布日）
- **该文在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI 方法」交叉方向，具体位于「从结构预测器内部表征提取能量信息」这一新兴子领域。与直接训练稳定性预测器（如 ThermoNet、RaSP）不同，DEEP 不依赖实验稳定性数据训练，而是从结构预测器自身的 distogram 输出中提取统计势能。该工作连接了结构预测（AlphaFold2/Boltz-2）、能量景观建模（统计势能）与突变效应预测（zero-shot）三个子领域，为「结构预测器内部到底学到了什么」提供了新的探测手段。

---

## 02 一句话总结

本文提出 DEEP 框架，从蛋白质结构预测器（Boltz-2、AlphaFold2）输出的残基对距离分布（distogram）中提取有效统计势能，以模型自身的末端距离状态为内部参考（无需实验稳定性数据训练），在 64 个 ProteinGym 稳定性 assay 上达到平均 Spearman 相关 0.720（DEEP-Boltz），超越 97 个已发表的 zero-shot 方法，并在 >180,000 个 Rosetta decoys 上准确区分天然态与非天然构象。

---

## 03 研究问题

- **具体问题**：现代蛋白质结构预测器（如 AlphaFold2、Boltz-2）的内部表征在多大程度上捕获了控制蛋白质稳定性和构象偏好的能量学原理？这些能量信息能否被显式提取并用于突变稳定性预测和构象判别？
- **为什么重要**：如果结构预测器的内部表征确实编码了能量信息，那么这些模型不仅是几何预测器，还可以作为免费的「能量函数」，用于突变效应预测、蛋白质设计、构象采样等下游任务，而无需昂贵的实验数据或额外的 MD 模拟。
- **现有方法为何不足**：
  - 直接训练稳定性预测器（如基于实验数据的监督方法）需要大量实验标注，泛化受限。
  - 传统统计势能（如 Rosetta）依赖已知结构数据库的频次统计，分辨率有限。
  - 已有从 AlphaFold2 提取能量的尝试（如 ESM 类方法）多依赖 log-likelihood 或注意力权重，缺乏系统的能量学框架。
- **精确研究问题**：Can a general framework extract effective statistical potentials from predicted residue-pair distance distributions of structure predictors, without training on experimental stability data, such that the resulting potential achieves state-of-the-art zero-shot mutation stability prediction and accurate native/non-native conformational discrimination?

---

## 04 背景与发展脉络

> 注：此脉络为「经外部核验」+「本文框架」混合标注。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 传统统计势能 | Rosetta, DFIRE, GOAP | 可解释、计算快 | 依赖结构数据库频次、分辨率有限、缺乏序列上下文 | DEEP 作为「现代版统计势能」，从预测器 distogram 提取 |
| 基于进化序列的方法 | EVE, DeepSequence | 捕获共进化信号 | 需多序列比对、对单点突变敏感度有限 | DEEP 不依赖 MSA 深度，直接从结构预测器输出提取 |
| 结构预测器作为能量函数 | AlphaFold2 pLDDT/pAE, ESM-IF | 利用预训练表征 | 多为启发式打分，缺乏系统能量学框架 | DEEP 提供系统化的 distogram→势能映射框架 |
| 监督式稳定性预测 | ThermoNet, RaSP, P rot | 精度高 | 需实验数据训练、泛化受限 | DEEP-Boltz 在 zero-shot 下达到与监督方法相当的水平 |
| 零样本突变效应预测 | 97 种已发表方法（ProteinGym 基准） | 无需实验数据 | 精度参差、机制不透明 | DEEP-Boltz 在 64 个 assay 上平均 Spearman 0.720，超越全部 97 种 |

**本文主张的位置**：DEEP 填补了「结构预测器内部表征 → 显式能量函数」这一空白，提供了一种无需实验数据、无需额外训练的通用能量提取框架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 结构预测器的能量信息未被利用 | AlphaFold2/Boltz-2 输出 distogram，但仅用于几何预测 | 缺乏将距离分布映射为能量的系统框架 | Abstract: "the extent to which their internal representations capture the energetic principles... remains unclear" |
| 突变稳定性预测依赖实验数据 | 监督方法需大量实验标注，zero-shot 方法精度不足 | 实验数据稀缺、标注成本高；现有 zero-shot 方法缺乏能量学基础 | Abstract: DEEP "without training on experimental stability data" 达到与监督方法相当水平 |
| 构象判别与突变效应预测被混为一谈 | 假设「能区分天然态」即「能预测突变效应」 | 两者可能是结构表征的不同属性 | Abstract: "recognizing favorable conformations and capturing their energetic sensitivity to sequence changes are distinct properties" |
| 统计势能分辨率有限 | 传统势能基于频次统计，缺乏序列上下文 | 依赖已知结构数据库、无法泛化到新序列 | Abstract: DEEP 从预测器 distogram 提取，利用模型学到的序列-结构关系 |

---

## 06 核心思想

### 1) 表面方法

DEEP 从结构预测器（Boltz-2 或 AlphaFold2）输出的残基对距离分布（distogram）中提取有效统计势能。具体地，对每个残基对 (i, j)，预测器输出一个距离分布 P_ij(d)；DEEP 将该分布转换为能量项 E_ij(d) = -log P_ij(d)（或类似变换），并以模型自身的「末端距离状态」作为内部参考（即用预测器对天然序列的预测作为参考态），从而无需外部实验数据或已知结构数据库。

### 2) 核心洞察

- **洞察一**：结构预测器的 distogram 输出不仅是几何预测，还隐式编码了能量学信息——因为预测器必须「理解」哪些残基对倾向于靠近/远离，才能做出准确预测。
- **洞察二**：以模型自身的末端状态为参考（而非外部参考态），可以消除模型偏差，使提取的势能具有自洽性。
- **洞察三**：构象判别（区分天然态 vs 非天然态）与突变效应预测（序列变化对稳定性的影响）是结构表征的两个不同属性，DEEP 框架可以分别评估这两个属性。

### 3) 可能的普适教训 [Analysis]

- 预训练模型的中间/辅助输出（如 distogram）可能包含比主任务输出更丰富的物理信息，值得系统挖掘。
- 「自参考」策略（用模型自身输出作为基线）可以避免外部参考态的选择偏差，是一种通用的无监督校准策略。
- 一个框架的「通用性」应通过多个下游任务（突变效应 + 构象判别）来验证，而非单一基准。

---

## 07 方法总览

- **输入**：蛋白质序列（单条），可选 MSA
- **输出**：
  - 突变稳定性分数（ΔΔG 或稳定性变化排序）
  - 构象判别分数（native vs non-native）
- **模块**：
  1. **结构预测器**：Boltz-2 或 AlphaFold2，输出 distogram（残基对距离分布）
  2. **能量提取模块**：将 distogram 转换为残基对能量项（如 -log P）
  3. **参考态模块**：以模型对野生型序列的末端距离状态为内部参考
  4. **打分模块**：对突变体或候选构象计算总能量分数
- **训练**：无监督，不训练于实验稳定性数据
- **工具**：Boltz-2、AlphaFold2、ProteinGym 基准、Rosetta decoy 集
- **反馈回路**：无（前馈式提取）
- **假设**：
  - 预测器的 distogram 输出编码了有效的能量学信息
  - 模型自身的末端状态可作为有效的参考态
  - 距离分布的对数变换可近似为有效势能

**文字流程**：
1. 输入野生型序列 → 结构预测器（Boltz-2/AF2）→ 获得 distogram
2. 对每个残基对，将距离分布转换为能量项
3. 以野生型预测的末端状态为参考，计算突变体或候选构象的相对能量
4. 输出稳定性分数或构象判别分数

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|---------------------|
| 结构预测器（Boltz-2/AF2） | 生成 distogram | 提供残基对距离分布，是能量提取的原料 | 输入：序列；输出：distogram | Abstract: "extracts effective statistical potentials directly from predicted residue-pair distance distributions" | 无 distogram 则整个框架无法工作（预期） |
| 能量转换模块 | 将距离分布转换为能量项 | 距离概率 → 能量的映射是统计力学的基本关系 | 输入：distogram；输出：残基对能量 | Abstract: "using the models own terminal distance state as an internal reference" | 若移除，无法获得能量分数（预期） |
| 内部参考态模块 | 以模型末端状态为参考 | 消除模型偏差，提供自洽基线 | 输入：野生型预测；输出：参考能量 | Abstract: "using the models own terminal distance state as an internal reference without training on experimental stability data" | 若移除，需外部参考态，可能引入偏差（预期） |
| 打分/判别模块 | 计算突变效应或构象分数 | 将能量转换为可比较的分数 | 输入：能量项；输出：Spearman 相关或判别准确率 | Abstract: "achieves a mean per-assay Spearman correlation of 0.720" | 若移除，无法量化性能（预期） |

> 注：由于本文为预印本且提供的材料为摘要级别，未提供详细的消融实验数据。上述「移除后影响」均为预期效应，非实测消融结果。

---

## 09 关键公式符号

> 注：由于提供的材料仅为摘要，未包含具体公式。以下基于摘要描述推断核心公式形式，标注为 [Analysis]。

**核心公式（推断）**：

$$E_{ij}(d) = -\log P_{ij}(d)$$

- $E_{ij}(d)$：残基对 (i, j) 在距离 d 处的有效能量
- $P_{ij}(d)$：结构预测器输出的残基对 (i, j) 距离分布
- 直觉：距离概率越低，能量越高（Boltzmann 反比关系）

**参考态公式（推断）**：

$$\Delta E = E_{\text{mutant}} - E_{\text{wildtype}}$$

- $E_{\text{mutant}}$：突变体序列的总能量
- $E_{\text{wildtype}}$：野生型序列的总能量（内部参考）
- 直觉：以模型自身对野生型的预测为基线，突变体的相对能量变化即为稳定性变化

> 来源：基于摘要中 "using the models own terminal distance state as an internal reference" 和 "extracts effective statistical potentials directly from predicted residue-pair distance distributions" 的推断。具体公式细节需查阅全文 Methods 节。

---

## 10 实验设计与证据链

### 数据集与评测协议

| 项目 | 详情 |
|------|------|
| 突变效应数据集 | ProteinGym 稳定性 assay，64 个 |
| 突变效应指标 | 每个 assay 内的 Spearman 相关，取平均 |
| 对比基线 | 97 个已发表的 zero-shot 方法 |
| 构象判别数据集 | Rosetta decoys，>180,000 个 |
| 构象判别任务 | 区分天然态（native）与非天然态（non-native）构象 |
| 模型 | Boltz-2（DEEP-Boltz）、AlphaFold2（DEEP-AF2） |
| 训练 | 无监督，不训练于实验稳定性数据 |

### 实验列表

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| DEEP-Boltz 在 ProteinGym 上的突变效应预测 | DEEP 提取的势能可预测突变稳定性 | 对比 97 个 zero-shot 方法 | 平均 Spearman 0.720，超越全部 97 个方法 | DEEP 提取的势能具有 SOTA zero-shot 突变预测能力 | 不能证明 DEEP 在所有 assay 上都最优（仅平均最优） | Abstract |
| DEEP-Boltz 与监督方法对比 | DEEP 可达到监督方法水平 | 对比「最佳监督方法」 | 与最佳监督方法相当 | DEEP 无需实验数据即可达到监督水平 | 不能证明 DEEP 超越所有监督方法 | Abstract: "on level with the best performing predictors trained directly on experimental stability measurements" |
| DEEP-Boltz 在 Rosetta decoys 上的构象判别 | DEEP 可区分天然态与非天然态 | 180,000+ decoys | 准确区分 native 与 non-native | DEEP 提取的势能编码了构象偏好信息 | 不能证明 DEEP 可用于构象采样或生成 | Abstract |
| DEEP-AF2 与 DEEP-Boltz 对比 | 不同预测器的能量信息含量不同 | DEEP-AF2 vs DEEP-Boltz | AF2 构象判别与 Boltz 几乎相同，但突变效应预测显著更弱 | 构象判别与突变效应预测是结构表征的不同属性 | 不能确定 AF2 与 Boltz 差异的具体机制 | Abstract |

---

## 11 结论正确解读

- **任务范围**：DEEP 的验证限于 (1) 单点突变的稳定性效应预测（ProteinGym 基准）和 (2) 天然态 vs 非天然态的二元构象判别（Rosetta decoys）。未验证：多点突变、构象采样、构象生成、蛋白质设计。
- **oracle/真值输入**：ProteinGym 的稳定性标签来自实验测量；Rosetta decoys 的 native/non-native 标签来自 Rosetta 生成协议。DEEP 本身不接收这些标签作为训练信号。
- **端到端状态**：DEEP 是「提取器」，依赖上游结构预测器（Boltz-2/AF2）的 distogram 输出。不是端到端的能量函数，而是「预测器 + 提取器」的组合。
- **算力成本**：未提供具体算力数据。推断主要成本在结构预测器的前向传播（Boltz-2/AF2），DEEP 提取本身计算量较小。
- **历史数据依赖**：DEEP 不依赖实验稳定性数据，但依赖结构预测器的预训练（Boltz-2/AF2 的训练数据）。
- **模型依赖**：DEEP 的性能高度依赖上游预测器的质量。DEEP-AF2 与 DEEP-Boltz 的差异表明，不同预测器编码的能量信息量不同。
- **最难情形**：突变效应预测中，对预测器训练分布之外的序列/突变类型可能失效；构象判别中，对与天然态能量接近的 near-native decoys 可能区分困难。
- **群体/领域边界**：验证限于球状蛋白（ProteinGym 覆盖范围）；未验证膜蛋白、 intrinsically disordered proteins、核酸复合物等。
- **不确定性**：预印本，未经同行评审；具体方法细节（如能量转换公式、参考态定义）需查阅全文。

**有边界的复述**：DEEP 从 Boltz-2 的 distogram 中提取的势能，在 ProteinGym 的 64 个稳定性 assay 上平均 Spearman 相关为 0.720，超越 97 个已发表 zero-shot 方法，与最佳监督方法相当；在 Rosetta decoys 上可准确区分天然态与非天然态。但该结论限于单点突变稳定性预测和二元构象判别任务，且依赖上游预测器的质量。

---

## 12 作者自认局限

> 在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 摘要中未明确列出局限性。但可推断以下约束（标注为 [Analysis]）：
  - DEEP 依赖上游预测器的 distogram 质量，不同预测器（AF2 vs Boltz-2）的能量信息含量不同。
  - 验证范围限于 ProteinGym 稳定性 assay 和 Rosetta decoys，未覆盖更广泛的蛋白质类型和突变类型。
  - 预印本状态，方法细节和局限性讨论需查阅全文。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| DEEP 的「自参考」策略可能引入循环论证 | 以模型自身对野生型的预测为参考，可能只是放大了模型自身的偏差，而非提取了真实的物理能量 | 如果 DEEP 只是「模型自我一致性」的度量，而非真实能量，则其泛化性存疑 | 将 DEEP 提取的势能与实验测定的能量（如折叠自由能）直接比较，而非仅比较排序相关性 | Abstract: "using the models own terminal distance state as an internal reference" |
| 平均 Spearman 0.720 可能掩盖 assay 间的巨大差异 | 某些 assay 上可能表现极好，某些可能接近零相关 | 平均指标可能高估方法的稳健性 | 检查 64 个 assay 的 Spearman 分布（方差、最差表现） | Abstract: "mean per-assay Spearman correlation of 0.720" |
| 与「97 个 zero-shot 方法」的对比可能不公平 | 对比的 97 个方法可能来自不同时期、不同实现，且 DEEP 使用了更强的上游模型（Boltz-2） | 如果对比基线较弱，SOTA 结论可能不稳健 | 与最新最强的 zero-shot 方法（如 ESM 系列）在同一上游模型条件下对比 | Abstract: "numerically outperforming all 97 published zero-shot methods" |
| 构象判别任务可能过于简单 | 180,000 个 decoys 中，大部分可能远离天然态，区分「远距离」decoy 容易 | 如果 DEEP 只能区分「明显错误」的构象，对 near-native 判别可能无效 | 按 decoy 的 RMSD 分层报告判别准确率 | Abstract: "accurately distinguishes native-like from non-native conformations" |
| DEEP-AF2 与 DEEP-Boltz 的差异未被解释 | 为什么 AF2 的构象判别与 Boltz 相同但突变效应预测更弱？是模型架构差异还是训练数据差异？ | 理解这一差异有助于设计更好的预测器 | 系统比较 AF2 与 Boltz-2 的架构和训练数据差异，并做控制实验 | Abstract: "reveals nearly identical conformational discrimination but substantially weaker mutation-effect prediction" |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **Distogram 作为能量信息来源**：结构预测器的 distogram 输出可被重新解释为能量景观的投影。这一思路可迁移到其他输出类型（如 pLDDT、pAE、注意力权重），构建多通道能量提取框架。

2. **自参考策略**：以模型自身的「末端状态」为内部参考，避免了外部参考态（如已知结构数据库）的选择偏差。这一策略可迁移到任何需要「参考态」的势能提取任务，如蛋白质设计中的序列-结构兼容性评估。

3. **构象判别 vs 突变效应预测的解耦**：本文证明这两个任务是结构表征的不同属性。对本课题的启示：在设计评估协议时，不应假设「能区分构象」的模型必然「能预测突变效应」，需要分别评测。

4. **Zero-shot 能量提取的可行性**：无需实验数据训练即可达到监督方法水平，说明预训练结构预测器内部已编码大量能量学信息。这为「无监督能量函数」方向提供了有力证据。

5. **跨模型迁移的评估框架**：将同一 DEEP 框架应用于 Boltz-2 和 AF2，通过性能差异揭示不同模型内部表征的能量学信息含量差异。这种「同一提取器、不同上游模型」的对比设计可用于评估任何结构预测器的物理合理性。

6. **对 MD/对接研究的启示**：DEEP 提取的势能可作为 MD 模拟的初始打分函数、或作为对接构象排序的补充评分，与物理势能（如 AMBER/CHARMM）结合使用。

---

## 15 与已有知识连接

- **AlphaFold2 的 distogram 输出**：AF2 的 distogram 头输出残基对距离分布，原始论文（Jumper et al., 2021, Nature）将其用于结构模块的几何约束。DEEP 重新利用这一输出作为能量来源，与已有工作（如 AF2 的 pLDDT 作为置信度分数）形成互补。

- **统计势能传统**：DEEP 与经典统计势能（如 DFIRE, Zhou & Zhou, 2002; GOAP, Zhou & Skolnick, 2011）在思想上一致——从频次/分布中提取能量，但 DEEP 的「频次」来自预测器的内部表征而非结构数据库。

- **ProteinGym 基准**：ProteinGym（Notin et al., 2023）是突变效应预测的标准基准。DEEP-Boltz 在 64 个稳定性 assay 上的表现可与该基准中的 97 个方法直接对比。

- **Zero-shot 突变预测**：与 ESM 系列（Meier et al., 2021; Lin et al., 2023）的 log-likelihood 方法、以及基于结构的方法（如 RaSP, Blaabjerg et al., 2023）形成对比。DEEP 的独特之处在于利用 distogram 而非序列或单一结构。

- **Boltz-2**：Boltz-2（Wohlwend et al., 2024）是新一代结构预测器，DEEP 选择其作为主要上游模型，说明新一代预测器的 distogram 可能编码更丰富的能量信息。

- **[Analysis] 候选连接**：DEEP 的自参考策略与「相对能量」概念（如 MM/PBSA 中的相对结合自由能）有相似之处，可探索将 DEEP 扩展到蛋白质-配体/蛋白质-蛋白质相互作用界面。

---

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：DEEP-MD——将 DEEP 势能作为 MD 模拟的增强采样偏置
- **来源局限/观察**：DEEP 提取的势能是静态的（基于单一序列的 distogram），未利用构象系综信息；MD 模拟的增强采样需要可微分的偏置势。
- **核心假设**：DEEP 势能可作为副本交换 MD（REMD）或 metadynamics 的偏置势，加速构象采样，且比传统集体变量更「物理相关」。
- **初步方法**：将 DEEP 势能实现为可微分的 PyTorch 模块，嵌入 OpenMM 或 AMBER 的自定义偏置力；在小型蛋白（如 villin headpiece）上比较 DEEP 偏置 MD 与常规 MD 的构象采样效率。
- **验证方式**：比较 DEEP-MD 采样的构象系综与实验（NMR/晶体）构象的 RMSD 分布、以及折叠/去折叠自由能面。
- **创新状态**：unverified

### 候选 2：DEEP-Design——利用 DEEP 势能进行序列设计
- **来源局限/观察**：DEEP 提取的势能对序列变化敏感（突变效应预测），但尚未用于序列设计。
- **核心假设**：DEEP 势能可作为序列设计的可微目标函数，与结构预测器联合优化，实现「能量感知」的序列设计。
- **初步方法**：将 DEEP 势能作为 ProteinMPNN 或 ESM-IF 的额外损失项，在目标结构上迭代优化序列，使 DEEP 势能最小化。
- **验证方式**：设计序列的实验表达与稳定性测试，或与 Rosetta 设计的序列进行计算比较。
- **创新状态**：unverified

### 候选 3：DEEP-Multimer——扩展 DEEP 到蛋白质复合物界面
- **来源局限/观察**：DEEP 目前验证于单体蛋白的稳定性与构象判别，未涉及蛋白质-蛋白质相互作用。
- **核心假设**：DEEP 势能可扩展至复合物界面残基对，用于预测突变对结合亲和力的影响（ΔΔG_binding）。
- **初步方法**：将 DEEP 框架应用于 Boltz-2 的复合物 distogram 输出，提取界面残基对的能量项；在 SKEMPI 2.0 基准上评估突变对结合亲和力的预测。
- **验证方式**：与 FoldX、MM/PBSA 等结合亲和力预测方法对比。
- **创新状态**：unverified

### 候选 4：DEEP-Ensemble——从构象系综中提取能量景观
- **来源局限/观察**：DEEP 使用单一序列的 distogram，未利用多构象信息；能量景观的完整描述需要系综。
- **核心假设**：对同一序列的多个预测构象（如不同种子或不同 MSA 的 AF2 预测）分别提取 DEEP 势能，可重建更完整的能量景观。
- **初步方法**：对同一序列生成多个 AF2/Boltz-2 预测，提取每个预测的 DEEP 势能，构建能量景观的低维嵌入（如 PCA 或 UMAP），与实验构象系综比较。
- **验证方式**：在已知具有多个构象状态的蛋白（如 kinases）上验证 DEEP-Ensemble 是否捕获已知的构象平衡。
- **创新状态**：unverified

### 候选 5：DEEP 与物理势能的混合能量函数
- **来源局限/观察**：DEEP 势能来自预测器的统计学习，可能缺乏物理真实性（如范德华、静电相互作用）；物理势能（AMBER/CHARMM）计算成本高但物理可解释。
- **核心假设**：DEEP 势能与物理势能的加权组合，可同时获得统计学习的精度和物理力学的可解释性。
- **初步方法**：在 ProteinGym 上优化 DEEP 与 AMBER 势能的加权系数；在 MD 模拟中测试混合势能的稳定性。
- **验证方式**：混合势能在突变效应预测和构象采样上的表现是否优于任一单独势能。
- **创新状态**：unverified

---

> **证据与来源说明**：本 Card 基于提供的摘要文本。所有「作者主张」均标注来源为 Abstract；标注 [Analysis] 的内容为基于摘要的推断分析，非作者原话。具体方法细节（如能量转换公式、参考态定义、消融实验）需查阅全文 Methods 节，本文未提供。数值（Spearman 0.720、64 个 assay、97 个方法、180,000 decoys）均与摘要原文一致。