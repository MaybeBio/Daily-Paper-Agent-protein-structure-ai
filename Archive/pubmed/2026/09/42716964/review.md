## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors report the synthesis of generative protein design workflows to screen 1,758 de novo designed protein binders against BCMA, CD19, and CD22 for use as chimaeric antigen receptors (CARs) in T cells. They identify three key challenges (tonic signalling, occluded epitope engagement, off-target activity) and develop computational and experimental heuristics to overcome these limitations, enabling on-target CAR activation while mitigating liabilities.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided.
- **Missing materials affecting confidence** Full manuscript, including Methods, Results, Figures, Tables, Supplementary Information, and any data or code availability statements.

## Reviewer
- **Overall assessment** The abstract presents a potentially impactful framework for integrating AI-designed protein binders into CAR T-cell therapy development. The scale of screening (1,758 binders) and the identification of specific failure modes are noteworthy. However, the abstract lacks sufficient detail to evaluate the robustness of the heuristics, the quantitative performance of the best candidates, and the generalizability of the approach. The claims are intriguing but not yet established from the provided material.
- **Who would be interested in the results, and why** Researchers in synthetic immunology, protein engineering, and AI-driven drug discovery would be interested. The work addresses a critical translational gap for AI-designed proteins, moving beyond biochemical characterization into functional cellular assays. The identified failure modes and heuristics could guide future design efforts.
- **Major strengths**
    - Large-scale screening of 1,758 de novo binders across three clinically relevant targets (BCMA, CD19, CD22) is a substantial experimental effort.
    - Explicit identification and characterization of three specific failure modes (tonic signalling, occluded epitope, off-target activity) provides actionable insights for the field.
    - The development of both computational and experimental heuristics to address these liabilities suggests a practical, integrated workflow.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "We develop computational and experimental heuristics to overcome these limitations... that retain on-target CAR activation while mitigating liabilities."
    - **Evidence pointer** Abstract only; location not provided.
    - **Concern** The abstract does not describe the nature, performance, or validation of these heuristics. It is unclear whether they are general rules, machine learning models, or specific sequence modifications. No quantitative data (e.g., fold improvement in activation, reduction in tonic signalling) is provided.
    - **Why it matters** Without evidence that the heuristics are effective and generalizable, the central claim of the framework is unsubstantiated. The reader cannot assess whether the approach is a meaningful advance or a minor tweak.
    - **Resolution test** The full manuscript must provide clear, quantitative data (e.g., bar charts, dose-response curves) comparing the performance of naive vs. heuristic-optimized CARs across all three targets and failure modes. Statistical significance and effect sizes must be reported.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Claim support
    - **Claim pointer** "We characterize three main challenges that hinder the utility of de novo protein binders as CARs, including tonic signalling, occluded epitope engagement and off-target activity."
    - **Evidence pointer** Abstract only; location not provided.
    - **Concern** The abstract states these challenges are "characterized" but provides no data on their frequency, severity, or mechanistic basis. For example, what fraction of the 1,758 binders exhibited tonic signalling? How was "occluded epitope" defined and measured? What was the nature of off-target activity?
    - **Why it matters** The claim of "characterization" implies a systematic analysis. Without any quantitative or qualitative description, the reader cannot evaluate the validity or depth of this analysis.
    - **Resolution test** The full manuscript must present a systematic analysis of the 1,758 binders, e.g., a breakdown of how many failed due to each challenge, with representative examples and supporting data (e.g., flow cytometry, killing assays, binding specificity panels).

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability
    - **Claim pointer** "Together, our framework accelerates the development of AI-designed proteins for future preclinical therapeutic screening, helping enable a new generation of cellular therapies."
    - **Evidence pointer** Abstract only; location not provided.
    - **Concern** The abstract only tests three targets (BCMA, CD19, CD22) and does not mention validation on any other target or in a different cellular context (e.g., NK cells). The claim of a general "framework" is premature.
    - **Why it matters** The impact of the work depends on its generalizability beyond the specific targets and binders tested. The abstract provides no evidence for this.
    - **Resolution test** The full manuscript should include at least one demonstration on a different target or a discussion of the principles that make the heuristics target-agnostic. Alternatively, the claim should be toned down to reflect the specific targets tested.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Claim of "synthesize generative protein design workflows"
    - **Evidence pointer** Abstract
    - **Issue** The phrase "synthesize generative protein design workflows" is vague. It is unclear whether the authors are combining existing workflows, creating a new one, or simply applying a standard pipeline.
    - **Required correction** Clarify what is novel about the workflow integration. For example, specify which generative models were used (e.g., RFdiffusion, ProteinMPNN, ESM-IF) and how they were combined.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Description of screening
    - **Evidence pointer** Abstract
    - **Issue** The abstract mentions "scalable protein-binding, T-cell activation and in vivo killing assays" but does not specify the model system (e.g., cell lines, mouse models) or the number of binders that progressed through each stage.
    - **Required correction** Provide a brief summary of the screening funnel (e.g., "Of 1,758 binders, X showed binding, Y showed activation, and Z showed in vivo efficacy").

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2. The core claims of characterizing challenges and developing effective heuristics are not supported by the abstract alone.
- **Assessment against Nature-style criteria**
    - **Originality:** Potentially high. The application of AI-designed binders to CARs and the systematic identification of failure modes is novel. However, the abstract does not clearly distinguish this from prior work on antibody-based CARs or other protein scaffolds.
    - **Scientific importance:** High, if the heuristics are effective and generalizable. The work could address a key bottleneck in translating AI-designed proteins to therapeutics.
    - **Interdisciplinary readership:** High. The topic bridges AI, protein engineering, and cellular immunotherapy, appealing to a broad audience.
    - **Technical soundness:** Cannot be assessed from the abstract. The lack of quantitative data and methodological detail prevents evaluation.
    - **Readability for nonspecialists:** The abstract is clear and well-structured, but terms like "tonic signalling" and "occluded epitope" may require brief explanation for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks the quantitative and methodological detail required to support its central claims. A full manuscript with rigorous data is needed for a proper evaluation.

## Risk / unsupported claims
- The claim that the framework "accelerates the development of AI-designed proteins for future preclinical therapeutic screening" is unsupported without evidence of generalizability or a quantitative comparison to existing methods.
- The claim that the three challenges are "characterized" is unsupported without data on their frequency, severity, or mechanism.
- The claim that the heuristics "retain on-target CAR activation while mitigating liabilities" is unsupported without quantitative performance data.