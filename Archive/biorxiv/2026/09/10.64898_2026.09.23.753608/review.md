## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided; supplementary materials referenced but not provided.
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and presentation as presented in the supplied text. No independent verification of data or code was performed.
- **Shared manuscript claim summary** The authors present AtomWeaver, a flow-matching generative model for peptide inverse folding that generates side-chain atom coordinates conditioned on a fixed backbone and target protein, with residue identity assigned post-hoc by matching predicted atom clouds against a reference library of canonical and non-canonical amino acid templates. The central claims are: (i) the model can access a broad non-canonical vocabulary without retraining; (ii) it achieves competitive canonical recovery and superior functional ranking on a deep mutational scan benchmark; (iii) it maintains self-consistency on de novo binder backbones; and (iv) it can recover stereochemical and backbone-modified residues in a case study on Hirulog-3.
- **Visible evidence base** Main text tables (Tables 1, 2, 3), figures (Figures 2, 3, 4), and benchmark descriptions. Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary Methods (S1–S19), Supplementary Tables (S1, S2, S3, S5, S9), Supplementary Figures (S2, S3, S5, S6, S7, S8, S9), and the PeptideArena benchmark details are not provided. These are essential for evaluating model architecture, training details, benchmark construction, and statistical analyses.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to inverse folding that decouples atom generation from residue identity assignment, enabling a flexible and extensible vocabulary. The core idea of generating unlabeled atom clouds and reading identity post-hoc is novel and potentially impactful for non-canonical peptide design. However, the evidence provided in the main text is insufficient to fully evaluate the method's performance and the strength of the claims. Key benchmark details, statistical analyses, and ablation studies are relegated to supplementary materials that were not available for review. The reported numerical advantages over baselines are modest and accompanied by overlapping confidence intervals, which the authors appropriately acknowledge but do not fully resolve. The manuscript would benefit from clearer presentation of the benchmark methodology and a more critical discussion of the limitations of the current evidence.
- **Who would be interested in the results, and why** Researchers in computational protein and peptide design, particularly those working on inverse folding, generative models for biomolecules, and non-canonical amino acid incorporation. The work is also relevant to medicinal chemists and therapeutic peptide developers interested in expanding the chemical space accessible to computational design. The methodological contribution of a coordinate-first generative approach with post-hoc identity assignment could influence future model designs in the broader generative chemistry community.
- **Major strengths**
  1. The conceptual novelty of separating atom generation from residue identity assignment is a genuine contribution. This design choice directly addresses a key limitation of existing inverse folding methods, namely their restriction to a fixed canonical vocabulary.
  2. The use of a structured geometric prior (nested shells along a backbone-derived direction) is a thoughtful and physically motivated alternative to the ubiquitous isotropic Gaussian prior in flow matching.
  3. The inclusion of a deep mutational scan benchmark with non-canonical substitutions is a valuable and relatively rare evaluation approach that goes beyond simple recovery metrics.
  4. The authors are appropriately cautious in their interpretation of numerical results, explicitly noting overlapping confidence intervals and the distinction between point estimates and statistically resolved differences.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that AtomWeaver achieves "high observed mean agreement with experimental values among the compared inverse-folding methods" on the deep mutational scan benchmark, and that it "retains ranking signal" in the mixed canonical/non-canonical setting.
  - **Evidence pointer** Table 3, Section 4.5, Supplementary Section S17, Supplementary Table S5
  - **Concern** The main text reports point estimates of agreement (mean ™ρ) but the associated uncertainty, provided only in Supplementary Table S5, is described as "overlapping" between methods. Without access to these intervals, it is impossible to assess whether the reported numerical advantages are meaningful or within noise. The authors state that the intervals are "not independent experimental-replication intervals," which further complicates interpretation. The claim of "high observed mean agreement" is therefore not adequately supported by the visible evidence.
  - **Why it matters** The central functional claim of the paper rests on this benchmark. If the differences between methods are not statistically resolvable, the claim of superiority, however cautiously worded, is not established. The reader cannot evaluate the strength of the evidence without the supplementary intervals.
  - **Resolution test** Provide the full bootstrap interval table in the main text or a clearly accessible supplementary file, and include a direct statistical comparison (e.g., paired bootstrap tests) between AtomWeaver and each baseline. If differences are not significant, the claims should be revised to reflect equivalence rather than advantage.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Benchmark validity
  - **Claim pointer** The manuscript introduces PeptideArena, a new benchmark of de novo designed peptide binders, and claims that AtomWeaver is "competitive with the field" on canonical self-consistency while maintaining self-consistency with non-canonical content.
  - **Evidence pointer** Section 4.4, Figure 3, Supplementary Table S3, Supplementary Figure S6
  - **Concern** The PeptideArena benchmark is new and not yet established in the field. The selection of targets, the generation of backbones via BoltzGen, and the use of OpenDDE for refolding are all described only briefly. The choice of OpenDDE over more established folding models (e.g., AlphaFold2) is justified only by its handling of non-canonical residues, but no validation of OpenDDE's accuracy on peptide-protein complexes is provided. The benchmark's ability to discriminate between methods is unclear without a more detailed description of its construction and validation.
  - **Why it matters** A new benchmark must be convincingly validated before its results can be used to support claims about method performance. If the benchmark is biased or noisy, the conclusions drawn from it are unreliable. The lack of detail on benchmark construction and validation is a significant gap.
  - **Resolution test** Provide a detailed description of PeptideArena's construction, including target selection criteria, backbone generation parameters, clustering and filtering thresholds, and a validation of OpenDDE's refolding accuracy on a set of known peptide-protein complexes. Ideally, include a comparison of OpenDDE's performance against other folding models on canonical peptides.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological clarity
  - **Claim pointer** The manuscript claims that the nested shell prior is a key technical innovation that makes the joint atom generation and identity readout tractable, and that it "appeared to make this optimization problem substantially more tractable."
  - **Evidence pointer** Section 3, Supplementary Methods S1–S4, Supplementary Figure S2, Supplementary Table S1
  - **Concern** The description of the nested shell prior in the main text is brief and qualitative. The formal definition of the prior, the derivation of the conditional flow matching objective with this non-Gaussian source, and the specific implementation details (e.g., how the shell radii and thicknesses are computed, how the prior is sampled at inference) are all in the supplementary methods, which were not provided. The claim that the prior improves optimization is presented as a hypothesis ("we offer two hypotheses for why") without supporting ablation data.
  - **Why it matters** The nested shell prior is presented as a central contribution of the work. Without a clear and complete description of its formulation and implementation, the method cannot be reproduced or fully evaluated. The lack of ablation evidence weakens the claim that this specific design choice is responsible for the method's performance.
  - **Resolution test** Provide the full mathematical formulation of the nested shell prior and the corresponding flow matching objective in the main text or a clearly accessible supplement. Include an ablation study that compares the nested shell prior against an isotropic Gaussian prior, holding all other components fixed, to quantitatively assess its contribution.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of claims
  - **Claim pointer** The manuscript claims that AtomWeaver "serves canonical and non-canonical peptide design alike" and that the vocabulary is "an expandable inference-time choice."
  - **Evidence pointer** Sections 4.3, 4.6, 5, Supplementary Table S9
  - **Concern** The evidence for non-canonical design is limited to a single case study (Hirulog-3) and a benchmark where the non-canonical candidates are drawn from a fixed set of 21 substitutions. The claim of an "expandable" vocabulary is supported only by the six withheld types, which show the weakest performance (median percentile ≈63). The practical utility of adding a new non-canonical residue at inference time, without any retraining, is not demonstrated beyond this limited test.
  - **Why it matters** The central promise of the method is its ability to access non-canonical chemistry. If the performance on unseen non-canonical types is poor, the practical value of the approach is diminished. The current evidence is too limited to support the broad claim of serving non-canonical design "alike" to canonical design.
  - **Resolution test** Expand the evaluation of non-canonical design to include a larger and more diverse set of non-canonical types, including those with backbone modifications beyond β-amino acids. Provide a systematic analysis of how performance varies with the structural and chemical properties of the non-canonical types.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Section 4.5, Table 3
  - **Evidence pointer** Table 3, Section 4.5
  - **Issue** The distinction between "single-site design" and "joint design" is described in the text but the implications for the reader are not immediately clear. The joint design setting is more realistic for de novo design but the results are presented without a clear explanation of why the joint setting is more challenging or how the baselines differ in their joint design procedures.
  - **Required correction** Add a brief explanation of the practical difference between single-site and joint design, and clarify why the joint setting is the more relevant test for de novo peptide design.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 4.5, Table 3
  - **Evidence pointer** Table 3, Section 4.5
  - **Issue** The manuscript reports mean ™ρ values but does not report the distribution of these values across positions. Given the small number of positions (39 total), the mean could be driven by a few positions with high agreement.
  - **Required correction** Report the per-position ™ρ values or a measure of dispersion (e.g., standard deviation, interquartile range) alongside the mean.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 8, Model availability
  - **Evidence pointer** Section 8
  - **Issue** The manuscript states that the model and code are released, but does not specify the exact version of the code, the dependencies, or the hardware requirements for inference. This limits reproducibility.
  - **Required correction** Provide a detailed README with installation instructions, dependency versions, and example commands for inference and benchmark evaluation.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Section 1, Introduction
  - **Evidence pointer** Section 1
  - **Issue** The introduction mentions UNAAGI as a related non-canonical inverse folding method but does not provide a detailed comparison of the two approaches. Given that UNAAGI is the closest prior work, a more explicit discussion of similarities and differences would help position the contribution.
  - **Required correction** Add a paragraph in the introduction or discussion that directly compares AtomWeaver with UNAAGI in terms of methodology, vocabulary flexibility, and reported performance.

## Risk / unsupported claims
- The claim of "high observed mean agreement with experimental values" on the deep mutational scan benchmark is not fully supported without the supplementary bootstrap intervals and a direct statistical comparison with baselines.
- The claim that the nested shell prior is responsible for the method's tractability and performance is not supported by any ablation data.
- The claim that AtomWeaver "serves canonical and non-canonical peptide design alike" is not fully supported given the limited evaluation of non-canonical design (one case study, one benchmark with a fixed non-canonical set, and weak performance on withheld types).
- The claim that the vocabulary is "an expandable inference-time choice" is not fully supported by the evidence, as the performance on unseen non-canonical types is the weakest reported result.
- The PeptideArena benchmark's validity as a discriminating evaluation tool is not established without a detailed description of its construction and validation.
- The use of OpenDDE for refolding is not validated against established folding models, which could affect the interpretation of self-consistency results.