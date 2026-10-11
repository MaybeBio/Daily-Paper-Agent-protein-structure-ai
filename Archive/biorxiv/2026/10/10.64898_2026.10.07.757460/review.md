## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a computational pipeline for de novo design of glycoproteins in which amino acid sequence encodes both the location and composition of N-linked glycans. They claim that steric restriction, tuned through three-dimensional protein structure, progressively reduces glycan processing, shifting glycans from complex-type to oligomannose-type structures. They further claim that the resulting oligomannose glycans remain functionally accessible, as demonstrated by inhibition of uropathogenic Escherichia coli adhesion to human bladder cells and binding to mannose-binding lectin.
- **Visible evidence base** Abstract text only; no experimental data, structural models, statistical analyses, or methodological details are available for assessment
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, supplementary information, sequence and structure data, experimental protocols, and raw or processed quantitative results

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing and potentially significant advance in computational glycoprotein design. The central idea, that steric occlusion can be programmed into designed proteins to control N-glycan processing, is novel and could have broad implications for glycobiology and protein engineering. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, reproducibility, or robustness of the claims. Key quantitative outcomes, structural validations, and experimental controls are not described. The functional assays are mentioned but not contextualized with effect sizes, replicates, or statistical significance. The claim that glycan composition is "encoded" by sequence is plausible but not established from the supplied material. The work is likely to interest glycobiologists, protein designers, and infectious disease researchers, but the case is not yet established from the abstract alone.
- **Who would be interested in the results, and why** Glycobiologists and glycoprotein engineers would be interested in the demonstration that glycan composition can be programmed through protein design. Computational protein designers would value the extension of design principles to glycoproteins. Researchers studying host-pathogen interactions, particularly those focused on uropathogenic E. coli and mannose-binding lectin, would be interested in the functional validation. The potential to produce glycoproteins with defined glycan profiles could also attract biopharmaceutical researchers interested in glycoengineering.
- **Major strengths** The conceptual advance is clear and compelling. The idea of using steric restriction to control glycan processing is elegant and potentially generalizable. The abstract connects design principles to functional outcomes, which strengthens the potential impact. The use of a uropathogenic E. coli adhesion model and mannose-binding lectin binding provides biologically relevant readouts.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality. The concept of programming N-glycan composition through steric control in de novo designed proteins appears original. No prior work is cited in the abstract, and the approach is distinct from existing glycoengineering strategies. However, originality cannot be fully assessed without a literature context.  
  Scientific importance. If the claims are substantiated, the work would represent a significant advance in both glycobiology and protein design. The ability to encode glycan composition genetically could enable new applications in vaccine design, therapeutics, and basic glycobiology. The importance is high, but it is contingent on the robustness of the evidence.  
  Interdisciplinary readership. The work bridges computational protein design, glycobiology, and infectious disease. The abstract is written in a way that is accessible to a broad scientific audience, though some glycobiology terminology may require familiarity. The potential readership is broad.  
  Technical soundness. Not assessable from the abstract. No methodological details, structural validations, or quantitative data are provided. The central claims rest on experimental evidence that is not visible.  
  Readability for nonspecialists. The abstract is clearly written and logically structured. The key concepts are introduced with sufficient context. The functional assays are described in accessible terms.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual advance is promising, and the work could be suitable for a high-impact venue if the technical concerns are resolved with full data. The recommendation is supportive in principle but conditional on the availability of rigorous experimental evidence.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** The method "uses three-dimensional protein structure to tune glycan accessibility to processing enzymes" and "systematic increases in steric restriction progressively reduced processing."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract claims a systematic relationship between steric restriction and glycan processing, but no quantitative data are presented. There is no description of how steric restriction was measured, how processing was quantified, or how many designed proteins were tested. The claim of "progressive" reduction implies a dose-response relationship that cannot be evaluated without data.  
- **Why it matters** The central design principle rests on this relationship. Without quantitative evidence, the claim that steric control is a general and tunable design parameter is unsupported.  
- **Resolution test** Provide data showing glycan processing outcomes for multiple designed proteins with varying degrees of steric restriction, including quantitative glycan profiling and structural validation of the designed steric environment.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** "The resulting oligomannose glycans remained accessible for biological recognition, inhibiting uropathogenic Escherichia coli adhesion to human bladder cells and binding mannose-binding lectin."  
- **Evidence pointer** Location not provided  
- **Concern** The functional assays are mentioned without any quantitative context. No effect sizes, replicate numbers, statistical tests, or controls are described. It is unclear whether the inhibition of E. coli adhesion is specific to the designed glycoproteins or whether mannose-binding lectin binding is comparable to natural oligomannose glycans.  
- **Why it matters** The functional relevance of the designed glycans is a key claim. Without quantitative and statistical support, the biological significance cannot be assessed.  
- **Resolution test** Provide dose-response curves, appropriate positive and negative controls, replicate numbers, and statistical analyses for both functional assays.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "We develop a general all-atom computational pipeline for creating de novo glycoproteins in which the amino acid sequence encodes both the location and composition of N-linked glycans."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract does not describe the computational method in any detail. There is no information on the scoring function, the sampling strategy, the treatment of glycan conformations, or the validation of the designed structures. The claim of "general" applicability is not supported by any demonstration of breadth.  
- **Why it matters** The computational pipeline is the foundation of the work. Without methodological detail, the approach cannot be evaluated for novelty, robustness, or reproducibility.  
- **Resolution test** Provide a detailed methods section, including benchmarks, validation against known glycoprotein structures, and demonstration of the pipeline on multiple design targets.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** "These results establish steric control of N-linked glycan processing as a genetically encodable design principle."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract does not demonstrate that the glycan composition is stably inherited or consistently reproduced across expression batches, cell types, or experimental replicates. The term "genetically encodable" implies a robust and reproducible relationship between sequence and glycan outcome, which is not established.  
- **Why it matters** The claim of genetic encodability is central to the potential utility of the approach. Without evidence of reproducibility and stability, the design principle may not be generalizable.  
- **Resolution test** Provide data on glycan composition reproducibility across multiple expression experiments, and ideally across different expression systems or cell lines.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Location not provided  
- **Issue** The phrase "heterogeneous complex-type structures" is used without defining what heterogeneity means in this context. It is unclear whether this refers to variability in glycan branching, terminal modifications, or other features.  
- **Required correction** Define the specific features of complex-type glycans that are being compared, or provide a reference for the classification.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Abstract background  
- **Evidence pointer** Location not provided  
- **Issue** The abstract does not mention any prior attempts at glycan engineering or computational glycoprotein design. This makes it difficult to assess the novelty of the approach relative to existing methods.  
- **Required correction** Add a brief statement of prior work and how the current approach differs from or advances beyond it.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Functional assay description  
- **Evidence pointer** Location not provided  
- **Issue** The abstract states that the designed glycoproteins inhibit E. coli adhesion and bind mannose-binding lectin, but does not specify whether these are independent assays or whether the same glycoprotein constructs were used in both.  
- **Required correction** Clarify whether the same set of designed glycoproteins was used in both assays, and specify the relevant controls.

## Risk / unsupported claims
- The claim that the method is "general" is unsupported without demonstration on multiple design targets.
- The claim of a "systematic" and "progressive" relationship between steric restriction and glycan processing is unsupported without quantitative data.
- The claim that oligomannose glycans "remained accessible for biological recognition" is supported only by qualitative mention of two assays, with no quantitative or statistical context.
- The claim that steric control is "genetically encodable" is unsupported without evidence of reproducibility across expression conditions.
- The overall claim that the work "extends computational protein design to functional glycoproteins with programmed composition" is not assessable from the abstract alone.