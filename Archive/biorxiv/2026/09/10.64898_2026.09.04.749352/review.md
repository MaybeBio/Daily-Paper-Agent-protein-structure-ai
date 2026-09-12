## Review setup
- **Input scope** 完整手稿（含摘要、正文、附录 A–D）
- **Assessment boundary** 仅基于提供的材料进行评审，不涉及外部数据或未提供的补充信息
- **Shared manuscript claim summary** 作者提出 Atlas 模型家族，包括 AtlasLM-3B（约 30.6 亿参数的蛋白质语言模型）、AtlasFold（单链全原子结构预测模型）和 AtlasFold-M（复合物预测模型）。核心主张包括：(1) AtlasLM-3B 在无监督接触预测上优于同规模 ESM2-3B；(2) AtlasFold 在 CAMEO22、CASP14 和 CASP15 上达到 PLM 基折叠模型的 SOTA 精度；(3) AtlasFold-M 在抗体–抗原预测上可与 AlphaFold3 和 ESMFold2 相比；(4) 模型支持快速、内存高效推理和批处理。
- **Visible evidence base** 摘要、正文第 1–3 节、附录 A–D（含训练细节、评估协议、计算 profiling 表）、图 1–9 的引用、表 1–16 的引用
- **Missing materials affecting confidence** 图 1–9 和表 1–16 的实际数据值未在文本中提供；附录中多处公式（单体目标函数、置信度损失、多聚体损失）以占位符形式出现，未给出具体数学表达式；FoldBench 基准的详细定义和与 AlphaFold3/ESMFold2 的统计显著性检验未报告；代码仓库链接已提供但未在评审范围内审查

## Reviewer
- **Overall assessment** 该手稿描述了一个开放且可训练的蛋白质结构预测系统，覆盖从语言模型预训练到单体和复合物预测的完整流程。技术路线清晰，工程贡献扎实，特别是对 AlphaFold3 架构的蛋白质特化简化以及长度自适应扩散步数的设计具有实用价值。然而，当前版本存在若干关键问题：核心性能对比缺乏统计显著性报告，部分训练细节和损失函数公式缺失，IDR 幻觉分析停留在描述层面，且与 AlphaFold3/ESMFold2 的对比在计算公平性上需要进一步澄清。总体而言，这是一个有潜力的系统贡献，但当前证据不足以完全支撑"PLM 基折叠模型 SOTA"和"抗体–抗原预测与 AlphaFold3 相当"的核心主张。
- **Who would be interested in the results, and why** 计算结构生物学和蛋白质设计领域的研究者会关注此工作，特别是那些对 PLM 基折叠方法感兴趣、希望避免 MSA 搜索开销的团队。此外，关注模型可解释性（如 IDR 幻觉分析）和高效推理（如批处理吞吐）的工程导向实验室也会感兴趣。开放源码和 MIT 许可的发布策略可能吸引希望在自有数据上微调或扩展模型的用户。
- **Major strengths** 1) 系统完整性：从语言模型到折叠再到复合物的全流程开放实现，具有较高的工程参考价值。2) 推理效率：长度自适应扩散步数和蛋白质特化架构在速度和内存上展示了明确优势。3) 诚实的技术报告：作者明确报告了 AtlasFold-M 在 P–P 子集上低于其他方法，以及 ESMFold2 在训练集暴露下仍未超越 AlphaFold2 的观察，这种透明度值得肯定。4) 消融和开发过程的记录（第 3 节）为社区提供了有价值的实践知识。
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** 统计严谨性
- **Claim pointer** "AtlasFold achieves state-of-the-art accuracy among PLM-based folding models"（摘要及第 2.2 节）
- **Evidence pointer** 表 1（数值未在文本中提供）
- **Concern** 手稿声称 AtlasFold 在 CAMEO22、CASP14 和 CASP15 上是 PLM 基折叠模型的 SOTA，但未提供任何统计显著性检验（如配对 bootstrap 或 Wilcoxon 检验）来支持这一主张。表 1 的数值未在文本中展示，无法评估差异幅度。此外，CASP14 和 CASP15 的测试集规模较小（n=70 和 n=56），均值差异可能不显著。
- **Why it matters** "SOTA" 是一个强主张，需要统计支持。若无显著性检验，读者无法判断 AtlasFold 与 ESMFold、SimpleFold 等方法的差异是否在噪声范围内。这直接影响该主张的可信度和可复现性。
- **Resolution test** 在修订稿中提供表 1 的完整数值，并对 CAMEO22、CASP14、CASP15 上的主要指标（如 TM-score、lDDT）进行配对显著性检验，报告效应量和置信区间。

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** 方法可复现性
- **Claim pointer** 附录 B 和 C 中描述的损失函数和训练目标
- **Evidence pointer** 附录 B.2.2（单体目标函数）、附录 C（多聚体损失），公式以占位符形式出现
- **Concern** 多个关键损失函数公式在附录中以空占位符呈现（如单体目标函数、置信度损失、多聚体损失），未给出具体数学表达式。这使得训练流程无法被独立复现，也阻碍了审稿人评估损失设计是否合理。
- **Why it matters** 可复现性是计算生物学方法论文的基本要求。损失函数是模型训练的核心组件，缺失公式意味着其他团队无法验证或扩展该方法，也削弱了"开放和可训练"这一核心卖点。
- **Resolution test** 在附录中补全所有损失函数的完整数学定义，包括各项的权重、掩码策略和边界条件。

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** 对比公平性
- **Claim pointer** "AtlasFold-M achieves success rates of 46.96% and 63.36% on the antibody–antigen and protein–protein subsets, respectively"（第 2.3 节）
- **Evidence pointer** 图 5、附录 C.3.2
- **Concern** AtlasFold-M 与 AlphaFold3、ESMFold2 的对比中，计算资源、推理设置和训练数据可能存在差异。例如，AlphaFold3 使用 MSA 输入，而 AtlasFold-M 不使用；ESMFold2 使用 60 亿参数的 ESMC-6B，而 AtlasFold-M 基于 30 亿参数的 AtlasLM-3B。手稿未讨论这些差异对性能对比的影响。此外，图 5 的误差棒仅反映种子组合的变异性，未包含模型初始化的变异性。
- **Why it matters** 公平对比是性能主张的基础。如果对比条件不一致，读者无法判断性能差异来自模型架构、数据规模还是推理设置。这影响对 AtlasFold-M 实际能力的评估。
- **Resolution test** 在方法部分明确列出所有对比模型的输入设置、推理超参数和计算资源，并讨论这些差异对结论的潜在影响。如可能，补充在相同计算预算下的对比实验。

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** 分析深度
- **Claim pointer** "These packed conformations resemble those produced by diffusion models, suggesting that this hallucination is not specific to diffusion-based coordinate generation"（第 2.5 节）
- **Evidence pointer** 图 8
- **Concern** IDR 幻觉分析仅基于两个示例（CAID2 目标 DP02376 和 7F60 核孔复合物），且结论停留在定性描述层面。作者观察到 ESMFold（使用 IPA 而非扩散）也产生 packed 构象，但未量化 packed 程度、未在不同模型间系统比较、也未分析 packed 构象对下游功能预测的影响。
- **Why it matters** 幻觉行为是扩散基折叠模型的一个已知问题，作者有机会提供更系统的分析。当前证据不足以支撑"幻觉不特定于扩散架构"这一结论，因为两个示例的统计效力有限。
- **Resolution test** 在更大规模的 IDR 数据集上量化 packed 构象的频率和程度，比较不同架构（扩散 vs IPA）的幻觉倾向，并报告统计检验结果。

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** 数据披露
- **Claim pointer** 附录 A 中描述的 AtlasLM 预训练数据组成
- **Evidence pointer** 附录 A、表 3
- **Concern** 预训练数据的具体组成（UniRef、MGnify、MetaClust 的版本、去重策略、采样比例）在附录中仅以表格形式列出，但未提供数据版本号、处理管线的具体参数或数据过滤的详细规则。此外，表 3 的数值未在文本中展示。
- **Why it matters** 数据组成直接影响模型性能和泛化能力。缺乏数据版本和处理细节使得其他团队难以复现预训练过程，也影响对 AtlasLM 与 ESM2/ESMC 对比的解读。
- **Resolution test** 在附录中提供数据版本号、处理管线的完整描述、过滤规则和最终数据规模。

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** 表述清晰度
- **Affected element** 第 2.2 节中关于 ESM2-15B 和 ESMC 模型的对比描述
- **Evidence pointer** 第 2.2 节、图 2
- **Issue** 手稿提到 AtlasLM-3B 在 P@L 和 P@L/5 上优于 ESM2-15B 和 ESMC-300M/600M，但未解释为何选择这些特定模型作为对比基线，也未讨论与 ESM2-650M 或 ESM2-35B 等更直接规模匹配的对比。
- **Required correction** 补充对比模型选择的理由，并考虑增加与 ESM2-650M 和 ESM2-15B 的规模匹配讨论。

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** 结果呈现
- **Affected element** 第 2.4 节推理性能对比
- **Evidence pointer** 图 6、图 7、表 11–16
- **Issue** 推理性能对比中，未明确说明所有模型是否在同一 GPU 上、使用相同精度（FP32/FP16/BF16/FP8）运行。不同精度对速度和内存影响显著。
- **Required correction** 在附录 D 中明确列出所有对比模型的精度设置、GPU 型号和软件版本。

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** 引用完整性
- **Affected element** 第 1 节引言中的相关文献引用
- **Evidence pointer** 第 1 节
- **Issue** 引言部分对 PLM 基折叠方法的综述不够全面，未引用一些近期相关工作（如 ESM3 的后续应用、其他 metagenomic PLM 如 ProGen2 等），可能影响读者对领域现状的把握。
- **Required correction** 补充近期相关工作的引用，特别是与 metagenomic 数据训练 PLM 相关的研究。

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** 术语一致性
- **Affected element** 全文
- **Evidence pointer** 多处
- **Issue** "state-of-the-art" 的使用不一致，有时指 PLM 基方法中的最优，有时可能被误解为所有方法中的最优。建议明确限定范围。
- **Required correction** 在首次使用时明确 "state-of-the-art among PLM-based methods" 或 "state-of-the-art overall"。

- **Technical failings that need to be addressed before the case is established** R1-M1（统计显著性缺失）、R1-M2（损失函数公式缺失）、R1-M3（对比公平性未讨论）
- **Assessment against Nature-style criteria** 
  - **Originality** 中等。将 metagenomic 规模 PLM 与 AlphaFold3 衍生折叠架构结合并非全新概念，但蛋白质特化简化和长度自适应扩散步数具有一定新意。IDR 幻觉分析提供了有价值的观察，但深度不足。
  - **Scientific importance** 中等偏高。PLM 基折叠方法是一个活跃方向，开放实现和高效推理具有实际价值。然而，性能优势的统计证据不足，限制了其科学影响力的确立。
  - **Interdisciplinary readership** 中等。计算结构生物学和蛋白质设计领域会关注，但对更广泛的生物学家群体吸引力有限，除非性能优势被更清晰地证明。
  - **Technical soundness** 存在明显缺口。损失函数公式缺失、统计检验缺失、对比公平性未讨论，这些是技术严谨性的基本要求。
  - **Readability for nonspecialists** 较好。正文结构清晰，图表引用合理，但附录中的技术细节对非专业读者可能过于密集。摘要和引言对背景的铺垫充分。
- **Recommendation posture** 目前证据不足以完全支撑核心主张。建议大修后重新考虑。作者需补全损失函数公式、提供统计显著性检验、澄清对比公平性，并考虑加强 IDR 幻觉分析的系统性。若这些技术问题得到解决，该工作有潜力成为 PLM 基折叠领域的有价值贡献。

## Risk / unsupported claims
- "AtlasFold achieves state-of-the-art accuracy among PLM-based folding models" — 缺乏统计显著性检验和表 1 的完整数值，当前不可评估。
- "AtlasFold-M's antibody–antigen prediction performance is comparable to that of AlphaFold3 and ESMFold2" — 图 5 的数值未在文本中提供，且对比条件未充分说明，当前不可评估。
- "AtlasLM-3B outperforms ESM2-3B on both P@L and P@L/5" — 图 2 的数值未在文本中提供，且未报告显著性检验，当前不可评估。
- "These packed conformations resemble those produced by diffusion models, suggesting that this hallucination is not specific to diffusion-based coordinate generation" — 仅基于两个示例，统计效力不足，属于薄弱支持。
- 附录 B 和 C 中的损失函数公式以占位符形式出现，相关训练目标无法评估。
- 表 1–16 的所有数值均未在文本中展示，所有定量对比主张均无法独立验证。