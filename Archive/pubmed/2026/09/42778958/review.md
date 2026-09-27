## Review setup
- **Input scope** Full manuscript text, including abstract, background, results, discussion, methods, and figure legends. Supplementary files were not provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with the stated conclusions. Editorial and stylistic issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors present ARG-PASS, a computational method that uses pairwise sequence-structure comparisons of conserved protein regions to predict antibiotic resistance genes (ARGs) from human microbiome data. They report functional validation of nine predicted ARGs in E. coli, including a highly divergent phnP gene with low sequence identity to known β-lactamases, and propose a "pre-resistance" category for genes with sub-clinical activity.
- **Visible evidence base** Main text, Methods, Tables 1–2, Figures 1–5, and references to Supplementary files (not provided).
- **Missing materials affecting confidence** Supplementary files (Tables S1–S9, Alignments 1–16, Figures S1–S3) were not available for review. These are referenced extensively for validation data, hyperparameter details, and phylogenetic analyses. Their absence limits full verification of several claims.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that integrates protein structure prediction with machine learning to identify divergent ARGs. The core idea of using conserved structural regions rather than full-length homology is sound and addresses a real limitation in current ARG detection methods. However, the evidence provided is insufficient to fully establish the method's generalizability, and several claims regarding novelty, clinical relevance, and the "pre-resistance" concept require stronger support. The experimental validation is limited in scope, and the absence of a dedicated negative test set weakens the specificity assessment. The manuscript would benefit from clearer reporting of validation metrics and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Researchers in antimicrobial resistance surveillance, metagenomics, and computational biology would find this work relevant. The method's potential to identify highly divergent ARGs that evade homology-based detection is of practical interest for environmental and clinical monitoring. The "pre-resistance" concept may also interest evolutionary biologists studying the emergence of clinical resistance.
- **Major strengths**
  1. The methodological innovation of using pairwise sequence-structure distributions of conserved regions is a thoughtful departure from standard homology-based approaches.
  2. The inclusion of experimental validation for nine predicted ARGs, including a highly divergent phnP gene, demonstrates a commitment to functional confirmation.
  3. The use of CLSI breakpoints to distinguish resistance from pre-resistance is a clinically meaningful framework.
  4. The cross-class evaluation of β-lactamase models provides some evidence of specificity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "ARG-PASS provides a precise computational approach that integrates sequence and structure to identify divergent ARGs that evade homology-based detection."
  - **Evidence pointer** Methods, Validation sections; Supplementary Tables S5–S7 (not provided)
  - **Concern** The precision, sensitivity, and specificity of ARG-PASS are reported only against the PCM dataset (n=59) and the ResFinderFG v2.0 dataset (n=204). The PCM dataset is small, and the ResFinderFG analysis is described as a sensitivity evaluation without a corresponding specificity assessment. The absence of a dedicated negative test set, acknowledged by the authors, means the false positive rate of ARG-PASS in a realistic metagenomic context is unknown. The claim of "precision" is therefore not fully established from the provided evidence.
  - **Why it matters** A method intended for ARG discovery must demonstrate that it does not produce excessive false positives, especially when applied to large metagenomic datasets where the vast majority of proteins are not ARGs. Without a robust negative control, the practical utility of ARG-PASS remains uncertain.
  - **Resolution test** Provide a dedicated negative test set of proteins with similar folds but no resistance function (e.g., non-ARG metallo-β-lactamase superfamily members) and report precision, specificity, and false positive rates. Alternatively, apply ARG-PASS to a large, well-annotated metagenomic dataset and compare predictions against functional metagenomics results.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** "We suggest pre-resistance genes may preferentially evolve into clinically relevant resistance determinants."
  - **Evidence pointer** Discussion, Figure 4
  - **Concern** The "pre-resistance" concept is introduced based on two genes (bla02, bla03) with sub-clinical MICs. The claim that these genes "may preferentially evolve" into clinically relevant determinants is speculative and not supported by any evolutionary or experimental data in this manuscript. The conceptual framework is interesting, but the evidence base is too thin to support a generalizable claim.
  - **Why it matters** If the "pre-resistance" category is to be a meaningful contribution, it needs a clearer operational definition and evidence that such genes are indeed on a trajectory toward clinical resistance. Without this, the term risks being a label for "low activity" without predictive value.
  - **Resolution test** Provide additional examples of pre-resistance genes, ideally with mutational or selection experiments demonstrating increased resistance under antibiotic pressure. Alternatively, rephrase the claim to be more cautious and explicitly frame it as a hypothesis requiring further testing.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "In total, 80% of the tested genes confer resistance at CLSI resistant breakpoints and the remainder represent 'pre-resistance' genes."
  - **Evidence pointer** Table 1, Results section
  - **Concern** The functional validation relies on a single E. coli expression system (BW25113 ΔbamB ΔtolC). The authors acknowledge this limitation, but the generalizability of the results to other hosts, particularly Gram-positive bacteria or anaerobes, is not addressed. The use of a hypersusceptible strain may overestimate the clinical relevance of the observed MICs.
  - **Why it matters** The clinical relevance of an ARG depends on its expression in relevant pathogens. A gene that confers resistance in a hypersusceptible laboratory strain may not do so in a clinical isolate with different membrane permeability or efflux systems.
  - **Resolution test** Validate a subset of the predicted ARGs in a more clinically relevant host, such as a pathogenic E. coli strain or another species. Discuss the potential impact of the expression system on the observed MICs.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality
  - **Claim pointer** "ARG-PASS (ARG-PAirwise Sequence vs Structure) is a protein function prediction method which leverages a one-class support vector machine trained on pairwise primary and tertiary distributions of structurally conserved regions of proteins encoded by ARGs."
  - **Evidence pointer** Methods, Figure 2
  - **Concern** The novelty of ARG-PASS relative to existing structure-based methods (e.g., PCM) is not clearly articulated. The authors state that PCM uses pairwise comparative modeling, but the specific advantages of ARG-PASS over PCM or other machine learning approaches are not systematically compared. The claim of novelty is therefore not fully substantiated.
  - **Why it matters** For a methods paper, it is essential to demonstrate that the new approach offers a meaningful improvement over existing tools. Without a direct comparison, the contribution of ARG-PASS is unclear.
  - **Resolution test** Provide a head-to-head comparison of ARG-PASS against PCM and at least one sequence-based machine learning method (e.g., DeepARG, CARD's Resistance Gene Identifier) on the same datasets, reporting precision, recall, and computational cost.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Background
  - **Issue** The abstract uses terms like "pairwise primary and tertiary distributions" and "one-class support vector machine" without sufficient context for a general microbiology audience. The significance of the approach is not immediately clear.
  - **Required correction** Briefly explain in plain language what the method does and why it is an improvement over existing approaches. For example, "We compare the 3D shapes and sequences of protein regions that are known to be important for resistance, allowing us to find genes that look very different from known resistance genes but have similar functional parts."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Manual adjustment of Foldseek seqID calculations"
  - **Evidence pointer** Methods section
  - **Issue** The manual adjustment of seqID calculations is described but the rationale and the exact procedure are not fully detailed. This is a critical step that could affect reproducibility.
  - **Required correction** Provide a more detailed description of the adjustment procedure, including the formula or algorithm used, and ideally a worked example.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion, "pre-resistance" concept
  - **Evidence pointer** Discussion, Figure 4
  - **Issue** The "fitness-MIC landscape" figure is conceptual and not based on experimental data. While useful for illustration, it may be misinterpreted as empirical.
  - **Required correction** Clearly label Figure 4b as a conceptual model and avoid implying that the positions of specific genes on the landscape are experimentally determined.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Training set"
  - **Evidence pointer** Methods section
  - **Issue** The criteria for selecting ARG classes and the specific number of structures per class are not fully reported. The clustering thresholds (20%, 30%, 50%) are described, but the rationale for these specific values is not given.
  - **Required correction** Provide a table or supplementary figure showing the number of structures per class and the number of clusters at each threshold. Justify the choice of thresholds.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results, "Development of the ARG-PASS method"
  - **Evidence pointer** Results section, Figure 2
  - **Issue** The description of the three-step framework is clear, but the figure legend is dense and may be difficult for nonspecialists to follow.
  - **Required correction** Simplify the figure legend and consider adding a schematic that shows the workflow in a more intuitive way.
- **Technical failings that need to be addressed before the case is established**
  1. Lack of a dedicated negative test set for specificity assessment (R1-M1).
  2. Insufficient evidence for the "pre-resistance" evolutionary claim (R1-M2).
  3. Limited generalizability of functional validation due to single-host expression system (R1-M3).
  4. Incomplete description of the manual seqID adjustment procedure (R1-m2).
  5. Absence of a direct comparison with existing methods to establish novelty (R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** The concept of using conserved structural regions for ARG prediction is a creative extension of existing structure-based approaches. However, the novelty is not fully demonstrated without a direct comparison to PCM or other methods. The "pre-resistance" concept is interesting but underdeveloped.
  - **Scientific importance** The problem of identifying divergent ARGs is significant for antimicrobial resistance surveillance. The method has potential, but the evidence for its practical utility is incomplete. The clinical relevance of the findings is limited by the narrow experimental scope.
  - **Interdisciplinary readership** The work bridges computational biology, microbiology, and clinical diagnostics. However, the presentation is heavily technical and may not be accessible to a broad audience. The abstract and introduction need to be more accessible.
  - **Technical soundness** The core methodology is plausible, but the validation is insufficient. The absence of a negative control set and the small validation dataset undermine confidence in the reported precision. The manual adjustment of seqIDs is a potential source of bias that is not fully addressed.
  - **Readability for nonspecialists** The manuscript is well-structured but uses technical jargon without adequate explanation. The figures are informative but the legends are dense. The discussion of limitations is honest but could be more critical.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising approach, but the claims of precision, novelty, and the "pre-resistance" concept require additional validation and clearer reporting. I would be supportive if the authors address the major concerns, particularly the need for a negative test set, a direct comparison with existing methods, and a more cautious framing of the evolutionary claims.

## Risk / unsupported claims
- The claim that ARG-PASS "provides a precise computational approach" is not fully supported due to the lack of a dedicated negative test set and the small validation dataset.
- The suggestion that "pre-resistance genes may preferentially evolve into clinically relevant resistance determinants" is speculative and not supported by experimental evidence in this manuscript.
- The statement that "80% of the tested genes confer resistance at CLSI resistant breakpoints" is based on a small sample size and a single expression system, limiting its generalizability.
- The assertion that the method can identify "potentially a large reservoir of previously uncharacterised ARGs with clinical relevance" is an extrapolation from a limited number of validated examples and requires broader testing.