## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence; no assessment of editorial fit for a specific journal
- **Shared manuscript claim summary** The authors report that the conserved N-terminal IQ motifs of the HECT E3 ligases UBE3B and UBE3C bind apo-calmodulin through distinct molecular recognition modes, with UBE3B showing high-affinity, C-lobe-centered binding and UBE3C showing weaker, more distributed engagement, supported by ITC, NMR, computational modeling, MD simulations, and phylogenetic analysis
- **Visible evidence base** Abstract; full introduction; results sections with figure references (Figures 1–9); discussion; materials and methods; supplementary table S1 and figure S1 referenced but not provided
- **Missing materials affecting confidence** Figures 1–9 and Table S1/Figure S1 are referenced but not included in the provided material; raw ITC thermograms, NMR spectral overlays, and MD trajectory data are not accessible; no peptide purity validation data beyond manufacturer statement

## Reviewer
- **Overall assessment** This manuscript presents a comparative biochemical and biophysical analysis of apo-calmodulin recognition by the IQ motifs of two related HECT E3 ligases. The combination of ITC, NMR, and MD simulation is appropriate and the central observation—that conserved IQ motifs can engage apo-CaM through distinct modes—is potentially interesting. However, the strength of the conclusions is limited by the absence of key experimental controls, the reliance on computational models without experimental validation of binding registers, and the lack of functional data connecting the observed binding differences to biological regulation. The phylogenetic analysis is presented as supporting evidence but its connection to the biochemical findings is not rigorously established. The manuscript would benefit from additional experiments to strengthen the mechanistic claims.

- **Who would be interested in the results, and why** Researchers studying calmodulin-mediated signaling, IQ motif biology, and the regulation of HECT E3 ubiquitin ligases would find these results relevant. The work also speaks to the broader question of how conserved linear motifs can encode divergent binding behaviors, which is of interest to those working on molecular recognition and protein evolution. The comparative approach between two closely related ligases may be useful for those investigating the functional diversification of enzyme families.

- **Major strengths** The study addresses a clear and well-framed question about whether conserved IQ motifs in related ligases encode conserved or divergent CaM recognition. The combination of multiple biophysical techniques (ITC, NMR) with computational approaches (AF3, MD) is appropriate for characterizing binding affinity, kinetics, and structural organization. The authors are appropriately cautious in interpreting their computational models as hypotheses rather than definitive structures. The discussion of alternative explanations for the weaker UBE3C response is thoughtful and balanced.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the UBE3B IQ motif binds apo-CaM with high affinity (Kd = 105 ± 18 nM) and preferentially engages the C-lobe, while the UBE3C IQ motif binds weakly and produces smaller, more distributed perturbations.
- **Evidence pointer** Results section "The UBE3B IQ motif preferentially engages the apo-CaM C-lobe with high affinity"; Figure 3; Methods "ITC"
- **Concern** The ITC experiments lack peptide-into-buffer control titrations, as explicitly stated in the methods. The authors acknowledge that the small heat changes observed for UBE3C "cannot be unambiguously distinguished from contributions arising from peptide dilution." This is a critical control for interpreting weak binding interactions. Without this control, the claim that UBE3C shows weak but measurable binding is not rigorously supported. Additionally, the reported stoichiometry of approximately 1.4 for both WT CaM and cCaM interactions is unusual and not adequately explained; the authors mention other stoichiometries in the literature but do not discuss what a non-integer stoichiometry of 1.4 might mean for their binding model or whether the one-site fitting model is appropriate.
- **Why it matters** The central comparative claim of the manuscript rests on the distinction between strong UBE3B binding and weak UBE3C binding. If the UBE3C ITC data cannot be reliably distinguished from dilution artifacts, the quantitative comparison is compromised. The non-ideal stoichiometry also raises questions about the validity of the one-site binding model used to extract Kd values.
- **Resolution test** The authors should perform peptide-into-buffer control titrations for both UBE3B and UBE3C peptides under identical conditions and show that the UBE3C heat changes exceed the dilution baseline. They should also address the 1.4 stoichiometry, either by discussing alternative binding models or by providing additional experiments (e.g., varying concentration ranges, different fitting models) to establish the appropriateness of the one-site model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that NMR titrations reveal distinct molecular recognition modes, with UBE3B binding in slow exchange and producing a localized C-lobe interaction surface, while UBE3C binds in fast exchange with smaller, more distributed perturbations.
- **Evidence pointer** Results section "NMR titrations reveal distinct apo-CaM recognition modes for the UBE3B and UBE3C IQ motifs"; Figures 4 and 5; Methods "NMR spectroscopy and CSP analysis"
- **Concern** The NMR titration for UBE3B was performed at 300 μM apo-CaM, which the authors acknowledge is "substantially above the submicromolar affinity measured independently by ITC," placing the experiment in the tight-binding regime. Under these conditions, the slow-exchange observation is expected and does not independently confirm high affinity. More importantly, the authors state that backbone assignments were determined "in-house" for the saturated UBE3B complex, but no details are provided on how assignments were transferred or validated for the UBE3C complex, where peaks shift rather than disappear. The CSP analysis for UBE3C relies on tracking peaks during titration, but with only five well-resolved resonances used for global fitting, the structural interpretation of "distributed perturbations" is based on a limited subset of residues. The mapping of CSPs onto AF3 models is presented without experimental validation of the model accuracy for these specific complexes.
- **Why it matters** The NMR data are central to the claim of distinct recognition modes. If the assignment transfer to the UBE3C complex is not rigorously established, the CSP mapping could be misleading. The limited number of residues used for quantitative fitting reduces confidence in the reported Kd of 180 ± 20 μM for UBE3C. The use of AF3 models as a basis for interpreting CSP data requires validation that the predicted structures are relevant to the solution-state complexes.
- **Resolution test** The authors should provide details on how assignments were transferred between free and bound states for both complexes, including any ambiguity in peak tracking for UBE3C. They should show complete CSP data for all assigned residues, not just the five used for fitting, and discuss whether the limited subset is representative. If possible, experimental validation of the AF3 models (e.g., through mutagenesis of predicted interface residues) would strengthen the structural interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the phylogenetic analysis reveals that UBE3B and UBE3C IQ motifs have followed divergent evolutionary trajectories within the broader IQ motif family.
- **Evidence pointer** Results section "UBE3B and UBE3C IQ motifs follow divergent evolutionary trajectories"; Figure S1; Methods "Phylogenetic analysis"
- **Concern** The phylogenetic analysis is presented as a single supplementary figure with minimal methodological detail. The authors state that approximately 450 IQ motif-containing proteins were analyzed, but the selection criteria for these proteins, the alignment quality, and the statistical support for the specific branching patterns that separate UBE3B and UBE3C are not described. The claim of "divergent evolutionary trajectories" is not quantitatively supported; no measures of sequence divergence, selection pressure, or functional diversification are provided. The connection between the phylogenetic placement and the biochemical findings is asserted but not rigorously demonstrated.
- **Why it matters** The evolutionary claim is presented as a supporting pillar of the manuscript's narrative that conserved IQ motifs can diverge functionally. Without robust phylogenetic evidence, this claim is speculative and does not add meaningful support to the biochemical findings.
- **Resolution test** The authors should provide a more detailed phylogenetic analysis, including alignment statistics, model selection, bootstrap support values for key nodes, and a quantitative comparison of sequence features between UBE3B and UBE3C IQ motifs relative to other IQ motif families. Alternatively, the evolutionary claims could be removed or substantially softened.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations reveal differences in conformational stability and interface organization between the UBE3B and UBE3C complexes, with the UBE3B complex retaining a more stable C-lobe-centered interface.
- **Evidence pointer** Results section "Structural modeling and MD simulations provide a framework for divergent apo-CaM engagement mechanisms"; Figures 6–9; Methods "MD simulations" and "MD trajectory analysis"
- **Concern** The MD simulation methods are described in detail, but key validation metrics are missing. The authors state that models were selected based on "predicted local distance difference test confidence scores," but the actual scores are not reported. The simulations are described as "multimicrosecond" totaling 12 μs across three replicates per complex, but the convergence of the simulations is not demonstrated. The analysis of buried surface area shows a bimodal distribution for the UBE3C complex, but the statistical significance of this bimodality and its reproducibility across the three independent simulations are not reported. The interpretation that the UBE3C complex samples "increased conformational heterogeneity" is based on qualitative observations rather than quantitative metrics.
- **Why it matters** The MD simulations are used to provide a structural framework for interpreting the experimental data. If the simulations are not demonstrably converged or if the observed differences are not statistically robust, the proposed framework is speculative and could mislead interpretation of the experimental results.
- **Resolution test** The authors should report convergence metrics (e.g., RMSD vs. time plots, block averaging), provide statistical analysis of the bimodal BSA distribution, and demonstrate that the observed differences between complexes are reproducible across independent simulations. If the simulations are not converged, this should be stated and the interpretations appropriately qualified.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript assumes familiarity with the details of IQ motif biology and calmodulin recognition modes. The distinction between compact and extended apo-CaM/IQ complexes is introduced but not explained clearly for readers who may not work on calmodulin. The significance of the HECT domain architecture and its regulation is discussed but the connection to the IQ motif findings could be made more explicit.
- **Required correction** Consider adding a brief explanation of the different apo-CaM/IQ recognition modes and why the distinction between them matters for calmodulin function. Clarify the potential functional implications of the different binding modes for UBE3B and UBE3C regulation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, ITC section
- **Evidence pointer** Methods "ITC"
- **Issue** The ITC fitting model is described as a "one-site binding model," but no details are given about the fitting software, the number of parameters, or the goodness-of-fit statistics. The reported errors (± values) are not defined as standard deviations or standard errors.
- **Required correction** Provide details on the fitting procedure, including software used, and define the error terms. Report goodness-of-fit statistics or show representative fits.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, NMR section
- **Evidence pointer** Methods "NMR spectroscopy and CSP analysis"
- **Issue** The NMR experiments were performed at pH 6.0 while ITC experiments were at pH 7.5. The authors do not discuss whether this pH difference could affect binding affinity or recognition mode. The CSP calculation formula is given, but the threshold for what constitutes a "significant" perturbation is not defined.
- **Required correction** Discuss the potential effect of pH on the binding measurements. Define the significance threshold used for CSP analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the functional implications of the divergent binding modes is speculative. The authors suggest that the differences may allow distinct responses to Ca2+ levels but do not provide experimental evidence or a detailed mechanistic model for how this would occur.
- **Required correction** Either provide a more concrete model for how the different binding modes could lead to distinct functional outcomes, or clearly label these as open questions for future investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure legends
- **Evidence pointer** Figures 3–9 (legends not provided in the submitted material)
- **Issue** The figure legends are not included in the provided material, making it impossible to assess whether the figures are adequately described and whether the data presentation is clear.
- **Required correction** Ensure that figure legends are complete and self-explanatory, including definitions of all abbreviations and statistical details.

## Risk / unsupported claims
- The claim that UBE3C IQ motif binds apo-CaM with a Kd of 180 ± 20 μM is based on a global fit of only five residues and lacks peptide-into-buffer control experiments; this quantitative value should be treated with caution.
- The claim of "divergent evolutionary trajectories" is not supported by the limited phylogenetic analysis presented; no quantitative measures of divergence or statistical support are provided.
- The structural models from AF3 are presented as a framework for interpretation, but the authors appropriately acknowledge they are not experimentally determined structures; however, the MD-based claims of differential stability and interface organization lack convergence and statistical validation.
- The statement that "UBE3B IQ motif binding occurred in slow exchange" is expected given the high concentration used relative to the Kd and does not independently confirm the affinity measured by ITC.
- The functional implications of the divergent binding modes for UBE3B and UBE3B regulation in cells are speculative and not supported by direct experimental evidence.
- The claim that "conserved IQ motifs in related HECT ligases can encode different apo-CaM binding modes" is supported by the experimental data, but the broader generalization to "conserved IQ motifs" across the family is not justified by the two examples studied.