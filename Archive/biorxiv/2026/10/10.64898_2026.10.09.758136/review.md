## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present a generative discrete diffusion model, MESSI, that takes protein structures as input and outputs sequences predicted to lack MHC class II binding epitopes while preserving structure. They claim high structural recovery, reduced predicted epitope counts, and experimental validation in three systems, including a luciferase, a PD-1 mini-binder, and uricase, with the latter showing improved catalytic activity relative to natural orthologs.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or experimental protocols are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary information, model architecture details, training data description, experimental methods, statistical analyses, and sequence-level data

## Reviewer

- **Overall assessment** The abstract describes a potentially valuable approach to a clinically important problem, namely the reduction of protein immunogenicity through generative design. The conceptual framing is clear and the choice of three experimental systems, including a clinically approved enzyme, is appropriate. However, the abstract provides no quantitative evidence for any of the central claims. Structural recovery values, epitope prediction counts, activity measurements, and statistical comparisons are all absent. The claim that MESSI outperforms post-hoc filtering is unsupported without data. The experimental results are described only in qualitative terms, making it impossible to assess effect sizes, variability, or significance. The work may be of interest to the protein engineering and therapeutic development communities, but the current evidence base is insufficient to evaluate the strength of the claims.
- **Who would be interested in the results, and why** Researchers in protein engineering, computational biology, and biotherapeutics development would be interested. The potential to reduce immunogenicity of protein therapeutics addresses a major bottleneck in biologic drug development. Those working on generative models for protein design would also find the methodological approach relevant, particularly the use of discrete diffusion with structural conditioning.
- **Major strengths** The problem addressed is clinically significant and well motivated. The use of a generative diffusion model for deimmunization is a novel angle compared to conventional post-hoc filtering. The inclusion of three distinct experimental systems, including a clinically approved enzyme, suggests an attempt at broad validation. The coupling of the model with evolution guidance for uricase is a thoughtful extension.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** MESSI designs sequences with high structural recovery and down to 0 predicted epitopes for specified MHC molecules at higher efficiency than post-hoc filtering approaches
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract states that MESSI achieves high structural recovery and zero predicted epitopes, and that it does so more efficiently than post-hoc filtering, but no quantitative data are provided. No structural recovery values, no epitope prediction counts, no efficiency metrics, and no comparison data are shown.
  - **Why it matters** These are the central quantitative claims of the method. Without numbers, the reader cannot assess whether the performance is meaningful, whether the improvement over filtering is substantial or marginal, or whether the results are reproducible.
  - **Resolution test** Provide quantitative results in the full manuscript, including structural recovery values, predicted epitope counts, and efficiency metrics, with appropriate comparisons to post-hoc filtering baselines and statistical analysis.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** Experimentally, we first applied MESSI to deimmunize a luciferase and a de novo designed mini-binder against PD-1, resulting in variants with no predicted epitopes and higher activity than their parents
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The experimental results are described only qualitatively. No activity values, no fold improvements, no number of variants tested, no experimental replicates, and no statistical significance are reported.
  - **Why it matters** The claim that deimmunized variants retain or improve activity is critical for the practical utility of the method. Without quantitative experimental data, the claim is not verifiable.
  - **Resolution test** Provide experimental data in the full manuscript, including activity measurements, variant counts, replicate numbers, and statistical tests comparing variants to parental proteins.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** We coupled MESSI with evolution guidance to deimmunize uricase, a clinically approved enzyme with severe immunogenicity, and found deimmunized variants with higher catalytic activity than their natural orthologs
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The uricase result is presented as a key demonstration of the method on a clinically relevant enzyme, but no catalytic activity values, no comparison to natural orthologs, and no immunogenicity measurements are provided.
  - **Why it matters** This is the most clinically relevant claim in the abstract. The absence of quantitative data prevents any assessment of whether the deimmunized variants are actually useful or whether the improvement over natural orthologs is meaningful.
  - **Resolution test** Provide catalytic activity data, immunogenicity measurements, and statistical comparisons to natural orthologs in the full manuscript.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Model name and description
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The model name MESSI is introduced without explanation of the acronym or the rationale for the name.
  - **Required correction** Define the acronym or provide a brief explanation of the name in the full manuscript.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Scope
  - **Affected element** MHC coverage
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract mentions specified MHC molecules but does not indicate which MHC alleles or how many were considered.
  - **Required correction** Specify the MHC alleles used in the study and the rationale for their selection.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Evolution guidance
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The coupling of MESSI with evolution guidance is mentioned but not described. The nature of the guidance and how it was integrated is unclear.
  - **Required correction** Describe the evolution guidance approach in the full manuscript, including the objective function and the optimization procedure.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative data for all central claims means the case is not established from the provided material.
- **Assessment against Nature-style criteria** Originality is potentially high, as the application of generative diffusion to deimmunization is not a standard approach. Scientific importance is clear given the clinical relevance of immunogenicity in biologic drugs. Interdisciplinary readership is plausible, spanning computational biology, immunology, and therapeutic development. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is adequate, with the abstract being accessible, though some terms such as discrete diffusion model and MHC class II may require background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a promising approach, but the absence of quantitative results for all major claims prevents any assessment of validity or significance. A full manuscript with detailed data would be required to evaluate the work properly.

## Risk / unsupported claims

- The claim that MESSI achieves high structural recovery and zero predicted epitopes is unsupported by quantitative data.
- The claim that MESSI is more efficient than post-hoc filtering approaches is unsupported.
- The claim that deimmunized luciferase and PD-1 mini-binder variants have higher activity than their parents is unsupported.
- The claim that deimmunized uricase variants have higher catalytic activity than natural orthologs is unsupported.
- The general claim that MESSI enables generative design of functional proteins with minimized immunogenicity is not assessable from the abstract.