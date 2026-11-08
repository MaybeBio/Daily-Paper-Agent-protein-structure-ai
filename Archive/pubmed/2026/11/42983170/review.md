## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report a genome-wide computational screening workflow (~85,000 prokaryotic genomes) integrating AlphaFold2 structure prediction, molecular docking, binding-energy estimation, and molecular dynamics simulations to identify bacterial L-asparaginases with minimal L-glutaminase co-activity. They identify RhAII from Acidobacteriota sp. as a highly specific L-asparaginase (K(M) 12 +/- 2 microM, k(cat) 34 +/- 2 s(-1), negligible L-glutaminase activity) and contrast it with PoAII from Planctomycetota sp. showing poor performance (K(M) 5797 +/- 1143 microM, k(cat) 1.2 +/- 0.1 s(-1)). They report a relationship between enzyme activity and conformational dynamics of a flexible gating element (FGE) based on MD simulations, and acknowledge a lack of correlation between predicted binding energies and catalytic efficiency.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or supplementary information provided
- **Missing materials affecting confidence** Full methods for computational screening, AlphaFold2 confidence metrics, docking protocols, MD simulation parameters and convergence criteria, experimental assay conditions, enzyme purity and quality control, statistical analysis details, sequence accession numbers, and any validation in biological models

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting approach to address a clinically relevant problem in L-asparaginase therapy for ALL. The identification of RhAII with reported high specificity and favorable kinetic parameters is promising. However, the evidence base available for assessment is limited to the abstract, which precludes verification of the computational workflow rigor, experimental validation quality, and the claimed structure-dynamics-function relationship. The acknowledged lack of correlation between predicted binding energies and catalytic efficiency raises questions about the predictive power of the screening pipeline. The manuscript may be of interest to the enzymology and antileukemic drug development communities, but the case is not fully established from the abstract alone.
- **Who would be interested in the results, and why** Researchers in enzyme engineering and drug development for ALL, particularly those focused on improving therapeutic proteins by reducing off-target activities. Computational biologists developing structure-based screening workflows for enzyme discovery may also find the approach relevant. Clinicians and pharmacologists interested in next-generation L-asparaginase formulations with improved safety profiles would be a secondary audience.
- **Major strengths** The study addresses a clinically meaningful problem with a clear objective. The scale of the genomic screening (~85,000 genomes) is substantial. The integration of multiple computational methods with experimental validation is a commendable design. The explicit acknowledgment of a limitation in the computational workflow (lack of binding energy correlation with catalytic efficiency) demonstrates scientific transparency.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The lack of correlation between predicted binding energies and catalytic efficiency undermines the predictive validity of the screening workflow. Without evidence that the computational ranking reliably identifies high-performing enzymes, the claim that RhAII was identified through this workflow as a promising candidate is weakened. Additionally, the absence of experimental validation in biological models, as acknowledged by the authors, means the therapeutic potential remains speculative.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of AlphaFold2, docking, and MD for enzyme screening is not entirely novel, but the specific application to L-asparaginase specificity is a reasonable contribution.
  - Scientific importance: Moderate. Improving L-asparaginase specificity has clinical relevance, but the impact depends on whether RhAII performs well in biological models, which is not yet demonstrated.
  - Interdisciplinary readership: Limited. The work bridges computational biology and enzymology, but the abstract is unlikely to attract broad interdisciplinary attention beyond these fields.
  - Technical soundness: Not fully assessable from the abstract. Key details on computational parameters, experimental replicates, and statistical treatment are missing.
  - Readability for nonspecialists: The abstract is reasonably clear, though kinetic parameters and MD terminology may be challenging for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible workflow and a promising hit, but the acknowledged limitation in the computational pipeline and the lack of biological validation mean the core claims cannot be fully supported. A revised manuscript with full methods and additional validation data would be needed to assess the case more favorably.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the computational screening workflow identified RhAII as a highly specific L-asparaginase with minimal L-glutaminase co-activity.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract states that predicted substrate binding energies did not correlate with catalytic efficiency, yet the screening workflow relied on binding-energy estimation as a key selection criterion. This internal inconsistency raises questions about how the six top-ranked enzymes were selected and whether the computational ranking had any predictive value. Without details on the selection thresholds, the ranking algorithm, or any retrospective analysis of why RhAII was correctly identified despite the poor correlation, the validity of the screening approach is unclear.
- **Why it matters** If the computational predictions do not correlate with experimental outcomes, the claim that genome-wide screening identified RhAII is weakened. The workflow may have produced a hit by chance rather than by design, which would undermine the generalizability of the approach and the scientific contribution.
- **Resolution test** Provide a detailed description of the selection criteria for the six enzymes, including any scoring functions or cutoffs. Include a retrospective analysis showing whether the computational metrics (binding energy, docking scores, MD-derived parameters) distinguished RhAII from poor performers. If no correlation exists, explain how RhAII was prioritized and whether the workflow can be expected to identify other high-specificity enzymes in future applications.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that RhAII shows negligible L-glutaminase activity and high specificity toward L-asparagine.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract reports kinetic parameters for RhAII (K(M) 12 +/- 2 microM, k(cat) 34 +/- 2 s(-1)) and states negligible L-glutaminase activity, but no experimental details are provided. It is unclear how L-glutaminase activity was measured, what detection limit was used, how many replicates were performed, and whether the enzyme was purified to homogeneity. The term "negligible" is qualitative and requires a quantitative definition, such as a specific activity ratio or a detection threshold.
- **Why it matters** The central claim of the study is high substrate specificity. If the L-glutaminase assay lacked sensitivity or the enzyme preparation contained contaminants, the conclusion could be misleading. Reproducibility and comparability with existing L-asparaginases depend on rigorous kinetic characterization.
- **Resolution test** Provide full experimental methods for enzyme expression, purification, and activity assays, including substrate concentration ranges, buffer conditions, temperature, pH, number of replicates, and statistical analysis. Report the L-glutaminase activity quantitatively (e.g., specific activity or k(cat)/K(M) ratio) and state the detection limit of the assay. Include a comparison with a reference enzyme such as EcAII under identical conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim a relationship between enzyme activity and the conformational dynamics of the flexible gating element (FGE), characterized by RMSF, and L-Asn positional fluctuations, evaluated by ligand RMSD.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract describes a correlation between FGE dynamics and enzyme activity based on MD simulations, but no quantitative data are presented. It is unclear how many enzymes were compared, what the range of RMSF and RMSD values was, whether the correlation was statistically significant, and whether the relationship was observed across all six validated enzymes or only a subset. The mechanistic interpretation that "stable substrate positioning" leads to high activity is plausible but not substantiated without data.
- **Why it matters** The proposed structure-dynamics-function relationship is a key conceptual contribution of the study. If the correlation is weak or based on a small number of observations, the claim may be overinterpreted. This relationship also provides the rationale for why binding energies failed to predict activity, so it needs to be rigorously established.
- **Resolution test** Provide quantitative RMSF and ligand RMSD data for all validated enzymes, with statistical tests (e.g., correlation coefficients, p-values). Show that the relationship holds across multiple enzymes and is not driven by a single outlier. Include convergence analysis for the MD simulations and demonstrate that the observed dynamics are robust to simulation length and force field parameters.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Methods section
- **Evidence pointer** Abstract, Methods section; location not provided
- **Issue** The abstract states that ~85,000 prokaryotic genomes were screened but does not specify the source databases, the taxonomic diversity, or the criteria for genome inclusion. This limits the reproducibility of the screening scope.
- **Required correction** Specify the genome databases used (e.g., NCBI RefSeq, GenBank), the version or release date, and any filtering criteria applied before screening.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, Conclusions section
- **Evidence pointer** Abstract, Conclusions section; location not provided
- **Issue** The conclusion states that RhAII is a "promising antileukemic candidate for further validation in biological models," but no information is provided on the expected therapeutic window, potential immunogenicity, or comparison with current clinical L-asparaginases beyond the kinetic parameters.
- **Required correction** Add a brief statement on how RhAII compares to existing enzymes (e.g., EcAII or Erwinase) in terms of specificity and kinetic efficiency, and clarify what specific biological models are planned for validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results section; location not provided
- **Issue** The kinetic parameters for PoAII are reported as K(M) 5797 +/- 1143 microM and k(cat) 1.2 +/- 0.1 s(-1), but the units and the number of significant figures are inconsistent with those for RhAII. The large error on the K(M) value suggests high variability, which is not discussed.
- **Required correction** Report all kinetic parameters with consistent significant figures and units. Provide a brief comment on the variability observed for PoAII and whether this affects the interpretation of its poor performance.

## Risk / unsupported claims
- The claim that RhAII has "negligible L-glutaminase activity" is unsupported without quantitative data and assay detection limits.
- The claim of a relationship between FGE dynamics and enzyme activity is unsupported without quantitative RMSF and RMSD data and statistical analysis.
- The claim that the screening workflow identified RhAII as a promising candidate is weakened by the acknowledged lack of correlation between predicted binding energies and catalytic efficiency; the selection logic is not fully transparent.
- The therapeutic potential of RhAII as an "antileukemic candidate" is not assessable from the abstract, as no biological model data are presented.
- The generalizability of the computational workflow to other enzyme families or targets is not discussed and cannot be evaluated from the abstract.