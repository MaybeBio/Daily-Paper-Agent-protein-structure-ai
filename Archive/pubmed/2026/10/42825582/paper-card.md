## 01 基本信息

- **标题**：Assessing sequence reversal effects on coiled-coil stability using AI-based structure prediction and enhanced sampling atomistic simulations
- **作者**：Arnittali, Maria; Markopoulou, Elena; Harmandaris, Vagelis; Rissanou, Anastassia N
- **单位**：未提供（根据作者姓名及期刊推测为希腊研究机构，具体单位未在摘要中提供）
- **期刊/预印本平台**：Physical Chemistry Chemical Physics (PCCP)
- **年份**：2026
- **论文类型**：研究论文（Research Article）
- **领域**：蛋白质结构预测 × 增强采样分子动力学模拟 × 卷曲螺旋（coiled-coil）稳定性
- **关键词**：coiled-coil, sequence reversal, ColabFold, molecular dynamics, well-tempered metadynamics, free energy surface, wtRop, rRop
- **DOI/arXiv 号**：10.1039/d6cp01691j
- **代码**：未提供
- **数据**：未提供
- **阅读日期**：2026-04-16（基于当前日期推断）
- **在该方向中的位置**：本文处于「蛋白质结构相关计算研究 × AI/物理模拟」交叉点，具体为：利用 AI 结构预测（ColabFold）生成未知序列的初始构象，再以经典 MD 和 well-tempered metadynamics 增强采样评估序列反转对 coiled-coil 热力学稳定性的影响。该方法论可迁移至其他蛋白质序列设计/突变稳定性评估任务。

---

## 02 一句话总结

本文通过 ColabFold 预测序列反转的 rRop 蛋白初始结构，结合经典 MD 和 well-tempered metadynamics 增强采样，计算四维自由能面，发现序列反转后的 rRop 两种取向（平行/反平行）均偏离天然反平行取向，其中反平行变体结构不稳定性最显著，而平行变体与野生型 wtRop 构象相似性更高。

---

## 03 研究问题

- **具体问题**：序列反转（sequence reversal/inversion）如何影响 coiled-coil 蛋白 wtRop 的结构完整性和热力学稳定性？特别是，反转后的 rRop 序列在平行与反平行两种单体取向下的自由能景观有何差异？
- **为什么重要**：Coiled-coil 是广泛存在的蛋白质结构基序，参与多种生物学功能。理解序列方向性（sequence directionality）对折叠稳定性的影响，对蛋白质设计、序列-结构关系理解及从头设计 coiled-coil 具有直接意义。序列反转是一种极端的序列扰动，能揭示序列与拓扑结构之间的深层耦合关系。
- **现有方法为何不足**：实验方法（如圆二色光谱、突变分析）难以系统扫描序列反转带来的构象变化；传统同源建模无法处理未知序列（rRop 无实验结构）；单一 MD 模拟受限于采样时间尺度，难以跨越自由能垒。
- **精确研究问题**：Can AI-based structure prediction combined with enhanced sampling atomistic simulations quantitatively characterize the free energy landscape differences between parallel and antiparallel orientations of a sequence-reversed coiled-coil protein, and determine which orientation retains greater structural similarity to the wild-type?

---

## 04 背景与发展脉络

> 注：此脉络为「仅本文框架」——基于摘要中可推断的信息构建，未经外部文献核验。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 实验结构解析 | X-ray crystallography, NMR | 高分辨率、真实构象 | 耗时、不适用于所有序列 | 未使用 |
| 同源建模 | MODELLER, SWISS-MODEL | 快速、基于模板 | 对无同源模板的序列失效 | rRop 无模板，故不适用 |
| AI 结构预测 | AlphaFold2, ColabFold | 高精度、无需模板 | 预测单一静态结构，不提供热力学信息 | 用于生成 rRop 初始模型 |
| 经典 MD | GROMACS, AMBER | 原子级动态信息 | 采样时间尺度有限 | 用于平衡和初步构象采样 |
| 增强采样 | Metadynamics, well-tempered metadynamics | 加速稀有事件采样、计算自由能面 | 需选择合适 collective variables | 用于计算四维自由能面 |
| **本文组合** | ColabFold + MD + WT-MetaD | 结合 AI 预测与热力学计算 | 依赖 CV 选择和力场精度 | **本文核心贡献** |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 未知序列无实验结构 | rRop 序列反转后无 PDB 结构可用 | 序列反转改变了氨基酸顺序，无法直接使用 wtRop 的晶体结构 | 摘要：AI-driven structure prediction (ColabFold) to generate initial models for the unknown rRop sequence |
| 单一静态结构不足以评估稳定性 | 仅靠结构预测无法判断热力学稳定性 | 结构预测提供静态快照，不包含自由能信息 | 摘要：These models were subjected to classical molecular dynamics simulations and well-tempered metadynamics |
| 构象采样不足 | 常规 MD 难以跨越自由能垒 | 卷曲螺旋解折叠/重折叠涉及稀有事件 | 摘要：enhanced sampling techniques allowed for the calculation of the free energy surface |
| 序列反转导致取向不确定性 | ColabFold 预测出平行和反平行两种单体取向 | 序列反转可能改变 coiled-coil 的拓扑偏好 | 摘要：yielded both parallel and antiparallel monomeric orientations |
| 多维度构象变化难以量化 | 需要同时追踪角度、距离、螺旋度、扭转角 | 单一 CV 不足以描述 coiled-coil 的构象变化 | 摘要：four collective variables: (i) angle, (ii) distance, (iii) helicity, (iv) torsion angle similarity |

---

## 06 核心思想

### 1) 表面方法
- 用 ColabFold 预测 rRop 的初始结构（平行/反平行两种取向）
- 对 wtRop 和 rRop 两种取向分别进行经典 MD 平衡
- 使用 well-tempered metadynamics 沿四个 CV 进行增强采样
- 构建四维自由能面，比较三种体系的稳定性差异

### 2) 核心洞察
- **AI 预测 + 增强采样互补**：ColabFold 提供合理的初始构象（解决"从哪开始"的问题），而 WT-MetaD 提供热力学信息（解决"有多稳定"的问题）。两者结合弥补了各自短板。
- **序列反转改变拓扑偏好**：rRop 两种取向均偏离天然反平行取向，稳定在中间角度——说明序列方向性对 coiled-coil 的拓扑选择有决定性影响。
- **反平行变体更不稳定**：反平行 rRop 表现出更大的单体分离、更明显的二级结构丢失、氢键网络破坏、溶剂可及表面积增加、疏水核心无法维持——这些多维度证据共同指向反平行取向的结构不稳定性。

### 3) 可能的普适教训 [Analysis]
- 对于序列设计/突变稳定性评估任务，单一结构预测工具（如 AlphaFold/ColabFold）不足以判断稳定性，必须结合动力学/热力学方法。
- 序列反转可作为"压力测试"来揭示序列-结构-稳定性之间的耦合关系，该方法可推广至其他 coiled-coil 或重复序列蛋白。
- 多 CV 的自由能面构建比单一 CV 更能全面刻画构象变化，尤其对于具有多个自由度的大尺度构象重排。

---

## 07 方法总览

**输入**：
- wtRop 序列（已知，天然序列）
- rRop 序列（wtRop 的反转序列，未知结构）

**输出**：
- 三种体系（wtRop、平行 rRop、反平行 rRop）的四维自由能面
- 各体系的稳定性比较（结构完整性、螺旋度、氢键网络、疏水核心等）

**模块**：
1. **结构预测模块**：ColabFold 对 rRop 进行结构预测，生成平行和反平行两种单体取向的初始模型
2. **MD 平衡模块**：经典分子动力学模拟对三种体系进行平衡
3. **增强采样模块**：well-tempered metadynamics 沿四个 CV 进行采样
4. **自由能分析模块**：从 metadynamics 轨迹重建四维自由能面
5. **结构分析模块**：氢键网络、溶剂可及表面积、疏水核心、螺旋度等结构指标分析

**训练**：不适用（无神经网络训练，ColabFold 为预训练模型）

**工具**：ColabFold（AI 结构预测）、经典 MD 模拟器（推测为 GROMACS/AMBER，摘要未指明）、PLUMED 或类似增强采样插件（推测，摘要未指明）

**假设**：
- ColabFold 预测的两种取向是 rRop 可能的天然构象
- 四个 CV 足以描述 coiled-coil 的关键构象变化
- 力场参数对 wtRop 和 rRop 的适用性一致

**文字流程**：
```
wtRop 序列 → 已知结构（PDB）
rRop 序列 → ColabFold 预测 → 平行取向模型 + 反平行取向模型
三种体系 → 经典 MD 平衡 → well-tempered metadynamics（4 CVs）→ 四维自由能面 → 稳定性比较
```

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| ColabFold 结构预测 | 为 rRop 生成初始结构模型 | rRop 无实验结构，MD 需要合理起点 | 输入：rRop 序列；输出：平行/反平行两种取向的初始构象 | 摘要：AI-driven structure prediction (ColabFold) to generate initial models | 预期影响：无初始结构则 MD 无法启动；若仅用单一取向可能遗漏重要构象态 [预期效应] |
| 经典 MD 平衡 | 对预测结构进行溶剂化平衡和弛豫 | 消除预测结构中的不合理接触，使体系达到物理合理状态 | 输入：ColabFold 预测结构；输出：平衡后的构象系综 | 摘要：subjected to classical molecular dynamics simulations | 预期影响：跳过平衡可能导致后续 metadynamics 从非物理构象出发 [预期效应] |
| Well-tempered metadynamics | 沿四个 CV 加速采样，计算自由能面 | 常规 MD 无法在有限时间内跨越 coiled-coil 构象重排的能垒 | 输入：平衡后的构象；输出：四维自由能面 | 摘要：enhanced sampling techniques allowed for the calculation of the free energy surface | 预期影响：移除后仅能获得局部构象采样，无法比较不同取向的全局稳定性 [预期效应] |
| 四维 CV 体系 | 定义角度、距离、螺旋度、扭转角相似性四个反应坐标 | 单一 CV 不足以描述 coiled-coil 的多维度构象变化 | 输入：MD 轨迹坐标；输出：CV 值随时间变化 | 摘要：four collective variables: (i) angle, (ii) distance, (iii) helicity, (iv) torsion angle similarity | 预期影响：CV 选择不当会导致自由能面投影不完整或误导 [预期效应] |
| 结构完整性分析 | 评估氢键网络、溶剂可及表面积、疏水核心 | 从多维度验证结构稳定性结论 | 输入：MD 轨迹；输出：各结构指标 | 摘要：disrupted hydrogen bond network, increased solvent-accessible surface area, failure to maintain a robust hydrophobic core | 预期影响：移除后仅能依赖自由能面，缺乏分子层面的机制解释 [预期效应] |

---

## 09 关键公式符号

> 摘要中未提供具体公式。以下为 well-tempered metadynamics 的标准公式，作为方法背景补充，非原文直接引用。

**Well-tempered metadynamics 偏置势**（标准形式，非原文公式）：

$$V(s, t) = \sum_{t' < t} \omega_0 \exp\left(-\frac{V(s(t'), t')}{k_B \Delta T}\right) \exp\left(-\frac{|s - s(t')|^2}{2\sigma^2}\right)$$

- $V(s, t)$：时刻 $t$ 在 collective variable 空间位置 $s$ 处的偏置势
- $\omega_0$：初始偏置沉积速率
- $k_B$：玻尔兹曼常数
- $\Delta T$：well-tempered 参数（有效温度增量）
- $\sigma$：高斯核宽度
- $s$：collective variable 向量（本文中为四维：角度、距离、螺旋度、扭转角相似性）

**自由能重建**（标准关系）：

$$F(s) = -\lim_{t \to \infty} V(s, t) \cdot \frac{T + \Delta T}{\Delta T}$$

- $F(s)$：沿 CV 的自由能面
- $T$：模拟温度

> 注：以上公式为 well-tempered metadynamics 的标准数学形式，本文摘要未给出具体参数值或修改版本。具体参数（$\omega_0$, $\Delta T$, $\sigma$ 等）未提供。

---

## 10 实验设计与证据链

**数据集/体系**：
- wtRop：野生型 Rop 蛋白（coiled-coil 基序，已知结构）
- rRop：wtRop 序列反转后的变体
- 平行 rRop：ColabFold 预测的平行单体取向
- 反平行 rRop：ColabFold 预测的反平行单体取向

**规模**：3 个体系（wtRop、平行 rRop、反平行 rRop）

**指标**：
- 四维自由能面（角度、距离、螺旋度、扭转角相似性）
- 结构完整性指标：氢键网络、溶剂可及表面积（SASA）、疏水核心维持、α-螺旋度

**基线**：wtRop 作为天然/野生型参照

**骨干/仪器**：未提供（推测为 GROMACS/AMBER + PLUMED，摘要未指明）

**oracle 输入**：wtRop 的已知实验结构（作为 MD 起点和比较基准）

**评测协议**：比较三种体系的自由能面特征和结构指标

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| ColabFold 预测 rRop 结构 | AI 能预测序列反转蛋白的合理构象 | rRop 序列输入 ColabFold | 产生平行和反平行两种单体取向 | AI 结构预测可处理未知序列并给出多种可能拓扑 | 预测结构不等于实验验证的真实构象 | 摘要：yielded both parallel and antiparallel monomeric orientations |
| 四维自由能面比较 | 序列反转改变 coiled-coil 的构象偏好 | wtRop vs 平行 rRop vs 反平行 rRop | 两种 rRop 均偏离天然反平行取向，稳定在中间角度 | 序列反转导致拓扑偏好改变 | 无法确定中间角度是否为全局最小或仅局部稳定 | 摘要：both rRop models deviate from the native antiparallel orientation to stabilize at an intermediate angle |
| 反平行 rRop 稳定性评估 | 反平行取向的 rRop 结构不稳定 | 反平行 rRop vs wtRop vs 平行 rRop | 反平行变体表现出最大不稳定性：单体分离增加、螺旋度丢失更明显 | 反平行取向是 rRop 的不稳定构象 | 无法确定反平行 rRop 在生理条件下是否完全无法折叠 | 摘要：antiparallel variant exhibits the most significant instability |
| 结构完整性多指标分析 | 反平行 rRop 的结构退化是多维度的 | 氢键网络、SASA、疏水核心 | 氢键网络破坏、SASA 增加、疏水核心无法维持 | 反平行 rRop 的结构不稳定性有分子层面的多重证据 | 未提供定量数值（如氢键数变化、SASA 增量） | 摘要：disrupted hydrogen bond network, increased solvent-accessible surface area, failure to maintain a robust hydrophobic core |
| 平行 rRop 与 wtRop 相似性比较 | 平行 rRop 与野生型更相似 | 平行 rRop vs wtRop | 平行变体与 wtRop 构象相似性更高 | 平行取向是 rRop 更可能保留功能的构象 | 相似性高不等于功能保留 | 摘要：parallel variant shares greater conformational similarity with the parent protein |

---

## 11 结论正确解读

**任务范围**：
- 本文仅评估了序列反转对单一 coiled-coil 蛋白（wtRop）的影响，结论不能直接推广至所有 coiled-coil 或所有蛋白质。
- 研究聚焦于热力学稳定性（自由能面、结构完整性），未涉及功能活性、动力学速率或体内行为。

**oracle/真值输入**：
- wtRop 的实验结构作为参照（oracle），但 rRop 无实验验证结构，ColabFold 预测的准确性未经过实验确认。

**端到端状态**：
- 该流程（AI 预测 → MD → MetaD）是端到端计算管线，但每一步都有误差累积风险：ColabFold 预测误差 → MD 力场误差 → MetaD CV 选择偏差。

**算力成本**：
- 未提供具体计算资源信息。四维 CV 的 well-tempered metadynamics 计算成本显著高于常规 MD，但摘要未给出具体模拟时长或资源消耗。

**历史数据依赖**：
- ColabFold 依赖训练数据库（PDB 等），对序列反转这类非天然序列的预测能力受训练数据分布限制。

**模型依赖**：
- 结论依赖 ColabFold 的预测准确性、MD 力场参数（未指明具体力场）、MetaD 参数选择（偏置因子、高斯宽度等）。

**最难情形**：
- 反平行 rRop 是最难稳定的构象，表现为最大单体分离和螺旋度丢失——这可能是序列反转破坏 coiled-coil 疏水核心相互作用的结果。

**不确定性**：
- 摘要未提供误差估计、重复实验或统计显著性检验。
- 四维自由能面的收敛性未讨论。
- 未与其他力场或增强采样方法进行交叉验证。

**有边界的复述**：
在 ColabFold 预测结构和所选力场及 MetaD 参数条件下，序列反转的 rRop 蛋白两种取向均偏离天然反平行取向，其中反平行取向表现出最显著的结构不稳定性（单体分离增加、螺旋度降低、氢键网络破坏、SASA 增加、疏水核心丧失），而平行取向与 wtRop 的构象相似性更高。该结论仅适用于 wtRop 系统及本文所用计算方法的精度范围。

---

## 12 作者自认局限

> 在提供的摘要材料中，未发现作者明确承认的局限。摘要为结果导向型描述，未包含 Limitations 或 Future Work 部分。

**作者提及的相关约束**（非正式局限，基于摘要推断）：
- 摘要中未讨论力场选择、CV 选择的合理性论证、模拟收敛性验证等，这些可能是作者在全文 Methods 中讨论但摘要未提及的内容。
- 未提供实验验证（如圆二色光谱、突变实验）来支持计算预测。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| ColabFold 预测的两种取向可能不完整 | AlphaFold 类工具对非天然序列（序列反转）的预测可靠性有限，可能遗漏其他低能构象 | 初始结构选择直接影响后续 MD/MetaD 采样结果 | 使用多种预测工具（AlphaFold2, ESMFold, RoseTTAFold）交叉验证；或使用无偏粗粒化采样生成初始构象 | 摘要：ColabFold yielded both parallel and antiparallel monomeric orientations |
| 四维 CV 的选择可能不充分 | 角度、距离、螺旋度、扭转角相似性可能无法完全描述 coiled-coil 的解折叠路径；存在 CV 耦合或正交性问题 | CV 选择不当会导致自由能面投影不完整，结论可能依赖 CV 选择 | 进行 CV 收敛性测试；使用时间结构分析（如 PCA、tICA）验证 CV 完备性；与无偏 MD 结果对比 | 摘要：four collective variables |
| 未提供定量误差估计 | 自由能面的数值不确定性、模拟收敛性未报告 | 无法评估结论的统计可靠性 | 检查 MetaD 偏置势收敛曲线；进行多副本独立模拟；计算自由能面的块平均误差 | 摘要未提供数值数据 |
| 反平行 rRop 的不稳定性可能受初始结构影响 | ColabFold 对反平行取向的预测质量可能低于平行取向，导致初始构象偏差 | 初始构象偏差可能被误读为固有热力学不稳定性 | 对两种取向进行更长时间的平衡；从不同初始构象启动 MetaD 验证结果一致性 | 摘要：antiparallel variant exhibits the most significant instability |
| 单一蛋白系统的结论推广性有限 | wtRop 是单一 coiled-coil 蛋白，序列反转效应可能因蛋白而异 | 无法确定结论是否适用于其他 coiled-coil 或重复序列蛋白 | 在多个 coiled-coil 系统上重复类似流程 | 摘要仅涉及 wtRop/rRop |
| 缺乏实验验证 | 计算预测的稳定性差异未经过实验（如 CD、DSC、突变）验证 | 计算结论需要实验锚定才能具有生物学意义 | 对 rRop 进行圆二色光谱、差示扫描量热或细胞实验验证 | 摘要未提及实验验证 |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **AI 预测 + 增强采样组合流程**：对于未知序列蛋白的稳定性评估，可复用「ColabFold 生成初始构象 → 经典 MD 平衡 → WT-MetaD 增强采样 → 自由能面分析」的完整管线。该流程适用于蛋白质设计中的候选序列筛选、突变稳定性预测等任务。

2. **多 CV 自由能面构建策略**：对于 coiled-coil 这类具有多个构象自由度的体系，使用四维 CV（角度、距离、螺旋度、扭转角相似性）比单一 CV 能更全面刻画构象变化。可迁移至其他多结构域蛋白或蛋白复合物的构象采样任务。

3. **序列反转作为结构-稳定性探针**：序列反转是一种极端的序列扰动，可作为"压力测试"揭示序列方向性与拓扑结构之间的耦合。该方法可推广至其他重复序列蛋白（如 ankyrin、leucine-rich repeat）或设计蛋白的鲁棒性评估。

4. **多维度结构完整性指标**：氢键网络、SASA、疏水核心维持、螺旋度等多指标联合分析，比单一指标更能全面评估结构稳定性。可迁移至蛋白质设计中的结构验证环节。

5. **取向多样性考虑**：AI 结构预测可能产生多种拓扑取向（平行/反平行），在 MD 模拟中应同时考虑所有预测构象，而非仅取最高置信度结果。这对 coiled-coil 设计、膜蛋白或蛋白-蛋白相互作用界面的构象采样有直接借鉴意义。

6. **自由能面比较策略**：通过比较突变体/变体与野生型的自由能面特征（最小值位置、能垒高度、构象态分布），可定量评估序列扰动对蛋白质稳定性的影响。该方法可迁移至蛋白质工程中的稳定性优化任务。

---

## 15 与已有知识连接

- **AlphaFold2/ColabFold 在非天然序列上的应用**：本文使用 ColabFold 预测序列反转蛋白的结构，与已知的 AlphaFold2 在突变体、设计序列上的应用研究相关。已知 AlphaFold2 对非天然序列的预测置信度可能降低，本文结果与此一致（产生两种取向，暗示预测不确定性）。

- **Coiled-coil 序列-结构关系**：Rop 蛋白是经典的 coiled-coil 研究模型，已有大量关于其折叠、稳定性、寡聚状态的研究。本文的序列反转研究补充了序列方向性对 coiled-coil 拓扑选择影响的新数据。

- **Well-tempered metadynamics 在蛋白质稳定性研究中的应用**：WT-MetaD 已被广泛用于蛋白质折叠/去折叠自由能计算。本文将其应用于序列反转变体的比较，是该方法在蛋白质工程评估中的又一实例。

- **AI 预测 + MD 的组合范式**：近年来出现多篇将 AlphaFold 预测结构与 MD 模拟结合的研究（如预测结构作为 MD 起点、AlphaFold 置信度作为 MD 约束等）。本文属于这一范式，但增加了增强采样以获取热力学信息。

- **序列反转/逆序列（retro-sequence）研究**：蛋白质逆序列设计（retro-proteins）是一个小众但持续的研究方向，本文为这一方向提供了新的计算证据。

- **与蛋白质设计方法的关联**：本文的「序列扰动 → 结构稳定性评估」流程，可视为蛋白质设计中的负设计（negative design）验证，与 Rosetta、ProteinMPNN 等设计工具的评估环节相关。

---

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：多力场交叉验证的序列反转稳定性评估
- **名称**：Cross-force-field validation of sequence reversal effects on coiled-coil stability
- **来源局限/观察**：本文仅使用单一力场（未指明），力场选择可能影响自由能面结论
- **核心假设**：序列反转导致的稳定性差异在不同力场（如 CHARMM36m, AMBER ff19SB, OPLS-AA）下保持一致
- **相对本文的增量**：增加结论的鲁棒性验证，排除力场伪影
- **初步方法**：在 2-3 种主流力场下重复 wtRop/rRop 的 MD + WT-MetaD 模拟，比较自由能面特征
- **验证方式**：检查不同力场下自由能面最小值位置、相对能垒高度的一致性
- **可能的失败模式**：不同力场给出定性不同的结论，需要更谨慎的力场选择论证
- **创新状态**：unverified

### 候选 2：序列反转对 coiled-coil 寡聚状态的影响
- **名称**：Impact of sequence reversal on coiled-coil oligomeric state preference
- **来源局限/观察**：本文聚焦于单体取向（平行/反平行），未涉及寡聚状态变化；Rop 蛋白天然为二聚体
- **核心假设**：序列反转可能改变 coiled-coil 的寡聚状态偏好（如二聚→三聚/四聚）
- **相对本文的增量**：从单体构象扩展到寡聚组装，更接近生物学功能
- **初步方法**：使用 AlphaFold-Multimer 预测 rRop 的寡聚状态，结合粗粒化 MD 或增强采样评估不同寡聚体的稳定性
- **验证方式**：比较不同寡聚状态下的结合自由能或组装自由能面
- **可能的失败模式**：AlphaFold-Multimer 对非天然序列的寡聚预测不可靠
- **创新状态**：unverified

### 候选 3：序列反转作为蛋白质设计鲁棒性评估工具
- **名称**：Sequence reversal as a robustness probe for de novo protein design
- **来源局限/观察**：本文展示了序列反转对 coiled-coil 稳定性的显著影响，提示序列方向性是设计鲁棒性的关键因素
- **核心假设**：设计蛋白对序列反转的耐受性可作为其折叠鲁棒性的度量指标
- **相对本文的增量**：将序列反转从"扰动研究"提升为"设计评估工具"
- **初步方法**：对多个 de novo 设计蛋白（coiled-coil、β-折叠等）进行序列反转，用 AI 预测 + MD 评估结构稳定性变化
- **验证方式**：比较设计蛋白与天然蛋白对序列反转的耐受性差异
- **可能的失败模式**：序列反转对某些折叠类型（如 β-折叠）的影响与 coiled-coil 不同，需要分类讨论
- **创新状态**：unverified

### 候选 4：基于自由能面的序列方向性设计原则
- **名称**：Free-energy-based design principles for sequence directionality in coiled-coils
- **来源局限/观察**：本文发现平行 rRop 与 wtRop 更相似，暗示序列方向性对拓扑选择有可预测的规律
- **核心假设**：coiled-coil 的序列方向性偏好可由自由能面特征（最小值位置、深度）定量预测
- **相对本文的增量**：从"评估"走向"设计"，提出可操作的设计原则
- **初步方法**：系统扫描 coiled-coil 序列的 N→C 方向性变化，用 WT-MetaD 计算自由能面，建立方向性-稳定性映射关系
- **验证方式**：设计若干序列方向性变体，用实验（CD、DSC）验证计算预测
- **可能的失败模式**：自由能面计算成本高，难以系统扫描大量序列
- **创新状态**：unverified

### 候选 5：AI 预测置信度与增强采样结果的关联分析
- **名称**：Correlating AI prediction confidence with enhanced sampling free energy landscapes
- **来源局限/观察**：ColabFold 对 rRop 产生两种取向，暗示预测不确定性；这种不确定性与后续 MD/MetaD 结果的关系值得探索
- **核心假设**：AlphaFold/ColabFold 的 pLDDT/PAE 置信度指标可预测哪些区域需要更密集的增强采样
- **相对本文的增量**：建立 AI 预测不确定性到模拟采样策略的映射，优化计算资源分配
- **初步方法**：对多个蛋白体系，比较 pLDDT 低分区域与自由能面中高能垒/多稳态区域的空间对应关系
- **验证方式**：统计 pLDDT 与局部自由能粗糙度/能垒高度的相关性
- **可能的失败模式**：pLDDT 与动力学性质可能无直接关联，相关性弱
- **创新状态**：unverified