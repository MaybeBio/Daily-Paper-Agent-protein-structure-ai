## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a computational pipeline integrating eight pathogenicity predictors, five stability tools, three structural impact tools, molecular docking, 100-ns molecular dynamics simulations, MM-GBSA binding free energy calculations, and three cancer susceptibility predictors to identify high-risk KRAS nsSNPs. Sixteen nsSNPs were consistently predicted deleterious; two variants, Y71D and M72K, were highlighted as high-risk, destabilizing KRAS, altering ligand binding in a mutation-dependent manner (reduced sotorasib affinity, enhanced adagrasib affinity), and potentially promoting cancer prognosis.
- **Visible evidence base** Abstract text only; no quantitative results, figures, tables, or methodological details provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, detailed methods, docking scores, simulation trajectories, MM-GBSA values, statistical analyses, and variant frequency data

## Reviewer
- **Overall assessment** The abstract describes a potentially useful computational framework for prioritizing KRAS nsSNPs and linking them to mutation-specific drug responses. The central claims, however, rest on a complex multi-step pipeline for which no quantitative evidence is visible in the abstract. The mutation-dependent differential binding between sotorasib and adagrasib is an interesting and clinically relevant observation, but the absence of numerical data, simulation quality metrics, and statistical validation prevents assessment of whether the conclusions are robust. The cancer prognosis claims are particularly under-supported given the abstract provides no effect sizes or confidence measures.
- **Who would be interested in the results, and why** Researchers in precision oncology, computational genomics, and structural biology would be interested. The work addresses a clinically important question, namely whether KRAS variants differentially affect response to approved targeted inhibitors, which is directly relevant to treatment stratification. The methodological framework may also interest bioinformaticians developing variant prioritization pipelines.
- **Major strengths** The study addresses a clinically relevant question with direct therapeutic implications. The multi-tool consensus approach for variant prioritization is methodologically sound in principle. The focus on mutation-dependent ligand interactions with two FDA-approved KRAS inhibitors is a distinctive and potentially valuable contribution. The integration of multiple computational layers, from pathogenicity to dynamics to cancer susceptibility, is comprehensive.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: moderate. The combination of KRAS nsSNP prioritization with differential inhibitor binding is somewhat novel, but the individual computational methods are well established. Scientific importance: potentially high given the clinical relevance of KRAS mutations and approved inhibitors, but the importance is contingent on the robustness of the findings, which cannot be assessed from the abstract. Interdisciplinary readership: the topic bridges genomics, structural biology, and oncology, which could attract a broad audience. Technical soundness: cannot be evaluated from the abstract; the absence of quantitative results and validation metrics is a significant limitation. Readability for nonspecialists: the abstract is generally clear, though the dense listing of tools and methods may be challenging for readers outside computational biology.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible pipeline and interesting hypotheses, but the absence of quantitative data, validation metrics, and methodological detail means the core claims cannot be evaluated. A supportive posture would require the full manuscript to demonstrate robust, statistically sound results.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Our analysis consistently predicted sixteen nsSNPs as highly deleterious, with Y71D and M72K identified as high-risk variants"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract states that sixteen nsSNPs were consistently predicted as deleterious by eight tools, but no data are presented showing the concordance across tools, the criteria for "consistently predicted," or the thresholds used. Similarly, the designation of Y71D and M72K as "high-risk" is asserted without quantitative support, such as pathogenicity scores, stability change values, or confidence intervals.
- **Why it matters** The entire study hinges on the reliability of the variant prioritization step. Without visible evidence of tool concordance and the criteria for high-risk designation, the selection of Y71D and M72K as the focus of subsequent analyses appears arbitrary and cannot be independently verified.
- **Resolution test** Provide a table or figure showing the predictions of all eight tools for all 324 nsSNPs, the consensus criteria, and the scores for Y71D and M72K relative to the other variants. Include numerical stability change values from the five stability tools.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** "Docking and simulation analyses showed that the Y71D and M72K nsSNPs reduced binding affinity and stability with ligand sotorasib compared to wild-type KRAS, whereas both high-risk nsSNPs exhibited enhanced binding and stability with ligand adagrasib"
- **Evidence pointer** Abstract; location not provided
- **Concern** The central and most clinically relevant claim is the differential binding of the two variants to sotorasib versus adagrasib. However, no docking scores, binding free energies, RMSD values, or other simulation metrics are provided. The claim of "reduced" and "enhanced" binding is made without any numerical context, and it is unclear whether the differences are statistically significant or within the error of the computational methods.
- **Why it matters** This is the key finding that would justify the study's clinical relevance. Without quantitative data, the reader cannot assess whether the observed differences are meaningful or merely computational noise. The claim of mutation-dependent ligand interactions is the study's main potential contribution, and it must be supported by robust numerical evidence.
- **Resolution test** Provide docking scores (e.g., binding affinities in kcal/mol) for wild-type and both variants with both ligands, RMSD and RMSF plots from the 100-ns simulations, and MM-GBSA binding free energies with standard errors. Include a statistical comparison, such as bootstrap confidence intervals or replicate simulations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "MM-GBSA analysis confirmed mutation-dependent KRAS binding changes, weakening sotorasib affinity while enhancing adagrasib interaction in the Y71D variant"
- **Evidence pointer** Abstract; location not provided
- **Concern** The MM-GBSA result is presented as "confirming" the docking and simulation findings, but no MM-GBSA values are reported. It is also unclear whether MM-GBSA was performed for M72K or only Y71D, as the abstract specifically mentions only the Y71D variant in this context. The term "confirmed" implies a level of validation that is not demonstrated.
- **Why it matters** MM-GBSA is an approximate method with known limitations, and its results should be interpreted with caution. The abstract presents it as a confirmatory step, which overstates its evidentiary weight. The inconsistency in reporting (Y71D only) raises questions about whether M72K was analyzed and whether the results were omitted because they were not supportive.
- **Resolution test** Report MM-GBSA binding free energies for all three variants (wild-type, Y71D, M72K) with both ligands, including standard deviations. Clarify whether M72K was included in the MM-GBSA analysis and, if not, explain why.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Cancer susceptibilities analyses indicated both Y71D and M72K may promote cancer prognosis"
- **Evidence pointer** Abstract; location not provided
- **Concern** The claim that Y71D and M72K "may promote cancer prognosis" is extremely vague and not supported by any quantitative data. The abstract does not report the scores from CScape, Dr. Cancer, or FATHMM, nor does it explain what "promote cancer prognosis" means in this context. It is unclear whether this refers to increased cancer risk, worse survival, or enhanced tumorigenic potential.
- **Why it matters** This claim extends the study's relevance to clinical outcomes, but it is the least supported assertion in the abstract. Without specific scores, thresholds, or an explanation of the biological interpretation, this claim is not evaluable and could be misleading if interpreted as a clinical finding.
- **Resolution test** Provide the raw scores from CScape, Dr. Cancer, and FATHMM for Y71D and M72K, the thresholds used for classification, and a clear statement of what the scores indicate biologically. If the tools provide categorical predictions, report those categories explicitly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Variant nomenclature
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract refers to "Y71D" and "M72K" without specifying the reference sequence or transcript. KRAS has multiple isoforms, and the numbering may differ depending on the reference used.
- **Required correction** Specify the reference sequence (e.g., NP_004976.2) and transcript ID, and confirm that the numbering corresponds to the canonical isoform.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Ligand selection rationale
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that sotorasib and adagrasib were used in docking and simulation studies but does not explain why these two inhibitors were selected over other KRAS inhibitors or why the analysis was limited to these two.
- **Required correction** Add a sentence in the abstract or methods explaining the rationale for selecting sotorasib and adagrasib, such as their clinical approval status and relevance to KRAS G12C mutations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "may promote cancer prognosis" is imprecise. Prognosis typically refers to the likely course of a disease, and "promoting" prognosis is not standard terminology.
- **Required correction** Rephrase to clarify the intended meaning, such as "may be associated with worse clinical outcomes" or "may increase cancer risk," depending on what the tools actually predict.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Transparency
- **Affected element** Tool version reporting
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract lists many computational tools but does not mention versions or default versus customized parameters. Tool versions and parameter choices can significantly affect results.
- **Required correction** In the full manuscript, report tool versions, database versions, and all non-default parameters. In the abstract, consider adding a statement that full parameters are provided in the methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scope
- **Affected element** Experimental validation
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract concludes by "supporting further experimental validation," which is appropriate, but it does not acknowledge the limitations of computational predictions in the absence of experimental data.
- **Required correction** Add a brief statement in the discussion or conclusion acknowledging that all findings are computational predictions that require experimental confirmation before clinical translation.

## Risk / unsupported claims
- The claim that Y71D and M72K "may promote cancer prognosis" is unsupported by any quantitative data in the abstract and is not evaluable without the underlying tool scores.
- The claim of "consistently predicted" for sixteen nsSNPs is not verifiable without concordance data across the eight tools.
- The differential binding affinities for sotorasib and adagrasib are asserted without numerical values, making the claim unverifiable from the abstract.
- The MM-GBSA result is described as "confirming" prior findings, but no MM-GBSA values are reported, and the term "confirmed" overstates the evidentiary weight of an approximate computational method.
- The clinical relevance implied by "cancer prognosis" is not supported by any survival data, clinical cohorts, or functional experiments.