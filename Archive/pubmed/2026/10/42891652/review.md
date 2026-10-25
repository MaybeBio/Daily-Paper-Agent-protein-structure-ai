## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supporting information references
- **Assessment boundary** Scientific validity of structural claims, methodological soundness of cryo-EM and MD simulation approaches, interpretation of results, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors report cryo-EM structures of the F1-ATPase from *Acinetobacter baumannii* captured during ATP synthesis, revealing conformational changes in the catalytic head, subunit ε transitions, and central stalk twisting. MD simulations are used to validate and extend these observations. The authors propose that these structural snapshots reveal novel therapeutic targets for drug-resistant *A. baumannii*.
- **Visible evidence base** Six cryo-EM conformers (C1a, C1b, C2a, C2b, C3a, C3b) with reported resolutions between 2.88 and 3.13 Å; targeted MD simulations for three transitions; ATP synthesis activity measurements; supporting figures and tables referenced but not fully visible
- **Missing materials affecting confidence** Supporting figures (S1-S14) and tables (S1A/B, S2) are referenced but not provided in the submitted text; supplementary movies are mentioned but not accessible; full validation statistics (Fourier shell correlation curves, map-model cross-correlation) are not included in the visible text

## Reviewer

### Overall assessment
This manuscript presents a substantial structural biology effort aimed at capturing catalytic intermediates of the *A. baumannii* F1-ATPase. The work addresses a clinically relevant pathogen and the structural data could be of interest to the ATP synthase and antimicrobial resistance communities. However, several technical concerns must be addressed before the central claims can be considered fully established. The interpretation of the cryo-EM states as catalytic intermediates along the ATP synthesis pathway requires stronger experimental support, particularly given the absence of the FO domain and the lack of a membrane potential. The MD simulations, while useful for exploring conformational space, are not sufficient to establish the mechanistic ordering of events proposed. The therapeutic targeting claims are speculative and would benefit from more direct evidence of druggability.

### Who would be interested in the results, and why
Structural biologists studying rotary ATPases, researchers investigating bacterial bioenergetics, and those working on antimicrobial resistance mechanisms would find this work relevant. The ε subunit conformational transitions are of particular interest to the ATP synthase field, as the regulatory mechanisms of this subunit remain incompletely understood across species. The potential therapeutic angle would interest medicinal chemists and drug discovery groups focused on *A. baumannii* infections, though the translational claims require further validation.

### Major strengths
1. The study addresses a clinically important pathogen with limited treatment options, and the structural characterization of its F1-ATPase fills a gap in the literature.
2. The capture of multiple conformational states, including the novel "initiation state" of εCTD transition, provides valuable structural information.
3. The combination of cryo-EM with targeted MD simulations is a reasonable approach to explore conformational transitions between discrete states.
4. The authors have deposited all structural data with clear accession identifiers, supporting transparency and reproducibility.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and interpretation
- **Claim pointer** The manuscript claims that the structures represent "ATP synthesizing AbF1-ATPase" captured "during ATP synthesis" and that the observed transitions are coupled with "spontaneous ATP formation."
- **Evidence pointer** Results section "Cryo-EM Approach to Resolve the AbF1-ATPase Incubated With MgADP and Pi"; Figure 1A
- **Concern** The F1-ATPase alone, without the FO domain and membrane potential, cannot perform physiologically relevant ATP synthesis. The authors acknowledge this limitation but still frame the structures as catalytic intermediates of ATP synthesis. The observed ATP formation in solution (Figure 1A) is a well-known phenomenon for isolated F1-ATPases under specific conditions, but the relevance of these states to the membrane-embedded, proton-motive-force-driven enzyme is not established. The nucleotide occupancy patterns differ between the reported states and previously published *A. baumannii* F-ATP synthase structures, yet the authors do not adequately discuss whether these differences reflect genuine catalytic intermediates or crystallization artifacts.
- **Why it matters** The central claim of the paper rests on the interpretation that these structures represent authentic ATP synthesis intermediates. If this interpretation is not rigorously supported, the mechanistic conclusions and the proposed therapeutic targeting strategy lose their foundation.
- **Resolution test** Provide additional experimental evidence that the observed states are catalytically relevant, such as time-resolved experiments, cross-linking studies to trap specific states, or mutagenesis of key residues predicted to be important for the transitions. Alternatively, temper the claims to describe the structures as conformational states observed in the presence of substrates without asserting their catalytic relevance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and validation
- **Claim pointer** The manuscript reports six cryo-EM structures at resolutions between 2.88 and 3.13 Å and uses these to make detailed claims about side-chain interactions, loop movements, and secondary structure transitions.
- **Evidence pointer** Results section; Table S1A/B (referenced but not visible); Figures S1-S3 (referenced but not visible)
- **Concern** The resolution range reported (2.88-3.13 Å) is modest for the detailed mechanistic claims made. At these resolutions, side-chain rotamer assignments and the identification of specific hydrogen bonds or salt bridges are often ambiguous. The authors do not provide sufficient validation metrics in the visible text, including Fourier shell correlation curves, map quality indicators, local resolution estimates, or model-to-map cross-correlation values. The distinction between the six conformers, particularly C1a versus C1b and C2a versus C2b, relies on relatively subtle structural differences that need to be supported by robust density features.
- **Why it matters** The mechanistic narrative depends on specific structural differences between states. If these differences are not confidently resolved, the proposed sequence of events and the identification of novel therapeutic targets are not reliable.
- **Resolution test** Provide full validation statistics for all six structures, including FSC curves, local resolution maps, and model-to-map correlation per residue. Show representative density for the key regions where conformational differences are claimed, particularly the εCTD, the βDP C-terminus, and the nucleotide binding sites. If the differences between conformers are within the coordinate error at this resolution, this must be explicitly acknowledged.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** MD simulation methodology and interpretation
- **Claim pointer** The manuscript states that "MD simulations validate and expand the ensemble of structural rearrangements underlying the rotary mechanism" and that the simulations "provide mechanistic continuity between the experimentally resolved cryo-EM states."
- **Evidence pointer** Methods section "Targeted Molecular Dynamics Simulations"; Results sections describing TMD simulations; Table S2 (referenced but not visible)
- **Concern** The TMD simulations use RMSD-based biasing potentials to drive transitions between experimentally determined states. This approach is inherently biased toward the target structures and cannot independently validate the transition pathway. The authors do not report whether the simulations were repeated with different initial velocities, whether the biasing force constants were optimized, or whether the resulting trajectories were analyzed for convergence. The claim that simulations "validate" the cryo-EM interpretations is overstated given the methodology used. Additionally, the simulation timescales (200-600 ns) are short relative to the large conformational changes described.
- **Why it matters** The manuscript presents the MD simulations as supporting evidence for the proposed mechanism. If the simulations are not rigorously performed and analyzed, this support is weakened, and the mechanistic conclusions rest solely on the cryo-EM structures.
- **Resolution test** Provide details on simulation repeats, convergence analysis, and error estimates. Consider using unbiased or enhanced sampling methods to test whether the transitions occur spontaneously. Clearly distinguish between what the simulations demonstrate versus what they assume through the biasing protocol.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Therapeutic targeting claims
- **Claim pointer** The manuscript claims that the structures "identify novel therapeutic targets and pave the way for rational design of selective inhibitors" and specifically proposes targeting the εCTD transition states with molecular glues.
- **Evidence pointer** Discussion section "Transition States Representing Novel Targets"
- **Concern** The therapeutic claims are speculative and not supported by direct experimental evidence. No compound screening, binding assays, or functional validation of the proposed targets is presented. The comparison to CELMoD molecular glues is made without demonstrating that the *A. baumannii* γ-ε interface is druggable or that disrupting the εCTD transition would selectively kill the pathogen. The claim that amino acid differences from the human counterpart would prevent toxicity is not substantiated by any comparative analysis.
- **Why it matters** The title and framing of the manuscript emphasize therapeutic relevance. If the therapeutic claims are not supported, the significance of the work is substantially reduced, and the manuscript may be overstating its translational value.
- **Resolution test** Either remove or substantially temper the therapeutic claims, or provide preliminary evidence of druggability, such as small-molecule binding assays, virtual screening results, or functional studies with εCTD mutants that demonstrate the importance of the proposed target sites.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Activity assay interpretation
- **Claim pointer** The manuscript states that "ATP synthesis measurements showed reproducible spontaneous ATP formation, which decreased over time due to slow cleavage of the formed ATP."
- **Evidence pointer** Results section; Figure 1A
- **Concern** The ATP synthesis assay is described only briefly. The authors do not provide details on the assay sensitivity, the amount of ATP formed relative to background, the stoichiometry of ATP per enzyme, or whether the observed signal could be due to adenylate kinase contamination or other artifacts. The claim that ATP formation "decreased over time due to slow cleavage" is presented without supporting data showing ATP hydrolysis activity under the same conditions.
- **Why it matters** The functional data are used to support the interpretation that the structural states are catalytically relevant. If the activity measurements are not rigorously controlled, this support is weakened.
- **Resolution test** Provide full details of the ATP synthesis assay, including controls (e.g., enzyme without substrates, boiled enzyme, adenylate kinase inhibitor), quantification of ATP produced per enzyme molecule, and time-course data showing both synthesis and subsequent hydrolysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Methods section "Purification and ATP Synthesis Measurement"
- **Evidence pointer** Methods section
- **Issue** The ATP synthesis assay description lacks sufficient detail on the detection method, calibration curve, and statistical treatment of replicates.
- **Required correction** Provide a more detailed description of the assay, including the luminescence detection protocol, ATP standard curve, number of replicates, and error analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1B and classification of conformers
- **Evidence pointer** Results section; Figure 1B
- **Issue** The classification of the six conformers into three main groups based on εCTD conformation is clear, but the relationship between the conformers and their potential temporal ordering is not explicitly stated in the figure legend or text.
- **Required correction** Add a clear statement in the figure legend or text explaining the proposed ordering of the states and the criteria used to assign them.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section "Factors Triggering εCTD Conformational Changes"
- **Evidence pointer** Discussion section
- **Issue** The discussion of εCTD regulatory mechanisms would benefit from more direct comparison with the extensive literature on *E. coli* and *Bacillus* PS3 ε subunit structures and dynamics.
- **Required correction** Expand the comparison with relevant literature to place the *A. baumannii* findings in a broader context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract and Results
- **Issue** The term "spontaneous ATP formation" is used, which could be misinterpreted as implying that ATP formation occurs without any energy input. The authors do clarify that the energy comes from substrate binding and conformational changes, but the terminology is potentially misleading.
- **Required correction** Consider using a more precise term such as "substrate-induced ATP formation" or "binding-driven ATP synthesis" throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures S1-S3 and Table S1
- **Evidence pointer** Referenced supporting information
- **Issue** The supporting figures and tables are not visible in the submitted text, making it impossible to assess the quality of the cryo-EM data processing and model refinement.
- **Required correction** Ensure that all supporting figures and tables are included in the submission and are of sufficient quality to allow assessment of the structural data.

### Technical failings that need to be addressed before the case is established
1. The cryo-EM structures are presented without full validation metrics in the visible text. FSC curves, local resolution maps, and model-to-map correlation values must be provided for all six conformers.
2. The distinction between conformers within each group (C1a vs C1b, C2a vs C2b) needs to be supported by clear density features and quantitative comparisons.
3. The MD simulation methodology requires more detail on convergence, repeatability, and the potential influence of the biasing protocol on the observed transitions.
4. The ATP synthesis assay needs additional controls and quantification to support the claim of spontaneous ATP formation.
5. The therapeutic targeting claims require either experimental support or substantial tempering.

### Assessment against Nature-style criteria
**Originality**: The work presents novel structural data on the *A. baumannii* F1-ATPase, including multiple conformational states of the ε subunit. The observation of an "initiation state" and the proposed transition pathway are new contributions. However, the overall concept of ε subunit conformational regulation is well established in the ATP synthase field, and the novelty lies primarily in the specific structural details for this organism.

**Scientific importance**: The clinical relevance of *A. baumannii* as a multidrug-resistant pathogen gives the work potential importance. Understanding the ATP synthase mechanism in this organism could inform future therapeutic development. However, the direct importance of the specific structural findings for understanding ATP synthase catalysis is incremental rather than transformative.

**Interdisciplinary readership**: The work bridges structural biology, bioenergetics, and antimicrobial resistance research. The potential therapeutic angle could attract interest from drug discovery researchers. However, the technical nature of the cryo-EM and MD analyses may limit accessibility to a broader readership.

**Technical soundness**: The cryo-EM data collection and processing appear to follow standard protocols, but the lack of visible validation metrics prevents full assessment. The MD simulation approach using TMD is appropriate for exploring transitions between known states but has inherent limitations for validating mechanisms. The activity assays are described too briefly to assess their rigor.

**Readability for nonspecialists**: The manuscript is written in a style accessible to structural biologists and biochemists, but the significance of the findings for a general scientific audience is not clearly articulated. The therapeutic implications are stated but not developed in a way that would engage nonspecialists.

### Recommendation posture
Supportive if technical concerns are resolved. The structural data are potentially valuable, and the manuscript addresses an important biological question in a clinically relevant organism. However, the central claims regarding catalytic intermediates and therapeutic targets require stronger experimental support and more rigorous validation. The authors should address the concerns regarding cryo-EM validation, MD simulation methodology, activity assay rigor, and temper the therapeutic claims appropriately.

## Risk / unsupported claims
1. The claim that the structures represent "ATP synthesizing" states captured "during ATP synthesis" is not fully supported, as the F1-ATPase alone cannot perform physiologically relevant ATP synthesis without the FO domain and proton motive force.
2. The claim that the observed εCTD transitions represent a "molecular gear" mechanism is an interpretation that goes beyond the static structural data presented.
3. The proposal that the transition states represent "novel therapeutic targets" is speculative and not supported by any functional or binding data.
4. The statement that MD simulations "validate" the cryo-EM interpretations is overstated given the biased nature of TMD simulations.
5. The claim that the εCTD transition pathway is relevant "across a variety of antimicrobial resistant bacteria" is an extrapolation from a single organism without comparative structural or functional data.