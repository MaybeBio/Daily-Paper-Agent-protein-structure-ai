## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the supplied abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a comparative computational study of two AAA+ ATPases, katanin and ClpB, using molecular dynamics simulations, machine learning, and bioinformatic analysis. They claim that nucleotide and substrate binding restrict the conformational landscapes of both systems, that ligand-specific conformations occur in ClpB, that SHAP-based feature ranking identifies allosteric contributions from regions adjacent to the nucleotide-binding site and pore loops, and that amino acid-level analysis reveals intra-ring cooperativity modulating long-distance communication within AAA+ protomers.
- **Visible evidence base** Abstract text only; no methodological details, simulation parameters, validation metrics, or quantitative results are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation convergence criteria, force field parameters, machine learning model specifications, statistical analyses, and any control or validation experiments

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting comparative computational study of allosteric regulation in two AAA+ ATPases. The combination of molecular dynamics, machine learning, and bioinformatic analysis is timely and could appeal to a biophysics audience. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the simulations, the validity of the machine learning approach, or the robustness of the biological conclusions. Several claims are stated without quantitative support, and the relationship between the computational findings and experimentally established allosteric mechanisms is not articulated. The work may be of interest to specialists in AAA+ ATPase biology and computational biophysics, but the case for the central conclusions is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying AAA+ ATPase mechanisms, particularly those focused on allosteric regulation, protein remodeling, microtubule severing, and protein disaggregation. Computational biophysicists interested in combining molecular dynamics with machine learning for feature attribution in protein conformational analysis would also find the methodological approach relevant. The comparative design between a single-domain and a double-domain AAA+ protein may interest those studying evolutionary and functional divergence within the AAA+ superfamily.
- **Major strengths** The comparative design between katanin and ClpB is well motivated, as it allows separation of clade 3-specific mechanisms from clade 5-specific contributions. The integration of molecular dynamics with machine learning and SHAP-based interpretability is a modern and potentially powerful approach for identifying allosteric determinants. The focus on both nucleotide and substrate effects on conformational landscapes addresses a central question in AAA+ ATPase function.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The authors claim that molecular dynamics simulations reveal restricted conformational landscapes upon nucleotide and substrate binding, with ligand-specific conformations in ClpB.  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** No simulation details are provided, including system construction, force field, simulation length, sampling methodology, convergence assessment, or number of replicas. Without these, the conformational landscape claims cannot be evaluated for statistical robustness or physical reliability.  
  - **Why it matters** Conformational landscape comparisons are only meaningful if the sampling is demonstrably converged and unbiased. Insufficient sampling or inadequate equilibration could produce apparent ligand-induced restriction that is an artifact of simulation setup rather than a physical property of the system.  
  - **Resolution test** Provide simulation protocols, convergence metrics (e.g., RMSD stability, principal component overlap, replica exchange acceptance rates if used), and evidence that the observed landscape differences exceed sampling noise.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The authors claim that SHAP analysis and binary classification of features in ligand states rank allosteric contributions of secondary structure elements, highlighting regions adjacent to the nucleotide-binding site and pore loops.  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The machine learning methodology is described only in passing. No information is given on feature construction, training data size, model architecture, cross-validation strategy, or how SHAP values were aggregated across the ensemble. The binary classification of ligand states is mentioned but not defined.  
  - **Why it matters** SHAP-based feature attribution is only meaningful if the underlying model is well calibrated and the features are physically interpretable. Without validation of the model and the feature set, the ranking of secondary structure elements cannot be trusted as evidence for allosteric mechanisms.  
  - **Resolution test** Describe the machine learning pipeline in detail, including feature definitions, model selection, training and test splits, performance metrics, and SHAP aggregation methods. Show that the model generalizes and that the SHAP rankings are stable across bootstrap resampling.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Support for conclusions  
  - **Claim pointer** The authors claim that amino acid-level analysis of allosteric paths reveals intra-ring cooperativity modulating long-distance communication within AAA+ protomers.  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The abstract states this as a finding, but no methodological basis is described for how allosteric paths were computed or how cooperativity was quantified. It is unclear whether this is derived from correlation analysis, network models, perturbation response, or another approach.  
  - **Why it matters** The claim of intra-ring cooperativity is a central mechanistic conclusion. Without a defined and validated method for identifying allosteric paths, the conclusion is not falsifiable or reproducible from the information given.  
  - **Resolution test** Specify the method used to identify allosteric communication paths, the criteria for defining cooperativity, and the statistical significance of the identified paths relative to null models.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Scientific importance  
  - **Claim pointer** The authors imply that the comparative study reveals both similar mechanisms involving the clade 3 domain and ClpB-specific mechanisms involving communication with the clade 5 domain.  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The abstract does not state what the clade 5-specific mechanisms are, how they differ from clade 3 mechanisms, or why they are functionally relevant for disaggregation. The comparative claim is therefore vague.  
  - **Why it matters** The comparative design is a key selling point of the study. If the clade 5-specific findings are not clearly articulated and tied to functional differences between severing and disaggregation, the added value of the comparison is diminished.  
  - **Resolution test** Clearly state the distinct mechanistic features attributed to clade 5 communication and relate them to known functional differences between katanin and ClpB.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Readability  
  - **Affected element** Abstract structure  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The abstract moves from general background to specific findings without a clear statement of the open question or hypothesis being tested.  
  - **Required correction** Add one sentence early in the abstract that frames the specific mechanistic question the comparative study addresses.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Clarity of terminology  
  - **Affected element** "Ligand-specific conformations"  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The phrase "ligand-specific conformations observed in the latter case" is ambiguous. It is unclear whether this means distinct conformations for nucleotide versus substrate, or distinct conformations for different nucleotide states.  
  - **Required correction** Specify which ligand conditions produced distinct conformations and in what sense they were distinct.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Quantitative support  
  - **Affected element** "Restrict the conformational landscape"  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The claim of landscape restriction is qualitative. No metric such as free energy differences, entropy changes, or overlap coefficients is reported.  
  - **Required correction** Provide a quantitative measure of landscape restriction in the abstract or indicate that such metrics are reported in the full text.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** "Bioinformatic analysis"  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The nature of the bioinformatic analysis is not described. It is unclear whether this refers to sequence analysis, structural comparisons, or evolutionary conservation mapping.  
  - **Required correction** Briefly state what the bioinformatic analysis consisted of and how it contributed to the conclusions.

## Risk / unsupported claims
- The claim that nucleotide and substrate binding restrict the conformational landscape is unsupported without simulation convergence and sampling details.
- The claim that SHAP analysis ranks allosteric contributions is unsupported without machine learning model specifications and validation.
- The claim that intra-ring cooperativity modulates long-distance communication is unsupported without a defined method for path identification and cooperativity quantification.
- The claim of ClpB-specific mechanisms involving clade 5 communication is not substantiated with specific mechanistic detail.
- The overall biological relevance of the findings to microtubule severing and protein disaggregation is not articulated beyond the introductory framing.