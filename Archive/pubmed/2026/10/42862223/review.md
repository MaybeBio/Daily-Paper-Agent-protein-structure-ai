## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or main text were available for evaluation
- **Shared manuscript claim summary** The chapter evaluates AlphaFold 3 (AF3) for RNA and protein:RNA complex structure prediction, arguing that RNA's conformational heterogeneity, condition dependence, and scarce training data limit AF3's performance and confidence metrics; that AF3 may operate via memorization and homology rather than de novo prediction in the RNA realm; that it nonetheless performs competitively with established RNA tools and serves as a hypothesis generator; and that practical guidelines and future data/representation improvements are needed
- **Visible evidence base** Abstract text only; no benchmarking data, case studies, figures, tables, or methodological details provided
- **Missing materials affecting confidence** Full chapter text, benchmarking datasets, specific case analyses, confidence metric comparisons, and any quantitative performance data; without these, the strength of the empirical claims cannot be assessed

## Reviewer
- **Overall assessment** The abstract presents a balanced and conceptually reasonable perspective on AF3's applicability to RNA and protein:RNA complexes, identifying plausible theoretical limitations and offering practical guidance. However, the claims are largely qualitative and lack the quantitative and methodological support that would be needed to establish them rigorously. The abstract reads as a useful overview for practitioners, but the evidence base for the central assertions, particularly regarding memorization versus de novo prediction and competitive performance, is not visible from the supplied material.
- **Who would be interested in the results, and why** Computational biologists, structural biologists, and experimentalists working on RNA structure or RNA:protein interactions would find this chapter useful as a practical reference. It would also interest developers of deep learning-based structure prediction tools who seek to understand AF3's limitations outside the protein domain, and educators or methodologists who need a critical assessment of AF3's applicability to non-protein targets.
- **Major strengths** The abstract clearly articulates the fundamental differences between RNA and protein structure that challenge AF3's framework, including conformational heterogeneity and condition dependence. It also appropriately emphasizes the importance of cautious interpretation of confidence metrics and the need for experimental validation, which is a responsible and practical stance. The suggestion that AF3 may rely on memorization and homology in the RNA realm is a thought-provoking hypothesis that merits further investigation.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative benchmarking results, specific case study outcomes, or methodological details that would allow the reader to verify the claims of competitive performance or the memorization hypothesis. The absence of these data means the central empirical assertions are currently unsupported.
- **Assessment against Nature-style criteria** Originality: The abstract offers a useful synthesis of known challenges and potential limitations, but the core ideas, such as data scarcity and conformational heterogeneity, are not novel in themselves. Scientific importance: The topic is timely and relevant given the rapid adoption of AF3, but the abstract does not present new findings that would substantially advance the field. Interdisciplinary readership: The content is accessible to a broad structural biology audience, though the lack of quantitative detail limits its impact for method developers. Technical soundness: The reasoning is plausible, but the absence of evidence prevents a full assessment of technical rigor. Readability for nonspecialists: The abstract is clearly written and understandable, though some terms such as "memorization" and "homology-based modeling" may require elaboration for a general audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The abstract presents a reasonable perspective, but the empirical claims need to be substantiated with data from the full chapter before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that benchmarking studies and individual case analyses suggest AF3 may function primarily through memorization of known structural motifs and homology-based modeling rather than genuine global de novo prediction, and that it performs competitively with established RNA prediction tools.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract references benchmarking studies and case analyses but provides no specific data, metrics, or examples. It is unclear which benchmarks were used, how performance was measured, or what criteria distinguish "memorization" from "de novo prediction." Without these details, the claim is an assertion rather than a demonstrated finding.
- **Why it matters** The central value of the chapter appears to rest on this distinction between memorization and genuine prediction, as it directly affects how practitioners should interpret AF3 outputs. If the evidence is anecdotal or based on limited cases, the conclusion may not generalize. The competitive performance claim also requires quantitative comparison against specific tools and datasets to be meaningful.
- **Resolution test** Provide specific benchmarking datasets, performance metrics (e.g., TM-score, RMSD, or interaction accuracy), and a clear operational definition of memorization versus de novo prediction. Include at least one quantitative comparison with established RNA prediction tools and describe the case selection criteria.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract states that RNA-related training data in the Protein Data Bank are scarce and lack the diversity of protein data, limiting both structural prediction itself and the reliability of AF3's self-assessment confidence metrics.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The claim about data scarcity and its impact on confidence metrics is plausible but is presented without any quantitative support. No statistics on RNA structure counts, diversity measures, or comparisons with protein data are given. The link between data scarcity and confidence metric reliability is asserted rather than demonstrated.
- **Why it matters** This claim underpins the practical guidance to interpret confidence metrics cautiously. If the relationship is not established, readers may either overtrust or unduly dismiss AF3's confidence scores for RNA targets. A quantitative demonstration would strengthen the argument and help users calibrate their expectations.
- **Resolution test** Provide data on the number and diversity of RNA-containing structures in the PDB relative to proteins, and show a correlation or case-based evidence linking data scarcity to confidence metric miscalibration for RNA targets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scope and generalizability
- **Claim pointer** The abstract claims that AF3 "performs competitively with established RNA prediction tools and can serve as an attractive hypothesis generator."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The scope of this claim is unclear. It is not specified which RNA prediction tools are compared, what types of RNA targets are included (e.g., single-stranded, structured, protein-bound), or under what conditions AF3 is competitive. The term "hypothesis generator" is also vague and could encompass a wide range of prediction accuracies.
- **Why it matters** Without a defined scope, the claim could be misinterpreted as a general endorsement of AF3 for all RNA targets, which may not be warranted given the acknowledged limitations. Clarifying the conditions under which AF3 is competitive would make the guidance more actionable.
- **Resolution test** Specify the comparison tools, target categories, and performance thresholds. Provide examples of cases where AF3-generated hypotheses led to experimentally validated findings, and state the success rate or criteria for a "useful" hypothesis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "memorization" is used without a precise definition. It could be interpreted as overfitting to training data, template-based modeling, or something else.
- **Required correction** Define "memorization" in the context of AF3, and distinguish it from homology modeling and genuine de novo prediction with concrete examples or criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Practical guidelines
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions practical guidelines but does not summarize any of them. The reader cannot assess their usefulness or novelty.
- **Required correction** Briefly list the key guidelines in the abstract, or indicate that they are detailed in the chapter with a summary of the most critical recommendations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Future directions
- **Affected element** Proposed improvements
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that future improvements will require expanded data, better evolutionary information, and alternative representations, but does not explain why these are expected to help or how they would address the identified limitations.
- **Required correction** Add a sentence explaining the rationale for each proposed improvement, linking them to the specific limitations identified earlier.

## Risk / unsupported claims
- The claim that AF3 functions primarily through memorization and homology rather than de novo prediction is unsupported in the abstract, as no evidence or methodology is provided.
- The claim that AF3 performs competitively with established RNA prediction tools is unsupported without specific benchmarks or comparisons.
- The claim that data scarcity limits confidence metric reliability is plausible but not demonstrated with quantitative data.
- The practical guidelines are mentioned but not described, making their effectiveness unassessable.
- The future improvements are listed without justification, so their potential impact cannot be evaluated.