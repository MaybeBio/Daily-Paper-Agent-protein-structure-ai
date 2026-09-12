## Review setup
- **Input scope** Full manuscript (abstract only provided in this review request)
- **Assessment boundary** Abstract only
- **Shared manuscript claim summary** The authors identify a novel SXXLF motif in the N-terminal domain (NTD) of the farnesoid X receptor (FXR) that mediates interactions with coregulator proteins and the ligand-binding domain (LBD), and modulates FXR transcriptional activity through interdomain and allosteric coupling.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or results sections provided.
- **Missing materials affecting confidence** Full manuscript, including all figures, tables, experimental methods, statistical analyses, and supplementary data.

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting discovery of a novel SXXLF motif in the FXR NTD, which could have implications for understanding nuclear receptor regulation. However, the evidence base is limited to the abstract, and several key claims cannot be evaluated without access to the full data. The novelty of the motif and the mechanistic details of its function require rigorous validation that is not visible here.

- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, structural biology, and transcriptional regulation would be interested, as the study proposes a new conserved motif that may expand the known repertoire of NR-interacting sequences and could inform drug design targeting FXR.

- **Major strengths** 
  - The identification of a novel SXXLF motif in the FXR NTD is potentially original and could fill a gap in understanding NTD function in this receptor.
  - The use of multiple complementary approaches (mutagenesis, mammalian two-hybrid, mammalian one-hybrid, MD simulations) suggests a robust experimental design.

- **Major Concerns**
  - **Concern ID** R1-M1
    **Severity** Major
    **Blocking** Yes
    **Axis** Evidence sufficiency
    **Claim pointer** "We show that the NTD engages in interdomain contact with other FXR domains. We also observe that the NTD interacts directly with coregulator proteins."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract states these interactions are observed but provides no quantitative data, controls, or experimental details (e.g., which coregulators, which domains, binding affinities). Without these, the claim is unsubstantiated.
    **Why it matters** The core premise of the study—that the NTD mediates these interactions—must be convincingly demonstrated before the motif's role can be assessed.
    **Resolution test** Provide specific experimental data (e.g., pull-down, co-IP, or SPR results) with appropriate controls and statistical measures.

  - **Concern ID** R1-M2
    **Severity** Major
    **Blocking** Yes
    **Axis** Claim validation
    **Claim pointer** "Using mutagenesis, mammalian two-hybrid assays, mammalian one-hybrid assay, and molecular dynamics (MD) simulations, we identify and validate a novel SXXLF motif in the NTD which mediates interactions with both coregulators and the ligand binding domain."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract does not specify which residues constitute the SXXLF motif, how it was identified (e.g., sequence alignment, structural prediction), or the magnitude of the effects of its mutation on interactions. The term "validate" is strong and requires clear statistical and functional evidence.
    **Why it matters** The novelty and central claim of the paper hinge on this motif. Without detailed evidence, the claim remains a hypothesis.
    **Resolution test** Provide sequence alignment showing conservation of the motif, mutagenesis data with effect sizes and p-values, and MD simulation results (e.g., RMSD, interaction energies) that support the functional role.

  - **Concern ID** R1-M3
    **Severity** Major
    **Blocking** Yes
    **Axis** Mechanistic interpretation
    **Claim pointer** "Mutation of the motif induces large changes in conformational and allosteric coupling in FXR."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract does not define "large changes" quantitatively or describe how allosteric coupling was measured. MD simulations can suggest allostery, but experimental validation (e.g., by FRET, HDX-MS, or functional assays) is needed.
    **Why it matters** Allosteric coupling is a complex claim that requires robust evidence to distinguish from direct binding effects.
    **Resolution test** Provide quantitative metrics (e.g., correlation coefficients, free energy changes) and experimental validation of allostery.

- **Minor Comments**
  - **Concern ID** R1-m1
    **Severity** Minor
    **Axis** Clarity
    **Affected element** Abstract text
    **Evidence pointer** Abstract; location not provided
    **Issue** The abstract states "few NTD functions are conserved between NRs" but then lists AR, ER, and MR as examples. It is unclear whether FXR NTD functions are expected to be similar or distinct.
    **Required correction** Clarify the relationship between FXR NTD and other NR NTDs, or state that the motif is novel and not previously described in other NRs.

  - **Concern ID** R1-m2
    **Severity** Minor
    **Axis** Terminology
    **Affected element** Abstract text
    **Evidence pointer** Abstract; location not provided
    **Issue** The term "SXXLF motif" is introduced without definition. Readers may not know that "X" denotes any amino acid.
    **Required correction** Define the motif explicitly (e.g., "Ser-X-X-Leu-Phe" where X is any residue) upon first use.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract lacks sufficient quantitative and mechanistic evidence to support the central claims of interdomain interaction, motif validation, and allosteric coupling.

- **Assessment against Nature-style criteria**
  - **Originality**: Potentially high, as a novel SXXLF motif in FXR NTD has not been reported. However, the abstract does not demonstrate that this motif is truly novel compared to known NR motifs (e.g., LXXLL, FXXLF).
  - **Scientific importance**: Moderate to high. If validated, the finding could advance understanding of NTD function in NRs, but the abstract does not establish broad significance beyond FXR.
  - **Interdisciplinary readership**: Limited. The topic is specialized for NR and structural biology communities; broader appeal is not evident from the abstract.
  - **Technical soundness**: Cannot be assessed from the abstract alone. The use of multiple methods is promising, but no data or controls are visible.
  - **Readability for nonspecialists**: The abstract is clear but assumes familiarity with NR terminology (e.g., AF-1, LBD, coregulator). A brief explanation of the SXXLF motif would help.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis, but the claims of interaction, motif validation, and allostery are unsupported without full data. A supportive posture would require resolution of the major concerns with detailed experimental evidence.

## Risk / unsupported claims
- The claim that the NTD engages in interdomain contact with other FXR domains is unsupported (no data provided).
- The claim that the NTD interacts directly with coregulator proteins is unsupported (no coregulator identity or binding data provided).
- The claim that the SXXLF motif is validated as mediating interactions is unsupported (no mutagenesis or assay results provided).
- The claim that mutation induces "large changes" in conformational and allosteric coupling is unsupported (no quantitative metrics or experimental validation provided).