## Review setup
- **Input scope** Full manuscript text (abstract, introduction, related works, methods, experiments, discussion, supplementary material references)
- **Assessment boundary** Scientific and technical evaluation of the proposed InstructPLM-mu framework, fusion strategy comparisons, fine-tuning recipe analysis, and claims regarding performance parity with ESM3
- **Shared manuscript claim summary** The authors propose InstructPLM-mu, a fine-tuning framework that injects structural information into pretrained sequence-only protein language models (ESM2) via three fusion strategies (Cross Attention, Channel-wise Concat, Token-wise Concat). They claim that Token-wise Concat achieves performance comparable to ESM3 (a much larger multimodal model trained from scratch) at a fraction of the computational cost, and that fine-tuning recipe choice critically affects performance, with overly aggressive tuning causing catastrophic forgetting.
- **Visible evidence base** Tables 1-5 (dataset details, fusion strategy comparisons, comparison with scratch-trained models, fine-tuning strategy results, ablation results), Figure 1 (overview), Figure 2 (fusion architectures), Figure 3 (training recipes), Supplementary Tables S1-S5, Supplementary Figures S1-S3
- **Missing materials affecting confidence** Actual numerical values for Tables 1-5 are not provided in the manuscript text; only table captions and qualitative descriptions are visible. Supplementary materials (Tables S1-S5, Figures S1-S3) are referenced but not included. Statistical significance details for Supplementary Table S3 are not visible. Implementation code and model weights are referenced but not accessible for verification.

## Reviewer

- **Overall assessment** The manuscript addresses a timely and practically important question: whether structural information can be efficiently injected into pretrained sequence-only PLMs via fine-tuning, rather than training multimodal models from scratch. The systematic comparison of three fusion strategies and three fine-tuning recipes is a valuable contribution. However, the absence of actual numerical results in the provided text severely limits the ability to evaluate the strength of the claims. The central claim of parity with ESM3 rests on a single average score comparison without visible error bars, statistical tests, or per-category breakdowns. The manuscript is well-structured and clearly written, but the evidence base as presented is insufficient to fully establish the case.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, mutation effect prediction, and protein language models. Researchers developing multimodal models for biological sequences would find the fusion strategy comparison and fine-tuning recipe analysis directly relevant. Practitioners in protein engineering who need resource-efficient methods for mutation screening would also benefit from the practical guidance offered.

- **Major strengths** 
  1. The research question is well-motivated and practically significant: demonstrating that fine-tuning can match scratch-trained multimodal performance would substantially lower the barrier to structural-aware prediction.
  2. The systematic comparison of three fusion strategies (Cross Attention, Channel-wise Concat, Token-wise Concat) provides useful architectural guidance.
  3. The investigation of fine-tuning recipes (Full Fine-tune, LoRA + Adapters, Adapter-only) and the observation that more trainable parameters do not always help is an important practical insight.
  4. The biological interpretation of Token-wise Concat as "instruction-like" structural tokens is conceptually appealing and connects architectural design to biological reasoning.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Token-wise Concat obtains the highest average score (0.469)" and "Token-wise concat (0.469) achieves comparable performance to ESM3 (0.468)"
- **Evidence pointer** Table 2, Table 3, location not provided
- **Concern** The actual numerical values for Tables 2 and 3 are not visible in the provided manuscript text. The claims of superiority for Token-wise Concat and parity with ESM3 rest entirely on these unverifiable numbers. Furthermore, no error bars, confidence intervals, or per-assay variance measures are reported in the text. The single average score comparison between 0.469 and 0.468 is presented as "comparable" without any statistical justification.
- **Why it matters** The central contribution of the paper is the claim that fine-tuning can match scratch-trained multimodal performance. Without visible numerical results and appropriate uncertainty quantification, this claim cannot be evaluated. A difference of 0.001 in average score could be within noise, and the absence of statistical testing undermines the validity of the comparison.
- **Resolution test** Provide the full numerical results for Tables 2 and 3, including per-assay scores, standard deviations or confidence intervals, and the results of appropriate statistical tests (e.g., paired tests across assays) demonstrating that the observed differences are significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "our experiments show that fine-tuning ESM2 with structural inputs can reach performance comparable to ESM3"
- **Evidence pointer** Table 3, location not provided
- **Concern** The comparison with ESM3 is made on a subset of 201 ProteinGym assays (after excluding proteins longer than 1000 residues), while ESM3's reported performance may be on the full 217-assay benchmark. The manuscript does not clarify whether the ESM3 baseline score of 0.468 was recomputed on the same 201-assay subset or taken from published results on the full benchmark. If the latter, the comparison is not apples-to-apples.
- **Why it matters** Benchmark comparisons are only meaningful when all methods are evaluated on identical data. If ESM3's score is from the full benchmark and the authors' methods are evaluated on a filtered subset, the comparison is biased and the claim of parity is not supported.
- **Resolution test** Clarify whether the ESM3 baseline was recomputed on the same 201-assay subset. If not, recompute all baselines on the identical evaluation set and report the results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "an overly aggressive training recipe may lead to knowledge forgetting of the pretrained PLMs"
- **Evidence pointer** Table 4, location not provided
- **Concern** The claim about knowledge forgetting is inferred from performance degradation under Full Fine-tune, but no direct evidence of forgetting (e.g., evaluation on the original pretraining task or a held-out language modeling benchmark) is provided. The observed performance drop could be due to overfitting to the fine-tuning data rather than catastrophic forgetting of pretrained knowledge.
- **Why it matters** The distinction between overfitting and catastrophic forgetting has different implications for model design. If the issue is overfitting, regularization or more data would help; if it is forgetting, different parameter-efficient strategies would be needed. The current evidence does not discriminate between these possibilities.
- **Resolution test** Evaluate fine-tuned models on a held-out language modeling or sequence understanding task to directly measure retention of pretrained knowledge, and compare with the fine-tuning performance to distinguish overfitting from forgetting.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "We will release code and checkpoints to facilitate reproducibility"
- **Evidence pointer** Data and code availability section, location not provided
- **Concern** The manuscript states that code and checkpoints will be released, but the provided GitHub and HuggingFace links are not accessible in the review context. More critically, the manuscript does not specify the exact training hyperparameters, data preprocessing steps, or evaluation protocol in sufficient detail to allow independent reproduction. Supplementary Tables S1 and S2 are referenced but not visible.
- **Why it matters** Reproducibility is a core requirement for computational biology research. Without detailed experimental protocols and accessible code, other researchers cannot verify the claims or build upon the work.
- **Resolution test** Provide complete training and evaluation details in the main text or supplementary materials, and ensure that code and model weights are publicly accessible at the time of publication.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, Cross Attention description
- **Evidence pointer** Methods, Cross Attention subsection, location not provided
- **Issue** The description of the Cross Attention mechanism states that structural embeddings serve as key and value, but does not specify the query source. It is implied that sequence embeddings serve as queries, but this is not explicitly stated.
- **Required correction** Clarify that sequence embeddings serve as queries in the Cross Attention mechanism, and specify whether the attention is bidirectional or unidirectional.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Related Works section
- **Evidence pointer** Related Works, location not provided
- **Issue** The related works section mentions several recent models (e.g., AIDO.Protein, VenusREM) but does not provide a systematic comparison of how these models handle structural information, which would help contextualize the novelty of the proposed fusion strategies.
- **Required correction** Add a brief comparative discussion of how existing multimodal PLMs incorporate structural information, highlighting the specific gap that InstructPLM-mu addresses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Main results section
- **Evidence pointer** Table 2, location not provided
- **Issue** The manuscript reports average scores across five functional categories but does not report the number of assays per category or the variance within categories. This makes it difficult to assess the robustness of the reported improvements.
- **Required correction** Report the number of assays per functional category and include per-category standard deviations or interquartile ranges.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Computational cost analysis
- **Affected element** Implementation details section
- **Evidence pointer** Implementation details, location not provided
- **Issue** The manuscript mentions computational efficiency details in Supplementary Table S2 but does not provide a clear comparison of training time and memory usage across the three fusion strategies in the main text.
- **Required correction** Add a brief summary of the computational cost comparison in the main text, highlighting any significant differences between fusion strategies.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "structure instructions" in the title and abstract is evocative but not precisely defined. It is unclear whether this refers to token-level injection, attention-based conditioning, or another mechanism.
- **Required correction** Define "structure instructions" explicitly in the introduction or methods section, and use consistent terminology throughout.

## Risk / unsupported claims
- The claim of performance parity with ESM3 (0.469 vs 0.468) is unsupported without visible numerical results, statistical testing, and confirmation that the comparison is on identical evaluation sets.
- The claim that "an overly aggressive training recipe may lead to knowledge forgetting" is inferred from performance degradation without direct evidence of forgetting.
- The claim that Token-wise Concat "allows the model to use them more flexibly, depending on the context" is a post-hoc interpretation without mechanistic evidence.
- The claim that "multimodal fine-tuning consistently improves zero-shot mutation prediction over sequence-only baselines" cannot be fully evaluated without visible numerical results for all baseline comparisons.
- The claim that "choosing the fine-tuning strategy is also critical" is based on results from a limited set of configurations and may not generalize to other backbone sizes or fusion methods.
- The generalizability of the findings beyond ESM2 and the two tested structure encoders (ProteinMPNN, ESM-IF) is not established.

## Assessment against Nature-style criteria
- **Originality** Moderate. The question of efficient structural information injection into pretrained PLMs is timely, and the systematic comparison of fusion strategies is useful. However, the individual components (Cross Attention, concatenation, LoRA) are all established techniques; the novelty lies primarily in their application and comparison in this specific context.
- **Scientific importance** Moderate to high. If the claims are substantiated, the finding that fine-tuning can match scratch-trained multimodal performance would have practical significance for the field, potentially shifting research focus toward efficient fine-tuning approaches.
- **Interdisciplinary readership** Moderate. The work is primarily of interest to computational biologists and machine learning researchers working on protein modeling. The biological implications are discussed but not deeply explored, limiting broader appeal.
- **Technical soundness** Currently not fully assessable. The methodological descriptions are clear, but the absence of visible numerical results and statistical analyses prevents evaluation of the technical validity of the claims. The potential mismatch in evaluation sets for the ESM3 comparison is a specific concern.
- **Readability for nonspecialists** Good. The manuscript is clearly written, with helpful analogies (e.g., "instruction-like" tokens) and a logical structure. The methods section is accessible to readers with basic familiarity with transformer architectures.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important question and the experimental design is thoughtful, but the absence of visible numerical results, statistical analyses, and clarification of the ESM3 comparison protocol prevents evaluation of the central claims. The authors should provide full numerical results, appropriate uncertainty quantification, and ensure all comparisons are on identical evaluation sets. If these concerns are addressed, the work could be a valuable contribution to the field.