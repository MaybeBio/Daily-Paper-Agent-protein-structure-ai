## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Results, Discussion, Materials and methods, Data availability, Acknowledgements). Figures and figure supplements are referenced but not supplied as images.
- **Assessment boundary** Assessment is limited to the supplied text and the claims it makes. Figure panels, blots, micrographs, numerical source data, and supplementary files were not available for inspection, so quantitative and image-based claims cannot be independently verified.
- **Shared manuscript claim summary** The authors report that the human SVEP1 CCP20 domain is the primary binding site for TIE1; that SVEP1 does not bind TIE2 in the tested binary setups; that ANG1/ANG2 enhance SVEP1-TIE1 binding; that combined SVEP1 and ANG2 stimulation of hdLECs produces TIE1 phosphorylation at pY1007 and downstream PI3K/AKT signaling readouts (pAKT, FOXO1 nuclear exclusion); and that AlphaFold-based modeling predicts a higher-order 2:2:2 SVEP1-TIE1-ANG1/2 assembly that could cluster TIE1 receptors.
- **Visible evidence base** SPR binding data (Figure 1C), negative-stain EM (Figure 1D, Figure 2—figure supplement 3), AlphaFold2.3/AF3 multimer predictions with PAE, ipTM and actifpTM metrics (Figure 1A-B, Figure 1—figure supplements 1-2, Figure 2A, Figure 2—figure supplements 1-2, Figure 4A-C, Figure 4—figure supplement 1), ELISA binding assays (Figure 2B), co-immunoprecipitation (Figure 2C), TIE1 pY1007 phosphorylation (Figure 3A, D), pAKT with ANG2 blocking antibody and TIE1/TIE2 knockdown (Figure 3B, E), FOXO1 nuclear/cytoplasmic ratio (Figure 3C, F), and mutant binding assays (Figure 1—figure supplement 3A-B).
- **Missing materials affecting confidence** Figure images and their quantitative source data; uncropped blots; statistics for individual panels; detailed methods for AF3 job parameters and model selection; the key resources table referenced repeatedly; the GitHub analysis scripts and BioImage Archive dataset contents; the funding information body.

## Reviewer
- **Overall assessment** The manuscript addresses a genuinely open question in vascular biology, namely how the orphan receptor TIE1 is engaged and phosphorylated, and it proposes SVEP1 as a bridging co-ligand that enables ANG2 to act on TIE1. The combination of structure prediction, biophysical binding assays, and cell-based signaling readouts is appropriate for the question. However, the central mechanistic claim, that SVEP1 enables efficient ANG2 binding to TIE1 and thereby drives TIE1 phosphorylation and downstream signaling, rests on evidence that is currently only partially visible and, in several places, internally inconsistent. The most consequential issues are the reliance on AlphaFold predictions as a primary argument for complex geometry and stoichiometry, the unresolved role of TIE2 in the observed pAKT response, the absence of direct demonstration that ANG2 is present in the ternary complex after immunoprecipitation, and the fact that the higher-order assembly model is explicitly acknowledged as unconfirmed. As presented, the core conclusion is plausible but not yet established from the supplied material.
- **Who would be interested in the results, and why** Vascular and lymphatic biologists working on the ANG/TIE axis, TIE1 orphan-receptor biology, and lymphangiogenesis; structural biologists using AlphaFold-multimer for ternary and higher-order complex prediction; researchers in lymphedema, glaucoma, and lymphatic malformation genetics where SVEP1 and TIE1 variants have been implicated; and cell-signaling groups interested in how extracellular matrix proteins modulate receptor tyrosine kinase activation.
- **Major strengths** The question is well motivated and builds on prior genetic and biochemical work linking SVEP1 and TIE1. The authors combine orthogonal approaches, including SPR, ELISA, co-immunoprecipitation, negative-stain EM, phosphorylation assays, knockdown, and blocking antibodies, which is the right general strategy. The use of disease-relevant human dermal LECs rather than only immortalized lines is a strength. The manuscript is candid in places about the limits of its own model, for example the statement that further experimentation is needed to confirm the multimerization model, and the discussion of the historical difficulty in detecting TIE1 phosphorylation is informative. The mutant binding experiments (SVEP1 E2568A-G2569A and TIE1 P202L-L203F) provide a useful specificity control for the proposed interface.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for the central mechanistic claim
- **Claim pointer** SVEP1 mediates strong binding of ANG2 and TIE1, and combined SVEP1 and ANG2 stimulation leads to TIE1 phosphorylation and downstream signaling.
- **Evidence pointer** Figure 2C, Figure 3A, Figure 3D, Figure 3B, Figure 3E
- **Concern** The co-immunoprecipitation experiment intended to show ternary complex formation does not detect ANG1 or ANG2 after immunoprecipitation, and the authors state this explicitly. The claim that ANG2 is a component of the SVEP1-TIE1 complex therefore rests on an increase in co-precipitated TIE1 rather than on direct detection of the angiopoietin in the complex. In addition, the reported decrease of ANG1 and ANG2 levels in total lysate after co-transfection is not explained and could indicate altered expression, secretion, or degradation rather than complex assembly.
- **Why it matters** The bridging model is the central novelty of the manuscript. If ANG2 cannot be shown to be physically present in the SVEP1-TIE1 complex, the interpretation that SVEP1 enables ANG2 binding to TIE1 is inferential rather than demonstrated.
- **Resolution test** Provide direct detection of ANG1/ANG2 in the SVEP1 pull-down, for example by tagged angiopoietin immunoblot, mass spectrometry, or a proximity-based assay, with controls for nonspecific binding and for the observed lysate-level decrease.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Attribution of the signaling response
- **Claim pointer** TIE1 activation by SVEP1 and ANG2 enables downstream signaling, and knockdown of either TIE1 or TIE2 reduces pAKT after SVEP1-ANG2 stimulation.
- **Evidence pointer** Figure 3B, Figure 3E
- **Concern** The pAKT response requires both TIE1 and TIE2 according to the knockdown data, yet the manuscript simultaneously argues that SVEP1 does not bind TIE2 and that TIE2 is not part of the proposed complex. The authors acknowledge that whether TIE2 is necessary for TIE1 phosphorylation after SVEP1-ANG2 treatment needs further investigation. This leaves the receptor composition of the signaling unit unresolved and creates tension with the model figure.
- **Why it matters** If TIE2 is required for the pAKT readout, then the claim that SVEP1-ANG2 acts through a TIE1-centered signaling hub is not separable from a TIE1-TIE2 heteromeric mechanism, which is the pre-existing paradigm the manuscript seeks to revise.
- **Resolution test** Determine whether TIE1 phosphorylation at pY1007 after SVEP1-ANG2 stimulation persists upon TIE2 knockdown or in TIE2-negative cells, and report pAKT and pTIE1 side by side under the same knockdown conditions with knockdown efficiency documented.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural inference versus experimental support
- **Claim pointer** AF3 predicts a 2:2:2 SVEP1-TIE1-ANG1/2 complex in which TIE1 dimerizes and ANG1/2 cross-links SVEP1 molecules, clustering TIE1 receptors.
- **Evidence pointer** Figure 4A, Figure 4B, Figure 4C, Figure 4—figure supplement 1
- **Concern** The higher-order assembly is derived entirely from prediction, and the authors state that further experimentation is needed to confirm it. The manuscript also notes that a previously reported crystallographic TIE1 Fn3 dimer was concluded to be a crystal artifact based on SAXS. The predicted TIE1 dimerization interface therefore contradicts the available solution evidence and is not experimentally tested here.
- **Why it matters** The multimerization model is presented in the abstract and discussion as a mechanistic explanation for signal amplification. Without experimental support, it functions as a hypothesis rather than a result, and the abstract wording does not fully convey this status.
- **Resolution test** Provide independent biophysical or cellular evidence for TIE1 oligomerization in the presence of SVEP1 and ANG1/2, for example size-exclusion chromatography with multi-angle light scattering, analytical ultracentrifugation, cross-linking, or single-molecule imaging, and reconcile the result with the prior SAXS finding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of the SVEP1-TIE1 versus SVEP1-TIE2 distinction
- **Claim pointer** SVEP1 binds TIE1 but not TIE2 in the absence of other proteins, and CCP20 is the primary binding site for TIE1.
- **Evidence pointer** Figure 1A, Figure 1B, Figure 1C, Figure 1—figure supplement 1, Figure 1—figure supplement 3A
- **Concern** The SPR and ELISA experiments use a truncated SVEP1 construct spanning CCP15 to CCP24 rather than full-length protein, and the manuscript acknowledges that only part of the C-terminus was used. The negative result for TIE2 is therefore restricted to this fragment and to binary conditions. The AF2.3 interface metrics for TIE2 are described as weaker but the model still yields a comparable buried surface area, which weakens the qualitative claim of no binding.
- **Why it matters** The selectivity of SVEP1 for TIE1 over TIE2 is a load-bearing element of the model. A fragment-based negative result cannot exclude TIE2 engagement by other SVEP1 regions or in the presence of angiopoietins, a possibility the authors themselves raise in the discussion.
- **Resolution test** Report full-length or additional SVEP1 domain constructs in binding assays with TIE2, include quantitative affinity estimates with confidence intervals for both receptors, and state explicitly the detection limit of the assay for the TIE2 negative result.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative reporting and statistical support
- **Claim pointer** The affinity of TIE1 for SVEP1 is significantly increased by ANG1 or ANG2, and combined stimulation produces stronger pAKT and FOXO1 nuclear exclusion than either factor alone.
- **Evidence pointer** Figure 2B, Figure 3A, Figure 3B, Figure 3C, Figure 3D, Figure 3E, Figure 3F
- **Concern** KD values are reported in the text with inconsistent decimal formatting and without units, confidence intervals, or replicate counts. The claim that the combined effect exceeds the sum of individual effects is stated in the discussion but the statistical test supporting an interaction or synergy term is not described. The statistics section describes t-tests, Mann-Whitney U, and Bonferroni correction but does not specify which comparisons used which test or how synergy was assessed.
- **Why it matters** The potentiation claim is central to the interpretation of cooperative signaling. Without an explicit interaction test, an additive effect cannot be distinguished from a synergistic one.
- **Resolution test** Report KD values with units, confidence intervals, and n; specify the statistical model used to test for interaction or synergy between SVEP1 and ANG2 for pAKT and FOXO1 readouts; and provide the underlying quantitative data for each panel.

- **Major Concerns** (continued)

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility of the phosphorylation readout
- **Claim pointer** Stimulation of hdLECs with both SVEP1 and ANG2 produces robust phosphorylation of TIE1 at pY1007.
- **Evidence pointer** Figure 3A, Figure 3D
- **Concern** The manuscript notes that SVEP1 alone has a slight effect on TIE1 phosphorylation, attributed to endogenous ANG2 expression in hdLECs. This raises the possibility that the observed phosphorylation depends on endogenous ligand levels that are not controlled or measured. The prior literature cited by the authors reports that TIE1 phosphorylation was not detectable with SVEP1 or ANG2 alone, which makes the baseline and the magnitude of the combined effect important to document.
- **Why it matters** If endogenous ANG2 contributes materially, the interpretation of the SVEP1-ANG2 combination as the specific activating condition is weakened, and reproducibility across LEC batches becomes a concern.
- **Resolution test** Measure and report endogenous ANG2 and ANG1 levels in the hdLECs used, include an ANG2 depletion or blocking condition for the pY1007 readout, and show the full time course and dose response with replicate quantification.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology and consistency
- **Affected element** Receptor nomenclature throughout the manuscript
- **Evidence pointer** Introduction, Results, Discussion
- **Issue** The manuscript alternates between TIE1/TIE2 and Tie1/Tie2, and between SVEP1 and Svep1, without a stated convention for species or context.
- **Required correction** Adopt a single convention, for example human uppercase and nonhuman title case, and apply it consistently.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Numerical reporting
- **Affected element** KD values in the Results
- **Evidence pointer** Results, section on ANG1/2 strengthening binding
- **Issue** KD values are written with commas as decimal separators and without units, for example KD = 146,9 and KD = 55,6.
- **Required correction** Use decimal points and state units, for example nM, consistently.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Cross-references to supplementary panels
- **Evidence pointer** Results, multiple sections
- **Issue** Several claims are supported only by references to figure supplements, and the main-text description does not always state what the supplementary panel shows or how many replicates it contains.
- **Required correction** Briefly state the assay and replicate number in the main text for each supplementary-supported claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methods completeness
- **Affected element** AlphaFold modeling parameters
- **Evidence pointer** Materials and methods, structure prediction section
- **Issue** The AF3 job parameters, model ranking criteria, and the basis for accepting the 2:2:2 stoichiometry are not fully specified, and the key resources table referenced for sequences is not included in the supplied text.
- **Required correction** Provide the full AF3 configuration, the number of seeds and samples, the ranking metric used, and the sequence boundaries for each chain.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Analysis scripts and imaging data
- **Evidence pointer** Data availability statement
- **Issue** The statement points to a GitHub repository and a BioImage Archive accession, but the relationship between these resources and the specific figure panels is not described.
- **Required correction** Map each deposited dataset and script to the figure panels it supports.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Description of TIE2 in the model
- **Evidence pointer** Results, section on higher-order complexes, and Discussion
- **Issue** The Results state that TIE2 was not predicted to co-bind stably, while the Discussion states that whether TIE2 can bind SVEP1 in the presence of angiopoietins remains an open question. The two statements are compatible but the framing shifts between sections.
- **Required correction** Align the wording so that the negative prediction and the acknowledged open question are presented consistently.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. These concern direct detection of angiopoietin in the complex, the unresolved requirement for TIE2 in the signaling readout, and the experimental status of the higher-order assembly model. R1-M4, R1-M5, and R1-M6 are important but not by themselves blocking.

- **Assessment against Nature-style criteria** Originality is moderate to high, since the proposal that an extracellular matrix protein acts as a bridging co-ligand for an orphan receptor tyrosine kinase is a distinct mechanistic idea, although it builds directly on the authors' prior SVEP1-TIE1 work. Scientific importance is potentially high for lymphatic and vascular biology, particularly if the TIE2-independent component of TIE1 activation can be demonstrated. Interdisciplinary readership is plausible, spanning vascular biology, structural prediction, and matrix biology, but the current reliance on predicted structures limits appeal to readers outside the modeling community. Technical soundness is mixed, with a good range of orthogonal methods but with unresolved issues in complex composition, receptor attribution, and quantitative reporting. Readability for nonspecialists is reasonable in the Introduction and Discussion, but the Results assume familiarity with AlphaFold metrics such as PAE, ipTM, and actifpTM without defining them, which will limit accessibility.

- **Recommendation posture** Currently not established from the provided evidence. The work is potentially supportive if the technical concerns, in particular R1-M1, R1-M2, and R1-M3, are resolved with direct experimental evidence.

## Risk / unsupported claims
- The claim that ANG2 is physically present in the SVEP1-TIE1 complex is not supported by the supplied evidence, since ANG1 and ANG2 were not detected after immunoprecipitation (Figure 2C).
- The claim that SVEP1-ANG2 signaling proceeds through a TIE1-centered mechanism is weakened by the reported requirement for TIE2 in the pAKT readout (Figure 3B, Figure 3E).
- The 2:2:2 higher-order assembly and TIE1 dimerization model is a prediction without experimental confirmation, and it conflicts with prior SAXS evidence cited by the authors indicating that the crystallographic TIE1 Fn3 dimer is likely an artifact (Figure 4A-C).
- The claim that SVEP1 does not bind TIE2 is supported only for the CCP15-CCP24 fragment under binary conditions and cannot be generalized to full-length SVEP1 or to angiopoietin-containing conditions (Figure 1C).
- The claim that combined SVEP1 and ANG2 stimulation exceeds the sum of individual effects is stated in the Discussion but the supporting statistical test for interaction or synergy is not described in the supplied text.
- The reported KD values lack units, confidence intervals, and replicate counts, so the magnitude of the affinity change upon ANG1 or ANG2 addition cannot be evaluated (Figure 2B).
- The contribution of endogenous ANG2 in hdLECs to the observed TIE1 phosphorylation is acknowledged but not quantified or controlled (Figure 3A, Figure 3D).