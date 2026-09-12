## Review setup
- **Input scope** Full manuscript (abstract only provided)
- **Assessment boundary** Claims and evidence as presented in the abstract
- **Shared manuscript claim summary** The authors report the identification and characterization of two xanthine oxidase (XO) inhibitory peptides (QGDIVAIPSGAAHW and AFYLAGGVPR) from sesame 11S globulin trypsin hydrolyzate, demonstrating mixed-type inhibition, preferential binding to the FAD domain of XO via molecular docking and MD simulations, and in vivo efficacy in a zebrafish hyperuricemia model.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript (methods, results, figures, tables, supplementary data), experimental details for kinetics, docking, MD simulations, and zebrafish model

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting discovery of food-derived XO inhibitory peptides from sesame with a novel FAD-domain targeting mechanism. However, the evidence base is too limited to evaluate the rigor of the claims. Critical details on peptide identification, kinetic analysis, computational validation, and in vivo experimental design are absent. The claim of preferential FAD domain binding requires stronger experimental support beyond computational predictions.

- **Who would be interested in the results, and why** Researchers in food chemistry, nutraceuticals, and functional foods, particularly those studying bioactive peptides for hyperuricemia management. The FAD-domain targeting mechanism may also interest structural biologists studying XO inhibition.

- **Major strengths** 1. Identification of novel XO inhibitory peptides from an understudied source (sesame). 2. Multi-level characterization from in vitro kinetics to in vivo zebrafish model. 3. Computational evidence for a potentially novel binding site (FAD domain).

- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental validation of binding site
    - **Claim pointer** "Molecular docking against two XO crystal structures (3NVY, 3NRZ) consistently favored the FAD domain"
    - **Evidence pointer** Abstract only; no docking results, binding poses, or comparison with known inhibitors provided
    - **Concern** The claim of preferential FAD domain binding is based solely on computational docking and MD simulations. No experimental validation (e.g., site-directed mutagenesis, competitive binding assays with FAD, or XO variants lacking the FAD domain) is mentioned. The abstract does not specify whether the docking was performed on the full XO structure or isolated domains, nor whether the FAD domain is accessible in the native enzyme conformation.
    - **Why it matters** Without experimental confirmation, the FAD domain targeting claim remains speculative. Many computational docking studies report false positives, especially for allosteric or non-catalytic sites. This is the central mechanistic claim of the paper.
    - **Resolution test** Provide experimental evidence such as: (a) binding assays with XO variants lacking the FAD domain, (b) competition assays with FAD or FAD-binding inhibitors, (c) spectroscopic evidence of peptide-FAD interaction, or (d) at minimum, a rigorous comparison of docking scores against known FAD-binding and molybdenum-binding inhibitors.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** In vivo model rigor
    - **Claim pointer** "In a zebrafish hyperuricemia model, TSH reduced uric acid and XO activity while upregulating purine salvage (hprt1) and urate transport (oat1) genes"
    - **Evidence pointer** Abstract only; no details on model induction, dosing, sample size, statistical analysis, or controls
    - **Concern** The abstract reports in vivo efficacy for the crude hydrolyzate (TSH), not the purified peptides. The gene expression data (hprt1, oat1) suggest additional mechanisms beyond XO inhibition, but the abstract provides no information on: (a) how hyperuricemia was induced, (b) dose-response relationships, (c) whether the peptides themselves were tested in vivo, (d) sample size and statistical power, (e) whether the observed effects are specific to the identified peptides or due to other components in TSH.
    - **Why it matters** The title and claims focus on specific peptides, but the in vivo validation uses a complex mixture. Without testing the purified peptides, the causal link between the identified peptides and the observed effects is not established. The gene expression changes also complicate the mechanism.
    - **Resolution test** Test the purified peptides individually or in combination in the zebrafish model, or provide clear evidence that the observed effects are attributable to the identified peptides (e.g., by comparing TSH with a peptide-depleted fraction).

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Peptide identification and purity
    - **Claim pointer** "Eight 11S globulin peptides were identified by nanoUHPLC-ESI-Q-TOF MS/MS"
    - **Evidence pointer** Abstract only; no MS/MS spectra, sequence coverage, or purity data
    - **Concern** The abstract does not specify whether the identified peptides were synthesized or isolated from the hydrolyzate. If synthesized, the purity and characterization (e.g., HPLC, MS) are not mentioned. If isolated from TSH, the purification strategy and yield are absent. The IC50 values (467.2 and 536.1 µM) are relatively high compared to known XO inhibitors (e.g., allopurinol IC50 ~1-10 µM), raising questions about physiological relevance.
    - **Why it matters** Without confirmation of peptide identity and purity, the reported IC50 values and kinetic data cannot be properly evaluated. High IC50 values also question the practical utility as functional food candidates.
    - **Resolution test** Provide MS/MS spectra for peptide identification, HPLC purity data for synthetic peptides, and a discussion of the IC50 values in the context of known food-derived XO inhibitors.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** IC50 values
    - **Evidence pointer** Abstract
    - **Issue** The IC50 values are reported as 467.2 and 536.1 µM with four significant figures, which implies an unrealistic precision given typical experimental variability in enzyme inhibition assays.
    - **Required correction** Round IC50 values to two or three significant figures (e.g., 467 and 536 µM, or 470 and 540 µM) and report standard deviations or confidence intervals.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Mechanistic interpretation
    - **Affected element** Mixed-type inhibition (α > 1)
    - **Evidence pointer** Abstract
    - **Issue** The abstract states "mixed-type inhibition (α > 1)" but does not explain what α represents or how it was determined. For readers unfamiliar with enzyme kinetics, this is unclear.
    - **Required correction** Briefly define α (the factor by which the inhibitor changes the Michaelis constant) and state whether the inhibition is competitive, uncompetitive, or noncompetitive in nature.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** "Preferential association with the XO FAD domain"
    - **Evidence pointer** Abstract
    - **Issue** The term "preferential association" is vague. Does it mean preferential over the molybdenum or other domains? Or preferential over other peptides?
    - **Required correction** Clarify the comparator: "preferential association with the FAD domain over the molybdenum-pterin domain" or similar.

- **Technical failings that need to be addressed before the case is established** R1-M1 (FAD domain validation), R1-M2 (in vivo peptide testing), R1-M3 (peptide identification and purity)

- **Assessment against Nature-style criteria**
    - **Originality**: Moderate. Food-derived XO inhibitors are well-studied, but FAD-domain targeting is a relatively novel concept. However, the abstract does not demonstrate that this mechanism is unique to these peptides.
    - **Scientific importance**: Moderate. If validated, the FAD-domain targeting mechanism could open new avenues for XO inhibitor design. However, the high IC50 values and lack of in vivo peptide data limit the immediate impact.
    - **Interdisciplinary readership**: Limited. The work is primarily of interest to food chemistry and nutraceutical researchers. The mechanistic claims are not sufficiently developed to attract structural biologists or pharmacologists.
    - **Technical soundness**: Cannot be assessed from the abstract alone. Critical experimental details are missing.
    - **Readability for nonspecialists**: Adequate for an abstract, though some kinetic terms (α, mixed-type inhibition) could be better explained.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis but lacks the experimental validation required to support the central claims of FAD-domain targeting and in vivo efficacy of the specific peptides. A full manuscript with detailed methods, controls, and experimental validation of the binding site is needed for proper evaluation.