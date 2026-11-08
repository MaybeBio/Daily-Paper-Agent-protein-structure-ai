## 01 基本信息

- **标题**：Crystallographic fragment screening in cancer and antiviral drug discovery: from electron density to translational outcomes
- **作者**：Balikci, Esra; Grimes, Jonathan M
- **单位**：未提供（根据 Grimes 姓氏推测可能为伦敦大学学院（UCL）相关机构，但原文未提供，标注为未提供）
- **期刊/平台**：Expert Opinion on Drug Discovery
- **年份**：2026（在线日期 2026-11-02）
- **论文类型**：综述（Review / Expert Opinion）
- **领域**：结构生物学 × 药物发现；crystallographic fragment screening (CFS)；癌症与抗病毒药物研发
- **关键词**：crystallographic fragment screening; fragment-based drug discovery; X-ray crystallography; structure-based drug design; oncology; antiviral; machine learning
- **DOI/arXiv**：10.1080/17460441.2026.2754037
- **代码**：未提供
- **数据**：未提供（文中提及"reusable structural datasets"作为未来方向，但未提供具体数据集）
- **阅读日期**：2026-11-02（以当前日期为准）
- **在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × 物理模拟（X-ray crystallography）」交叉方向，聚焦实验结构测定（CFS）如何为计算药物设计提供起点。对本课题（蛋白质结构预测、构象采样、分子对接、MD 模拟、结构/序列设计 × AI/物理模拟）而言，本文提供了：1) 实验结构信息（电子密度）作为计算方法的"oracle/真值"输入；2) 计算/ML 方法在 fragment elaboration 和 prioritization 中的定位与边界；3) 可复用结构-亲和力数据集作为未来训练/验证资源的倡议。

---

## 02 一句话总结

本文综述了 crystallographic fragment screening (CFS) 如何在癌症和抗病毒药物发现中通过实验测定 fragment 的结合位点、构象和化学延伸路径，为后续计算和化学优化提供结构假设，并指出计算/ML 方法可辅助但不可替代实验结构测定与功能验证。

---

## 03 研究问题

- **具体问题**：CFS 在癌症和抗病毒药物发现中如何将弱结合的 fragment 转化为可行动的化学起点（lead series、preclinical candidates、clinical molecules）？其实际要求、局限、验证标准和计算辅助的边界是什么？
- **为什么重要**：药物发现早期的不确定性主要来自缺乏实验支持的结构假设。CFS 通过在化学投资前建立结构假设，降低"基于活性或建模推断但缺乏实验结构证据"的结合模式风险。
- **现有方法为何不足**：传统 fragment-based drug discovery (FBDD) 依赖生化活性筛选（如 NMR、SPR），但这些方法不直接提供原子分辨率的结合模式；计算对接和建模可预测结合模式，但存在假阳性和精度不足问题。CFS 直接提供电子密度证据，弥补了这一缺口。
- **精确研究问题（Can...?）**：Can crystallographic fragment screening provide an experimentally grounded binding hypothesis early enough in discovery to reduce the risk of pursuing incorrect binding modes inferred from activity or modeling alone?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架（Introduction 和 Areas Covered 部分），未做外部核验，标注为「仅本文框架」。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文主张的位置 |
|------|-----------|------|------|---------------|
| 传统 FBDD（NMR/SPR 为主） | SAR by NMR（Shuker et al. 1996 等） | 可检测弱结合；无需晶体 | 无原子分辨率结合模式；需后续结构解析 | CFS 提供直接结构证据，弥补此缺口 |
| 高通量 X 射线晶体学 | 同步辐射/Free-Electron Laser 高通量筛选 | 直接获得电子密度、结合位点、构象 | 需晶体；通量和成本高；需专业设施 | CFS 的核心技术基础 |
| 计算对接/虚拟筛选 | Docking, pharmacophore, ML scoring | 低成本、高通量 | 结合模式预测精度有限；假阳性 | 可辅助 fragment elaboration 和 prioritization，但不替代实验 |
| CFS + 计算/ML 整合 | 结构-亲和力数据集 + ML 排序 | 扩展化学空间探索；支持多参数优化 | 依赖高质量训练数据；需实验验证 | 本文主张的未来方向：tighter structure-design-synthesis-test cycles |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|----------|
| 早期结合模式不确定性 | 基于活性或建模推断的结合模式可能错误 | 活性测定不提供原子分辨率信息；建模存在精度限制 | Introduction："risk of pursuing a binding mode inferred from activity or modeling but not supported by experimental structural evidence" |
| Fragment 结合弱 | 弱结合难以用常规生化方法检测和定位 | Fragment 分子量小、亲和力低（通常 mM 级） | Introduction："CFS...defining a fragment's binding site, pose and routes for chemical elaboration" |
| 化学延伸方向不明确 | 缺乏结构指导时，medicinal chemistry 投资可能浪费 | 无实验结构假设时，SAR 探索盲目 | Introduction："reduces early uncertainty...before major medicinal-chemistry investment" |
| 计算方法的验证缺口 | 计算预测缺乏实验结构验证 | 计算模型可能过拟合或精度不足 | Expert Opinion："they do not replace experimental determination of binding modes or functional validation" |
| 数据可复用性不足 | 结构-亲和力数据分散、不标准化 | 缺乏统一数据集和共享机制 | Expert Opinion："reusable structure-affinity datasets" 作为未来方向 |

---

## 06 核心思想

### 1) 表面方法
综述 CFS 的技术流程：制备晶体 → 浸泡/共结晶 fragment 库 → 高通量 X 射线数据收集 → 电子密度解析 → 识别结合位点和构象 → 基于结构进行 fragment 化学延伸（elaboration）→ 优化为 lead 和临床候选分子。涵盖癌症（kinase inhibitors、PHIP2 bromodomain、brachyury、PYCR1）和抗病毒（viral proteases、polymerases、influenza PA endonuclease、SARS-CoV-2 Mac1）案例。

### 2) 核心洞察
CFS 的核心价值不在于"筛选"本身，而在于**在化学投资前建立实验支持的结构假设**。它将弱结合（weak binding）转化为可行动的几何信息（actionable geometry），揭示可配体化口袋（ligandable pockets），并提供可信的设计起点。计算/ML 方法的价值在于**延伸**这一结构信息（探索化学空间、排序延伸方案、多参数优化），而非替代实验测定。

### 3) 可能的普适教训 [Analysis]
- 对计算驱动的研究：**实验结构数据（如电子密度）是计算方法的"锚点"**，可显著降低模型预测的不确定性。本课题中，AlphaFold 预测结构或 MD 模拟构象若能与 CFS 实验电子密度交叉验证，可提高可信度。
- 对方法整合：**计算与实验的"tight cycle"（结构-设计-合成-测试）** 比任何单一方法更有效。这提示本课题中 AI 结构预测与 MD/对接应嵌入实验验证闭环，而非独立运行。
- 对数据建设：**可复用结构-亲和力数据集**是未来计算方法的训练和验证基础，本课题可借鉴此倡议构建领域专用 benchmark。

---

## 07 方法总览

> 本文为综述，无单一方法实现，以下为 CFS 工作流程的总结（基于 Areas Covered 和 Introduction）。

- **输入**：蛋白晶体；fragment 库（低分子量化合物集合）；靶蛋白（癌症或病毒相关）
- **输出**：fragment 结合位点、结合构象（pose）、化学延伸路径；后续 lead series、preclinical candidates、clinical molecules
- **模块**：
  1. 晶体准备与 fragment 浸泡/共结晶
  2. 高通量 X 射线数据收集（同步辐射/Free-Electron Laser）
  3. 电子密度解析与 fragment 定位
  4. Hit 验证与优先级排序（验证标准：电子密度质量、结合位点可配体性、化学可延伸性）
  5. 结构指导的 fragment elaboration（medicinal chemistry）
  6. 计算/ML 辅助：化学空间探索、延伸排序、多参数优化
- **工具**：X-ray crystallography（核心）；计算/ML 方法（辅助，具体工具未提供）
- **反馈回路**：结构-设计-合成-测试循环（Expert Opinion 中强调 tighter cycles）
- **假设**：实验结构假设可降低药物发现早期不确定性；弱结合 fragment 可通过结构指导延伸为高亲和力配体

**文字流程**：靶蛋白结晶 → fragment 库浸泡/共结晶 → 高通量衍射数据收集 → 电子密度计算与 fragment 定位 → hit 验证与优先级排序 → 基于结构的 fragment 化学延伸 → 优化为 lead/临床候选 → 计算/ML 辅助延伸和排序 → 新一轮结构-设计-合成-测试循环

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 高通量 X 射线晶体学 | 获得 fragment 结合的实验电子密度 | 提供原子分辨率结合模式，弥补生化筛选和建模的不足 | 输入：晶体+fragment；输出：电子密度图、结合位点、pose | Introduction："defining a fragment's binding site, pose and routes for chemical elaboration" | 移除后失去实验结构证据，回到"基于活性或建模推断"的高风险模式 |
| Hit 验证与优先级排序 | 筛选可靠 hit，排除假阳性 | 确保进入化学延伸的 fragment 有质量保证 | 输入：初始 hit 列表；输出：验证后的优先 fragment | Areas Covered："criteria for hit validation and prioritization" | 移除后可能将无效 fragment 投入化学投资，浪费资源 |
| 结构指导的 fragment elaboration | 基于结合模式进行化学延伸 | 将弱结合转化为高亲和力 lead | 输入：fragment 结合模式；输出：延伸后的 lead series | 案例：kinase inhibitors、viral proteases 等 | 移除后 fragment 无法转化为 lead，CFS 价值丧失 |
| 计算/ML 辅助方法 | 探索化学空间、排序延伸方案、多参数优化 | 扩展实验结构信息的应用范围，提高效率 | 输入：结构数据+化学库；输出：延伸候选排序 | Expert Opinion："Computational and machine-learning methods can extend this information" | 移除后仍可进行 CFS，但化学空间探索效率降低（预期效应，非实测） |
| 可复用结构-亲和力数据集 | 支持计算方法的训练和验证 | 为 ML 方法提供高质量训练数据 | 输入：CFS 实验数据；输出：标准化数据集 | Expert Opinion："reusable structure-affinity datasets" 作为未来方向 | 移除后 ML 辅助方法缺乏训练基础（预期效应，非实测） |

> 注：本文为综述，未提供消融实验数据。除「Hit 验证」和「结构指导的 elaboration」外，其余模块的移除影响为 [Analysis] 预期效应。

---

## 09 关键公式符号

**不适用**。本文为综述，未包含数学公式或算法描述。所有内容为定性讨论 CFS 流程、案例和未来方向。

---

## 10 实验设计与证据链

> 本文为综述，无原始实验数据。以下基于文中描述的案例和作者主张。

- **数据集/群体**：未提供具体数据集。文中提及的案例包括：kinase inhibitors、PHIP2 bromodomain、brachyury、PYCR1（癌症）；viral proteases、polymerases、influenza PA endonuclease、SARS-CoV-2 Mac1（抗病毒）。
- **规模**：未提供（综述未报告筛选规模或统计量）。
- **指标**：未提供（未报告亲和力数值、晶体分辨率等定量指标）。
- **基线**：未提供（未与 NMR/SPR 或其他筛选方法做定量对比）。
- **预算/骨干/仪器**：未提供（提及"high-throughput crystallography"但未指定设施）。
- **Oracle 输入**：X-ray 电子密度（作为结构假设的实验真值）。
- **评测协议**：未提供（综述未描述系统评测协议）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|------------------|------|
| 癌症案例综述（kinase inhibitors、PHIP2、brachyury、PYCR1） | CFS 可推进 fragment 至 lead/临床 | 各案例独立，无统一对比 | 文中描述为成功案例 | CFS 在癌症靶点中可提供结构起点 | 无法证明 CFS 优于其他 FBDD 方法；无定量成功率 | Areas Covered |
| 抗病毒案例综述（proteases、polymerases、PA endonuclease、Mac1） | CFS 可推进 fragment 至 lead/临床 | 各案例独立，无统一对比 | 文中描述为成功案例 | CFS 在抗病毒靶点中可提供结构起点 | 无法证明 CFS 优于其他 FBDD 方法；无定量成功率 | Areas Covered |
| 计算/ML 辅助讨论 | 计算/ML 可延伸 CFS 信息 | 无实验对比 | 作者主张可辅助 | 计算/ML 有辅助价值 | 未证明计算/ML 可替代实验；无性能数据 | Expert Opinion |

---

## 11 结论正确解读

- **任务范围**：本文仅覆盖 CFS 在癌症和抗病毒药物发现中的应用，不涉及其他治疗领域或非 CFS 的 FBDD 方法。
- **Oracle/真值输入**：X-ray 电子密度是 CFS 的核心实验真值，所有结构假设以此为基础。
- **端到端状态**：文中案例显示 CFS 可推进至临床分子，但未提供端到端成功率或失败率统计。
- **算力成本**：未讨论计算成本；仅提及高通量晶体学需要专业设施。
- **历史数据依赖**：综述基于 2026 年 3-9 月的 PubMed 检索，可能遗漏非 PubMed 收录文献或 2026 年 9 月后发表的工作。
- **模型依赖**：计算/ML 方法被定位为辅助工具，不依赖特定模型；但作者未评估具体模型的性能。
- **最难情形**：CFS 需要高质量晶体，膜蛋白、柔性靶点或低表达蛋白可能不适用；作者未详细讨论这些困难。
- **不确定性**：作者未提供定量不确定性分析（如置信区间、效应量）。
- **群体/领域边界**：结论仅适用于可结晶靶点；对不可结晶靶点（如部分膜蛋白、 intrinsically disordered proteins）不适用。

**有边界的复述**：在可结晶的癌症和病毒靶点中，CFS 通过实验电子密度提供早期结构假设，可降低药物发现中结合模式不确定性的风险；计算/ML 方法可辅助化学空间探索和延伸排序，但作者未提供定量证据表明其优于传统方法，也未证明其可替代实验验证。

---

## 12 作者自认局限

> 在提供的材料中，作者未以独立"Limitations"章节明确列出局限。以下为文中隐含提及的约束，标注为「作者提及的相关约束」而非正式局限。

### 作者提及的相关约束

| 约束 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算/ML 不替代实验 | "they do not replace experimental determination of binding modes or functional validation" | 将计算/ML 作为辅助工具，与实验结合 | Expert Opinion |
| 需要可复用数据集 | 当前缺乏标准化结构-亲和力数据集 | 构建 reusable structure-affinity datasets | Expert Opinion |
| 需要 tighter cycles | 结构-设计-合成-测试循环不够紧密 | 缩短循环周期，连接晶体学证据与生物学决策 | Expert Opinion |
| 文献检索范围 | 仅 PubMed 检索（2026 年 3-9 月） | 未提供（综述方法学局限，作者未明确讨论） | Areas Covered（"targeted PubMed searches"） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 案例选择可能偏向成功案例 | 综述可能未报告 CFS 失败案例或低效案例，导致"生存者偏差" | 若 CFS 实际成功率低，则"降低不确定性"的主张被高估 | 系统检索 CFS 失败案例，统计 hit-to-lead 转化率 | Areas Covered 仅描述成功案例，未报告失败率 |
| 未与 NMR/SPR 等替代方法定量对比 | CFS 的优势可能被夸大；不同 FBDD 方法适用场景不同 | 读者无法判断 CFS 是否优于其他 fragment 筛选方法 | 设计头对头比较实验（同一靶点，CFS vs NMR/SPR） | 全文未提供定量对比数据 |
| 计算/ML 辅助的讨论缺乏具体证据 | 作者主张计算/ML 可"extend information"，但未引用具体成功案例或性能数据 | 读者无法评估计算/ML 的实际贡献 | 检索具体 ML 辅助 CFS 延伸的案例研究，评估其预测准确率 | Expert Opinion 为定性主张，无数据支撑 |
| 未讨论 CFS 的适用边界 | 膜蛋白、柔性靶点、不可结晶蛋白可能完全不适用 CFS | 读者可能过度推广 CFS 的适用性 | 系统分析 CFS 在不可结晶靶点上的失败模式 | 全文未讨论不可结晶靶点 |
| "reusable datasets"倡议缺乏具体方案 | 作者提出未来方向但未给出数据标准、格式或共享机制 | 该倡议若无法落地，则计算/ML 辅助的发展受限 | 评估现有结构生物学数据库（如 PDB）是否可扩展为结构-亲和力数据集 | Expert Opinion 仅提及方向，无实施方案 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **实验结构作为计算方法的"锚点"**：CFS 的核心价值在于提供实验电子密度作为结构假设的真值。本课题中，AlphaFold 预测结构或 MD 模拟构象应与实验电子密度（如 PDB 中的晶体结构）交叉验证，以识别预测误差并提高可信度。可迁移：在结构预测评估中，将 CFS 实验结合位点作为 benchmark 的 ground truth。

2. **"弱结合 → 可行动几何"的转化逻辑**：CFS 将弱结合 fragment 转化为可操作的结合位点和 pose 信息。本课题中，分子对接和 MD 模拟常面临弱结合模式的低信噪比问题；可借鉴 CFS 的"先定位再优化"策略，先通过实验或高置信计算确定结合位点，再进行构象采样和亲和力优化。

3. **计算/ML 的定位是"延伸"而非"替代"**：作者明确主张计算/ML 方法可探索化学空间、排序延伸方案，但不替代实验测定。本课题中，AI 结构预测和生成模型应定位为"假设生成器"，其输出需经实验或高保真物理模拟（MD、FEP）验证。

4. **"tight cycle"设计原则**：结构-设计-合成-测试的紧密循环是 CFS 成功的关键。本课题中，AI 驱动的结构设计应嵌入实验验证闭环，而非独立运行；可设计主动学习框架，让实验反馈指导下一轮生成。

5. **可复用结构-亲和力数据集的倡议**：作者强调需要标准化数据集支持计算/ML 方法。本课题可借鉴此倡议，构建包含 CFS 实验数据（结合位点、pose、亲和力）的 benchmark，用于训练和评估结构预测、对接和生成模型。

6. **Hit 验证标准的重要性**：CFS 强调电子密度质量、可配体性和化学可延伸性作为 hit 优先级标准。本课题中，计算筛选（对接、虚拟筛选）的 hit 验证应引入类似标准（如结合位点可配体性、合成可及性），而非仅依赖打分函数。

---

## 15 与已有知识连接

- **相似方法**：与 NMR-based fragment screening（Shuker et al., 1996, Science）和 SPR-based FBDD 同属 fragment-based drug discovery 家族，但 CFS 提供原子分辨率结构信息，这是其独特优势。本课题中，分子对接和 MD 模拟可视为"计算版 CFS"，但缺乏实验真值锚定。
- **组合方向**：CFS 与 AlphaFold 结构预测可形成互补——AlphaFold 提供未实验解析靶点的预测结构，CFS 提供实验验证的结合位点；两者结合可提高结构假设的可靠性。本课题中，可探索"AlphaFold 预测 + CFS 验证"的混合工作流。
- **冲突/张力**：CFS 依赖晶体，对不可结晶靶点（膜蛋白、IDP）不适用；而 AlphaFold 和 MD 模拟可处理这些靶点。这提示本课题中计算方法在不可结晶靶点上具有独特价值，但需注意缺乏实验验证的风险。
- **可迁移领域**：CFS 的"结构假设先于化学投资"逻辑可迁移到蛋白质设计——在设计新蛋白或配体前，先通过实验或高置信计算确定结合位点，再进行序列/结构优化。本课题中，结构/序列设计可借鉴此"先锚定后优化"策略。
- **候选方向（未验证）**：CFS 的"reusable structure-affinity datasets"倡议与 AlphaFold 的 training data 策略（PDB 为基础）有潜在协同；未来可构建整合 CFS 实验数据和计算预测的联合 benchmark。此方向为 [Analysis] 推测，原文未提及。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：CFS 电子密度作为 AlphaFold 预测结构的验证基准
- **名称**：CFS-guided AlphaFold validation framework
- **来源局限/观察**：AlphaFold 预测结构缺乏实验验证，尤其在配体结合位点；CFS 提供实验电子密度作为真值。
- **核心假设**：CFS 实验结合位点可有效识别 AlphaFold 预测结构在配体结合区域的误差。
- **初步方法**：收集 CFS 实验数据（结合位点、pose），与 AlphaFold 预测结构比对，量化结合位点残基的预测误差；开发基于电子密度图的评分函数。
- **验证方式**：在已知 CFS 靶点（如 kinase、viral protease）上测试，比较 AlphaFold 预测与实验结构的 RMSD 和结合位点重叠度。
- **可能的失败模式**：AlphaFold 预测在 apo 状态下可能无法准确反映 holo 构象；CFS 数据覆盖有限。
- **创新状态**：unverified

### 候选 2：ML 辅助的 fragment elaboration 排序模型
- **名称**：Structure-aware fragment elaboration ranking (SAFER)
- **来源局限/观察**：作者主张计算/ML 可辅助 fragment 延伸排序，但未提供具体方法或数据。
- **核心假设**：结合 CFS 实验结构（结合位点、pose）和 ML 模型，可更准确预测 fragment 延伸后的亲和力提升。
- **初步方法**：构建包含 CFS 实验结构、fragment 化学特征和实验亲和力的数据集；训练图神经网络或 transformer 模型，输入为结合位点结构 + fragment SMILES，输出为预测亲和力/延伸优先级。
- **验证方式**：在 CFS 案例（如 brachyury、Mac1）上回测，比较 ML 排序与实验结果的 top-k 命中率。
- **可能的失败模式**：数据量不足；实验亲和力测量误差；模型过拟合。
- **创新状态**：unverified

### 候选 3：CFS 与 MD 模拟的 tight cycle 主动学习框架
- **名称**：CFS-MD active learning loop
- **来源局限/观察**：作者强调"tighter structure-design-synthesis-test cycles"，但未提出具体实现。
- **核心假设**：将 CFS 实验结构作为 MD 模拟的初始构象，结合主动学习，可加速 fragment 优化并减少实验轮次。
- **初步方法**：设计循环：CFS 实验结构 → MD 模拟 fragment 结合稳定性 → ML 预测延伸方案 → 合成测试 → 新 CFS 验证；每轮用实验反馈更新 ML 模型。
- **验证方式**：在 1-2 个靶点（如 influenza PA endonuclease）上实施小规模循环，比较与传统 FBDD 的迭代次数和成功率。
- **可能的失败模式**：MD 模拟成本高；主动学习收敛慢；实验周期长。
- **创新状态**：unverified

### 候选 4：可复用 CFS 结构-亲和力数据集构建
- **名称**：OpenCFS: a standardized crystallographic fragment screening benchmark
- **来源局限/观察**：作者提出"reusable structure-affinity datasets"但未提供具体方案。
- **核心假设**：标准化 CFS 数据集可显著提升计算/ML 方法的训练和评估质量。
- **初步方法**：整合 PDB 中 CFS 相关条目，统一标注结合位点、pose、亲和力、化学延伸信息；制定数据格式和评估协议。
- **验证方式**：邀请社区使用该数据集复现和比较不同计算方法。
- **可能的失败模式**：数据标准化难度大；PDB 注释不完整；社区采纳率低。
- **创新状态**：unverified

### 候选 5：CFS 结合位点可配体性预测模型
- **名称**：Ligandability prediction from CFS electron density
- **来源局限/观察**：CFS 可"reveals ligandable pockets"，但可配体性预测缺乏系统方法。
- **核心假设**：CFS 电子密度特征（如碎片密度、B-factor、occupancy）可训练模型预测新靶点的可配体性。
- **初步方法**：从 CFS 数据提取电子密度统计特征，训练分类器预测"可配体 vs 不可配体"口袋；结合 AlphaFold 预测结构推广到未实验靶点。
- **验证方式**：在已知可配体/不可配体靶点集上交叉验证。
- **可能的失败模式**：特征选择偏差；可配体性定义模糊；推广到 AlphaFold 结构时误差累积。
- **创新状态**：unverified