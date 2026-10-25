## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific soundness, methodological rigor, validity of conclusions relative to evidence presented, and suitability for the stated venue
- **Shared manuscript claim summary** The authors use OneOPES enhanced-sampling molecular dynamics to characterize the energetics of the up-to-down conformational transition in TREK-2 potassium channels, proposing a shared energetic axis coupling lower helices, proximal C-terminus, and selectivity filter. They validate predicted effects of a disease-mimicking mutation (A314P) using electrophysiology with a conformation-sensitive inhibitor.
- **Visible evidence base** Computational free-energy surfaces (1D and 2D), structural analyses, and electrophysiological recordings (TEVC and inside-out patch-clamp) from Xenopus oocytes
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; no methodological details for the norfluoxetine dose-response curve fitting beyond the Hill equation; no raw trajectory data or convergence metrics beyond those described; no information on how the path CV was validated against unbiased simulations

## Reviewer

### Overall assessment
This manuscript presents a computationally intensive study aimed at establishing an energetic framework for TREK-2 channel regulation, linking conformational changes in the lower helices and proximal C-terminus to selectivity filter dynamics. The use of OneOPES to quantify free-energy differences between up- and down-states under different conditions is a reasonable and potentially valuable approach. The electrophysiological validation using norfluoxetine as a state-dependent inhibitor is a thoughtful experimental design. However, several concerns limit the strength of the conclusions as currently presented. The manuscript would benefit from clearer presentation of convergence criteria, more direct evidence linking the simulated free-energy differences to functional outcomes, and a more cautious interpretation of the selectivity filter dynamics given acknowledged limitations in sampling.

### Who would be interested in the results, and why
Researchers in the ion channel biophysics community, particularly those studying two-pore domain potassium channels, mechanosensitive channels, and polymodal regulation. The methodological community interested in enhanced-sampling techniques applied to membrane proteins would also find value. The potential link to disease mechanisms (FHEIG syndrome) broadens relevance to translational researchers studying channelopathies.

### Major Strengths
- The application of OneOPES to a large, complex membrane protein system is technically ambitious and represents a methodological advance for the field
- The combination of computational predictions with electrophysiological validation using a state-dependent inhibitor is a strong experimental design
- The acknowledgment of limitations (e.g., inability to resolve full SF gating, variability across runs) is commendable and indicates scientific honesty
- The proposed framework of a shared energetic axis is conceptually appealing and could stimulate further research

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the free-energy landscapes obtained from OneOPES provide a quantitative framework for understanding how phosphorylation, membrane stretch, and mutation modulate TREK-2 gating.
- **Evidence pointer** Results section "The global conformational transition of TREK-2 is driven by the coordinated motion of M4-pCt"; Figures 2b–d, 5d; Supplementary Table 3
- **Concern** The convergence of the OneOPES simulations is not adequately demonstrated. The authors report run-to-run variability but do not provide quantitative convergence metrics (e.g., free-energy difference estimates as a function of simulation time, overlap between replica ensembles, or comparison of independent runs beyond standard deviation envelopes). Given that the central claims rest on free-energy differences between conditions (e.g., ΔΔG values of 31.8 and −23.0 kJ/mol), the reader needs stronger evidence that these differences are converged and not artifacts of insufficient sampling. The authors state that formal significance tests were not applied, which is acceptable, but the separation relative to propagated error (|ΔΔG|/σ) should be reported explicitly for all comparisons.
- **Why it matters** Without demonstrated convergence, the quantitative free-energy differences that form the core of the manuscript's claims cannot be reliably interpreted. The conclusions about condition-dependent shifts in conformational equilibria depend entirely on the accuracy of these numbers.
- **Resolution test** Provide convergence plots showing free-energy estimates as a function of simulation time for each system, report the |ΔΔG|/σ values for all pairwise condition comparisons, and show that the qualitative conclusions are robust to the choice of analysis window (e.g., comparing the first and second halves of the trajectories).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Claim substantiation
- **Claim pointer** The manuscript states that "the free-energy landscapes obtained from OneOPES... establish an energetic framework for TREK-2 regulation and dysfunction" and that the A314P mutation "shifts the equilibrium strongly toward the up-state."
- **Evidence pointer** Results section "Disease-mimicking mutation reshapes the TREK-2* energy landscape toward a conductive state"; Figures 5d–f; Supplementary Figure 7
- **Concern** The link between the simulated up-state stabilization in A314P and the experimentally observed increase in current is indirect. The authors show that A314P increases current ~9-fold and that the mutation stabilizes the up-state in simulations, but the causal chain connecting these observations is not established. Specifically, the manuscript does not demonstrate that the up-state is more conductive than the down-state in the same simulation framework, nor does it rule out alternative mechanisms for increased current (e.g., changes in single-channel conductance, open probability, or surface expression). The norfluoxetine shift in IC50 is consistent with a conformational shift but could also be explained by altered drug binding affinity independent of the up/down equilibrium.
- **Why it matters** The manuscript's central claim is that a shared energetic axis couples lower helices, pCT, and SF to govern gating. The A314P data are presented as key supporting evidence, but the connection between simulated conformational preferences and functional outcomes is not rigorously established.
- **Resolution test** Perform additional simulations or analyses that directly compare ion conduction in up- vs. down-state conformations (e.g., using the same force field and system setup), or provide experimental data (e.g., single-channel recordings) that link the conformational shift to conductance changes. Alternatively, temper the claims to reflect that the simulations predict a conformational shift that is consistent with, but does not prove, the functional mechanism.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript acknowledges that "the energetic description of the Y175 deviates from our previous unbiased simulations" and attributes this to missing CVs.
- **Evidence pointer** Results section "Energetic coupling between the pCT and SF defines the thermodynamic basis of TREK-2* gating"; Supplementary Figure 6
- **Concern** The authors acknowledge that Y175 dynamics were not adequately sampled, yet Y175 is described as an important component of the selectivity filter. This limitation is disclosed, which is good, but it raises questions about the completeness of the proposed energetic framework. If a key SF residue's dynamics are not reliably characterized, can the authors confidently claim a "shared energetic axis" that includes the SF? The manuscript would be strengthened by a more explicit discussion of how this limitation affects the overall conclusions.
- **Why it matters** The proposed framework's generality depends on the reliability of the SF characterization. An acknowledged sampling failure for one of the two key SF residues weakens the claim that the framework captures the essential coupling.
- **Resolution test** Either improve sampling of Y175 dynamics (e.g., by adding CVs that capture the M4 loop/EC loop interactions identified in prior work) or explicitly state that the framework's conclusions regarding SF coupling are based primarily on F284 dynamics, with Y175 requiring future investigation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 2a
- **Evidence pointer** Figure 2a
- **Issue** The representation of the path CV preparation is difficult to interpret. The salmon-colored regions are described as "highly flexible regions that are affecting the RMSD changes," but it is unclear which specific residues or structural elements these correspond to, and how they were selected.
- **Required correction** Provide a clearer figure legend or annotation identifying the specific residues/regions excluded from alignment, and briefly justify why these were chosen based on the crystal structures and prior simulations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "OneOPES simulations"
- **Evidence pointer** Methods section "OneOPES simulations"
- **Issue** The description of the replica-exchange setup is somewhat unclear. The authors state that "Replica 0 acted as the convergence monitor, while the remaining seven replicas (1–7) were used to enhance exploration," but then describe that replicas 1–6 biased auxiliary CVs and the eighth replica implemented multi-thermal expansion. This is confusing: are there 8 replicas total (0–7) or 9 (0–8)?
- **Required correction** Clarify the total number of replicas and the specific role of each replica in the setup.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph on Y175
- **Issue** The discussion of Y175 limitations is somewhat buried in the broader discussion of methodology. Given that this is a significant limitation, it deserves more prominent placement and a clearer statement of its implications.
- **Required correction** Move the Y175 limitation discussion to a more prominent position, perhaps in the Results section where Y175 data are first presented, and explicitly state what conclusions can and cannot be drawn from the Y175 data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "MD-based system preparation"
- **Evidence pointer** Methods section "MD-based system preparation"
- **Issue** The manuscript states that the pCT region was "manually extended using the PyMOL builder tool" and that this choice is "supported by AlphaFold3 predictions." However, no details are provided on how the AlphaFold3 prediction was used, or whether the manually built structure was compared to the AlphaFold3 prediction to ensure consistency.
- **Required correction** Provide a brief description of how the AlphaFold3 prediction was used to validate the manually built pCT structure, or state that the manual build was based on the AlphaFold3 prediction directly.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 5
- **Evidence pointer** Figure 5b, c, g–i
- **Issue** The electrophysiology data presentation is somewhat dense. The figure combines TEVC current measurements, NFX dose-response curves, and time courses in a single panel, which may be overwhelming for readers.
- **Required correction** Consider splitting the electrophysiology data into separate panels or sub-panels with clearer labels, and ensure that the statistical details (n numbers, error bars) are clearly visible and described in the legend.

### Technical failings that need to be addressed before the case is established
- R1-M1: Convergence of free-energy estimates not adequately demonstrated
- R1-M2: Causal link between simulated conformational shift and functional outcome not established
- R1-M3: Incomplete sampling of Y175 dynamics limits the generality of the proposed framework

### Assessment against Nature-style criteria

**Originality:** The application of OneOPES to a K2P channel system is novel and represents a methodological contribution. The concept of a shared energetic axis coupling lower helices, pCT, and SF is an interesting hypothesis. However, the underlying idea that these regions are coupled is not entirely new, and the manuscript builds substantially on the authors' prior work.

**Scientific importance:** The manuscript addresses a significant question in ion channel biology: how polymodal regulation converges on a common gating mechanism. If the claims are fully substantiated, the work could have broad implications for understanding K2P channel regulation and disease mechanisms. However, the current evidence does not fully establish the framework.

**Interdisciplinary readership:** The work bridges computational biophysics, electrophysiology, and structural biology. The findings would be of interest to researchers in all three communities, though the technical nature of the methods may limit accessibility to a broader audience.

**Technical soundness:** The computational methodology is state-of-the-art, but convergence concerns and acknowledged sampling limitations weaken the quantitative claims. The electrophysiology is well-executed but the connection to the computational predictions is indirect.

**Readability for nonspecialists:** The manuscript is generally well-written but assumes significant background knowledge in both MD simulation techniques and ion channel electrophysiology. The abstract is accessible, but the results and discussion sections may be challenging for readers outside these specialties.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a potentially valuable framework and a novel methodological application, but the convergence of the free-energy calculations must be demonstrated more rigorously, and the link between simulated conformational preferences and functional outcomes needs to be strengthened or the claims appropriately tempered. The acknowledged limitations in Y175 sampling should be addressed more directly in the presentation of the framework's scope.