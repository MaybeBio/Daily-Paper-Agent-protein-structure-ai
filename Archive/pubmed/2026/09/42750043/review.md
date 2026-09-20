## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present Genolator, a multimodal large language model that fuses DNA sequence, amino acid sequence, and protein structure embeddings with natural language understanding to answer questions about protein function, including subcellular localization, molecular function, and biological processes. The model is fine-tuned on over 365,000 question-answer pairs generated from Gene Ontology annotations and is evaluated on confirmation/denial tasks and open-ended questions, with analyses of hidden representations and attention patterns.
- **Visible evidence base** Main text, methods section, figure legends for Figures 1-15, Table 1, and references to supplementary files (Additional files 1 and 2)
- **Missing materials affecting confidence** Supplementary figures and tables (Figures S1-S20, Table S1), Additional file 2 (including case study Excel sheets and prompts), actual model outputs, hyperparameter details, and full evaluation results for all baseline models

## Reviewer

- **Overall assessment** The manuscript describes a technically ambitious integration of multiple genomic modalities into a generative language model framework. The core idea of fusing DNA, protein sequence, and structural embeddings with a fine-tuned LLM is timely and potentially useful for the genomics community. However, the current evidence base is insufficient to establish the claimed advantages. The evaluation is largely self-referential, with limited external validation, and several methodological details that are critical for reproducibility are missing. The attention and ablation analyses are suggestive but do not fully support the conclusion that the multimodal approach is the primary driver of performance. The manuscript would benefit from a more rigorous comparison against state-of-the-art protein function prediction methods and a clearer demonstration of practical utility beyond the constructed QA framework.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, genome annotation, and the application of large language models to biological data. Researchers developing multimodal AI systems for genomics would also find the architectural choices and fusion strategy relevant. The natural language interface aspect may appeal to clinicians and biologists seeking more accessible tools for interpreting genomic variants, though the current manuscript does not yet demonstrate this use case convincingly.

- **Major strengths**
  - The multimodal fusion strategy combining DNA, protein sequence, and structural embeddings is conceptually novel and addresses a real gap in existing models.
  - The use of frozen foundation models (Evo2, ESM2, PST) with trainable projectors is a practical and efficient design choice.
  - The construction of a large QA dataset with both confirmation/denial and open-ended questions is a substantial effort.
  - The inclusion of attention analysis and ablation studies shows a thoughtful approach to model interpretability.
  - The manuscript is generally well-written and the figures are informative.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that Genolator outperforms baseline models including GPT 4.1 and XGBoost on confirmation/denial tasks.
- **Evidence pointer** Table 1, Section "Genolator can accurately confirm and deny gene functionality associations and outperforms allrounder and specialist baseline models"
- **Concern** The evaluation methodology for the confirmation/denial task is not fully described. It is unclear how the binary classification is derived from the generative model's responses. The automatic GPT 4.1 post-processor used to label responses as "confirmation" or "denial" introduces a potential source of bias and error that is not quantified. Furthermore, the XGBoost baseline is trained on PST embeddings and prompt embeddings, but the details of this training (e.g., feature construction, hyperparameters, class balancing) are not provided. The comparison with GPT 4.1, which receives raw sequences in the prompt, is not apples-to-apples because Genolator receives pre-computed embeddings. This makes it difficult to attribute the performance difference to the model architecture versus the input representation.
- **Why it matters** Without a clear and unbiased evaluation protocol, the central claim of outperformance cannot be verified. The comparison is confounded by differences in input representation and the use of an LLM-based post-processor that may favor the fine-tuned model.
- **Resolution test** Provide a detailed description of the classification protocol, including the exact prompt used for the GPT 4.1 post-processor and its accuracy on a manually annotated subset. Report the performance of the XGBoost baseline with full hyperparameter details. Include an additional baseline where GPT 4.1 is given the same embedding-based input as Genolator, or where Genolator is given raw sequences, to isolate the effect of the multimodal fusion.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The overall reproducibility of the model training and evaluation pipeline.
- **Evidence pointer** Methods section "Fine-tuning and experimental setup"
- **Concern** Critical training details are missing. The manuscript states that training was conducted for up to ten epochs with early stopping, but does not specify the number of training steps, the optimizer, the learning rate schedule, the warmup steps, the weight decay, or the LoRA rank and alpha values. The batch size is given as eight, but the gradient accumulation steps are not mentioned. The hardware configuration for training is not described. The exact composition of the training, validation, and test splits after the KMeans clustering is not reported (e.g., number of genes per split). The prompt templates used for training and inference are not shown in the main text, only referenced as being in Additional file 2.
- **Why it matters** Reproducibility is a cornerstone of scientific publication. Without these details, other researchers cannot replicate the training procedure or verify the results. The manuscript claims a reproducible pipeline but omits essential information.
- **Resolution test** Add a comprehensive hyperparameter table, describe the optimizer and scheduler, report the final split sizes, and include the full prompt templates in the main text or a clearly referenced supplementary section.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that Genolator's hidden representations are "biologically and linguistically plausible" and that the model learns meaningful structure.
- **Evidence pointer** Section "Genolator's hidden states contain linguistically and biological plausible representations", Figures 3-8
- **Concern** The t-SNE visualizations and cosine similarity analyses are largely qualitative. The manuscript reports specific cosine similarity values for selected term pairs but does not provide a systematic quantitative assessment. For example, it is unclear whether the observed clustering is significantly different from what would be expected by chance or from a model trained without one of the modalities. The claim of "biological plausibility" is based on visual inspection of a few selected examples. A more rigorous analysis, such as comparing the embedding geometry to a known ontology structure or using a quantitative clustering metric, would strengthen this claim.
- **Why it matters** The interpretability analysis is presented as evidence that the model has learned meaningful representations. If this is not rigorously demonstrated, the claim is weakened and the value of the multimodal approach is less clear.
- **Resolution test** Provide a quantitative evaluation of the clustering, such as silhouette scores or adjusted Rand index compared to a random baseline. Perform an ablation where one modality is removed and show that the clustering quality degrades. Consider comparing the embedding distances to a gold-standard semantic similarity measure for GO terms.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the open-ended question answering capability is a valuable feature, with reported overlap rates of 78-89% with ground truth.
- **Evidence pointer** Section "Evaluating the Genolators capability to answer open-ended questions", Figure 9
- **Concern** The evaluation of open-ended questions relies on a GPT 4.1-based LLM-as-judge to map both predictions and ground truth to GO Slim terms. This introduces a circularity concern, as GPT 4.1 is also used as a baseline and was shown to perform poorly on the confirmation/denial task. The accuracy of the GPT 4.1 mapping itself is not validated. The reported "overlap" rates are difficult to interpret without knowing the baseline rate of overlap expected by chance. For example, if the model always predicted the most common GO Slim term, what would the overlap rate be? The manuscript does not provide this context.
- **Why it matters** The open-ended QA capability is a key differentiator of the model. If the evaluation is biased or not properly calibrated, the reported performance may be misleading.
- **Resolution test** Validate the GPT 4.1 mapping on a manually annotated subset. Report the expected overlap rate for a trivial baseline (e.g., always predicting the most frequent term). Consider using a more objective evaluation metric, such as semantic similarity against the GO graph.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The claim that Genolator "enhances accessibility to genomic information" and is useful for "clinical research."
- **Evidence pointer** Abstract, Conclusion
- **Concern** The manuscript does not provide any demonstration of practical utility in a real-world or clinical setting. The evaluation is entirely on a synthetic QA dataset constructed by the authors. There is no validation on experimentally characterized proteins, no comparison to established protein function prediction benchmarks (e.g., CAFA), and no case study showing how a researcher would use Genolator to gain new biological insights. The claim of clinical relevance is therefore unsupported.
- **Why it matters** The stated motivation is to advance understanding of disease mechanisms and support clinical research. Without a concrete demonstration of utility, the broader impact claim is not established.
- **Resolution test** Include a case study on a set of proteins with well-characterized functions that were not part of the training set. Compare Genolator's predictions to experimental annotations. Discuss how the natural language interface could be used in a practical research workflow.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1 and Figure 2
- **Evidence pointer** Figure legends
- **Issue** The figures are described as illustrative but the actual content of the conversation and the backend process is not fully explained in the legend. It is unclear what the user is typing and what the model is responding with.
- **Required correction** Expand the figure legends to include a more detailed description of the interaction, including example user queries and model responses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Structural enriched protein sequence embeddings with PST"
- **Evidence pointer** Methods section
- **Issue** The description of the PST model is brief. It is not clear how the PST model differs from the standard ESM2 model in terms of architecture and training. The reference to Hartout et al. is helpful but a brief summary of the key innovation would improve readability.
- **Required correction** Add a sentence or two summarizing how PST incorporates structural information into sequence embeddings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Construction of custom QA datasets"
- **Evidence pointer** Methods section
- **Issue** The process of generating QA pairs with GPT 4.1 is described but the specific prompts used for generation are not shown. The quality control process (e.g., how "accepted," "declined," or "review" annotations were reconciled) is not described.
- **Required correction** Include the generation prompts in the supplementary material and describe the inter-annotator agreement or reconciliation process.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion of cosine similarity values
- **Evidence pointer** Section "The Genolator implicitly learns the different categories of the GO-hierarchy"
- **Issue** The manuscript reports cosine similarity values but does not explain the scale or what constitutes a "low" or "high" value in this context. The interpretation of these values is not intuitive for a non-specialist reader.
- **Required correction** Provide context for the cosine similarity values, such as the range of values observed across all term pairs and what values would be expected for unrelated terms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table is described as having green highlights for best performance, but the table itself is not visible in the provided text. It is unclear which metrics are reported and for which models.
- **Required correction** Ensure the table is included in the final version and that all column and row headers are clearly defined.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Discussion of GPT 4.1 limitations
- **Evidence pointer** Section "The non-finetuned publicly available GPT 4.1 model (falsely) remembers genomic data and struggles with the concept of sequence similarity"
- **Issue** The case study with GPT 4.1 is interesting but the sample size is very small (three genes). The conclusions drawn about GPT 4.1's limitations are based on anecdotal evidence.
- **Required correction** Acknowledge the limited sample size and consider expanding the case study or framing it as a preliminary observation.

## Risk / unsupported claims
- The claim that Genolator "outperforms" GPT 4.1 and XGBoost is not fully supported due to the confounded evaluation design and missing methodological details.
- The claim that the hidden representations are "biologically plausible" is based on qualitative visual inspection and lacks quantitative validation.
- The claim of clinical relevance and enhanced accessibility is not demonstrated with any real-world use case.
- The reported overlap rates for open-ended questions are not calibrated against a chance baseline and rely on an unvalidated LLM-as-judge.
- The performance of the ablated projector-only models is reported but not discussed in sufficient detail to understand the contribution of each modality.
- The manuscript does not report any statistical significance testing for the differences in performance between models.
- The generalizability of the model to proteins with unknown function, which is a stated motivation, is not tested.