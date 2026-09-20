## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that the TIR domain of the plant TNL receptor RCSP contains noncanonical structural features (BB-loop deletion, alpha5alpha6-loop insertion, atypical catalytic residues) that enable recognition of insect chemosensory proteins (CSPs) and mediate weak cell death in Nicotiana benthamiana, proposing a novel plant-insect interaction mechanism.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or statistical details provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, statistical analyses, structural coordinates, AlphaFold3/DMFold modeling parameters, docking protocols, mutagenesis validation data, evolutionary analysis details

## Reviewer
- **Overall assessment** The abstract presents an intriguing and potentially novel finding regarding structural diversification of a plant TNL receptor TIR domain in response to insect effectors. However, the evidence base is severely limited by the abstract-only format, and several key claims cannot be evaluated for technical soundness. The noncanonical mechanisms proposed are interesting but require substantial experimental validation that is not visible here.
- **Who would be interested in the results, and why** Plant immunologists studying NLR receptor structure-function relationships; researchers investigating insect-plant coevolution and effector biology; structural biologists interested in TIR domain diversification; agricultural scientists working on pest resistance in Solanaceae crops.
- **Major strengths** The identification of a plant TNL receptor that recognizes insect chemosensory proteins is conceptually novel and broadens the known ligand repertoire of plant immune receptors. The structural features described (BB-loop deletion, alpha5alpha6-loop insertion, atypical catalytic residues) suggest genuine mechanistic divergence from canonical TIR domains. The evolutionary analysis framing Solanaceae-specific adaptations provides a useful context for understanding receptor diversification.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (structural modeling validation), R1-M2 (functional evidence for dual catalytic residues), R1-M3 (cell death phenotype quantification), R1-M4 (specificity of CSP recognition)
- **Assessment against Nature-style criteria** Originality is high, as the concept of insect effector recognition by a structurally diversified TNL receptor is not previously reported. Scientific importance is moderate to high, with potential implications for understanding plant immunity and pest resistance, though the broad significance beyond Solanaceae is not established. Interdisciplinary readership appeal is limited by the abstract's focus on structural details without clear translational context. Technical soundness cannot be assessed from the abstract alone, and the reliance on AlphaFold3/DMFold predictions without experimental structural validation is a concern. Readability for nonspecialists is acceptable but the abstract is dense with structural terminology that may obscure the broader biological message.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a compelling hypothesis but lacks sufficient experimental detail to support the core mechanistic claims. Supportive if technical concerns are resolved with full experimental validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that AlphaFold3/DMFold modeling reveals a novel interface stabilizing an atypical tetrameric architecture, and that BB-loop deletion disrupts canonical NAD(+) binding and tetramerization.
- **Evidence pointer** Abstract text; structural analysis and modeling sections not provided
- **Concern** The structural claims rest entirely on computational predictions (AlphaFold3/DMFold) with no experimental structural validation (e.g., crystallography, cryo-EM, or mutagenesis-based oligomerization assays). The abstract states that BB-loop deletion "disrupts" canonical tetramerization and that the alpha5alpha6-loop insertion "stabilizes" an atypical tetramer, but no direct evidence for these conformational states is presented.
- **Why it matters** The central novelty of this work is the noncanonical structural mechanism. Without experimental validation of the predicted tetrameric architecture and the functional consequences of the BB-loop deletion and alpha5alpha6-loop insertion, the structural model remains speculative and cannot support the mechanistic conclusions.
- **Resolution test** Provide experimental structural data (e.g., crystal structure or cryo-EM) or at minimum biochemical evidence (e.g., size-exclusion chromatography, cross-linking, or native PAGE) demonstrating the oligomeric state of RCSP-TIR and the effects of the described mutations on tetramerization and NAD(+) binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that RCSP depends on dual catalytic residues (D86/Q87) to mediate weak cell death, with substitution of the canonical catalytic glutamate to glutamine (E87Q).
- **Evidence pointer** Abstract text; site-directed mutagenesis data not provided
- **Concern** The claim that D86/Q87 function as dual catalytic residues is unusual, as the canonical TIR catalytic glutamate is replaced by glutamine, which is not typically catalytically active. The abstract does not explain how glutamine at this position supports catalysis, nor does it provide enzymatic assays (e.g., NAD(+) cleavage or NADase activity) to demonstrate catalytic function. The "weak cell death" phenotype is not quantified or compared to appropriate controls.
- **Why it matters** The catalytic mechanism is a core claim of the paper. If the enzymatic activity is not demonstrated biochemically, the assertion of "dual catalytic residues" is unsupported. The weak cell death phenotype may arise from noncatalytic signaling functions rather than enzymatic activity, which would change the mechanistic interpretation.
- **Resolution test** Provide direct enzymatic assays showing NAD(+) cleavage or NADase activity for RCSP-TIR and mutants (D86A, Q87A, E87Q alone and in combination). Quantify cell death with statistical comparisons to wild-type and negative controls, and demonstrate that the observed cell death is dependent on the proposed catalytic residues.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The abstract claims that CSPs induce dwarfism in Nicotiana benthamiana through recognition by RCSP, and that RCSP mediates "weak cell death."
- **Evidence pointer** Abstract text; phenotypic data not provided
- **Concern** The abstract mentions dwarfism and weak cell death but provides no quantitative data, dose-response relationships, or temporal dynamics. It is unclear whether the dwarfism phenotype is specific to CSP recognition by RCSP or could result from general stress responses. The "weak" cell death phenotype raises questions about biological relevance and whether the response is robust enough to constitute a meaningful immune activation.
- **Why it matters** The physiological relevance of the RCSP-CSP interaction depends on the strength and specificity of the phenotypic responses. Without quantitative data and appropriate genetic controls (e.g., RCSP knockout or silencing), the causal link between CSP recognition and the observed phenotypes is not established.
- **Resolution test** Provide quantitative measurements of plant height, cell death area or ion leakage, with statistical analysis and appropriate controls (e.g., RCSP-silenced plants, catalytically dead mutants, and unrelated effector controls). Show dose-dependent responses to CSP application.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The abstract claims that evolutionary analysis classifies RCSP-TIR homologs into four distinct clades, highlighting Solanaceae-specific adaptations, and that this enables CSP recognition and immune signaling reprogramming.
- **Evidence pointer** Abstract text; evolutionary analysis details not provided
- **Concern** The evolutionary analysis is mentioned but no details are given regarding the number of sequences analyzed, the phylogenetic methods used, or the statistical support for the four clades. The claim of "Solanaceae-specific adaptations" is not supported by any comparative genomic or functional data showing that non-Solanaceae RCSP homologs fail to recognize CSPs.
- **Why it matters** The evolutionary framing is used to argue for the novelty and specificity of the interaction. Without robust phylogenetic analysis and functional comparisons across species, the claim of Solanaceae-specific adaptation is speculative and does not strengthen the mechanistic story.
- **Resolution test** Provide the phylogenetic tree with bootstrap or posterior probability support, list the species included, and include functional assays (e.g., CSP recognition) for representative homologs from different clades to demonstrate specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract structure
- **Evidence pointer** Abstract text
- **Issue** The abstract begins with the structural findings before introducing the biological context of CSPs and RCSP, which may confuse readers unfamiliar with the system.
- **Required correction** Reorder the abstract to first introduce the biological question (CSP effectors and RCSP receptor), then present the structural and mechanistic findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Atypical plant TNL immune receptor"
- **Evidence pointer** Title and abstract
- **Issue** The term "atypical" is used without clear definition of what constitutes the typical reference. The abstract describes specific structural features, but the baseline for "typical" TNL receptors is not stated.
- **Required correction** Define the canonical TNL features being compared against, or replace "atypical" with more specific descriptors (e.g., "structurally divergent").

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods description
- **Evidence pointer** Abstract text
- **Issue** The abstract mentions "integrated approaches combining molecular docking and site-directed mutagenesis" but provides no details on docking software, scoring functions, or validation of docking predictions.
- **Required correction** In the full manuscript, ensure docking methods are described with sufficient detail for reproducibility, including software versions, parameters, and validation steps.

## Risk / unsupported claims
- The claim that RCSP "may utilize a noncanonical NAD(+)-binding pocket" is speculative and not supported by direct binding or enzymatic data in the abstract.
- The claim that the alpha5alpha6-loop insertion "stabilizes an atypical tetrameric architecture" is based solely on computational modeling without experimental validation.
- The claim of "dual catalytic residues (D86/Q87)" is unsupported without enzymatic assays demonstrating catalytic activity.
- The claim of "Solanaceae-specific adaptations" is not substantiated by the evolutionary analysis details provided.
- The biological significance of "weak cell death" as a meaningful immune response is not established without quantitative comparison to known immune outputs.