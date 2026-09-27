## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, claims-to-evidence alignment, and suitability for a general multidisciplinary audience
- **Shared manuscript claim summary** The authors report that generative AI models (ESM3, ProteinMPNN, EvoDiff) can design de novo thiolation (T) domains for non-ribosomal peptide synthetases (NRPSs) that are functional across minimal, full-length, and hybrid assembly line architectures. They report that AI-designed T-domains can match or exceed native T-domain performance, with one representative design showing improved biochemical properties, and that compatibility is strongly dependent on the downstream C-domain identity.
- **Visible evidence base** In vivo activity data for 66 AI-designed T-domains across three design rounds in a type S GxpS platform; positional swapping data at T1, T2, T4, T5; hybrid NRPS data with XtpS and SzeS; biochemical characterization of AI-2 vs WT; MD simulations of WT vs AI-2 in three catalytic states; phylogenetic analysis
- **Missing materials affecting confidence** Supplementary Note 1 (design details, filtering criteria, surrogate model training), Supplementary Data 1 (sequences, raw data), Supplementary Figures 1–18, Supplementary Tables 1 and 4, Source Data files, Supplementary Methods 1 and 2. These are referenced but not provided in the submitted material, limiting full assessment of methodology and data quality.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and well-executed study demonstrating that generative protein models can produce functional T-domains for NRPS engineering. The experimental scope is impressive, with 578 recombinant variants tested across multiple architectures. The central claims are largely supported by the visible evidence, though several important limitations must be addressed. The claim that AI-designed T-domains "increase yields by up to ~3-fold" requires careful scrutiny regarding the specific context and reproducibility of this effect. The positional dependence and downstream C-domain specificity findings are compelling and represent a useful conceptual contribution. The biochemical characterization of AI-2 is a strength, though the MD simulation analysis is presented as suggestive rather than definitive, which is appropriate. The manuscript would benefit from clearer articulation of what is genuinely novel versus incremental, and from more explicit discussion of the practical utility of the designs given the observed context dependence.

- **Who would be interested in the results, and why** Researchers in natural product biosynthesis, NRPS engineering, and synthetic biology will find the demonstration of AI-designed functional domains in megasynthases of direct relevance. The broader protein design community will be interested in the successful application of generative models to dynamic, multidomain systems, which extends beyond the more static targets typically addressed. The work also has potential relevance for industrial biotechnology groups interested in improving yields of peptide natural products, though the context dependence of the designs will require careful consideration for such applications.

- **Major strengths**
  1. The scale of experimental validation (578 variants) is a significant strength, providing robust empirical grounding for the claims.
  2. The systematic progression from minimal to full-length to hybrid systems is logically structured and strengthens the conclusions.
  3. The identification of downstream C-domain identity as a key determinant of T-domain compatibility is a useful conceptual insight with practical implications.
  4. The biochemical characterization of AI-2 provides mechanistic insight beyond simple activity measurements.
  5. The honest reporting of context dependence and the limitations of the approach is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claims-to-evidence alignment
- **Claim pointer** The abstract states that AI-designed T-domains "increase yields by up to ~3-fold relative to NRPSs carrying the native T-domain."
- **Evidence pointer** Figure 3a, Figure 7b, Results section "AI-designed T-domains can be leveraged to generate hybrid NRPSs"
- **Concern** The ~3-fold yield increase claim appears to derive from specific hybrid contexts (e.g., GxhS-1 where AI-27 and AI-31 outperform the native GxpS_T3 by large margins, and GshS where AI-2 and AI-12 show ~25-65% increases). However, the visible data do not clearly establish whether this improvement is consistent, statistically robust, or specific to certain contexts. In the full-length GxpS system (Figure 3a), the improvements over WT are more modest. The claim as stated in the abstract implies a generalizable improvement that the data may not support. Additionally, the peak area measurements used for hybrid systems are semi-quantitative, and the manuscript does not report statistical testing for these comparisons.
- **Why it matters** The yield improvement claim is a headline result that will attract attention from applied researchers. If the effect is context-specific or not statistically robust, the claim overstates the findings and could mislead potential users of the technology.
- **Resolution test** Provide statistical analysis (e.g., confidence intervals, effect sizes) for the yield comparisons across all contexts where the claim is made. Clarify in the abstract and results whether the ~3-fold improvement is specific to particular hybrid architectures or generalizable. If the improvement is context-specific, revise the claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "we generated 76 de novo T-domain sequences" and that these were "conditioned on the target junction environment" using three generative models.
- **Evidence pointer** Results section "AI-designed T-domains are frequently functional in a minimal NRPS assay system"; Methods section "Generative design and computational prioritization of T-domains"; Supplementary Note 1 (not provided)
- **Concern** The visible methods section provides only a high-level description of the generative design strategy. Critical details are relegated to Supplementary Note 1, which was not provided for review. Specifically, the following cannot be assessed: (1) the exact prompting/conditioning strategy for each model, (2) the filtering criteria and their thresholds, (3) the surrogate model architecture and training details, (4) how the "diversity" of generated sequences was ensured, and (5) the computational cost and feasibility of the approach. Without these details, the reproducibility of the design pipeline cannot be evaluated, and the claim that the approach is broadly applicable is not fully supported.
- **Why it matters** A central contribution of this work is the demonstration that generative models can be applied to NRPS T-domain design. If the design pipeline is not described in sufficient detail, other researchers cannot reproduce or build upon the approach, limiting its impact.
- **Resolution test** Provide the full content of Supplementary Note 1 in the revised manuscript or as accessible supplementary material. Ensure that all model parameters, filtering thresholds, and training procedures are described with sufficient detail for reproduction. If space constraints are an issue, consider moving some methods details to the main text.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "molecular dynamics simulations indicate preserved global stability but reshaped, state-dependent interdomain contact networks" for AI-2 compared to WT.
- **Evidence pointer** Results section "Molecular dynamics simulations suggest state-dependent alterations of interdomain contacts in WT GxpS_T3 and AI-2"; Figure 5; Supplementary Figures 7–9, 16; Supplementary Table 3
- **Concern** The MD simulation analysis is based on only two independent 100-ns simulations per system and state. This is a limited sampling for drawing conclusions about "state-dependent" differences in contact networks. The manuscript appropriately notes that the analysis is comparative and hypothesis-generating, but the claim of "reshaped, state-dependent interdomain contact networks" is presented in the abstract and results as a finding. The contact analysis criteria (hydrogen bonds with ≥30% occupancy, distance-based contacts with ≥80% occupancy) are reasonable, but the statistical robustness of the observed differences between WT and AI-2 is not established. Additionally, the homology models used as starting structures have domain-level sequence identities of 19.5–44.1% to templates, which raises questions about the reliability of the predicted contact networks.
- **Why it matters** The MD analysis is used to provide a mechanistic rationale for the observed functional differences. If the simulation results are not robust, the mechanistic interpretation is weakened, and the connection between sequence design and functional outcome becomes less clear.
- **Resolution test** Acknowledge more explicitly the limitations of the MD analysis in the main text. Consider additional simulations or enhanced sampling to strengthen the contact analysis. Alternatively, temper the language used to describe the MD findings, presenting them as preliminary observations that require experimental validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claims-to-evidence alignment
- **Claim pointer** The manuscript states that "the identity of the downstream C-domain emerged as the primary determinant of compatibility" based on the positional and hybrid experiments.
- **Evidence pointer** Results section "AI-designed T-domains can be leveraged to generate hybrid NRPSs"; Figure 7; Supplementary Figures 11–14
- **Concern** The conclusion that downstream C-domain identity is the primary determinant is based on a limited set of contexts. The authors tested T-domains designed for C/E-type contexts in C/E-containing hybrids (GxhS-1, GshS) and T-domains designed for LCL-type contexts in an LCL-containing hybrid (GxhS-2). However, the number of C-domain contexts tested is small (essentially two C-domain classes), and other factors such as the specific A-domain, linker length, or overall module architecture could also contribute to the observed patterns. The phylogenetic analysis (Supplementary Figure 10) is suggestive but does not establish causality.
- **Why it matters** The claim that downstream C-domain identity is the "primary determinant" is a strong conclusion that has implications for how researchers approach NRPS engineering. If this conclusion is overstated, it could lead to overly narrow design strategies.
- **Resolution test** Soften the language to indicate that downstream C-domain identity is "a major determinant" rather than "the primary determinant." Discuss alternative explanations for the observed patterns. If possible, include additional experiments testing T-domains in contexts with different downstream C-domains of the same class to strengthen the conclusion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The opening sentence "Large language models and generative protein design promise to accelerate biotechnology, but it remains unclear whether they can engineer dynamic megasynth(et)ases whose activity depends on transient, context-specific domain interfaces" is somewhat vague. The term "megasynth(et)ases" is unusual and may confuse readers unfamiliar with the field.
- **Required correction** Consider rephrasing to "Large language models and generative protein design promise to accelerate biotechnology, but their application to dynamic, multidomain assembly line enzymes such as non-ribosomal peptide synthetases (NRPSs) remains underexplored."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, generative design section
- **Evidence pointer** Methods section "Generative design and computational prioritization of T-domains"
- **Issue** The description of the surrogate model training states that "multiple modeling strategies were benchmarked, including linear regression on pretrained protein language model embeddings, zero-shot scoring approaches, and fine-tuning of ESMC68 using regression and contrastive objectives." The choice of the final two strategies (linear regression on ESMC embeddings and contrastive fine-tuning) is not justified in the visible text.
- **Required correction** Provide a brief justification for why these two strategies were selected over the alternatives, or refer to Supplementary Note 1 for this information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results, positional dependence section
- **Evidence pointer** Figure 6 and accompanying text
- **Issue** The positional dependence data (Figure 6) shows that the same T-domain variant can have very different activities at different positions. The text explains this in terms of downstream C-domain identity, but the figure does not clearly indicate which C-domain class is downstream of each position.
- **Required correction** Add annotations to Figure 6 indicating the downstream C-domain class for each position, or add this information to the figure legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, MD simulation section
- **Evidence pointer** Methods section "Molecular dynamics (MD) simulations"
- **Issue** The methods state that "two independent 100-ns simulations were performed" for each system and state. This is a relatively short simulation time for drawing conclusions about protein dynamics, and the manuscript does not report convergence checks or error estimates for the contact analyses.
- **Required correction** Add a brief statement about simulation convergence or acknowledge the limited sampling more explicitly in the methods or results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion, final paragraph
- **Issue** The final paragraph of the discussion introduces the concept of "partner-aware predictors" without sufficient context. This concept is not mentioned in the results and appears somewhat abruptly.
- **Required correction** Either introduce this concept earlier in the discussion or provide a brief explanation of what is meant by "partner-aware predictors" in this context.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, hybrid NRMS section
- **Evidence pointer** Results section "AI-designed T-domains can be leveraged to generate hybrid NRPSs"; Figure 7
- **Issue** The hybrid NRPS experiments use LC-MS peak areas as a semi-quantitative measure of product formation. The manuscript notes this limitation but does not provide any assessment of the variability of these measurements (e.g., technical replicates, coefficient of variation).
- **Required correction** Add information about the reproducibility of the LC-MS peak area measurements, or acknowledge this limitation more explicitly in the text.

## Risk / unsupported claims
- The claim of "up to ~3-fold" yield improvement is not fully supported by the visible data without statistical analysis and context specification.
- The statement that AI-designed T-domains "enable catalytically active hybrids at recombined junctions" is supported by the data, but the generalizability beyond the specific hybrids tested is not established.
- The MD simulation-based claim of "reshaped, state-dependent interdomain contact networks" is based on limited sampling and should be treated as preliminary.
- The conclusion that downstream C-domain identity is "the primary determinant" of T-domain compatibility is stronger than the evidence supports.
- The claim that the generative design approach "reduces, rather than eliminating, the experimental search" is reasonable but not quantitatively supported.
- The phylogenetic analysis (Supplementary Figure 10) is used to support the claim that AI-designed T-domains cluster by downstream partner identity, but the statistical significance of this clustering is not reported.
- The statement that "AI-2 consistently accumulated at higher levels and was readily recovered in the soluble fraction" is based on qualitative SDS-PAGE analysis; no quantitative protein yield data are provided.
- The manuscript claims that the work "establish[es] generative design as an effective route to context-conditioned engineering and reprogramming of biosynthetic assembly lines," but the demonstration is limited to a single NRPS system (GxpS) and two hybrid contexts.