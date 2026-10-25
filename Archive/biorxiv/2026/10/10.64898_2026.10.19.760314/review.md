## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided for evaluation
- **Shared manuscript claim summary** The authors introduce LangAAI, a masked language model that conditions on antibody and antigen primary sequences only, without requiring 3D structures, docking poses, or epitope annotations. They claim that LangAAI exhibits genuine antigen conditioning, as demonstrated by reduced sequence recovery when the cognate antigen is replaced with a non-binding decoy, with the effect concentrated in CDR3. They further claim improved amino-acid recovery relative to existing antibody language models, parity with structure-based methods under their respective protocols, and comparable ranking of experimentally measured variants by affinity relative to inverse-folding models using backbone coordinates.
- **Visible evidence base** Abstract text only. No figures, tables, methods descriptions, benchmark definitions, dataset specifications, or statistical details were provided.
- **Missing materials affecting confidence** Full manuscript, methods section, benchmark protocols, dataset descriptions, baseline model specifications, decoy antigen construction details, statistical significance measures, and all quantitative results. The absence of these materials severely limits the ability to verify the central claims.

## Reviewer

- **Overall assessment** The abstract presents a potentially valuable contribution to antibody modeling, addressing a real gap in the field by proposing a sequence-only approach to antigen-conditioned CDR design. The concept of using decoy antigens to probe genuine antigen conditioning is methodologically interesting. However, the abstract alone provides insufficient evidence to evaluate the validity, robustness, or generalizability of the claims. The central claims of improved recovery, parity with structure-based methods, and affinity ranking comparability are stated without quantitative support. The manuscript cannot be assessed for technical soundness from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational antibody design, protein language models, and therapeutic antibody development would be interested. The work addresses a practical bottleneck in antibody engineering, namely the dependence on experimentally determined antigen structures. A sequence-only approach that demonstrably conditions on antigen information could enable broader application of computational design to targets lacking structural data. The decoy-based evaluation strategy may also be of methodological interest to the protein language model community.
- **Major strengths** The problem addressed is well-motivated and practically relevant. The proposed approach, if validated, would remove a significant barrier in antibody design. The decoy antigen substitution strategy is a thoughtful and potentially rigorous way to test whether the model genuinely uses antigen information rather than ignoring it. The claim of concentrating antigen sensitivity in CDR3 is biologically plausible and, if confirmed, would support the model's relevance to antigen specificity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** LangAAI shows a marked reduction in sequence recovery when the cognate antigen is replaced with a non-binding decoy, concentrated in CDR3
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract states that decoy antigen substitution causes a marked reduction in sequence recovery concentrated in CDR3, but provides no quantitative data, no statistical significance, no description of how decoys were constructed, and no comparison of effect sizes across CDR loops or across models.
  - **Why it matters** This is the central evidence for the claim of genuine antigen conditioning. Without quantitative details and a clear description of the decoy construction and evaluation protocol, the reader cannot assess whether the effect is robust, specific, or an artifact of the specific decoy set or evaluation metric.
  - **Resolution test** Provide the full decoy substitution results, including recovery values for all CDR loops, statistical significance tests, and a description of decoy construction. Show that the effect is consistent across multiple decoy antigens and is not explained by trivial sequence properties of the decoys.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** LangAAI improves amino-acid recovery relative to existing antibody language models, matches the performance of structure-based methods when evaluated under their respective protocols, and ranks experimentally measured variants by affinity comparably to inverse-folding models
  - **Evidence pointer** Abstract, location not provided
  - **Concern** Three comparative performance claims are made without any numerical results, benchmark definitions, baseline specifications, or statistical analyses. The phrase "matches the performance" and "comparably" are undefined without error bars or significance testing.
  - **Why it matters** These claims constitute the primary evidence for the utility of LangAAI. Without quantitative benchmarks, the reader cannot determine whether the improvements are meaningful, whether parity claims are justified, or whether the comparisons were conducted fairly with matched training data and evaluation protocols.
  - **Resolution test** Provide full benchmark tables with all baseline models, metrics, standard deviations, and statistical tests. Specify the exact evaluation protocols used for each comparison and confirm that baselines were evaluated under identical conditions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** LangAAI is a masked language model that conditions exclusively on antibody and antigen primary sequences
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No description of the model architecture, training data, training procedure, or implementation details is provided. The abstract does not state how antigen sequences are incorporated into the model, how the model is trained, or what data were used.
  - **Why it matters** Reproducibility is a core requirement for computational biology claims. Without architecture and training details, the work cannot be replicated or extended by other groups, and the reader cannot assess whether the approach is genuinely novel relative to existing antibody language models.
  - **Resolution test** Provide a complete methods section describing the model architecture, training data, preprocessing, hyperparameters, and code availability.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The phrase "exposure to antigen sequences alone does not necessarily entail learning the underlying interaction determinants" is vague and could be interpreted in multiple ways. It is unclear whether this refers to a limitation of existing models, a design principle, or a hypothesis.
  - **Required correction** Clarify the intended meaning and specify whether this statement is supported by prior literature or is a motivating hypothesis.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Benchmark description
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract mentions "benchmarks" and "their respective protocols" without naming the benchmarks or protocols. This makes it impossible to contextualize the claims.
  - **Required correction** Name the specific benchmarks and protocols used in the full manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Use of "inverse-folding models"
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "inverse-folding models" is used without definition. It is likely clear to specialists but may be ambiguous to a broader readership.
  - **Required correction** Provide a brief definition or example of inverse-folding models in the full manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results, benchmark details, and model description means that none of the central claims can be verified from the supplied material.
- **Assessment against Nature-style criteria** Originality: The concept of sequence-only antigen conditioning with decoy-based validation is potentially original, but the abstract does not provide enough context to establish novelty relative to prior work. Scientific importance: The problem is important and the potential impact is high if the claims hold, but the evidence is insufficient to assess whether the contribution is substantial. Interdisciplinary readership: The work would appeal to computational biologists, immunologists, and protein engineers, but the abstract is written at a level that assumes significant familiarity with antibody modeling. Technical soundness: Cannot be assessed from the abstract alone. Readability for nonspecialists: The abstract is concise but uses field-specific terminology without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising direction and a potentially rigorous evaluation strategy, but the absence of quantitative results, methodological details, and benchmark specifications prevents any assessment of validity. The manuscript should be evaluated after the full text, figures, and supplementary materials are provided.

## Risk / unsupported claims

- The claim of "marked reduction in sequence recovery" upon decoy substitution is unsupported without quantitative data.
- The claim of "improved amino-acid recovery relative to existing antibody language models" is unsupported without benchmark results.
- The claim of "matches the performance of structure-based methods" is unsupported without comparative data.
- The claim of ranking "experimentally measured variants by affinity comparably to inverse-folding models" is unsupported without correlation or ranking metrics.
- The claim that LangAAI "does not require 3D structures, docking poses, or epitope annotations" is plausible but cannot be verified without model description.
- The overall claim of "antigen-aware antibody optimization" is not established from the abstract alone.