## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, conclusion, methods, and data availability statement. No figures, tables, or supplementary material were provided.
- **Assessment boundary** Assessment is limited to the textual claims and methodological descriptions as presented. Numerical results are reported but cannot be independently verified without access to figures, tables, and supplementary sections referenced throughout.
- **Shared manuscript claim summary** The authors propose pair representation scaling, an inference-time method that multiplies the latent pair representation by a scalar (1 + β) at the input to the Pairformer in AlphaFold 3 and Boltz-2. They claim this broadens conformational sampling to recover alternative states on a benchmark of 86 two-state proteins, with effects extending to post-training-cutoff targets, persisting without an MSA, and being attributable to structured modulation rather than generic noise.
- **Visible evidence base** Textual descriptions of benchmark composition, metric definitions, statistical tests, and qualitative results. All quantitative results are referenced to figures and tables that were not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary sections (S1–S16), the public repository contents, and the actual numerical data underlying the reported statistics. Without these, the magnitude, direction, and robustness of the reported effects cannot be independently assessed.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually simple and potentially useful intervention for controlling conformational sampling in diffusion-based structure predictors. The idea of scaling a single internal representation is elegant and the transferability across AlphaFold 3 and Boltz-2 is a genuine strength. However, the evidence as presented in text alone is insufficient to fully evaluate the claims. Key concerns include the absence of any quantitative data in the text, the reliance on a single scalar with target-specific optimal sign, the limited significance of Boltz-2 results against default inference, and the unclear practical utility given that the method does not identify which sampled model is the alternative state. The manuscript is well-written and the methodological controls are thoughtfully designed, but the core claims require the missing figures and tables to be substantiated.
- **Who would be interested in the results, and why** Researchers working on conformational ensembles, protein dynamics, and the interpretability of deep learning structure prediction models. The method offers a low-cost, training-free approach to broaden sampling, which could be of interest to those studying conformational transitions, cryptic pockets, or alternative functional states. The finding that pair representations encode alternative-state information is also relevant to the growing community probing the internal representations of protein language models and structure predictors.
- **Major strengths**
  1. The method is conceptually simple, requiring only a single scalar multiplication at inference time, with no retraining or architectural changes.
  2. The same operation transfers across two different diffusion-based predictors, suggesting a general property of this architecture class.
  3. The control experiments are well-designed: matched Gaussian noise, contact-localized scaling, and alternative scaling positions collectively argue for a structured, global modulation effect.
  4. The after-training-cutoff analysis is a thoughtful control for memorization effects.
  5. The distogram analysis provides a mechanistic link between the intervention and the predicted distance distributions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** The manuscript claims that pair representation scaling "improved all three metrics across all three groups" in AlphaFold 3 and "broadened the conformational ensemble with a smaller but consistent effect" in Boltz-2.
  - **Evidence pointer** Figure 1, Figure 2, Table 1, Section 2.2, location not provided
  - **Concern** All quantitative results are reported only in figures and tables that were not provided. The text gives a few point estimates (e.g., success rate 0.60 to 0.73, RMSD improvement 1.18 Å with CI, fill ratio 0.43 vs 0.29) but the vast majority of the reported comparisons, including all per-group and per-category statistics, are inaccessible. Without the actual data, the magnitude of the effects, the distribution of per-target outcomes, and the validity of the statistical claims cannot be assessed.
  - **Why it matters** The central claim of the paper is that scaling improves conformational sampling. This claim rests entirely on the numerical results, which are not visible in the provided material. A reviewer cannot verify the strength, consistency, or practical significance of the reported improvements.
  - **Resolution test** Provide all figures and tables with full numerical data, including per-target values, effect sizes, confidence intervals, and exact p-values for every comparison.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological ambiguity
  - **Claim pointer** The manuscript states that "the value of β that surfaces the alternative state differs in sign between targets" and that "which of the two states a given β surfaces, however, stays target-specific."
  - **Evidence pointer** Section 2.3, Section 2.6, Section 4.1, location not provided
  - **Concern** The method requires sweeping β over a range and then selecting the value that surfaces the alternative state. The sign and magnitude of the optimal β are target-specific, and the manuscript does not describe any procedure for choosing β without prior knowledge of the alternative state. This raises the question of whether the method is truly usable in a predictive setting or only as a post-hoc analysis tool.
  - **Why it matters** If the user must already know the alternative state to select the correct β, the method's practical utility for discovering unknown conformations is severely limited. The manuscript should clarify whether any heuristic or general rule exists for choosing β, or whether the method is intended only for retrospective ensemble expansion.
  - **Resolution test** Provide a clear protocol for selecting β in the absence of a known alternative state, or explicitly state the limitation and discuss its implications for practical use.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The manuscript reports that in Boltz-2, "per-state and worst-case gains were consistent in direction but did not cross the significance threshold (p ≈ 0.06 for the worst-case improvement in the two precutoff groups)" and that only the fill-ratio gain reached significance.
  - **Evidence pointer** Section 2.2, location not provided
  - **Concern** The Boltz-2 results appear substantially weaker than the AlphaFold 3 results, with the primary metrics (per-state success rate and worst-case RMSD) not reaching significance against default inference. The manuscript frames this as a "smaller but consistent effect," but the evidence for consistency is not presented. The combination with MSA subsampling is reported to recover significance, but the interaction between the two interventions is not mechanistically explained.
  - **Why it matters** The claim that the method transfers to Boltz-2 is a key part of the paper's generality argument. If the effect is not statistically robust in Boltz-2, the claim of transferability is weakened, and the method may be specific to AlphaFold 3.
  - **Resolution test** Provide full per-target data for Boltz-2, including the distribution of effect sizes, and clarify whether the non-significant results reflect small effect sizes, high variance, or insufficient power.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretability of the mechanism
  - **Claim pointer** The manuscript claims that "the predicted distance distributions show that scaling shifts the encoded two-state distribution toward the experimentally observed alternative state, a directed modulation rather than an arbitrary perturbation."
  - **Evidence pointer** Section 2.5, Section 2.6, Figure 4, location not provided
  - **Concern** The mechanistic claim that the effect is "directed" relies on the correlation between distogram changes and the experimentally observed alternative state. However, the manuscript also reports that a large fraction of newly bimodal pairs in Boltz-2 (about three-quarters) have peaks matching neither reference state, and even in AlphaFold 3 about half fall in this category. The interpretation of "directed" is therefore qualified by a substantial fraction of spurious changes.
  - **Why it matters** The claim of directed modulation is central to distinguishing this method from generic perturbation. If a large fraction of the changes are not aligned with the alternative state, the mechanism may be more complex than presented, and the "directed" claim may be overstated.
  - **Resolution test** Provide a more detailed breakdown of the per-pair outcomes, including the fraction of pairs that shift toward the alternative state versus away from it, and discuss the implications of the spurious changes for the mechanistic interpretation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1, equation for scaling
  - **Evidence pointer** Section 2.1, location not provided
  - **Issue** The equation z_ij^scaled = (1 + β) z_ij is described as applied "at each recycling iteration," but it is unclear whether the scaling is applied to the same tensor repeatedly or whether the tensor evolves between iterations. The phrase "the scaling applied at each recycling iteration" could be interpreted either way.
  - **Required correction** Clarify whether the scaling is applied identically at every iteration or whether the tensor is first updated by the recycling mechanism and then scaled.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.2, benchmark composition
  - **Evidence pointer** Section 2.2, location not provided
  - **Issue** The benchmark combines sources (BioEmu, OC23, IOMemP, entropy-guided folding) but the overlap between these sets is not discussed. The manuscript notes that the 86 targets cover 85 proteins, with MurJ contributing two targets, but does not state whether any targets appear in multiple source benchmarks.
  - **Required correction** State explicitly whether any targets are shared between the source benchmarks and how duplicates were handled.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 4.7, software and hardware
  - **Evidence pointer** Section 4.7, location not provided
  - **Issue** The manuscript states that AlphaFold 3 version 3.0.1 was run locally, but the AlphaFold 3 server is typically used through a web interface. It is unclear whether the authors used a locally installed version of the model weights, which may have licensing implications.
  - **Required correction** Clarify how AlphaFold 3 was accessed and whether the model weights were obtained through the standard licensing process.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Section 2.6, internal representations
  - **Evidence pointer** Section 2.6, location not provided
  - **Issue** The subsection title "Internal Representations under Scaling" is followed by a paragraph that reads out representations "under the full scaling sweep without rescaling them further." The phrase "without rescaling them further" is confusing given that the method itself is a scaling operation.
  - **Required correction** Rephrase to clarify that the readout is taken from the model's internal state after the scaling has been applied, without additional post-processing.
- **Technical failings that need to be addressed before the case is established**
  1. All quantitative evidence is in missing figures and tables (R1-M1).
  2. The target-specific nature of β selection is not addressed as a practical limitation (R1-M2).
  3. The statistical significance of Boltz-2 results against default inference is not established (R1-M3).
  4. The mechanistic interpretation of "directed" modulation is qualified by a large fraction of spurious changes (R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** The idea of scaling a single internal representation to bias conformational sampling is novel and distinct from prior work that modifies MSAs, injects noise, or optimizes auxiliary objectives. The observation that a global scalar can shift sampling between states is a non-obvious finding.
  - **Scientific importance** The ability to control conformational sampling in diffusion-based predictors has potential implications for studying conformational transitions and alternative functional states. However, the practical utility is limited by the target-specific nature of β and the lack of a selection criterion. The importance is moderate and depends on whether the method can be used predictively.
  - **Interdisciplinary readership** The work sits at the intersection of machine learning, structural biology, and biophysics. The method is accessible to a broad audience, but the significance may be most apparent to those working on conformational ensembles. The interdisciplinary appeal is moderate.
  - **Technical soundness** The experimental design is thoughtful, with appropriate controls (matched noise, contact localization, alternative positions, training-cutoff grouping). However, the statistical reporting is incomplete in the text, and the Boltz-2 results are not significant on the primary metrics. The technical soundness cannot be fully assessed without the missing data.
  - **Readability for nonspecialists** The manuscript is clearly written and the method is explained in accessible terms. The use of a single scalar is easy to grasp. However, the discussion of distogram analysis and Pairformer internals may be challenging for readers without a background in deep learning for proteins. Overall readability is good.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the controls are well-designed, but the evidence as presented is incomplete. The authors must provide the full numerical data, address the β-selection limitation, and clarify the statistical robustness of the Boltz-2 results. If these are resolved, the manuscript could make a useful contribution to the field of conformational sampling in deep learning structure predictors.

## Risk / unsupported claims
- The claim that scaling "recovers alternative states that default inference misses, most strongly in AlphaFold 3, where the gains extend even to targets deposited after the training cutoff" is not verifiable without the figures and tables.
- The claim that the effect is "directed modulation rather than an arbitrary perturbation" is only partially supported by the text, given the large fraction of spurious bimodal changes reported.
- The claim that the method "approaches the alternative-state recovery of alignment-based sampling methods" is not supported by any quantitative comparison in the text.
- The claim that the benefit "persists even without a multiple-sequence alignment" is reported but the magnitude of the effect in the sequence-only setting is not quantified in the text.
- The practical utility of the method for discovering unknown conformations is not established, as the manuscript does not describe how to select β without prior knowledge of the alternative state.