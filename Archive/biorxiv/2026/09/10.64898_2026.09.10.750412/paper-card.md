## 01 基本信息

- **标题**：Agentic-AI-ready genome-wide poxvirus–host interaction screen refined by a protein language model
- **作者**：Jacob Marcel Anter; Jason Mercer; Artur Yakimovich
- **单位**：未提供（根据致谢推测与 CASUS、Helmholtz AI 相关）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：方法学 + 资源型研究（含湿实验筛选 + 计算框架）
- **领域**：病毒-宿主互作、RNAi 筛选、蛋白质语言模型、正-未标记学习
- **关键词**：poxvirus、vaccinia virus、RNAi screen、protein language model、positive-unlabelled learning、host factor prioritisation、agentic AI
- **DOI/arXiv 号**：10.64898/2026.09.10.750412
- **代码**：GitHub 仓库 ICARusPox（具体 URL 未提供）
- **数据**：Zenodo 仓库，https://doi.org/10.5281/zenodo.22307677
- **阅读日期**：2026-09-13
- **在课题方向中的位置**：本文属于「蛋白质结构相关计算研究 × AI 方法」中的功能筛选数据精炼方向。核心创新在于将蛋白质语言模型（pLM）衍生的 PPI 预测概率作为先验知识，通过 PU 学习框架对全基因组 RNAi 筛选结果进行重排序和置信度加权，从而缓解脱靶效应和 assay 噪声。该工作展示了 pLM 嵌入不仅可用于结构预测，还可作为功能筛选的生物学先验，对蛋白质-蛋白质相互作用预测与功能基因组学交叉领域具有方法学参考价值。

---

## 02 一句话总结

本文针对痘病毒-宿主互作的全基因组 RNAi 筛选结果受脱靶效应和 assay 噪声干扰的问题，提出 ICARus 框架——利用蛋白质语言模型（xCAPT5）预测病毒-宿主 PPI 概率，通过正-未标记（PU）学习对筛选结果进行置信度加权精炼，从而提升已知宿主因子的回收率并拓宽高排名基因的功能景观，同时发布支持 agentic AI 交互的社区资源 ICARusPox。

---

## 03 研究问题

- **具体问题**：全基因组 RNAi 筛选（针对痘病毒感染）的原始 readout 受脱靶效应（off-target effects, OTEs）和 assay 噪声干扰，导致真正的病毒-宿主互作（virus-host interactions, VHIs）难以与假阳性区分，宿主因子（host factors）的优先级排序不可靠。
- **为什么重要**：mpox 等痘病毒疫情的暴发凸显了理解痘病毒-宿主互作的紧迫性。可靠的宿主因子鉴定是发现宿主导向抗病毒靶点（host-directed antiviral targets）的前提。RNAi 筛选虽可系统性地发现宿主基因，但其噪声问题长期未得到有效解决。
- **现有方法为何不足**：传统方法依赖化学修饰 siRNA 或统计校正来缓解 OTEs，但无法利用生物学先验知识（如蛋白质互作信息）来区分真实互作与噪声；公共 PPI 数据库覆盖度有限，难以泛化到新病原体。
- **精确研究问题**：Can a protein language model-derived PPI prior, integrated via positive-unlabelled learning, refine the read-out of a genome-wide RNAi screen to improve the prioritisation of vaccinia virus host factors?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 Discussion 的叙述，标注为「仅本文框架」，未经外部系统核验。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| RNAi 筛选技术 | 全基因组 siRNA 文库（如 Rämö et al. 2014 的 VACV 筛选） | 可系统性地沉默每个宿主基因，发现参与病毒感染的宿主因子 | 脱靶效应（OTEs）和 assay 噪声导致假阳性/假阴性 |
| OTE 缓解策略 | 化学修饰 siRNA、多 siRNA 验证、统计校正 | 部分降低脱靶效应 | 无法利用生物学先验区分真实互作与噪声 |
| 基于数据库的 hit triage | 使用公共 PPI 数据库（如 HVIDB）进行功能注释和互作验证 | 提供实验验证的互作信息 | 数据库覆盖度有限，对新病原体泛化能力差 |
| AI 驱动的 PPI 预测 | SENSE-PPI、xCAPT5、MaTPIP 等 pLM 方法 | 可从序列直接预测 PPI，泛化能力强 | 预测概率未经功能筛选验证，直接用于 hit prioritisation 的框架尚缺 |
| **本文位置** | **ICARus：pLM-PPI 先验 + PU 学习精炼 RNAi readout** | **将 PPI 预测概率作为连续先验，通过 PU 学习对筛选结果进行置信度加权，而非简单二值化** | 依赖 PPI 预测模型质量；PU 学习假设（如先验概率）需谨慎设定 |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| RNAi 脱靶效应（OTEs） | siRNA 与非靶标 mRNA 结合，导致基因沉默表型与真实基因功能不符 | siRNA 序列互补性不完全；单个基因的多个 siRNA 可能共享种子序列 | Introduction 第 2 段："RNAi is hampered by off-target effects (OTEs) involving binding of an siRNA molecule to an mRNA molecule other than its intended target" |
| Assay 噪声 | 阳性/阴性对照的 Z'-score 仅 0.43，线性可分性边际 | 实验条件波动、细胞异质性、成像/分析流程误差 | Results 第 1 节："the best-performing positive and negative controls resulted in 0.43, suggesting the linear separability of the results was marginal" |
| 公共 PPI 数据库覆盖不足 | 实验验证的 PPI 数据稀疏，尤其对新病原体 | 实验验证成本高、周期长；数据库更新滞后 | Introduction 第 3 段："the coverage of public interaction databases remains inherently limited" |
| 现有 hit triage 缺乏生物学先验 | 仅依赖统计阈值或功能注释，无法区分真实互作与噪声 | 未利用蛋白质序列中蕴含的互作信息 | Introduction 第 3 段："Hit triage has benefited from... functional annotation data and PPI data... However, the coverage... remains inherently limited" |
| 多模态整合困难 | 表型特征与 PPI 特征直接拼接未带来性能提升 | 不同模态信息量不对等，需样本级自适应加权 | Results 第 3 节："the multimodal approach did not outperform the PPI-only model"（作者归因于模态互补性不足） |

---

## 06 核心思想

### 1) 表面方法

ICARus 是一个两阶段计算框架：
- **阶段一**：使用 xCAPT5（pLM 驱动的 PPI 预测模型）对 VACV 所有 440 个蛋白与人类宿主蛋白之间的互作概率进行预测，得到每个宿主基因的 PPI 特征向量（维度 = 440，每个维度对应一个 VACV 蛋白的互作概率）。
- **阶段二**：将 PPI 特征向量作为输入，训练一个 PU 学习模型（MLP + nnPU loss），以已知 VACV 宿主因子为正样本，其余基因为未标记样本，输出每个基因的宿主因子概率。
- **最终精炼**：将 PU 模型概率与原始筛选强度相乘（soft-masking），实现置信度加权，得到精炼后的 readout。

### 2) 核心洞察

- **pLM 作为生物学先验的桥梁**：pLM 嵌入捕捉了蛋白质序列中与结构、功能和互作相关的基本生化原理，因此其 PPI 预测可以超越实验验证数据库的覆盖限制，为功能筛选提供可泛化的先验知识。
- **PU 学习而非监督学习**：RNAi 筛选中「非宿主因子」的标签本质上是不可靠的（未标记 ≠ 负样本），因为许多真正的宿主因子尚未被发现。PU 学习显式建模这种不确定性，将未标记样本视为「可能是正样本」而非「负样本」。
- **连续先验而非二值过滤**：传统方法将 PPI 信息作为二值过滤器（有互作/无互作），而 ICARus 使用连续概率进行 soft-masking，保留了不确定性信息，避免因 PPI 预测错误而完全丢弃真实候选基因。

### 3) 可能的普适教训 [Analysis]

- **先验知识的注入方式决定其效用**：将外部生物学先验（如 PPI 预测）作为连续权重而非硬性过滤器，可以更鲁棒地处理先验本身的不确定性。这一思路可迁移到其他功能筛选（如 CRISPR 筛选）的 hit prioritisation。
- **模态融合需考虑信息互补性**：本文发现多模态（表型 + PPI）并未优于单模态（PPI-only），提示模态融合并非简单拼接，而需评估各模态的信息增益和冗余度。这对蛋白质结构预测中多序列比对、结构模板、语言模型嵌入等多源信息的融合策略具有警示意义。
- **「未标记」与「负样本」的区分是生物信息学的核心建模决策**：在蛋白质互作预测、功能注释等任务中，负样本的构建方式直接影响模型性能。PU 学习框架为处理「缺失标签」而非「确定负样本」的场景提供了范式。

---

## 07 方法总览

- **输入**：
  - 全基因组 siRNA 筛选的原始 readout（每个基因的早期/晚期病毒基因表达、细胞数等表型特征，3 维向量）
  - 人类宿主蛋白与 VACV 蛋白的氨基酸序列
  - 已知 VACV 宿主因子列表（正样本，来自文献，Table S8）
- **输出**：
  - 每个基因的宿主因子概率（PU 模型输出）
  - 精炼后的 readout（原始强度 × PU 概率）
  - 高排名宿主因子列表（用于实验验证）
- **模块**：
  1. **PPI 预测模块**：xCAPT5（Sled checkpoint + MLP 分类头），输入蛋白序列对，输出互作概率
  2. **特征聚合模块**：对每个宿主基因，将其编码的所有蛋白的 PPI 概率向量按元素取最大值，得到 440 维基因级 PPI 特征
  3. **PU 学习模块**：MLP + nnPU loss，输入 PPI 特征，输出宿主因子概率
  4. **Soft-masking 模块**：将 PU 概率与原始表型强度相乘，得到精炼 readout
  5. **Agentic 资源模块**：ICARusPox 网站，提供数据浏览、脚本执行和 LLM 接口
- **训练**：
  - PPI 分类头：在 VACV 特异性 PPI 数据集上微调（686 训练 / 68 验证 / 70 测试），二元交叉熵损失
  - PU 模型：nnPU loss，正类先验 π_p = 5 × 10⁻²，1,000 epochs，Adam 优化器
- **假设**：
  - 已知宿主因子（正样本）的标签是可靠的
  - 未标记基因中可能存在未知宿主因子（因此用 PU 而非二元分类）
  - PPI 预测概率与宿主因子可能性正相关
- **文字流程**：
  1. 对 VACV 的 440 个蛋白与所有人类蛋白进行 PPI 预测（xCAPT5）
  2. 将蛋白级 PPI 概率聚合为基因级特征（逐元素最大值）
  3. 以已知宿主因子为正样本，其余为未标记样本，训练 PU 模型
  4. 用 PU 模型对全基因组进行评分，得到宿主因子概率
  5. 将概率与原始筛选强度相乘，得到精炼 readout
  6. 对精炼后的高排名基因进行功能富集分析（ORA），评估生物学合理性
  7. 将原始和精炼数据发布至 ICARusPox 平台，支持 agentic AI 交互

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| xCAPT5 PPI 预测（Sled + MLP 头） | 预测 VACV 蛋白与人类蛋白的互作概率 | 提供超越实验数据库的 PPI 先验 | 输入：蛋白序列对；输出：互作概率（0-1） | Table 1-2：微调后 AUROC 0.93，PR AUC 0.94，MCC 0.72 | 移除后失去 PPI 先验，PU 模型无有效输入特征，框架失效 |
| 基因级特征聚合（逐元素最大值） | 将蛋白级 PPI 概率聚合为基因级特征 | 基因可能编码多个蛋白异构体，需统一为单一特征向量 | 输入：蛋白级 PPI 概率向量；输出：440 维基因级特征 | Methods 节："aggregated by taking the element-wise maximum across all isoforms" | 若改为均值或求和，可能稀释强互作信号，降低 PU 模型判别力 [Analysis] |
| PU 学习模型（MLP + nnPU loss） | 从 PPI 特征预测宿主因子概率 | 处理「未标记 ≠ 负样本」的问题，显式建模标签不确定性 | 输入：440 维 PPI 特征；输出：宿主因子概率 | Table 3：未扰动特征 AUROC 0.77 vs 行/列置换后 ~0.47-0.50 | 移除后无法将 PPI 先验转化为可用的置信度权重 |
| Soft-masking（置信度加权） | 将 PU 概率与原始强度相乘 | 实现 PPI 信息对原始 readout 的连续校正 | 输入：原始强度 + PU 概率；输出：精炼 readout | Results 第 3 节：精炼后功能景观拓宽 | 若改为硬阈值过滤，可能丢失低强度但真实的宿主因子 [Analysis] |
| 功能富集分析（ORA） | 评估精炼后高排名基因的生物学合理性 | 验证精炼是否引入生物学一致的功能类别 | 输入：高排名基因列表；输出：富集的 Reactome 通路 | Results 第 3 节：精炼后 "Membrane trafficking" 等类别占比上升 | 移除后无法验证精炼的生物学有效性 |
| ICARusPox agentic 平台 | 发布数据并提供 LLM 交互接口 | 使社区能够以 agentic AI 方式探索数据 | 输入：用户查询/脚本；输出：分析结果/可视化 | Results 第 4 节：平台提供 dashboard、BioJS 沙箱和 LLM API | 移除后数据可用性降低，但核心方法不受影响 |

---

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 直觉 | 来源指针 |
|------|----------|------|------|----------|
| Recall@k = (已知正样本中排名前 k 的比例) | k = 预测数量 | 评估 PU 模型对已知宿主因子的回收能力 | 衡量模型能否将已知正样本排在前面 | Methods "Evaluation metrics" 节，equation 1 |
| Precision@k = (前 k 中真正正样本的比例) | k = 预测数量 | 评估前 k 预测的精确度 | 衡量前 k 个预测中有多少是真实正样本 | Methods "Evaluation metrics" 节，equation 2 |
| Enrichment@k = Precision@k / 基线正样本率 | 基线正样本率 = 数据集中正样本比例 | 量化模型相对随机选择的富集程度 | >1 表示优于随机选择 | Methods "Evaluation metrics" 节，equation 3-4 |
| nnPU loss | π_p = 正类先验（5 × 10⁻²） | PU 学习训练目标 | 在无负样本标签下估计分类器 | Methods 节："non-negative PU (nnPU) loss with a positive-class prior of π_p = 5 × 10⁻²" |
| Soft-masking: refined = raw × P(host factor) | raw = 原始筛选强度；P = PU 模型概率 | 置信度加权 | 高概率基因保留强度，低概率基因被抑制 | Results 第 3 节："multiplication of the raw intensities by the PU model probability" |

---

## 10 实验设计与证据链

- **数据集/群体**：
  - 全基因组 siRNA 筛选：HeLa CCL-2 细胞，VACV WR 株（双荧光报告病毒），约 1,046 个训练基因 / 104 验证 / 294 测试（PU 学习数据集）
  - PPI 数据集：412 个实验验证的 VACV WR-人类 PPI（HVIDB），负样本为计算生成的核仁蛋白配对，最终 686 训练 / 68 验证 / 70 测试
- **规模**：全基因组（约 18,000 基因），PU 学习数据集为 1,444 基因
- **指标**：AUROC、PR AUC、MCC、Recall@k、Precision@k、Enrichment@k
- **基线**：未校正的原始筛选强度；行/列置换的 PPI 特征（消融对照）
- **骨干/仪器**：Molecular Devices ImageXpress 高内涵显微镜；CellProfiler 图像分析流水线
- **oracle 输入**：已知 VACV 宿主因子列表（文献来源，Table S8）作为 PU 学习的正样本
- **评测协议**：在测试集上评估 AUROC/PR AUC；通过 ORA 评估精炼后高排名基因的功能富集；通过置换检验验证 PPI 特征的非随机性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| PPI 模型基准测试 | xCAPT5 优于 SENSE-PPI 和 MaTPIP | 零样本 vs 微调，Sled vs Pan checkpoint | xCAPT5 + Sled 微调后 AUROC 0.93，PR AUC 0.94，MCC 0.72 | xCAPT5 适合 VACV-人类 PPI 预测 | 未与其他非 pLM 方法比较 | Table 1-2 |
| PU 模型特征消融 | PPI 特征包含非随机信号 | 未扰动 vs 行/列置换特征 | 未扰动 AUROC 0.77 vs 置换后 0.47-0.50 | PPI 特征对宿主因子预测有显著贡献 | 未测试其他特征组合 | Table 3, Figs. S6-S9 |
| 多模态 vs 单模态 | 表型 + PPI 特征优于 PPI 单独 | 多模态（表型 + PPI）vs PPI-only | 多模态未优于 PPI-only | 当前表型特征提供有限增量信息 | 未测试更丰富的表型特征 | Results 第 3 节, Fig. S7 |
| Soft-masking 功能景观分析 | 精炼后高排名基因功能更广 | 精炼前 vs 精炼后 ORA | "Membrane trafficking" 从 7.6% 升至 27.2%，"Immune response" 从 14.7% 升至 29.2% | 精炼引入生物学一致的宿主因子类别 | 未进行湿实验验证新候选 | Results 第 3 节, Fig. 3c |
| 置换检验 | PPI 特征信号非随机 | 行/列置换 vs 原始 | 置换后性能接近随机 | 信号来自 PPI 特征本身 | 未检验 PPI 预测误差的影响 | Table 3 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对 VACV（痘病毒科原型）在 HeLa 细胞中的全基因组 siRNA 筛选。结论不应外推至其他病毒、细胞类型或筛选技术（如 CRISPR）。
- **端到端状态**：ICARus 是计算精炼框架，输出的是优先级排序的候选基因列表，而非经过湿实验验证的宿主因子。所有性能指标均基于已知宿主因子的回收率，不代表新候选的准确率。
- **oracle 依赖**：PU 学习的正样本来自文献已知宿主因子，其完整性和准确性直接影响模型性能。若已知宿主因子存在偏差（如偏向高表达基因），模型可能继承该偏差。
- **PPI 预测的不确定性**：xCAPT5 的预测概率本身存在误差，且训练数据（HVIDB）可能包含体外条件下可检测但体内不发生的互作。作者在 Discussion 中承认了这一局限。
- **性能边界**：AUROC 0.77（PU 模型）和 0.93（PPI 分类器）是在特定测试集上的结果，且测试集与训练集同源（同一 VACV 株）。跨病毒株或跨物种的泛化性能未评估。
- **有边界的复述**：ICARus 利用 pLM 衍生的 PPI 先验，通过 PU 学习对 VACV 全基因组 RNAi 筛选结果进行置信度加权，在已知宿主因子的回收率和功能景观广度上优于未校正的原始筛选，但新候选基因的生物学功能仍需独立实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 依赖正样本集质量 | 正样本为已知 VACV 宿主因子，可能不完整或有偏差 | 定期更新正样本集，纳入新实验证据 | Discussion 第 1 段："The framework would therefore benefit from periodic curation and updating of the positive reference set as new experimental evidence becomes available" |
| PPI 数据质量与生物学背景 | 实验验证的 PPI 可能包含体外可检测但体内不发生的互作 | 更严格筛选 PPI 数据的实验条件和细胞定位信息 | Discussion 第 2 段："Experimentally demonstrated VACV-human PPIs may include interactions that are detectable under in vitro conditions but are unlikely to occur during infection" |
| 多模态整合未提升性能 | 表型 + PPI 特征未优于 PPI-only | 探索更丰富的表型特征或更复杂的融合策略 | Results 第 3 节："this approach did not outperform the PPI-only model" |
| 自噬相关基因代表性下降 | 精炼后自噬类别的基因占比降低 | 作者认为可能反映正样本集偏差，需进一步研究 | Discussion 第 1 段："The reduced representation of autophagy-related genes after refinement may illustrate this limitation" |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| PU 学习正样本仅来自文献，未包含本筛选新发现的候选 | 正样本集可能偏向研究充分的基因（如免疫相关），导致模型对未充分研究的通路（如自噬）产生系统性低估 | 若正样本集有偏，精炼结果可能强化已有研究偏见，而非发现新生物学 | 使用独立来源的正样本集（如 CRISPR 筛选、遗传关联研究）进行交叉验证 | Discussion 中作者承认自噬基因代表性下降 |
| PPI 特征维度为 440（VACV 蛋白数），但未报告特征重要性分析 | 可能只有少数 VACV 蛋白的互作概率驱动模型预测，其余为噪声 | 理解哪些 VACV 蛋白的互作信息最关键，有助于生物学解释和模型简化 | 进行特征重要性分析（如 SHAP、排列重要性） | Methods 节未提及特征重要性分析 |
| Soft-masking 的乘法操作缺乏理论推导 | 乘法假设 PPI 概率与原始强度独立且线性可乘，但实际关系可能更复杂 | 若乘法假设不成立，精炼后的 readout 可能引入新的偏差 | 比较乘法、加法、对数等不同融合策略的性能 | Results 第 3 节仅报告乘法结果 |
| 置换检验仅置换 PPI 特征，未置换正样本标签 | 模型可能通过记忆正样本的序列特征而非泛化的 PPI 模式进行预测 | 若模型过拟合正样本，新候选的可靠性存疑 | 进行标签置换检验，或使用独立验证集 | Table 3 仅报告特征置换结果 |
| 未与简单基线（如直接使用 PPI 数据库评分）比较 | 未证明 pLM 衍生的 PPI 先验优于传统数据库先验 | 若传统方法同样有效，pLM 的增量价值不明确 | 增加与 HVIDB 直接评分、STRING 等数据库评分的比较 | 文中未提供此类比较 |
| 平台宣称 "agentic-AI-ready" 但未提供具体 agent 工作流评估 | 平台提供 LLM 接口，但未展示 agent 能否有效利用数据产生新假设 | Agentic 功能是本文的卖点之一，缺乏评估则难以判断其实际效用 | 设计标准化的 agent 任务（如候选基因优先级排序、通路假设生成）进行评估 | Results 第 4 节仅描述平台功能，无评估 |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **pLM 作为功能筛选先验的范式**：本文展示了 pLM（如 xCAPT5）不仅可用于结构预测，其嵌入衍生的 PPI 概率可作为功能基因组学筛选的连续先验。对于蛋白质结构相关计算研究，这意味着 pLM 嵌入可能蕴含超越结构的生物学功能信息，值得在结构-功能关联任务中进一步挖掘。

2. **PU 学习处理「未标记 ≠ 负样本」**：在蛋白质互作预测、功能注释等任务中，负样本的构建是核心难题。本文的 PU 学习框架为处理「缺失标签」场景提供了可迁移的建模思路，尤其适用于病毒-宿主互作这类正样本稀少、负样本不确定的问题。

3. **Soft-masking 而非硬过滤**：将外部先验作为连续权重而非二值过滤器，可以保留不确定性信息，避免因先验错误而完全丢弃真实候选。这一策略可迁移到结构预测中的模板筛选、对接中的打分函数融合等场景。

4. **多模态融合的警示**：本文发现表型 + PPI 多模态并未优于 PPI 单模态，提示模态融合需评估信息互补性而非简单拼接。对于蛋白质结构预测中多源信息（MSA、模板、语言模型嵌入）的融合策略，这一发现具有方法论警示意义。

5. **Agentic 数据资源的设计**：ICARusPox 将数据、分析函数和 LLM 接口整合为一个 agent 可交互的平台，为计算生物学数据共享提供了新范式。对于结构生物学领域，类似的设计可应用于结构数据库、MD 模拟轨迹等资源的发布。

6. **置换检验作为特征有效性验证**：通过行/列置换 PPI 特征验证信号非随机性，是一种简单有效的消融实验设计，可迁移到其他特征工程任务的验证中。

---

## 15 与已有知识连接

- **Rämö et al. 2014**：本文的筛选实验方案完全沿用 Rämö 等人的 VACV 全基因组 siRNA 筛选流程（Methods 节明确说明）。该工作为本文提供了原始数据来源和实验基础。
- **xCAPT5 (Anter et al.)**：本文使用的 PPI 预测模型，属于 pLM 驱动的互作预测方法。与 SENSE-PPI、MaTPIP 等同类方法进行了基准比较。
- **PU 学习 (Elkan & Noto 2008; du Plessis et al. 2014)**：nnPU loss 是 PU 学习的经典变体，本文将其应用于功能筛选精炼，是该理论在病毒学领域的迁移应用。
- **HVIDB (Human-Virus Interaction Database)**：本文 PPI 正样本的来源数据库，提供了实验验证的 VACV-人类互作数据。
- **DAVID 功能注释工具**：用于 ORA 分析，将精炼后的高排名基因映射到 Reactome 通路。
- **AlphaFold 等结构预测方法**：本文未直接使用结构预测，但其 pLM 嵌入思想与 AlphaFold 的 Evoformer 架构共享序列表示学习的基础。对于结构-功能关联研究，本文提供了 pLM 嵌入在功能预测中应用的新视角。
- **Agentic AI 在生物学的应用**：ICARusPox 与近期 LLM 驱动的科学发现平台（如 ChemCrow、Coscientist）理念一致，但聚焦于数据资源的 agent 可访问性设计。

---

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：pLM-PPI 先验在 CRISPR 筛选精炼中的迁移应用
   - **来源局限/观察**：本文方法针对 RNAi 筛选，但 CRISPR 筛选同样面临脱靶效应和噪声问题，且 CRISPR 筛选数据规模更大、噪声特征不同。
   - **核心假设**：pLM 衍生的 PPI 先验同样能提升 CRISPR 筛选的 hit prioritisation 性能。
   - **初步方法**：将 ICARus 框架迁移至 CRISPR 筛选数据，使用 pLM 预测的 PPI 概率作为特征，PU 学习进行精炼。
   - **验证方式**：在公开的 CRISPR 筛选数据集（如 DepMap）上评估已知互作基因的回收率。
   - **创新状态**：unverified

2. **候选名称**：结构感知的 PPI 先验增强
   - **来源局限/观察**：本文仅使用序列衍生的 pLM 嵌入，未利用蛋白质三维结构信息。AlphaFold 预测的结构可能提供更精确的互作界面信息。
   - **核心假设**：结合结构信息（如互作界面残基、结合能）的 PPI 先验比纯序列先验更能提升宿主因子预测精度。
   - **初步方法**：使用 AlphaFold-Multimer 预测 VACV-人类蛋白复合物结构，提取界面特征与 xCAPT5 概率融合。
   - **验证方式**：在本文的 VACV 数据集上对比结构增强与纯序列先验的 AUROC/PR AUC。
   - **创新状态**：unverified

3. **候选名称**：动态先验更新的迭代 PU 学习
   - **来源局限/观察**：本文的 PU 学习使用静态正样本集，未利用模型自身的预测结果进行迭代优化。
   - **核心假设**：通过迭代方式，将高置信度预测加入正样本集，可逐步提升模型对未知宿主因子的发现能力。
   - **初步方法**：设计自训练循环，每轮将 PU 模型高置信度预测（如概率 > 0.9）加入正样本集，重新训练。
   - **验证方式**：在 VACV 数据集上比较迭代与静态训练的候选基因列表差异，并通过文献验证新候选。
   - **创新状态**：unverified

4. **候选名称**：跨病毒属的 PPI 先验泛化性评估
   - **来源局限/观察**：本文仅针对 VACV，未评估框架对其他痘病毒（如 mpox virus、ectromelia virus）的适用性。
   - **核心假设**：pLM 衍生的 PPI 先验可跨病毒属泛化，但泛化性能受病毒蛋白序列相似性影响。
   - **初步方法**：在 mpox virus 的已知互作数据上测试 ICARus 框架，比较与 VACV 的性能差异。
   - **验证方式**：使用 HVIDB 中其他痘病毒的互作数据作为测试集。
   - **创新状态**：unverified

5. **候选名称**：agentic 结构-功能联合分析工作流
   - **来源局限/观察**：ICARusPox 提供 agentic 数据访问，但未将结构预测工具（如 AlphaFold、MD 模拟）整合进分析流程。
   - **核心假设**：将结构预测和 MD 模拟工具整合进 agentic 工作流，可实现对候选宿主因子的结构-功能联合验证。
   - **初步方法**：设计 LLM 驱动的 agent，自动调用 AlphaFold 预测候选互作复合物结构，并运行短程 MD 模拟评估互作稳定性。
   - **验证方式**：在 ICARus 输出的高排名候选基因上运行工作流，评估结构验证对候选优先级的修正效果。
   - **创新状态**：unverified