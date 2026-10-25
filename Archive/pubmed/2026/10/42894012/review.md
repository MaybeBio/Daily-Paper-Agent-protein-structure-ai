## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table legends as provided.
- **Assessment boundary** Scientific content, technical soundness, interpretation of results, and alignment with claims made in the abstract and main text. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors report the 3.6 Å crystal structure of MmCadA, a PIB-2-type Zn2+/Cd2+/Pb2+ transporting P-type ATPase from Mesorhizobium metallurans, in an inward-open E1-like state. They propose a Zn2+ uptake pathway involving a negatively charged surface cavity that directly exposes the conserved CPC motif to the intracellular milieu. Through biochemical assays on N-terminal deletion and point mutants, they propose that the N-terminus, particularly histidine-rich segments, plays autoinhibitory and metal-delivery roles. Molecular dynamics simulations on an AlphaFold model are used to support a model of autoinhibition.
- **Visible evidence base** Main text figures 1–5; supplementary figures 1–15; supplementary tables 1–5; methods section.
- **Missing materials affecting confidence** Electron density maps and validation statistics (e.g., PDB validation report, map-to-model correlation) are not provided in the manuscript text. Coordinates and structure factors are not accessible. Raw data for ATPase activity assays (e.g., dose-response curves, replicates beyond summary statistics) are not shown. MD simulation convergence metrics and replica exchange acceptance ratios are not fully reported. The AlphaFold model identifier is given, but the specific model version and confidence metrics beyond pLDDT are not detailed.

## Reviewer
- **Overall assessment** This manuscript presents a valuable new structure of a PIB-2-type ATPase in an E1-like state, which has been lacking in the field. The structural analysis is generally careful, and the comparison to PIB-1 and PII ATPases is informative. The biochemical data on N-terminal truncations are interesting but are limited by the use of a single protein preparation for all functional measurements, and the interpretation of the autoinhibitory mechanism would be strengthened by direct binding or conformational data. The MD simulations are used in a somewhat qualitative manner and do not yet provide a mechanistic test of the proposed autoinhibition model. Overall, the work is of interest to the membrane transporter and metal homeostasis communities, but several technical concerns need to be addressed before the conclusions are fully supported.
- **Who would be interested in the results, and why** Researchers studying P-type ATPases, transition metal homeostasis, membrane protein structure and function, and those interested in the molecular basis of metal selectivity and regulation. The proposed regulatory model involving histidine-rich segments may also be of interest to the broader field of metal-sensing proteins and to biotechnologists working on phytoremediation or metal resistance engineering.
- **Major strengths** 1. First structure of a PIB-2 ATPase in an inward-open E1 state, filling a clear gap in the field. 2. Clear identification of a negatively charged uptake cavity that directly exposes the CPC motif, providing a concrete structural basis for metal entry. 3. The combination of structure, biochemistry, and MD simulations is appropriate for the questions asked. 4. The discussion of the N-terminal regulatory model is thoughtful and places the findings in a broader context of PIB-ATPase diversity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of functional data
  - **Claim pointer** The manuscript states that "all subsequent functional data" were obtained from "three independent technical measurements from a single protein purification" and uses these data to support conclusions about Vmax, Km, and metal selectivity of wild-type and mutant constructs.
  - **Evidence pointer** Results section "Metal specificity"; Figure 1B; Figure 4B, C; Methods "Functional characterization"
  - **Concern** All ATPase activity measurements, including those for the deletion and point mutants, are derived from a single protein purification. This is a critical limitation because batch-to-batch variation in membrane protein preparations can be substantial, and the reported differences between constructs (e.g., 2–5-fold changes in activity) may be within the range of preparation-to-preparation variability. Without independent biological replicates (i.e., at least two or three separate purifications), the quantitative comparisons between wild-type and mutants are not statistically robust.
  - **Why it matters** The central functional conclusion of the paper, that the N-terminus autoinhibits the ATPase and that His-1 facilitates metal delivery, rests on these activity measurements. If the observed differences are not reproducible across preparations, the proposed regulatory model is not supported.
  - **Resolution test** Provide ATPase activity data from at least three independent protein purifications for wild-type and key mutants (e.g., ∆MBD-2-His-2, ∆MBD-2-His-2-MBD-1-His-1, C17A/C20A, C168A/C171A). Report individual data points and perform appropriate statistical tests (e.g., one-way ANOVA with post-hoc comparisons). If this is not feasible, the claims should be softened to reflect the preliminary nature of the functional data.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Structural validation and interpretation
  - **Claim pointer** The manuscript claims a 3.6 Å structure of MmCadA in an inward-open E1 state, with specific statements about the conformation of the CPC motif, the position of the A-domain, and the absence of bound metal.
  - **Evidence pointer** Results "Structure determination and overall structure"; Figure 1C–E; Supplementary Figures 6–8; Supplementary Table 1
  - **Concern** The manuscript does not provide electron density maps or validation metrics (e.g., map-to-model correlation, B-factor distributions, Ramachandran statistics) in the main text or supplementary material. At 3.6 Å resolution, the interpretation of side-chain conformations, particularly for the CPC motif and the proposed metal-coordinating residues, is challenging. The authors state that no metal is bound, but it is unclear whether the absence of density for a metal ion is conclusive at this resolution, especially if the ion is weakly bound or partially occupied. Additionally, the Rfree/Rwork values (31.5/27.7) are relatively high, which may indicate overfitting or model bias.
  - **Why it matters** The structural model is the foundation of the paper. If the map quality does not support the specific conformational claims (e.g., the exposure of C564, the position of the A-domain), the proposed uptake mechanism is weakened. The high Rfree also raises questions about the reliability of the model.
  - **Resolution test** Provide representative electron density maps (e.g., 2Fo-Fc and Fo-Fc) for the CPC motif, the proposed uptake cavity, and the A-domain. Report validation statistics (e.g., MolProbity score, clash score, Ramachandran outliers, map CC values). If the Rfree cannot be improved, discuss the limitations and how the model was validated against overfitting.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Support for the autoinhibition model
  - **Claim pointer** The manuscript proposes that the N-terminal region, particularly MBD-2 and His-2, autoinhibits the ATPase by constraining the cytosolic domains, and that His-1 acts as a metal sensor that relieves this inhibition.
  - **Evidence pointer** Results "An N-terminus with multifaceted roles" and "A structural model for the autoinhibition"; Figure 4; Supplementary Figures 13–14
  - **Concern** The autoinhibition model is based on (i) activity differences between truncation mutants and (ii) an AlphaFold model with MD simulations. The MD simulations are used to show that the N-terminus contacts the A- and P-domains, but the simulations are short (3 x 500 ns) and the replica exchange temperature range is very narrow (303.15–303.25 K), which is unlikely to provide meaningful enhanced sampling. The contact analysis is descriptive and does not demonstrate that these contacts are functionally relevant. The double cysteine crosslinking experiments are suggestive but are only shown as a single western blot with no quantification or controls for crosslinking efficiency.
  - **Why it matters** The proposed regulatory mechanism is a major conclusion of the paper. If the MD simulations do not adequately sample the conformational space, and if the crosslinking data are not quantitative, the model remains speculative.
  - **Resolution test** Strengthen the MD analysis by reporting convergence metrics, replica exchange acceptance ratios, and a more detailed analysis of the contacts (e.g., contact lifetimes, free energy estimates). Provide quantitative crosslinking data (e.g., densitometry from multiple replicates) and include a control mutant that disrupts the proposed interface. Alternatively, test the model directly by measuring metal binding to the N-terminal domain or by performing activity assays under conditions that would be expected to relieve autoinhibition.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1B
  - **Evidence pointer** Results "Metal specificity"; Figure 1B
  - **Issue** The activity data in Figure 1B are presented as bar graphs with error bars, but the text states that these are from three technical replicates from a single purification. It would be helpful to show the individual data points and to clarify whether the error bars represent SD or SEM.
  - **Required correction** Show individual data points in Figure 1B and 4B, C, and specify the error bar definition in the figure legend.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness of methods
  - **Affected element** MD simulation methods
  - **Evidence pointer** Methods "Molecular dynamics simulations"; Supplementary Table 5
  - **Issue** The methods for MD simulations are described, but the force field parameters, water model, and the specific AlphaFold model version used are not stated. The replica exchange temperature spacing is very narrow and the rationale for this choice is not explained.
  - **Required correction** Specify the force field, water model, and AlphaFold version. Justify the narrow temperature range or use a wider range to improve sampling.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of in vivo data
  - **Affected element** Supplementary Figure 5
  - **Evidence pointer** Results "Metal specificity"; Supplementary Figure 5
  - **Issue** The in vivo metal challenge assays show that MmCadA protects against metal toxicity, but the data are only shown as growth curves at a single time point (OD600 at 5 h). It would be more informative to show full growth curves or to quantify the area under the curve.
  - **Required correction** Provide full growth curves or a more quantitative readout of cell viability.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion
  - **Issue** The authors acknowledge the low confidence in the His-1 and His-2 predictions, but the discussion would benefit from a more explicit statement of the limitations of the MD simulations and the functional assays.
  - **Required correction** Add a sentence in the Discussion acknowledging that the MD simulations are based on a model with low confidence in the N-terminal region and that the functional data are from a single preparation.

## Risk / unsupported claims
- The claim that the N-terminus "auto-inhibits" the ATPase is not fully supported by the data, as the activity differences between wild-type and truncation mutants are based on a single purification and the mechanism of inhibition is not directly demonstrated.
- The claim that His-1 "donates ions to the CPC site" is speculative and is not directly tested in this manuscript.
- The claim that the structure represents a "primed for metal-ion uptake" state is reasonable but is based on the absence of bound metal and the conformation of the CPC motif, which is not fully validated at 3.6 Å resolution.
- The functional significance of the observed dimer is not established, and the authors themselves note that the interface is not conserved. This is appropriately presented as speculative.
- The in vivo metal challenge data are consistent with MmCadA functioning as a metal exporter, but the data do not distinguish between Zn2+, Cd2+, and Pb2+ specificity in vivo.

## Assessment against Nature-style criteria
- **Originality** The structure of a PIB-2 ATPase in an E1 state is novel and addresses a clear gap in the field. The proposed uptake mechanism, involving a negatively charged cavity and direct exposure of the CPC motif, is a new contribution. The regulatory model for the N-terminus is also original, although it is not fully tested.
- **Scientific importance** The work is important for understanding how PIB-2 ATPases achieve metal selectivity and how they are regulated. The findings have implications for metal homeostasis in bacteria and plants, and potentially for engineering metal tolerance. The importance is moderate to high, but the impact would be greater if the regulatory model were more strongly supported.
- **Interdisciplinary readership** The work will appeal to structural biologists, membrane protein biochemists, and researchers in metal homeostasis. The broader implications for biotechnology are mentioned but not developed, which may limit the interdisciplinary reach.
- **Technical soundness** The structural determination appears to be technically sound, but the lack of validation metrics and the relatively high Rfree are concerns. The functional assays are limited by the single-preparation issue. The MD simulations are not sufficiently rigorous to support the mechanistic claims.
- **Readability for nonspecialists** The manuscript is generally well-written and the figures are clear. The introduction and discussion are accessible. However, the results section is dense and may be challenging for readers not familiar with P-type ATPase nomenclature and the Post-Albers cycle.

## Recommendation posture
Supportive if technical concerns are resolved. The structural data are valuable and the manuscript addresses an important question. However, the functional conclusions are not fully supported by the current data, and the structural validation needs to be improved. If the authors can provide additional replicates for the activity assays, show electron density maps and validation statistics, and strengthen the MD analysis, the manuscript would be suitable for publication.