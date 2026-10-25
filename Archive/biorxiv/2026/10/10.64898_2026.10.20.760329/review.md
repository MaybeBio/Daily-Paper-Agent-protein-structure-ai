## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present UnibindMD, an integrated computational platform combining five stages (BindCraft, Boltz-2, PRODIGY, ADMET-AI, GROMACS/CHARMM36m) for de novo peptide binder design. They report application to three Andes virus targets, with 464 accepted binders from 4,475 trajectories, top candidates at ipTM = 0.94 and pLDDT = 0.94, predicted binding free energies of -9.1 to -11.1 kcal mol-1, and stable 100 ns molecular dynamics simulations for three selected leads.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, simulation parameters, trajectory analyses, target structure preparation protocols, and supplementary data

## Reviewer

- **Overall assessment** The abstract describes a potentially useful integrated pipeline for peptide binder design, addressing a legitimate concern about over-reliance on self-consistent confidence metrics. However, the evidence presented in the abstract is insufficient to evaluate the technical soundness of the platform, the validity of the reported metrics, or the generalizability claims. Several quantitative claims lack methodological context, and the biological relevance of the three targets is asserted but not demonstrated with functional validation.
- **Who would be interested in the results, and why** Computational biologists and protein design researchers interested in integrated pipelines that combine deep learning with physics-based validation. Structural biologists working on viral entry mechanisms, particularly arenaviruses, may find the application to Andes virus relevant. Drug discovery scientists seeking practical workflows for peptide binder development could benefit if the platform is shown to be robust and generalizable.
- **Major strengths** The platform addresses a real limitation in current AI-based protein design, namely the circularity of self-consistent confidence metrics. The multi-stage design is logical and each component is well-established in the field. The choice of Andes virus targets is timely and clinically motivated, given the high case fatality rate and lack of approved therapeutics.
- **Major Concerns** The abstract reports quantitative results without sufficient methodological context to assess their validity. The acceptance rate range of 2.3-67.6% is extremely broad and unexplained. The molecular dynamics metrics are presented as evidence of stability but the criteria for "stable" are not justified. The claim of generalizability is unsupported by the single-target-family demonstration. No functional or experimental validation is presented.
- **Minor Comments** The abstract uses "G = -9.1 to -11.1 kcal mol-1" without specifying the sign convention or the method used by PRODIGY. The Kd range of 8 nM-0.2 μM spans more than an order of magnitude and is not discussed. The statement about ADMET-AI flagging "expected poor oral bioavailability" is vague and does not specify which properties were predicted. The relationship between the three targets and the "intervention points" framing is not explained in terms of therapeutic rationale.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail on the molecular dynamics setup, the criteria for selecting the three leads from 464 accepted binders, the statistical treatment of the trajectory analyses, or the validation of the PRODIGY predictions against known binders. The claim that the platform is "generalizable" is not supported by the evidence presented.
- **Assessment against Nature-style criteria** Originality: moderate. The integration of existing tools is useful but not conceptually novel. Scientific importance: potentially high if the platform is validated, but the abstract does not demonstrate this. Interdisciplinary readership: the work spans AI, structural biology, and drug discovery, which could attract broad interest. Technical soundness: cannot be assessed from the abstract alone. Readability for nonspecialists: the abstract is accessible but uses field-specific terms without sufficient explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible pipeline and promising preliminary results, but the lack of methodological detail and functional validation prevents assessment of whether the core claims are supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "all three remained stably bound over 100 ns of unrestrained molecular dynamics (receptor CαRMSD ≤ 2.6 Å, retained peptide fold, ≥ 99.5% of frames preserving more than half of the initial interface contacts, and 75-82% helical content)"
- **Evidence pointer** Abstract, location not provided
- **Concern** The molecular dynamics stability criteria are presented without justification. The threshold of "more than half of the initial interface contacts" is arbitrary and may not reflect meaningful binding. The helical content metric is reported without context for whether this is expected for the designed peptides or the target interface. The RMSD threshold of 2.6 Å is not compared to any control or reference simulation.
- **Why it matters** The central claim of the platform is that it provides dynamics-validated binders. If the stability criteria are not rigorous or are not benchmarked against known negatives, the validation step may be meaningless and the platform's advantage over single-method design is not established.
- **Resolution test** Provide the simulation setup, force field parameters, equilibration protocol, and a comparison of the stability metrics for the selected leads against negative controls or known non-binders. Justify the contact preservation threshold and show that it correlates with experimentally validated binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "By converting single-prediction design into a cross-validated, dynamics-tested workflow, UnibindMD provides a rapid, scalable, and generalizable path from any protein target to validated peptide-binder candidates"
- **Evidence pointer** Abstract, location not provided
- **Concern** The generalizability claim is based on three targets within a single viral system. No evidence is presented that the platform performs equally well on diverse target classes, such as protein-protein interaction interfaces, enzyme active sites, or membrane proteins. The "any protein target" claim is not supported by the data shown.
- **Why it matters** The stated value of the platform is its general applicability. If the platform only works on a narrow range of targets, the claim is misleading and the practical utility is limited.
- **Resolution test** Demonstrate the platform on targets from at least two additional protein families with different structural and biophysical characteristics. Report success rates and failure modes across these diverse targets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation adequacy
- **Claim pointer** "The three selected leads were predicted by PRODIGY to bind with G = -9.1 to -11.1 kcal mol-1 (Kd 8 nM-0.2 μM)"
- **Evidence pointer** Abstract, location not provided
- **Concern** The binding affinity predictions are computational only. No experimental validation, such as surface plasmon resonance, isothermal titration calorimetry, or cellular assays, is presented. The abstract does not state whether any of the 464 accepted binders were tested experimentally.
- **Why it matters** Computational predictions of binding affinity are known to have significant error. Without experimental confirmation, the claim that these are "validated peptide-binder leads" is not supported. The term "validated" is used in the abstract but appears to refer only to computational cross-validation.
- **Resolution test** Provide experimental binding data for at least the three selected leads, or clearly state that the results are computational predictions and adjust the language accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Acceptance rate reporting
- **Evidence pointer** Abstract, location not provided
- **Issue** The acceptance rate range of 2.3-67.6% across nine campaigns is extremely broad and unexplained. This range suggests high variability in performance across targets or conditions.
- **Required correction** Report the acceptance rate per target and discuss the sources of variability. If the range reflects different target difficulty, this should be stated explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "validated"
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract uses "validated" to describe the peptide-binder leads, but the evidence presented is entirely computational. This terminology may mislead readers into assuming experimental confirmation.
- **Required correction** Replace "validated" with "computationally assessed" or "in silico validated" throughout the abstract, or provide experimental data to justify the term.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** ADMET-AI results
- **Evidence pointer** Abstract, location not provided
- **Issue** The ADMET-AI statement is vague. "Expected poor oral bioavailability" and "no PAINS alerts" are reported without specific values or comparison to reference compounds.
- **Required correction** Report the specific ADMET properties predicted, such as permeability, solubility, and metabolic stability, and compare them to known peptide therapeutics or approved peptide drugs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Context
- **Affected element** Target selection rationale
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the three targets are "intervention points" for Andes virus but does not explain why these specific targets were chosen or how they relate to the viral life cycle and pathogenesis.
- **Required correction** Provide a brief rationale for each target, including its role in viral entry, replication, or pathogenesis, and why disrupting it with a peptide binder would be therapeutically relevant.

## Risk / unsupported claims

- The claim that UnibindMD provides "a rapid, scalable, and generalizable path from any protein target to validated peptide-binder candidates" is unsupported. The evidence covers only three targets in one viral system, and no experimental validation is presented.
- The claim that the three selected leads are "validated" is unsupported. All evidence is computational, and the term "validated" implies experimental confirmation that is not described.
- The molecular dynamics stability metrics are presented as evidence of binding stability, but no benchmarks, controls, or comparisons to known non-binders are provided. The criteria for "stable" are not justified.
- The predicted binding affinities (G = -9.1 to -11.1 kcal mol-1) are reported without experimental confirmation or comparison to known binders of the same targets.
- The acceptance rate range of 2.3-67.6% is reported without explanation, making it impossible to assess the consistency and reliability of the platform.
- The ADMET-AI results are reported in vague terms without specific values, preventing assessment of the developability claims.