## Review setup
- **Input scope** Abstract
- **Assessment boundary** Claims and evidence presented in the abstract only
- **Shared manuscript claim summary** The authors present PLI-Parallax, a deposited dataset of predicted and experimental protein-ligand coordinates with distance labels, designed to provide calibrated per-system confidence measures for predicted complexes. The dataset includes 307 million distance records across two tiers (crystal and corpus), uses inter-method agreement to predict label accuracy, and provides split-conformal intervals. The deposit also includes 646 evaluation configurations across seven data split families, with 631 reporting two-sample test separation, and 906 protein accessions partitioned to control sequence leakage.
- **Visible evidence base** Abstract text only; no figures, tables, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, figures, tables, supplementary data, code repository, dataset access details, and any experimental validation results

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable resource for the structural biology and computational drug discovery communities. The core idea—using inter-method agreement to calibrate confidence in predicted protein-ligand geometries—is conceptually sound and addresses a recognized gap. However, the abstract is dense and lacks sufficient detail to evaluate the technical validity, statistical rigor, and practical utility of the proposed approach. Key claims about calibration, coverage, and generalisation are stated without supporting evidence or methodological justification. The assessment is therefore provisional, pending full manuscript review.

- **Who would be interested in the results, and why** Computational structural biologists, drug discovery researchers, and developers of protein-ligand prediction methods. The dataset could serve as a benchmark for evaluating prediction tools and as a resource for training confidence models. The split-conformal intervals and evaluation splits are of direct interest to practitioners needing reliable uncertainty estimates for predicted complexes.

- **Major strengths** 1. Addresses a clear and important gap: the lack of calibrated, per-system confidence measures for predicted protein-ligand geometries. 2. Large-scale dataset (307 million distance records) with both experimental and predicted data, enabling calibration and evaluation. 3. Use of inter-method agreement as a signal for accuracy is a well-motivated approach. 4. Inclusion of multiple evaluation splits (including protein-cold) and two-sample tests for leakage control is methodologically rigorous.

- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Statistical validity / calibration
    - **Claim pointer** "On the crystal tier that interval covers observed accuracy at the stated rate."
    - **Evidence pointer** Abstract only; no figure or table provided
    - **Concern** The abstract claims that the split-conformal interval achieves nominal coverage on the crystal tier, but provides no quantitative results (e.g., coverage rate, interval width, calibration plot). Without these, the claim is unverifiable.
    - **Why it matters** Calibration is the central claim of the work. If the intervals do not achieve the stated coverage, the entire premise of providing "practically usable per-system measures" is undermined.
    - **Resolution test** Provide a calibration plot (e.g., empirical coverage vs. nominal level) for the crystal tier, along with interval width statistics. Report the exact coverage rate achieved at the stated nominal level.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Generalisation / transferability
    - **Claim pointer** "On the corpus tier it ranks systems by expected label quality, since both distributions differ."
    - **Evidence pointer** Abstract only
    - **Concern** The abstract states that the interval ranks systems on the corpus tier, but does not explain how this ranking is validated or what metric is used to assess ranking quality. The claim that "both distributions differ" is vague and does not justify the transfer of calibration from the crystal to the corpus tier.
    - **Why it matters** The corpus tier is where the method is most needed (no ground truth). Without a validation strategy for ranking quality, the practical utility of the intervals on this tier is unclear.
    - **Resolution test** Describe the validation approach for ranking on the corpus tier (e.g., using held-out experimental data, synthetic benchmarks, or cross-validation). Report a ranking metric (e.g., Spearman correlation, AUC for identifying correct vs. incorrect complexes).

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Reproducibility / data access
    - **Claim pointer** "The deposit is accompanied by 646 evaluation configurations across seven data split families, and 631 of them report how far their training and test entities separate under a two-sample test."
    - **Evidence pointer** Abstract only
    - **Concern** The abstract does not specify what the 15 missing configurations are, why they are missing, or whether this affects the completeness of the evaluation. The two-sample test used is not named, and the threshold for "separation" is not defined.
    - **Why it matters** Reproducibility and completeness of the evaluation are critical for a resource paper. Missing configurations and undefined metrics reduce confidence in the reported results.
    - **Resolution test** List the 15 missing configurations and explain their absence. Name the two-sample test (e.g., Kolmogorov-Smirnov, Wasserstein distance) and state the threshold used to define separation.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The phrase "predicted label accuracy together with a split-conformal interval" is ambiguous. It is unclear whether the interval is on the label accuracy itself or on the predicted geometry.
    - **Required correction** Clarify: e.g., "each system carries a predicted label (e.g., correct/incorrect) together with a split-conformal interval on the probability that the label is correct."

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Readability
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The abstract is dense with numbers (307,314,646, 30,567, 646, 631, 906) without context. It is difficult for a nonspecialist to assess the significance of these numbers.
    - **Required correction** Provide brief context for key numbers (e.g., "30,567 systems, out of 31,746 in the corpus tier, carry predicted label accuracy").

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The term "cross-docked pairs" is used without definition. It may be unclear to readers outside the docking community.
    - **Required correction** Define "cross-docked" (e.g., "pairs where a ligand is docked into a receptor structure that was not co-crystallised with that ligand").

- **Technical failings that need to be addressed before the case is established** R1-M1 (calibration claim unverified), R1-M2 (ranking validation missing)

- **Assessment against Nature-style criteria** 
    - **Originality**: Moderate. The idea of using inter-method agreement for calibration is not entirely novel, but the scale and systematic nature of the dataset are original.
    - **Scientific importance**: High, if the calibration claims hold. The resource could significantly impact how predicted protein-ligand geometries are used in practice.
    - **Interdisciplinary readership**: Moderate. The work is primarily of interest to computational structural biologists and drug discovery researchers; broader appeal is limited without clear biological or chemical insights.
    - **Technical soundness**: Cannot be assessed from the abstract alone. The calibration and ranking claims are unverified.
    - **Readability for nonspecialists**: Poor. The abstract is dense and uses jargon without explanation. A nonspecialist would struggle to understand the key contributions.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising resource, but the central claims about calibration and ranking are unverifiable without the full manuscript. A supportive recommendation would require the full manuscript to demonstrate that the split-conformal intervals achieve nominal coverage and that the ranking on the corpus tier is validated.

## Risk / unsupported claims
- "On the crystal tier that interval covers observed accuracy at the stated rate." — Unsupported; no quantitative evidence provided.
- "On the corpus tier it ranks systems by expected label quality." — Unsupported; no validation strategy or metric provided.
- "The 906 protein accessions were partitioned to control sequence leakage, so a protein-cold split here tests generalisation across sequence space." — Unsupported; no evidence that the partition effectively controls leakage (e.g., sequence identity thresholds, clustering method).