## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report all-atom molecular dynamics simulations of NSD2 bound to the nucleosome for wild type, E1099K, T1150A, and the double mutant. They claim that global enzyme dynamics are unaltered by mutations, while time-lagged independent component analysis and Markov state modeling reveal differences in free-energy landscapes. Mutants are reported to show reduced SAM-H3K36 distances, modified energy landscapes favoring catalytically competent states, and reorganization of intramolecular contacts. The authors conclude that oncogenic mutations promote hyperactivity through strategic reorganization of conformational dynamics rather than simple destabilization.
- **Visible evidence base** Abstract text only; no simulation details, convergence metrics, error estimates, or experimental comparisons are visible
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, system setup, convergence and sampling validation, free-energy landscape figures, Markov state model validation, contact network analysis, and any quantitative comparison with experimental activity data

## Reviewer
- **Overall assessment** The abstract presents a plausible mechanistic hypothesis linking oncogenic mutations in NSD2 to altered conformational dynamics and enhanced catalytic activity. However, the evidence base is limited to a summary of findings without quantitative details or validation. The central claims, particularly the distinction between global stability and local flexibility, and the causal link between observed conformational changes and hyperactivity, are not fully established from the supplied material. The work is potentially of interest to the structural biology and epigenetics communities, but the current abstract does not provide sufficient evidence to assess technical soundness or reproducibility.
- **Who would be interested in the results, and why** Researchers studying histone methyltransferases, chromatin regulation, and cancer epigenetics would be interested. The proposed framework linking conformational dynamics to oncogenic hyperactivity could inform drug discovery efforts targeting NSD2. Computational biophysicists interested in applying time-lagged independent component analysis and Markov state modeling to protein-nucleosome complexes may also find the methodological approach relevant.
- **Major strengths** The study addresses a clinically relevant question with a clear mechanistic hypothesis. The use of advanced computational methods, including time-lagged independent component analysis and Markov state modeling, is appropriate for studying conformational dynamics. The inclusion of multiple mutants and a double mutant provides a systematic comparison. The interpretation that mutations act through reorganization of dynamics rather than simple destabilization is a nuanced and potentially valuable perspective.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The hypothesis that oncogenic mutations in NSD2 act through conformational dynamics rather than destabilization is not entirely novel, as similar concepts have been proposed for other enzymes, but the specific application to NSD2 is of interest. Scientific importance: The topic is important given the role of NSD2 in cancer, but the abstract does not provide sufficient evidence to establish the significance of the findings beyond a hypothesis. Interdisciplinary readership: The work bridges computational biophysics and cancer biology, which could appeal to a broad audience, but the abstract is written in a specialized manner that may limit accessibility. Technical soundness: Cannot be assessed from the abstract alone; no validation or convergence details are provided. Readability for nonspecialists: The abstract is dense and uses specialized terminology without sufficient context, making it difficult for nonspecialists to follow.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a coherent hypothesis, but the lack of quantitative results, validation, and methodological details prevents a supportive recommendation. The authors should provide full evidence, including convergence analysis, model validation, and quantitative comparisons with experimental data, before the case can be assessed.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "analysis of MD simulations reveals that the global dynamics of the enzymes remain unaltered upon mutations" and that time-lagged independent component analysis and Markov state modeling uncovered "fundamental differences in free-energy landscapes among the variants."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no quantitative measures of global dynamics, such as root-mean-square deviation or fluctuation values, nor any metrics for comparing free-energy landscapes, such as barrier heights or population distributions. Without these data, the claim that global dynamics are unaltered while free-energy landscapes differ is not verifiable.  
- **Why it matters** The central distinction between global stability and local flexibility is a key conclusion. If the global dynamics are not rigorously quantified, the interpretation that mutations act through local reorganization rather than global destabilization is unsupported.  
- **Resolution test** Provide quantitative comparisons of global dynamics metrics (e.g., root-mean-square deviation, root-mean-square fluctuation) with statistical uncertainties, and show free-energy landscape projections with error bars or bootstrapped confidence intervals for each variant.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "the mutant systems demonstrate reduced SAM-H3K36 distances with modified energy landscapes that facilitate transitions or favor prolonged occupancy of catalytically competent states."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No numerical values for SAM-H3K36 distances are provided, nor are the criteria for defining "catalytically competent states" described. The claim of reduced distances is central to the mechanistic interpretation, but without quantitative data and statistical significance testing, it cannot be evaluated.  
- **Why it matters** The reduced substrate distance is the primary structural evidence linking mutations to hyperactivity. If this claim is not robustly supported, the entire mechanistic model is weakened.  
- **Resolution test** Report mean and standard deviation of SAM-H3K36 distances for each variant, with statistical tests (e.g., bootstrap or permutation tests) to establish significance. Define catalytically competent states with explicit geometric criteria and show occupancy times or probabilities.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "the mutations reorganize the network of intramolecular contacts around the catalytic site, SAM-binding pocket, and histone-binding interface, optimizing substrate engagement geometry."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify which contacts are reorganized, how the reorganization was quantified, or whether the changes are statistically significant. The term "optimizing" implies a functional benefit, but no direct link to catalytic activity is demonstrated.  
- **Why it matters** This claim is the mechanistic basis for the proposed "strategic reorganization" model. Without specific contact analysis and validation, the conclusion that mutations optimize geometry is speculative.  
- **Resolution test** Provide a detailed contact map analysis with residue-specific differences between variants, including statistical significance. Show how the reorganized contacts correlate with reduced SAM-H3K36 distances or enhanced catalytic competence.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The authors state that "these findings are consistent with experimental observations of enhanced catalytic activity" and that the results "establish a framework to develop novel therapeutics."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No experimental data are cited or described in the abstract. The claim of consistency with experimental observations is unverifiable without specific references or quantitative comparisons. The therapeutic framework is presented as a conclusion, but no targetable features are identified.  
- **Why it matters** The translational relevance of the work depends on the link to experimental activity data. Without this connection, the significance of the computational findings for cancer biology and drug discovery is overstated.  
- **Resolution test** Cite specific experimental studies with quantitative activity measurements and show direct comparisons between simulated conformational metrics and experimental activity trends. Identify specific conformational features that could be targeted by therapeutics.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract uses specialized terms such as "time-lagged independent component analysis" and "Markov state modeling" without brief explanations, which may limit accessibility for readers outside computational biophysics.  
- **Required correction** Add a brief parenthetical explanation of these methods or their purpose in the context of the study.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "balancing local flexibility with global stability" is vague and could be interpreted in multiple ways. It is unclear what specific metrics support this balance.  
- **Required correction** Clarify which local and global metrics are being referenced and how the balance is quantified.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not mention the simulation length, number of replicates, or force field used, which are essential for assessing the reliability of the molecular dynamics results.  
- **Required correction** Include key simulation parameters, such as total simulation time per variant, number of independent runs, and force field, in the abstract or refer to methods.

## Risk / unsupported claims
- The claim that "global dynamics of the enzymes remain unaltered upon mutations" is unsupported without quantitative metrics.
- The claim that "mutant systems demonstrate reduced SAM-H3K36 distances" is unsupported without numerical data and statistical testing.
- The claim that mutations "optimize substrate engagement geometry" is unsupported without specific contact analysis.
- The claim that findings are "consistent with experimental observations of enhanced catalytic activity" is unverifiable without cited experimental data.
- The claim that the results "establish a framework to develop novel therapeutics" is overstated without identification of specific targetable features.