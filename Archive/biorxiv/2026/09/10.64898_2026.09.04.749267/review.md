## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a computational pipeline combining a fine-tuned ProGen-2 protein language model with an ESM-2 discriminator to generate 5.6 million novel Rubisco-like sequences, from which 21 diverse candidates were predicted active, 6 were soluble in E. coli, 5 produced quantifiable 3PGA, one showed an apparent CO₂/O₂ specificity estimate exceeding natural Rubiscos assayed, and one crystal structure matched the predicted dimer and active-site geometry with sub-angstrom Cα agreement.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** All experimental details, sequence generation parameters, filtering criteria, activity assay protocols, specificity measurement methods, structural refinement statistics, and raw data

## Reviewer
- **Overall assessment** The abstract describes a potentially significant advance in applying protein language models to a long-standing challenge in enzyme engineering. The reported results, if fully substantiated, would represent a notable step toward exploring Rubisco sequence space beyond natural diversity. However, the abstract alone provides insufficient detail to evaluate the rigor of the computational pipeline, the validity of the activity and specificity measurements, or the quality of the structural evidence. Several claims, particularly the CO₂/O₂ specificity estimate and the structural agreement, require careful scrutiny of the underlying data before the central conclusions can be accepted.
- **Who would be interested in the results, and why** Researchers in enzyme engineering, protein design, computational biology, and photosynthesis research would find these results relevant. The work speaks directly to efforts in carbon fixation improvement and demonstrates a generalizable approach for applying PLMs to enzyme families with complex folding and assembly requirements. The broader protein design community would also be interested in the demonstration that sequence-only generation followed by structural filtering can recover functional proteins.
- **Major strengths** The work addresses a well-recognized and important challenge in Rubisco engineering, namely the tight coupling of folding, assembly, specificity, and catalysis that has hampered traditional approaches. The scale of sequence exploration (5.6 million sequences) and the claim of accessing previously unobserved phylogenetic space suggest a genuinely novel approach. The combination of computational generation with experimental validation, including a crystal structure, represents a comprehensive pipeline. The reported success rate, while modest, is plausible for a first-generation design effort.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "One design produced an apparent CO₂/O₂ specificity estimate beyond the range of the natural representative Rubiscos assayed"
- **Evidence pointer** location not provided
- **Concern** The abstract reports a single design with an apparent CO₂/O₂ specificity estimate exceeding natural Rubiscos, but provides no information about the assay method, the number of replicates, the error associated with the measurement, or the identity and number of natural Rubiscos used as comparators. The word "apparent" is concerning, as it may indicate a preliminary or indirect measurement rather than a direct specificity determination.
- **Why it matters** CO₂/O₂ specificity is a central parameter in Rubisco function and the primary motivation for much of the engineering effort in this field. An overinterpreted or methodologically weak specificity measurement could mislead the field and undermine the central claim of the paper. The specificity of Rubisco is notoriously difficult to measure accurately, and small methodological differences can produce large apparent differences.
- **Resolution test** Provide the full assay methodology, including the kinetic equations used, the number of independent measurements, the statistical error, and a direct comparison with multiple natural Rubiscos measured under identical conditions. The specificity value should be reported with confidence intervals and the comparison should be statistically robust.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "We also solved the crystal structure of one de novo design that reproduced the predicted dimer and active-site geometry with sub-angstrom Cα agreement"
- **Evidence pointer** location not provided
- **Concern** The claim of sub-angstrom Cα agreement between the predicted model and the crystal structure is presented without any supporting statistics. No resolution of the crystal structure, R-factors, or the specific regions over which the Cα agreement was calculated are provided. Sub-angstrom agreement over what fraction of the structure, and with what quality of electron density, are critical questions.
- **Why it matters** Structural validation is a key piece of evidence that the computational pipeline correctly predicted the fold. However, sub-angstrom Cα agreement can be misleading if it is calculated over only a subset of residues or if the crystal structure is of low resolution. The structural claim is central to the paper's argument that the design approach can predict native-like geometry.
- **Resolution test** Provide the crystallographic statistics (resolution, Rwork/Rfree, completeness), the number of residues included in the Cα comparison, and a clear statement of whether the comparison includes the active-site residues specifically. Ideally, show a superposition figure with the predicted model and the experimental structure.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** "we leveraged recent advances in protein large language models (PLMs) to generate sequences beyond those observed in nature, using both ProGen-2 that was fine-tuned on a limited dataset of non-Form I Rubiscos and an ESM-2 discriminator"
- **Evidence pointer** location not provided
- **Concern** The abstract does not describe the training data composition, the fine-tuning procedure, the discriminator threshold, or the criteria by which the 21 candidates were selected from the 5.6 million generated sequences. The phrase "limited dataset of non-Form I Rubiscos" raises questions about whether the training set was sufficiently diverse to enable meaningful exploration of sequence space.
- **Why it matters** The reproducibility and generalizability of the approach depend entirely on the details of the computational pipeline. Without knowing the training data, the model architecture choices, and the filtering criteria, other researchers cannot assess whether the approach is broadly applicable or whether the results are specific to this particular implementation.
- **Resolution test** Provide a complete description of the training data (including sequence counts, taxonomic diversity, and sequence identity thresholds), the fine-tuning protocol, the discriminator architecture and threshold selection, and the full filtering cascade from 5.6 million to 21 candidates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "Six designs were soluble in Escherichia coli, and five were shown to produce quantifiable 3PGA"
- **Evidence pointer** location not provided
- **Concern** The abstract reports that 5 of 6 soluble designs produced quantifiable 3PGA, but does not provide the activity levels, the assay conditions, the background subtraction, or the sensitivity of the detection method. The distinction between "quantifiable" and "active" is unclear, and the catalytic rates are not reported.
- **Why it matters** The production of 3PGA is the key functional readout for Rubisco activity. Without quantitative activity data, it is impossible to assess whether these designs are merely marginally active or whether they approach the catalytic efficiency of natural Rubiscos. The field needs to know whether these are useful starting points or only proof-of-concept.
- **Resolution test** Provide specific activity values (kcat, or at minimum, 3PGA production rates normalized to protein amount), the assay detection limit, negative controls, and a comparison with a natural Rubisco assayed under identical conditions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Claim scope
- **Claim pointer** "providing a broadly accessible path toward generating de novo Rubiscos that have activity and specificity parameters needed to address longstanding limitations in biological carbon fixation"
- **Evidence pointer** location not provided
- **Concern** The concluding claim that this approach provides a "broadly accessible path" toward Rubiscos with the parameters needed to address carbon fixation limitations extends beyond what the reported data can support. The abstract reports one design with an apparent specificity beyond natural comparators and five designs with quantifiable 3PGA production, but no data on catalytic efficiency, CO₂ affinity, or overall performance relative to the requirements for improving carbon fixation.
- **Why it matters** The significance of the work for the carbon fixation community depends on whether the generated designs have properties that could be useful in practical applications. The current data suggest proof-of-concept but do not establish that the approach can generate Rubiscos with the combination of properties needed for meaningful improvements in carbon fixation.
- **Resolution test** Either temper the concluding claims to match the reported data, or provide additional data showing that the generated designs have catalytic properties approaching or exceeding those of natural Rubiscos in relevant contexts.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** "apparent CO₂/O₂ specificity estimate"
- **Evidence pointer** location not provided
- **Issue** The use of "apparent" to qualify the specificity estimate is ambiguous. It is unclear whether this indicates a preliminary measurement, a computational prediction, or a measurement made under non-standard conditions.
- **Required correction** Clarify the meaning of "apparent" in this context and specify whether the value was measured experimentally or predicted computationally.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** "21 highly diverse candidates predicted to be active"
- **Evidence pointer** location not provided
- **Issue** The abstract does not define what "predicted to be active" means in this context. The ESM-2 discriminator presumably provides a score, but the threshold and the basis for calling a sequence "active" are not described.
- **Required correction** Define the prediction criteria and the confidence associated with the activity predictions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** "beyond the range of the natural representative Rubiscos assayed"
- **Evidence pointer** location not provided
- **Issue** The abstract does not specify which natural Rubiscos were used as comparators. The specificity of Rubisco varies widely across organisms, and the choice of comparators significantly affects the interpretation.
- **Required correction** List the natural Rubiscos used for comparison and their measured specificity values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Precision
- **Affected element** "sub-angstrom Cα agreement"
- **Evidence pointer** location not provided
- **Issue** The abstract does not specify the numerical value of the Cα RMSD or the number of residues over which it was calculated.
- **Required correction** Report the specific RMSD value and the fraction of residues included in the comparison.

## Risk / unsupported claims
- The claim that one design has a CO₂/O₂ specificity beyond natural Rubiscos is unsupported without assay details and statistical analysis; the use of "apparent" further weakens this claim.
- The claim of sub-angstrom Cα agreement is unverifiable without crystallographic statistics and the specific RMSD value.
- The claim that the approach is "broadly accessible" and provides a path toward Rubiscos with parameters needed to address carbon fixation limitations is not supported by the reported data, which demonstrate proof-of-concept but not practical utility.
- The claim of occupying "regions of Rubisco phylogenetic space not previously observed in nature" is unverifiable without a phylogenetic analysis showing the placement of the generated sequences relative to known Rubiscos.
- The overall success rate (5 active designs from 5.6 million generated sequences) is presented without context for how this compares to other design approaches or what the expected success rate would be for random sequences.