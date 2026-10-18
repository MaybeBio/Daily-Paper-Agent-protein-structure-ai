## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The study reports that phytic acid (PA) complexes with soybean beta-conglycinin (7S) and glycinin (11S) most strongly near pH 3.0, reducing solubility and promoting aggregation. PA binding decreases beta-sheet content in both proteins, reduces gastric hydrolysis, increases intestinal hydrolysis, and is supported by molecular docking, molecular dynamics simulations, and isothermal titration calorimetry showing higher affinity for 11S.
- **Visible evidence base** Abstract text only; no numerical data beyond those cited, no experimental protocols, no statistical analyses, no structural or calorimetric figures
- **Missing materials affecting confidence** Full manuscript, experimental methods, statistical details, raw or representative data for circular dichroism, simulated digestion, ITC, docking and MD outputs, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a coherent and potentially interesting study on PA interactions with two major soy proteins, with a plausible mechanistic framework. However, the evidence base is limited to summary statements, and several claims cannot be independently evaluated without access to the full methods and data. The reported effects on secondary structure and digestibility are modest in magnitude, and the abstract does not clarify whether these changes are statistically robust or biologically meaningful. The molecular simulation and ITC results are presented as supportive but their integration with experimental data is not fully transparent.
- **Who would be interested in the results, and why** Researchers in food protein chemistry, plant protein functionality, and gastrointestinal digestion, particularly those studying antinutritional factors such as phytic acid in soy-based foods. The findings may also interest those working on protein-polyphenol or protein-ligand interactions and their impact on protein digestibility, with potential applications in food formulation and nutritional science.
- **Major strengths** The study addresses a relevant and under-explored topic, namely the interaction of phytic acid with specific soy protein fractions rather than whole protein isolates. The combination of experimental and computational approaches is commendable, and the use of ITC to quantify binding affinity adds quantitative rigor. The focus on pH-dependent behavior is appropriate given the relevance of gastric and intestinal conditions.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide statistical measures (e.g., error bars, p-values) for the reported structural and digestibility changes, nor does it specify the number of replicates. The relationship between the docking/MD predictions and the experimental observations is asserted but not demonstrated with quantitative comparisons. The ITC data are reported as single dissociation constants without indication of fitting quality or experimental conditions beyond pH and temperature.
- **Assessment against Nature-style criteria** Originality: moderate, as PA-protein interactions are known, but the focus on 7S and 11S fractions is a useful contribution. Scientific importance: limited for a broad audience, as the findings are specific to soy protein processing and digestion. Interdisciplinary readership: narrow, primarily food science and protein biochemistry. Technical soundness: cannot be fully assessed from the abstract, but the described methods are appropriate. Readability for nonspecialists: the abstract is clear and accessible, though some terms (e.g., beta-sheet content, ITC) assume basic familiarity.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical reporting and the integration of computational and experimental evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness
- **Claim pointer** The abstract states that PA binding reduced beta-sheet content from 36.0% to 31.4% in 7S and from 37.3% to 35.1% in 11S, and that hydrolysis decreased from 10.59% to 7.42% for 7S and from 9.93% to 6.92% for 11S during gastric digestion.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract reports specific numerical changes in secondary structure and digestibility but provides no indication of variability, replication, or statistical significance. The magnitude of the beta-sheet changes (4.6 and 2.2 percentage points) and gastric hydrolysis reductions (about 3 percentage points) may be within experimental noise, especially for circular dichroism-based secondary structure estimation.
- **Why it matters** Without statistical measures, the reader cannot determine whether the observed effects are real or artifacts. This is critical because the central claim of the study, that PA binding alters protein structure and digestibility, depends on these quantitative differences being robust.
- **Resolution test** Provide mean values with standard deviations or confidence intervals, number of independent replicates, and appropriate statistical tests (e.g., t-test or ANOVA) for each reported comparison. If the differences are not statistically significant, the claims should be revised.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Integration of computational and experimental evidence
- **Claim pointer** The abstract states that molecular docking and molecular dynamics simulations provided theoretical support for interpreting the experimental observations, suggesting contributions from electrostatic interactions and hydrogen bonding, with more extensive contacts predicted for PA-11S.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract asserts that simulations support the experimental findings, but no quantitative link is provided. For example, the predicted binding energies, contact numbers, or interaction residues are not reported, nor is it shown how these predictions correlate with the ITC-derived affinities or the observed structural changes.
- **Why it matters** The claim of "theoretical support" is only meaningful if the computational results are quantitatively compared with experimental data. Without this, the simulations remain speculative and do not strengthen the mechanistic interpretation.
- **Resolution test** Report key simulation outputs (e.g., binding free energies, hydrogen bond occupancy, contact maps) and explicitly compare them with ITC data and structural changes. If the simulations are only qualitative, state this limitation and avoid implying direct validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation of digestibility changes
- **Claim pointer** The abstract states that hydrolysis decreased during gastric digestion but increased during subsequent intestinal digestion for both proteins.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not explain the mechanism by which PA binding reduces gastric hydrolysis but enhances intestinal hydrolysis. Possible explanations include pH-dependent dissociation of the complex, differential enzyme accessibility, or changes in protein aggregation state, but none are discussed.
- **Why it matters** The digestibility results are a key outcome of the study, and the opposing effects in gastric versus intestinal phases are intriguing. Without a mechanistic explanation, the findings remain descriptive and their implications for nutritional science are unclear.
- **Resolution test** Provide a mechanistic discussion supported by data, such as pH-dependent complex stability, enzyme activity assays, or structural characterization of the complexes under gastric and intestinal conditions. If the mechanism is not fully resolved, acknowledge this as a limitation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of ITC reporting
- **Affected element** Isothermal titration calorimetry results
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract reports dissociation constants of 12.3 muM for 11S and 32.5 muM for 7S, but does not specify the stoichiometry (n) or the thermodynamic parameters (DeltaH, DeltaS) beyond stating that binding is enthalpically and entropically favorable for 7S and enthalpy-driven for 11S.
- **Required correction** Provide the full set of ITC-derived parameters, including stoichiometry and enthalpy and entropy changes, and indicate the fitting model used. This will allow readers to assess the thermodynamic basis of the binding differences.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** pH dependence
- **Affected element** Complex formation near pH 3.0
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that complex formation was most pronounced near pH 3.0, but does not specify the pH range tested or the methods used to assess complex formation (e.g., turbidity, light scattering, or binding assays).
- **Required correction** Briefly describe the pH range and the experimental approach used to determine the pH optimum, and clarify whether the observed behavior is consistent with electrostatic interactions given the pKa of phytic acid and the isoelectric points of the proteins.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "hydrolysis" versus "digestibility"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract uses "hydrolysis" to describe the degree of protein breakdown during simulated digestion, but the term "digestibility" is used in the title and elsewhere. These are related but not identical concepts, and the abstract does not define how hydrolysis was quantified.
- **Required correction** Define the metric used (e.g., degree of hydrolysis, percentage of peptide bonds cleaved) and ensure consistent terminology throughout the abstract and manuscript.

## Risk / unsupported claims
- The claim that PA binding reduces beta-sheet content is unsupported without statistical analysis and raw spectral data.
- The claim that simulations provide "theoretical support" is unsupported without quantitative comparison to experimental results.
- The claim that hydrolysis increases during intestinal digestion is unsupported without data on the extent of increase and its variability.
- The claim that binding is enthalpically and entropically favorable for 7S but enthalpy-driven for 11S is unsupported without full thermodynamic parameters.
- The general implication that these findings have implications for protein hydrolysis during gastrointestinal digestion is not directly supported by the abstract, as the study uses simulated conditions and the physiological relevance is not discussed.