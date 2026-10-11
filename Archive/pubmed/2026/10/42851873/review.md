## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusions, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims based solely on the supplied text
- **Shared manuscript claim summary** The authors use deep mutational scanning datasets to experimentally evaluate local frustration in proteins, benchmark several in silico predictors, and propose a new metric (SPIN) for residue-level stability optimality
- **Visible evidence base** Abstract, Introduction, Results and Discussion, Conclusions, Methods sections; references to figures (Figure 1, Figure S1-S3), tables (Table 1, Table S1), equations (eq S1, Formula 1), and supplementary data are mentioned but not provided
- **Missing materials affecting confidence** All figures, tables, supplementary data files, and the full equation derivations are not included in the supplied material; specific numerical results (e.g., correlation coefficients beyond those stated) are not fully detailed

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in the protein biophysics literature by attempting to provide experimental validation of local frustration theory using large-scale mutational datasets. The authors present a thoughtful analysis of existing computational tools and propose a novel metric (SPIN) that may offer complementary insights. However, the provided text lacks the detailed quantitative results, figures, and supplementary materials necessary to fully evaluate the strength of the claims. The conceptual framework is sound and the work is potentially significant, but the current evidence base is insufficient to establish the central conclusions with confidence.

- **Who would be interested in the results, and why** Protein biophysicists and computational biologists studying protein stability, folding, and evolution would be the primary audience. Researchers developing or using deep mutational scanning approaches, those interested in protein design, and scientists working on energy landscape theory would also find this work relevant. The benchmarking of existing tools and the introduction of SPIN could inform method selection and development in these fields.

- **Major strengths** The manuscript addresses a long-standing gap between theoretical predictions of local frustration and experimental validation. The use of large-scale deep mutational scanning datasets (nearly 8,000 positions across 178 proteins) provides substantial statistical power. The critical evaluation of multiple in silico methods is valuable, and the proposal of SPIN as a complementary metric is conceptually interesting. The authors appropriately acknowledge limitations of existing approaches and their own analysis.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that "Results provide experimental evidence for theoretical predictions regarding the relationship between local frustration and protein sequence, structure, and evolution" (Abstract)
  - **Evidence pointer** Results and Discussion sections; Figure 1, Figure S2; location not provided for specific numerical values
  - **Concern** The abstract and results sections make broad claims about experimental evidence supporting theoretical predictions, but the specific quantitative results (correlation coefficients, statistical significance values, effect sizes) are not presented in the supplied text. The only numerical values mentioned are r = 0.30 for sequence conservation, r = 0.42 for Pythia, and 36% variance explained by burial, but these are scattered and not systematically reported.
  - **Why it matters** Without comprehensive quantitative results, the reader cannot assess the strength of the evidence or determine whether the conclusions are justified. The claim of "experimental evidence" for theoretical predictions requires clear presentation of the data supporting this assertion.
  - **Resolution test** Provide a systematic summary of all key statistical results, including correlation coefficients, confidence intervals, and p-values for each relationship examined, with corresponding figure references.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** The claim that SPIN is a valid complementary measure of residue-level stability optimality (Results and Discussion, SPIN section)
  - **Evidence pointer** SPIN section; Formula 1; Table S1; location not provided for validation results
  - **Concern** The SPIN metric is introduced and its properties are described, but no validation is presented in the supplied text. The authors state that "the ability of the measure to capture energetic optimality at the amino acid level was examined" and report median SPIN values, but there is no comparison against independent experimental measurements, no assessment of predictive validity, and no demonstration that SPIN provides information beyond existing metrics.
  - **Why it matters** A new metric requires rigorous validation to establish its utility. Without evidence that SPIN captures meaningful biological information beyond what is already available, its introduction is premature and its claimed advantages cannot be evaluated.
  - **Resolution test** Present validation analyses showing SPIN correlates with independent experimental measurements, demonstrates expected relationships with known biological features, and provides unique information not captured by existing metrics.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The claim that findings from the expanded dataset of 178 proteins support general conclusions about local frustration patterns (Results and Discussion, Expanded Datasets section)
  - **Evidence pointer** Expanded Datasets section; Figure 2B; location not provided
  - **Concern** The authors acknowledge that the dataset contains "only small protein domains" and that "a higher proportion of solvent-exposed positions may influence predictions." This raises questions about whether the conclusions generalize to larger, multi-domain proteins that are more representative of the proteome. The authors note this limitation but do not address its implications for their broader claims.
  - **Why it matters** If the dataset is biased toward small, potentially atypical proteins, the conclusions about local frustration patterns and tool performance may not be generalizable. This is particularly important given the authors' stated goal of understanding "protein behavior...in nature."
  - **Resolution test** Either demonstrate that the conclusions hold in a more diverse protein set, or explicitly limit the scope of claims to small, single-domain proteins and discuss the implications for broader applicability.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Definition of local frustration
  - **Evidence pointer** Introduction, Table 1
  - **Issue** The manuscript refers to multiple definitions of local frustration (single-residue, mutational, configurational) but the distinctions are not clearly explained in the main text. Table 1 is referenced but not provided.
  - **Required correction** Provide a clear, concise explanation of the different local frustration definitions in the main text, with a summary table that is fully described.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data filtering criteria
  - **Evidence pointer** Methods section
  - **Issue** The authors state that data were filtered using a threshold of 15 mutations per position and compared against a stricter criterion requiring all 17 ΔG values, but the rationale for these specific thresholds is not explained.
  - **Required correction** Justify the chosen thresholds and describe the sensitivity of results to these choices.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of tool performance
  - **Evidence pointer** Results and Discussion, Comparison section
  - **Issue** The authors report that Pythia outperformed other tools but do not discuss potential reasons for this beyond architectural differences. The discussion of why Pythia's graph-based approach might be advantageous is speculative.
  - **Required correction** Provide a more balanced discussion of possible explanations for performance differences, including potential biases in training data or evaluation methodology.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Limitations section
  - **Evidence pointer** Conclusions
  - **Issue** The manuscript does not include a dedicated limitations section. While some limitations are acknowledged throughout, a consolidated discussion would help readers understand the scope and caveats of the work.
  - **Required correction** Add a limitations paragraph or section that explicitly addresses dataset biases, methodological assumptions, and the generalizability of findings.

- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of comprehensive quantitative results in the supplied text. The manuscript makes strong claims about experimental validation and tool benchmarking, but the specific data supporting these claims are not visible. Additionally, the SPIN metric requires formal validation before its utility can be assessed. The authors should also clarify the relationship between their experimental approach and the theoretical definitions of local frustration, as the operationalization of the concept may differ from the original theoretical framework.

- **Assessment against Nature-style criteria** 
  - Originality: The work is conceptually original in its attempt to provide large-scale experimental validation of local frustration theory and in proposing SPIN as a new metric. However, the novelty of SPIN relative to existing approaches needs clearer articulation.
  - Scientific importance: The question of whether theoretical predictions of local frustration hold experimentally is important for the field. The benchmarking of existing tools has practical value. The introduction of SPIN could be significant if validated.
  - Interdisciplinary readership: The work bridges biophysics, computational biology, and evolutionary biology, and would appeal to a broad readership in these areas. The conceptual framework is accessible, though some technical details may be challenging for nonspecialists.
  - Technical soundness: The methodological approach is reasonable, but the supplied text does not provide sufficient detail to fully assess technical soundness. The lack of visible quantitative results and validation analyses is a significant concern.
  - Readability for nonspecialists: The manuscript is generally well-written and the conceptual framework is explained clearly. However, the multiple definitions of local frustration and the introduction of SPIN may be confusing without the referenced figures and tables.

- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising and the work addresses an important question, but the supplied text lacks the quantitative detail and validation necessary to support the central claims. The authors should be encouraged to resubmit with comprehensive results, validation of SPIN, and a clearer articulation of the relationship between their experimental approach and theoretical predictions.

## Risk / unsupported claims
- The claim of "experimental evidence for theoretical predictions regarding the relationship between local frustration and protein sequence, structure, and evolution" is not supported by the visible quantitative results.
- The claim that SPIN is a useful complementary measure is unsupported without validation analyses.
- The claim that Pythia outperforms other tools is stated but not fully contextualized with statistical comparisons.
- The assertion that "results support overall predicted patterns of local frustration" is not verifiable from the supplied text.
- The generalizability of findings from small protein domains to broader protein populations is not established.