## Review setup
- **Input scope** Full manuscript text (abstract, introduction, main sections, conclusion, acknowledgements)
- **Assessment boundary** Scientific content, logical coherence, evidence quality, and alignment with stated review objectives; no assessment of formatting or reference completeness beyond what is visible
- **Shared manuscript claim summary** The authors argue that despite the dominance of generative models in protein design, physical principles remain essential and must be integrated through physically grounded representations, physics-inspired architectural constraints, and experimental data to achieve functional protein design, especially under out-of-distribution conditions.
- **Visible evidence base** Narrative review with cited examples (BindCraft, RFdiffusion, Boltz-2, TERMinator, ChromaDesign, Caliby, AlloGen, PLACER, AlphaFold3, LASErMPNN, COMBS, Protpardelle, Metal3D), case studies (exatecan binder, zinc phosphatase, serine hydrolase), and descriptions of recent experimental assays (Martell et al., Ferrari et al., Müntener and Abramson et al., Passow et al.). No figures or tables were provided in the supplied material.
- **Missing materials affecting confidence** Figures (Figure 1 and Figure 2 are referenced but not included), full reference list, and any supplementary data or methodological details for the cited case studies. The absence of figures limits assessment of visual evidence supporting key claims.

## Reviewer
- **Overall assessment** This is a well-written and timely perspective that addresses a critical gap in the current discourse on protein generative modeling. The authors make a compelling case for the continued relevance of physics, supported by a broad range of recent examples. However, the manuscript is more of a narrative synthesis than a systematic review, and several claims would benefit from quantitative evidence or clearer definitions. The central thesis is plausible and important, but the evidence base is uneven, with some assertions resting on single examples or unpublished work. The manuscript would be strengthened by a more explicit framework for evaluating when physics integration is necessary and by addressing potential counterarguments more directly.
- **Who would be interested in the results, and why** Computational biologists, protein engineers, and machine learning researchers working on generative models for biomolecular design. The review is also relevant to experimentalists interested in the interface between computational design and biophysical characterization. The discussion of physically grounded representations and experimental data integration speaks directly to current challenges in functional protein design.
- **Major strengths** The manuscript provides a clear and balanced perspective on a rapidly evolving field. The authors successfully identify key failure modes of purely data-driven approaches, such as adversarial examples and length generalization issues. The discussion of physics-inspired architectural regularization, particularly the Potts model, is insightful and connects historical methods to modern architectures. The inclusion of recent experimental assays that could expand the modelable space is forward-looking and practical. The writing is accessible to a broad audience without oversimplifying technical details.
- **Major Concerns** The manuscript lacks a systematic framework for evaluating the relative importance of different physical components. Several claims are supported by single case studies or anecdotal evidence, which may not generalize. The discussion of "physical foundation" is sometimes vague, and the authors do not clearly define what constitutes "physics" versus "data-driven" in hybrid approaches. The treatment of electrostatics is interesting but underdeveloped, with no discussion of recent ML-based electrostatic models. The conclusion is somewhat generic and does not synthesize the diverse threads into a coherent roadmap.
- **Minor Comments** The abstract is dense and could benefit from a clearer statement of the review's scope. The transition between sections is sometimes abrupt. The authors use "physical" and "physics-based" interchangeably, which could confuse readers. The discussion of autoguidance is interesting but would benefit from a more detailed explanation of the mechanism. The reference to "low temperature sampling" is used multiple times but never formally defined. The final paragraph on experimental assays is a list-like enumeration that could be better integrated into the main argument.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide quantitative comparisons between physics-integrated and purely data-driven approaches. The claim that "physics is not adequately captured by generative models" is asserted but not rigorously demonstrated. The case studies are described qualitatively, and no performance metrics are provided. The discussion of Boltz-2's affinity module is too brief to assess its relevance. The absence of figures limits the ability to evaluate the proposed framework.
- **Assessment against Nature-style criteria** Originality: The perspective is original in its synthesis of recent developments, though individual ideas have been discussed elsewhere. Scientific importance: The topic is of high importance given the rapid adoption of generative models in protein design. Interdisciplinary readership: The manuscript is accessible to both computational and experimental researchers, though some sections assume familiarity with ML terminology. Technical soundness: The arguments are logically coherent but lack quantitative support. Readability for nonspecialists: The writing is clear, but the abstract and some technical sections may be challenging for readers without a background in both ML and biophysics.
- **Recommendation posture** Supportive if technical concerns are resolved. The core thesis is valuable and timely, but the manuscript would benefit from a more rigorous evidence base, clearer definitions, and a more structured framework for evaluating physics integration.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Physics is not adequately captured by generative models or by structure prediction oracles, since length is a statistical property of the training set rather than a physical variable."
- **Evidence pointer** Section "Limitations of structure prediction models for ranking designs", location not provided
- **Concern** The claim that length generalization failure is due to physics not being captured is asserted without direct evidence. The authors attribute the performance drop to a statistical property of the training set, but this is a hypothesis, not a demonstrated mechanism. Alternative explanations, such as architectural limitations or training data distribution, are not discussed.
- **Why it matters** This claim is central to the manuscript's thesis that physics integration is necessary. If the failure is due to other factors, the argument for physics-based grounding is weakened.
- **Resolution test** Provide quantitative evidence, such as controlled experiments comparing models with and without physics-based features on length generalization tasks, or cite existing studies that directly test this hypothesis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Definitional clarity
- **Claim pointer** "Respecting the underlying physics of macromolecular systems, increasingly through learned representations that are physically grounded and updating generative models with experimental data, is foundational to generative modeling for functional protein design."
- **Evidence pointer** Abstract, location not provided
- **Concern** The term "physically grounded" is used throughout but never precisely defined. It is unclear whether this refers to representations that encode physical quantities (e.g., energies, forces), architectures that mimic physical processes, or training objectives that incorporate physical constraints. The lack of a clear definition makes it difficult to evaluate the claims.
- **Why it matters** The central recommendation of the manuscript depends on this concept. Without a clear definition, readers cannot assess which approaches qualify as "physically grounded" and which do not.
- **Resolution test** Provide an explicit definition of "physically grounded" with examples and non-examples, and use this definition consistently throughout the manuscript.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** "A meta-analysis of 3,766 experimentally characterized binders show that physics-based metrics provide additional predictive power to sort in silico binders from non-binders compared to structure prediction metrics alone, such as ipSAE."
- **Evidence pointer** Section "Physical terms as filters and guidance", location not provided
- **Concern** The meta-analysis is cited but not described in sufficient detail. The authors do not specify the source, methodology, or effect sizes. This makes it impossible to assess the strength of the evidence.
- **Why it matters** This is a key quantitative claim supporting the use of physics-based filters. Without details, readers cannot verify the claim or understand its scope.
- **Resolution test** Provide the citation and a brief summary of the meta-analysis methodology and key results, including effect sizes and confidence intervals.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** "Recent work showing the convergence of internal representations of scientific foundation models hint at a common physical structure learned by otherwise dissimilar models."
- **Evidence pointer** Section "Grounding models in physics-based representations and architectures", location not provided
- **Concern** The "recent work" is not cited or described. The claim is vague and cannot be evaluated without knowing which models were compared and what "convergence" means operationally.
- **Why it matters** This claim supports the idea that physical structure emerges naturally in well-trained models, which is relevant to the argument for physics-based grounding. Without evidence, it remains an unsupported assertion.
- **Resolution test** Provide specific citations and a brief description of the studies, including the models compared and the metrics used to assess representation convergence.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** "The decision to use a Potts model to parameterize the distribution of sequences from which to sample may seem counterintuitive given the flexibility of autoregressive models, as the latter can capture any arbitrary distribution over sequences, including higher-order correlations beyond second order. However, several works indicate that second order terms are necessary and sufficient to capture protein structure and function."
- **Evidence pointer** Section "Physics-inspired architectural regularization", location not provided
- **Concern** The claim that second-order terms are "necessary and sufficient" is strong and likely overstated. The cited works may show that second-order models perform well in specific contexts, but this does not establish necessity or sufficiency in general. The authors do not discuss potential limitations or counterexamples.
- **Why it matters** This claim justifies the use of Potts models as a design choice. If it is overstated, the argument for architectural regularization is weakened.
- **Resolution test** Soften the claim to reflect the specific contexts in which second-order models have been shown to be effective, and discuss any known limitations or cases where higher-order terms are needed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is dense and covers many topics without a clear roadmap. The phrase "physical foundation" is used but not explained.
- **Required correction** Consider restructuring the abstract to state the review's scope, the main argument, and the key conclusions more explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section "Physical terms as filters and guidance"
- **Evidence pointer** Section "Physical terms as filters and guidance", location not provided
- **Issue** The terms "physics-based" and "physical" are used interchangeably, which could confuse readers. For example, "physics-based metrics" and "physical plausibility" are used in the same paragraph.
- **Required correction** Define these terms and use them consistently, or clarify the distinction between them.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Kinetics as an explicit design objective"
- **Evidence pointer** Section "Kinetics as an explicit design objective", location not provided
- **Issue** The discussion of low temperature sampling is repeated from earlier sections but never formally defined. The mechanism by which it "averages out unmodeled latent variables" is not explained.
- **Required correction** Provide a brief definition of low temperature sampling and a more detailed explanation of its effect on the learned distribution.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "New assays to expand the modelable space"
- **Evidence pointer** Section "New assays to expand the modelable space", location not provided
- **Issue** The enumeration of experimental methods reads like a list and is not well integrated into the main argument. The connection between these assays and the thesis of physics integration is not made explicit.
- **Required correction** Add a concluding sentence that ties these methods back to the central argument, explaining how they enable physics-aware model training or validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Distilling the necessary and sufficient physical conditions for functional protein design"
- **Evidence pointer** Section "Distilling the necessary and sufficient physical conditions for functional protein design", location not provided
- **Issue** The term "necessary and sufficient physical conditions" is used in the section title but not defined or systematically addressed in the text. The examples given are illustrative but do not establish a general framework.
- **Required correction** Either define what is meant by "necessary and sufficient" in this context or revise the title to be less definitive.

## Risk / unsupported claims
- The claim that "second order terms are necessary and sufficient to capture protein structure and function" is not supported by the evidence provided and is likely an overstatement.
- The claim that "physics is not adequately captured by generative models" is asserted without direct quantitative evidence.
- The "meta-analysis of 3,766 experimentally characterized binders" is cited but not described, making it impossible to evaluate.
- The "recent work showing the convergence of internal representations" is not cited or described, rendering the claim unverifiable.
- The assertion that "low temperature sampling... effectively averages out the unmodeled latent variables" is presented as a mechanism but is not explained or supported.
- The claim that "modeling electrostatics is sparse in recent machine learning methods" is made without a systematic survey or citation.