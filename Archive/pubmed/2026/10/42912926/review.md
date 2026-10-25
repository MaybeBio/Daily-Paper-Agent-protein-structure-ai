## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present CHAMP, an automated Python-based workflow combining coarse-grained molecular dynamics simulations with dual analysis of contact persistence and spatial density to identify cholesterol-binding hot spots at protein-membrane interfaces. The protocol is claimed to require limited user intervention, enable consistent and reproducible analyses across targets, and is validated on the serotonin transporter and cannabinoid receptor 1 (CB1), recovering known cholesterol-binding regions and identifying a potential additional site in CB1. The protocol is also applied to the CB1 negative allosteric modulator Org27569 to demonstrate generality beyond sterols.
- **Visible evidence base** Abstract text only; no quantitative results, simulation parameters, validation metrics, or comparative benchmarks are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation setup details, validation datasets, statistical analyses, and any comparison against existing methods

## Reviewer
- **Overall assessment** The abstract presents a potentially useful computational protocol for mapping cholesterol-binding hot spots in membrane proteins. The methodological concept is reasonable and the choice of validation targets is sensible given prior literature. However, the abstract provides no quantitative evidence of performance, no details on how "recovery" of known sites was assessed, and no comparison against existing approaches. The claim of generality based on a single additional application to a small-molecule ligand is not sufficiently supported. The work may be of interest to the computational biophysics and membrane protein communities, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Computational biophysicists and cheminformaticians working on membrane protein-lipid interactions would be the primary audience. Researchers studying cholesterol modulation of membrane proteins, particularly transporters and GPCRs, may find the protocol useful for generating hypotheses about interaction sites. Developers of automated analysis workflows for molecular dynamics simulations may also be interested in the methodological contribution.
- **Major strengths** The protocol addresses a real need for automated, reproducible identification of cholesterol-binding sites across multiple membrane protein systems. The dual analysis approach combining contact persistence and spatial density is conceptually sound. The emphasis on limited user intervention and cross-target consistency is a practical advantage. The validation on two distinct protein classes and the extension to a non-sterol ligand suggest potential breadth.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The combination of contact persistence and spatial density analysis in an automated workflow is a modest methodological increment rather than a conceptual breakthrough. Similar approaches for mapping lipid interaction sites exist in the literature, and the novelty appears to lie in the specific integration and automation rather than in a fundamentally new principle.  
  Scientific importance: The problem of identifying cholesterol-binding sites is relevant, but the abstract does not demonstrate that CHAMP provides a significant advance over existing methods. The importance of the claimed findings cannot be assessed without quantitative validation.  
  Interdisciplinary readership: The work sits at the interface of computational chemistry, biophysics, and membrane biology. The abstract is written in a way that is accessible to specialists in these areas, but the lack of quantitative results limits its appeal to a broader readership.  
  Technical soundness: The methodological logic is plausible, but no technical details are provided to assess the soundness of the implementation, the choice of simulation parameters, or the statistical treatment of the results.  
  Readability for nonspecialists: The abstract is clearly written and the workflow is described in understandable terms. However, the absence of concrete outcomes makes it difficult for a nonspecialist to gauge the practical utility of the protocol.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a reasonable protocol and plausible applications, but without quantitative validation data, methodological details, or comparison to existing tools, the claims of recovery, identification, and generality cannot be evaluated. A supportive posture would require the full manuscript to demonstrate robust performance.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The protocol "recovers known cholesterol-binding regions reported in experimental and computational studies" for the serotonin transporter and CB1.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract states that known cholesterol-binding regions are recovered but provides no quantitative measure of recovery. It is unclear whether recovery means partial overlap, full spatial coincidence, or statistical enrichment. No metrics such as distance thresholds, overlap coefficients, or false positive rates are given.  
- **Why it matters** The central validation claim of the protocol rests on this recovery. Without a defined and quantified criterion for what constitutes successful recovery, the claim is unfalsifiable and cannot be compared against other methods.  
- **Resolution test** Provide a clear definition of recovery (e.g., fraction of known sites identified within a specified distance threshold), report the numerical values for both validation targets, and include a comparison against a null model or an existing method.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The protocol "identifies a potential additional interaction site" in the CB1 system.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The identification of a potential additional site is presented as a finding, but no evidence is provided to support its biological relevance. It is not stated whether this site has any prior experimental or computational support, whether it is statistically significant relative to noise, or whether it is reproducible across independent simulations.  
- **Why it matters** A novel predicted site is only meaningful if it can be distinguished from false positives and if some rationale for its potential functional relevance is provided. Without this, the claim is speculative.  
- **Resolution test** Report the statistical significance of the predicted site relative to background density, state whether it has any prior literature support, and discuss its potential functional relevance in the context of CB1 biology.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The application to Org27569 shows that CHAMP "can capture relevant interaction hot spots beyond sterol molecules."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not specify what "relevant" means in this context. It is not stated whether the identified hot spots for Org27569 correspond to known binding sites, whether they are supported by experimental data, or whether they are merely spatially clustered regions with no demonstrated functional significance. A single application to one ligand is insufficient to establish generality.  
- **Why it matters** The claim of generality beyond sterols is a key part of the protocol's potential utility. Without a defined relevance criterion and without multiple test cases, the claim is not supported.  
- **Resolution test** Define the criterion for relevance (e.g., overlap with known binding site, correlation with mutational data), report the results for Org27569 against that criterion, and ideally include at least one additional non-sterol ligand to demonstrate consistency.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological transparency  
- **Claim pointer** The protocol "requires limited user intervention and is designed to enable consistent and reproducible analyses across different targets."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract makes claims about automation and reproducibility but provides no information on the specific parameters that must be set by the user, the computational cost, the sensitivity of results to parameter choices, or the variability across replicate runs.  
- **Why it matters** Reproducibility and ease of use are central selling points of the protocol. Without evidence on parameter sensitivity and run-to-run variability, these claims cannot be assessed.  
- **Resolution test** Provide a parameter sensitivity analysis, report run-to-run variability for at least one system, and state the computational cost in terms of wall-clock time and resources.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Description of the dual analysis  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states that the protocol combines "contact persistence and spatial density" but does not explain how these two measures are integrated. It is unclear whether they are combined into a single score, used as sequential filters, or treated as independent outputs.  
- **Required correction** Clarify in the abstract or methods how the two analyses are combined and what each contributes to the final hot spot identification.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Validation scope  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions validation on two targets and an additional application to a ligand, but does not state whether any negative controls were included, such as proteins without known cholesterol-binding sites, to assess false positive rates.  
- **Required correction** Include a statement on whether negative controls were used and, if so, report the false positive rate. If not, acknowledge this as a limitation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Software availability  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The protocol is described as an "automated Python-based workflow," but the abstract does not state whether the code is publicly available, under what license, or whether documentation and example inputs are provided.  
- **Required correction** State the software availability, including repository URL, license, and any dependencies, in the abstract or a data availability statement.

## Risk / unsupported claims
- The claim that CHAMP "recovers known cholesterol-binding regions" is unsupported without quantitative recovery metrics.
- The claim that a "potential additional interaction site" is identified in CB1 is unsupported without statistical or biological evidence.
- The claim that the protocol "can capture relevant interaction hot spots beyond sterol molecules" is unsupported without a defined relevance criterion and additional test cases.
- The claims of limited user intervention and cross-target reproducibility are not assessable from the abstract.
- The general utility of the protocol for "large-scale and comparative studies" is speculative and not supported by any demonstration of scalability.