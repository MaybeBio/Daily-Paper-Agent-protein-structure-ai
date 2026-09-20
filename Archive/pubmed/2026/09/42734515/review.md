## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific content, methodological soundness, claim-evidence alignment, and reporting quality as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark AI-based structure prediction methods for nanobody-antigen complexes and propose an integrative docking pipeline using HADDOCK3 that achieves higher success rates than AlphaFold2-Multimer when some epitope information is available, with a framework-aware paratope definition improving performance.
- **Visible evidence base** Textual descriptions of results, numerical values for success rates and RMSDs, methodological descriptions, references to figures and tables (not visible)
- **Missing materials affecting confidence** All figures, tables (including Tables S1-S3), supplementary material, benchmark data set details, and the GitHub repository contents

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely problem in structural biology, namely the prediction of nanobody-antigen complexes. The authors present a systematic benchmark of current AI-based methods and demonstrate that integrative modeling with HADDOCK3 can outperform AlphaFold2-Multimer when epitope information is available. The work is technically sound in its overall design, but several concerns regarding data set construction, statistical rigor, and the strength of certain claims need to be addressed. The manuscript is well-written and accessible, though some methodological details require clarification. The proposed framework-aware paratope definition is a useful contribution, but its generalizability and the statistical significance of the improvements need stronger support.

- **Who would be interested in the results, and why** Researchers in structural biology, computational biology, and protein engineering, particularly those working on antibody and nanobody design, integrative modeling, and benchmarking of AI-based structure prediction methods. The work is also relevant for developers of docking software and machine learning methods for protein-protein complex prediction.

- **Major strengths** The manuscript addresses a clear and important gap in the field, namely the limited evaluation of AI-based methods for nanobody-antigen complexes specifically. The benchmark data set is carefully constructed with attention to non-redundancy and temporal separation from training data. The systematic evaluation of multiple prediction methods and docking scenarios is thorough. The proposed framework-aware paratope definition is a novel and practical contribution. The authors are transparent about limitations, including the small data set size and the challenges of model scoring.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and claim support
- **Claim pointer** The authors claim that their pipeline achieves higher success rates than the AlphaFold2-Multimer baseline in the low-information scenarios (LI and 2I), and that the framework-aware paratope definition improves docking performance.
- **Evidence pointer** Results sections "Information-Driven HADDOCK Unbound Docking" and "Framework-Aware Paratope Description Improves the Modeling Success"; Figures 3, 4, S9 (not visible)
- **Concern** The manuscript reports success rates and improvements without providing any statistical significance testing or confidence intervals. With a data set of only 40 complexes, the observed differences between scenarios and between paratope definitions could be within sampling variability. For example, the improvement in LI Top 10 SR from 30% to 42.5% (unbound) or from 50% to 62.5% (bound) represents only a handful of additional successful cases. The authors should provide statistical analysis, such as bootstrap confidence intervals or paired tests, to support the claim that the observed improvements are meaningful.
- **Why it matters** The central claim of the manuscript is that the proposed pipeline outperforms existing methods. Without statistical support, the reader cannot assess whether the observed differences are robust or could be due to chance, particularly given the modest data set size.
- **Resolution test** Provide confidence intervals or statistical tests (e.g., McNemar's test for paired success/failure outcomes) for the key comparisons. If the improvements are not statistically significant, temper the claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data set construction and potential bias
- **Claim pointer** The benchmark data set is described as nonredundant and designed to minimize data leakage with AI training sets.
- **Evidence pointer** Methods section "Benchmark Data Set Assembly"; Tables S1, S2 (not visible)
- **Concern** The data set construction relies on a CDR3 sequence identity threshold of 60% for redundancy removal. This is a reasonable but somewhat arbitrary choice. More importantly, the authors state that structures were selected based on deposition date after September 30th, 2021, to avoid overlap with training data. However, the training data cutoffs for different methods (AlphaFold2, ImmuneBuilder, NanoBot, RaptorX-Single, AlphaFold3) may differ, and some methods may have been trained on data released after this date. The authors should verify and report the actual training data cutoffs for each method and confirm that the benchmark data set does not overlap with any of them. Additionally, the exclusion of certain structures (e.g., PDB 7NBB for being a polyubiquitin chain) should be justified more thoroughly, as this could introduce selection bias.
- **Why it matters** The validity of the benchmark depends on ensuring that the evaluated methods have not seen the test structures during training. If there is any overlap, the reported success rates could be inflated, undermining the conclusions.
- **Resolution test** Provide a detailed table of training data cutoffs for each method and confirm that all benchmark structures fall outside these cutoffs. Justify all exclusion criteria and assess their potential impact on the results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity and reproducibility
- **Claim pointer** The authors describe a pipeline combining AI structure prediction and integrative modeling with HADDOCK3, including a framework-aware paratope definition.
- **Evidence pointer** Methods sections "Information Scenarios and Restraints Generation", "HADDOCK3 Docking Protocols", and "Paratope Analysis and Framework-Aware Restraints Definition"
- **Concern** The description of the framework-aware paratope definition is incomplete. The authors state that "several other regions were also defined as active" and list 10 regions, but it is unclear how these regions were selected. Were they derived from the clustering analysis of the Paratope Data Set? If so, how exactly? The relationship between the two identified binding modes and the specific regions listed needs to be clarified. Additionally, the authors mention that "when a region is defined as active, it is sufficient for any of the selected residues to be in contact with the antigen's defined epitope for the restraint to be satisfied," but the exact implementation in HADDOCK3 (e.g., how ambiguous restraints are defined for multiple residues) is not fully described.
- **Why it matters** The framework-aware paratope definition is a key contribution of the manuscript. Without a clear and complete description, other researchers cannot reproduce or build upon this work.
- **Resolution test** Provide a detailed description of how the regions were derived from the clustering analysis, including the criteria for selecting specific residues. Include a step-by-step description of how the restraints are implemented in HADDOCK3, possibly with a schematic figure.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with AlphaFold3
- **Claim pointer** The authors state that AlphaFold3 achieves higher success rates than AlphaFold2-Multimer on the benchmark data set, but they do not include AlphaFold3 in the docking pipeline comparisons.
- **Evidence pointer** Results section "AlphaFold Has Moderate Accuracy in Nanobody-Antigen Complex Prediction"; Table 1 (not visible)
- **Concern** The manuscript reports AlphaFold3 results (32.5% Top 1 acceptable SR) but excludes AlphaFold3 from the docking pipeline evaluation due to licensing restrictions. While this is understandable, the comparison between the proposed pipeline and AlphaFold3 is incomplete. The authors should discuss more explicitly how the proposed pipeline compares to AlphaFold3 in terms of both success rates and computational cost, and whether the pipeline offers advantages beyond what AlphaFold3 can achieve.
- **Why it matters** AlphaFold3 represents the current state of the art for complex prediction, and readers will want to know whether the proposed pipeline offers a meaningful alternative or improvement. Without a direct comparison, the practical value of the pipeline is unclear.
- **Resolution test** Provide a discussion section comparing the proposed pipeline to AlphaFold3 in terms of success rates, computational cost, and applicability. If possible, include a qualitative comparison based on the reported results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Results section "AlphaFold Has Moderate Accuracy in Nanobody-Antigen Complex Prediction"
- **Evidence pointer** Text describing AlphaFold3 results
- **Issue** The authors report AlphaFold3 results with 25 models generated per complex, but the number of seeds used is not clearly stated. The text mentions "5 different seeds" in the Methods section, but this is not explicitly linked to the AlphaFold3 results in the Results section.
- **Required correction** Clarify the number of seeds used for AlphaFold3 predictions in the Results section and discuss how this might affect the reported success rates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of information
- **Affected element** Results section "The Quality of Antigen Structure Prediction with AlphaFold2-Multimer Can Be Limiting for Docking"
- **Evidence pointer** Text describing antigen model selection
- **Issue** The authors state that they selected the best antigen models based on global pLDDT, but it is unclear how many models were generated per antigen and whether the selection was based on the complex prediction or the monomer prediction.
- **Required correction** Provide details on the number of models generated, the selection criteria, and whether the antigen models were extracted from the complex predictions or predicted separately.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Information-Driven HADDOCK Unbound Docking"
- **Evidence pointer** Text describing success rates
- **Issue** The manuscript reports success rates as percentages without specifying the number of cases or providing confidence intervals. For a data set of 40 complexes, a 5% difference represents only 2 cases.
- **Required correction** Report the number of successful cases alongside percentages and consider providing confidence intervals for key results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion completeness
- **Affected element** Discussion section
- **Evidence pointer** Text discussing limitations
- **Issue** The authors mention the limited size of the benchmark data set but do not discuss the potential impact of data set composition (e.g., antigen types, nanobody families) on the generalizability of the findings.
- **Required correction** Add a brief discussion of the diversity of the benchmark data set and how the results might generalize to other nanobody-antigen systems.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "HADDOCK3 Docking Protocols"
- **Evidence pointer** Text describing the docking protocol
- **Issue** The authors mention that the default HADDOCK scoring function is used but do not provide the exact parameters or version of HADDOCK3 used. The equation for the scoring function is provided, but the specific weights and terms may vary between versions.
- **Required correction** Specify the exact version of HADDOCK3 and any non-default parameters used in the docking runs.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Results section "Framework-Aware Paratope Description Improves the Modeling Success"
- **Evidence pointer** Text describing the new paratope definition
- **Issue** The term "framework-aware paratope" is used, but the distinction between this and the standard CDR-based paratope definition is not clearly explained in the main text.
- **Required correction** Provide a clear definition of the framework-aware paratope and how it differs from the standard definition, possibly with a schematic figure.

## Risk / unsupported claims
- The claim that the proposed pipeline achieves "higher success rates than the AlphaFold baseline on all generated models" is not fully supported without statistical testing, given the modest data set size.
- The claim that the framework-aware paratope definition improves docking performance is based on a single benchmark data set and needs validation on independent data.
- The statement that AlphaFold3 results are "consistent with other benchmarking studies" is not supported by specific citations in the provided text.
- The claim that the pipeline's computational requirements are "comparable to those of AlphaFold" is not quantified in the provided text.
- The generalizability of the findings beyond the specific benchmark data set is not established, particularly given the limited diversity of the data set.