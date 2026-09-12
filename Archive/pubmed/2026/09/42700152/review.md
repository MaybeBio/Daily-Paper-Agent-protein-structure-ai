## Review setup
- **Input scope** 全文（Perspective/Review 手稿）
- **Assessment boundary** 仅基于提供的稿件文本；未检索或核实任何外部引用文献、数据库内容或未提供的图表数据
- **Shared manuscript claim summary** 本文为结构T细胞受体（TCR）免疫信息学领域的视角性综述，主张深度学习蛋白质结构预测方法的成熟已使TCR结构数据能够以组库规模获取，并据此综述了TCR结构生物学原理、结构预测工具（同源建模、AlphaFold2及其衍生模型）、TCR:pMHC复合物预测、基于结构的特异性预测，以及TCR和TCR模拟物（TCRm）的计算设计前沿。
- **Visible evidence base** 正文文本；引用了多个外部数据库（STCRDab、TCR3d、FTCRDab、OTS等）和工具（STCRpy、TCRBuilder2、TCRmodel2、tFold-TCR、TCRdock等）；提及Figure 1、2、3、4和Table 1，但图表内容未提供
- **Missing materials affecting confidence** 所有图表（Figure 1-4、Table 1）未提供；外部基准测试和数据库内容无法独立核实；作者自身未发表结果（如IMMREP25初步实验）的细节有限

## Reviewer
- **Overall assessment** 这是一篇撰写清晰、结构合理的视角性综述，及时总结了机器学习时代TCR结构预测领域的快速发展。作者是该领域的核心贡献者，文中多处引用自身工作（STCRpy、TCRBuilder2+、OTS、FTCRDab等），提供了有价值的领域内视角。综述覆盖范围全面，从实验结构数据库到预测工具、特异性推断和计算设计均有涉及。主要不足在于：部分关键论断缺乏定量支撑或仅引用作者自身未发表的工作；对领域内争议（如TCR特异性预测的可行性）的讨论可更深入；图表未提供导致部分论述无法评估。总体而言，该文对领域内研究者有参考价值，但作为视角性文章，其新颖性主要体现在综合框架而非新数据或新方法。
- **Who would be interested in the results, and why** 计算免疫学、结构生物信息学和蛋白质设计领域的研究者会对本文感兴趣。具体包括：开发TCR特异性预测工具的研究人员（可了解结构方法的现状与局限）；TCR工程和细胞治疗开发者（可了解计算设计工具的可用性与验证状态）；以及关注AlphaFold等通用结构预测模型在免疫受体上应用效果的生物信息学方法开发者。综述中对抗体领域工具（如TAP、SPACE）与TCR领域的对比，对跨领域研究者也有参考价值。
- **Major strengths** 1. 综述范围全面且组织清晰，从实验数据到预测工具再到设计应用，逻辑递进合理。2. 作者对领域有直接贡献，文中对工具开发动机和局限性的讨论具有实践洞察力。3. 对结构预测在特异性推断中的应用（STAG、TCRdock、NetTCR-struc）进行了有价值的梳理，这是当前领域的前沿问题。4. 对TCR与抗体结构生物学的差异（如CDR3α的结构多样性）有深入讨论，具有领域教育意义。
- **Major Concerns** 见下方详细列表。
- **Minor Comments** 见下方详细列表。
- **Technical failings that need to be addressed before the case is established** R1-M1（未提供图表数据）、R1-M2（未发表结果支撑核心论断）、R1-M3（IMMREP25结果描述不完整）
- **Assessment against Nature-style criteria** **Originality**：中等。综述框架本身并非全新，但将结构预测、特异性推断和设计三个主题整合于TCR语境下，具有一定综合价值。**Scientific importance**：较高。TCR特异性预测是免疫学核心难题，结构方法的进展值得及时综述。**Interdisciplinary readership**：中等。主要面向计算免疫学和结构生物学研究者，对实验免疫学家的可读性取决于其对机器学习概念的熟悉程度。**Technical soundness**：总体可靠，但部分关键论断依赖未提供的图表或未发表数据，无法完全验证。**Readability for nonspecialists**：良好。术语使用一致，背景介绍充分，但部分技术细节（如扩散模型、pAE指标）对非专业读者可能略显密集。综合而言，该文作为领域综述具有发表价值，但需解决证据可验证性问题。
- **Recommendation posture** Supportive if technical concerns are resolved. 本文作为视角性综述具有领域价值，但需提供图表数据、明确区分已发表与未发表结果，并补充IMMREP25实验的完整描述。

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** 文中多处引用Figure 1-4和Table 1来支撑关键论断，包括TCR结构特征（Figure 1）、数据分布偏差（Figure 2）、置信度指标与特异性相关性（Figure 3）以及设计流程（Figure 4）。
- **Evidence pointer** Figure 1-4, Table 1（均未提供）
- **Concern** 所有图表均未随稿件提供，导致文中依赖这些图表的定量论断无法评估。例如，Figure 2b声称展示了TRAV-TRBV基因对联合分布的稀疏采样，Figure 3b声称展示了IMMREP25数据集中21/30的靶标肽被正确识别，但这些数据无法核实。
- **Why it matters** 作为视角性综述，图表的可验证性是读者评估作者论断可信度的基础。缺少图表使关键定量声明成为不可验证的断言，削弱了文章作为参考资源的可靠性。
- **Resolution test** 提供所有图表及其生成代码或详细方法说明，使读者能够独立验证文中引用的定量结果。

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** 文中多处引用作者自身未发表的工作作为关键论断的依据，包括STCRpy工具的功能描述、FTCRDab数据库的生成、以及IMMREP25初步实验的结果。
- **Evidence pointer** Section 2.2, Section 3.3, Section 4.3
- **Concern** 作者在多个关键节点依赖未发表的自身工作来支撑论述。例如，STCRpy的功能描述和FTCRDab的生成过程均无对应发表文献或预印本引用；IMMREP25初步实验（21/30靶标肽识别）被描述为"brief experiment"但无方法细节。这使得读者无法区分哪些论断有同行评议支撑，哪些仅为作者个人经验。
- **Why it matters** 视角性综述的价值部分在于其可信度。未发表结果的引用应明确标注并说明其局限性，否则读者可能将初步结果误认为已确立的领域共识。
- **Resolution test** 对每处未发表工作明确标注"unpublished data"或"personal communication"，并提供足够的实验细节（样本量、方法、统计显著性）供读者评估；或引用已发表的预印本/同行评议文献替代。

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** 文中声称IMMREP25是"首次"结构信息被多个团队用于特异性预测的竞赛，且多个参赛队伍"实现了统计显著的AUC0.1改进"，但未提供具体数值范围、参赛队伍数量或比较基准。
- **Evidence pointer** Section 4.3
- **Concern** IMMREP25结果的描述过于简略。作者提到"14/15的改进提交包含结构信息"和"最高AUC0.1为0.601"，但未说明这些结果的统计检验方法、与基线比较的具体方式，以及"结构信息"的具体定义（是预测结构还是实验结构？）。此外，作者声称"等待方法论文发表"但未提供任何引用。
- **Why it matters** IMMREP25是文中论证"结构方法正在改善特异性预测"的关键证据。如果该论断缺乏可验证的细节，读者无法判断这是领域趋势还是个别案例。
- **Resolution test** 补充IMMREP25的详细结果描述，包括参赛方法概览、统计检验方法、基线定义，以及引用已发表的竞赛总结报告（如有）。

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Balance
- **Claim pointer** 文中对TCR特异性预测的讨论主要聚焦于结构方法，对序列方法的进展和局限性着墨较少。
- **Evidence pointer** Section 4.3
- **Concern** 综述在讨论特异性预测时，将结构方法作为主要叙事线，但对序列基方法的现状（如GLIPH、TCRdist等）及其与结构方法的比较讨论不足。作者提到"序列方法难以泛化到未见抗原"，但未提供具体证据或引用支持这一论断。
- **Why it matters** 视角性综述的价值在于提供平衡的领域图景。如果读者无法了解序列方法的现状和挑战，可能高估结构方法的相对优势。
- **Resolution test** 增加一段对序列基特异性预测方法的简要综述，包括其代表性工具、性能基准和已知局限，并明确说明结构方法相对于序列方法的增量价值。

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.2.5 标题和内容
- **Evidence pointer** Section 4.2.5
- **Issue** 该节标题为"Deep Learning Models That Jointly Predict the TCR and pMHC Complex"，但内容同时涵盖了AlphaFold2/3等通用模型和TCR特异性模型（TCRmodel2、TCRdock、tFold-TCR），标题可能误导读者认为所有讨论的模型均为TCR特异性。
- **Required correction** 考虑将标题改为"Deep Learning Models for TCR:pMHC Complex Prediction"或明确区分通用模型与TCR特异性模型。

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** 术语使用
- **Evidence pointer** 全文
- **Issue** 文中交替使用"TCR:pMHC"和"pMHC:TCR"两种顺序，虽不影响理解，但建议统一以保持一致性。
- **Required correction** 统一使用"TCR:pMHC"（与标题和多数文献一致）。

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 5.3.2
- **Evidence pointer** Section 5.3.2
- **Issue** 对TCR设计方法的讨论中，作者提到"Bits to Binders"竞赛的命中率范围（0.6%-38.4%），但未说明该竞赛是否涉及TCR或TCRm设计，可能造成读者混淆。
- **Required correction** 明确说明该竞赛的靶标类型，或将其与TCR/TCRm设计的关联性解释清楚。

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 4.1.3
- **Evidence pointer** Section 4.1.3
- **Issue** 关于CDR3α结构多样性的讨论中，作者提到"CDR3α loop structures showing little tendency to cluster into canonical forms"，但未提供与CDR3β的定量比较（如聚类分析的具体指标）。
- **Required correction** 补充定量比较数据（如聚类数、簇内RMSD分布等），或引用已发表的比较分析。

## Risk / unsupported claims
- 文中声称"结构信息在IMMREP25中被多个团队使用并实现统计显著的泛化改进"，但未提供可验证的竞赛结果细节或引用。
- 作者自身未发表的初步实验（Protenix预测IMMREP25数据集中21/30靶标肽）被用作结构方法有效性的证据，但无方法细节和统计检验。
- 文中对STCRpy和FTCRDab的功能描述和性能声明无对应发表文献支撑。
- 声称"TCR:pMHC复合物预测的准确性是特异性推断的关键限制因素"缺乏直接比较证据。
- 对序列基特异性预测方法的局限性讨论缺乏具体引用和定量支撑。