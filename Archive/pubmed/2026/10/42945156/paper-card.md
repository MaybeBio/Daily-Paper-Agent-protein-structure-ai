## 01 基本信息
- 标题：Structural basis for inhibition of the lipid flippase MurJ by phage lysis protein SglPP7 suggests convergent evolution with other Sgl peptides
- 作者与单位：Hosoda, Kaito; Kohga, Hidetaka; Wu, Sixian; Tanaka, Hiroyuki; Shigematsu, Hideki; Miyazaki, Ryoji; Chek, Min Fey; Tsukazaki, Tomoya（具体单位未在提供材料中列出）
- 期刊/预印本平台：PLoS Biology
- 年份：2026（日期 2026-10-27）
- 论文类型：实验结构生物学 + 计算（cryo-EM 结构解析 + 突变分析 + MD 模拟）
- 领域：膜蛋白结构生物学、细菌细胞壁合成、噬菌体裂解蛋白、抗菌策略
- 关键词：未提供（正文未列关键词列表）
- DOI/arXiv 号：10.1371/journal.pbio.3004039
- 代码：未提供
- 数据：cryo-EM map 与模型（PDB 登录号未在提供材料中列出）；S1 Table 含数据收集与精修统计
- 阅读日期：未提供
- 在「蛋白质结构相关计算研究 × AI/物理模拟」方向中的位置：本文以 cryo-EM 实验结构为核心，辅以 MD 模拟验证构象稳定性，并报告 AlphaFold3 在预测 MurJ/SglPP7 复合物界面与 MurJ 构象态上的失败案例。对课题方向的价值在于：(1) 提供膜蛋白-肽复合物的实验结构基准；(2) 展示 AF3 在膜蛋白构象态预测上的系统性偏差（偏好 inward-facing）；(3) 展示 MD 模拟作为实验结构验证与构象动力学分析的工具；(4) 提供「序列分歧蛋白靶向同一蛋白不同结合模式」的趋同进化案例，对结构/序列设计有参考意义。

## 02 一句话总结
本文通过 cryo-EM 解析了大肠杆菌 MurJ 与噬菌体裂解蛋白 SglPP7 的复合物结构（3.2 Å），结合突变分析和 MD 模拟，发现 SglPP7 通过其跨膜螺旋沿 MurJ 膜内裂隙结合并将 C 端尾部插入 C-lobe 内部腔体，将 MurJ 稳定在 outward-facing 构象，且其结合模式与序列无关的 LysM 和 SglCJ3 截然不同，提示趋同进化。

## 03 研究问题
- 具体问题：SglPP7 如何抑制 MurJ 的 lipid II 翻转酶功能？其结合模式与已知的 MurJ 抑制剂 LysM 是否相同？
- 为什么重要：MurJ 是细菌细胞壁合成的必需蛋白，是潜在抗菌靶点；理解噬菌体来源的 Sgl 蛋白如何抑制 MurJ，可为开发新型抗菌策略提供结构基础。
- 现有方法为何不足：此前仅有 LysM/MurJ 复合物结构，SglPP7 虽经遗传筛选提示靶向 MurJ，但其结构机制未知；SglPP7 与 LysM 无序列相似性，无法通过同源建模推断结合模式。
- 精确研究问题：Can SglPP7 inhibit MurJ through a binding mode distinct from that of LysM, and if so, what is the structural basis?

## 04 背景与发展脉络
- 阶段一：Sgl 蛋白的发现与功能鉴定。蛋白 E（ΦX174）抑制 MraY，蛋白 A2（Qβ）抑制 MurA，LysM（噬菌体 M）靶向 MurJ。优点：证明 Sgl 蛋白可作为「蛋白抗生素」。局限：结构机制多数未知。
- 阶段二：MurJ 的结构与转运机制研究。MurJ 为 14 次跨膜蛋白，N-lobe（TM1–6）、C-lobe（TM7–12）、TM13–14，通过 alternating-access 机制转运 lipid II，类似 MATE 转运蛋白。优点：明确了构象循环框架。局限：抑制剂如何锁定特定构象态尚不清楚。
- 阶段三：MurJ/LysM 复合物 cryo-EM 结构解析。LysM 楔入 MurJ outward-facing 构象，阻止构象变化。优点：首个 MurJ-Sgl 复合物结构。局限：仅一个例子，无法判断是否为通用机制。
- 阶段四（本文位置）：解析 MurJ/SglPP7 复合物结构，与 LysM 和 SglCJ3 比较，提出趋同进化假说。本文主张：序列分歧的 Sgl 蛋白通过不同结合模式（cavity-occupying / surface-binding / cleft-binding）稳定同一构象态。
- 脉络标注：以上脉络基于本文 Introduction 和 Results 的叙述框架 [仅本文框架]，未独立核验外部文献。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| SglPP7 抑制 MurJ 的结构机制未知 | 仅有遗传筛选提示 SglPP7 靶向 MurJ，无结构信息 | SglPP7 与 LysM 无序列相似性，无法同源建模 | Introduction 末段；Fig 1B–1C |
| AlphaFold3 无法预测 SglPP7 在 MurJ 上的结合位置 | AF3 预测的 SglPP7 位置与实验结构不符，且置信度低 | 可能反映 PDB 中 inward-facing MurJ 结构占多数，AF3 偏好预测 inward-facing 构象 | S3 Fig |
| C 端标签使 SglPP7 丧失裂解活性 | C-terminal His10-tag SglPP7 无裂解活性，而 N-terminal tag 保留活性 | C 端尾部需插入 MurJ 内部腔体，C 端标签产生空间位阻 | Fig 1D |
| SglPP7 跨膜螺旋不依赖少数关键残基 | Alanine scanning 仅 F22A、L30A、S39A 显示轻微活性降低 | 跨膜螺旋通过广泛、分散的弱相互作用支撑 | S9 Fig |
| 脂质样密度无法确定分子种类 | 在 putative lipid II 结合槽中观察到脂质样密度，但无亲水头基特征 | 分辨率不足以识别分子种类 | S6 Fig |

## 06 核心思想
1. 表面方法：利用 cryo-EM 解析 MurJ/SglPP7 复合物结构（3.2 Å），结合体内裂解实验、突变分析和 MD 模拟，阐明 SglPP7 的抑制机制，并与 LysM 和 SglCJ3 结构比较。
2. 核心洞察：SglPP7 通过其跨膜螺旋沿 MurJ 的 TM7 形成广泛接触面，并将 C 端尾部（residues 50–55，关键残基 W53）深深插入 C-lobe 内部腔体（由 TM7、TM8、TM10、TM12 形成），将 MurJ 锁定在 outward-facing 构象。这一「embedded tail」机制与 LysM 的「surface-binding」和 SglCJ3 的「cleft-binding」截然不同，但三者均稳定同一构象态，提示趋同进化。
3. 可能的普适教训 [Analysis]：序列高度分歧的蛋白可通过完全不同的结合模式靶向同一蛋白的同一功能态；AlphaFold3 在膜蛋白构象态预测上可能存在系统性偏差（偏好 PDB 中占多数的构象态），实验结构仍不可替代；MD 模拟可作为验证实验结构稳定性和构象动力学的补充工具。

## 07 方法总览
- 输入：SglPP7 基因序列（codon-optimized for E. coli）、E. coli MurJ 序列、LysM 和 SglCJ3 已知结构。
- 输出：MurJ/SglPP7 复合物 cryo-EM 结构（3.2 Å）、裂解活性数据、MD 模拟轨迹、结构比较结果。
- 模块：
  - 体内裂解实验（lysis assay）：评估 SglPP7 及其突变体的毒性。
  - 蛋白表达与纯化：共表达 Met-Ala-EcMurJ2-511-3×FLAG、Met-His10-SglPP7、BsAmj，Ni-NTA 纯化，Superose 6 凝胶过滤。
  - Nanodisc 重构：MSP1D1 + E. coli 磷脂，摩尔比 1.4:1:120。
  - Cryo-EM 数据收集与处理：CRYO ARM 300，K3 检测器，cryoSPARC 处理，3.2 Å 分辨率。
  - 模型构建与精修：AlphaFold3 预测 SglPP7 结构 + MurJ/LysM 复合物中 MurJ outward 模型（PDB 9UKV）docking 入 map，Coot 手动修改，PHENIX real_space_refine。
  - MD 模拟：YASARA dynamics，AMBER14 力场，POPE/POPG 膜，0.9% NaCl，120 ns，3 次独立模拟。
  - 突变分析：N 端截短、C 端截短、W53 突变、alanine scanning。
- 训练：不适用（无机器学习模型训练）。
- 工具：cryoSPARC v4.6.2–v5.0.6、UCSF ChimeraX、Coot、PHENIX、PyMOL、YASARA、AlphaFold3。
- 反馈回路：结构观察 → 突变设计 → 裂解实验验证 → MD 模拟验证构象稳定性 → 结构比较。
- 假设：SglPP7 与 LysM 结合模式不同；C 端尾部插入对功能至关重要；MD 可捕捉 SglPP7 对 MurJ 构象动力学的稳定作用。
- 文字流程：基因合成 → 质粒构建 → 共表达纯化 → Nanodisc 重构 → cryo-EM 数据收集 → 数据处理与 3D 重构 → 模型构建与精修 → 结构分析 → 突变体设计与裂解实验 → MD 模拟 → 与 LysM/SglCJ3 结构比较 → 提出工作模型。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Cryo-EM 结构解析 | 确定 MurJ/SglPP7 复合物原子结构 | 无同源结构可推断结合模式 | 输入：纯化复合物 nanodisc；输出：3.2 Å map 和原子模型 | Fig 1E–1G, S1, S1 Table | 无法确定结合界面和 embedded tail 特征 [预期效应] |
| 裂解实验（lysis assay） | 评估 SglPP7 突变体毒性 | 验证结构观察的功能相关性 | 输入：SglPP7 突变体质粒；输出：菌落生长/裂解表型 | Fig 1D, Fig 2C, S4, S5, S9 | 无法判断哪些残基/区域对功能重要 [预期效应] |
| MD 模拟 | 评估 SglPP7 对 MurJ 构象动力学的影响 | 实验结构为静态，需动态验证 | 输入：MurJ 或 MurJ/SglPP7 结构；输出：RMSD、Cα–Cα 距离轨迹 | Fig 3A–3D | 无法定量比较有无 SglPP7 时 MurJ 的构象波动 [预期效应] |
| 结构比较 | 比较 SglPP7/LysM/SglCJ3 结合模式 | 检验趋同进化假说 | 输入：三个复合物结构；输出：RMSD、结合界面残基集、结合模式分类 | Fig 4A–4C, S7, S8 | 无法提出趋同进化结论 [预期效应] |
| AlphaFold3 预测 | 预测 SglPP7 结构用于模型构建 | 无实验相位信息时辅助建模 | 输入：SglPP7 序列；输出：预测结构 | Methods, S3 Fig | 无法完成 SglPP7 初始模型搭建 [预期效应]；但 AF3 预测的复合物界面位置错误 [实测] |

## 09 关键公式符号
- Cα RMSD：衡量两个结构之间 Cα 原子位置的均方根偏差。用途：比较 MurJ/SglPP7 与 MurJ/LysM 等复合物中 MurJ 构象的相似性。直觉：值越小，构象越相似。来源：Results 节，Fig 4A，S2D Fig，S7 Fig。
- Cα–Cα distance：两个残基 Cα 原子之间的距离。用途：监测 MD 模拟中特定跨膜螺旋间距离变化（Y266–L247 和 G360–G415）。直觉：距离减小表示螺旋间靠近，距离维持表示结构稳定。来源：Fig 3C–3D。
- 无其他理解必需的公式。

## 10 实验设计与证据链
- 数据集/群体：E. coli BL21 ΔrecA (DE3) 细胞；E. coli JCM 20135 MurJ；噬菌体 PP7 SglPP7；噬菌体 M LysM；SglCJ3。
- 规模：cryo-EM 17,650 movies，最终 453,217 particles 用于 3D 重构；MD 模拟 3 次独立运行，每次 120 ns。
- 指标：cryo-EM 整体分辨率 3.2 Å；裂解活性（菌落生长/无生长）；Cα RMSD；Cα–Cα 距离。
- 基线：MurJ/LysM 复合物结构（PDB 9UKV）；SglPP7-free MurJ MD 模拟；已知 LysM-resistant MurJ 突变体。
- 预算：未提供。
- 骨干/仪器：CRYO ARM 300 TEM（300 kV，冷场发射枪，Omega 型能量过滤器，K3 检测器）；YASARA dynamics 软件。
- Oracle 输入：实验 cryo-EM map 作为模型构建的 oracle；AlphaFold3 预测结构作为初始模型。
- 评测协议：cryoSPARC 标准处理流程；MD 模拟 NPT 条件 298 K，1 atm；裂解实验 37 °C 22 h。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| SglPP7 毒性实验 | SglPP7 抑制 MurJ 导致裂解 | untagged vs N-His10 vs C-His10 | untagged 和 N-His10 有裂解活性，C-His10 无 | C 端对功能重要 | 不能证明 C 端标签直接阻断活性位点 | Fig 1D |
| Cryo-EM 结构解析 | SglPP7 结合 MurJ 的位点和构象 | 3.2 Å 分辨率 | SglPP7 沿膜内裂隙结合，C 端插入 C-lobe 腔体，MurJ 为 outward-facing | 结构支持 embedded tail 机制 | 不能排除其他构象态存在 | Fig 1E–1G, S1 |
| N 端截短 | N 端 1–25 是否必需 | GFP-SglPP7 系列截短 | 除 GFP-SglPP722–55 外均有活性 | 最小功能单元约从 residue 22 开始 | 不能排除 N 端在特定条件下有调控作用 | S4 Fig |
| C 端截短 | C 端尾部长度要求 | 逐步截短 | 保留至 residue 53 才有活性 | C 端尾部（至 W53）对功能必需 | 不能确定 54–55 是否完全无贡献 | Fig 2C, S5A |
| W53 突变 | W53 是否为关键残基 | W53A/G/C/S/K/R | W53A 全活性，W53G/C/S 略降，W53K/R 失活 | W53 重要但可被邻近残基部分补偿 | 不能排除其他残基在特定背景下更重要 | Fig 2C, S5B |
| W53 突变（1–53 背景） | W53 在最小功能背景下的作用 | 1–53 截短背景下的 W53 变体 | 所有变体活性减弱 | C 端区域是功能决定簇 | 不能确定 W53 是唯一关键残基 | Fig 2C, S5C |
| MD 模拟（RMSD） | SglPP7 是否稳定 MurJ | MurJ vs MurJ/SglPP7，3×120 ns | 复合物 RMSD 持续低于 MurJ 单独 | SglPP7 抑制 MurJ 构象波动 | 不能证明 SglPP7 完全冻结 MurJ | Fig 3A–3B |
| MD 模拟（Cα–Cα 距离） | embedded tail 是否稳定 C-lobe 腔体 | Y266–L247 vs G360–G415 | Y266–L247 距离在 MurJ 单独中减小，复合物中维持；G360–G415 不变 | embedded tail 稳定 C-lobe 腔体 | 不能排除其他螺旋间相互作用 | Fig 3C–3D |
| Alanine scanning | SglPP7 TM 螺旋是否依赖少数关键残基 | 单点突变 | 仅 F22A、L30A、S39A 轻微降低活性 | 广泛弱相互作用支撑结合 | 不能排除组合突变有更大效应 | S9 Fig |
| LysM-resistant MurJ 突变体 | SglPP7 和 LysM 是否共享结合界面 | 已知 LysM 抗性突变体 + SglPP7 诱导 | 仅 Q244P 可生长，其余仍敏感 | 结合界面不同 | 不能排除 Q244P 影响两个界面 | Fig 4C |
| 结构比较 | 三种 Sgl 蛋白结合模式是否不同 | SglPP7 vs LysM vs SglCJ3 | 结合模式分别为 cavity-occupying / surface-binding / cleft-binding | 趋同进化假说 | 不能证明进化历史 | Fig 4A–4B, S7, S8 |
| AlphaFold3 预测 | AF3 能否预测复合物界面 | AF3 vs 实验结构 | AF3 预测位置错误，置信度低，偏好 inward-facing | AF3 在膜蛋白构象态预测上有局限 | 不能推广到所有膜蛋白 | S3 Fig |

## 11 结论正确解读
- 任务范围：本文结论限于 E. coli MurJ 与噬菌体 PP7 SglPP7 的复合物，以及与其他 Sgl 蛋白的结构比较。
- Oracle/真值输入：cryo-EM map 为实验测定，非 oracle；AlphaFold3 预测仅用于初始模型搭建，最终模型经实验 map 精修。
- 端到端状态：从基因到结构到功能验证的完整链条，但 MD 模拟为 120 ns，可能不足以捕捉慢速构象变化。
- 算力成本：未提供。
- 历史数据依赖：结构比较依赖 PDB 中已有的 MurJ/LysM 和 MurJ/SglCJ3 结构。
- 模型依赖：AlphaFold3 用于 SglPP7 初始模型预测，但复合物界面预测失败。
- 最难情形：SglPP7 N 端 1–25 区域在 cryo-EM map 中不可见，无法建模；脂质样密度无法确定分子种类。
- 群体/领域边界：结论限于 E. coli MurJ 和特定噬菌体 Sgl 蛋白，未验证其他细菌或其他 MurJ 同源物。
- 不确定性：趋同进化结论为「consistent with the possibility」，非确定性结论；MD 模拟仅 3 次独立运行，统计力度有限。
- 有边界的复述：在 E. coli MurJ 与 SglPP7 的复合物中，SglPP7 通过跨膜螺旋沿 TM7 广泛接触并将 C 端尾部插入 C-lobe 腔体，稳定 MurJ 于 outward-facing 构象；该结合模式与 LysM 和 SglCJ3 不同，提示序列分歧的 Sgl 蛋白可能独立进化出不同策略抑制 MurJ。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| SglPP7 N 端 1–25 区域 cryo-EM map 质量差 | 无法可靠建模，模型从 residue 26 开始 | 未明确提出 | S1D, S2C Fig |
| 脂质样密度无法确定分子种类 | 无亲水头基特征 | 未明确提出 | S6 Fig |
| MD 模拟时长有限 | 120 ns，可能不足以捕捉慢速构象变化 | 未明确提出 | Methods |
| 趋同进化结论为可能性 | 用「consistent with the possibility」表述 | 未明确提出 | Abstract, Results |
| AlphaFold3 预测失败 | AF3 无法预测 SglPP7 结合位置，偏好 inward-facing | 未明确提出 | S3 Fig |

作者提及的相关约束（非正式局限）：
- 另一组在本文准备期间报道了 MurJ/SglPP7 复合物结构（N 端截短、突变体、BRIL 融合、Fab-nanobody 复合物），本文使用全长 SglPP7 和 nanodisc 重构，两者结构高度相似（Cα RMSD 0.747 Å）。
- Alanine scanning 仅显示少数残基轻微降低活性，而另一研究使用 Δ2–24 最小功能变体背景报告 Y36 替换导致显著功能丧失，提示背景依赖性。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| MD 模拟仅 120 ns，3 次独立运行 | 可能不足以捕捉 MurJ 构象转变的慢速过程；统计力度有限 | 结论「SglPP7 稳定 outward-facing 构象」可能低估了长时间尺度上的构象变化 | 延长模拟至微秒级，增加独立运行次数 | Methods, Fig 3 |
| Alanine scanning 仅少数残基显示轻微活性降低 | 可能因为单点突变被邻近残基补偿；也可能因为裂解实验灵敏度不足 | 「广泛弱相互作用」结论可能掩盖了组合突变的重要效应 | 进行组合突变、使用更敏感的活性检测 | S9 Fig |
| AlphaFold3 预测失败被归因于 PDB 中 inward-facing 结构占多数 | 也可能是 AF3 训练数据中膜蛋白-肽复合物不足，或 AF3 对构象态切换的建模能力有限 | 对 AI 结构预测在膜蛋白构象态预测上的局限性有广泛意义 | 系统评估 AF3 在不同膜蛋白构象态预测上的表现 | S3 Fig |
| 趋同进化结论基于三个 Sgl 蛋白的结构比较 | 三个例子不足以排除共同祖先的可能性；也可能存在其他未发现的结合模式 | 趋同进化是强结论，需要更多序列和结构证据 | 扩大 Sgl 蛋白采样，进行系统发育分析 | Fig 4, S7, S8 |
| 脂质样密度在 putative lipid II 结合槽中 | 可能是 E. coli 磷脂而非 lipid II；也可能是纯化过程中共纯化的脂质 | 影响对 SglPP7 是否直接竞争 lipid II 结合的解释 | 使用 defined lipid II 类似物进行结构解析或结合实验 | S6 Fig |
| C 端 His10-tag 使 SglPP7 失活 | 可能是标签影响蛋白稳定性或膜插入，而非直接空间位阻 | 支持 embedded tail 机制的关键证据之一，但存在替代解释 | 使用更小标签或非结构性标签验证 | Fig 1D |
| 结构比较中 RMSD 值均较小（0.7–0.8 Å） | 可能反映 MurJ outward-facing 构象的刚性，而非 Sgl 蛋白诱导的特定构象 | 不能排除 MurJ 本身在 outward-facing 态下构象变化有限 | 比较更多 MurJ 构象态的结构 | Fig 4A, S7 |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念：膜蛋白-肽复合物的 cryo-EM 结构解析流程（nanodisc 重构、cryoSPARC 处理、AlphaFold3 辅助建模 + 实验 map 精修）。可迁移到本课题中膜蛋白-配体复合物的结构预测与验证。
- 可迁移方法：MD 模拟作为实验结构的动态验证工具，通过比较有无配体时的 RMSD 和特定残基对距离变化，评估配体对蛋白构象动力学的稳定作用。可迁移到本课题中评估预测结构或设计蛋白的构象稳定性。
- 可迁移实验设计：Alanine scanning + 截短突变 + 裂解实验的组合，用于验证结构观察的功能相关性。可迁移到本课题中验证设计蛋白的关键残基。
- 可迁移洞察：AlphaFold3 在膜蛋白构象态预测上可能存在系统性偏差（偏好 PDB 中占多数的构象态），实验结构仍不可替代。对本课题中依赖 AF3 进行复合物结构预测的工作有警示意义。
- 可迁移洞察：序列高度分歧的蛋白可通过完全不同的结合模式靶向同一蛋白的同一功能态。对本课题中蛋白-蛋白相互作用设计和结合模式预测有参考意义。
- 可迁移公式/指标：Cα RMSD 和 Cα–Cα 距离作为结构比较和 MD 分析的指标。可直接用于本课题的结构比较和模拟分析。

## 15 与已有知识连接
- 相似：MurJ/LysM 复合物结构（PDB 9UKV）[19]；MurJ/SglCJ3 复合物结构 [20]；T. africanus MurJ 的 outward-facing 晶体结构 [16]。
- 组合：本文将 cryo-EM 结构解析、突变分析、MD 模拟和结构比较整合，形成多证据链。可组合到本课题中「预测-验证-模拟」的工作流。
- 冲突：AlphaFold3 预测的 SglPP7 结合位置与实验结构不符，且 AF3 偏好预测 inward-facing MurJ 构象。与本课题中依赖 AF3 进行复合物预测的假设存在潜在冲突。
- 可迁移领域：噬菌体裂解蛋白作为「蛋白抗生素」的机制研究；FtsZ 抑制剂（Kil, Gp0.4, Hdi, Icd）虽无结构信息，但类似地靶向同一蛋白 [26–29]。可迁移到本课题中蛋白-蛋白相互作用设计和抗菌肽设计。
- 外部文献：未提供完整参考文献列表，以上连接基于正文引用编号。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：AF3 在膜蛋白构象态预测上的系统性偏差评估
   - 来源局限/观察：本文 S3 Fig 显示 AF3 无法预测 SglPP7 结合位置，且偏好 inward-facing MurJ 构象。
   - 核心假设：AF3 在膜蛋白构象态预测上存在系统性偏差，偏好 PDB 中占多数的构象态。
   - 相对本文的增量：从单个案例扩展到系统性评估。
   - 初步方法：选取多个具有多种构象态的膜蛋白，比较 AF3 预测构象态与实验构象态的分布。
   - 验证方式：统计 AF3 预测构象态与 PDB 中构象态分布的相关性。
   - 可能的失败模式：AF3 可能对某些膜蛋白构象态预测准确，偏差不具普遍性。
   - 创新状态：unverified。

2. 名称：基于 SglPP7 embedded tail 机制的 MurJ 抑制肽设计
   - 来源局限/观察：SglPP7 C 端尾部（residues 50–55，关键 W53）插入 MurJ C-lobe 腔体，对功能至关重要。
   - 核心假设：模拟 SglPP7 C 端尾部的短肽可独立结合 MurJ 并稳定 outward-facing 构象。
   - 相对本文的增量：从天然蛋白到最小功能肽的简化。
   - 初步方法：设计基于 SglPP7 C 端序列的短肽，进行 MD 模拟和结合自由能计算。
   - 验证方式：体外结合实验（如 ITC、SPR）和体内裂解实验。
   - 可能的失败模式：短肽可能无法独立折叠或结合，需要跨膜螺旋提供额外相互作用。
   - 创新状态：unverified。

3. 名称：Sgl 蛋白趋同进化的系统发育与结构分析
   - 来源局限/观察：本文基于三个 Sgl 蛋白的结构比较提出趋同进化假说，但样本量小。
   - 核心假设：更多 Sgl 蛋白的结构比较将支持趋同进化假说，并可能发现新的结合模式。
   - 相对本文的增量：扩大样本量，进行系统发育分析。
   - 初步方法：从 NCBI 数据库挖掘更多 Sgl 蛋白序列，进行系统发育分析和结构预测。
   - 验证方式：对代表性 Sgl 蛋白进行 cryo-EM 结构解析。
   - 可能的失败模式：多数 Sgl 蛋白可能无法表达或纯化，结构解析困难。
   - 创新状态：unverified。

4. 名称：MD 模拟时长对膜蛋白-配体复合物稳定性评估的影响
   - 来源局限/观察：本文 MD 模拟仅 120 ns，可能不足以捕捉慢速构象变化。
   - 核心假设：延长模拟至微秒级将揭示 SglPP7 对 MurJ 构象动力学的更全面影响。
   - 相对本文的增量：从短时间模拟到长时间模拟的扩展。
   - 初步方法：对 MurJ/SglPP7 复合物进行微秒级 MD 模拟，比较不同时间尺度下的构象变化。
   - 验证方式：分析 RMSD、RMSF、构象聚类等指标随时间的变化。
   - 可能的失败模式：计算资源需求大，可能无法在合理时间内完成。
   - 创新状态：unverified。

5. 名称：脂质样密度在 MurJ 结构中的功能意义
   - 来源局限/观察：本文在 MurJ putative lipid II 结合槽中观察到脂质样密度，但无法确定分子种类。
   - 核心假设：该脂质样分子可能参与 MurJ 构象转变或 SglPP7 结合。
   - 相对本文的增量：从观察现象到功能验证。
   - 初步方法：使用 defined lipid II 类似物进行 cryo-EM 结构解析或结合实验。
   - 验证方式：比较有无脂质 II 时 MurJ/SglPP7 复合物的结构差异。
   - 可能的失败模式：脂质 II 可能无法在纯化过程中保留，或结构解析分辨率不足。
   - 创新状态：unverified。