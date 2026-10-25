## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors introduce two new docking benchmark test sets (SB2025, N=1,244; FARMA2025, N=165) and use them to compare three docking programs (DOCK6, Vina, AD4) across pose reproduction, cross-docking, database enrichment, and reverse docking tasks, with emphasis on approved drugs
- **Visible evidence base** Text descriptions of results, tables and figures referenced but not shown in detail, statistical values cited in text (e.g., success rates, AUC values, R² values)
- **Missing materials affecting confidence** Actual figures and tables (Figures 1-6, Tables 1-3, Table S1-S6), supplementary data files, benchmark datasets themselves, and detailed numerical results for all experiments

## Reviewer
- **Overall assessment** This manuscript presents a substantial and potentially valuable contribution to the computational drug discovery field through the introduction of two new benchmark datasets and a systematic comparison of three widely used docking programs. The work addresses an important need for standardized, clinically relevant test sets and provides a comprehensive evaluation framework. However, the current manuscript has several significant issues that need to be addressed, particularly regarding the clarity of the dataset construction methodology, the statistical rigor of the comparisons, and the interpretation of the reverse docking results. The claims about FARMA2025 being the first of its kind and the generalizability of the findings require more careful support. The manuscript would benefit from clearer presentation of the benchmarking protocols and more nuanced discussion of the limitations.

- **Who would be interested in the results, and why** Computational chemists and structural biologists developing or using docking software would be the primary audience. Drug discovery researchers in both academic and industrial settings would find the benchmark datasets and comparative performance data valuable for tool selection and protocol optimization. The FARMA2025 dataset, in particular, would be of interest to those working on drug repurposing and target identification. The methodological framework for benchmarking could also inform future software development efforts.

- **Major strengths** 
  1. Introduction of two new benchmark datasets (SB2025 and FARMA2025) that address gaps in existing test sets, particularly the focus on approved drugs and the alignment with FDA drug target class distributions
  2. Comprehensive benchmarking across four distinct tasks (PR, CD, DE, RD) under standardized conditions
  3. Systematic exploration of key parameters affecting docking outcomes (sampling space, exhaustiveness, charge models, RMSD calculation methods)
  4. The FARMA2025 dataset's design to mirror FDA drug target class distributions is a thoughtful approach to creating a clinically relevant benchmark
  5. The authors' willingness to identify weaknesses in their own software (DOCK6) and explore parameter space is commendable

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology clarity and reproducibility
- **Claim pointer** The manuscript claims to introduce "a calculation-ready set of 1,244 protein-ligand complexes" and that these are "freely available" for download
- **Evidence pointer** Methods section, "SB2025 Test Set Criteria" and "File Preparation for Energy Minimization and Docking" sections; location not provided
- **Concern** The description of how the SB2025 dataset was constructed is insufficiently detailed. While the authors mention criteria for inclusion (resolution, non-covalent binding, etc.), the specific workflow for how structures were selected, processed, and validated is not fully described. The claim that the dataset is "calculation-ready" requires a clear description of the exact preparation pipeline, including protonation state assignment, charge calculation methods, and any manual curation steps. Without this detail, other researchers cannot reproduce the dataset construction or fully understand potential biases in the benchmark.
- **Why it matters** The value of a benchmark dataset depends entirely on its construction methodology. If the preparation pipeline is not fully specified, users cannot assess whether the dataset is appropriate for their specific applications, and the reproducibility of the benchmarking results is compromised. This is particularly important given the authors' claim that this dataset improves upon previous versions.
- **Resolution test** The authors should provide a complete, step-by-step description of the dataset construction pipeline, including all software tools, parameters, and decision criteria used. Ideally, this would include a flowchart or pseudocode of the preparation process, and the exact commands or scripts used should be made available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of comparisons
- **Claim pointer** The manuscript states that "Averaged PR success rate across triplicate runs for DOCK6 was slightly improved compared to Vina (followed by AD4)" and makes similar comparative claims for CD, DE, and RD
- **Evidence pointer** Results sections for PR, CD, DE, and RD; location not provided
- **Concern** The statistical analysis of the differences between programs appears to be limited to reporting means and standard deviations. The manuscript does not describe any formal statistical testing (e.g., paired t-tests, Wilcoxon signed-rank tests, or ANOVA) to determine whether the observed differences between programs are statistically significant. Given the relatively small differences reported (e.g., 74.6% vs 71.0% for PR), it is unclear whether these differences are meaningful or within the range of random variation. Additionally, the manuscript does not discuss the distribution of results across the different protein families or ligand types, which could reveal important interaction effects.
- **Why it matters** The primary contribution of this work is the comparative benchmarking of three docking programs. Without proper statistical analysis, readers cannot determine whether the observed differences are robust or merely artifacts of the specific test set composition. This is particularly important for practical recommendations about which program to use for specific applications.
- **Resolution test** The authors should perform appropriate statistical tests to compare the performance of the three programs across all benchmarks. This should include both overall comparisons and analyses stratified by protein class or ligand properties. The results of these tests should be reported with appropriate effect sizes and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of reverse docking results
- **Claim pointer** The manuscript claims that "Challenging RD tests using FARMA2025, which gauge the ability to correctly rank the cognate structure best, indicate that generating the correct ligand pose is necessary but not sufficient"
- **Evidence pointer** Results section, "Reverse Docking (RD)" subsection; location not provided
- **Concern** The interpretation of the RD results as showing that "generating the correct ligand pose is necessary but not sufficient" is not well supported by the data presented. The manuscript reports CFR rates of 28.5% (DOCK6), 20.0% (Vina), and 10.9% (AD4), and PA-CFR rates of 91.5%, 90.9%, and 77.8% respectively. However, the relationship between pose accuracy and ranking accuracy is not systematically analyzed. The claim that pose accuracy is "necessary" would require demonstrating that cases where the correct pose is generated but the ranking is incorrect are systematically different from cases where both pose and ranking are correct. The current analysis does not provide this level of detail.
- **Why it matters** The RD results are presented as a key finding of the study, and the interpretation has implications for how researchers should approach target identification and drug repurposing studies. If the claim is not well supported, it could lead to incorrect conclusions about the utility of docking for these applications.
- **Resolution test** The authors should provide a more detailed analysis of the RD results, including a breakdown of cases where pose generation succeeded but ranking failed, and vice versa. They should also discuss potential reasons for these discrepancies and whether they relate to scoring function limitations or other factors.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The manuscript states that "the PR studies suggest that DOCK6 performed best using a larger search space and AD4 performed best using a smaller search space" and makes similar generalizable claims about program performance
- **Evidence pointer** Results sections for PR and DE; location not provided
- **Concern** The benchmarking was performed using specific versions of each program (DOCK6.12, Vina 1.1.2, AD4.2.6) with specific parameter settings. The manuscript does not adequately discuss how these findings might generalize to other versions of these programs or to other docking software. Additionally, the choice of test set composition (e.g., the specific protein families and ligand types included) may limit the generalizability of the findings. The authors acknowledge this to some extent but do not provide a thorough discussion of the limitations.
- **Why it matters** Readers may be tempted to use these results to make decisions about which docking program to use for their specific applications. Without a clear discussion of the limitations and potential biases in the benchmarking, these decisions may be based on incomplete information.
- **Resolution test** The authors should include a more detailed discussion of the limitations of their benchmarking approach, including how the specific program versions, parameter settings, and test set composition might affect the generalizability of their findings. They should also discuss how their results compare to other published benchmarking studies.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and significance of FARMA2025
- **Claim pointer** The manuscript claims that FARMA2025 "closely mirrors the distribution of FDA drug target classes for small molecules through 2023 (r² = 0.72)" and implies this is a novel contribution
- **Evidence pointer** Abstract and Results section, "Test Set Protein Class Composition" subsection; location not provided
- **Concern** While the concept of a drug-focused benchmark dataset is valuable, the manuscript does not adequately demonstrate the novelty of FARMA2025 compared to existing drug-focused benchmark sets. The authors mention that FARMA2025 is "the first of its kind" but do not provide a comprehensive comparison with other available drug-focused test sets. Additionally, the r² value of 0.72, while indicating a reasonable correlation, also indicates that 28% of the variance is unexplained, which could represent significant biases in the dataset composition.
- **Why it matters** The claim of novelty is important for establishing the significance of this contribution. If similar datasets already exist, the value of FARMA2025 is diminished. Additionally, understanding the limitations of the dataset composition is crucial for appropriate use.
- **Resolution test** The authors should provide a more comprehensive comparison of FARMA2025 with existing benchmark datasets, including a discussion of what makes it unique. They should also discuss the implications of the r² value and any potential biases in the dataset composition.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure and table references
- **Affected element** Results and Discussion sections
- **Evidence pointer** Multiple locations throughout Results and Discussion; location not provided
- **Issue** The manuscript frequently references figures and tables without providing sufficient context in the text. For example, "Figure 1a–c outlines the three most common experiments" and "Table 1 outlines the eleven CD protein families" do not provide enough information for the reader to understand the key findings without constantly referring to the figures.
- **Required correction** The authors should ensure that each figure and table is accompanied by a clear description of the key findings in the text, rather than simply referring the reader to the figure or table.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple locations; location not provided
- **Issue** The manuscript uses several terms that could be more precisely defined or used consistently. For example, "success rate" is used for PR, but "matrix success rate" and "cognate success rate" are used for CD. The distinction between these terms should be clearly defined and used consistently throughout.
- **Required correction** The authors should provide clear definitions of all key terms and ensure they are used consistently throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of parameter optimization
- **Affected element** Results section, "PR Outcomes Varying Parameters Affecting Ligand Sampling" subsection
- **Evidence pointer** Location not provided
- **Issue** The manuscript reports that varying sampling parameters had little effect on outcomes but does not provide a detailed discussion of why this might be the case. The authors mention that "none of the programs showed meaningful differences in PR success rates using low vs high parameter settings" but do not explore potential reasons for this observation.
- **Required correction** The authors should provide a more detailed discussion of the parameter sensitivity results, including potential explanations for the observed insensitivity and implications for practical use of these programs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of statistical reporting
- **Affected element** Results sections for DE and RD
- **Evidence pointer** Location not provided
- **Issue** The manuscript reports AUC values and other statistical measures but does not consistently report confidence intervals or other measures of uncertainty. This makes it difficult to assess the precision of the reported values.
- **Required correction** The authors should report confidence intervals or other appropriate measures of uncertainty for all key statistical measures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Conclusions section
- **Evidence pointer** Location not provided
- **Issue** The conclusions section is somewhat brief and does not provide a comprehensive discussion of the limitations of the study. While some limitations are mentioned, a more thorough discussion would help readers understand the scope and applicability of the findings.
- **Required correction** The authors should expand the conclusions section to include a more comprehensive discussion of the limitations of their study and the implications for future work.

## Risk / unsupported claims
- The claim that FARMA2025 is "the first of its kind" is not adequately supported without a comprehensive comparison to existing drug-focused benchmark datasets
- The interpretation that "generating the correct ligand pose is necessary but not sufficient" for accurate target ranking in RD is not fully supported by the data presented
- The claim that the benchmarking results are generalizable across different versions of the programs or to other docking software is not adequately discussed
- The assertion that the SB2025 dataset is "calculation-ready" requires more detailed documentation of the preparation pipeline to be verifiable
- The statement that "one random seed would likely be sufficient" for prospective virtual screens is a strong claim that requires more rigorous statistical support
- The comparison of dataset composition to FDA drug target classes (r² = 0.72) is presented without discussion of the implications of the unexplained variance