## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, without access to full methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors introduce Pallatom2, a 65.9 million parameter atom-to-atom generative model for de novo protein binder design. The model jointly represents sequence, backbone, side-chain geometry, and interface contacts using an Atom14 representation and residue-guided sparse all-atom attention. The abstract reports state-of-the-art in silico screening performance across nine targets, experimental validation yielding 112 active binders from 210 tested candidates (53.3%) across ten targets, picomolar affinities for six targets, and additional capabilities in interface transfer, affinity maturation, and recovery of inactive designs.
- **Visible evidence base** Abstract text only. No figures, tables, methods descriptions, or supplementary data were provided for assessment.
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, methods section, experimental protocols, statistical analyses, benchmark definitions, and supplementary information. The absence of these materials substantially limits the depth of technical verification possible.

## Reviewer

- **Overall assessment** The abstract presents an ambitious and potentially significant contribution to computational protein design. The reported experimental success rates and affinity values are notable, and the range of demonstrated capabilities is broad. However, the abstract alone provides insufficient detail to verify the technical soundness of the model architecture, the fairness of benchmark comparisons, or the robustness of the experimental claims. Several claims require careful scrutiny regarding statistical rigor, benchmark protocol transparency, and the generalizability of the reported results. The work is potentially impactful for the protein design community, but the current evidence base does not permit full technical validation.
- **Who would be interested in the results, and why** Computational protein designers and structural biologists would be the primary audience. Researchers developing generative models for biomolecular design would find the architectural innovations relevant. Experimental groups working on binder discovery, particularly those targeting protein-protein interactions, would be interested in the reported experimental success rates and affinities. The demonstrated capabilities in affinity maturation and recovery of inactive designs may also interest therapeutic antibody engineers and nanobody developers.
- **Major strengths** The model is compact at 65.9 million parameters, which is advantageous for accessibility and reproducibility. The reported experimental validation across ten targets with a 53.3% hit rate is substantial and exceeds typical success rates in the field. The demonstration of multiple design capabilities beyond de novo discovery, including interface transfer, affinity maturation, and recovery of inactive designs, suggests broad utility. The extension of monomer sampling to 1,600 residues indicates scalability.
- **Major Concerns** The concerns below identify issues that require clarification or additional evidence. None can be fully resolved from the abstract alone, but the blocking status reflects whether the concern undermines the core claims as presented.
- **Minor Comments** The minor comments below note presentation and clarity issues that should be addressed in a revised manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The atom-to-atom generative approach with unified Atom14 representation appears novel, though the abstract does not provide sufficient comparison to prior architectures to fully establish originality. Scientific importance: The reported experimental success rates and picomolar affinities, if reproducible, would represent a meaningful advance in computational binder design. Interdisciplinary readership: The work bridges machine learning, structural biology, and experimental protein engineering, which could attract broad interest. Technical soundness: Cannot be adequately assessed from the abstract alone. The architecture description is high-level, and no validation details are provided. Readability for nonspecialists: The abstract is technically dense and assumes familiarity with protein design terminology, which is appropriate for the target audience but may limit broader accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The reported results are potentially significant, but the abstract alone does not provide sufficient evidence to fully establish the claims. A full manuscript with detailed methods, benchmark protocols, and experimental data would be required for complete assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Pallatom2 achieves state-of-the-art in silico screening performance across all nine targets with cross-method benchmark data under the reported protocols."
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of state-of-the-art performance across all nine targets is presented without any specification of the benchmark methods, evaluation metrics, or comparison baselines. The phrase "under the reported protocols" is ambiguous and does not clarify whether the comparison was fair, whether the same computational budget was used for all methods, or whether the benchmark targets were selected to favor Pallatom2.
- **Why it matters** State-of-the-art claims are central to establishing the model's value. Without transparent benchmark definitions and fair comparison protocols, the claim cannot be independently verified. Selective benchmarking or favorable protocol choices could inflate apparent performance.
- **Resolution test** Provide a detailed benchmark description including the names and versions of all compared methods, the exact evaluation metrics, the computational resources allocated to each method, and the criteria for target selection. Ideally, use established community benchmarks with pre-registered protocols.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "biolayer interferometry identifies 112 active designs among 210 tested candidates (53.3%), with binders obtained for all ten experimentally evaluated targets."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports raw counts and percentages of active designs but does not provide any statistical context. There is no information on the distribution of hits across targets, the criteria for defining "active," the number of replicates, the variability between experiments, or whether the hit rate is significantly different from what would be expected by chance or from baseline methods.
- **Why it matters** A 53.3% hit rate is impressive only if it exceeds what alternative approaches would achieve under identical conditions. Without statistical comparison to baselines or controls, the experimental success claim is difficult to contextualize. High hit rates can also result from lenient activity thresholds.
- **Resolution test** Provide per-target hit rates, the definition of "active" with the specific biolayer interferometry response thresholds, replicate information, and a statistical comparison to appropriate controls or baseline design methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Six targets yield picomolar-scale apparent affinities, including K_D values of 3.96 pM for SC2RBD and 33.8 pM for PD-L1, while TNFα reaches 1.166 nM."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports apparent K_D values without specifying the measurement method, the number of independent experiments, the error bars, or the fitting model used. The term "apparent" is used, which suggests these values may not represent true equilibrium dissociation constants. Picomolar affinities are exceptionally strong and require rigorous validation to rule out artifacts such as avidity effects, non-specific binding, or fitting errors.
- **Why it matters** Picomolar affinities are a headline result that would attract significant attention. If these values are not rigorously validated, the credibility of the entire experimental program could be questioned. The distinction between "apparent" and true K_D is critical for interpreting the biological relevance of the results.
- **Resolution test** Provide full experimental details including the biolayer interferometry or surface plasmon resonance protocols, the fitting models, the number of replicates, the standard deviations or confidence intervals for each K_D value, and a discussion of potential avidity or non-specific binding effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "starting-interface-guided BCMA design preserves association kinetics despite substantial sequence divergence; partial diffusion improves TNFα affinity by up to 7.57-fold; and CDR-associated interface remodeling converts an inactive de novo nanobody into binders with apparent K_D values of 4.31 and 5.93 nM."
- **Evidence pointer** Abstract, location not provided
- **Concern** Three distinct capabilities are claimed in a single sentence without any supporting details. For the BCMA design, "preserves association kinetics" is vague and lacks quantitative comparison to the starting interface. For TNFα affinity maturation, the 7.57-fold improvement is reported without the baseline affinity or the number of designs tested. For the nanobody recovery, only two successful examples are mentioned, which is a very small sample size.
- **Why it matters** These claims suggest broad applicability of the method, but each requires specific evidence to be convincing. The BCMA result needs kinetic parameters before and after design. The affinity maturation result needs a clear baseline and demonstration that the improvement is statistically significant. The nanobody recovery result needs a larger sample size or a clear explanation of why two examples are sufficient.
- **Resolution Test** Provide quantitative data for each claim: association and dissociation rate constants for BCMA designs compared to the starting interface, the full affinity maturation trajectory with baseline and improved K_D values for multiple designs, and a larger cohort of recovered nanobodies with their affinities and success rates.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "A unified Atom14 representation and residue-guided sparse all-atom attention enable bidirectional information exchange between residue-level and atom-level representations, coordinating global structure with local atomic detail in a compact model of just 65.9 million parameters."
- **Evidence pointer** Abstract, location not provided
- **Concern** The architectural description is high-level and does not provide sufficient detail to evaluate the novelty or validity of the design. The abstract does not explain how the Atom14 representation is constructed, how the sparse attention pattern is determined, how the bidirectional information exchange is implemented, or how the model avoids common failure modes such as mode collapse or poor diversity in generated sequences.
- **Why it matters** The architectural claims are foundational to the model's performance. Without technical detail, the community cannot assess whether the approach is genuinely novel or whether it would generalize to other protein design tasks. Reproducibility is a core expectation for computational methods.
- **Resolution Test** Provide a detailed methods section with architectural diagrams, pseudocode or a clear mathematical formulation of the attention mechanism, and an ablation study demonstrating the contribution of each architectural component to the reported performance.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, first sentence
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "precise coordination of molecular structure, binding geometry, and experimentally measurable performance" is vague. The term "experimentally measurable performance" is unusual in this context and could be interpreted in multiple ways.
- **Required correction** Clarify what is meant by "experimentally measurable performance" and consider rephrasing to be more specific about the design objectives.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, experimental validation section
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not specify which ten targets were experimentally evaluated or how they were selected. The choice of targets could influence the perceived generalizability of the method.
- **Required correction** List the ten targets and provide a brief justification for their selection, including any criteria related to difficulty or diversity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, model description
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "residue-guided sparse all-atom attention" is not defined. It is unclear how the residue-level guidance is implemented and what makes the attention pattern "sparse."
- **Required correction** Provide a brief explanation of the attention mechanism in the abstract or refer to a figure that illustrates the architecture.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, comparison to prior work
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract claims state-of-the-art performance but does not mention any specific prior methods by name. This makes it difficult for readers to contextualize the claimed improvement.
- **Required correction** Name the specific prior methods that Pallatom2 outperforms and briefly describe the performance gap.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, affinity maturation claim
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "partial diffusion improves TNFα affinity by up to 7.57-fold" is ambiguous. It is unclear what "partial diffusion" means in this context and whether the improvement is in K_D, IC50, or another metric.
- **Required correction** Define "partial diffusion" and specify the exact metric used to quantify the affinity improvement.

## Risk / unsupported claims

- The claim of state-of-the-art in silico screening performance across all nine targets is unsupported without benchmark details and comparison protocols.
- The experimental hit rate of 53.3% is reported without statistical context, baseline comparisons, or per-target breakdowns.
- The picomolar K_D values are presented as "apparent" without measurement details, replicates, or error analysis, making them difficult to interpret.
- The three additional capabilities (interface transfer, affinity maturation, recovery of inactive designs) are asserted without quantitative supporting data.
- The architectural novelty and technical validity of the model cannot be assessed from the abstract alone.
- The generalizability of the method beyond the ten tested targets is not established.
- The claim of "efficient" modeling is not supported by any runtime, memory, or computational cost data.