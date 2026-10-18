## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors propose a computationally guided dual-modification strategy for porcine hemoglobin, combining covalent phosphorylation with non-covalent EGCG interactions. They report that molecular dynamics simulations identify key stabilizing residues, that EGCG binding reduces alpha-helix content from 74% to 30%, and that the resulting complex improves surface hydrophobicity, antioxidant activity, foaming capacity, and pork sausage texture (springiness and chewiness) relative to phosphorylated hemoglobin alone.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or numerical results beyond those stated in the abstract
- **Missing materials affecting confidence** Full methods for phosphorylation and EGCG conjugation, MD simulation parameters and validation, spectroscopic data (circular dichroism or FTIR), surface hydrophobicity assay details, antioxidant assay specifics, foaming capacity measurements, sausage formulation and texture analysis protocol, statistical analysis details, and any raw data or supplementary information

## Reviewer

- **Overall assessment** The abstract presents an interesting and potentially valuable approach to valorizing hemoglobin from meat processing by-products. The combination of computational prediction with experimental modification is conceptually appealing and the reported outcomes, particularly the improvement in sausage texture, are practically relevant. However, the abstract alone provides insufficient detail to assess the rigor of the computational methods, the validity of the structural conclusions, or the statistical robustness of the functional and textural claims. Several key claims are presented without supporting numerical data or methodological context, and the relationship between the molecular-level observations and the macroscopic meat quality outcomes is not mechanistically established.
- **Who would be interested in the results, and why** Researchers and technologists in meat science, food protein chemistry, and food ingredient valorization would find these results relevant. The work addresses a real industrial problem, namely the underutilization of blood by-products, and proposes a modification strategy that could be adapted to other proteins. Those working on protein-polyphenol interactions and their functional consequences would also have interest, as would groups focused on computational approaches to food protein engineering.
- **Major strengths** The study addresses a genuine sustainability challenge in meat processing. The integration of artificial neural network prediction and molecular dynamics simulations to guide experimental modification is a forward-looking approach. The reported improvement in sausage springiness and chewiness, specifically overcoming phosphorylation-induced brittleness, is a practically meaningful outcome. The identification of specific residues contributing to complex stability provides a molecular-level rationale for the observed effects.
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
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to good, as the combination of computational guidance with dual covalent and non-covalent modification for hemoglobin is not a common approach, though individual elements are established in the literature. Scientific importance is moderate, with clear applied relevance but limited fundamental advance. Interdisciplinary readership is plausible, spanning food science, protein chemistry, and computational biology, though the work is unlikely to attract broad attention beyond these fields. Technical soundness cannot be fully assessed from the abstract, and several claims require verification. Readability for nonspecialists is acceptable, with the abstract being generally clear, though some terms and transitions are abrupt.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting concept and promising results, but the lack of methodological detail and supporting data prevents verification of the core claims. A supportive posture would require access to the full manuscript and resolution of the major concerns.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations and binding energy calculations revealed that ALA142, ASN139 and THR38 make the most significant contributions to complex stability through robust hydrogen bonding networks.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract provides no information on the simulation methodology, including force field parameters, simulation length, equilibration protocol, or the method used for binding energy calculation (for example MM-PBSA, MM-GBSA, or other approaches). Without this context, the reliability of the residue-level contributions cannot be evaluated. Additionally, the criteria for defining "most significant contributions" are not stated, and no quantitative values for binding energies or per-residue decomposition are provided.
- **Why it matters** The computational findings are presented as the rational basis for the entire modification strategy. If the simulation methodology is not robust or the binding energy calculations are not converged, the molecular-level rationale for the experimental design is undermined. Residue-level claims require rigorous validation, as they are often sensitive to simulation parameters and analysis methods.
- **Resolution test** Provide full simulation details, including software, force field, water model, simulation time, temperature and pressure coupling, and convergence criteria. Report binding energy values with standard deviations and per-residue decomposition data. Ideally, validate the predicted key residues through mutagenesis or at least through comparison with experimental structural data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that spectroscopic analysis confirmed that EGCG interaction drastically reduced the alpha-helix content from 74% to 30%, inducing a conformational opening that exposed cryptic hydrophobic pockets.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract does not specify which spectroscopic technique was used, such as circular dichroism or FTIR, nor does it provide the conditions under which the measurement was made. The magnitude of the reported change, from 74% to 30% alpha-helix content, is substantial and would represent a major structural reorganization. No information is given on how the secondary structure percentages were calculated, whether the measurement was performed on the phosphorylated hemoglobin or the native protein as the baseline, or whether the EGCG concentration used in the spectroscopic study matches that used in the functional assays.
- **Why it matters** The structural change is central to the proposed mechanism, as the authors link the conformational opening to improved surface hydrophobicity and functional properties. If the secondary structure analysis is not performed under controlled and comparable conditions, or if the baseline is not clearly defined, the interpretation of the structural transition is unreliable. The claim of exposed hydrophobic pockets is also speculative without supporting evidence, such as dye-binding assays or structural modeling.
- **Resolution test** Specify the spectroscopic method, sample preparation, buffer conditions, and EGCG concentration. Provide the full spectra or at least the deconvolution results. Clarify whether the baseline is native Hb, phosphorylated Hb, or both. Provide independent evidence for hydrophobic pocket exposure, such as ANS fluorescence or a comparable probe.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the modified Hb exhibited superior surface hydrophobicity, antioxidant activity, and foaming capacity, and that the EGCG-PHb complex effectively overcame phosphorylation-induced gel brittleness and significantly enhanced springiness and chewiness in a pork sausage model.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** No numerical data are provided for any of the functional properties. There are no values for surface hydrophobicity, antioxidant activity, foaming capacity, or texture parameters. The abstract does not state the magnitude of improvement, the statistical significance, the number of replicates, or the statistical tests used. For the sausage model, no information is given on the concentration of EGCG-PHb added, the formulation of the sausages, the cooking protocol, or the texture analysis method, such as TPA parameters and probe geometry.
- **Why it matters** The applied claims are the most practically significant part of the study. Without quantitative data and statistical analysis, the reader cannot assess whether the reported improvements are meaningful or reproducible. The claim that the complex "effectively acted" to overcome brittleness is vague and requires specific texture profile data to be convincing.
- **Resolution test** Provide quantitative results for all functional assays, including mean values, standard deviations, and p-values or confidence intervals. Specify the number of independent replicates. For the sausage study, provide the full formulation, processing conditions, and texture analysis parameters. Ideally, include a comparison of native Hb, phosphorylated Hb, and EGCG-PHb in the same model system.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that the dual-modification strategy provides new insights into the development and utilization of Hb.
- **Evidence pointer** Abstract, Conclusion section; location not provided
- **Concern** The abstract does not establish a clear mechanistic link between the molecular-level observations, such as the identified key residues and the secondary structure change, and the macroscopic functional outcomes in the sausage model. It is not clear whether the improved texture is due to the EGCG binding, the phosphorylation, or a synergistic effect of both. The claim of "new insights" is therefore not substantiated, as the abstract does not demonstrate that the computational predictions were validated experimentally or that the mechanism of action is understood beyond a descriptive level.
- **Why it matters** For the work to have broader scientific impact, the mechanism connecting the modification strategy to the functional improvement needs to be articulated and supported by evidence. Without this, the study remains an empirical demonstration rather than a mechanistic advance, which limits its value to the field.
- **Resolution test** Provide a mechanistic model that links the structural changes induced by EGCG binding and phosphorylation to the observed functional properties. This could include dose-response studies, comparison of singly modified versus dually modified Hb, or correlation analyses between structural parameters and functional outcomes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Background section
- **Evidence pointer** Abstract, Background; location not provided
- **Issue** The phrase "computationally guided dual-modification strategy" is introduced without explaining how the computational guidance was used in the experimental design. The connection between the artificial neural network prediction and the actual modification conditions is unclear.
- **Required correction** Briefly state what the neural network predicted and how that prediction informed the choice of modification conditions, such as EGCG concentration or phosphorylation degree.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results; location not provided
- **Issue** The transition from the molecular dynamics results to the spectroscopic analysis is abrupt. It is not clear whether the simulations were performed on the EGCG-Hb complex, the EGCG-phosphorylated Hb complex, or both.
- **Required correction** Specify the exact system used in the simulations and clarify the relationship between the simulated complex and the experimentally characterized complex.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results; location not provided
- **Issue** The abstract mentions "superior surface hydrophobicity, antioxidant activity and foaming capacity" but does not state the comparison baseline. It is unclear whether these properties are superior to native Hb, phosphorylated Hb, or both.
- **Required correction** State the comparator for each functional property, for example "compared to phosphorylated Hb" or "compared to native Hb."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Conclusion section
- **Evidence pointer** Abstract, Conclusion; location not provided
- **Issue** The conclusion states that the complex "significantly improved" sausage texture, but the abstract does not provide any indication of the magnitude of improvement or whether the improvement was observed at all EGCG-PHb concentrations tested.
- **Required correction** Include a brief quantitative statement, such as the percentage improvement in springiness or chewiness, and note whether the effect was dose-dependent.

## Risk / unsupported claims

- The claim that ALA142, ASN139 and THR38 are the most significant contributors to complex stability is unsupported without simulation details and quantitative binding energy data.
- The claim that alpha-helix content decreased from 74% to 30% is unsupported without specifying the spectroscopic method, conditions, and analysis approach.
- The claim that the modified Hb exhibited superior surface hydrophobicity, antioxidant activity, and foaming capacity is unsupported without numerical data and comparator information.
- The claim that EGCG-PHb significantly enhanced springiness and chewiness in pork sausages is unsupported without texture data, statistical analysis, and formulation details.
- The claim that the dual-modification strategy provides "new insights" is not substantiated, as the mechanistic link between molecular changes and functional outcomes is not established.
- The overall applicability of the approach to other meat products or proteins is not assessable from the abstract.