## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present HDOCK-Multimer (HDM), a framework integrating docking and combinatorial assembly for structure prediction of large protein complexes. They claim HDM reduces reliance on subcomponent quality through docking while leveraging pairwise interactions via assembly, and that it substantially outperforms CombFold, MoLPC, AlphaFold-Multimer, and AlphaFold3 on three benchmarks (35 large heteromeric complexes, 172 large protein complexes, 7 CASP15 targets). They further claim HDM can predict stoichiometry and model complexes without stoichiometry input.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, or methodological descriptions are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, benchmark definitions, evaluation metrics, statistical analyses, and comparison protocols

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable approach to a significant problem in structural biology, namely the prediction of large protein complex structures. The proposed integration of docking and combinatorial assembly is conceptually reasonable and addresses a known limitation of end-to-end deep learning methods. However, the abstract provides no quantitative evidence to support the central claims of substantial improvement over state-of-the-art methods. Without access to the underlying data, methodology, and benchmark details, the case is not established from the supplied material. The stoichiometry prediction claim is intriguing but entirely unsupported in the abstract.
- **Who would be interested in the results, and why** Structural biologists, computational biologists, and researchers working on protein-protein interactions and complex assembly would be interested. The work addresses a practical bottleneck in applying deep learning methods to large assemblies, which is relevant to fields such as drug discovery, enzyme engineering, and understanding macromolecular machines. The potential to predict stoichiometry without input would be of particular interest to experimentalists who often lack this information.
- **Major strengths** The problem addressed is important and timely, as large protein complexes remain challenging for current end-to-end approaches. The conceptual framework of combining docking and assembly is a sensible strategy that could offer practical advantages. The claimed breadth of evaluation across multiple benchmarks and comparison to several state-of-the-art methods suggests a thorough benchmarking effort, if the claims are substantiated in the full manuscript.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "HDM substantially outperforms state-of-the-art methods including CombFold, MoLPC, AlphaFold-Multimer and AlphaFold3"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that HDM "substantially outperforms" four state-of-the-art methods across three benchmarks, but provides no quantitative metrics, no statistical significance testing, and no description of the evaluation criteria. The term "substantially" is undefined.
  - **Why it matters** The central claim of the work rests on this performance comparison. Without quantitative data, the reader cannot assess the magnitude of improvement, whether it is consistent across benchmarks, or whether it is statistically meaningful. This is the core evidence needed to establish the value of the method.
  - **Resolution test** Provide performance metrics (e.g., TM-score, DockQ, lDDT) for HDM and each comparator on each benchmark, with measures of variance and statistical significance. Define "substantial" in operational terms.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological transparency
  - **Claim pointer** "HDM efficiently reduces reliance on subcomponent quality through docking, while leveraging the pairwise interactions of subcomponents through assembly"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract describes the conceptual framework but provides no details on how docking and assembly are integrated, how the combinatorial space is managed, what docking method is used, how pairwise interactions are scored, or how the assembly is optimized. The claim that HDM "reduces reliance on subcomponent quality" is not supported by any ablation or sensitivity analysis.
  - **Why it matters** The novelty and technical contribution of the work depend on the specific integration strategy. Without methodological detail, the reader cannot evaluate whether the approach is genuinely new, reproducible, or likely to generalize. The claim about reduced reliance on subcomponent quality is a key differentiator and requires direct evidence.
  - **Resolution test** Describe the algorithm in sufficient detail for reproduction. Provide ablation studies showing performance as a function of subcomponent quality, and compare against a pure docking or pure assembly baseline.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support
  - **Claim pointer** "HDM also demonstrates the capacity to predict the stoichiometry and model the complex without stoichiometry input"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** This is a significant additional claim, but the abstract provides no information on how stoichiometry is predicted, on which benchmarks this was tested, what accuracy was achieved, or how it compares to existing stoichiometry prediction methods.
  - **Why it matters** Stoichiometry prediction is a distinct and challenging problem. If substantiated, this would broaden the applicability of the method considerably. However, as stated, the claim is unverifiable and could overstate the method's capabilities.
  - **Resolution test** Provide a dedicated section with stoichiometry prediction results, including benchmark details, accuracy metrics, and comparison to relevant baselines.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Benchmark description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The three benchmarks are described as "35 large heteromeric complexes, 172 large protein complexes and 7 CASP15 targets." It is unclear whether these are overlapping or distinct sets, and what defines "large."
  - **Required correction** Clarify the relationship between the benchmark sets and provide a definition of "large" (e.g., number of chains, total molecular weight, or interface size).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Comparison scope
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract compares HDM to CombFold, MoLPC, AlphaFold-Multimer, and AlphaFold3, but does not mention other relevant docking-based or assembly-based methods that might be expected in a comprehensive comparison.
  - **Required correction** Justify the choice of comparators or acknowledge other methods in the full manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Availability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** No mention is made of code availability, web server access, or data availability, which is important for a methods paper in computational science.
  - **Required correction** State in the abstract or full manuscript where the software and benchmark data can be accessed.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative evidence for the central performance claim), R1-M2 (insufficient methodological detail to assess novelty and reproducibility), R1-M3 (unsupported stoichiometry claim). These are blocking because the abstract alone does not establish the core contributions of the work.
- **Assessment against Nature-style criteria**  
  Originality: The conceptual integration of docking and assembly is not entirely new, but the specific framework may offer a novel combination. This cannot be fully assessed without methodological detail.  
  Scientific importance: The problem of large protein complex prediction is of high importance, and a method that addresses it effectively would be valuable. The potential stoichiometry prediction adds further significance.  
  Interdisciplinary readership: The topic bridges computational biology, structural biology, and bioinformatics, and would appeal to a broad interdisciplinary audience if the claims are substantiated.  
  Technical soundness: Cannot be assessed from the abstract. The lack of quantitative results and methodological detail prevents evaluation of the technical rigor.  
  Readability for nonspecialists: The abstract is clear and accessible, with the conceptual framework explained in plain terms. However, the absence of concrete results weakens its impact for a general readership.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible and potentially important approach, but the central claims are unsupported by quantitative data or methodological detail. A supportive recommendation would require the full manuscript to provide rigorous benchmarking, statistical analysis, and a complete description of the method.

## Risk / unsupported claims
- The claim of "substantially outperforms" all four state-of-the-art methods is unsupported in the abstract, as no metrics or statistical analyses are provided.
- The claim that HDM "efficiently reduces reliance on subcomponent quality" is unsupported, as no ablation or sensitivity analysis is described.
- The claim of stoichiometry prediction capability is unsupported, as no results or methodology are provided.
- The generalizability of the method across different types of large complexes cannot be assessed from the abstract alone.