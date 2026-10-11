## Review setup

- **Input scope** Abstract only (title, author list, and arXiv metadata provided; no full text, figures, tables, or supplementary materials)
- **Assessment boundary** Assessment limited to the claims and evidence visible in the abstract; no methodological details, experimental results, or code availability can be verified
- **Shared manuscript claim summary** The authors propose La-Ribo, a method for RNA co-design (sequence and structure) using geometry-latent flow matching. The abstract claims that this approach enables joint generation of RNA sequence and 3D structure, and implies improved performance over existing methods.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark comparisons, or implementation details are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, method description, experimental setup, baseline comparisons, code or data availability statements, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting methodological contribution to RNA design, combining geometric deep learning with flow matching in a latent space. However, the abstract is too brief to evaluate the technical soundness, novelty relative to existing RNA design tools, or the validity of any performance claims. No quantitative evidence is visible, and the core methodological claims cannot be assessed from the supplied material. The work may be of interest to computational biologists and machine learning researchers, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Computational biologists working on RNA structure prediction and design, machine learning researchers interested in generative models for biomolecular structures, and pharmaceutical or synthetic biology groups developing RNA-based therapeutics. The combination of geometry-aware modeling and flow matching is a timely topic, and successful co-design of sequence and structure would have practical utility.
- **Major strengths** The problem addressed (RNA co-design of sequence and structure) is important and underexplored relative to protein design. The methodological framing, using geometry-latent flow matching, is conceptually appealing and aligns with recent advances in generative modeling for biomolecules. The abstract is clearly written and accessible to a broad scientific audience.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract implies that La-Ribo achieves effective RNA co-design via geometry-latent flow matching, but no technical details are provided to support this claim.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not describe the model architecture, the flow matching formulation, the latent space construction, or the training procedure. Without these details, it is impossible to assess whether the method is technically sound, novel, or correctly implemented.
  - **Why it matters** Technical soundness is a prerequisite for any methodological claim. The absence of any methodological description prevents evaluation of whether the approach is valid, reproducible, or an improvement over existing methods.
  - **Resolution test** Provide a full method section describing the model, the flow matching objective, the geometry representation, and the training and inference procedures. Include sufficient detail for replication.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for claims
  - **Claim pointer** The abstract implies improved or competitive performance for RNA co-design, but no results are reported.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No quantitative results, benchmarks, or comparisons to existing RNA design methods are presented. Any claim of effectiveness or superiority is unsupported.
  - **Why it matters** Without empirical validation, the utility of the method cannot be established. The RNA design field has existing baselines, and new methods must demonstrate clear advantages or at least competitive performance on standard benchmarks.
  - **Resolution test** Include experimental results on established RNA design benchmarks, with comparisons to relevant baselines, and report metrics for both sequence recovery and structural accuracy.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Novelty and positioning
  - **Claim pointer** The abstract presents La-Ribo as a new method, but does not articulate how it differs from prior RNA design approaches or from flow matching methods applied to other biomolecules.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not cite or discuss prior work on RNA design, geometric flow matching, or related generative models. Without this context, the novelty of the contribution cannot be evaluated.
  - **Why it matters** Scientific contribution requires clear differentiation from existing work. The lack of positioning against the literature makes it impossible to judge whether the method is a meaningful advance or an incremental variation.
  - **Resolution test** Add a related work section that situates La-Ribo within the existing literature, explicitly stating the novel components and the expected advantages over prior methods.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract terminology
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "geometry-latent flow matching" is used without definition or context, which may be opaque to readers outside the machine learning for biomolecules community.
  - **Required correction** Briefly define the term or provide a one-sentence explanation of the approach in the abstract.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Code and data availability
  - **Evidence pointer** Abstract, location not provided
  - **Issue** No statement about code or data availability is present in the abstract.
  - **Required correction** Include a data and code availability statement in the full manuscript, and mention it in the abstract if space permits.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scope of claims
  - **Affected element** Abstract claims
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not specify the scope of the co-design task, such as whether it handles pseudoknots, modified nucleotides, or specific RNA lengths.
  - **Required correction** Clarify the scope and limitations of the method in the abstract or introduction.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no methodological detail), R1-M2 (no empirical results), R1-M3 (no literature positioning). These are not technical failings in the implementation but rather critical omissions in the provided material that prevent any technical assessment.
- **Assessment against Nature-style criteria** Originality: cannot be assessed due to lack of literature context. Scientific importance: the problem is important, but the contribution cannot be evaluated. Interdisciplinary readership: the abstract is accessible, but the lack of results limits appeal. Technical soundness: not assessable from the abstract. Readability for nonspecialists: the abstract is clear but uses undefined jargon. Overall, the manuscript does not currently meet the evidentiary standard for a Nature-style publication based on the supplied material.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone is insufficient to support the claims. A full manuscript with methodological detail, experimental validation, and literature positioning is required before a meaningful assessment can be made.

## Risk / unsupported claims

- The claim that La-Ribo enables effective RNA co-design is unsupported, as no results are provided.
- Any implied improvement over existing methods is unsupported, as no comparisons are presented.
- The novelty of the approach is unassessable, as no prior work is cited or discussed.
- The technical validity of the geometry-latent flow matching approach is unassessable, as no methodological details are given.