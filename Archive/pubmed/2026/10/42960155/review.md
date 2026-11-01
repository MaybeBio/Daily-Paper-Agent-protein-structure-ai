## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Materials and methods, Data and code availability, Acknowledgments, Author contributions, Declaration of interests, Supplemental information listing)
- **Assessment boundary** Single-reviewer technical and conceptual assessment of the supplied manuscript text only. No reanalysis of deposited data, no access to source code, model weights, or internal datasets, and no independent verification of the cited prospective experimental studies.
- **Shared manuscript claim summary** The authors present Xelari, a modular structure-based pipeline for de novo DNA and RNA aptamer design from protein structures without target-specific SELEX data or retraining. The pipeline combines five trained models (INGA, InNA, AliNA, Edgar, ValentiNA) and three algorithmic modules (Ehrlich, DiNA, MoNA). Individual modules are benchmarked retrospectively against computational or experimental references. Prospectively, three DNA aptamers designed against *Treponema pallidum* proteins showed cell-associated binding in a treponeme assay (apparent KD 0.91 to 2.57 micromolar), and a fourth DNA aptamer functioned as a capture reagent for Tau441 in a serum-based hybrid assay. The authors position structure-based design as a complement to experimental selection and explicitly state that a general success rate is not established.
- **Visible evidence base** Abstract; Introduction; Results (Xelari architecture, target preparation, surface site specificity, binding-site localization, InNA, AliNA, Edgar, scaffold library, MoNA assembly, complex relaxation and affinity prediction, chemical modifications, prospective validation); Discussion; Materials and methods; Data and code availability; Acknowledgments; Author contributions; Declaration of interests; Supplemental information listing (Figure S1, Tables S1 to S15 referenced but not provided in the submission).
- **Missing materials affecting confidence** Supplemental figures and tables (S1 to S15) are referenced throughout but not included in the supplied text. Source code, model weights, and internal training datasets are explicitly not deposited. The complete denominator of candidates ranked, synthesized, and tested in the prospective studies is not reported. The two prospective experimental studies are cited rather than presented in full. The ValentiNA calibration dataset (Table S11) and retrospective affinity compilation (Table S12) are not available for inspection.

## Reviewer
- **Overall assessment** The manuscript describes a modular, structure-first pipeline for aptamer design and reports module-level retrospective benchmarks plus two prospective applications. The framing is unusually candid about limitations, and the authors repeatedly and correctly distinguish ranking association from absolute prediction, retrospective from prospective evidence, and feasibility from success rate. The principal scientific weakness is that the central claim, that the complete workflow can generate functional aptamers against new targets without SELEX, rests on four DNA aptamers evaluated in two settings, neither of which provides purified-target 1:1 binding data for the intended protein, and neither of which reports the candidate denominator. The module benchmarks are informative but do not compose into an end-to-end accuracy estimate, and the authors acknowledge this. Several technical concerns (proprietary pipeline, non-deposited code and weights, non-homology-controlled Edgar DNA split, calibration and evaluation overlap, RNA-only MoNA benchmark, G-quadruplex exclusion) limit reproducibility and generality. The work is a credible feasibility demonstration and a useful methodological contribution if the technical concerns are addressed and the claims are held to the narrower scope the authors themselves articulate.

- **Who would be interested in the results, and why** Researchers in aptamer discovery and nucleic-acid therapeutics, particularly groups working on targets that are difficult to produce in purified native form (membrane proteins, disordered proteins, post-translationally modified targets). Computational structural biologists and machine-learning practitioners interested in surrogate models for physics-based reference calculations across coupled design stages. Assay developers interested in aptamer-antibody hybrid formats. The work is likely to be of interest to the readership of a molecular therapy or nucleic-acid therapeutics journal, and the modular architecture may be of broader methodological interest to the molecular design community.

- **Major strengths**
  - The problem framing is well motivated. The Introduction gives a specific and technically grounded account of SELEX constraints (target production, library coverage, amplification bias, post-selection modification) rather than a generic critique.
  - The decomposition of de novo design into sequential subproblems, each with a stated reference method and a stated surrogate, is a coherent and inspectable architecture.
  - The InNA benchmark is the strongest quantitative result in the manuscript. Sub-kcal/mol RMSE against r2SCAN-3c on 483,735 pair geometries, with lysine and glutamic acid held out entirely from training and validation, is a meaningful transfer result for a pairwise scoring function.
  - The manuscript is unusually explicit about what its evidence does not show. The authors state that the cellular assay does not establish intended-target engagement, that the Tau441 study does not provide an aptamer-only affinity, that the ValentiNA panel does not establish family-independent accuracy, that the Edgar benchmark is not homology-controlled for DNA, and that the MoNA benchmark is RNA-only.
  - The chemical-modification analysis, while limited, tests directional ranking across three distinct modification classes (C5 base, 2-prime sugar, backbone) and reports both attenuation and exaggeration of predicted effects rather than only favorable cases.
  - The Discussion identifies concrete failure modes and a specific next test (a prospective series with predefined denominators and independent replication), which is a constructive framing.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** End-to-end validation and claim scope
- **Claim pointer** The manuscript claims that Xelari enables de novo aptamer design from protein structure without target-specific SELEX data, and that Xelari-generated candidates can retain experimental function after synthesis in more than one biological and assay setting.
- **Evidence pointer** Results, Prospective experimental validation; Results, Prospective live-cell binding; Results, Prospective application to Tau441 detection in serum; Discussion
- **Concern** The prospective evidence comprises four DNA aptamers in two settings. In the *T. pallidum* study, binding was measured on intact cells and was not confirmed against the purified intended lipoproteins, so engagement of the design target is not established. In the Tau441 study, the aptamer served as a capture reagent in a sandwich format in which both recognition reagents contribute to signal, and no aptamer-only 1:1 affinity or independently mapped epitope is reported. Neither study reports the complete denominator of candidates ranked, synthesized, and tested. The central claim of the manuscript therefore rests on a small number of functional successes whose target-level attribution is not established.
- **Why it matters** The headline claim is about a design capability, not about four specific sequences. Without a denominator and without target-engagement confirmation, the reader cannot distinguish a pipeline that reliably produces functional candidates from one that produced four functional sequences among an unknown number attempted. The authors acknowledge this, but the Abstract and title still carry the stronger framing.
- **Resolution test** Report the complete candidate denominator for each prospective campaign (ranked, synthesized, tested, functional). Provide purified-target binding data for at least the *T. pallidum* aptamers, or an epitope-mapping or competition experiment that assigns the cellular signal to the intended lipoprotein. For Tau441, provide an aptamer-only binding measurement or an epitope-mapping experiment. Alternatively, restrict the Abstract and title claims to the demonstrated scope.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and independent verification
- **Claim pointer** The manuscript presents Xelari as a platform whose modules are benchmarked and whose predictions are deposited for independent recalculation.
- **Evidence pointer** Data and code availability; Results, Xelari architecture; Materials and methods, Data sources, training, and test datasets
- **Concern** Source code, model weights, checkpoints, and internal training and model-development datasets are explicitly not deposited. The prediction platform is proprietary and available for academic use upon request. The deposited material permits recalculation of reported benchmark statistics from frozen predictions but does not permit re-execution of the pipeline, retraining of any model, or independent application of Xelari to a new target. The claim that the pipeline is modular and that individual failure modes are separately inspectable is therefore not independently testable by a reader.
- **Why it matters** A methods paper whose central object is a computational pipeline is difficult to evaluate or build upon if the pipeline cannot be run. The module benchmarks can be checked arithmetically from the deposit, but the composition of modules into the end-to-end workflow, which is the actual claim, cannot. This also limits the ability of the community to test the authors' own stated next step, a broader prospective series.
- **Resolution test** Deposit at minimum the inference code and frozen weights for the five trained models and the three algorithmic modules, or provide a documented execution environment sufficient to reproduce the reported prospective designs from the deposited target structures. If full release is not possible, state explicitly which claims are and are not independently reproducible from the deposit.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark independence and calibration
- **Claim pointer** ValentiNA showed MAE of 0.931 kcal/mol and Spearman rho of 0.795 across 32 retrospective records associated with 27 structural templates, and the calibrated predictions for the three *T. pallidum* aptamers differed from measured apparent KD values by 1.06- to 1.18-fold.
- **Evidence pointer** Results, Complex relaxation and affinity prediction; Figure 7; Materials and methods, Prediction of the complex binding free energy with ValentiNA; Materials and methods, Validation protocol; Table S11; Table S12
- **Concern** The calibration coefficients were fitted on 17 literature records (Table S11), and the retrospective evaluation uses 32 records (Table S12). The manuscript states that separation by PDB identifier does not establish independence and that related aptamer-target systems can occur in both calibration and evaluation. The template-aggregated sensitivity analysis collapses repeated structural inputs but does not establish statistical independence. The three *T. pallidum* comparisons apply a global affine calibration fitted on 17 separate complexes and report 1.06- to 1.18-fold agreement, but the authors correctly note this is not an independent test of ranking accuracy. The reported accuracy metrics therefore describe correspondence within a panel that is not demonstrably independent of calibration.
- **Why it matters** The reported MAE and Spearman rho are presented as the quantitative performance of the affinity module. If calibration and evaluation records overlap at the aptamer-family or target-family level, these numbers overstate generalization. The authors flag this, but the Abstract reports the numbers without the caveat.
- **Resolution test** Report the overlap between the 17 calibration records and the 32 evaluation records at the aptamer-family and target-family level, not only by PDB identifier. Provide a held-out evaluation in which neither the aptamer family nor the target family appears in calibration. If the panel cannot support this, state the overlap explicitly in the Abstract.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Module benchmark validity
- **Claim pointer** Edgar correlated with experimental folding energies but did not reproduce their absolute scale, supporting its use as a ranking heuristic. AliNA achieved a mean F1 of 0.757 on 339 PDB-derived RNA evaluation sequences.
- **Evidence pointer** Results, Folding free energy estimation; Figure 6; Results, Predicting the secondary structure of candidate sequences; Materials and methods, Edgar folding-free-energy assessment; Materials and methods, Nucleic acid secondary structure prediction with AliNA
- **Concern** Two issues affect the interpretation of these benchmarks. First, the Edgar internal test set is not homology-controlled for DNA because sequence augmentation preceded random partitioning, so augmented variants of one parent structure can appear in more than one subset; the reported R2 of 0.958 therefore measures approximation of the simulation reference and not generalization. The authors state this. Second, the AliNA evaluation set is disjoint from training at the Rfam-family level, but the lower-similarity stratum contains only 33 sequences and the pseudoknot analysis is restricted to the higher-similarity subset (n = 86) for RNA and is not scored for the lower-similarity RNA subset (n = 14) or ssDNA (n = 4). The reported mean F1 of 0.757 aggregates strata of very different size and does not characterize performance on sequences distant from training.
- **Why it matters** Both modules are used as filters or ranking heuristics inside the pipeline, and their behavior on out-of-distribution inputs determines whether the pipeline can be expected to work on targets and sequences unlike those in training. The current benchmarks do not establish this.
- **Resolution test** For Edgar, report a homology-controlled DNA split and the corresponding metrics. For AliNA, report stratified metrics separately with confidence intervals, and state explicitly what the lower-similarity stratum can and cannot support given n = 33.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generative scope and internal consistency
- **Claim pointer** Xelari generates de novo DNA and RNA aptamers from protein structures. The current scaffold library contains approximately 12,000 RNA and 11,000 DNA single-chain scaffolds spanning 15 to 45 nt.
- **Evidence pointer** Results, Generation and structural validation of the scaffold library; Results, Assembly of full-length aptamers from the scaffold library; Discussion; Materials and methods, Scaffold library construction; Materials and methods, Assembly of the full-length aptamers from the scaffold library
- **Concern** The generative scope is narrower than the title and Abstract imply. G-quadruplex folds are not enumerated and MoNA does not generate them, yet G-quadruplex aptamers are a major and therapeutically validated class. The MoNA topology-recovery benchmark contains RNA assemblies only, so the DNA assembly path is not benchmarked at the assembly stage. The DNA branch reconstructs in RNA representation and converts to DNA, and the manuscript reports that 86.3 percent of converted chains classify as B-like after relaxation, but also states that this establishes backbone geometry and not that the tertiary fold or protein-binding energetics survive conversion. The DNA structural benchmark (median RMSD 2.52 Angstrom, median lDDT 0.724 over 58 structures) is computed over paired heavy atoms only and does not address binding competence.
- **Why it matters** The prospective validation is entirely DNA, while the assembly benchmark is entirely RNA and the reconstruction path for DNA goes through an RNA intermediate. The evidence chain for the DNA branch, which is the branch that produced the only prospective functional results, is therefore the least directly benchmarked.
- **Resolution test** Provide a DNA MoNA assembly benchmark analogous to the RNA benchmark. Report whether any of the four prospective DNA aptamers were tested for retention of the intended fold after conversion, or provide a binding-competence comparison between the RNA-intermediate model and the final DNA model for at least one case.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** INGA reliability and downstream propagation
- **Claim pointer** INGA is used for conformational relaxation of the target and of the aptamer-protein complex, and is described as complementing conventional geometry optimization and molecular dynamics.
- **Evidence pointer** Results, Target preparation; Figure 2; Table S1; Materials and methods, Conformational relaxation using the INGA neural network model
- **Concern** The reported INGA behavior includes substantial geometric artifacts. Raw outputs increased mean potential energy by 170 to 211 eV relative to input, produced 2.51 to 14.36 unphysical bond lengths per structure on average, and up to 28 percent of outputs contained more than five unphysical bond lengths. GFN-FF refinement reduced the energy increase to 1.8 to 5.3 eV but did not resolve the bond-length artifacts, and the fail rate was slightly higher after refinement (up to 30 percent). Retention of structures already in the target cluster dropped from 96.4 percent with GFN-FF alone to 50.4 percent after the full INGA-GFN-FF step. INGA is used at two points in the pipeline, for target relaxation and for complex relaxation before ValentiNA scoring.
- **Why it matters** A relaxation module that degrades already-correct conformations and introduces unphysical geometry in a substantial fraction of outputs will propagate error into site selection, seed construction, and final affinity ranking. The manuscript reports these numbers but does not quantify the downstream consequence.
- **Resolution test** Report the effect of INGA-introduced geometry on downstream stages, for example by comparing DiNA localization or ValentiNA ranking with and without INGA relaxation on a defined subset. Report the fraction of pipeline runs in which the final complex passed a geometry sanity check.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Abstract accuracy
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The Abstract reports the ValentiNA MAE and Spearman rho and the InNA RMSE without the caveats that appear in the Results, specifically that the ValentiNA panel does not establish family-independent validation and that the Edgar benchmark is not homology-controlled for DNA. The Abstract does state that the analysis does not establish family-independent validation for ValentiNA, which is appropriate, but the InNA and AliNA numbers are reported without their scope conditions.
- **Required correction** Add a single clause to the Abstract stating the scope condition for each reported metric, or move the metrics to a summary sentence that carries the caveats.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Numerical reporting
- **Affected element** Results, Folding free energy estimation; Figure 6
- **Evidence pointer** Figure 6; Results, Folding free energy estimation
- **Issue** The text reports a regression slope of 1.793 and intercept of minus 3.489 for predicted on experimental energy, while the Figure 6 legend reports a least-squares fit with predicted energy on the x axis and slope 0.400, intercept 0.255. The two regressions are of different variables and the text does not make the direction explicit at the point of use.
- **Required correction** State the regression direction explicitly in the text and in the figure legend, and label the axes so that the reported slope and intercept can be matched to the plotted line without ambiguity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Complex relaxation and affinity prediction; Table S14
- **Evidence pointer** Results, Complex relaxation and affinity prediction; Table S14
- **Issue** The G4 and non-G4 strata are compared by point estimates only, and the manuscript correctly states that the point estimates do not establish equivalence. However, the G4 group is entirely thrombin-associated, so topology, target identity, chemistry, and assay conditions are fully confounded. The text notes this but the stratified statistics are still presented in a way that invites a topology interpretation.
- **Required correction** Either remove the G4 versus non-G4 stratified statistics from the main text and retain them only as a supplementary descriptive table, or add an explicit statement at the point of presentation that the comparison is uninterpretable with respect to topology.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Results, Analysis of surface site specificity; Materials and methods, Target surface analysis and binding site selection with Ehrlich
- **Evidence pointer** Results, Analysis of surface site specificity; Equation 1; Materials and methods, Target surface analysis and binding site selection with Ehrlich
- **Issue** Equation 1 uses weights alpha_g and alpha_c with the statement that both components are combined with equal weights alpha_g = alpha_c, while the Materials and methods state that geometric and compositional components are combined with equal weights alpha = beta = 1. The notation is not consistent between the two locations.
- **Required correction** Use a single notation for the two weights throughout and state the numerical value once.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure and table completeness
- **Affected element** Supplemental information listing
- **Evidence pointer** Supplemental information
- **Issue** Tables S1 through S15 and Figure S1 are referenced throughout the Results and Materials and methods but are not included in the supplied manuscript text. Several quantitative claims, including the INGA bond-length statistics, the AliNA stratified metrics, the MoNA benchmark, and the ValentiNA calibration and evaluation records, depend on these tables.
- **Required correction** Ensure that all referenced supplemental tables and figures are included in the version provided to reviewers and readers, and that the values cited in the main text can be verified directly against them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Runtime claim
- **Affected element** Abstract; Results, Xelari architecture; Results, Prospective live-cell binding
- **Evidence pointer** Abstract; Results, Xelari architecture; Results, Prospective live-cell binding
- **Issue** The title and Abstract emphasize design "in hours." The per-target computational time is reported as approximately 2 to 3 h on a single H200 GPU, with observed wall-clock time below 24 h on shared infrastructure including scheduling latency, and scaffold library construction performed offline. The prospective *T. pallidum* section also notes that the under-24-h figure refers to the module versions and hardware of that campaign and is not a runtime benchmark of the present pipeline version.
- **Required correction** State the runtime claim once, in a single location, with the hardware, the inclusion or exclusion of scheduling latency, and the exclusion of scaffold library construction and of synthesis and experimental confirmation, and use the same figure consistently in the title, Abstract, and Results.

- **Technical failings that need to be addressed before the case is established** R1-M1 (prospective denominator and target engagement), R1-M2 (code and weights not deposited), R1-M3 (calibration and evaluation overlap), R1-M4 (Edgar DNA split and AliNA lower-similarity stratum), R1-M5 (DNA assembly path not benchmarked), R1-M6 (INGA geometry artifacts and downstream propagation).

- **Assessment against Nature-style criteria**
  - **Originality** The individual components are largely adaptations of existing ideas: surrogate models for physics-based reference calculations, surface-patch descriptors for specificity, secondary-structure prediction, and graph-neural-network folding-energy estimation. The originality lies in the composition of these into a single structure-first pipeline for aptamer design and in the explicit decomposition of the design problem into separately benchmarked subproblems. This is a meaningful methodological contribution but not a conceptual advance of the kind associated with a broad multidisciplinary journal.
  - **Scientific importance** The problem is important, and the demonstration that structure-based design can produce experimentally functional aptamers without SELEX is a useful existence proof. The importance is currently limited by the small prospective sample, the absence of target-engagement confirmation in the cellular assay, the absence of an aptamer-only affinity for Tau441, and the proprietary nature of the pipeline. The work is more likely to be of high interest to the specialized aptamer and nucleic-acid therapeutics community than to a general readership.
  - **Interdisciplinary readership** The manuscript is written for a computationally literate but biologically oriented audience, and the modular framing is accessible. The relevance to adjacent fields (protein design, molecular recognition, assay development) is plausible but would be strengthened by a clearer statement of what a non-specialist should take from the results.
  - **Technical soundness** The InNA benchmark is technically strong. The Ehrlich benchmarks are reasonable. The DiNA localization benchmark is reported under two aggregation schemes and the authors are explicit about the difference. The Edgar, AliNA, INGA, MoNA, and ValentiNA benchmarks each carry stated limitations that the authors disclose. The principal soundness gap is that the module benchmarks do not compose into an end-to-end accuracy estimate, and the prospective evidence does not close that gap.
  - **Readability for nonspecialists** The manuscript is generally well organized and the limitations are stated clearly. The density of module names and acronyms is high, and a reader outside the field will need the architecture figure and a glossary to follow the Results. The Abstract is readable but carries several numerical claims whose scope conditions appear only later.

- **Recommendation posture** Currently not established from the provided evidence for the full claim as framed in the title and Abstract. Supportive of publication in a specialized venue if the technical concerns are resolved, specifically if the prospective candidate denominator and target-engagement data are provided, if the calibration and evaluation overlap is quantified at the family level, if the DNA assembly path is benchmarked, and if the code and weights are made available or the reproducibility boundary is stated explicitly. The narrower claim, that a structure-first pipeline can produce experimentally functional DNA aptamers in two assay settings without SELEX, is supported by the supplied material.

## Risk / unsupported claims
- The claim that Xelari enables de novo aptamer design "in hours" is supported only for the computational candidate generation step on a specific GPU, excludes scaffold library construction, and excludes synthesis and experimental confirmation. The title and Abstract do not carry these exclusions.
- The claim that the three *T. pallidum* aptamers bind their intended lipoprotein targets is not supported. Binding was measured on intact cells and was not confirmed against purified intended targets.
- The claim that the Tau441 aptamer binds Tau441 with a defined affinity is not supported. The reported KD of 0.92 nM is a workflow prediction, and the manuscript states it is not treated as experimentally validated.
- The claim that ValentiNA achieves MAE of 0.931 kcal/mol and Spearman rho of 0.795 as a general performance figure is weak, because the evaluation panel is not demonstrably independent of the calibration panel at the aptamer-family or target-family level.
- The claim that Edgar reproduces folding free energies is not supported in absolute terms. The manuscript reports predictive R2 of minus 3.976 and a regression slope of 1.793, and correctly restricts the claim to ranking.
- The claim that AliNA generalizes to sequences distant from training is weak, because the lower-similarity stratum contains 33 sequences and the pseudoknot analysis is restricted to the higher-similarity subset.
- The claim that the DNA branch of the pipeline produces binding-competent DNA folds is not established. The reported structural benchmark covers paired heavy atoms only and the manuscript states that it does not address protein-binding energetics after conversion.
- The claim that the pipeline is modular and that failure modes are separately inspectable is not independently testable, because source code, model weights, and internal datasets are not deposited.
- The claim that the prospective studies constitute independent validation is not supported. The manuscript itself states that the *T. pallidum* characterization was authored predominantly by Xelari-affiliated individuals and should not be regarded as fully independent third-party validation, and that neither study constitutes fully independent third-party validation.
- The claim that the approach is a complement to experimental selection is a positioning statement rather than a tested proposition. No head-to-head comparison with SELEX on a matched target is reported.