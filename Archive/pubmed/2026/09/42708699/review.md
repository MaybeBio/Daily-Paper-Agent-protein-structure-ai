## Review setup
- **Input scope** Full manuscript (abstract, introduction, theory, results and discussion, conclusion, methods, supplementary material description)
- **Assessment boundary** Scientific content, methodology, evidence, and claims as presented in the manuscript
- **Shared manuscript claim summary** The authors present a fully automated framework that transforms enhanced sampling trajectories into human-readable representations of protein dynamics by combining enhanced sampling along collective variables derived from frequency-selective anharmonic mode analysis with a post hoc analysis of biased trajectories using weighted dynamic cross-correlation matrices. The method identifies residue pairs and domains exhibiting correlated and anti-correlated motions, yielding simple domain-domain distances that serve as physically interpretable collective variables. The approach is applied to five proteins, including KRAS and HIV-1 protease, and is claimed to consistently identify biologically relevant domains and motions without prior system-specific knowledge.
- **Visible evidence base** Abstract, introduction, theory section, results and discussion (including Figures 1-5 described in text), conclusion, methods, supplementary material description
- **Missing materials affecting confidence** Figures 1-5 and Supplementary Figures S1-S3 are described but not provided; no raw data, simulation trajectories, or code outputs are included; no statistical analysis details beyond error propagation description; no comparison to alternative methods for domain identification

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially useful framework for automating the extraction of interpretable collective variables from enhanced sampling simulations. The core idea of using weighted dynamic cross-correlation matrices from biased trajectories to identify domain-domain distances is novel and addresses a genuine need in the field. However, the evidence provided is insufficient to fully evaluate the method's robustness, generalizability, and superiority over existing approaches. The lack of provided figures and detailed quantitative comparisons limits the assessment of the claims.
- **Who would be interested in the results, and why** Computational biophysicists and chemists working on enhanced sampling methods, protein dynamics, and collective variable design would be interested. The method offers a potential solution to the interpretability problem of complex collective variables, which is a recognized challenge in the field. Researchers using machine learning-derived collective variables may find the approach particularly relevant for translating complex variables into simple geometric descriptors.
- **Major strengths** 1. The core concept of using weighted DCCM from biased trajectories to automatically identify interpretable domain-domain distances is novel and addresses a significant practical problem. 2. The method is designed to be fully automated and does not require prior system-specific knowledge, which is a major advantage for high-throughput applications. 3. The application to five diverse proteins demonstrates potential generalizability. 4. The approach of minimizing correlations between the two identified domain pairs is a thoughtful design choice that maximizes independent information.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The method "consistently identifies biologically relevant domains and motions without prior system-specific knowledge" and "reproduces known conformational states with low statistical uncertainty while maximizing independent dynamical information."
  - **Evidence pointer** Results and Discussion section, Figures 1-5 (not provided)
  - **Concern** The manuscript claims that the method consistently identifies biologically relevant domains and motions, but the evidence for this claim is insufficiently presented. The main text focuses exclusively on KRAS, with results for the other four proteins relegated to the Supporting Information, which is not provided. Without seeing the figures (Figures 1-5 and Supplementary Figures S1-S3), it is impossible to evaluate whether the identified domains are indeed biologically relevant, whether the free energy surfaces reproduce known states, or whether the statistical uncertainties are as low as claimed. The description of the KRAS results is qualitative and lacks quantitative validation metrics.
  - **Why it matters** The central claim of the paper is that the method works across multiple systems and produces meaningful results. Without visual evidence and quantitative comparisons to known structures or experimental data, the reader cannot assess whether the method is genuinely effective or merely coincidental for KRAS. The lack of provided figures makes the manuscript's core evidence inaccessible.
  - **Resolution test** Provide all figures (Figures 1-5 and Supplementary Figures S1-S3) with clear labels, legends, and quantitative annotations. Include quantitative metrics for domain identification accuracy (e.g., overlap with known functional domains measured by Jaccard index or similar), free energy surface comparison to literature values (e.g., RMSD of free energy minima positions), and statistical uncertainty quantification across all five systems.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** "Our approach utilizes weighted averages over biased trajectories to compute a dynamic cross correlation matrix (DCCM) from which we extract residues and domains that move collectively or against each other using a simple algorithm."
  - **Evidence pointer** Theory section, Results and Discussion section
  - **Concern** The method for identifying domains relies on a threshold value of +0.5 for selecting correlated residues, but the authors state that "alternative choices for the correlation threshold can alter the balance of inclusiveness or stringency in the selection of correlated residues. However this was not tested here." This is a critical methodological gap. The sensitivity of the domain identification to this threshold is not explored, and there is no justification for why +0.5 is the appropriate value. Similarly, the algorithm for selecting b1 and b2 residues prioritizes lack of correlation with a1/a2 but does not prioritize collective motion, yet the authors claim that "despite not prioritizing collective motion in the selection of residues b1 and b2, we frequently observed that both are part of collectively moving domains." This observation is not quantified or systematically validated.
  - **Why it matters** The threshold and selection criteria are central to the method's performance. Without testing the sensitivity to these parameters, the robustness of the method is unknown. Users cannot be confident that the method will work for new systems without extensive manual tuning. The claim that b1/b2 are "frequently" part of collectively moving domains is vague and requires quantitative assessment.
  - **Resolution test** Perform a systematic sensitivity analysis of the correlation threshold (e.g., testing values from 0.3 to 0.7 in increments of 0.05) and report how domain composition, free energy surfaces, and biological relevance change. Quantify the frequency with which b1/b2 residues are part of collectively moving domains across all five systems, using a consistent definition. Provide a statistical measure (e.g., percentage of systems where b1/b2 are in domains of size >3 residues).

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Comparison to existing methods
  - **Claim pointer** The method "enables systematic recasting of complex CVs into simple geometric descriptors without loss of essential dynamics" and "its generality and automation make it broadly applicable for interpreting enhanced sampling simulations."
  - **Evidence pointer** Results and Discussion section, Conclusion
  - **Concern** The manuscript does not provide any quantitative comparison to alternative methods for identifying interpretable collective variables or domain motions. There is no comparison to standard approaches such as principal component analysis (PCA), time-lagged independent component analysis (TICA), or other domain identification methods (e.g., community analysis, dynamical network analysis). The claim that the method "maximizes independent dynamical information" is not supported by any quantitative metric (e.g., mutual information, correlation coefficients between the identified variables). Without such comparisons, it is unclear whether the proposed method offers advantages over existing techniques.
  - **Why it matters** The field already has multiple methods for identifying collective variables and domain motions. To establish the value of this new method, the authors must demonstrate that it performs as well as or better than existing approaches in terms of accuracy, interpretability, automation, or computational efficiency. The lack of comparison undermines the claim of broad applicability and novelty.
  - **Resolution test** Compare the identified domains and free energy surfaces to those obtained from PCA, TICA, or other relevant methods applied to the same simulation data. Provide quantitative metrics such as: (1) overlap of identified domains with known functional regions, (2) statistical uncertainty of free energy surfaces, (3) computational cost, (4) degree of automation required. Show that the proposed method produces results that are at least as good as existing methods, with clear advantages in interpretability or automation.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and code availability
  - **Claim pointer** "Source code and scripts for FRESEAN mode analysis, well-tempered metadynamics simulations with GROMACS and PLUMED, and the weighted DCCM analysis are available in our GitHub repository."
  - **Evidence pointer** Code Availability section
  - **Concern** While the authors state that code is available, the manuscript does not provide any details about the implementation of the weighted DCCM analysis algorithm. The pseudo-code in the Theory section is helpful but lacks specifics about data structures, convergence criteria, or handling of edge cases (e.g., what happens if no residue pair meets the anti-correlation criteria? What if the DCCM has no negative elements?). The GitHub repository is mentioned but not described in terms of documentation, testing, or ease of use. Without a clear, reproducible implementation, other researchers cannot independently verify or build upon the method.
  - **Why it matters** Reproducibility is a cornerstone of computational science. The method's utility depends on other researchers being able to apply it to their own systems. Insufficient implementation details and lack of documented, tested code limit the method's adoption and the ability to validate the claims.
  - **Resolution test** Provide a detailed description of the algorithm implementation, including data structures, convergence criteria, and error handling. Ensure the GitHub repository includes: (1) a README with installation and usage instructions, (2) example input/output files for at least one system, (3) unit tests for the DCCM analysis algorithm, (4) a list of dependencies with version numbers. Consider depositing the code in a permanent repository (e.g., Zenodo) with a DOI.

- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Theory section, Equation 1
  - **Evidence pointer** location not provided
  - **Issue** The notation in Equation 1 uses "rts" for coordinates at time ts, but the subscript "s" is not defined. It appears that "s" indexes time steps, but this is not explicitly stated.
  - **Required correction** Define the index "s" explicitly (e.g., "where s indexes the time steps of the simulation trajectory") and ensure consistent notation throughout the Theory section.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results and Discussion section
  - **Evidence pointer** location not provided
  - **Issue** The authors state that "the lowest free energy states are generally sampled most reliably, even in biased simulations, and thus feature the lowest statistical uncertainty." This is a general statement that may not hold for all enhanced sampling methods. For well-tempered metadynamics, the bias potential reduces the barriers but does not guarantee uniform sampling of all low-energy states.
  - **Required correction** Qualify the statement to reflect the specific enhanced sampling method used (well-tempered metadynamics) and provide a brief explanation of why low-energy states are sampled reliably in this context.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Results and Discussion section
  - **Evidence pointer** location not provided
  - **Issue** The description of the KRAS free energy surface (Figure 5) is detailed but difficult to follow without the figure. The text describes minima at specific dA and dB values, but the reader cannot visualize the landscape.
  - **Required correction** Include a brief description of the free energy surface features in the figure caption and consider adding a schematic or simplified representation in the text to aid understanding.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Methods section
  - **Evidence pointer** location not provided
  - **Issue** The Methods section states that "the two lowest-frequency vibrational modes (modes 7 and 8 at zero frequency) were chosen as collective variables (CVs) for enhanced sampling." The numbering "modes 7 and 8" is not explained. It is unclear why modes 1-6 are excluded.
  - **Required correction** Explain the mode numbering convention (e.g., "modes 1-6 correspond to translational and rotational degrees of freedom and are excluded") or provide a reference to the original FRESEAN method for details.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Conclusion
  - **Evidence pointer** location not provided
  - **Issue** The conclusion mentions that the method can be applied to "any set of simulations that have been biased along complex CVs that are challenging to interpret directly." However, the method relies on the availability of weights from the bias potential (Equation 2), which may not be straightforward to compute for all enhanced sampling methods (e.g., replica exchange, umbrella sampling with multiple windows).
  - **Required correction** Clarify the scope of applicability by specifying which enhanced sampling methods are compatible with the weighted DCCM analysis, or provide guidance on how to compute weights for other methods.

- **Technical failings that need to be addressed before the case is established** R1-M1 (evidence sufficiency), R1-M2 (methodological validation), R1-M3 (comparison to existing methods)
- **Assessment against Nature-style criteria** 
  - **Originality**: The concept of using weighted DCCM from biased trajectories to automatically extract interpretable domain-domain distances is novel and addresses a recognized problem. However, the individual components (DCCM, metadynamics, FRESEAN mode analysis) are established methods. The originality lies in their combination and the specific algorithm for domain identification.
  - **Scientific importance**: The problem of interpreting complex collective variables is important for the field of enhanced sampling. If validated, the method could facilitate broader adoption of advanced CV-based methods by making results more accessible. However, the importance is diminished by the lack of quantitative validation and comparison to existing methods.
  - **Interdisciplinary readership**: The method is primarily of interest to computational biophysicists and chemists. The "human-readable" aspect could potentially attract experimentalists, but the current presentation is too technical and lacks sufficient validation to be accessible to a broader audience.
  - **Technical soundness**: The theoretical framework appears sound, but the lack of provided figures, sensitivity analysis, and comparison to alternatives prevents a full assessment of technical soundness. The threshold selection and algorithm for b1/b2 selection are not adequately justified.
  - **Readability for nonspecialists**: The manuscript is well-written and the logic is clear, but the heavy reliance on figures that are not provided and the technical nature of the methods limit readability for nonspecialists. The abstract and introduction effectively motivate the problem.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising conceptual framework, but the evidence is insufficient to support the central claims. The lack of provided figures, sensitivity analysis, and comparison to existing methods are critical gaps. The authors should address these concerns before the manuscript can be considered for publication.