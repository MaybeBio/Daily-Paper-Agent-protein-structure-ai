## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary material were provided for evaluation
- **Shared manuscript claim summary** The authors present SMartini, an automated pipeline for generating Martini 3 coarse-grained parameters for arbitrary small molecules. The pipeline maps all-atom structures to coarse-grained beads, derives bonded parameters via Boltzmann inversion of atomistic trajectories, and refines these through iterative coarse-grained simulations with distribution-matching. Validation is claimed on a diverse set of small molecules including drug-like compounds, metabolites, and cofactors. The authors state that the pipeline reduces manual effort and enables high-throughput coarse-grained simulations of protein-ligand systems.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark data, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, validation datasets, parameter quality metrics, comparison against existing tools, and implementation details

## Reviewer

- **Overall assessment** The abstract describes a potentially useful tool for the Martini 3 community, addressing a real bottleneck in coarse-grained simulation setup. However, the abstract provides no quantitative evidence of performance, no comparison with existing parametrization approaches, and no details on the scope or limitations of the method. The central claims of accuracy, generality, and practical utility cannot be evaluated from the supplied material. The work may be of interest to computational biophysicists and the Martini user community, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers using Martini 3 for coarse-grained simulations of biomolecular systems, particularly those studying protein-ligand interactions, membrane-associated small molecules, or large ligand libraries. The tool could also appeal to method developers in the coarse-grained force field community and to groups performing high-throughput screening or drug discovery at coarse-grained resolution.
- **Major strengths** The problem addressed is relevant and timely, as automated parametrization for Martini 3 remains a practical challenge. The proposed workflow, combining Boltzmann inversion with iterative distribution-matching refinement, is a sensible and established strategy. The stated goal of enabling high-throughput parametrization of ligand libraries addresses a clear community need.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The pipeline is validated on a diverse set of small molecules including drug-like compounds, metabolites, and cofactors
  - **Evidence pointer** Abstract, validation statement; location not provided
  - **Concern** The abstract states that validation was performed on a diverse set of molecules but provides no quantitative results, no list of molecules, no comparison against reference data, and no metrics for accuracy or convergence. Without these details, the claim of successful validation is unsupported.
  - **Why it matters** The central value proposition of the tool is that it produces reliable parameters for arbitrary small molecules. If the validation set is small, biased, or the accuracy metrics are weak, the generality claim collapses. The reader cannot assess whether the method works for their molecule of interest.
  - **Resolution test** Provide the full validation dataset, quantitative accuracy metrics (for example, distribution overlap measures, RMSD of bonded distributions, or free energy comparisons), and a comparison against existing tools or manually parametrized references.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generality claim
  - **Claim pointer** The pipeline maps the all-atom molecule onto a coarse-grained bead representation and automatically fits both bonded and non-bonded parameters for arbitrary small molecules
  - **Evidence pointer** Abstract, method description; location not provided
  - **Concern** The claim of applicability to arbitrary small molecules is broad. The abstract does not describe how bead typing is assigned, how ring systems or conjugated moieties are handled, how charged or highly polar groups are treated, or what failure modes exist. Many small molecules of pharmaceutical interest contain features that are notoriously difficult to parametrize in coarse-grained models.
  - **Why it matters** If the method fails for common chemical motifs, the practical utility is substantially reduced. The abstract gives no indication of the chemical space covered or the limitations of the approach.
  - **Resolution test** Describe the bead typing rules, list known limitations or failure cases, and provide coverage statistics across a large chemical library. If the method is truly general, demonstrate this on a diverse and challenging test set.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Comparative performance
  - **Claim pointer** SMartini makes automated parametrization of large ligand libraries practical and reduces the manual effort required for coarse-grained model development
  - **Evidence pointer** Abstract, final claim; location not provided
  - **Concern** No comparison is made against existing parametrization tools for Martini 3, such as the official Martini 3 small molecule parametrization protocols or other automated pipelines. The claim of reduced manual effort and practical utility requires a benchmark showing time savings, success rates, and parameter quality relative to current practice.
  - **Why it matters** The field already has tools and protocols for Martini parametrization. A new tool must demonstrate clear advantages or at least comparable quality with reduced effort. Without a comparative benchmark, the practical contribution is unclear.
  - **Resolution test** Provide a benchmark comparing SMartini against existing approaches in terms of wall-clock time, user intervention required, success rate across a test set, and quality of the resulting parameters as measured by reproducing reference properties.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Method description
  - **Evidence pointer** Abstract, method description; location not provided
  - **Issue** The abstract does not state whether the pipeline is open source, where the code is available, or what the software dependencies are.
  - **Required correction** State the software availability, license, and distribution platform in the abstract or clearly indicate where this information can be found.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Convergence criteria
  - **Evidence pointer** Abstract, refinement description; location not provided
  - **Issue** The abstract mentions refinement until the coarse-grained ensemble reproduces the all-atom reference within tolerance, but the tolerance is not defined.
  - **Required correction** Specify the convergence criterion or state that this detail is provided in the full manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scope clarity
  - **Affected element** Target user base
  - **Evidence pointer** Abstract, final statement; location not provided
  - **Issue** The abstract mentions protein-ligand systems but does not clarify whether the pipeline handles covalent ligands, cofactors bound covalently, or only non-covalent small molecules.
  - **Required correction** Clarify the scope of supported systems or state that only non-covalent small molecules are currently supported.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract provides no quantitative validation data, no demonstration of generality across chemical space, and no comparative benchmark against existing tools. These are required to establish the central claims of the work.
- **Assessment against Nature-style criteria** Originality: the combination of Boltzmann inversion with iterative refinement for Martini 3 is not conceptually new, but the specific implementation may offer practical advantages. Scientific importance: potentially high for the coarse-grained simulation community, but the importance cannot be assessed without evidence of broad applicability and improved performance. Interdisciplinary readership: the work would appeal to computational chemists, biophysicists, and possibly medicinal chemists, but the abstract does not frame the work for a broad audience. Technical soundness: cannot be evaluated from the abstract alone. Readability for nonspecialists: the abstract is clear and accessible, but lacks the quantitative context needed for a general reader to judge significance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible and potentially useful tool, but the central claims of validation, generality, and practical utility are unsupported by quantitative data. A full manuscript with validation results, benchmarks, and clear statements of limitations would be required to assess whether the case can be made.

## Risk / unsupported claims

- The claim that the pipeline is validated on a diverse set of small molecules is unsupported; no validation data are provided.
- The claim that the pipeline works for arbitrary small molecules is unsupported; no coverage analysis or limitation statement is provided.
- The claim that the pipeline reduces manual effort and makes high-throughput parametrization practical is unsupported; no benchmark or comparison is provided.
- The claim that the coarse-grained ensemble reproduces the all-atom reference within tolerance is unverifiable; the tolerance is not defined and no results are shown.
- The overall utility of the tool for protein-ligand simulations is asserted but not demonstrated.