## Review setup
- **Input scope** Full manuscript text including abstract, main text, supplementary methods, and funding information
- **Assessment boundary** Scientific claims, methodological soundness, experimental validation, and framework utility as presented in the provided material
- **Shared manuscript claim summary** The authors present Chaperone, a lightweight Python framework that standardizes protein design tool orchestration through a DataFrame-based block interface, and demonstrate that this framework improves agentic workflow efficiency (86% token reduction, 64% GPU cost reduction) and enables successful experimental validation across three distinct design tasks: small-molecule binders, nanoparticles, and protein fusions
- **Visible evidence base** In silico evaluation across nine design tasks comparing agent performance with and without the harness; wet lab validation for cortisol binders (fluorescence polarization), nanoparticles (negative stain EM), and protein fusions (bright-field microscopy); supplementary descriptions of evaluation protocols
- **Missing materials affecting confidence** No code repository contents or version information; no raw scoring data or per-task breakdowns; no negative control experiments for the harness comparison; no quantitative EM analysis for nanoparticle validation; no diffraction data for crystal claims; no statistical analysis of replicate variability

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable contribution to the growing field of agentic protein design. The Chaperone framework addresses a real bottleneck in computational protein design, and the reported efficiency gains are substantial. However, the evidence base for the central claim that Chaperone improves agent performance is thinner than the abstract suggests, and several experimental validations lack quantitative rigor. The framework itself appears well-designed and the wet lab results are encouraging, but the manuscript would benefit from more detailed evaluation methodology, additional controls, and clearer presentation of limitations.

- **Who would be interested in the results, and why** Computational protein designers and developers of scientific agent frameworks will find the Chaperone architecture directly relevant to their work. The demonstrated efficiency gains in agentic workflows are of broad interest to the AI-for-science community. Experimental protein designers may be interested in the cortisol binder results, though the single-target demonstration limits generalizability. The framework's open-source availability increases its potential impact.

- **Major strengths**
  1. The block-based DataFrame abstraction is elegant and addresses a genuine pain point in protein design tool integration
  2. The in silico evaluation suite spans diverse design tasks and uses held-out scoring, which is methodologically sound
  3. The reported efficiency gains (86% token reduction, 64% GPU cost reduction) are substantial and practically meaningful
  4. Experimental validation across three distinct design challenges demonstrates real-world utility
  5. The framework is made freely available, which will facilitate adoption and further testing

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we find using Chaperone reduces total token usage relative to baseline agents by 86% and GPU costs by 64%, while increasing the overall computational design pass rate"
- **Evidence pointer** Section 3, Figure 1f, Figure 1g
- **Concern** The central quantitative claim of the manuscript rests on a comparison between agents with and without the Chaperone harness, but the evaluation methodology has a critical asymmetry: harnessed agents had internet access disabled while baseline agents had web access. This confounds the effect of the harness itself with the effect of restricted tool access. Additionally, only a single agent model (GPT-5.6-sol) was evaluated, and the manuscript does not report per-task results, variance across runs, or statistical significance testing. The pass rate increase from 6% to 12% is reported as a mean, but no confidence intervals or per-task breakdowns are provided.
- **Why it matters** The efficiency and pass rate improvements are the primary quantitative evidence for the manuscript's central claim. Without addressing the internet access confound and providing statistical rigor, the magnitude of the harness benefit cannot be reliably assessed. The single-model evaluation also limits generalizability claims.
- **Resolution test** Provide per-task results with variance measures, run the comparison with matched internet access conditions (both enabled or both disabled), evaluate at least one additional agent model, and report statistical significance testing for the efficiency and pass rate differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation rigor
- **Claim pointer** "yielding low nanomolar binders to cortisol zero shot" and "one successfully assembled into a protein nanoparticle" and "form crystalline assemblies"
- **Evidence pointer** Section 4.1, Section 4.2, Section 4.3, Figure 2
- **Concern** The experimental validations are presented with insufficient quantitative detail. For the cortisol binder, the manuscript reports a best affinity of 1.32 nM but does not provide the full binding curve, replicate measurements, or the number of proteins tested. The nanoparticle validation reports one success out of 15 designs but provides no quantitative EM analysis (e.g., particle size distribution, symmetry assessment). The crystal claim is supported only by bright-field microscopy images, which cannot demonstrate crystallinity; no diffraction data are shown. The fusion validation lacks any biochemical characterization beyond microscopy.
- **Why it matters** These experimental results are presented as demonstrations of the framework's utility, but the level of validation is not commensurate with the strength of the claims. For a framework paper, the experimental sections should either be more rigorously quantified or presented with appropriately hedged language.
- **Resolution test** Provide full binding curves with replicate measurements for cortisol binders, quantitative EM analysis (particle dimensions, symmetry metrics) for nanoparticles, and X-ray diffraction or electron diffraction data for crystal claims. Alternatively, soften the claims to match the evidence level.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "we make Chaperone freely available to the community on GitHub"
- **Evidence pointer** Abstract, Section 5
- **Concern** The manuscript states the framework is available on GitHub but provides no repository URL in the visible text, no version information, no installation instructions, and no documentation of the block interface beyond the single algorithm example. The supplementary material describes evaluation protocols but does not include the actual evaluation prompts, scoring functions, or agent configuration details needed to reproduce the benchmark results.
- **Why it matters** Reproducibility is a core expectation for computational framework papers. Without access to the code, evaluation prompts, and scoring implementations, independent verification of the reported results is not possible.
- **Resolution test** Provide the GitHub URL, a versioned release, documentation of the block API, and include evaluation prompts and scoring function implementations in the supplementary material.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to existing approaches
- **Claim pointer** "Previous efforts targeting cortisol involved iterative computational design followed by experimental affinity maturation, with Lee et al. ultimately achieving a binding affinity of 68 nM"
- **Evidence pointer** Section 4.1
- **Concern** The comparison to prior work is limited to a single affinity value from one study. The manuscript does not discuss how the Chaperone-based approach compares to other agentic frameworks or automated design pipelines in terms of efficiency, success rate, or design quality. The claim that Chaperone "accelerates" the design process is supported only by the two-week timeline, but no comparison to a non-harnessed timeline for the same task is provided.
- **Why it matters** The manuscript positions Chaperone as an improvement over existing approaches, but the evidence for this improvement is largely internal to the study. A meaningful comparison to alternative frameworks or to manual workflows would strengthen the contribution.
- **Resolution test** Include a comparison to at least one alternative agentic framework or to a manual workflow for the same design task, reporting comparable efficiency and success metrics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure is referenced extensively but the visible text does not describe the figure panels in sufficient detail. The relationship between panels b, c, d, f, and g is not immediately clear from the text alone.
- **Required correction** Add a detailed figure legend that explains each panel and how they relate to the claims in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2, "block" definition
- **Evidence pointer** Section 2
- **Issue** The term "block" is used to describe both the framework's computational unit and the experimental design blocks in the supplementary methods, which could cause confusion.
- **Required correction** Consider using a distinct term for the framework unit, such as "tool block" or "pipeline block," to avoid ambiguity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.2
- **Evidence pointer** Section 4.2, Figure 2h, 2i
- **Issue** The nanoparticle section reports one success out of 15 designs but does not describe what happened to the other 14 designs or whether any iterative refinement was attempted.
- **Required correction** Briefly describe the outcomes for the unsuccessful designs and whether any design modifications were made based on the initial results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3
- **Evidence pointer** Section 3, Figure 1f
- **Issue** The pass rate improvement from 6% to 12% is reported as a mean, but the number of evaluation runs and the distribution of results across the nine tasks are not reported.
- **Required correction** Report the per-task pass rates and the number of independent evaluation runs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract claims "more than 50 other protein design tools" are integrated, but the main text does not provide a list or categorization of these tools.
- **Required correction** Include a supplementary table listing the integrated tools and their categories.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1
- **Issue** The phrase "zero shot" in the abstract and Section 4.1 is potentially misleading, as the design process involved iterative refinement and human guidance.
- **Required correction** Clarify what "zero shot" means in this context, or use alternative phrasing such as "without affinity maturation."

## Risk / unsupported claims
- The claim that Chaperone reduces token usage by 86% and GPU costs by 64% is confounded by the asymmetric internet access conditions in the evaluation and lacks statistical rigor
- The claim of "low nanomolar binders to cortisol zero shot" is not fully supported, as the manuscript does not demonstrate that no affinity maturation occurred and does not provide full binding characterization
- The claim of "crystalline assemblies" is unsupported by the evidence presented, as bright-field microscopy cannot demonstrate crystallinity
- The claim that Chaperone integrates "more than 50 other protein design tools" is not verifiable from the provided material, as no tool list is given
- The generalizability of the efficiency gains to other agent models is not established, as only GPT-5.6-sol was evaluated
- The claim that the framework "enables rapid iteration and scalable exploration" is supported only by the two-week cortisol campaign, which lacks a comparison to non-harnessed timelines