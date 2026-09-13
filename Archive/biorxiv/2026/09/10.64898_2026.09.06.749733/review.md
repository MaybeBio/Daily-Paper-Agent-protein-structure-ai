## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present Inverse FoldDir, a Dirichlet flow matching method for structure-conditioned protein sequence design. They report improved structural recovery over ESM-IF1 on CATH 4.2, characterize denoising trajectories, and provide experimental validation in an anti-GFP nanobody redesign task.
- **Visible evidence base** Abstract text only; no numerical tables, figures, methods descriptions, or experimental protocols were supplied
- **Missing materials affecting confidence** Full methods, model architecture details, training and evaluation protocols, CATH 4.2 split definitions, baseline implementation details, experimental assay descriptions, statistical analyses, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a potentially useful contribution to inverse folding, with a novel methodological angle (Dirichlet flow on the probability simplex) and an experimental validation component that is uncommon in this space. However, the evidence base is too thin to assess technical soundness, statistical robustness, or the strength of the experimental claims. The reported gains over ESM-IF1 are modest and lack uncertainty estimates. The experimental result, while encouraging, is based on a small number of positives without clear controls or quantitative binding data in the abstract.
- **Who would be interested in the results, and why** Computational protein design researchers, particularly those working on inverse folding, sequence design for de novo backbones, and controllable generation. The method's support for fixed-residue inpainting and soft priors may appeal to practitioners in protein engineering and therapeutic antibody design. The experimental validation component would interest experimentalists seeking practically useful design tools.
- **Major strengths** The methodological framing (joint iterative denoising on the simplex) is distinct from one-shot or autoregressive approaches. The inclusion of experimental validation, even preliminary, is a notable strength. The reported trajectory analysis, showing position-dependent commitment rates, offers a potentially useful mechanistic insight into the generation process.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (no uncertainty quantification), R1-M2 (insufficient experimental detail), R1-M3 (no statistical treatment of experimental results), R1-M4 (no methodological detail for reproducibility)
- **Assessment against Nature-style criteria** Originality: the Dirichlet flow formulation is a reasonable extension of existing flow matching ideas to the sequence design setting, but the abstract does not establish clear novelty over prior flow-based or diffusion-based inverse folding methods. Scientific importance: inverse folding is an active and important area, and controllable design with experimental validation is valuable; however, the modest reported improvements do not clearly demonstrate a step-change in capability. Interdisciplinary readership: the abstract is accessible to a broad structural biology and protein engineering audience, though some methodological terms may require familiarity with generative models. Technical soundness: cannot be assessed from the abstract alone; no details on training, validation, or statistical rigor are provided. Readability for nonspecialists: the abstract is generally clear, though the trajectory analysis description is somewhat opaque without figures.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but unverifiable from the abstract alone. A supportive posture would require full methods, uncertainty estimates, and more detailed experimental reporting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "Inverse FoldDir achieved a mean TM-score of 84.5 (on a 0-100 scale) and a mean C α RMSD of 1.76Å, compared with 83.3 and 1.86Å, respectively, for ESM-IF1"
- **Evidence pointer** Abstract, location not provided
- **Concern** The reported performance metrics are point estimates without any measure of variance, confidence intervals, or statistical significance testing. The differences (1.2 TM-score points, 0.1Å RMSD) may or may not be meaningful depending on the distribution across the test set.
- **Why it matters** Without uncertainty quantification, readers cannot determine whether the reported improvement over ESM-IF1 is robust or within noise. This is particularly important given the modest magnitude of the differences.
- **Resolution test** Provide per-target distributions, confidence intervals, paired significance tests (e.g., Wilcoxon signed-rank), and effect sizes for both metrics across the CATH 4.2 test set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** "two of 35 redesigned sequences retained reproducible sfGFP-binding signal across independent assay runs with approximately 43% sequence divergence from the native nanobody"
- **Evidence pointer** Abstract, location not provided
- **Concern** The experimental result is reported with minimal detail. No information is provided on the assay type, detection threshold, positive/negative controls, expression levels, or how "reproducible" was defined. The success rate (2/35) is low, and it is unclear whether this represents a meaningful improvement over random or baseline design methods.
- **Why it matters** Experimental validation is a key differentiator of this work, but the current description is insufficient to judge whether the designed sequences are genuinely functional or whether the result could arise from assay artifacts or permissive detection criteria.
- **Resolution test** Provide full experimental methods, including assay protocol, controls, replicate definitions, quantitative binding measurements (e.g., EC50 or fluorescence values), and a comparison to appropriate baseline designs (e.g., ESM-IF1 designs or random sequences) tested under identical conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodology
- **Claim pointer** "performs iterative denoising on the amino acid probability simplex" and "learned Dirichlet flow"
- **Evidence pointer** Abstract, location not provided
- **Concern** No methodological details are provided regarding the model architecture, training data, loss function, noise schedule, or inference procedure. The Dirichlet flow formulation is mentioned but not described in sufficient detail to understand its relationship to prior flow matching or diffusion approaches.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without architecture and training details, the method cannot be reimplemented or compared fairly against existing baselines.
- **Resolution test** Provide a complete methods section including model architecture, training hyperparameters, data splits, and code availability. Clarify how the Dirichlet flow is parameterized and how it differs from existing categorical diffusion or flow matching methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim scope
- **Claim pointer** "supporting full sequence generation, fixed-residue inpainting, and user-defined soft residue priors"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract claims support for three modes of controllable generation, but no results are shown for inpainting or soft priors. It is unclear whether these modes were evaluated, and if so, with what performance.
- **Why it matters** The controllability features are a stated advantage of the method, but without evaluation, readers cannot assess whether they work as claimed or whether they degrade sequence quality.
- **Resolution test** Provide quantitative evaluations for inpainting and soft-prior scenarios, including comparisons to baselines under the same conditions, or explicitly state that these modes are supported but not yet benchmarked.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Trajectory analysis description
- **Evidence pointer** Abstract, location not provided
- **Issue** The statement "positions commit at different rates and that some residues change identity late in generation" is vague without visual or quantitative support.
- **Required correction** Provide a figure showing commitment dynamics over denoising steps, or quantify the fraction of positions that change identity at late stages.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Baseline comparison
- **Affected element** Baseline selection
- **Evidence pointer** Abstract, location not provided
- **Issue** Only ESM-IF1 is mentioned as a baseline. It is unclear whether other state-of-the-art inverse folding methods (e.g., ProteinMPNN, ESM-IF2, or recent diffusion-based approaches) were compared.
- **Required correction** Clarify the full set of baselines evaluated and justify the selection, or acknowledge that only ESM-IF1 was used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Metric interpretation
- **Affected element** TM-score scale
- **Evidence pointer** Abstract, location not provided
- **Issue** The TM-score is reported on a 0-100 scale, which is unconventional (typically 0-1). This may cause confusion.
- **Required correction** State the scale explicitly in the text or use the standard 0-1 scale for consistency with the field.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Experimental framing
- **Affected element** Success rate interpretation
- **Evidence pointer** Abstract, location not provided
- **Issue** The 2/35 success rate is presented without context. It is unclear whether this is expected, better than chance, or comparable to other design methods in similar tasks.
- **Required correction** Provide context, such as the success rate of native sequences or baseline designs in the same assay, to allow interpretation.

## Risk / unsupported claims
- The claim of improved performance over ESM-IF1 is unsupported without uncertainty quantification or significance testing.
- The experimental validation claim (2/35 binders) is unsupported without assay details, controls, and quantitative data.
- The claim of supporting inpainting and soft priors is unsupported without evaluation results.
- The trajectory analysis claim is unsupported without figures or quantitative summaries.
- The statement "natural route toward future property-guided sampling" is speculative and not supported by any evidence in the abstract.