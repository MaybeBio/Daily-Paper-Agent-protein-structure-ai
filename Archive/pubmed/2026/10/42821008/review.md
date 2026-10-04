## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full text, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors present a perspective on computational methods for identifying allosteric and cryptic binding pockets, covering physics-based approaches (geometry/energetics-based pocket detection, molecular simulations, mixed-solvent/probe methods) and AI/ML approaches (PocketMiner, AlphaFold3, Boltz), and claim that AI/ML methods are over 1,000-fold faster than classical simulations. They aim to define domains of applicability, highlight strengths and limitations, and identify integration opportunities in prospective drug discovery.
- **Visible evidence base** Abstract text only; no figures, tables, references, or benchmark data provided
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, benchmark study details, specific performance metrics, method comparison data, and any case studies or validation results

## Reviewer
- **Overall assessment** This perspective addresses a timely and important topic in computational drug discovery. The abstract provides a reasonable high-level overview of the method landscape, but the claims regarding speed advantages and the stated aims of defining applicability domains cannot be evaluated from the abstract alone. The manuscript may be of interest to computational chemists and drug discovery scientists, but the evidence base provided is insufficient to assess the depth and rigor of the analysis.
- **Who would be interested in the results, and why** Computational chemists, structural biologists, and drug discovery scientists working on challenging targets would be interested in a practical overview of available tools for allosteric and cryptic pocket discovery. The comparison of physics-based and AI/ML approaches, if well-executed, could help practitioners select appropriate methods for their projects.
- **Major strengths** The topic is highly relevant and addresses a recognized gap in computational drug discovery. The abstract covers a broad spectrum of methods, from classical simulation techniques to cutting-edge AI models, which suggests a comprehensive scope. The explicit mention of benchmark studies and domains of applicability indicates an intention to provide practical guidance.
- **Major Concerns** 
  - R1-M1
  - R1-M2
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The quantitative claim of "over 1,000-fold faster" requires substantiation with specific benchmark data and clear definitions of what is being compared. The abstract does not provide evidence for the claimed speed advantage, nor does it clarify whether this refers to wall-clock time, computational cost, or sampling efficiency.
- **Assessment against Nature-style criteria** 
  - Originality: The topic is not new, but the perspective format may offer a useful synthesis. The abstract does not reveal a novel conceptual framework or unique insight that would distinguish it from existing reviews.
  - Scientific importance: High, given the relevance of allosteric and cryptic sites to drug discovery for challenging targets.
  - Interdisciplinary readership: Moderate. The abstract is accessible to computational scientists but may be less engaging for experimental biologists or medicinal chemists without specific interest in computational methods.
  - Technical soundness: Cannot be assessed from the abstract. The claims require verification against the full manuscript.
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon (e.g., "mixed-solvent and probe-based approaches", "cofolding models") that may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient material to evaluate the scientific claims or the quality of the perspective. A decision would require access to the full manuscript.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that AI/ML methods such as PocketMiner and deep learning cofolding models are "over 1,000-fold faster than classical simulations."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The quantitative speed claim is presented without any supporting data, benchmark details, or definition of the comparison basis. It is unclear whether this refers to inference time, total workflow time, or sampling efficiency, and whether the comparison is apples-to-apples across different hardware, software versions, and problem sizes.
- **Why it matters** A specific quantitative claim of this nature is likely to be cited and used by practitioners to justify method selection. Without rigorous benchmarking data, the claim could be misleading and may not hold across different target classes or simulation protocols.
- **Resolution test** Provide benchmark data with clear methodology, including hardware specifications, system sizes, simulation lengths, and the specific metrics used for the speed comparison. Ideally, include a table or figure showing the performance comparison across multiple test cases.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope and depth of analysis
- **Claim pointer** The abstract states that the authors "aim to define their domains of applicability, highlight their strengths and limitations, and identify opportunities for their integration in prospective drug discovery."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not provide any indication of the criteria used to define domains of applicability, the nature of the strengths and limitations discussed, or the specific integration opportunities proposed. Without this information, it is impossible to assess whether the perspective offers substantive guidance or merely lists methods.
- **Why it matters** A perspective that claims to define applicability domains must provide a clear analytical framework, supported by evidence from benchmark studies or case examples. The absence of any such detail in the abstract raises questions about the depth of the analysis.
- **Resolution test** In the full manuscript, provide a structured framework for method selection, supported by comparative benchmark data and case studies. Summarize key findings in the abstract, such as specific scenarios where one method class outperforms another.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "cryptic pockets" is used without a definition. While specialists may understand the term, nonspecialist readers may benefit from a brief explanation.
- **Required correction** Add a brief parenthetical definition, such as "pockets that are not visible in apo structures but appear transiently during simulations or in holo states."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of method coverage
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions specific tools (Fpocket, SiteMap, SILCS, MixMD, PocketMiner, AlphaFold3, Boltz) but does not indicate whether other widely used methods are covered in the full manuscript.
- **Required correction** In the full manuscript, clarify the selection criteria for included methods and acknowledge any notable omissions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "mixed-solvent and probe-based approaches" may be unclear to readers unfamiliar with these techniques.
- **Required correction** Provide a brief explanation of what these approaches entail, such as "methods that use cosolvent molecules or small probes in simulations to identify favorable binding sites."

## Risk / unsupported claims
- The claim that AI/ML methods are "over 1,000-fold faster than classical simulations" is unsupported in the abstract and cannot be evaluated without benchmark data.
- The statement that computational methods "remain underutilized" for allosteric and cryptic site discovery is presented without supporting evidence or citation.
- The abstract implies that the perspective will provide practical guidance on method selection, but no evidence of such guidance is visible in the abstract.
- The claim that allosteric and cryptic pockets offer routes to "biological targets historically considered undruggable" is a general assertion that requires contextual support in the full manuscript.