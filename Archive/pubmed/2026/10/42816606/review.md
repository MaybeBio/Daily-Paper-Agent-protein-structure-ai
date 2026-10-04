## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce SynthIDBio, a family of methods for watermarking AI-generated protein sequences and structures. They claim that SynthIDBio-sequence embeds watermarks into protein sequences while preserving function, demonstrated by watermarked functional designed protein binders with binding affinity comparable to non-watermarked counterparts and near-perfect watermark detection accuracy. They further claim that SynthIDBio-structure, a fine-tuned AlphaFold3 model, embeds an imperceptible watermark into biomolecular structures. The work is presented as a proof-of-concept that function-preserving biological watermarking is feasible.
- **Visible evidence base** Abstract text only; no quantitative data, methodological details, or experimental descriptions are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary information, statistical analyses, and any detailed experimental protocols

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting and timely idea with potential relevance to biosecurity and provenance tracking in AI-driven biology. However, the claims are broad and the evidence base is entirely absent from the supplied material. Key assertions regarding functional preservation, watermark detection accuracy, and imperceptibility of structural watermarks cannot be evaluated without quantitative data and methodological detail. The work may be of interest to the community, but the current evidence does not establish the case.
- **Who would be interested in the results, and why** Researchers in AI for biology, protein engineering, and biosecurity policy would be interested. The work addresses provenance of AI-generated biological sequences and structures, which is relevant to those developing generative models for proteins, those concerned with dual-use risks, and policymakers working on responsible AI deployment in biotechnology.
- **Major strengths** The problem addressed is timely and important. The idea of embedding watermarks in both sequences and structures is novel and potentially impactful. The proof-of-concept framing is appropriate for an initial demonstration.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The concept of function-preserving watermarking for proteins appears novel, but the abstract does not provide enough context to assess novelty relative to prior watermarking work in other domains.  
  Scientific importance: The potential importance is high given biosecurity concerns, but the abstract does not demonstrate that the methods are robust or generalizable.  
  Interdisciplinary readership: The topic bridges AI, structural biology, and biosecurity, which could attract broad interest, but the abstract lacks sufficient technical detail for specialists and clarity for nonspecialists.  
  Technical soundness: Not assessable from the abstract alone. No quantitative results, statistical measures, or methodological descriptions are provided.  
  Readability for nonspecialists: The abstract is generally clear but uses terms such as "imperceptible watermark" and "fine-tuned AlphaFold3" without explanation, which may hinder nonspecialist understanding.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising, but the claims require full manuscript review with detailed methods and data.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "SynthIDBio-sequence actively embeds a watermark into protein sequences while preserving function. We demonstrate this by creating watermarked, functional designed protein binders with binding affinity comparable with non-watermarked counterparts and near-perfect watermark detection accuracy."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The claim of functional preservation is supported only by a qualitative statement of "comparable" binding affinity. No quantitative values, statistical comparisons, or error bars are provided. The claim of "near-perfect watermark detection accuracy" is similarly unsupported by any numerical metric.  
- **Why it matters** Functional preservation is the central claim of the work. Without quantitative evidence, the reader cannot assess whether the watermarking method truly preserves function or whether the observed performance is within acceptable biological variability. Detection accuracy is also critical for practical utility.  
- **Resolution test** Provide quantitative binding affinity measurements for watermarked and non-watermarked binders, including replicates, statistical tests, and effect sizes. Provide watermark detection accuracy with confidence intervals and describe the detection threshold.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** "SynthIDBio-structure, a fine-tuned AlphaFold3 model, embeds an imperceptible watermark into biomolecular structures."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not describe how the watermark is embedded in structures, what "imperceptible" means quantitatively, or how the fine-tuning of AlphaFold3 was performed. No validation of structural fidelity or watermark detectability is provided.  
- **Why it matters** The structural watermarking claim is a major component of the work. Without methodological detail and validation, the claim is not assessable and the approach cannot be reproduced or evaluated for potential structural perturbations.  
- **Resolution test** Describe the watermarking algorithm for structures, define imperceptibility with quantitative metrics such as RMSD or per-residue distance changes, and provide detection accuracy on a test set.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability and scope  
- **Claim pointer** "Our work is a proof-of-concept that function-preserving biological watermarking is feasible."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract demonstrates the method on one class of proteins, designed binders. The claim of general feasibility is broader than the evidence presented. It is unclear whether the method works across diverse protein families, functions, or sequence lengths.  
- **Why it matters** A proof-of-concept should clearly state the scope of demonstration. Overgeneralization from a single protein class could mislead readers about the maturity and applicability of the method.  
- **Resolution test** Clarify the scope of the demonstration in the abstract and provide evidence from multiple protein classes or discuss limitations explicitly.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Robustness and security  
- **Claim pointer** "SynthIDBio-sequence actively embeds a watermark into protein sequences while preserving function."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not address the robustness of the watermark to common sequence modifications such as mutations, truncations, or re-synthesis. It also does not discuss potential adversarial attempts to remove the watermark.  
- **Why it matters** For provenance tracking to be useful in real-world settings, the watermark must survive typical sequence manipulations and be resistant to removal. Without this information, the practical utility of the method is unclear.  
- **Resolution test** Provide robustness tests against sequence edits, including point mutations, insertions, deletions, and re-synthesis, and discuss adversarial robustness.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "imperceptible watermark" is used without definition. For structures, imperceptibility is not self-explanatory.  
- **Required correction** Define imperceptibility in the abstract or refer to a quantitative metric.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Method description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention whether the methods or code will be made available, which is important for reproducibility.  
- **Required correction** State data and code availability in the abstract or main text.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Related work  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not discuss prior watermarking approaches in other domains or for biological sequences, which would help position the novelty.  
- **Required correction** Add a brief statement on prior work and how SynthIDBio differs.

## Risk / unsupported claims
- The claim of "binding affinity comparable with non-watermarked counterparts" is unsupported by quantitative data.
- The claim of "near-perfect watermark detection accuracy" is unsupported by any numerical metric.
- The claim of "imperceptible watermark" in structures is undefined and unvalidated.
- The claim that "function-preserving biological watermarking is feasible" is overgeneralized from a single protein class demonstration.
- The robustness of the watermark to sequence or structure modifications is not addressed and cannot be assessed.