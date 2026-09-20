## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose DiffEnsemble, a diffusion-based framework that learns latent dynamical representations from static protein structures and integrates AlphaFold-derived structural profiles as conditional guidance, to model protein conformational ensembles. They report benchmarking on 72 protein targets from the ATLAS molecular dynamics simulation dataset, claiming superior performance over BioEmu and AlphaFLOW, with specific improvements of 28.9% and 7.5% in Pearson correlation coefficients for ensemble pairwise root-mean-square deviation and root-mean-square fluctuation, respectively.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or supplementary information were supplied
- **Missing materials affecting confidence** Full manuscript text, methods section, benchmark details, statistical analyses, figure and table contents, dataset construction details, and any code or reproducibility information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of diffusion models to protein conformational ensemble prediction, with a conceptually appealing idea of leveraging static structure databases to infer dynamical properties. However, the evidence provided in the abstract alone is insufficient to evaluate the technical soundness, statistical rigor, or generalizability of the claims. The reported performance improvements are presented without confidence intervals, statistical tests, or methodological details, and the absence of any description of the model architecture, training procedure, or evaluation protocol prevents independent assessment. The core claim that latent dynamical information in static structures can effectively support ensemble modeling is plausible but not established from the supplied material.
- **Who would be interested in the results, and why** Computational structural biologists, researchers working on protein dynamics and conformational sampling, and developers of generative models for biomolecular applications would be interested. The work addresses a recognized challenge in reconstructing conformational ensembles when experimental dynamic data are scarce, and the proposed approach of using static structure databases as a source of dynamical information could be of practical value if validated.
- **Major strengths** The conceptual framing is clear and addresses a relevant problem in structural biology. The use of AlphaFold-derived structural profiles as conditional guidance is a sensible and timely integration of existing resources. The choice of benchmarking against established methods such as BioEmu and AlphaFLOW on the ATLAS dataset provides a reasonable comparative context.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate; the application of diffusion models to conformational ensembles is not entirely new, though the specific use of static structure-derived latent dynamics as conditioning is a distinctive angle. Scientific importance is potentially high if the claims hold, given the broad relevance of conformational ensembles to function and drug design. Interdisciplinary readership is plausible, spanning structural biology, machine learning, and biophysics. Technical soundness cannot be assessed from the abstract alone, as no methodological or statistical details are provided. Readability for nonspecialists is adequate, with the abstract being concise and accessible, though some terms such as "latent dynamical representations" and "conditional diffusion" may require prior familiarity.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but the absence of methodological and statistical detail precludes a supportive recommendation. A full manuscript with detailed methods, validation, and statistical analysis would be required to assess the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that DiffEnsemble outperforms BioEmu and AlphaFLOW, with specific improvements of 28.9% and 7.5% in Pearson correlation coefficients for ensemble pairwise root-mean-square deviation and root-mean-square fluctuation, respectively.
- **Evidence pointer** Abstract, location not provided
- **Concern** The performance improvements are reported as single point estimates without any indication of variance, confidence intervals, or statistical significance testing. It is unclear whether these improvements are consistent across the 72 targets or driven by a subset. No information is provided on how the Pearson correlations were computed, whether they are averaged per target or pooled, or whether the differences are statistically meaningful.
- **Why it matters** Without measures of uncertainty or statistical testing, the reported improvements cannot be distinguished from noise. The claim of superiority over existing methods is central to the paper's contribution, and unsupported performance claims undermine the credibility of the entire study.
- **Resolution test** Provide confidence intervals or standard errors for the reported metrics, perform appropriate statistical tests (for example paired tests across the 72 targets), and report per-target distributions of the correlation coefficients. If the improvements are not uniformly observed, discuss the conditions under which DiffEnsemble performs better or worse.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The claim that DiffEnsemble learns latent dynamical representations from static protein structures in the Protein Data Bank and integrates the structural profile derived from the AlphaFold Protein Structure Database as conditional guidance during the diffusion process.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no description of the model architecture, the nature of the latent dynamical representations, how they are learned from static structures, or how the AlphaFold-derived structural profile is integrated as conditioning. There is no information on the training data, the preprocessing steps, the diffusion process specifics, or the inference procedure.
- **Why it matters** The methodological novelty is a key selling point of the work, but without any technical detail, the approach cannot be evaluated for soundness, reproducibility, or novelty relative to existing diffusion-based methods. Readers cannot determine whether the proposed framework is genuinely distinct or a minor variation of existing approaches.
- **Resolution test** Provide a detailed methods section describing the model architecture, training procedure, conditioning mechanism, and inference protocol. Include sufficient detail to allow replication, and clarify what specifically constitutes the "latent dynamical representations" and how they are derived from static structures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation scope
- **Claim pointer** The claim that benchmarking on 72 protein targets from the ATLAS molecular dynamics simulation dataset demonstrates that DiffEnsemble outperforms existing methods.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports results on a single benchmark dataset. No information is provided on the diversity of the 72 targets in terms of size, fold class, conformational flexibility, or functional relevance. It is unclear whether the benchmark includes targets with large-scale conformational changes, intrinsically disordered regions, or other challenging features that would test the method's generalizability. Additionally, no comparison is made to experimental data or to the quality of the generated ensembles in terms of physical plausibility beyond the two reported metrics.
- **Why it matters** Performance on a single dataset, even with multiple targets, may not generalize to the broader space of proteins. The claim that the method effectively models conformational ensembles requires evidence that the generated ensembles are physically realistic and biologically meaningful, not just that they correlate with simulation-derived metrics on a selected benchmark.
- **Resolution test** Describe the composition of the 72 targets and justify their representativeness. Include additional validation on independent datasets or experimental data where available. Report additional metrics that assess physical plausibility, such as Ramachandran plot distributions, clash scores, or agreement with experimental observables such as chemical shifts or SAXS profiles.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** "latent dynamical representations"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "latent dynamical representations" is used without definition or context. It is unclear whether this refers to a learned embedding of conformational states, a reduced-dimensional representation of dynamics, or something else.
- **Required correction** Define the term explicitly in the abstract or introduction, and clarify how these representations relate to physical dynamics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of comparison
- **Affected element** Benchmarking against BioEmu and AlphaFLOW
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that DiffEnsemble outperforms BioEmu and AlphaFLOW but does not specify the performance of these baselines on the same metrics. Without baseline values, the magnitude of the improvement is difficult to contextualize.
- **Required correction** Report the baseline performance values alongside the DiffEnsemble results, or provide a figure or table showing the comparison.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Abstract, location not provided
- **Concern** No mention is made of code availability, model weights, or access to the trained models. For a computational method, reproducibility is a key consideration.
- **Required correction** State in the abstract or a data availability statement whether code and models will be made publicly available, and if so, under what license.

## Risk / unsupported claims
- The claim of superiority over BioEmu and AlphaFLOW is unsupported due to the absence of statistical testing, confidence intervals, and baseline values.
- The claim that latent dynamical information embedded in static structural data can effectively support ensemble modeling is not established, as no mechanistic or ablative evidence is provided to support this interpretation.
- The generalizability of the method beyond the 72 ATLAS targets is unassessable from the supplied material.
- The physical plausibility of the generated ensembles is not demonstrated, as only correlation-based metrics are reported.
- The methodological novelty relative to existing diffusion-based approaches cannot be evaluated without a methods description.