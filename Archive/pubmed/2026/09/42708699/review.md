## Review setup
- **Input scope** 全文（含摘要、引言、理论、结果与讨论、结论、方法、补充材料说明）
- **Assessment boundary** 仅基于所提供的手稿材料进行评估；未提供补充信息（SI）的具体内容、图1-6及表的具体数据
- **Shared manuscript claim summary** 作者提出一个全自动工作流程，将增强采样模拟（沿FRESEAN模式分析得到的低频振动模式作为CVs）产生的轨迹，通过加权动态交叉相关矩阵（DCCM）分析，自动提取域-域距离作为“人类可读”的CVs，并在五个蛋白体系（KRAS、HEWL、HIV-1 Pr、MCL-1、RBP）上验证该方法能重现已知构象状态。
- **Visible evidence base** 正文中的图1-5（图注描述）、方法学描述、KRAS的详细结果；其他四个蛋白的结果仅在SI中提及
- **Missing materials affecting confidence** 补充信息（SI）全文、图1-5的实际数据内容、统计误差的具体数值、与文献已知构象状态的定量比较

## Reviewer

- **Overall assessment** 该手稿提出了一种新颖且具有潜在广泛适用性的方法，将复杂的、难以解释的增强采样CVs转化为简单的几何距离变量。方法逻辑清晰，算法描述完整，KRAS案例展示具有说服力。然而，由于其他四个验证体系的详细结果仅在SI中，且正文缺乏定量比较，当前证据基础不足以完全确立该方法“普遍适用”的核心主张。方法学本身有坚实理论基础，但验证深度不足。

- **Who would be interested in the results, and why** 计算化学与生物物理领域的研究人员，特别是从事增强采样模拟、CV设计与蛋白质构象动力学研究的小组。对使用机器学习生成CVs的研究者尤其相关，因为该方法提供了一条将“黑箱”CVs转化为可解释几何变量的途径。此外，对构象系综生成和蛋白质功能机制研究感兴趣的实验与计算交叉团队也会关注。

- **Major strengths** 
  1. 方法设计巧妙且自动化程度高，解决了增强采样模拟中CVs可解释性差的真实痛点
  2. 加权DCCM分析在理论上正确，考虑了metadynamics偏置势的权重修正
  3. 算法伪代码和流程描述清晰，可复现性强
  4. 选择KRAS作为主要展示案例具有生物学意义，switch I/II区域的识别具有功能相关性
  5. 代码公开可用，符合可重复性要求

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** “We apply this method to five proteins, including KRAS and HIV-1 protease, and show that it consistently identifies biologically relevant domains and motions without prior system-specific knowledge.”
- **Evidence pointer** Results and Discussion, Figure 1-5, SI (Figure S1-S3)
- **Concern** 核心主张是方法在五个蛋白上“一致地”识别出生物学相关域和运动，但正文仅详细展示了KRAS的结果。其他四个蛋白（HEWL、HIV-1 Pr、MCL-1、RBP）的结果仅在SI中提及，且正文仅以文字描述（如“we correctly identify the moving parts of the α– and β-domains involved in the lid-opening of HEWL”）带过，缺乏定量证据。
- **Why it matters** “普遍适用性”是该方法的核心卖点。如果仅在一个体系上得到充分验证，读者无法判断该方法在其他蛋白上的表现是否同样可靠，也无法评估其局限性（如对特定蛋白大小、结构类型或动力学特征的依赖）。
- **Resolution test** 在正文或SI中提供所有五个蛋白的定量结果，包括：识别的域组成、与已知功能域的定量重叠度（如Jaccard指数或类似度量）、自由能面的统计误差、以及域-域距离与已知构象变化的对应关系。

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation against known states
- **Claim pointer** “Projection onto these distances produces free energy surfaces that reproduce known conformational states with low statistical uncertainty while maximizing independent dynamical information.”
- **Evidence pointer** Results and Discussion, Figure 5
- **Concern** 手稿声称自由能面“重现已知构象状态”，但未提供与文献中已知状态的定量比较。例如，KRAS的已知活性/非活性状态、HEWL的开放/闭合状态等，应以结构重叠、关键距离分布或与实验数据的直接对比来验证。目前仅凭视觉检查自由能面不足以支持“重现”这一强主张。
- **Why it matters** 如果新CVs生成的自能面与已知状态不对应，则该方法生成的“人类可读”变量可能具有误导性。定量验证是确立方法可靠性的必要条件。
- **Resolution test** 提供与已知构象状态的定量比较，如：将自由能面极小值对应的结构簇与已知晶体结构进行RMSD对比，或与实验测量的距离分布进行比较。

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological limitation
- **Claim pointer** “The latter is determined by error propagation from standard deviations and errors of the mean of the probability distributions obtained after weighting the configurations in independent metadynamics simulation trajectories as defined in Eq. 7.”
- **Evidence pointer** Theory, Eq. 7-8; Results and Discussion, Figure 5
- **Concern** 自由能面的统计误差仅来源于20个独立轨迹间的标准差。然而，metadynamics的收敛性还取决于偏置势填充速率、CVs是否充分描述慢自由度、以及模拟时间是否足够。手稿未讨论这些因素对自由能面可靠性的影响，也未提供收敛性分析（如偏置势随时间的变化、不同模拟时长的自由能面比较）。
- **Why it matters** 如果模拟未充分收敛，即使轨迹间标准差小，自由能面也可能系统性地偏离真实值。读者需要知道当前结果是否已达到收敛。
- **Resolution test** 提供收敛性分析，如偏置势随模拟时间的演化、将20条轨迹分为两组比较自由能面差异、或增加模拟时长验证结果稳定性。

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing methods
- **Claim pointer** “This workflow enables systematic recasting of complex CVs into simple geometric descriptors without loss of essential dynamics.”
- **Evidence pointer** Introduction, Conclusion
- **Concern** 手稿未与现有方法进行系统比较。例如，PCA或TICA本身就能提供可解释的运动模式；基于距离的CVs（如接触图、残基对距离）在增强采样中已有广泛应用。作者应说明该方法相比现有替代方案的独特优势，以及“不损失关键动力学信息”的定量依据。
- **Why it matters** 如果现有方法能达到类似效果且更简单，该方法的新颖性和实用价值将受到质疑。比较分析有助于读者判断何时应选择该方法。
- **Resolution test** 在至少一个体系上，将该方法提取的域-域距离与PCA/TICA主成分、或与文献中使用的几何CVs进行自由能面和信息含量（如互信息、重构精度）的定量比较。

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, 参数选择
- **Evidence pointer** Theory, “Alternative choices for the correlation threshold can alter the balance of inclusiveness or stringency in the selection of correlated residues. However this was not tested here.”
- **Issue** 相关性阈值（+0.5）的选择对域识别结果有直接影响，但作者未测试该参数的敏感性。
- **Required correction** 在SI中提供至少一个体系上不同阈值（如0.3、0.5、0.7）下的域识别结果比较，以证明方法对阈值选择不敏感或说明其影响。

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, KRAS分析
- **Evidence pointer** Figure 2, Figure 3
- **Issue** 正文提到“domain A1 for KRAS consists of two sets of amino acids (residues 33–37 and residues 60–61)”，但未解释为何这些残基在序列上分离却在结构上接触，以及这种非连续域在生物学上的意义。
- **Required correction** 增加一段简要讨论，解释非连续域的结构基础及其对功能的意义，帮助读者理解该方法的生物学输出。

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results and Discussion, 自由能面
- **Evidence pointer** Figure 5
- **Issue** 手稿提到“even states with free energies around +20 kJ/mol relative to the minimum feature statistical errors below 3 kJ/mol”，但未说明该误差估计是否已考虑metadynamics偏置势填充的不确定性。
- **Required correction** 明确说明误差传播的具体公式和假设，或引用标准方法。

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Conclusion
- **Evidence pointer** Conclusion, “we anticipate that such fully automated enhanced sampling protocols will play a critical role in the generation of extensive protein conformational ensembles”
- **Issue** 作者提到该方法可为机器学习模型提供训练数据，但未讨论该方法生成的系综与ML训练数据需求之间的匹配度（如多样性、覆盖度）。
- **Required correction** 增加一段简短讨论，说明该方法生成的系综在哪些方面适合作为ML训练数据，以及可能的局限性。

- **Technical failings that need to be addressed before the case is established** R1-M1（多体系验证不足）、R1-M2（缺乏定量验证）

- **Assessment against Nature-style criteria** 
  - **Originality** 方法本身具有新颖性，将DCCM分析与增强采样轨迹的加权处理结合，自动提取可解释的域-域距离，这一思路在文献中未见直接先例。但需注意，DCCM本身是成熟工具，创新点在于加权处理与自动域识别的结合。
  - **Scientific importance** 如果方法被充分验证，其重要性较高。增强采样模拟的CV可解释性是领域内的公认瓶颈，该方法提供了一条通用解决路径，对构象系综生成、功能机制研究和ML训练数据制备均有潜在影响。
  - **Interdisciplinary readership** 方法学属性较强，主要吸引计算化学/生物物理领域读者。对实验生物学家的吸引力取决于方法能否提供易于理解的构象描述，目前证据尚不充分。
  - **Technical soundness** 理论框架正确，加权DCCM的数学基础扎实。但验证深度不足（仅一个体系详细展示），且缺乏收敛性分析和与现有方法的比较，技术可靠性尚未完全确立。
  - **Readability for nonspecialists** 写作整体清晰，方法学描述易于理解。但KRAS案例的生物学意义讨论较简略，非计算背景读者可能难以评估结果的生物学相关性。

- **Recommendation posture** 目前证据不足以完全确立核心主张。方法学有潜力，但需要补充多体系定量验证、收敛性分析和与现有方法的比较。建议在作者补充这些内容后重新考虑。

## Risk / unsupported claims
1. “consistently identifies biologically relevant domains and motions” — 仅KRAS有详细证据，其他四个蛋白未在正文中展示定量结果，该“一致性”主张目前证据不足。
2. “reproduce known conformational states” — 缺乏与已知状态的定量比较，该主张目前不可评估。
3. “without loss of essential dynamics” — 未提供信息含量或动力学保真度的定量度量，该主张目前不可评估。
4. “maximizing independent dynamical information” — 未提供与替代CVs的信息独立性比较，该主张目前不可评估。
5. “fully automated” — 方法流程确实自动化，但“fully”的程度取决于是否需要人工检查域识别的生物学合理性，这一点未讨论。