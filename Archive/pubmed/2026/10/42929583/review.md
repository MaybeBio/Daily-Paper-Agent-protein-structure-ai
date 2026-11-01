## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Methods, Results, Discussion and Conclusions, Data and Software Availability, Acknowledgements). Supplementary Material section is listed but its content is not included.
- **Assessment boundary** Evaluation is restricted to the supplied manuscript text and the claims it makes. No independent verification of code, data repositories, competition leaderboards, or cited literature was performed. Numerical values are taken as reported by the authors.
- **Shared manuscript claim summary** The authors report two open-source, physics-based entries to the ASAP-Polaris-OpenADMET antiviral pose prediction challenge based on templated molecular growth with hybrid ML/MM potentials (FEgrow). They claim their approach was among the top-performing physics-based methods, that a retrospective workflow making greater use of training data as templates achieves a 74% success rate across SARS-CoV-2 and MERS-CoV Mpro, that building poses against an ensemble of feasible side-chain conformers (via ApoDock) improves the generation of low-RMSD poses, and that the tested scoring functions (ApoScore, gnina, short ABFE) cannot reliably select native-like poses from the generated ensemble.
- **Visible evidence base** Abstract; Introduction; Methods (prospective manual core selection, prospective MCS core selection, retrospective FEgrow plus ApoDock); Results (three subsections with references to Figures 1 to 6 and Sections S1 and S2); Discussion and Conclusions; Data and Software Availability. Figure content itself is not reproduced in the supplied text, only referenced.
- **Missing materials affecting confidence** Supplementary Material (Section S1 ABFE methods, Section S2 interaction fingerprints) is not provided. Figure panels are referenced but not included, so visual and quantitative details cannot be inspected. Competition leaderboard and organizer baseline values are cited but not reproduced. No per-ligand data tables are supplied.

## Reviewer
- **Overall assessment** This is a well-motivated and transparently reported account of a blind-challenge participation, with a useful negative result on pose selection from receptor ensembles. The work is strongest as a methodological case study and as a community resource. However, several central quantitative claims rest on retrospective reanalysis, on a small number of systems, and on comparisons to competition baselines that are not fully documented in the supplied text. The scoring-function and ABFE conclusions are appropriately hedged but are limited by the specific implementations tested. The manuscript is readable and the limitations are largely acknowledged, but the evidence as presented does not fully establish some of the headline performance and mechanistic claims without the missing supplementary detail and figure-level data.

- **Who would be interested in the results, and why** Computational chemists and structure-based drug design practitioners interested in pose prediction, template-based molecular growth, and receptor flexibility. Developers and users of open-source docking and scoring tools (FEgrow, ApoDock, gnina). Participants and organizers of blind challenges (D3R, CACHE, CASP, ASAP-Polaris-OpenADMET) interested in benchmarking methodology and in the failure modes of scoring functions. Researchers working on Mpro antiviral design who need to understand when rigid-receptor approximations break down.

- **Major strengths** The study addresses a genuinely important and under-reported problem, namely pose selection from generated ensembles rather than pose generation alone. The prospective blind-challenge context provides an objective external benchmark. The authors report a negative result (scoring functions no better than random) that is valuable to the community. The workflow is open-source and the data and code are made available. The retrospective improvement to 74% is a concrete, testable claim. The analysis of side-chain flexibility (M165, Q189, M49 for SARS-CoV-2; Q192, L49, M25, Q167, M168 for MERS-CoV) is mechanistically informative, and the compound 2 MERS-CoV example illustrates the induced-fit argument clearly. The manuscript distinguishes generation from selection, which is a useful conceptual framing.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / claim support
- **Claim pointer** The retrospective workflow achieves a 74% success rate across SARS-CoV-2 and MERS-CoV Mpro, described as would have been the competition's top-performing physics-based method and among the best across all categories for MERS-CoV.
- **Evidence pointer** Results, subsection "FEgrow Is among the Top-Scoring Physics-Based Methods in the Prospective Pose Challenge"; Figure 3 (MCS-based retrospective); Methods, subsection "Retrospective Analysis: Combining FEgrow and ApoDock".
- **Concern** The 74% figure is derived from a retrospective procedure that uses the released crystal structures and training-set receptor structures, and it is not a prospective result. The manuscript states that apart from hindsight no information unavailable at the start of the blind competition was used, but the retrospective MERS-CoV procedure builds ligands into SARS-CoV-2 training protein structures and maps them back onto the MERS-CoV reference by backbone alignment. The dependence of the reported success rate on this specific mapping and on the choice of closest-MCS training structure is not quantified, and no uncertainty estimate or per-target breakdown with confidence intervals is given.
- **Why it matters** The headline performance claim is the main quantitative result of the paper. If it is sensitive to arbitrary retrospective choices, the claim that the method would have been top-ranked is not established.
- **Resolution test** Provide per-target success rates with confidence intervals, a sensitivity analysis over the choice of template receptor structure and mapping procedure, and an explicit statement of which steps require post-hoc information. Report the same metric under a strictly prospective-compatible protocol.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / statistical support
- **Claim pointer** Neither ApoScore nor gnina is significantly better than random picking for selecting low-RMSD poses from the ensemble, and short ABFE calculations do not recover the lowest-RMSD conformers better than random.
- **Evidence pointer** Results, subsection "Scoring Functions Cannot Reliably Sort Binding Poses from Decoys"; Figure 5; Figure 6; Section S1 (not provided).
- **Concern** The negative conclusion is based on a single ensemble size (20 receptor structures), a single target pair, and a subset of 27 neutral MERS-CoV ligands for ABFE. The ABFE analysis explicitly does not enforce pose-restricted sampling and relies on short simulation time to keep ligands kinetically trapped, with acknowledged substantial shifts. The claim of no significant improvement is supported by a paired bootstrap, but the power of that test is not reported, and the absence of evidence is presented close to evidence of absence.
- **Why it matters** The paper's central methodological message is that scoring is the bottleneck. If the tests are underpowered or the sampling is inadequate, the conclusion may reflect the specific protocol rather than a general property of scoring functions.
- **Resolution test** Report statistical power or effect sizes for the random-versus-scoring comparisons, expand the ABFE subset and ensemble size where feasible, and state explicitly that the conclusion is limited to the tested protocols. Provide the ABFE convergence diagnostics referenced in Section S1.

- **Concern ID** R1-M3
- **Severity** Major
 **Blocking** No
- **Axis** Technical soundness / reproducibility
- **Claim pointer** Building poses against an ensemble of feasible side-chain conformers is useful in generating improved binding poses, with enrichment of low-RMSD poses especially for MERS-CoV.
- **Evidence pointer** Results, subsection "Rigid Receptor Approximation Limits Achievable Accuracy"; Figure 4; Figure 5; Section S2 (not provided).
- **Concern** The enrichment claim rests on the subset of structures with the lowest ligand RMSD per compound (blue points), which is a best-case selection and therefore not a measure of prospective utility. The reported fractions (72% SARS-CoV-2, 59% MERS-CoV with pocket RMSD < 2 Å) are conditional on already having selected the best pose. The ApoDock ensemble was generated once per target rather than conditioned per ligand, which the authors acknowledge, and the per-residue RMSD distributions show ApoDock underestimates the L49 displacement in MERS-CoV.
- **Why it matters** The claim that side-chain ensembles are useful for generation is plausible but the presented metric conflates generation capacity with selection, and the ensemble may not sample the relevant conformational states.
- **Resolution test** Report generation enrichment using an unbiased metric that does not condition on the best pose, quantify how often the native-like side-chain conformation is present in the ensemble, and state the fraction of cases where the correct pose is absent from the ensemble entirely.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim support / comparison validity
- **Claim pointer** The approach was among the top-performing physics-based methods, and the corrected MCS-based entry would have moved alongside another template-based approach as the top-ranked open-source software entries.
- **Evidence pointer** Abstract; Results, subsection "FEgrow Is among the Top-Scoring Physics-Based Methods in the Prospective Pose Challenge"; Introduction.
- **Concern** The ranking claims depend on competition leaderboard values that are summarized in the text but not reproduced, and on a post-hoc correction of 11 misaligned structures. The effect of that correction on the reported 47% and 48% values is described qualitatively but the corrected prospective numbers are not given as a clean before-and-after table. Comparisons to POSIT, FlexX, Glide, and EasyDock/AutoDock are cited from the competition report rather than independently analyzed.
- **Why it matters** Ranking claims are relative claims and require the comparison set to be visible and consistently computed.
- **Resolution test** Provide a table of all physics-based entries with success rates as reported by the organizers, clearly mark which values are the authors' own and which are from the leaderboard, and give the corrected prospective success rates before and after the alignment fix.

- **Major Concerns** (continued)

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / method description
- **Claim pointer** The hybrid ML/MM protocol with scaled Lennard-Jones radii and charges mitigates the rigid-protein approximation, and the lowest-energy conformation is extracted as the best pose.
- **Evidence pointer** Methods, first paragraph; Introduction.
- **Concern** The scaling of Lennard-Jones radii and atomic charges is described as mitigating the rigid-protein approximation but no values, rationale, or validation are given in the supplied text. The selection of the single lowest-energy conformer as the pose is a strong assumption that is not benchmarked against alternative selection criteria within the prospective workflow.
- **Why it matters** These choices directly affect pose accuracy and reproducibility, and readers cannot assess or reproduce them from the supplied text.
- **Resolution test** State the scaling factors and their basis, and report a sensitivity analysis of pose success to the conformer selection criterion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Prospective submission results
- **Evidence pointer** Results, subsection "FEgrow Is among the Top-Scoring Physics-Based Methods in the Prospective Pose Challenge"
- **Issue** The text reports 47% and 48% before correction and 54% after correction for the MCS approach, but the corrected value for the manual core submission is not stated.
- **Required correction** Report the corrected success rate for the manual core submission alongside the MCS value.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure references
- **Evidence pointer** Results, multiple subsections; Figures 1 to 6
- **Issue** Several figure references appear without panel letters in the supplied text (for example "Figure  a", "Figure  b"), and the mapping between claims and specific panels is sometimes ambiguous.
- **Required correction** Ensure every figure citation specifies the panel and that each quantitative claim points to a specific panel.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Software naming
- **Evidence pointer** Methods and Results
- **Issue** The software is referred to as both "Apodock" and "ApoDock" in different places.
- **Required correction** Use a single consistent spelling throughout.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** ABFE protocol
- **Evidence pointer** Results, subsection "Scoring Functions Cannot Reliably Sort Binding Poses from Decoys"; Section S1 (not provided)
- **Issue** The ABFE protocol is summarized as 0.1 ns per window with five independent replicates, but the number of windows, the restraint scheme, and the convergence criteria are only in Section S1, which is not supplied.
- **Required correction** Summarize the key ABFE parameters in the main text and ensure Section S1 is available to reviewers and readers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Claim precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract; Discussion and Conclusions
- **Issue** The phrase "among the top-performing physics-based methods" is used without a defined threshold or rank.
- **Required correction** State the rank or percentile relative to the 13 physics-based entries.

- **Technical failings that need to be addressed before the case is established** R1-M1 (retrospective 74% claim lacks sensitivity analysis and uncertainty), R1-M2 (negative scoring conclusion may be underpowered and protocol-limited), R1-M3 (enrichment metric conditions on best pose), R1-M4 (ranking claims depend on unreproduced leaderboard values and post-hoc correction), R1-M5 (ML/MM scaling and pose selection not documented).

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The individual components (FEgrow, ApoDock, gnina, ABFE) are established. The originality lies in the blind-challenge evaluation, the generation-versus-selection framing, and the negative result on pose selection from receptor ensembles. This is a useful contribution but not a conceptual advance.
  - **Scientific importance** Moderate to high for the computational drug design community. The finding that side-chain ensembles improve generation but not selection is practically important and aligns with known scoring limitations. The claim of a 74% retrospective success rate, if robust, would be of interest, but its retrospective nature limits its weight.
  - **Interdisciplinary readership** Limited. The work is specialized and assumes familiarity with docking, ML/MM potentials, and free energy calculations. The conceptual message about generation versus selection could interest a broader computational audience, but the manuscript is written primarily for specialists.
  - **Technical soundness** Partially established. The prospective workflow is clearly described. The retrospective analyses are plausible but under-supported in the supplied text, with missing supplementary detail, absent uncertainty estimates, and metrics that condition on best-case selection.
  - **Readability for nonspecialists** Fair. The Introduction provides good context on Mpro and blind challenges. The Results are dense with method-specific terminology and would benefit from a schematic of the workflow and a clearer separation of prospective and retrospective results.

- **Recommendation posture** Currently not established from the provided evidence for the headline retrospective performance and ranking claims. Supportive if technical concerns are resolved, specifically if the retrospective 74% claim is accompanied by sensitivity analysis and uncertainty, if the scoring and ABFE negative results are reported with power or effect sizes and explicit protocol limitations, and if the ranking comparisons are made fully visible. The negative result on pose selection is the most robust and valuable element and could anchor a revised manuscript.

## Risk / unsupported claims
- The claim that the retrospective workflow "would have been the competition's top-performing physics-based method" is not supported by the supplied material because the leaderboard values are summarized rather than reproduced and the retrospective protocol uses post-hoc information.
- The claim that the approach was "among the top-performing physics-based methods" lacks a defined rank or threshold in the supplied text.
- The claim that scaling Lennard-Jones radii and atomic charges "mitigate[s] to some extent the rigid-protein approximation" is asserted without values, rationale, or validation.
- The claim that ApoDock-generated ensembles are "similar to those observed experimentally" is based on visual comparison of distributions and is qualified by the authors as "not in perfect agreement"; it is weak as stated.
- The claim that scoring functions are "unable to successfully pick out native structures" is supported only for the specific implementations, ensemble size, and target pair tested, and the statistical power of the comparison is not reported.
- The claim that short ABFE calculations fail to enrich low-RMSD poses is limited by the acknowledged lack of pose-restricted sampling and by the small subset of 27 neutral MERS-CoV ligands.
- The statement that "apart from the use of hindsight, we did not use any information here that was unavailable at the start of the blind competition" is difficult to evaluate because the retrospective procedure depends on released crystal structures and training-set receptor structures, and the boundary between hindsight and available information is not precisely defined.
- The reported 72% and 59% pocket RMSD fractions for the lowest-ligand-RMSD subset are conditional on best-pose selection and should not be interpreted as prospective enrichment.