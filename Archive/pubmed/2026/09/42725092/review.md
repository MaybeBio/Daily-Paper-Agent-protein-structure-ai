## Review setup
- **Input scope** Full manuscript (abstract only provided)
- **Assessment boundary** Abstract only
- **Shared manuscript claim summary** The authors develop an explainable AI framework to interrogate five AI models (AlphaFold3, Protenix, Boltz-2, Chai-1, DynamicBind) on orthosteric and allosteric ligand-protein complexes. They report a consistent performance gap in allosteric vs. orthosteric binding prediction, explain this via energy landscape theory (frustration landscapes), and propose that the AI blind spot can be turned into mechanistic insight.
- **Visible evidence base** Abstract only; no figures, tables, methods, or results sections provided.
- **Missing materials affecting confidence** Full text, all figures, tables, methods, datasets, code, and supplementary information.

## Reviewer
- **Overall assessment** The abstract presents an intriguing and potentially important claim: that a systematic failure of current AI models to predict allosteric ligand binding can be explained by energy landscape theory and repurposed as a diagnostic tool. The concept is novel and the scope (five models, stratified datasets) is ambitious. However, the abstract alone provides insufficient evidence to evaluate the rigor of the framework, the statistical significance of the performance gap, the validity of the frustration landscape analysis, or the generalizability of the conclusions. The core claim—that the blind spot is "allosteric" in a mechanistic sense—requires careful control for confounding factors (e.g., binding site geometry, ligand properties, training data bias) that are not addressed in the abstract.

- **Who would be interested in the results, and why** Structural biologists, computational chemists, and AI researchers working on protein-ligand interactions and drug discovery. The work could interest those seeking to understand the limitations of current AI models and those exploring physics-informed explanations for AI behavior. The potential to turn a failure mode into a diagnostic tool for allostery is of broad methodological interest.

- **Major strengths** 1. The question is timely and important: allosteric binding is a major unsolved problem in computational drug discovery. 2. The approach of using explainable AI to interrogate multiple state-of-the-art models is methodologically sound in principle. 3. The connection to energy landscape theory provides a biophysical grounding that goes beyond black-box performance metrics.

- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "a consistent and substantial performance gap observed across diverse architectures emerges in prediction of allosteric complexes"
    - **Evidence pointer** Abstract only; no quantitative data provided
    - **Concern** The abstract asserts a "consistent and substantial performance gap" but provides no metrics (e.g., RMSD, DockQ, binding affinity correlation), no statistical tests, and no comparison of effect sizes across models. Without these, the claim is unverifiable.
    - **Why it matters** The entire narrative hinges on the existence and magnitude of this gap. If the gap is small, model-dependent, or confounded by dataset composition, the central thesis collapses.
    - **Resolution test** Provide quantitative performance metrics for each model on orthosteric vs. allosteric datasets, with confidence intervals and statistical significance (e.g., paired t-test or Wilcoxon). Show that the gap is robust across multiple random splits and is not explained by trivial factors (e.g., ligand size, binding site depth).

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Conceptual clarity and control
    - **Claim pointer** "The biophysical logic for this dichotomy is unveiled through physics-based lens of the energy landscape theory"
    - **Evidence pointer** Abstract only; no data on frustration landscapes
    - **Concern** The abstract claims that frustration landscape analysis explains the performance gap, but it is unclear how this analysis was performed (e.g., on which structures, using which algorithm, with what validation). The link between AI prediction failure and "neutral frustration landscapes" is asserted, not demonstrated.
    - **Why it matters** Without a clear, testable link between the computational frustration analysis and the AI model behavior, the explanation remains a post-hoc narrative. The claim that the blind spot is "diagnostic" requires that the frustration landscape be predictive of model failure, not just correlated.
    - **Resolution test** Show that frustration landscape features (e.g., local frustration index, frustration density) quantitatively predict the performance gap across individual complexes. Provide a confusion matrix or ROC curve demonstrating that the frustration-based classifier outperforms a null model.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Dataset rigor and bias
    - **Claim pointer** "rigorously stratified datasets of orthosteric and allosteric ligand-protein complexes"
    - **Evidence pointer** Abstract only; no dataset description
    - **Concern** The abstract does not describe how orthosteric and allosteric complexes were defined, curated, or stratified. Potential confounds include: (a) allosteric sites may be systematically less well-represented in training data; (b) allosteric ligands may have different physicochemical properties; (c) the structural resolution of allosteric complexes may be lower.
    - **Why it matters** If the performance gap is driven by data bias rather than a fundamental biophysical property, the conclusions are not generalizable.
    - **Resolution test** Provide a detailed dataset table with PDB IDs, resolution, ligand properties, and training set overlap for each model. Show that the gap persists after controlling for these variables (e.g., via propensity score matching or regression).

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Terminology
    - **Evidence pointer** Abstract
    - **Issue** The phrase "allosteric blind spot" is evocative but ambiguous. It is unclear whether this refers to a failure of prediction, a failure of interpretation, or a fundamental limitation of the models.
    - **Required correction** Define "blind spot" explicitly in the abstract (e.g., "systematic underperformance in predicting allosteric vs. orthosteric binding poses").

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Framework description
    - **Evidence pointer** Abstract
    - **Issue** The abstract mentions an "explainable AI framework" but does not specify which XAI method was used (e.g., SHAP, LIME, attention maps, integrated gradients).
    - **Required correction** Name the XAI method(s) and briefly state how they were applied to the models.

- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative evidence for performance gap), R1-M2 (causal link to frustration landscapes), R1-M3 (dataset bias control).

- **Assessment against Nature-style criteria** 
    - **Originality**: High. The idea of using AI failure as a diagnostic for allostery is novel and potentially transformative.
    - **Scientific importance**: High if validated. Allostery is a central problem in drug discovery and structural biology.
    - **Interdisciplinary readership**: Moderate to high. The work bridges AI, structural biology, and biophysics.
    - **Technical soundness**: Cannot be assessed from abstract alone. The concerns above indicate that the evidence base is currently insufficient.
    - **Readability for nonspecialists**: The abstract is well-written and accessible, though some terms (e.g., "minimal frustration quenching") may require definition.

- **Recommendation posture** Currently not established from the provided evidence. The concept is promising, but the abstract lacks the quantitative and methodological detail needed to evaluate the core claims. A full manuscript with rigorous controls, statistical analysis, and validation is required before the case can be assessed.

## Risk / unsupported claims
- The claim of a "consistent and substantial performance gap" is unsupported without quantitative data.
- The claim that frustration landscapes "unveil" the biophysical logic is unsupported without showing the analysis and its predictive power.
- The claim that the framework "turns the allosteric blind spot into mechanistic insight" is unsupported without demonstrating that the insight is novel, testable, and generalizable beyond the specific models and datasets used.