## 01 基本信息
- **标题**: LM2KM: feature extraction from pretrained protein and molecular language models combined with quantum mechanics (QM) features for K(M) predictions
- **作者与单位**: Zhai, Jingchen; Cai, Lianjin; Niu, Taoyu; Xie, Lei; Wang, Junmei（单位未提供，据致谢推测含 University of Pittsburgh）
- **期刊/预印本平台**: Digital Discovery
- **年份**: 2026-11-03
- **论文类型**: 方法学研究（系统评估 + 预测模型构建）
- **领域**: 酶动力学参数预测（KM） × 蛋白质/分子语言模型 × 量子力学描述符
- **关键词**: Michaelis constant (KM), protein language models, molecular language models, quantum mechanics descriptors, enzyme kinetics, PBPK
- **DOI/arXiv 号**: 10.1039/d6dd00139d
- **代码**: 提供（Jupyter Notebook/IPYNB，Zenodo: https://doi.org/10.5281/zenodo.23020002）
- **数据**: 提供（PKL 格式，含 20,462 条 KM 记录及嵌入特征）
- **阅读日期**: 2026-11-03（检索日期）
- **在课题方向中的位置**: 该文属于「蛋白质结构相关计算研究 × AI 方法」中酶动力学参数（KM）预测方向，核心创新在于系统比较多种预训练蛋白质语言模型（PLM）和分子语言模型（MLM）的嵌入特征，并首次将量子力学（QM）描述符与语言模型特征融合用于 KM 预测。与结构预测（AlphaFold 类）不同，本文聚焦序列-功能映射，但其中 PLM 特征提取策略、滑动窗口处理长序列、PCA 降维、QM 特征融合等思路可迁移至结构相关任务（如突变效应预测、底物特异性分析）。

## 02 一句话总结
本文构建 LM2KM 框架，系统评估 4 种 PLM 与 2 种 MLM 的嵌入特征组合用于 KM 预测，发现 ProtT5 最后四层平均嵌入（70 PCs）+ MolFormer CLS 嵌入（20 PCs）+ QM 描述符的组合达到 R²=0.537，且模型对未见分子和蛋白序列具有泛化能力。

## 03 研究问题
- **具体问题**: 如何从蛋白质序列和底物分子结构（SMILES）中提取有效特征，实现高精度、可泛化的 KM 预测？
- **为什么重要**: KM 是酶-底物亲和力的关键参数，对酶动力学建模、PBPK 药物开发、代谢通路识别至关重要。实验测定 KM 耗时费力，计算预测可大规模补充数据缺口。
- **现有方法不足**: (1) 传统 QSAR 依赖手工描述符，缺乏序列上下文信息；(2) 已有 ML 方法多基于 EC 编号进行数据划分，忽略了同一序列对应多个 EC 注释的歧义问题；(3) 语言模型嵌入维度高、冗余大，直接用于回归易过拟合；(4) 缺乏对 PLM/MLM 组合及特征维度的系统比较；(5) QM 描述符虽能反映反应性，但鲜有与语言模型特征融合的研究。
- **精确研究问题**: Can pretrained protein and molecular language model embeddings, when systematically combined with QM descriptors and optimized feature dimensionality, achieve competitive KM prediction performance with generalizability to unseen molecules and protein sequences?

## 04 背景与发展脉络
（标注：以下脉络主要基于本文 Introduction 和 Discussion 的叙述框架，部分经外部核验标注）

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 物理模拟时代 | QM/MM 计算活化自由能，过渡态理论推导 KM | 机理明确 | 计算昂贵，难以大规模应用 | 本文保留 QM 描述符作为补充特征 |
| 经典 QSAR | 分子描述符 + 回归/统计模型 | 计算快，可解释 | 缺乏序列上下文，泛化差 | 本文以语言模型嵌入替代手工描述符 |
| 早期 ML | 手工特征 + 随机森林/SVM 等 | 比 QSAR 灵活 | 特征工程依赖专家知识 | 本文采用集成树（bagged trees）作为回归器 |
| 深度学习时代 | GNN、DNN 直接学习分子/序列表示 | 自动特征提取 | 数据需求大，可解释性差 | 本文利用预训练语言模型避免从头训练 |
| 预训练语言模型 | ProtT5, ESM-2, ProtBERT, Ankh (PLM); ChemBERTa, MolFormer (MLM) | 捕获序列/分子深层语义 | 嵌入维度高，需降维；不同模型适用性未明 | 本文系统比较 4 PLM × 2 MLM 组合 |
| 混合特征（本文） | PLM + MLM + QM 描述符 + PCA 降维 + 集成树 | 兼顾序列、结构、电子反应性 | QM 计算成本高；未建模酶-底物相互作用 | 本文核心贡献 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| KM 实验测定成本高 | 大量酶-底物对缺乏 KM 数据 | 实验耗时费力，尤其早期药物发现阶段 | Introduction: "experimental measurement of KM is labor-intensive and often unavailable" |
| 现有预测方法精度有限 | 已发表模型 R² 约 0.50 | 特征表示不充分，或数据划分不合理 | Discussion: "Other published single-task KM prediction models typically report R2 values around 0.50" |
| EC 编号歧义导致数据噪声 | 同一序列对应多个 EC 注释 | 以 EC 而非序列定义数据唯一性 | Introduction: "a single protein sequence may be associated with multiple EC numbers" |
| 语言模型嵌入维度高 | 原始嵌入数千维，直接回归易过拟合 | PLM/MLM 输出为高维稠密向量 | Methods: "PCA was applied to each set of model outputs" |
| 长序列超出模型输入限制 | 部分蛋白序列超过 PLM 最大长度 | 模型架构固定输入窗口 | Methods: "overlapped sliding-window strategy was applied" |
| QM 计算成本高 | 部分分子 QM 优化不可行 | 大分子或柔性分子几何优化昂贵 | Results: "A subset (n = 20,002) was constructed by removing molecules whose QM calculations were computationally prohibitive" |

## 06 核心思想

**1) 表面方法**：
构建 LM2KM 流水线：输入蛋白序列和底物 SMILES → 分别通过 PLM 和 MLM 提取嵌入 → 对长序列用滑动窗口处理 → PCA 降维至 20/60/70 PCs → 拼接 PLM + MLM（+ 可选 QM）特征 → 训练集成袋装树（ensemble bagged trees）回归模型 → 输出 log2(KM) 预测值。

**2) 核心洞察**：
- **特征互补性**：PLM 捕获蛋白序列的进化与结构语义，MLM 捕获底物分子的化学语义，QM 描述符补充电子反应性信息，三者互补而非替代。
- **维度不对称性**：蛋白特征需要更高维度（60-70 PCs）才能充分表征，而分子特征在较低维度（20 PCs）即达饱和，反映两类生物分子信息复杂度的本质差异。
- **序列级而非 EC 级数据划分**：以蛋白序列唯一性定义数据，避免同一序列多 EC 标签造成的训练/测试泄漏。
- **QM 的增量价值**：QM 描述符（尤其硬度/软度）提供语言模型无法直接编码的电子结构信息，且预计算的非线性变换比原始 HOMO/LUMO 更利于树模型利用。

**3) 可能的普适教训 [Analysis]**：
- 预训练语言模型嵌入并非「即插即用」，需要针对下游任务做维度选择和层选择（如 ProtT5 最后四层优于最后一层）。
- 物理化学描述符（如 QM）与深度表示学习并非对立，融合可带来稳健增益，尤其在数据量有限时。
- 数据划分粒度（序列级 vs 注释级）对模型评估的公平性影响可能大于模型选择本身。

## 07 方法总览

**输入**: 蛋白氨基酸序列（FASTA）、底物 SMILES 字符串、KM 实验值（log2 变换）

**输出**: log2(KM) 回归预测值

**模块**:
1. **数据模块**: BRENDA 数据库提取 → 序列级去重 → SMILES 标准化（InChIKey 映射）→ log2 变换
2. **蛋白嵌入模块**: 4 种 PLM（ProtT5, ESM-2, ProtBERT, Ankh），长序列用滑动窗口（510 aa, step 256）
3. **分子嵌入模块**: 2 种 MLM（ChemBERTa, MolFormer），提取 CLS token 或池化嵌入
4. **降维模块**: PCA 保留 Top 20/60/70 PCs
5. **QM 模块**: Gaussian 16 在 ωB97XD/6-31G* 水平优化几何，计算 HOMO/LUMO 衍生 8 个全局反应性描述符
6. **回归模块**: 集成袋装树（ensemble bagged trees），对 top/bottom 10% 数据加权

**训练**: 固定随机种子划分训练/测试集；5 次独立实验（不同随机种子）评估稳定性；配对 t 检验比较模型差异

**工具**: Python（实现）、MATLAB（初步筛选）、Gaussian 16（QM 计算）

**假设**:
- KM 的 log2 变换近似正态分布
- 蛋白序列和底物结构信息足以预测 KM（无需显式 3D 结构）
- QM 描述符在 ωB97XD/6-31G* 水平足够表征反应性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| 序列级去重 | 以蛋白序列而非 EC 编号定义唯一性 | 避免同一序列多 EC 标签造成数据泄漏 | 输入: 55,965 原始记录；输出: 20,462 唯一序列-底物对 | Introduction: "protein uniqueness was defined at the amino acid sequence level" | 若移除，模型可能因训练/测试重叠而虚高 R² |
| 滑动窗口 | 处理超过 PLM 输入限制的长序列 | PLM 有固定最大长度（如 510 aa） | 输入: 长蛋白序列；输出: 重叠窗口嵌入的平均 | Methods: "overlapped sliding-window strategy" | 若移除，长序列蛋白无法编码或信息丢失 |
| PCA 降维 | 压缩高维嵌入至 20-70 维 | 原始嵌入数千维，直接回归易过拟合 | 输入: PLM/MLM 原始嵌入；输出: Top PCs | Results 图 4: PCA 收敛分析 | 若移除，模型性能下降（过拟合）或计算成本剧增 |
| QM 描述符 | 补充电子反应性信息 | 语言模型不直接编码电子结构 | 输入: 优化后分子几何；输出: 8 个全局描述符 | Results 图 7: QM 一致提升性能 | 若移除，R² 下降（文中报告 QM 带来显著增益） |
| 集成袋装树 | 回归预测 log2(KM) | 对高维稀疏特征稳健，可处理非线性 | 输入: 拼接特征向量；输出: 预测值 | Methods: "ensemble bagged trees achieved the best performance" | 若替换为线性模型，可能无法捕获非线性关系 |
| 加权策略 | 对 top/bottom 10% KM 值加权 | KM 分布集中在中部，尾部样本稀疏 | 输入: 训练样本及权重；输出: 加权损失 | Methods: "additional weights were assigned to the top and bottom 10%" | 若移除，尾部预测精度可能下降 |

## 09 关键公式符号

**1) KM 对数变换**:
\[
y = \log_2(K_M)
\]
- \( y \): 模型预测目标（log2 尺度）
- \( K_M \): Michaelis 常数（实验值）

**2) 电离能/电子亲和能近似**:
\[
IP \approx -E_{\text{HOMO}}
\]
\[
EA \approx -E_{\text{LUMO}}
\]
- \( IP \): 电离能
- \( EA \): 电子亲和能
- \( E_{\text{HOMO}} \): 最高占据分子轨道能量
- \( E_{\text{LUMO}} \): 最低未占分子轨道能量

**3) 决定系数 R²**:
\[
R^2 = 1 - \frac{\sum_{i=1}^{n}(y_i^{\text{obs}} - y_i^{\text{pred}})^2}{\sum_{i=1}^{n}(y_i^{\text{obs}} - \bar{y})^2}
\]
- \( n \): 样本数
- \( y_i^{\text{obs}} \): 第 i 个样本的观测 log2(KM)
- \( y_i^{\text{pred}} \): 第 i 个样本的预测值
- \( \bar{y} \): 观测值均值

**4) 均方根误差 RMSE**:
\[
RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i^{\text{obs}} - y_i^{\text{pred}})^2}
\]

**5) 全局反应性描述符**（由 HOMO/LUMO 衍生）:
- 化学势: \( \mu = (E_{\text{HOMO}} + E_{\text{LUMO}})/2 \)
- 化学硬度: \( \eta = (E_{\text{LUMO}} - E_{\text{HOMO}})/2 \)
- 化学软度: \( S = 1/(2\eta) \)
- 亲电指数: \( \omega = \mu^2/(2\eta) \)
- 供电子/受电子能力等（文中未给出完整公式，以上为标准定义）

## 10 实验设计与证据链

**数据集**: BRENDA 数据库（2025 年 1 月检索），55,965 条原始记录 → 序列级去重后 20,462 条唯一蛋白-底物对；QM 子集 20,002 条

**特征集**: 10 种蛋白特征（4 PLM × 多种提取策略）+ 4 种分子特征（2 MLM × CLS/pooled）

**基线**: 无明确外部基线，内部比较为「无 QM 特征」的对应模型

**评测协议**: 固定随机种子划分；5 次独立实验（不同种子）；配对 t 检验；R² 和 RMSE 指标

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| PCA 收敛分析 | 不同 PLM/MLM 嵌入的固有维度不同 | 各特征集累计方差 vs PC 数 | ProtBERT 收敛最快（1-2 PCs 达 90%）；ProtT5_last1/ESM2_cls 等需 ~200 PCs | 不同模型信息冗余度差异大 | 未直接证明最优 PC 数 = 90% 方差所需数 | Results 图 4 |
| PLM-MLM 组合评估 | 存在最优 PLM-MLM 组合 | 穷举 4 PLM × 2 MLM × 2 维度 | ProtT5_last4 + MolFormer_cls 最优 | 模型选择影响显著 | 未证明该组合在所有数据集上最优 | Results 图 5, S1, S2 |
| 维度不对称性 | 蛋白需更高维度，分子低维度即饱和 | 20 vs 60 PCs 对比 | 蛋白 60 PCs > 20 PCs；分子 20 PCs 已足够 | 两类特征信息复杂度不同 | 未系统扫描中间维度 | Results 图 5, 6 |
| QM 特征贡献 | QM 描述符提升预测性能 | 有/无 QM 特征对比 | 所有维度下 QM 均带来显著提升（p=0.0084, 0.0077） | QM 提供互补信息 | 未证明 QM 对极端值（outliers）的改善 | Results 图 7, 表 2, 3 |
| 单描述符分析 | 硬度/软度贡献最大 | 逐一添加 8 个 QM 描述符 | 硬度、软度提升最显著 | 电子结构信息对 KM 预测有价值 | 未分析描述符间交互 | Results 图 9 |
| 泛化性评估 | 模型对未见分子/序列有效 | 按分子/序列新颖性分层评估 | 未见分子和序列的预测性能与总体相当 | 模型未严重依赖记忆 | 未测试跨物种/跨酶家族泛化 | Results 图 8 |
| 基准对比 | LM2KM 与已发表方法可比 | KmPred 基准（相同划分） | R²=0.509 vs KmPred R²=0.51 | 性能与 SOTA 相当 | 未证明显著优于 SOTA | Discussion |

## 11 结论正确解读

- **任务范围**: 仅限 KM 预测，不涉及 Kcat、催化效率等其它动力学参数；输入为序列+SMILES，不依赖 3D 结构。
- **Oracle/真值输入**: 使用 BRENDA 实验 KM 值，经 log2 变换；QM 描述符来自 DFT 计算（ωB97XD/6-31G*），非实验测量。
- **端到端状态**: 非端到端——特征提取（PLM/MLM/QM）与回归模型（袋装树）分离，特征提取器未针对 KM 任务微调。
- **算力成本**: QM 计算是主要瓶颈（20,002 个分子的 DFT 优化），语言模型推理成本中等；训练成本低（袋装树）。
- **历史数据依赖**: 训练数据来自 BRENDA（截至 2025 年 1 月），存在数据库偏差（如对模式生物、常见底物偏置）。
- **模型依赖**: 袋装树为非线性模型，对特征缩放不敏感，但无法外推到训练分布之外；特征选择（PCA）在训练集上完成，存在轻微信息泄漏风险。
- **最难情形**: 多蛋白复合物体系（1,556 条记录涉及多蛋白）可能更难预测，文中未单独分析。
- **群体/领域边界**: 模型适用于序列-底物对，不适用于 apo 酶或非代谢底物；QM 特征仅对可优化几何的小分子有效。
- **不确定性**: 文中未报告预测区间或置信度估计；R²=0.537 意味着仍有约 46% 方差未解释。
- **有边界的复述**: LM2KM 在 BRENDA 来源的 20,462 条 KM 数据上，通过系统比较 4 PLM × 2 MLM 组合，确定 ProtT5_last4（70 PCs）+ MolFormer_cls（20 PCs）+ QM 描述符为最优特征配置，R²=0.537；在 KmPred 公共基准上 R²=0.509，与当前 SOTA 相当；模型对未见分子和序列具有泛化能力，但 QM 计算成本限制了大规模应用。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 未显式建模酶-底物相互作用 | 模型分别编码蛋白和分子，未捕捉二者互作模式 | 探索蛋白-配体交互指纹等描述符 | Discussion: "do not explicitly capture variations in KM arising from enzyme-substrate interactions" |
| QM 描述符未直接表征反应机理 | QM 特征仅反映底物电子结构，未涉及过渡态或催化机制 | 引入更细粒度的 QM/MM 计算 | Discussion: "not intended to directly represent the mechanistic determinants of KM" |
| 未联合预测 Kcat | 单一任务预测 KM，未利用 Kcat 与 KM 的共享信息 | 多任务学习联合预测 KM 和 Kcat | Discussion: "extending the current framework to jointly predict KM and Kcat through multi-task learning" |
| 数据偏差 | BRENDA 数据库本身存在实验条件、物种、底物类型偏差 | 未明确提及 | 隐含于数据来源描述 |
| QM 计算成本 | 20,002 个分子的 DFT 优化计算量大 | 未明确提及 | Results: "computationally prohibitive" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| R²=0.537 的增量是否显著 | 与无 QM 基线相比提升幅度未报告具体数值，仅报告 p 值 | 统计显著 ≠ 实际显著，需效应量 | 报告 ΔR² 及 95% CI | Results 图 7, 表 2 |
| PCA 在训练集上拟合 | 若 PCA 变换在训练集上计算后应用于测试集，存在轻微信息泄漏 | 可能高估泛化性能 | 使用嵌套交叉验证或仅在训练折叠内拟合 PCA | Methods: "PCA was applied to each set of model outputs" |
| 袋装树对特征重要性的解释有限 | 未报告特征重要性分析，无法判断 PLM/MLM/QM 各自贡献 | 影响可解释性和后续优化 | 计算置换重要性或 SHAP 值 | 未提供 |
| 未见分子/序列的泛化评估方法 | 图 8 的「未见」定义不明确（是 scaffold split 还是随机 split？） | 影响泛化结论的可信度 | 明确 split 策略并报告分子/序列聚类阈值 | Results 图 8 |
| 与 KmPred 基准比较的公平性 | 仅报告 R²=0.509 vs 0.51，未说明是否使用完全相同的训练/测试划分 | 微小差异可能来自数据划分而非模型 | 使用 KmPred 官方划分并报告多次运行均值±标准差 | Discussion |
| QM 描述符的冗余性 | 8 个描述符均由 HOMO/LUMO 衍生，可能存在高度共线性 | 可能夸大 QM 的独立贡献 | 计算描述符间相关性矩阵，做消融 | Results 图 9 |
| 未报告误差分布 | 仅报告 R²/RMSE，未分析预测误差是否在低/高 KM 区间不均匀 | 影响实际应用（如药物筛选阈值） | 绘制误差 vs 实验值散点图，分层评估 | 未提供 |
| 多蛋白体系处理方式 | 1,556 条多蛋白记录如何编码？是拼接序列还是选择其一？ | 多蛋白体系是代谢网络的常见场景 | 明确多蛋白编码策略并单独评估 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **PLM 层选择策略**：ProtT5 最后四层平均嵌入优于最后一层，提示深层语义需要跨层聚合。可迁移至结构预测任务（如突变效应预测），用最后 k 层平均替代单层嵌入。

2. **维度不对称原则**：蛋白序列信息复杂度高于小分子，需要更高维特征（60-70 PCs vs 20 PCs）。在设计多模态融合模型时，应允许不同模态使用不同特征维度，而非强制统一。

3. **QM 描述符的增量价值**：即使有强大的语言模型嵌入，物理化学描述符仍能提供互补信息。对结构相关任务（如结合亲和力预测），可考虑将 DFT 或半经验 QM 描述符与深度学习特征融合。

4. **序列级数据去重**：以序列而非注释（EC 编号）定义数据唯一性，避免标签歧义导致的数据泄漏。这一原则适用于所有序列-功能预测任务。

5. **滑动窗口 + 重叠平均**：处理超长序列时，用重叠窗口（510 aa, step 256）并在嵌入层平均，比截断或 padding 更保真。可迁移至长蛋白结构域预测或全长蛋白嵌入。

6. **加权损失处理长尾分布**：对 top/bottom 10% 数据加权，改善极端值预测。适用于 KM、IC50 等呈长尾分布的生化参数预测。

7. **系统比较框架**：穷举 PLM × MLM × 维度组合 + 配对 t 检验，是评估特征工程方案的可复制范式。

8. **保守基准评估**：在公共基准（KmPred）上使用相同划分进行头对头比较，比仅报告自建测试集更有说服力。

## 15 与已有知识连接

- **PLM 选择**：ProtT5 (Elnaggar et al., 2021, IEEE TPAMI)、ESM-2 (Lin et al., 2023, Science)、ProtBERT (Elnaggar et al., 2021)、Ankh (Elnaggar et al., 2023, bioRxiv)——均为蛋白质语言模型领域代表性工作，本文系统比较其在下游回归任务的表现。
- **MLM 选择**：ChemBERTa (Chithrananda et al., 2020, arXiv)、MolFormer (Ross et al., 2022, ICLR)——分子 SMILES 语言模型代表。
- **KM 预测先验工作**：KmPred (2026, 引用 23)——本文直接对比的 SOTA；其他 KM 预测 ML 方法（引用 8，R²≈0.50）。
- **QM 描述符**：概念源自概念密度泛函理论（Parr & Yang），HOMO/LUMO 衍生描述符广泛用于反应性预测（如 Mayr 亲电性尺度）。
- **集成树回归**：袋装树（Breiman, 1996）在生化性质预测中常优于深度学习（如随机森林在 QSAR 中的基准表现）。
- **与 AlphaFold 类工作的关系**：本文不涉及结构预测，但 PLM 嵌入（如 ESM-2）已被证明包含结构信息（Lin et al., 2023），因此本文的 PLM 特征选择策略可部分迁移至结构相关任务。
- **与 MD/对接的关系**：本文未使用 MD 或对接，但 QM 描述符与 MD 导出的反应性描述符（如 MM-PBSA 能量项）在概念上互补，可考虑融合。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**: QM-enhanced PLM embeddings for binding affinity prediction
   - **来源局限/观察**: 本文证明 QM 描述符提升 KM 预测，但 KM 是稳态参数，结合亲和力（Ki/Kd）预测可能同样受益于电子结构信息。
   - **核心假设**: 将 QM 描述符与 PLM 嵌入融合可提升蛋白-配体结合亲和力预测精度，尤其在配体反应性主导结合的体系。
   - **初步方法**: 在 PDBbind 等数据集上，用 ProtT5 编码蛋白序列 + 配体 QM 描述符（ωB97XD/6-31G* 水平），训练袋装树或轻量神经网络。
   - **验证方式**: 与仅用 PLM 嵌入的基线对比，报告 ΔR² 和 ΔRMSE；按配体反应性分层分析。
   - **创新状态**: unverified

2. **候选名称**: Cross-modal feature selection for enzyme kinetic parameter prediction
   - **来源局限/观察**: 本文仅用 PCA 降维，未做特征选择或模态重要性分析；袋装树可提供特征重要性但未报告。
   - **核心假设**: 基于置换重要性的特征选择可进一步压缩特征维度，提升模型可解释性和泛化性。
   - **初步方法**: 在本文公开数据上，计算各 PLM/MLM/QM 特征的置换重要性，保留 top-k 特征重新训练，比较性能-维度曲线。
   - **验证方式**: 与 PCA 基线对比；报告特征重要性排序的稳定性（多折交叉验证）。
   - **创新状态**: unverified

3. **候选名称**: Multi-task learning for KM and Kcat co-prediction
   - **来源局限/观察**: 作者在 Discussion 中明确提出多任务学习联合预测 KM 和 Kcat 是未来方向。
   - **核心假设**: KM 和 Kcat 共享底物识别和催化机制信息，多任务学习可提升两者预测精度。
   - **初步方法**: 构建共享 PLM/MLM 编码器 + 双任务输出头，在 BRENDA 数据上联合训练；比较单任务 vs 多任务性能。
   - **验证方式**: 报告两个任务的 R²/RMSE，以及任务间迁移增益。
   - **创新状态**: unverified（作者提及但未实施）

4. **候选名称**: Sliding-window embedding aggregation for long protein language models
   - **来源局限/观察**: 本文滑动窗口策略（510 aa, step 256）仅用于 ProtT5 等有长度限制的模型，未系统比较不同窗口大小和步长。
   - **核心假设**: 窗口大小和重叠率影响长序列蛋白的嵌入质量，存在最优配置。
   - **初步方法**: 在 KM 数据集上，对窗口大小（256/510/1024）和步长（128/256/512）做网格搜索，评估对预测性能的影响。
   - **验证方式**: 报告各配置的 R² 和计算成本；分析窗口边界效应。
   - **创新状态**: unverified

5. **候选名称**: Structure-aware QM descriptors for enzyme-substrate interaction modeling
   - **来源局限/观察**: 本文 QM 描述符仅基于底物分子，未考虑酶活性位点环境；作者承认未建模酶-底物相互作用。
   - **核心假设**: 在 QM 描述符中引入酶活性位点残基的静电/极化效应（如通过 QM/MM 或 Poisson-Boltzmann），可提升 KM 预测。
   - **初步方法**: 对已知结构的酶-底物复合物，计算活性位点静电势或极化率作为额外特征；对无结构酶，用 AlphaFold 预测结构。
   - **验证方式**: 与仅底物 QM 描述符对比；按结构可用性分层评估。
   - **创新状态**: unverified

6. **候选名称**: Benchmarking PLM embeddings for enzyme engineering applications
   - **来源局限/观察**: 本文聚焦 KM 预测，但 PLM 嵌入在突变效应预测（如 ΔΔG、热稳定性）中同样常用。
   - **核心假设**: 本文确定的「最后四层平均 + PCA」策略可迁移至酶工程中的突变效应预测任务。
   - **初步方法**: 在 ProTherm、FireProtDB 等数据集上，用相同特征提取策略训练突变效应预测模型，与现有方法对比。
   - **验证方式**: 报告 ΔΔG 预测的 MAE/RMSE，与 SOTA 对比。
   - **创新状态**: unverified