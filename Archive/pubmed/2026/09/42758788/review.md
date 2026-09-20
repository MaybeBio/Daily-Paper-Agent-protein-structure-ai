## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract text
- **Shared manuscript claim summary** The authors propose, based on integrative AI-assisted structure prediction and molecular dynamics simulations, that CPPF binds at a composite alpha/beta-tubulin interface pocket, with dominant contacts from beta-tubulin residues VAL236 and LEU253, and that this binding mode is preserved across two major beta-tubulin conformational states.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation protocols, force field parameters, convergence criteria, MM-PBSA calculation details, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract presents a plausible computational hypothesis for CPPF binding to tubulin, but the evidence base visible in the abstract is insufficient to evaluate the technical rigor of the simulations or the robustness of the proposed binding mode. The claim of a "composite" interface pocket dominated by beta-tubulin contacts is internally consistent, but the absence of methodological detail and quantitative validation limits confidence. The authors appropriately acknowledge the need for experimental validation, which tempers the strength of the conclusions.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, structural biology of microtubule-targeting agents, and anticancer pharmacology would find these results relevant. The work addresses a clinically important problem, namely multidrug resistance to microtubule-targeting drugs, and offers a testable structural hypothesis that could guide medicinal chemistry efforts.
- **Major strengths** The study addresses a significant biomedical problem with clear translational relevance. The use of multiple complementary AI-based structure prediction tools, combined with MD simulations, represents a modern integrative approach. The authors explicitly acknowledge the computational nature of the findings and call for experimental validation, which is scientifically honest.
- **Major Concerns** The abstract provides no quantitative data, no error estimates, and no methodological details that would allow assessment of simulation quality or convergence. The comparison between alpha- and beta-tubulin binding energetics is stated qualitatively without numerical support. The claim that binding is "preserved" across conformations relies on comparable MM-PBSA values, but no values are given.
- **Minor Comments** The abstract would benefit from stating the number of independent simulations performed, the total simulation time, and the criteria used to define a stable binding mode. The phrase "composite interface pocket" is not defined in the abstract. The relevance of the PDB 5IJ0 structure versus 6E7B for the physiological context is not explained.
- **Technical failings that need to be addressed before the case is established** None can be identified from the abstract alone, but the absence of any quantitative results means the technical case is not currently assessable.
- **Assessment against Nature-style criteria** Originality: moderate, as computational prediction of ligand binding sites on tubulin is an active area. Scientific importance: potentially high given the MDR context, but not established from the abstract alone. Interdisciplinary readership: the topic bridges computational biology, structural biology, and oncology, which is attractive. Technical soundness: not assessable from the abstract. Readability for nonspecialists: the abstract is clear and accessible, though some terms such as MM-PBSA and Protenix may require background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and the approach is modern, but the abstract alone does not provide sufficient quantitative or methodological evidence to support the central claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "CPPF binds at the alpha/beta interface with dominant contributions from beta-tubulin residues, particularly VAL236 and LEU253"
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract states this as a finding but provides no quantitative data, such as binding free energies, contact frequencies, or occupancy values, to support the identification of specific residues as dominant.
- **Why it matters** Without quantitative support, the reader cannot assess whether the proposed binding mode is robust or an artifact of a single simulation trajectory or prediction tool.
- **Resolution test** Provide numerical values for residue-wise interaction energies or contact occupancies, with error estimates across multiple independent simulations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "we performed structure prediction using Protenix, RoseTTAFold All-Atom (RFAA) and Umol, as well as molecular dynamics (MD) simulations"
- **Evidence pointer** Abstract text, location not provided
- **Concern** No details are given on how the three AI tools were used, how their outputs were reconciled, what force field was used for MD, what simulation length was achieved, or how convergence was assessed.
- **Why it matters** The reliability of the binding mode prediction depends entirely on the quality and convergence of the simulations. Without these details, the technical soundness of the work cannot be evaluated.
- **Resolution test** Include a methods summary in the abstract or provide access to full methods that specify all simulation parameters, convergence criteria, and validation steps.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for comparative claims
- **Claim pointer** "beta-tubulin exhibited more favorable binding energetics and deeper, broader free-energy minima than alpha-tubulin" and "comparable MM-PBSA binding free energies"
- **Evidence pointer** Abstract text, location not provided
- **Concern** These comparative statements are made without any numerical values, statistical measures, or error bars. The term "comparable" is undefined.
- **Why it matters** The central claim of a beta-tubulin-dominated interface rests on these comparisons. Without numbers, the claim is not falsifiable or verifiable.
- **Resolution test** Report mean and standard deviation of binding free energies for each system, and state the criterion for "comparable" (for example, within a defined energy threshold).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text, location not provided
- **Issue** The term "composite interface pocket" is used without definition, which may confuse readers unfamiliar with the structural context.
- **Required correction** Define the term briefly, for example by noting that the pocket is formed by residues from both subunits.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Contextual justification
- **Affected element** Structural model choice
- **Evidence pointer** Abstract text, location not provided
- **Issue** The choice of PDB 5IJ0 as the primary structure and 6E7B as the alternative conformational state is not justified in the abstract.
- **Required correction** Add a sentence explaining why these two structures represent relevant physiological states of tubulin.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation reporting
- **Evidence pointer** Abstract text, location not provided
- **Issue** No information is given on the number of replicates, total simulation time, or convergence metrics.
- **Required correction** Include at least the total simulation time and number of independent runs in the abstract, or state that full details are in the methods.

## Risk / unsupported claims

- The specific residue-level binding mode (VAL236, LEU253) is unsupported by quantitative data in the abstract.
- The comparative energetic claim between beta- and alpha-tubulin is unsupported by numerical values.
- The claim of preserved binding across conformational states is unsupported by reported MM-PBSA values.
- The overall binding mode at the interface is presented as a finding, but the abstract provides no statistical or convergence evidence to support it.