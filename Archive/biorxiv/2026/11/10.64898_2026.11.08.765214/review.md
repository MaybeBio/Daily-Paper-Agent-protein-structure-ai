## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors present HV-MultiScaleGNN, a topology-driven multi-scale graph neural network framework for host-virus protein-protein interaction (HV-PPI) prediction. The framework operates exclusively on the topology of a heterogeneous interaction network, integrating the human interactome with experimentally validated HV-PPIs. Three graph representation strategies are evaluated: Local view (one-hop relation-aware graph attention), Global view (propagation-based neighbourhood aggregation), and an integrated Local+Global view. The Local view achieved the best discriminative performance (AUROC = 0.9444, AUPRC = 0.9422), the Global view exhibited the lowest expected calibration error (ECE = 0.0379), and the integrated view provided strong predictive performance (AUROC = 0.9378, AUPRC = 0.9356). Comparative evaluation against representative graph representation learning methods showed competitive performance. Additional analyses include protein-protein docking, atomistic-level understanding, and GO and KEGG enrichment of selected host proteins.
- **Visible evidence base** Abstract text only; no methodological details, dataset descriptions, baseline specifications, or quantitative comparisons beyond the reported metrics are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset construction details, baseline method specifications, hyperparameter settings, statistical significance tests, docking and enrichment analysis details, and code availability

## Reviewer

- **Overall assessment** The abstract describes a potentially useful framework for HV-PPI prediction that addresses a relevant problem in virology and antiviral research. The central idea of comparing multiple graph representation strategies within a unified framework is sensible and could be of interest to the computational biology community. However, the abstract alone provides insufficient information to evaluate the technical soundness of the approach, the validity of the experimental design, or the robustness of the reported results. Several claims, particularly regarding comparative performance and the biological analyses, cannot be assessed without access to the full manuscript. The work appears promising in scope but the evidence base provided is too limited to establish the case.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-protein interaction prediction, graph neural network applications in biology, and host-pathogen interaction modelling would be the primary audience. Researchers studying viral infection mechanisms and those involved in antiviral drug discovery may also find the framework useful as a prioritization tool for experimental validation. The systematic comparison of graph representation strategies could inform methodological choices in related prediction tasks.
- **Major strengths** The problem addressed is biologically and clinically relevant. The framework's design to operate exclusively on network topology, without requiring sequence or structure features, is a distinctive and potentially practical advantage given the incompleteness of such data for many viral and host proteins. The systematic evaluation of three complementary graph representation strategies within a single framework is a methodologically thoughtful approach. The inclusion of calibration metrics alongside discrimination metrics indicates attention to model reliability, which is important for experimental prioritization.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The framework achieves strong predictive performance (AUROC = 0.9444, AUPRC = 0.9422 for the Local view) on large-scale HV-PPI datasets.
  - **Evidence pointer** Abstract, Results section (location not provided)
  - **Concern** The abstract reports performance metrics but provides no information about the datasets used, including their size, composition, source, train-test split methodology, or the proportion of positive to negative examples. Without this information, the reported AUROC and AUPRC values cannot be interpreted meaningfully. AUPRC is particularly sensitive to class imbalance, and the reported values may reflect dataset characteristics rather than model quality.
  - **Why it matters** Predictive performance metrics are only meaningful in the context of the evaluation dataset and protocol. If the dataset is small, imbalanced, or contains leakage between training and test sets, the reported metrics could be misleading. The claim of strong predictive performance cannot be verified or compared to other methods without this essential context.
  - **Resolution test** Provide full dataset descriptions including the number of positive and negative interactions, the source databases, the version of the human interactome used, the temporal or random split strategy, and the ratio of positive to negative examples. Report performance metrics stratified by interaction type or host protein category if applicable.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** Comparative evaluation against representative graph representation learning methods showed competitive predictive performance.
  - **Evidence pointer** Abstract, Results section (location not provided)
  - **Concern** The abstract states that the framework showed competitive performance against representative baselines but provides no information on which baselines were used, how they were configured, whether hyperparameter tuning was performed fairly across methods, or the magnitude of performance differences. Without this information, the comparative claim is unverifiable.
  - **Why it matters** A central claim of the work is that the proposed framework performs competitively relative to existing methods. If baselines were not carefully tuned or if the comparison is limited to a small set of methods, the claim of competitiveness may not hold in broader contexts. The reader cannot assess whether the comparison was fair or comprehensive.
  - **Resolution test** List all baseline methods with their configurations and hyperparameter tuning procedures. Report performance of all methods on identical train-test splits. Provide statistical significance tests (e.g., DeLong test for AUROC differences) and confidence intervals for all reported metrics.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The framework operates exclusively on the topology of a heterogeneous interaction network and enables relation-specific link prediction without relying on sequence- or structure-derived features.
  - **Evidence pointer** Abstract, Methods section (location not provided)
  - **Concern** The abstract provides no details on the model architecture, including the number of layers, hidden dimensions, attention heads, aggregation functions, or the optimization procedure. The graph construction process, including how the heterogeneous network is built and how node and edge types are encoded, is not described. The training procedure, including loss functions, regularization, and early stopping criteria, is absent.
  - **Why it matters** Reproducibility is a fundamental requirement for computational research. Without architectural and training details, other researchers cannot implement or build upon the proposed framework. The claim of a novel framework cannot be evaluated without understanding what exactly is novel relative to existing GNN-based link prediction methods.
  - **Resolution test** Provide complete architectural specifications, hyperparameter values, optimization details, and the exact procedure for constructing the heterogeneous network. Release code and trained models in a public repository.
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evidence quality
  - **Claim pointer** Interfacial interactions were identified using protein-protein docking and atomistic-level understanding was explored. GO and KEGG enrichment provided additional functional insights into the selected host proteins.
  - **Evidence pointer** Abstract, Results section (location not provided)
  - **Concern** The abstract mentions docking, atomistic-level analysis, and GO/KEGG enrichment as additional analyses but provides no results from these analyses. It is unclear how many protein complexes were docked, whether docking predictions were validated experimentally or through known structures, what the enrichment results showed, or how these analyses relate to the core prediction framework.
  - **Why it matters** These analyses are presented as part of the contribution but their findings are not summarized. The reader cannot assess whether these analyses add meaningful biological insight or are peripheral to the main contribution. If the docking and enrichment results are used to support the utility of the framework, their absence weakens the overall case.
  - **Resolution test** Summarize key findings from the docking and enrichment analyses, including the number of interactions analyzed, the confidence of docking predictions, and the most significant GO terms and KEGG pathways identified. Clarify how these analyses validate or extend the prediction results.
  
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The framework helps experimental researchers to delineate novel HV-PPIs.
  - **Evidence pointer** Abstract, Conclusion section (location not provided)
  - **Concern** The abstract claims practical utility for experimental researchers but provides no evidence of prospective validation, such as experimental confirmation of novel predictions, case studies demonstrating the framework's utility in a discovery setting, or comparison with experimentally confirmed interactions discovered after the training data cutoff.
  - **Why it matters** The claim of practical utility is a strong one that requires evidence beyond retrospective performance metrics. Many computational prediction methods perform well in retrospective evaluations but fail to provide actionable predictions in practice. Without prospective validation or case studies, this claim remains speculative.
  - **Resolution test** Provide case studies of novel predictions that were subsequently validated experimentally, or demonstrate the framework's utility through a retrospective analysis where predictions are compared to interactions confirmed after the training data cutoff date.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, Methods description
  - **Evidence pointer** Abstract, paragraph 1 (location not provided)
  - **Issue** The phrase "topology-driven" is used to describe the framework but its specific meaning in this context is not defined. It could refer to the exclusive use of network topology as input features, or to a topology-aware model architecture, or both.
  - **Required correction** Clarify what "topology-driven" means in the context of the framework, either by defining the term explicitly or by rephrasing to avoid ambiguity.
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, Results description
  - **Evidence pointer** Abstract, paragraph 1 (location not provided)
  - **Issue** The abstract states that the Local view achieved the best discriminative performance while the integrated view provided "consistently strong" performance. The basis for the "consistently strong" characterization is not explained, and it is unclear whether the differences between the Local and integrated views are statistically significant.
  - **Required correction** Clarify the criteria used to characterize the integrated view as "consistently strong" and report whether performance differences between strategies are statistically significant.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract, Evaluation description
  - **Evidence pointer** Abstract, paragraph 1 (location not provided)
  - **Issue** The abstract mentions evaluation using "discrimination, calibration, and ranking metrics" but only reports AUROC, AUPRC, and ECE. The ranking metrics are not specified.
  - **Required correction** Specify which ranking metrics were used and report their values, or remove the reference to ranking metrics if they are not central to the evaluation.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Abstract, Data description
  - **Evidence pointer** Abstract, paragraph 1 (location not provided)
  - **Issue** The abstract refers to "large-scale HV-PPIs datasets" but does not specify the number of interactions, the number of unique host and viral proteins, or the data sources.
  - **Required correction** Provide basic dataset statistics in the abstract or indicate where these details can be found in the full manuscript.
  
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract, Availability statement
  - **Evidence pointer** Abstract, end (location not provided)
  - **Issue** No statement is provided regarding code or data availability.
  - **Required correction** Add a data and code availability statement to the abstract or indicate that this information is provided in the full manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset description and evaluation protocol missing), R1-M2 (baseline comparison details missing), R1-M3 (architectural and training details missing). These three concerns collectively prevent assessment of whether the reported performance is meaningful, whether the comparative claims are valid, and whether the framework can be reproduced.
- **Assessment against Nature-style criteria** 
  - Originality: The idea of systematically comparing multiple graph representation strategies within a single framework for HV-PPI prediction has some novelty, but graph neural networks for link prediction in biological networks are well established. The specific contribution relative to existing work cannot be fully assessed from the abstract.
  - Scientific importance: HV-PPI prediction is a relevant problem with potential implications for understanding viral infection and antiviral development. However, the abstract does not demonstrate that the framework provides a substantial advance over existing methods beyond competitive performance.
  - Interdisciplinary readership: The work sits at the intersection of machine learning, network biology, and virology. The abstract is written in a way that is largely accessible to computational readers, but the biological significance of the results is not articulated in a way that would engage a broad readership.
  - Technical soundness: Cannot be assessed from the abstract alone. The missing details on datasets, baselines, and architecture preclude evaluation of technical rigor.
  - Readability for nonspecialists: The abstract is reasonably clear for readers familiar with graph neural networks and PPI prediction, but terms such as "relation-aware graph attention" and "propagation-based neighbourhood aggregation" are used without explanation. The biological motivation and potential impact could be articulated more clearly for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible framework and reports strong performance metrics, but the absence of dataset details, baseline comparisons, and architectural information prevents verification of the central claims. The work may be technically sound and of interest to the community, but the evidence provided is insufficient to support the claims made. A full review of the complete manuscript would be required to determine whether the technical concerns can be resolved.

## Risk / unsupported claims
- The claim of "competitive predictive performance" against representative baselines is unsupported because no baseline methods, configurations, or quantitative comparisons are provided in the abstract.
- The claim that the framework "helps experimental researchers to delineate novel HV-PPIs" is unsupported because no prospective validation or case studies are described.
- The reported AUROC and AUPRC values cannot be interpreted without knowledge of the dataset composition, class balance, and evaluation protocol.
- The claim that the framework operates "exclusively on the topology of a heterogeneous interaction network" is stated but the graph construction process and the types of information encoded in the network are not described.
- The biological analyses (docking, atomistic-level understanding, GO/KEGG enrichment) are mentioned but no results are reported, making their contribution unassessable.
- The novelty of the framework relative to existing GNN-based link prediction methods cannot be evaluated from the abstract.