## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors propose MARCO, a radioactive watermarking method for protein generative models. The method embeds watermarks into generated protein sequences and enables detection of model misuse. The abstract claims effectiveness, robustness, and utility in tracing generated proteins back to their source model.
- **Visible evidence base** Abstract text only. No figures, tables, methods section, or experimental details are provided.
- **Missing materials affecting confidence** Full manuscript, experimental protocols, benchmark datasets, baseline comparisons, statistical analyses, implementation details, and any quantitative results. The abstract contains no numerical outcomes or comparative performance data.

## Reviewer

- **Overall assessment** The abstract introduces a timely and relevant problem, namely watermarking for protein generative models, which sits at the intersection of AI security and computational biology. The concept of radioactive watermarking for protein sequences is plausible and potentially valuable. However, the abstract as provided is insufficient to evaluate the technical soundness, originality relative to existing watermarking literature, or the strength of empirical claims. No results, metrics, or methodological specifics are presented. The case for the method's effectiveness is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in AI security and model provenance, developers of protein generative models, regulatory bodies concerned with biosecurity and misuse of generative models, and computational biologists working on protein design. The work could also interest policymakers addressing responsible AI deployment in the life sciences.
- **Major strengths** The problem is well-motivated and timely. The application domain, protein generative models, is of high societal importance. The concept of embedding watermarks directly into generated protein sequences is a sensible approach to traceability. The abstract communicates the core idea clearly.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that MARCO is effective and robust for watermarking protein generative models.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract provides no quantitative results, no comparison to existing watermarking methods, no description of the watermarking scheme, and no details on the detection procedure. The claim of effectiveness is unsupported by any visible data.
  - **Why it matters** Without empirical evidence, the central claim of the work cannot be assessed. The abstract does not allow a reviewer to determine whether the method works, under what conditions, or how it compares to alternatives.
  - **Resolution test** Provide the full manuscript with experimental sections, including benchmark datasets, evaluation metrics, baseline comparisons, and statistical significance tests. The abstract should include at least one quantitative result demonstrating the method's performance.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Originality
  - **Claim pointer** The abstract implies that MARCO is a novel contribution to watermarking for generative models.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not discuss prior work on watermarking for generative models, including text and image domains, nor does it position MARCO relative to existing protein-specific watermarking approaches. The novelty claim is therefore unverifiable.
  - **Why it matters** Originality is a core criterion for publication. Without a clear statement of prior art and the specific gap MARCO fills, the contribution cannot be evaluated.
  - **Resolution test** Include a related work section in the full manuscript and explicitly state the novelty of MARCO relative to existing methods. The abstract should mention the key differentiator.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract claims that MARCO is robust, implying resistance to attacks or tampering.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No information is given on the threat model, types of attacks considered, or robustness evaluation. The claim of robustness is not supported by any described experiments.
  - **Why it matters** Robustness is a critical property for any watermarking scheme. Without a defined threat model and adversarial evaluation, the claim is speculative.
  - **Resolution test** Provide a detailed robustness analysis in the full manuscript, including attack scenarios, degradation tests, and comparison to baseline robustness levels.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract terminology
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "radioactive watermark" is not defined. It is unclear whether this refers to a specific technical property or is a stylistic choice.
  - **Required correction** Define the term in the abstract or use standard terminology such as "embedded watermark" or "tracing watermark."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Scope
  - **Affected element** Abstract claims
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not specify the types of protein generative models covered, such as diffusion-based, autoregressive, or GAN-based models. The scope of applicability is unclear.
  - **Required correction** State the model classes for which MARCO is designed and whether the method generalizes across architectures.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, location not provided
  - **Issue** No mention of code or data availability. Reproducibility is a key expectation for methods papers.
  - **Required correction** Include a statement on code and data availability in the abstract or full manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract provides no empirical evidence, no positioning against prior work, and no robustness analysis. These are fundamental gaps that prevent any assessment of the method's validity.
- **Assessment against Nature-style criteria** 
  - Originality: Not assessable from the abstract. No comparison to prior watermarking work is provided.
  - Scientific importance: The problem is important, but the abstract does not demonstrate that MARCO advances the field in a meaningful way.
  - Interdisciplinary readership: The topic bridges AI security and biology, which is promising. However, the abstract lacks sufficient detail to engage either community deeply.
  - Technical soundness: Not assessable. No methodological or experimental details are given.
  - Readability for nonspecialists: The abstract is readable but uses undefined terminology. It does not explain the technical approach in accessible terms.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not support the claims made. A full manuscript with experimental results, related work, and robustness analysis is required before the case can be evaluated.

## Risk / unsupported claims

- The claim that MARCO is effective is unsupported by any quantitative data.
- The claim that MARCO is robust is unsupported by any adversarial evaluation.
- The claim of novelty is unverifiable without a discussion of prior art.
- The scope of applicability to different protein generative model architectures is not stated and cannot be inferred.