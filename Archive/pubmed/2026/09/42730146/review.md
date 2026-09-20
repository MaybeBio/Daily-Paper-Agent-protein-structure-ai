## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary figure references.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with the stated scope of evaluating transformer-based models on orphan proteins. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors evaluate three transformer-based structure prediction tools (AlphaFold2, ESMFold, OmegaFold) on a curated set of orphan proteins from Meloidogyne nematodes, finding low-confidence tertiary predictions but more reliable secondary structure recovery, and conclude that TBMs fail to generalize to sequences lacking evolutionary context.
- **Visible evidence base** Main text figures (Fig 1–5), supplementary figure references (S1–S10), supplementary table reference (Table S1), methods descriptions, and a data availability link.
- **Missing materials affecting confidence** Supplementary figures and table are referenced but not provided in the submitted material. Experimental validation (e.g., crystallography, NMR) is absent, which is acknowledged by the authors. The exact composition of the orphan dataset (e.g., sequence length distributions, species breakdown) is only partially described.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question: whether transformer-based structure prediction models generalize to orphan proteins lacking detectable homologs. The authors use a biologically relevant dataset from Meloidogyne and apply multiple complementary analyses, including pLDDT comparisons, cross-model structural agreement, disorder prediction, and database searches. The finding that tertiary predictions are unreliable while secondary structure is partially recoverable is plausible and consistent with existing literature. However, the manuscript has several methodological gaps that limit the strength of the conclusions. The lack of a clear null model for the secondary structure agreement analysis, incomplete reporting of dataset characteristics, and the absence of a direct comparison to non-transformer baselines weaken the case. The discussion of why secondary structure succeeds while tertiary fails is speculative but reasonable. Overall, the work is a useful contribution, but the evidence as presented does not fully establish the central claims.
- **Who would be interested in the results, and why** Computational biologists studying protein structure prediction, particularly those interested in model generalization and out-of-distribution performance. Researchers working on orphan proteins or de novo gene emergence, especially in non-model organisms, would find the benchmark and results relevant. The paper may also interest developers of protein language models who need to understand failure modes on evolutionarily isolated sequences.
- **Major strengths** The study addresses a clearly defined and biologically important problem. The use of a curated, expert-validated orphan dataset from a non-model genus is a strength. The multi-method approach, combining three structure predictors, multiple disorder predictors, and two database search strategies, provides a broad view. The control for sequence length effects is a thoughtful addition. The secondary structure agreement analysis with statistical significance testing is a useful contribution.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological rigor
  - **Claim pointer** The authors claim that secondary structure is "consistently and significantly recovered across models" (Discussion) and that agreement is "significantly more similar than expected by chance" (Section 3.5).
  - **Evidence pointer** Section 3.5, Table S1, Figs S2–S4 (not provided)
  - **Concern** The statistical test for secondary structure agreement is described only in the Appendix, which is not included in the submitted material. The main text states that a P-value below 0.05 is achieved for 95% of sequences, but the null model is not described. Without knowing how the null distribution was generated (e.g., random assignment with what constraints on composition and length?), it is impossible to assess whether the test is meaningful. For example, if the null model does not preserve amino acid composition or secondary structure propensities, the test could be trivially significant.
  - **Why it matters** This is the core positive result of the paper. If the statistical test is flawed or overly permissive, the claim that secondary structure is reliably predicted is not supported. The reader cannot evaluate this without the Appendix.
  - **Resolution test** Provide the full null model description in the main text or a clearly accessible supplement. Show that the null model preserves relevant sequence properties (e.g., composition, length, per-residue propensities). Report the distribution of P-values across all sequences, not just the 95% threshold.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Completeness of evidence
  - **Claim pointer** The authors state that "the observed deficiencies in tertiary structure prediction are not a trivial consequence of shorter sequences" (Discussion), based on a length-matched control.
  - **Evidence pointer** Section 4, Figs S9 and S10 (not provided)
  - **Concern** The length-matched control is described only in the Discussion and the corresponding figures are in the supplementary material, which was not provided. The main text does not describe how the length-matched subset was constructed, how many sequences were included, or which metrics were compared. Without this information, the claim that length is not a confounding factor cannot be verified.
  - **Why it matters** Orphan proteins are often shorter than average, and sequence length is known to affect structure prediction confidence. If the control is underpowered or improperly matched, the conclusion that the failure is due to lack of evolutionary context rather than length is not established.
  - **Resolution test** Describe the matching procedure in the main text (e.g., binning, propensity score matching). Report the number of sequences in the control and the distribution of lengths. Show that the key metrics (pLDDT, TM-score agreement) are unchanged in the matched subset.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretive clarity
  - **Claim pointer** The authors state that "the more closely the method is related to TBMs, the more disorder will be predicted" (Section 3.3).
  - **Evidence pointer** Section 3.3, Fig 4
  - **Concern** This is an interesting observation, but the interpretation is ambiguous. The authors do not discuss whether this reflects a systematic bias in TBM-based disorder predictors, or whether it indicates that TBMs are correctly identifying disorder that other methods miss. The lack of experimental validation for disorder means the direction of the bias cannot be determined. The authors acknowledge this indirectly but do not explore the implications for their main argument.
  - **Why it matters** If TBM-based disorder predictors are biased toward overpredicting disorder, this could explain the low pLDDT scores for tertiary structure, which would be a different failure mode than the one the authors emphasize. The paper would be stronger if this alternative interpretation were addressed.
  - **Resolution test** Add a discussion of whether the observed trend is consistent with known biases in TBM-based disorder predictors. If possible, compare to a small set of experimentally characterized disordered proteins to calibrate the predictors.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Benchmark completeness
  - **Claim pointer** The authors conclude that "reliable structural inference for orphan proteins remains challenging" (Section 3.4).
  - **Evidence pointer** Section 3.4
  - **Concern** The database search results are reported as hit counts, but the authors do not report the distribution of alignment lengths, sequence identities, or coverage for the significant hits. The threshold of e-value below 10^-3 is permissive, and the biological relevance of the hits is not discussed. For example, a hit with 50% identity over a short region may not indicate meaningful structural similarity.
  - **Why it matters** The conclusion that orphan proteins lack structural homologs depends on the quality of the search. If the hits are mostly spurious or cover only fragments, the conclusion is stronger. If the hits are meaningful but the authors dismiss them, the conclusion is weaker. The current reporting does not allow the reader to judge.
  - **Resolution test** Report the distribution of alignment coverage and identity for significant hits. Discuss a few representative examples, including whether the predicted structures align over full-length or only local regions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.2
  - **Evidence pointer** Section 2.2, "In order to compose a comparable negative sample of non-orphan structure predictions, we created two different sets:"
  - **Issue** This sentence is incomplete. The two sets are not described in the main text.
  - **Required correction** Complete the sentence or refer to a supplementary section where the two sets are defined.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 2.2
  - **Evidence pointer** Section 2.2, AlphaFold2 description
  - **Issue** The authors state that AlphaFold2 was run "at the orthogroup level" with a custom MSA, but do not specify how the representative sequence was chosen or how many sequences were included in the MSA on average.
  - **Required correction** Provide the selection criterion for the representative sequence and the average MSA depth.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 3.1
  - **Evidence pointer** Section 3.1, Fig 2
  - **Issue** Spearman correlation coefficients are reported for pLDDT comparisons, but confidence intervals or P-values are not given.
  - **Required correction** Report P-values or confidence intervals for the correlations.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Section 3.5
  - **Evidence pointer** Section 3.5, "pairwise identity ranging from 85% to 90%"
  - **Issue** The term "pairwise identity" is used for secondary structure agreement, but it is not defined. It is unclear whether this refers to per-residue agreement or something else.
  - **Required correction** Define the metric explicitly.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, reference to Middendorf and Eicholt 2024
  - **Issue** The comparison to the Drosophila study is brief and the sentence ends with a colon, suggesting a quote or list that is not present.
  - **Required correction** Complete the sentence and provide a more detailed comparison of the two studies' findings.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical test for secondary structure agreement) and R1-M2 (length-matched control) are the most critical. Both are central to the main claims and cannot be evaluated from the submitted material. R1-M3 (disorder interpretation) and R1-M4 (database search quality) are important but not blocking.
- **Assessment against Nature-style criteria**  
  *Originality*: The question of TBM generalization to orphan proteins is not entirely new, but the specific application to Meloidogyne and the multi-method comparison is a useful contribution. The work is incremental rather than transformative.  
  *Scientific importance*: The topic is relevant to a broad community, as orphan proteins are widespread and understudied. The findings have practical implications for users of structure prediction tools. However, the importance is moderate, as the conclusions are largely negative (TBMs fail on tertiary structure) and the positive result (secondary structure) is not surprising.  
  *Interdisciplinary readership*: The manuscript is likely to appeal to computational biologists, structural biologists, and evolutionary biologists. The writing is accessible, but some methods details are sparse.  
  *Technical soundness*: The overall approach is reasonable, but the missing details on the statistical test and the length-matched control are significant gaps. The lack of experimental validation is acknowledged but limits the strength of the conclusions.  
  *Readability for nonspecialists*: The manuscript is generally well-written and the figures are clear. The abstract and introduction are accessible. Some methods sections assume familiarity with specific tools.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is valid and the dataset is valuable, but the current evidence does not fully establish the central claims about secondary structure reliability and the role of sequence length. The authors should provide the missing methodological details and clarify the interpretation of the disorder results.

## Risk / unsupported claims
- The claim that secondary structure is "consistently and significantly recovered" is not fully supported without the null model description (R1-M1).
- The claim that the observed failures are not due to sequence length is not verifiable without the length-matched control details (R1-M2).
- The claim that "the more closely the method is related to TBMs, the more disorder will be predicted" is presented as a general trend but is based on a single dataset and three predictors; the direction of the bias is not established (R1-M3).
- The conclusion that "reliable structural inference for orphan proteins remains challenging" is supported, but the database search results are not reported in sufficient detail to assess the strength of this conclusion (R1-M4).
- The statement that "the convergence of these findings strongly suggests that the observed behavior reflects a general property of TBMs" is speculative, as it relies on a single comparison to a Drosophila study with limited detail.