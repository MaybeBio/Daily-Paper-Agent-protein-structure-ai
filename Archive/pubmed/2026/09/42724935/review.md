## Review setup
- **Input scope** 摘要（protocol 描述）
- **Assessment boundary** 仅评估摘要所呈现的方法学逻辑、可复现性声明与适用性描述；不评估完整 protocol 的逐步操作细节
- **Shared manuscript claim summary** 作者提出 HuDiff 是一种自适应自回归扩散方法，仅以 CDR 序列为输入即可从零生成人源化抗体和纳米抗体，无需人源模板；采用两阶段训练（人源抗体序列预训练 + 目标物种序列微调，以 humanness scores 引导）；HuDiff-Ab 同时处理重轻链，HuDiff-Nb 提供 inpainting 模式保留关键框架残基；可生成多个多样化候选供实验筛选
- **Visible evidence base** 摘要文本；无图、表、算法伪代码、超参数、数据集规模、评估指标或验证数据
- **Missing materials affecting confidence** 完整 protocol 正文、训练数据来源与规模、humanness score 定义与计算方式、模型架构细节、生成序列的验证结果（体外或体内数据）、与现有方法（如 CDR grafting、structure-based humanization）的对比基准

## Reviewer
- **Overall assessment** 摘要描述了一个具有潜在实用价值的抗体人源化生成框架，其「仅需 CDR 输入、无需人源模板」的核心主张若成立，将简化现有工作流程。然而，当前摘要提供的技术细节极为有限，无法评估方法的可实现性、创新程度或实际性能。作为 protocol 类稿件，其价值取决于步骤的完整性和可复现性，而摘要中这些信息基本缺失。建议在完整稿件中补充关键实现细节和验证数据后再作最终判断。

- **Who would be interested in the results, and why** 治疗性抗体和纳米抗体研发人员，特别是从事抗体工程、免疫原性降低和候选分子筛选的研究组；计算生物学和机器学习应用于蛋白质设计的研究者；以及关注 AI 驱动生物药物开发平台的工业界科学家。他们会对「仅需 CDR 输入即可生成人源化序列」这一简化流程感兴趣，因为它可能减少对结构数据和模板库的依赖。

- **Major strengths** 
  1. 核心主张明确且具有实际意义：仅以 CDR 为输入、无需人源模板，直接回应了传统人源化方法依赖模板匹配的瓶颈。
  2. 两阶段训练策略（人源预训练 + 目标物种微调）逻辑清晰，符合迁移学习在生物序列建模中的成熟范式。
  3. 区分 HuDiff-Ab 和 HuDiff-Nb 两种模式，并针对纳米抗体引入 inpainting 机制，显示了对不同抗体格式特殊性的考虑。
  4. 生成多个多样化候选的设计目标与实验筛选流程衔接合理，具有实际操作性。

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** 技术可实现性
  - **Claim pointer** 「HuDiff is an adaptive autoregressive diffusion approach that generates humanized antibodies and nanobodies from scratch using only complementarity-determining region sequences as input」
  - **Evidence pointer** 摘要全文；location not provided
  - **Concern** 摘要未提供任何关于「adaptive autoregressive diffusion」架构的具体描述。自回归模型与扩散模型的结合方式、自适应机制的具体含义、CDR 序列如何条件化生成过程，这些核心设计决策均未说明。作为 protocol 稿件，读者需要明确的架构定义才能复现。
  - **Why it matters** 如果架构描述不完整，protocol 无法被独立实施。此外，「adaptive」和「from scratch」的表述在当前描述下缺乏可验证的技术内涵，可能误导读者对方法复杂度和输入要求的理解。
  - **Resolution test** 在完整 protocol 中提供模型架构图、输入输出张量维度、CDR 序列编码方式、自回归与扩散组件的具体交互机制，以及「adaptive」的准确定义。

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** 可复现性
  - **Claim pointer** 「pretraining on human antibody sequences to learn framework region patterns, followed by fine-tuning on target-species sequences guided by humanness scores」
  - **Evidence pointer** 摘要全文；location not provided
  - **Concern** 摘要未提供预训练和微调数据集的具体来源、规模、物种范围或序列筛选标准。humanness score 的定义、计算方法和在训练中的具体引导方式（如损失函数加权、采样约束或后处理过滤）完全未说明。两阶段训练的超参数（学习率、训练轮数、批次大小等）也未提及。
  - **Why it matters** 对于 protocol 类稿件，数据获取和评分标准是复现的关键路径。缺少这些信息，读者无法判断训练数据的适用性，也无法评估 humanness score 是否客观反映免疫原性风险。
  - **Resolution test** 在 protocol 中列出数据来源（如 OAS、IMGT 等）、版本号、序列数量、物种组成、预处理流程；提供 humanness score 的数学定义或引用原始文献，并说明其在训练流程中的具体集成方式。

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** 性能验证
  - **Claim pointer** 「Generates multiple diverse humanized candidates for downstream experimental screening」
  - **Evidence pointer** 摘要全文；location not provided
  - **Concern** 摘要未提供任何生成序列的质量评估数据。没有 humanness score 的分布、与已知人源抗体的序列相似性、框架区残基保守性、CDR 结构完整性或功能活性（如抗原结合亲和力）的验证结果。也没有与现有方法（如 CDR grafting、Sapiens、BioPhi 等）的对比数据。
  - **Why it matters** 人源化的核心目标是降低免疫原性同时保留抗原结合活性。没有实验或计算验证，无法判断生成的「人源化」序列是否真正满足这两个要求。protocol 的价值取决于其输出是否可靠。
  - **Resolution test** 在稿件中提供至少一个案例研究：输入一组 CDR 序列，展示生成的人源化候选的 humanness score、与亲本抗体的序列比对、关键框架残基的保留情况，以及（如有）实验验证的亲和力或表达数据。

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** 方法适用性边界
  - **Claim pointer** 「HuDiff-Nb can incorporate a specialized inpainting mode to preserve critical nanobody framework residues」
  - **Evidence pointer** 摘要全文；location not provided
  - **Concern** 摘要未说明 inpainting 模式的具体触发条件、哪些残基被定义为「critical」、以及该模式与传统 CDR grafting 或结构引导设计有何本质区别。纳米抗体的人源化面临独特的框架区保守性问题，但摘要未提供针对这一挑战的解决方案细节。
  - **Why it matters** 纳米抗体因其小尺寸和 CDR3 长环结构而具有特殊的人源化难点。如果 inpainting 模式只是简单的残基掩码和重建，可能不足以解决框架区稳定性和 VHH 特异性残基（如 45e、47、103 等）的保留问题。
  - **Resolution test** 在 protocol 中明确 inpainting 模式的输入格式、掩码策略、关键残基的定义标准，并提供纳米抗体人源化的具体案例或基准测试。

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** 术语清晰度
  - **Affected element** 「adaptive autoregressive diffusion」
  - **Evidence pointer** 摘要第一段
  - **Issue** 「adaptive」一词在摘要中未定义，可能指架构自适应、训练策略自适应或生成过程自适应，含义模糊。
  - **Required correction** 在摘要或引言中明确「adaptive」的具体含义，或在完整稿件中首次出现时给出定义。

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** 输入要求
  - **Affected element** 「using only complementarity-determining region sequences as input」
  - **Evidence pointer** 摘要第一段
  - **Issue** 未说明 CDR 序列的格式要求（如是否包含 CDR1-3 全部、是否需标注种系来源、长度范围限制）以及是否支持单域抗体（VHH）的 CDR 输入。
  - **Required correction** 在 protocol 的输入数据格式部分明确 CDR 序列的规范、示例和边界情况。

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** 输出多样性
  - **Affected element** 「Generates multiple diverse humanized candidates」
  - **Evidence pointer** 摘要 Key features 第 4 条
  - **Issue** 未说明多样性的量化方式（如序列同一性阈值、聚类方法）或推荐生成数量。
  - **Required correction** 在 protocol 中提供多样性评估指标和推荐的候选数量范围。

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** 计算资源
  - **Affected element** 训练和推理流程
  - **Evidence pointer** 摘要全文；location not provided
  - **Issue** 未提及训练所需的 GPU 类型、显存需求、预计训练时间或推理速度，影响用户对资源需求的预判。
  - **Required correction** 在 protocol 的「设备要求」或「计算资源」部分补充硬件规格和运行时间估计。

- **Technical failings that need to be addressed before the case is established** R1-M1（架构定义缺失）、R1-M2（数据与评分标准未说明）、R1-M3（无性能验证数据）。这三项是 protocol 可复现性和方法可信度的基础，必须在完整稿件中解决。

- **Assessment against Nature-style criteria** 
  - **Originality** 中等。将扩散模型应用于抗体人源化并非全新概念，但「仅以 CDR 为输入、无需模板」的设定具有一定区分度。然而，摘要未提供与现有生成式人源化方法（如基于语言模型或扩散模型的方法）的差异化分析。
  - **Scientific importance** 中等偏高。抗体人源化是治疗性抗体开发的关键步骤，简化流程具有实际价值。但方法的最终重要性取决于生成序列的质量和实验验证结果，当前摘要无法支撑更高层级的科学贡献声明。
  - **Interdisciplinary readership** 中等。计算生物学、结构生物学和抗体工程领域的研究者可能感兴趣，但摘要的技术描述过于简略，难以吸引非专业读者。
  - **Technical soundness** 当前不可评估。核心架构、训练策略和验证方法均未提供足够细节，无法判断技术路线的合理性。
  - **Readability for nonspecialists** 尚可。摘要语言清晰，但「adaptive autoregressive diffusion」和「inpainting mode」等术语缺乏解释，可能阻碍非计算背景读者理解。

- **Recommendation posture** 目前无法从摘要材料中确认方法的可行性和价值。建议在收到完整 protocol 后重新评估。若完整稿件包含架构细节、数据来源、humanness score 定义和至少一个验证案例，则持支持态度；否则，当前证据不足以建立方法可信度。

## Risk / unsupported claims
- 「eliminating the need for preexisting human templates」：摘要未提供证据表明生成的人源化序列在免疫原性上等同于或优于模板依赖方法，该主张目前无支撑。
- 「adaptive」：未定义，无法评估其技术含义。
- 「guided by humanness scores」：humanness score 的定义和计算方式未提供，该训练引导机制不可评估。
- 「preserve critical nanobody framework residues」：未说明哪些残基被视为 critical 以及 inpainting 如何实现保护，该功能声明不可评估。
- 「Generates multiple diverse humanized candidates」：多样性未量化，候选质量未验证，该功能声明仅有方向性意义。