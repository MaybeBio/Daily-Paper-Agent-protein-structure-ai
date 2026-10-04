## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract, with no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present EnsPlex, a multi-source framework for protein complex structure prediction that combines conformation-expanded docking, AlphaFold-Multimer, AlphaFold3, and Boltz-1 for candidate generation, and a trained quality-assessment model (FACET) for candidate selection. They report up to a 27.8% relative improvement in target success rate over AlphaFold3 with built-in ranking across 102 antigen-antibody systems, and improved within-source ranking on internal and homology-filtered external data.
- **Visible evidence base** Abstract text only. No figures, tables, methods descriptions, or numerical results beyond the single reported improvement percentage are provided.
- **Missing materials affecting confidence** Full manuscript, methods section, all quantitative results, benchmark definitions, statistical analyses, and supplementary materials are unavailable. The abstract does not provide baseline absolute success rates, per-system breakdowns, or details of the FACET training and evaluation protocol.

## Reviewer

- **Overall assessment** The abstract describes a plausible and potentially valuable integrative approach to protein complex prediction, addressing a real gap in the field by coupling multi-source sampling with learned candidate selection. However, the evidence presented in the abstract is insufficient to evaluate the technical soundness of the method or the robustness of the reported improvement. The single headline metric, a 27.8% relative improvement over AlphaFold3, is not contextualized with absolute numbers, statistical significance, or comparison against other selection methods. The claim that FACET improves ranking in external data is stated without supporting detail. The abstract is well written and the conceptual framing is clear, but the scientific case is not established from the supplied material.
- **Who would be interested in the results, and why** Structural biologists, computational biologists, and researchers working on protein-protein interaction prediction, particularly those focused on antigen-antibody complexes. The work is also relevant to developers of deep learning-based structure prediction methods and to researchers interested in model quality assessment and ensemble methods. The potential to improve success rates beyond single-model approaches would be of broad interest to the structural bioinformatics community.
- **Major strengths** The conceptual framing is clear and addresses a genuine limitation in the field, namely the separation of candidate generation from candidate selection. The multi-source sampling strategy is sensible and leverages existing state-of-the-art tools. The use of DockQ and its component metrics as supervision for the quality-assessment model is a reasonable and potentially effective design choice. The evaluation across 102 antigen-antibody systems is a substantial benchmark size.
- **Major Concerns** The concerns below are based solely on the abstract. The absence of methodological detail and quantitative context prevents a full assessment.
- **Minor Comments** The abstract is concise and readable, but several statements would benefit from additional context or qualification.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The integrative approach is not entirely novel in concept, as ensemble methods and reranking are established ideas, but the specific combination of diverse generators with a learned selector is a reasonable contribution. Scientific importance: Potentially high if the reported improvements are robust and generalizable, but this cannot be assessed from the abstract. Interdisciplinary readership: The work is primarily of interest to structural biology and computational biology audiences; broader appeal would depend on demonstrated generalizability beyond antigen-antibody systems. Technical soundness: Not assessable from the abstract. Readability for nonspecialists: The abstract is accessible and well structured, though some terms such as "conformation-expanded docking" and "homology-filtered external data" are not defined.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising framework, but the lack of methodological detail and quantitative context means the core claims cannot be evaluated. A full manuscript with detailed methods, comprehensive results, and statistical analyses would be required to assess the validity and significance of the reported improvements.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "EnsPlex achieved up to a 27.8% relative improvement in target success rate over AlphaFold3 with its built-in ranking under matched output budgets."
- **Evidence pointer** Abstract, location not provided
- **Concern** The headline result is reported as a single relative improvement percentage without absolute success rates, baseline values, or the number of systems for which improvement was observed. The phrase "up to" suggests variability across systems, but no distribution, confidence interval, or statistical test is reported.
- **Why it matters** Without absolute numbers and statistical context, the reader cannot judge whether the improvement is meaningful, consistent, or within the range of expected variability. A 27.8% relative improvement could correspond to a small absolute gain if the baseline is low, and the practical significance would be unclear.
- **Resolution test** Provide absolute target success rates for EnsPlex and AlphaFold3, the per-system distribution of improvements, and appropriate statistical analyses such as paired tests or confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "FACET is trained to predict candidate quality using DockQ and its component metrics as supervision."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the architecture, training data, feature set, or evaluation protocol for FACET. It is unclear whether FACET is a supervised regression model, a ranking model, or a classifier, and how its predictions are integrated into the final candidate selection.
- **Why it matters** The quality-assessment model is a central component of the proposed framework. Without understanding its design and training, the reader cannot assess whether the reported improvements are attributable to the model or to other aspects of the pipeline, nor whether the approach is reproducible.
- **Resolution test** Provide a detailed description of FACET architecture, training data and labels, feature representation, and the selection algorithm that uses its predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "These findings support the utility of EnsPlex for structure prediction in the evaluated antigen-antibody systems."
- **Evidence pointer** Abstract, location not provided
- **Concern** The evaluation is limited to 102 antigen-antibody systems. The abstract does not report results on other types of protein complexes, such as enzyme-inhibitor, signaling, or obligate complexes, nor does it discuss whether the method is expected to generalize beyond antibody-antigen interactions.
- **Why it matters** The stated scope of the conclusion is appropriately limited to the evaluated systems, but the broader utility of the method for general protein complex prediction remains unknown. The title and framing suggest a general-purpose tool, which the evidence does not yet support.
- **Resolution test** Report results on additional benchmark sets covering diverse complex types, or explicitly discuss the expected scope and limitations of the method.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** "FACET also improved within-source ranking in the internal candidate pools and in homology-filtered external data."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not specify which baselines FACET is compared against for within-source ranking, nor what "homology-filtered external data" refers to. It is unclear whether the comparison is against other quality-assessment methods, random selection, or the native ranking of each generator.
- **Why it matters** Without defined baselines and dataset descriptions, the claim of improved ranking cannot be interpreted. The reader cannot determine whether the improvement is meaningful relative to existing approaches or whether the external data are representative of realistic use cases.
- **Resolution test** Specify the baselines used for comparison, describe the external dataset and its filtering criteria, and report quantitative ranking metrics with statistical significance.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "conformation-expanded docking" is used without definition. It is described as comprising "monomer conformational expansion followed by flexible HADDOCK docking," but the nature of the expansion and the flexibility treatment are not specified.
- **Required correction** Provide a brief definition or reference for the conformation-expansion procedure and the flexible docking protocol.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Benchmark description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that 102 antigen-antibody systems were used, but does not describe the source of these systems, the diversity of the antigen and antibody structures, or the criteria for inclusion.
- **Required correction** Include a brief description of the benchmark composition and selection criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Footnotes, location not provided
- **Issue** The abstract lists a GitHub repository and two Zenodo DOIs, but does not state what is contained in each resource or whether the code and data are sufficient to reproduce the reported results.
- **Required correction** Clarify the contents of the repository and the Zenodo deposits, and state the license and access conditions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Result framing
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "up to a 27.8% relative improvement" is ambiguous regarding whether this is the best single system, the mean, or the median improvement. The abstract does not clarify the summary statistic used.
- **Required correction** Specify the summary statistic and report the range or distribution of improvements across systems.

## Risk / unsupported claims

- The claim of a 27.8% relative improvement over AlphaFold3 is unsupported without absolute baseline values, per-system results, and statistical analyses.
- The claim that FACET improves within-source ranking is unsupported without defined baselines, dataset descriptions, and quantitative metrics.
- The general utility of EnsPlex for protein complex prediction beyond antigen-antibody systems is not supported by the evidence presented.
- The methodological details of FACET, including architecture, training data, and selection algorithm, are not described and therefore cannot be evaluated.
- The composition and filtering criteria of the "homology-filtered external data" are not described and the associated results cannot be interpreted.