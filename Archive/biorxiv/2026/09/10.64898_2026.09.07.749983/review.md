## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusion, supplementary notes) as provided
- **Assessment boundary** Scientific and technical evaluation of the described method, experimental design, results, and claims; no assessment of code functionality or web server availability beyond stated claims
- **Shared manuscript claim summary** The authors present ForceFlowAb, a physics-aware mixture-of-experts flow-matching framework for antigen-conditioned antibody CDR sequence-structure co-design. They claim improved antibody-antigen interaction energies compared to FlowDesign and Diffab, with competitive sequence recovery, structural accuracy, and interface quality, supported by Rosetta-based metrics and AlphaFold 3 evaluation.
- **Visible evidence base** Abstract, full introduction, methods sections 2.1-2.4, results sections 3.1-3.7, conclusion, supplementary note on training, case study description
- **Missing materials affecting confidence** Full figures and tables (Fig. 1-6, Supplementary Figs S1-S8, Tables S1-S4) are referenced but not provided; detailed mathematical formulations for loss functions and interpolation are partially described but equations are not fully shown; no statistical analysis details (e.g., significance testing, confidence intervals) are provided; no comparison of computational cost or runtime against baselines

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in antibody engineering with a technically plausible combination of established components: flow matching, mixture-of-experts routing, and differentiable force-field guidance. The motivation is clearly articulated, and the methodological choices are reasonable. However, the evidence presented is insufficient to fully establish the claimed advantages. Key results are described qualitatively with reference to figures that are not available in the provided material, and critical details regarding statistical significance, hyperparameter sensitivity, and the specific contribution of each component are lacking. The work is potentially of interest to the computational antibody design community, but the current evidence base does not fully support the strength of the claims made.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on antibody design and generative protein models would be the primary audience. The combination of flow matching with mixture-of-experts and physics-based guidance is a methodological direction that could inform future work in protein generation beyond antibodies. Researchers developing structure-based generative models for proteins may find the architectural choices and the integration of energy-based guidance during sampling of interest.
- **Major strengths**
  1. The problem is well-motivated and addresses a clear limitation in existing generative antibody design methods, namely the lack of explicit physical guidance and adaptive modeling of heterogeneous interfaces.
  2. The methodological combination of flow matching, mixture-of-experts, and differentiable force-field guidance is novel in the context of antibody CDR design and represents a sensible integration of complementary ideas.
  3. The evaluation includes multiple complementary metrics (Rosetta energy, IMP, DockQ, AAR, Cα RMSD, AF3-based scores), which is appropriate for assessing different aspects of design quality.
  4. The authors acknowledge the limitation of not including AbX and Ab-Diffuser due to practical constraints, which is transparent.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that ForceFlowAb achieved "more favorable antibody-antigen interaction energies than FlowDesign and Diffab, with improvement rates (IMP) of 46.5% versus 35.0% and 35.5%, respectively" for CDR-H3 design.
  - **Evidence pointer** Section 3.3, Fig. 2, Supplementary Table S2
  - **Concern** The quantitative results are presented in figures and supplementary tables that are not available in the provided material. The text describes trends ("tended to produce lower ΔΔG values") but does not provide the actual distributions, variances, or statistical significance of the differences. Without access to the underlying data, it is impossible to assess whether the reported IMP differences are robust or within noise. Furthermore, the definition of IMP and how it relates to the distribution of energies across 100 sampled candidates is not fully specified.
  - **Why it matters** The central claim of the paper rests on the superiority of ForceFlowAb over baselines in terms of interaction energy. If the differences are not statistically significant or are sensitive to the specific test set or evaluation protocol, the main conclusion would be weakened. The current presentation does not allow the reader to verify this.
  - **Resolution test** Provide the full data distributions for ΔΔG, IMP, DockQ, and AAR for all methods, including measures of variance (e.g., standard deviation, interquartile range) and results of appropriate statistical tests (e.g., Wilcoxon signed-rank test) comparing ForceFlowAb to each baseline. Clarify the exact definition of IMP and how it is computed from the 100 sampled candidates.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the "differentiable force-guidance mechanism steers generated CDR conformations towards energetically favourable antibody-antigen interfaces during sampling" and that this contributes to improved results.
  - **Evidence pointer** Section 2.3, Section 3.7, Fig. 6
  - **Concern** The description of the force-guidance mechanism is incomplete. The text states that a reduced MadraX-based energy is used, retaining only backbone hydrogen-bond energy, backbone entropy, and peptide-bond violation penalty, but the rationale for selecting these specific terms is not provided. The gradient is applied only to Cα coordinates, which is a significant simplification, and the potential consequences for side-chain placement and overall structural realism are not discussed. The ablation study (Section 3.7) is described only qualitatively; the actual magnitude of the degradation when force guidance is removed is not reported.
  - **Why it matters** The contribution of the physics-based guidance is a key novelty of the method. If the mechanism is not well-justified or its effect is marginal, the added complexity may not be warranted. The current description does not allow the reader to understand the design choices or assess the robustness of the approach.
  - **Resolution test** Provide a more detailed description of the force-guidance implementation, including the exact energy terms, their functional forms, and the rationale for their selection. Report quantitative results from the ablation study, including the specific changes in metrics when force guidance is removed. Discuss the limitations of applying gradients only to Cα atoms and the potential impact on side-chain conformations.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The claim that the method can be reproduced from the provided description and that the source code is available.
  - **Evidence pointer** Section 2.3, Section 2.4, Supplementary Note 1, Data availability
  - **Concern** While the overall architecture is described, several critical implementation details are missing. The exact architecture of the Input Frame Encoder, the number of IPA and Transformer blocks in the CDR Embedder, the specific dimensions of the hidden layers, and the precise formulation of the loss functions are not fully specified. The training procedure is described in Supplementary Note 1, but the hyperparameter search strategy, if any, is not mentioned. The code is stated to be available, but it is not possible to verify its functionality or completeness from the manuscript.
  - **Why it matters** Reproducibility is a core requirement for computational methods. Without complete implementation details, other researchers cannot build upon or verify the method. The availability of code mitigates this to some extent, but the manuscript should be self-contained enough to allow understanding and reimplementation.
  - **Resolution test** Provide a complete specification of all architectural components, including layer counts, dimensions, and activation functions. Include the full mathematical formulation of all loss terms. Describe the hyperparameter selection process and provide the final hyperparameter values. Ensure the code repository is complete, documented, and includes instructions for reproduction.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evaluation rigor
  - **Claim pointer** The claim that "AlphaFold 3 evaluation further supported the structural compatibility of the generated sequences" and the use of AF3-based metrics (ipTM, pLDDT) as an independent assessment.
  - **Evidence pointer** Section 3.5, Fig. 4, Supplementary Figs S3-S4
  - **Concern** The use of AF3 as an evaluation tool is reasonable, but the interpretation of the results is unclear. The authors report a "joint confidence pass rate" of 50% for ForceFlowAb versus 42% for Diffab, but the significance of this difference is not assessed. Moreover, the relationship between AF3 confidence scores and actual experimental binding affinity or structural validity is not established. The authors do not discuss potential biases in AF3 evaluation, such as the model potentially favoring sequences similar to its training distribution.
  - **Why it matters** The AF3-based assessment is presented as supporting evidence for the method's utility. If the differences are not significant or the metric is not well-calibrated, this support is weak. The reader needs to understand the limitations of this evaluation approach.
  - **Resolution test** Provide statistical analysis of the AF3-based metrics, including confidence intervals or significance tests. Discuss the known limitations of using AF3 confidence scores as a proxy for experimental validity. Consider including additional independent evaluations, such as comparison to experimentally validated antibodies or docking-based assessments.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.2, Task formulation
  - **Evidence pointer** Section 2.2
  - **Issue** The notation for the interpolation of amino acid identities and coordinates is described but the actual equations are not shown. The text states "Amino acid identities and Cα coordinates are interpolated linearly" but does not provide the specific formulas.
  - **Required correction** Include the explicit mathematical expressions for the linear interpolation of both categorical (amino acid) and continuous (coordinate) variables, and clarify how the interpolation handles the discrete nature of amino acid identities.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.1, Evaluation settings
  - **Evidence pointer** Section 3.1
  - **Issue** The exclusion of AbX and Ab-Diffuser is mentioned, but the specific reasons are only briefly stated. For AbX, the lack of a training pipeline is cited, but it is unclear why the provided pretrained checkpoints could not be used for evaluation. For Ab-Diffuser, the absence of an official implementation is stated, but it is not clear if any unofficial implementations were considered.
  - **Required correction** Provide more detail on why the pretrained AbX model could not be used under the unified evaluation protocol, and clarify whether any alternative implementations of Ab-Diffuser were evaluated or considered.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 3.3, Section 3.4
  - **Evidence pointer** Section 3.3, Section 3.4
  - **Issue** The results are described in terms of trends ("tended to produce lower", "showed a higher") without reporting the number of test cases, the variance across test cases, or any statistical significance measures.
  - **Required correction** Report the number of test complexes, the distribution of results across test cases, and the results of appropriate statistical tests for all key comparisons.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.3, Force Guidance module
  - **Evidence pointer** Section 2.3
  - **Issue** The description of the force-guidance application states it is applied "in the later phase of the sampling trajectory (specifically, steps 70-80)" but does not explain why this specific range was chosen or how sensitive the results are to this choice.
  - **Required correction** Provide a rationale for the choice of steps 70-80 and include a sensitivity analysis showing the effect of varying this range on the final results.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.6, Expert selection analysis
  - **Evidence pointer** Section 3.6, Fig. 5
  - **Issue** The expert selection analysis is described qualitatively, and the implications of the observed patterns are not discussed in depth. The authors state that "expert selection depends on the input CDR environment" but do not elaborate on what this means for the method's interpretability or design.
  - **Required correction** Provide a more detailed interpretation of the expert selection patterns, including what specific features or sequence motifs are associated with different expert preferences, and discuss the implications for understanding CDR sequence-structure relationships.
- **Technical failings that need to be addressed before the case is established**
  1. Lack of statistical significance testing for all key comparisons between ForceFlowAb and baselines (R1-M1).
  2. Incomplete description of the force-guidance mechanism and its ablation results (R1-M2).
  3. Insufficient implementation details for reproducibility (R1-M3).
  4. Unclear interpretation and limitations of AF3-based evaluation (R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of flow matching, mixture-of-experts, and force-based guidance is novel in the context of antibody CDR design, but each component is established in the broader generative modeling literature. The specific integration and application to antibody design represents incremental novelty rather than a fundamentally new paradigm.
  - **Scientific importance** Moderate. Antibody design is an important application area, and improvements in computational methods could have practical impact. However, the demonstrated improvements over baselines are modest and not fully established statistically. The method does not address fundamental limitations of existing approaches beyond combining known techniques.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to computational biologists and machine learning researchers working on protein design. The methods and evaluation are highly specialized, and the potential broader impact on fields such as immunology or drug discovery is not demonstrated.
  - **Technical soundness** The approach is technically plausible, but the evidence presented is insufficient to fully assess its soundness. Key implementation details are missing, and the statistical rigor of the evaluation is inadequate. The ablation study is described only qualitatively.
  - **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with generative models, protein structure, and antibody biology. The abstract is accessible, but the methods and results sections would be challenging for readers outside the immediate field.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a plausible method with a reasonable motivation, but the evidence base is insufficient to support the strength of the claims. The lack of statistical analysis, incomplete method description, and qualitative presentation of key results prevent a definitive assessment of the method's value. The authors should be encouraged to resubmit after addressing the major concerns, particularly providing full quantitative results with statistical analysis, complete implementation details, and a more rigorous ablation study.