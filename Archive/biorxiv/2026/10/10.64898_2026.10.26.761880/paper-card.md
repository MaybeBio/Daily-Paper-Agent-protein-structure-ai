## 01 基本信息
- **标题**：De novo design of light-controlled conformational protein switches
- **作者**：Alexander T. Hilditch; Nicolas M. Goldbach; Chenxuan Liu; Luciano A. Abriata; Ann-Sophie Kröll; Friederike C. Reinhardt; Sabine Aschenbrenner; Natalia Gasilova; Sarah Warrelmann; René Rasche; Yassine Faik; Kimali Pilet; Elisabetta Occelli; Sandrine Georgeon; Joseph Schmidt; Laure Menin; Joerg Standfuss; Josef Wachtveitl; Dominik Niopek; Bruno E. Correia
- **单位**：未在提供材料中逐条列出（通讯作者 Bruno E. Correia 隶属 EPFL，据致谢与 GitHub 组织 LPDI-EPFL 推断；其余单位未提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2026（日期 2026-10-28）
- **论文类型**：预印本（研究论文，含计算设计 + 实验验证）
- **领域**：计算蛋白质设计 / 光遗传学 / 蛋白质构象开关
- **关键词**：未提供（可据内容归纳：de novo design, retinal, conformational switch, optogenetics, RFdiffusion, ProteinMPNN, AlphaFold, NMR）
- **DOI/arXiv 号**：10.64898/2026.10.26.761880
- **代码**：https://github.com/LPDI-EPFL/sparc
- **数据**：PDB 34XO（SPARC-117 prot 晶体结构）；Zenodo 10.5281/zenodo.23063068（设计指标、模型、SPARC-152 主链归属）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文是「蛋白质结构相关计算研究 × AI/物理模拟」中**多构象设计（multistate design）** 的代表性工作：用 RFdiffusionAllAtom 生成配体异构驱动的替代构象、用 ProteinMPNN/LigandMPNN 做跨构象 tied 序列设计、用 AF2/AF3 做构象态过滤，并用 NMR/超快光谱/晶体学做物理验证。对构象采样、构象生成、结构/序列设计、蛋白-肽对接与光控 PPI 均有直接可迁移价值。

## 02 一句话总结
本文用 RFdiffusionAllAtom 在 11-cis-retinal 结合蛋白上扩散出与 all-trans-retinal 兼容的替代构象并同时扩散出肽结合位点，再用 ProteinMPNN/LigandMPNN 做跨构象 tied 序列设计、AF2/AF3 过滤，得到光照后结合增强 >30 倍的光激活异源二聚体（SPARC），并在 NMR 中观察到由 retinal 异构驱动的构象变化。

## 03 研究问题
- **具体问题**：能否完全从零（bottom-up）设计出同时具备（i）retinal 结合、（ii）retinal 异构驱动的构象变化、（iii）构象特异性的全新蛋白-蛋白相互作用（PPI）的蛋白质，从而在光照下形成异源二聚体？
- **为什么重要**：光遗传学工具箱依赖数量有限的天然光受体，其波长、动力学、动态范围、可改造性受限；de novo 设计可提供可定制、非天然优化的光响应模块。
- **现有方法为何不足**：已工程化的光响应蛋白多借用天然骨架与机制，或直接在 PPI 界面上挂光响应基团而绕过构象变化；小分子结合与构象变化仍是困难设计目标；构象集合生成/动态条件化 inverse folding 的通用性落后于单态方法。
- **精确研究问题**：Can de novo proteins be designed to couple retinal isomerisation to a defined backbone conformational change that unveils a conformation-specific protein-peptide interface, yielding light-activated heterodimers?

## 04 背景与发展脉络
- **阶段 1｜天然光受体借用**：以 rhodopsin、LOV、BLUF、Cry2、phytochrome 等天然模块为基础。优点：机制成熟、动态范围好；局限：波长多限于蓝光、分子量大、难以改造、跨语境移植差。
- **阶段 2｜光响应基团直接接界面**：用非天然氨基酸/光响应 moiety 直接调控 PPI，绕过构象变化。优点：设计简单；局限：需 genetic code expansion，缺乏天然光受体的构象耦合复杂度。
- **阶段 3｜de novo 单态设计**：深度学习推动小分子结合与单态结构设计。优点：可探索新序列空间；局限：多构象/动态设计仍困难。
- **阶段 4｜de novo 多构象/刺激响应设计**：钙控动态蛋白、helical hinge proteins、protein phosphoswitches 等。优点：证明构象变化可设计；局限：数量少，光控 + 配体异构耦合 + 构象特异 PPI 三者集成尚未实现。
- **本文主张的位置**：把 chromophore 结合、光驱动构象变化、构象特异 PPI 集成到同一 minimal scaffold，声称是「new-to-nature photoreceptors」。
- **脉络标注**：以上脉络为**仅本文框架**（依据 Introduction 与 Conclusions 的叙述整理），未做外部文献核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 光遗传学可用光受体少 | 工具箱依赖少量天然 photoreceptors | 天然蛋白按宿主需求进化，难移植、难改造 | Introduction |
| 光响应蛋白机制复杂 | 需整合 chromophore、化学变化→构象变化→下游效应 | 需定义并生成两个以上可设计且可过渡的构象 | Introduction |
| 小分子结合与构象变化设计困难 | 单态方法通用性好，动态/多态方法落后 | 多构象设计需同时满足可设计性与可行结构过渡 | Introduction |
| retinal 在可溶蛋白中未被使用 | 其与可溶光响应蛋白的兼容性未被探索 | retinal 天然用于膜结合 rhodopsin | Introduction |
| 单态设计限制异构化 | 单态 RBP 只显示长寿命 ESA/GSB→HGS，无异构 | 结构刚性阻碍 retinal 异构 | Results 图 3h |
| 初始光激活响应弱 | SPARC-39 仅 1.5 倍 | 未明确归因，作者通过扩大可设计位点优化 | Results 图 3b、Supplementary Fig. 6 |
| 正交性难实现 | 前四名设计两两不正交 | 序列与结构高度相似 | Results、Supplementary Figs. 14 & 15 |
| 细胞内受体激活弱 | 初始 SPARC 对 FGFR1 几乎无响应 | 作者推测异源二聚体解离过快 | Results、Supplementary Fig. 24 |

## 06 核心思想
1. **表面方法**：从实验验证的 retinal 结合蛋白（RBP）出发，in silico 把 11-cis-retinal 异构为 all-trans，用 RFdiffusionAllAtom 扩散与 all-trans 冲突的部分并同时扩散一段 25–30 aa 肽，形成光激活构象；用 ProteinMPNN/LigandMPNN 跨两态 tied 设计序列，AF2/AF3 过滤。
2. **核心洞察**：把「配体异构」当作构象切换的驱动力，把「新构象」当作构象特异 PPI 的载体；即用配体状态耦合蛋白构象态，再用构象态门控 PPI。单态设计会锁死异构化，多态设计才释放功能。
3. **可能的普适教训 [Analysis]**：多构象设计不只是「生成两个结构」，而是要让两态共享同一序列（tied design）且过渡可行；配体/辅基可作为外部刺激把构象平衡推向功能态，这一逻辑可推广到其他刺激响应（pH、金属、光）体系。

## 07 方法总览
- **输入**：实验验证的 RBP 结构（AF3 模型）、11-cis-retinal、目标折叠（4/5/6-helix bundle、β-barrel）、天然 rhodopsin 序列库（UniRef100）。
- **输出**：光激活异源二聚体（SPARC prot + SPARC pep）序列与模型；晶体结构；NMR 归属；细胞内功能数据。
- **模块**：RBP 设计（RFdiffusion partial diffusion + SolubleMPNN + AF2 + Rosetta MotifGraft + Gnina docking + LigandMPNN + AF2/AF3）；SPARC 设计（RDKit 异构 + RFdiffusionAllAtom + ProteinMPNN/LigandMPNN tied + AF2/AF3）；序列空间分析（ESM2 + UMAP）；实验验证（吸收光谱、native/top-down MS、CD、split-luciferase、超快光谱、晶体学、NMR、细胞内钙成像）。
- **训练**：无新模型训练；使用预训练 RFdiffusion/RFdiffusionAllAtom、ProteinMPNN、LigandMPNN、SolubleMPNN、AF2、AF3、ESM2、Gnina。
- **工具**：RFdiffusion、ProteinMPNN、LigandMPNN、SolubleMPNN、AlphaFold2/3、Rosetta MotifGraft、Gnina、RDKit、ESM2、UMAP、DSSP、NMRtist/ARTINA、Sparky、BIOP-Desktop、Cellpose-SAM。
- **反馈回路**：计算设计 → 实验筛选（吸收/发光）→ 命中 → 计算优化（扩大可设计位点）→ 再实验 → 理性工程（电荷互换、红移突变、亲和力突变、scaffolding）。
- **假设**：retinal 异构可传递为 backbone 构象变化；两态可共享序列；新构象可承载构象特异 PPI。
- **文字流程**：选折叠 → 生成多样化 backbone → 嫁接 Schiff base 关键 Lys/Glu → dock 11-cis-retinal → 重设计核心 → AF2/AF3 过滤 → 实验验证 RBP → RDKit 异构为 all-trans → RFdiffusionAllAtom 扩散冲突区 + 扩散肽 → tied 多态序列设计 → AF2/AF3 过滤 → split-luciferase 筛选 → 优化与工程 → 细胞与 NMR 验证。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| RFdiffusion partial diffusion | 生成多样化 backbone | 增加可设计性 | 起始折叠→500 backbones | Methods | 预期降低设计成功率（未实测消融） |
| SolubleMPNN + AF2 单序列 | 筛选可设计 backbone | AF 模型比 RFdiffusion backbone 更可设计 | backbone→序列/结构 | Methods | 预期保留低质量 backbone（未实测） |
| Rosetta MotifGraft | 植入 Schiff base 的 Lys/Glu | 需要质子化 Schiff base 与 counter-ion | backbone→graft | Methods | 预期无法形成质子化 Schiff base（未实测） |
| Gnina docking | 共价 dock 11-cis-retinal | 需要合理配体姿态 | graft→10 poses | Methods | 预期配体姿态错误（未实测） |
| LigandMPNN 核心重设计 | 围绕配体设计口袋 | 生成结合序列 | pose→50 序列 | Methods | 预期结合失败（未实测） |
| AF2/AF3 过滤（RBP） | 选配体 pLDDT>70、姿态一致 | 提高命中率 | 序列→筛选 | Methods | 预期命中率下降（未实测） |
| RDKit 异构 | 生成 all-trans 构象 | 模拟光激活 | 11-cis→all-trans | Methods | 无异构则无切换（概念必需） |
| RFdiffusionAllAtom | 扩散冲突区 + 扩散肽 | 生成替代构象与结合位点 | RBP→新构象+肽 | Methods | 预期无光激活 PPI（未实测消融） |
| ProteinMPNN/LigandMPNN tied design | 两态共享序列 | 保证同一序列可访问两态 | 两态→序列 | Methods | 预期两态不兼容（未实测） |
| AF2/AF3 双态过滤 | 选 pLDDT>80、iPTM>0.7、异构态、4–6 Å RMSD | 保证构象变化 | 序列→筛选 | Methods | 预期假阳性升高（未实测） |
| Split-luciferase 筛选 | 检测光激活结合 | 高通量 | 裂解液→发光 | Results 图 3a | 无此筛选则无法快速筛选 92+60 设计 |
| 超快光谱 | 检测 retinal 异构 | 验证机制 | 蛋白→瞬态吸收 | Results 图 3h,i | 无法区分单态/多态机制 |
| NMR in situ 光照 | 观察构象变化 | 溶液实时验证 | 蛋白→HSQC | Results 图 5 | 无法证明构象变化与肽结合 |
| 晶体学 | 验证暗态结构 | 结构保真度 | 蛋白→结构 | Results 图 3g | 仅暗态，无法验证光态 |

## 09 关键公式符号
- **MRE 计算**（Methods，CD）：MRE = θ / (c · l · b)，θ 为毫度椭圆率差，c 为蛋白浓度 (mM)，l 为光程 (cm)，b 为酰胺键数。用途：归一化 CD 信号。
- **mCSP**（Methods，NMR）：对 cis-retinal 蛋白中每个已归属 crosspeak，计算其到目标谱所有 crosspeak 在 CSP 空间的距离，取最近者赋给该残基。用途：量化化学位移扰动。
- **Schiff base 质量偏移**：+266.2035 Da（retinal Schiff base 单同位素质量，C20H26）。用途：MS 验证。
- 其余公式未提供。

## 10 实验设计与证据链
- **数据集/群体**：92 个初始异源二聚体设计 + 60 个优化设计；40 个 scaffolded miniprotein；天然 rhodopsin 序列 71,663 条（过滤后 60,273 microbial + 11,365 visual）+ 27 个 de novo 蛋白；HEK-293T、CHO-R1c 细胞。
- **规模**：RBP 设计成功率 2.5%（β-barrel）–13.5%（5-helix bundle）；SPARC-39 1.5 倍；优化后 23/60 有响应，4 个 >7 倍，SPARC-111 >30 倍；SPARC-111 + SPARC-141pep-S14A + I28D 组合 95 倍。
- **指标**：发光 fold-change、吸收红移、MS 质量偏移、CD 热稳定性、Cα RMSD、NMR CSP、钙响应。
- **基线**：无 retinal 对照、K76A 突变、单态 RBP 5HB-87、天然 bovine rhodopsin 光谱。
- **预算**：未提供。
- **骨干/仪器**：Tecan Spark/Infinite MPLEX、Orbitrap Exploris 240、Chirascan V100、Bruker 800 MHz NMR、Nikon Crest X-Light V3、Diamond i24。
- **oracle 输入**：晶体结构、NMR 归属、MS 碎片为实验真值；AF2/AF3 为计算 oracle。
- **评测协议**：裂解液/纯化蛋白 split-luciferase、三次连续光照、细胞内 NanoGlo Live Cell、钙成像 300–400 细胞。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| RBP 吸收筛选 | de novo 可结合 retinal | 多种折叠，±retinal | 红移 440–530 nm，成功率 2.5–13.5% | 可 de novo 设计 retinal 结合 | 不证明高亲和力或天然级光谱 | Results 图 2a |
| Native/top-down MS | Schiff base 形成与位点 | +266 Da | 确认修饰与位点 | 共价结合正确 | 不证明异构效率 | Results 图 2b |
| ESM2+UMAP | 探索新序列空间 | vs 天然 rhodopsin | de novo 独立聚类 | 序列空间新颖 | 不证明功能更优 | Results 图 2c |
| Split-luciferase 筛选 | 光激活结合 | 92 设计，±retinal，±光照 | 1/92 命中（SPARC-39，1.5 倍） | 概念可行 | 不证明高动态范围 | Results 图 3b |
| K76A / 无 retinal | 响应特异性 | 突变/缺配体 | 完全消失 | 依赖 retinal Schiff base | 不证明唯一机制 | Results |
| 优化设计 | 扩大可设计位点提升响应 | 60 设计 | 23 有响应，4 个 >7 倍，SPARC-111 >30 倍 | 多态设计可优化 | 不证明可预测 | Results 图 3e |
| 晶体学 | 暗态结构保真 | SPARC-117 prot | Cα RMSD 0.92 Å | 设计结构准确 | 未解析 retinal 密度，未验证光态 | Results 图 3g |
| 超快光谱 | retinal 异构 | 单态 vs 多态 | 单态无异构，多态有异构 | 多态设计释放异构 | 不证明异构速率天然级 | Results 图 3h,i |
| 电荷互换 | 正交性 | SPARC-111 ortho | 保持响应且正交 | 界面可理性改造 | 仅一对 | Results 图 4a |
| 红移突变 | 波长可调 | I28D 等 | 红移 ≤30 nm，I28D 提升响应 | 波长可调 | 未达正交激活 | Results 图 4b |
| 亲和力突变 | 灵敏度可调 | S14A 等 | 4.5 倍提升，组合 95 倍 | 亲和力可调 | 细胞内未提升 | Results 图 4c |
| Scaffolding | 肽可折叠化 | 40 miniprotein | >半数有响应 | 效应域可改造 | 未全部优于亲本 | Results 图 4d |
| 细胞内 split-luc | 活细胞 PPI | HEK-293T | 光激活，多次可重复 | 活细胞可用 | 优化突变未提升 | Results 图 4e |
| FGFR1 钙成像 | 控制受体信号 | ±SpyTag/SpyCatcher | 需共价锁，改进组合响应更好 | 可控制受体聚类 | 需共价锁，弱于现有工具 | Results 图 4f |
| NMR in situ | 构象变化机制 | ±肽，±光照，all-trans | 四态，光激活后谱变宽/分裂 | 支持设计机制 | 未捕获中间态 | Results 图 5 |

## 11 结论正确解读
- **任务范围**：设计并验证光激活异源二聚体，非通用光遗传学工具。
- **oracle/真值输入**：晶体结构、NMR 归属、MS 为实验真值；AF2/AF3 为计算过滤，非真值。
- **端到端状态**：从计算设计到细胞功能已打通，但细胞内效力需共价锁辅助。
- **算力成本**：未提供。
- **历史数据依赖**：依赖预训练模型与天然 rhodopsin 序列库。
- **模型依赖**：RFdiffusionAllAtom、ProteinMPNN/LigandMPNN、AF2/AF3 的偏差会影响结果。
- **最难情形**：正交激活、红移、细胞内高信噪比、retinal 在可溶蛋白组中的可用性。
- **群体/领域边界**：体外 + 两种细胞系；未在体内/神经元验证。
- **不确定性**：晶体中 retinal 密度未解析；NMR 未捕获中间态；优化突变在细胞内未提升。
- **有边界复述**：本文证明 de novo 多态设计可产生光激活异源二聚体，并在体外与细胞中实现光控 PPI 与受体聚类，但动态范围、正交性、细胞内效力仍有限。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 波长红移不足 | 多数设计吸收短于 rhodopsin，红移突变不足以正交激活 | 创建红移激活波长以改善穿透 | Conclusions |
| 细胞内效力不足 | 需共价锁辅助受体激活 | 进一步探索细胞内更广功能 | Conclusions |
| retinal 可溶蛋白组可用性不明 | 因 retinal 溶解度 | 可用 hydroxy-retinal 衍生物缓解 | Conclusions |
| 信号信噪比 | 未明确量化 | 改善 switch 信噪比 | Conclusions |

**作者提及的相关约束（非正式局限）**：SPARC-39 响应弱；优化突变在细胞内未提升；晶体中 retinal 密度未解析。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 92 设计仅 1 命中 | 命中率低，可能依赖筛选噪声 | 影响可重复性与通用性 | 独立重复筛选、统计置信区间 | Results 图 3b |
| SPARC-111 与 SPARC-39 序列差异 23.5% 但结构几乎相同 | 功能提升可能来自表达/稳定性而非构象切换 | 影响机制归因 | 测表达量、热稳定性、动力学 | Results 图 3f |
| 超快光谱仅 4 个多态设计 | 样本小，异构结论可能不普遍 | 影响机制普适性 | 扩大样本、测更多设计 | Results 图 3i |
| NMR 未捕获中间态 | 构象路径可能非设计路径 | 影响机制模型 | 时间分辨 NMR/停流 | Results 图 5 |
| 细胞内优化突变未提升 | 体外-体内不一致 | 影响转化 | 测细胞内表达/定位/半衰期 | Results 图 4e |
| FGFR1 需 SpyTag/SpyCatcher | 共价锁可能改变机制 | 影响「光控」纯度 | 无锁条件下测动力学 | Results 图 4f |
| 晶体未解析 retinal 密度 | 暗态配体姿态未直接验证 | 影响设计保真度 | 更高分辨率/不同晶体形式 | Results 图 3g |
| 正交性仅一对 | 通用性未知 | 影响并行控制 | 设计更多正交对 | Results 图 4a |

## 14 学到什么
**Agent 提炼的知识候选**
- **多构象 tied design 流程**：用配体异构生成替代构象 → 扩散冲突区 → 同时扩散结合伙伴 → 跨态 tied 序列设计 → 双态 AF 过滤。可迁移到构象采样/构象生成与结构/序列设计。
- **配体作为构象开关**：把配体状态耦合到蛋白构象平衡，再用构象态门控 PPI。可迁移到金属/pH/光响应设计。
- **单态 vs 多态机制验证**：超快光谱可区分「结合但不异构」与「结合且异构」，是构象设计的重要物理验证手段。
- **NMR in situ 光照**：光纤耦合 LED 在磁体内实时光照，可追踪构象景观。可迁移到其他光响应蛋白。
- **理性工程组合**：电荷互换实现正交、红移突变、亲和力突变、scaffolding。可迁移到 PPI 设计。
- **序列空间分析**：ESM2 + UMAP 评估设计新颖性。可迁移到设计评估。
- **筛选策略**：split-luciferase 裂解液筛选 + 纯化验证 + 细胞内验证的分层策略。

## 15 与已有知识连接
- **相似**：RFdiffusion/RFdiffusionAllAtom、ProteinMPNN/LigandMPNN、AF2/AF3 为课题常用工具；多态设计与 phosphoswitch、hinge protein 等工作同源（本文引用）。
- **组合**：retinal 化学 + 构象设计 + PPI 设计 + 细胞信号控制。
- **冲突**：与「单态设计足够」的假设冲突；本文显示单态锁死异构。
- **可迁移领域**：构象采样、构象生成、分子对接（Gnina）、MD/超快光谱、结构/序列设计、光遗传学。
- **外部核验**：未提供；以上连接基于本文引用与课题常识，未做外部文献核验。

## 16 研究想法
**Agent 生成的研究候选**
1. **名称**：多刺激耦合的多态蛋白开关
   - **来源局限**：本文仅用 retinal 光控。
   - **核心假设**：同一 scaffold 可耦合两种刺激（光 + pH/金属）到不同构象态。
   - **增量**：从单刺激扩展到多刺激逻辑门。
   - **初步方法**：在 SPARC 口袋引入金属配位残基，用 RFdiffusionAllAtom 生成第三态。
   - **验证**：吸收/NMR/发光。
   - **失败模式**：态间过渡不可行。
   - **创新状态**：unverified。
2. **名称**：用 MD 验证 SPARC 构象过渡路径
   - **来源局限**：本文未做 MD，NMR 未捕获中间态。
   - **核心假设**：all-trans 态到肽结合态存在可行路径。
   - **增量**：补足构象过渡的物理证据。
   - **初步方法**：增强采样 MD（metadynamics/REMD）。
   - **验证**：与 NMR CSP 对比。
   - **失败模式**：力场偏差。
   - **创新状态**：unverified。
3. **名称**：正交 SPARC 对的自动化设计
   - **来源局限**：仅一对正交。
   - **核心假设**：电荷模式可系统化生成正交对。
   - **增量**：并行光控。
   - **初步方法**：界面电荷设计 + AF3 过滤。
   - **验证**：交叉配对发光。
   - **失败模式**：交叉反应。
   - **创新状态**：unverified。
4. **名称**：红移 SPARC 的定向进化
   - **来源局限**：红移 ≤30 nm。
   - **核心假设**：口袋极性可进一步红移。
   - **增量**：改善组织穿透。
   - **初步方法**：易错 PCR + 吸收筛选。
   - **验证**：光谱 + 发光。
   - **失败模式**：牺牲异构效率。
   - **创新状态**：unverified。
5. **名称**：SPARC 用于构象特异 PPI 的通用平台
   - **来源局限**：仅验证少数 PPI。
   - **核心假设**：SPARC prot 可替换效应肽。
   - **增量**：通用光控 PPI 工具箱。
   - **初步方法**：RFdiffusion 生成新肽 + tied design。
   - **验证**：发光/细胞。
   - **失败模式**：肽不折叠。
   - **创新状态**：unverified。