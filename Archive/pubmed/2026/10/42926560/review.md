## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose that the performance gap between deep learning models on orthosteric versus allosteric protein–ligand binding pose prediction is explained by local energy landscape topology, specifically the magnitude of frustration quenching upon ligand binding and the network centrality of binding sites. They further claim that generative diffusion models outperform single-shot regression because multi-pose sampling is required to cross energy barriers, and that frustration quenching magnitude and structural network centrality serve as physical descriptors of AI performance limits.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark descriptions, dataset details, or statistical analyses are visible
- **Missing materials affecting confidence** Full manuscript, methods, figures, tables, benchmark definitions, dataset curation details, model specifications, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing hypothesis that links protein energy landscape physics to deep learning performance in binding pose prediction. The framing of the allosteric "blind spot" as a physical property rather than an algorithmic defect is potentially valuable. However, the abstract provides no quantitative evidence, no methodological detail, and no specific results that would allow assessment of whether the claims are supported. The central assertions, while plausible, are presented as conclusions without visible supporting data. The manuscript cannot be evaluated for technical soundness from the supplied material.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists interested in energy landscape theory would find the frustration-based framework relevant. Machine learning researchers developing protein–ligand docking and co-folding models would be interested in the proposed physical descriptors of model performance limits. Drug discovery scientists using AI-based pose prediction tools would benefit from understanding when and why these tools fail at allosteric sites. The work could also interest researchers studying protein allostery and network analysis of protein structures.
- **Major strengths** The hypothesis is clearly articulated and conceptually novel, connecting frustration theory and network topology to AI model performance in a way that reframes a known empirical limitation as a physically grounded phenomenon. The proposed distinction between generative and regression approaches in terms of energy barrier crossing is mechanistically sensible. The abstract is well written and accessible to a broad interdisciplinary audience.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: The frustration-based explanation for AI pose prediction performance differences appears original and potentially significant. However, originality cannot be fully assessed without seeing how the authors distinguish their framework from prior work on energy landscape analysis of binding sites.
  - Scientific importance: If substantiated, the findings could provide a predictive framework for when deep learning models will succeed or fail at specific binding sites, which would be valuable for both fundamental biophysics and applied drug discovery. The importance is high but conditional on evidence.
  - Interdisciplinary readership: The topic bridges machine learning, biophysics, and structural biology, and the abstract is written in a way that nonspecialists in each field could follow. The potential readership is broad.
  - Technical soundness: Cannot be assessed from the abstract alone. No methods, data, or statistical analyses are visible.
  - Readability for nonspecialists: The abstract is well structured and uses accessible language, though terms such as "frustration quenching" and "betweenness" may require some background. Overall readability is good.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and the framing is compelling, but the abstract contains no quantitative results or methodological detail. A supportive posture would require the full manuscript to demonstrate that the claims are backed by rigorous benchmarking, appropriate statistical analysis, and robust validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "AI prediction success strongly tracks frustration quenching" and that this explains the orthosteric versus allosteric performance gap.
- **Evidence pointer** Abstract only; no figures, tables, or quantitative results provided
- **Concern** The central claim of the paper is presented without any visible quantitative support. No correlation coefficients, performance metrics, statistical significance values, or comparative benchmarks are reported in the abstract. The reader cannot assess the strength of the relationship between frustration quenching and prediction success, nor whether the proposed explanation is statistically robust.
- **Why it matters** This is the foundational claim of the manuscript. Without quantitative evidence demonstrating a strong and statistically significant relationship between frustration quenching and model performance, the entire framework rests on assertion rather than demonstration. The claim that this relationship "defines the intrinsic limits of AI performance" requires rigorous statistical validation across multiple datasets and models.
- **Resolution test** The full manuscript must provide quantitative measures of frustration quenching for each binding site, corresponding model performance metrics, and a statistical analysis demonstrating the strength and significance of the relationship. Ideally, this would include correlation analyses, effect sizes, and validation across independent datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that they evaluated "leading co-folding and docking paradigms across curated benchmarks and large-scale uncurated datasets" and compared "generative diffusion with single-shot regression."
- **Evidence pointer** Abstract only; no methods section, model list, or dataset descriptions provided
- **Concern** The abstract provides no information about which specific models were evaluated, how benchmarks were curated, what constitutes "large-scale uncurated datasets," or how the generative and regression approaches were compared. Without this information, the reader cannot evaluate whether the model selection was representative, whether the benchmarks were appropriate, or whether the comparison was fair and controlled.
- **Why it matters** The conclusions about model performance and the necessity of multi-pose sampling depend entirely on the specific models and datasets used. If the model selection was biased or the benchmarks were not representative, the conclusions could be artifacts of the specific evaluation setup. Reproducibility and generalizability cannot be assessed without methodological detail.
- **Resolution test** The full manuscript must provide a complete list of models evaluated, detailed descriptions of benchmark construction and dataset curation, and a clear explanation of the comparison protocol including hyperparameters, training procedures, and evaluation metrics. The methods should be sufficiently detailed to allow independent replication.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that "multi-pose sampling capacity is required to cross energy barriers and discover the frustration funnel, whereas joint receptor–ligand coordinate co-adaptation governs local optimization within the funnel."
- **Evidence pointer** Abstract only; no mechanistic or ablation studies visible
- **Concern** The abstract asserts a mechanistic explanation for why generative diffusion models outperform single-shot regression, but no evidence is presented to support this specific causal mechanism. The claim that multi-pose sampling is "required" to cross energy barriers is a strong causal statement that would require ablation studies or controlled experiments isolating the effect of sampling strategy from other model differences.
- **Why it matters** The proposed mechanism distinguishes between two aspects of model design and assigns them distinct functional roles. If this mechanistic claim is incorrect, the practical recommendations that might follow from it would be misguided. The claim that sampling capacity is "required" is particularly strong and demands direct evidence.
- **Resolution test** The full manuscript must include controlled comparisons that isolate the effect of sampling strategy, such as ablations where a generative model is restricted to single-pose output or where a regression model is augmented with multi-pose sampling. Ideally, the authors would also provide evidence that the proposed mechanism operates as described, for example through analysis of intermediate sampling trajectories or energy landscape exploration behavior.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology clarity
- **Affected element** Abstract, term "frustration quenching"
- **Evidence pointer** Abstract, first paragraph
- **Issue** The term "frustration quenching" is used as a central concept but is not defined in the abstract. While specialists in energy landscape theory may be familiar with the concept, the interdisciplinary readership of this work may not have sufficient background to understand what is meant by the magnitude of frustration quenching and how it is measured.
- **Required correction** Provide a brief operational definition of frustration quenching in the abstract, such as a one-sentence explanation of how it is quantified and what it represents physically.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Quantitative reporting
- **Affected element** Abstract, performance claims
- **Evidence pointer** Abstract, no specific numbers reported
- **Issue** The abstract states that models "systematically underperform" at allosteric pockets and that "AI prediction success strongly tracks" frustration quenching, but no quantitative magnitudes are given. The reader cannot gauge the size of the performance gap or the strength of the proposed relationship.
- **Required correction** Include representative quantitative values in the abstract, such as the performance difference between orthosteric and allosteric sites and a correlation coefficient or effect size for the frustration quenching relationship.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope clarity
- **Affected element** Abstract, generalizability claims
- **Evidence pointer** Abstract, final sentence
- **Issue** The abstract concludes that frustration quenching and network centrality "define the intrinsic limits of AI performance," which is a very broad claim. It is unclear whether this applies to all deep learning models, all binding sites, and all ligand types, or whether the findings are specific to the models and datasets evaluated.
- **Required correction** Qualify the generalizability claim to reflect the scope of the actual evaluation, such as "for the models and datasets evaluated here" or similar limiting language.

## Risk / unsupported claims
- The claim that "AI prediction success strongly tracks frustration quenching" is unsupported in the abstract, as no quantitative evidence is provided.
- The claim that "multi-pose sampling capacity is required to cross energy barriers" is unsupported, as no mechanistic or ablation evidence is visible.
- The claim that frustration quenching and network centrality "define the intrinsic limits of AI performance" is an overgeneralization that cannot be assessed from the abstract alone.
- The claim that the allosteric "blind spot" is "a quantitative property of energy landscape architecture rather than a defect of any specific predictive framework" is presented as a conclusion but is not supported by any visible data.
- The comparative performance of "leading co-folding and docking paradigms" is asserted but not quantified or described.
- The distinction between generative diffusion and single-shot regression in terms of energy barrier crossing is asserted but not demonstrated.