## 01 基本信息

- **标题**：Latent generative search unlocks de novo design of untapped biomolecular interactions at scale
- **作者与单位**：Didi K; Reidenbach D; Penner M; 等（NVIDIA、Manifold Bio、Viva Biotech、Novo Nordisk 等，详见 Competing Interest Statement）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2026-09-18
- **论文类型**：预印本（方法学 + 实验验证）
- **领域**：蛋白质设计 × 生成式 AI × 实验验证（噬菌体展示）
- **关键词**：de novo binder design, latent generative search, sequence-structure codesign, reward-guided inference, carbohydrate-binding proteins, phage display
- **DOI/arXiv 号**：10.64898/2026.09.12.751118
- **代码**：https://github.com/NVIDIA-BioNeMo/Proteina-Complexa
- **数据**：未提供（文中提及超过一百万 designs 的噬菌体展示筛选，但未给出完整数据集）
- **阅读日期**：2026-09-18
- **该文在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI 方法」中的 de novo 蛋白-蛋白/蛋白-配体相互作用设计方向。其核心创新在于：(1) 使用连续潜空间中的序列-结构联合生成（codesign），绕开传统 inverse-folding 两步法；(2) 在推理时引入 reward-guided search（类似 RL/引导生成），而非仅靠训练时监督；(3) 首次实现 de novo 自由碳水化合物结合蛋白。该文与 AlphaFold 类结构预测方法互补——它不预测天然结构，而是生成新结合界面；与 MD 模拟的关系在于其目标靶点包括柔性配体（如碳水化合物），这类体系正是 MD 采样困难的场景。

---

## 02 一句话总结

本文提出 latent generative search（LGS）框架，在 Proteina-Complexa 生成模型的连续潜空间中进行 reward-guided 推理时搜索，联合生成 binder 的序列与结构，经超过一百万 designs 的噬菌体展示筛选，在多个靶点（治疗性受体、病毒附着蛋白、胞内信号靶点）上获得高亲和力 binder，并首次生成能结合自由碳水化合物（含血型抗原区分）的 de novo 蛋白。

---

## 03 研究问题

- **具体问题**：如何设计能够结合极性、溶剂暴露表位（如蛋白表面亲水区域）以及小分子柔性配体（如碳水化合物）的 de novo 结合蛋白？
- **为什么重要**：现有 de novo binder 设计方法主要依赖疏水相互作用，对极性和水合表面效果差；碳水化合物等柔性配体在生物学中广泛存在（血型抗原、病原体表面糖基化等），但从未有 de novo 蛋白成功结合自由碳水化合物。
- **现有方法为何不足**：
  - 传统方法（如 RFdiffusion + ProteinMPNN）采用「结构生成 → 序列逆折叠」两步法，逆折叠步骤可能丢失结构信息，且对极性界面的序列设计能力有限。
  - 现有方法偏好疏水接触，对水合极性表面缺乏设计原则。
  - 柔性配体（如糖）的构象空间大，难以用固定骨架的 docking 或扩散方法处理。
- **精确研究问题**：Can a generative model that codesigns sequence and structure in a continuous latent space, combined with reward-guided search at inference time, produce de novo binders to polar, solvent-exposed epitopes and small flexible ligands (including free carbohydrates) at scale?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的框架，标注为「仅本文框架」；部分代表性方法为外部常识，标注「经外部核验」。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 早期计算设计 | Rosetta 能量函数设计 | 物理可解释 | 成功率低，需大量实验筛选 | 背景 |
| 深度生成结构设计 | RFdiffusion（扩散模型生成骨架） | 可生成新骨架，成功率提升 | 需逆折叠步骤；对极性界面效果差 | 本文的直接前身 |
| 序列设计 | ProteinMPNN 等逆折叠方法 | 快速、可扩展 | 依赖输入结构；对极性表面序列设计能力有限 | 本文绕开的步骤 |
| 序列-结构联合生成 | 潜空间生成模型（如 Proteina-Complexa 的前身工作） | 避免逆折叠信息损失 | 缺乏推理时引导，生成质量不可控 | 本文的基础模型 |
| 推理时引导生成 | LGS（本文） | 在潜空间中用 reward 引导搜索，无需重新训练 | 需要可微或可查询的 reward 函数 | **本文核心贡献** |

**本文主张的位置**：LGS 是第一个将「潜空间序列-结构联合生成」与「推理时 reward-guided search」结合用于 binder 设计的方法，并首次扩展到自由碳水化合物靶点。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 极性/水合表位难以设计 binder | 现有方法对亲水表面成功率极低 | 现有方法偏好疏水接触；极性界面需要精确的氢键网络和水的协调，难以用现有评分函数捕捉 | Abstract：「provide few of the hydrophobic contacts favoured by current methods」 |
| 柔性配体（糖类）无法设计 | 从未有 de novo 蛋白结合自由碳水化合物 | 柔性配体构象空间大，难以用固定骨架方法处理；糖-蛋白相互作用依赖极性接触 | Abstract：「have largely resisted de novo binders」 |
| 逆折叠步骤信息损失 | 结构生成后的序列设计可能破坏结合界面 | 逆折叠是独立步骤，无法在序列-结构联合空间中优化 | Abstract：「removes the inverse-folding step on which current methods rely」 |
| 生成模型缺乏目标导向 | 无条件生成无法保证结合活性 | 训练目标（数据似然）与设计目标（结合亲和力）不一致 | 推理时引入 reward-guided search（Methods 节） |

---

## 06 核心思想

### 1) 表面方法
- 使用 Proteina-Complexa 生成模型，在连续潜空间中联合生成 binder 的序列与结构（codesign）。
- 在推理时引入 reward-guided search：定义 reward 函数（如结合能、界面互补性、形状匹配等），在潜空间中进行引导搜索，使生成偏向高 reward 区域。
- 通过 multiplexed phage display 对超过 100 万 designs 进行实验筛选。

### 2) 核心洞察
- **潜空间是连续且可导航的**：与离散序列空间或结构坐标空间不同，潜空间中的插值和搜索可以同时改变序列和结构，保持二者的协调性。
- **推理时搜索可以补偿训练目标的不足**：生成模型只需学习合理的序列-结构分布，而结合特异性可以通过推理时的 reward 引导实现，无需为每个靶点重新训练。
- **Codesign 优于两步法**：联合生成序列和结构避免了逆折叠的信息损失，尤其对极性界面（氢键网络需要序列-结构协同优化）。

### 3) 可能的普适教训 [Analysis]
- 生成模型的「推理时计算」可以作为一种通用杠杆：当训练数据有限或目标函数复杂时，用推理时搜索替代训练时优化，可能比重新训练更高效。
- 对柔性配体（如糖、小分子）的结合设计，可能需要放弃「刚性界面」假设，转而利用潜空间的连续变形能力来匹配配体构象。

---

## 07 方法总览

- **输入**：靶点结构（蛋白或配体）；目标表位/结合位点定义；reward 函数（结合能、界面指标等）。
- **输出**：binder 的序列 + 预测结构（codesign 输出）；经实验验证的 binder 列表。
- **模块**：
  1. **Proteina-Complexa 生成模型**：在连续潜空间中联合生成序列与结构。
  2. **Reward 函数**：评估生成 binder 与靶点的结合潜力（具体形式未在摘要中详述）。
  3. **潜空间搜索算法**：在潜空间中进行 reward-guided 迭代搜索（具体算法细节未在摘要中详述）。
  4. **实验筛选**：multiplexed phage display，>1M designs。
- **训练**：Proteina-Complexa 为预训练生成模型；LGS 不重新训练模型，仅在推理时搜索。
- **工具**：代码在 GitHub（NVIDIA-BioNeMo/Proteina-Complexa）。
- **假设**：潜空间中的 reward-guided 搜索能有效找到高结合潜力的序列-结构对；codesign 优于序列后设计。
- **流程**：定义靶点与 reward → 在潜空间中初始化候选 → 迭代搜索（生成 → 评估 → 更新）→ 输出候选序列 → 实验筛选 → 验证 binder。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| Proteina-Complexa 生成模型 | 在潜空间中联合生成序列与结构 | 提供可导航的连续潜空间，支持 codesign | 输入：潜变量/噪声；输出：序列+结构 | Abstract：「codesigns sequence and structure」 | 无生成模型则无法生成候选（预期） |
| Reward 函数 | 评估 binder-靶点结合潜力 | 引导搜索方向，使生成偏向高结合候选 | 输入：binder-靶点复合物；输出：标量 reward | Abstract：「reward-guided search」 | 无 reward 则搜索无方向，退化为无条件生成（预期） |
| 潜空间搜索算法 | 在潜空间中迭代优化候选 | 推理时引导，无需重新训练 | 输入：初始潜变量+reward；输出：优化后的潜变量 | Abstract：「steer the Proteina-Complexa generative model」 | 无搜索则生成质量不可控（预期） |
| Codesign（联合生成） | 同时生成序列与结构 | 避免逆折叠信息损失，尤其对极性界面 | 输入：潜变量；输出：序列+结构对 | Abstract：「removes the inverse-folding step」；「codesigned sequences surpassing post hoc redesign」 | 若改为两步法，性能下降（实测：codesign 优于 post hoc redesign） |
| Multiplexed phage display | 实验验证候选 binder | 计算预测需实验确认 | 输入：>1M designs；输出：validated binders | Abstract：「screen of more than one million designs」 | 无实验验证则无法确认功能（预期） |

---

## 09 关键公式符号

不适用。摘要与正文中未提供具体公式或符号定义。方法细节（reward 函数形式、搜索算法更新规则等）未在提供的材料中披露。

---

## 10 实验设计与证据链

- **数据集/群体**：超过 1,000,000 个 designs（计算生成）；经 multiplexed phage display 筛选。
- **靶点**：治疗性受体、病毒附着蛋白、胞内信号靶点、自由碳水化合物（含血型抗原）。
- **指标**：validated binders 数量；结合亲和力（高亲和力）；与现有方法对比的 binder 数量。
- **基线**：「every other method tested」（具体基线方法未在摘要中列出）。
- **预算/规模**：>1M designs 的噬菌体展示筛选（大规模）。
- **评测协议**：multiplexed phage display；未提供详细协议。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| 大规模 binder 筛选 | LGS 能产生 validated binders | 与其他方法对比 | LGS 产生更多 validated binders | LGS 优于现有方法 | 未提供具体数量与效应量 | Abstract |
| Codesign vs post hoc redesign | 联合生成优于序列后设计 | codesign 输出 vs 后设计序列 | codesign 序列表现更好 | 联合生成保留关键界面信息 | 未提供具体指标 | Abstract |
| 碳水化合物 binder | 能设计自由糖结合蛋白 | 无先例（首次） | 成功生成糖结合蛋白，含血型抗原区分 | 方法扩展到柔性极性配体 | 未提供亲和力数值 | Abstract |
| 多靶点验证 | 方法泛化性 | 受体、病毒蛋白、胞内靶点 | 均获得高亲和力 binder | 方法具有靶点泛化性 | 未提供各靶点成功率 | Abstract |

---

## 11 结论正确解读

- **任务范围**：de novo binder 设计，靶点包括蛋白（受体、病毒蛋白、胞内蛋白）和自由碳水化合物。
- **oracle/真值输入**：噬菌体展示实验筛选是最终真值；reward 函数为计算代理（具体形式未披露）。
- **端到端状态**：计算生成 → 实验验证全流程完成，但未提供临床或体内数据。
- **算力成本**：未提供。
- **历史数据依赖**：Proteina-Complexa 为预训练模型，训练数据未披露。
- **模型依赖**：结果依赖 Proteina-Complexa 的潜空间质量；若更换生成模型，LGS 效果可能变化。
- **最难情形**：自由碳水化合物（柔性、极性、水合）是当前方法最难的目标类别，本文首次突破。
- **群体/领域边界**：结果限于噬菌体展示可筛选的靶点；未覆盖膜蛋白、翻译后修饰等复杂体系。
- **不确定性**：未提供 binder 亲和力具体数值、成功率、假阳性率；未提供与现有方法的定量对比数据。
- **有边界的复述**：在本文测试的靶点集合内，LGS 结合 Proteina-Complexa 的 codesign 潜空间搜索，在噬菌体展示筛选中产生了比对比方法更多的 validated binders，并首次获得自由碳水化合物结合蛋白；但具体性能数值、泛化边界和计算成本未在提供的材料中披露。

---

## 12 作者自认局限

在提供的材料（摘要 + 声明）中，未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，来自 Competing Interest Statement）：
- 多位作者为 NVIDIA、Manifold Bio、Viva Biotech、Novo Nordisk 员工，存在商业利益关联。
- 方法相关专利已申请（美国专利公开号 2026/0212951 A1 及临时专利 64/005,317），可能限制方法开源使用。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 未提供定量对比数据 | 摘要仅称「more validated binders than every other method tested」，无具体数量、效应量、统计显著性 | 无法评估优势的实际幅度 | 要求作者提供与各基线方法的完整对比表（含 designs 数量、验证率、亲和力分布） | Abstract |
| Reward 函数未披露 | 搜索效果高度依赖 reward 设计；若 reward 有偏差，结果可能偏向特定界面类型 | Reward 是方法核心，不披露则无法复现 | 要求补充 reward 函数形式、超参数、消融实验 | Methods 节未提供 |
| 碳水化合物 binder 的亲和力与特异性未量化 | 「binds a free carbohydrate」与「discriminates between blood-group antigens」未给出 Kd 或特异性倍数 | 无法判断实际应用价值 | 要求提供 SPR/ITC 亲和力数据及交叉反应性实验 | Abstract |
| 未提供失败案例分析 | 大规模筛选中必然有大量失败 designs；失败模式可揭示方法边界 | 失败分析是方法改进的关键 | 要求补充失败 designs 的特征分析（如 reward 分数分布、序列特征） | 未提供 |
| 预印本未经同行评审 | 方法细节、数据完整性、结论稳健性未经验证 | 预印本结论可能被后续评审修正 | 关注后续正式发表版本 | 期刊状态 |
| Codesign 优势的机制解释不足 | 为何 codesign 优于 post hoc redesign？是潜空间连续性、还是 reward 搜索的贡献？ | 机制理解影响方法迁移 | 要求消融：固定结构仅搜索序列 vs 联合搜索 | Abstract 仅给结论 |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **推理时 reward-guided search 作为通用设计范式**：本文最核心的可迁移思想是「训练时学分布，推理时做优化」。对于蛋白质设计，这意味着可以先用大规模数据预训练生成模型，再针对特定靶点定义 reward 函数进行推理时搜索，避免为每个靶点重新训练。可迁移到本课题的构象采样/生成任务：例如用生成模型产生候选构象，再用物理或 ML reward 引导搜索。

2. **Codesign（序列-结构联合生成）优于两步法**：传统「结构生成 → 序列设计」的流水线存在信息损失。本文证据表明联合生成在 binder 设计中更优。可迁移到本课题的序列设计任务：考虑在潜空间中同时优化序列与结构，而非固定骨架做逆折叠。

3. **潜空间连续性的价值**：连续潜空间允许插值和梯度引导，这是离散空间（如氨基酸序列）难以实现的。可迁移到构象生成任务：用 VAE/扩散模型的潜空间表示构象系综，在潜空间中做 reward-guided 采样可能比直接坐标空间更高效。

4. **极性/柔性界面的设计原则**：本文证明极性、水合、柔性靶点（糖类）并非不可设计，只是需要合适的生成框架。可迁移到本课题的分子对接/MD 模拟：对柔性配体，可能需要显式考虑水分子和构象系综，而非单一刚性结构。

5. **大规模实验筛选作为计算方法的验证闭环**：>1M designs 的噬菌体展示筛选提供了强大的验证信号。可迁移到本课题：计算方法应设计与高通量实验兼容的输出格式（如条形码、multiplex 策略）。

6. **Reward 函数设计是关键瓶颈**：搜索效果取决于 reward 质量。可迁移到本课题：若用 MD 模拟或对接打分作为 reward，需注意计算成本与可微性；可考虑用 ML 代理模型加速 reward 评估。

---

## 15 与已有知识连接

- **RFdiffusion (Watson et al., 2023, Nature)**：扩散模型生成蛋白骨架，是本文的直接前身。本文的 Proteina-Complexa 可视为 RFdiffusion 的潜空间扩展，增加了序列联合生成和推理时引导。连接点：RFdiffusion 的骨架生成 + ProteinMPNN 逆折叠 = 两步法；本文的 codesign = 一步法。
- **ProteinMPNN (Dauparas et al., 2022, Science)**：逆折叠序列设计。本文声称 codesign 优于 post hoc redesign（即优于 ProteinMPNN 类方法），这是一个可直接对比的 claim。
- **AlphaFold (Jumper et al., 2021, Nature)**：结构预测。本文不预测天然结构，而是生成新结合界面；但 AlphaFold 可作为 reward 函数的一部分（预测复合物结构并评估置信度）。
- **Diffusion models for protein design (e.g., Chroma, Ingraham et al., 2023)**：Chroma 也做序列-结构联合生成，但本文的增量是推理时 reward-guided search 和碳水化合物靶点。
- **Carbohydrate-binding proteins (lectins)**：天然凝集素是糖结合蛋白的经典范例，但 de novo 设计糖结合蛋白此前未实现。本文填补了这一空白。
- **Phage display for binder screening**：高通量实验验证的标准方法，本文将其扩展到 >1M designs 规模。
- **[Analysis] 候选方向**：与 MD 模拟的联系——本文的 reward 函数若包含物理能量项（如 Rosetta 或 AMBER 打分），则与 MD 模拟的力场设计直接相关；柔性糖配体的处理也涉及构象采样问题，可与增强采样方法（如 metadynamics、replica exchange）结合。

---

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：潜空间 reward-guided 构象采样（Latent Reward-Guided Conformational Sampling）
   - **来源局限/观察**：本文在潜空间中搜索 binder 序列-结构，但未涉及构象系综；对柔性配体（糖）的构象多样性处理方式未披露。
   - **核心假设**：在潜空间中结合 reward-guided 搜索与构象多样性约束，可以更高效地采样蛋白-配体结合构象系综，优于传统 MD 或 docking。
   - **初步方法**：用 Proteina-Complexa 或类似模型生成 binder-配体复合物潜变量，定义 reward 为结合能 + 构象多样性惩罚，在潜空间做多模态搜索。
   - **验证方式**：对已知柔性配体体系（如凝集素-糖）回测，比较生成构象与实验结构（晶体/MD 系综）的覆盖度。
   - **创新状态**：unverified

2. **候选名称**：物理-生成混合 reward 函数（Physics-Generative Hybrid Reward）
   - **来源局限/观察**：本文 reward 函数未披露；纯 ML reward 可能缺乏物理可解释性。
   - **核心假设**：将 MD 力场能量项（如 AMBER/CHARMM）与 ML 界面评分结合作为 reward，可提高生成 binder 的实验成功率。
   - **初步方法**：在 LGS 框架中，reward = α·ML_score + β·MM_energy + γ·solvation_term，在潜空间中搜索。
   - **验证方式**：对本文的靶点集合进行消融，比较不同 reward 组合的验证率。
   - **创新状态**：unverified

3. **候选名称**：AlphaFold 引导的潜空间搜索（AlphaFold-Guided Latent Search）
   - **来源局限/观察**：本文未使用结构预测作为 reward 或验证；AlphaFold 可作为复合物结构的强先验。
   - **核心假设**：将 AlphaFold 对生成复合物的预测置信度（pLDDT/pAE）纳入 reward，可过滤低质量设计，提高实验命中率。
   - **初步方法**：在 LGS 搜索的每次迭代中，对候选复合物运行 AlphaFold 预测，将置信度分数加入 reward。
   - **验证方式**：对比有无 AlphaFold reward 的验证率与亲和力分布。
   - **创新状态**：unverified（AlphaFold 用于设计验证已有先例，但结合潜空间搜索为新的）

4. **候选名称**：糖-蛋白界面设计规则提取（Glycan-Binding Interface Design Rules）
   - **来源局限/观察**：本文首次实现 de novo 糖结合蛋白，但未系统分析成功 binder 的界面特征。
   - **核心假设**：成功糖结合 binder 存在可提取的序列-结构模式（如极性残基排列、水分子介导氢键网络），可用于后续设计规则。
   - **初步方法**：对本文成功 binder 与失败 designs 做对比分析，提取界面残基偏好、氢键模式、形状互补性特征。
   - **验证方式**：用提取规则设计新糖靶点 binder，检验成功率是否提升。
   - **创新状态**：unverified

5. **候选名称**：多靶点 reward 联合搜索（Multi-Target Joint Reward Search）
   - **来源局限/观察**：本文针对单靶点设计；对需要选择性（如区分血型抗原）的场景，reward 需包含负向约束。
   - **核心假设**：在 reward 中同时包含目标结合项与非目标排斥项，可在潜空间中搜索选择性 binder。
   - **初步方法**：reward = 目标结合能 − λ·非目标结合能，在潜空间中搜索。
   - **验证方式**：对血型抗原体系测试选择性 binder 设计。
   - **创新状态**：unverified（选择性设计已有先例，但结合潜空间搜索为新）