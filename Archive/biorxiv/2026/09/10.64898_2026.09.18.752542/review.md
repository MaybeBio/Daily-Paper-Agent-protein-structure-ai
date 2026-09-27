## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present NeoToxPred, a sequence-only binary toxicity classifier built by fine-tuning the ESM-C 600M protein language model with a six-layer feed-forward head. The claimed novelty resides in training-data curation, specifically orthologous negatives from the same InterPro families under taxonomic proximity control, length-stratified negatives, and family-disjoint splitting. Reported internal performance includes MCC 0.897 and F1 0.949 on long sequences, MCC 0.869 on short peptides, outperforming five recent predictors. External validation on the redfin waspfish proteome recovered 11 of 16 empirically validated toxins. Computational alanine scanning is claimed to localize predictions to functional residues.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full methods, training and validation dataset descriptions, benchmark details, baseline predictor specifications, external validation protocol, alanine scanning methodology, statistical significance tests, and all numerical results beyond those stated in the abstract

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable contribution to the toxicity prediction literature, with a sensible emphasis on negative-set construction. However, the evidence base available for review is limited to the abstract, and several claims cannot be verified without access to the full manuscript. The central methodological claims are reasonable in principle, but the reported performance metrics and external validation results require detailed scrutiny of the underlying protocols. The framing of the contribution as primarily data-centric rather than architectural is refreshing and aligns with current concerns in the field, but the abstract alone does not establish the robustness of the approach.
- **Who would be interested in the results, and why** Researchers in protein function prediction, toxin discovery, and computational toxicology would find this work relevant. The emphasis on negative-set design has broader implications for any sequence classification task where homology-based confounding is a concern. The external validation on a venomous fish proteome may interest toxinology and drug discovery communities seeking sequence-based screening tools.
- **Major strengths** The explicit focus on negative-set design as a source of performance inflation is timely and addresses a recognized weakness in the field. The use of orthologous negatives under taxonomic proximity control and length stratification targets specific confounding variables. The family-disjoint splitting strategy is a sound response to pattern memorization concerns. The external validation on a previously unseen proteome is a meaningful step beyond internal benchmarks.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail to assess whether the negative-set construction fully eliminates the claimed confounds. The external validation recovery rate of 11 of 16 requires context on the baseline false-positive rates and the statistical significance of the recovery. The alanine scanning claim lacks methodological detail. The comparison with five recent predictors is unverifiable without specification of the baselines and evaluation protocols.
- **Assessment against Nature-style criteria** Originality is moderate to high, as the data-centric framing is not entirely new but the specific combination of orthologous and length-stratified negatives is a distinctive contribution. Scientific importance is potentially high for the toxicity prediction community, though the broader impact beyond this niche is unclear. Interdisciplinary readership is plausible given the intersection of machine learning, evolutionary biology, and toxinology. Technical soundness cannot be fully assessed from the abstract alone, but the described methodology is reasonable. Readability for nonspecialists is adequate, though the abstract assumes familiarity with protein language models and MCC.
- **Recommendation posture** Supportive if technical concerns are resolved upon full manuscript review. The core idea is sound and the reported results are promising, but the abstract-level evidence is insufficient to establish the case definitively.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The orthologous negative set drawn from the same InterPro families under controlled taxonomic proximity eliminates phylogenetic shortcuts.
- **Evidence pointer** Abstract, methods not provided
- **Concern** The abstract states that orthologous negatives are drawn from the same InterPro families under controlled taxonomic proximity, but no details are given on how taxonomic proximity is defined, how the threshold is set, or how the risk of residual phylogenetic signal is quantified. Without this information, it is unclear whether the negative set truly eliminates phylogenetic shortcuts or merely reduces them.
- **Why it matters** The central claim of the paper is that negative-set design is the key innovation. If the orthologous negative construction is not rigorously defined and validated, the entire contribution is weakened.
- **Resolution test** Provide a detailed description of the taxonomic proximity metric, the selection thresholds, and an analysis demonstrating that the resulting negative set does not retain phylogenetic confounding, for example by showing that model performance is stable across taxonomic distance bins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Length-stratified negative control set eliminates sequence length as a predictive cue.
- **Evidence pointer** Abstract, methods not provided
- **Concern** The abstract claims that length stratification eliminates sequence length as a predictive cue, but no information is provided on how the stratification was performed, whether the length distributions of positives and negatives are matched, or whether the model was tested for residual length dependence beyond the reported stability across sequence lengths.
- **Why it matters** If length remains a predictive cue, the model may be exploiting a trivial feature rather than learning functional determinants of toxicity, which would undermine the biological interpretability of the predictions.
- **Resolution test** Show the length distributions of the training and test sets, demonstrate that the model's performance does not vary systematically with sequence length, and provide an analysis of the model's reliance on length as a feature, for example through ablation or feature attribution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** External validation on the redfin waspfish proteome recovered 11 of 16 empirically validated toxins without collapsing into a single-class prediction.
- **Evidence pointer** Abstract, external validation details not provided
- **Concern** The recovery of 11 of 16 toxins is reported without context on the total number of predictions made, the false-positive rate, the threshold used for calling a toxin, or the statistical significance of the recovery compared to random expectation. The statement that structure-dependent baselines identified substantially fewer positives is also vague without specifying which baselines and what their false-positive rates were.
- **Why it matters** A recovery rate of 11 of 16 is only meaningful if the model is not simply predicting many positives, which would trivially increase recall at the cost of precision. The comparison with baselines is essential to establish that the model provides added value.
- **Resolution test** Provide the full confusion matrix for the external validation, the precision-recall trade-off, the threshold selection procedure, and a statistical test comparing the recovery rate to a random or baseline model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** Computational alanine scanning confirmed that the framework contextually localizes its predictions to functionally active residues.
- **Evidence pointer** Abstract, alanine scanning methods not provided
- **Concern** The alanine scanning claim is presented as a validation of the model's interpretability, but no details are given on how the scanning was performed, how the functional residues were defined, or how the localization was quantified. Without this information, the claim is not assessable.
- **Why it matters** Interpretability claims are increasingly important for model acceptance, but they require rigorous validation. If the alanine scanning is not properly benchmarked, the claim may overstate the model's biological insight.
- **Resolution test** Describe the alanine scanning protocol, define the ground truth for functional residues, and provide a quantitative comparison of the model's predicted importance scores against experimental or structural data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "decisively outperforming five recent predictors" is vague without naming the predictors or providing the comparison metrics.
- **Required correction** Specify the names of the five predictors and the metrics used for comparison, or refer to a table in the full manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model availability
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not state whether the model, code, or training data will be made publicly available.
- **Required correction** Add a data and code availability statement to the abstract or the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance metrics
- **Evidence pointer** Abstract, location not provided
- **Issue** The reported MCC and F1 values are presented without confidence intervals or significance tests against the baselines.
- **Required correction** Provide confidence intervals or statistical tests for the reported metrics, or state that they are point estimates from a single split.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** External validation scope
- **Evidence pointer** Abstract, location not provided
- **Issue** The external validation is limited to a single proteome, which limits the generalizability of the claim.
- **Required correction** Acknowledge this limitation in the abstract or full manuscript, or provide additional external validation on multiple proteomes.

## Risk / unsupported claims
- The claim that orthologous negatives eliminate phylogenetic shortcuts is unsupported without detailed methods and validation.
- The claim that length stratification eliminates sequence length as a predictive cue is unsupported without distribution matching and residual analysis.
- The external validation recovery rate of 11 of 16 is uninterpretable without false-positive context and baseline comparison.
- The alanine scanning localization claim is not assessable without methodological detail.
- The comparison with five recent predictors is unverifiable without specification of the baselines and evaluation protocols.
- The statement that structure-dependent baselines identified substantially fewer positives is vague and unsupported without specific numbers.