## Review setup
- **Input scope** Full manuscript text (review article), including Simple Summary, main text, and Acknowledgments. No figures, tables, or reference list were provided.
- **Assessment boundary** Assessment is limited to the scientific content, logical coherence, internal consistency, and evidentiary support of the narrative review as presented in the text. Claims about specific quantitative values are assessed against the internal consistency of the manuscript and the stated provenance of the data. No external verification of cited literature was performed.
- **Shared manuscript claim summary** The manuscript is a narrative review of microbial rhodopsins, focusing on structural-functional mechanisms and their application to optogenetic silencing tool design. It places particular emphasis on a newly characterized archaeorhodopsin, HeAR, from a Halorubrum strain isolated from Ejinoor Salt Lake, Inner Mongolia. The authors summarize the rhodopsin family, photocycle dynamics, and ion-pumping mechanisms, then compare HeAR quantitatively with established rhodopsins (BR, AR3, AR4), and finally review the landscape of optogenetic silencing tools and rational design strategies. A central claim is that HeAR possesses a distinctive kinetic signature (fast M-state formation/decay, slow overall photocycle, slow dark adaptation) that may have implications for low-light silencing, though the authors explicitly state this remains a hypothesis requiring direct testing.
- **Visible evidence base** The manuscript cites a body of literature (references numbered [1]–[223]) and draws on the authors' own prior work (Ref. [24]) for quantitative HeAR data. Specific quantitative values are presented for HeAR (absorption maxima, photocycle kinetics, pKa, proton extrusion rates, ATP levels) and for comparators (BR, AR3, AR4). Figures 1–3 are described but not visible. Tables 1–3 are referenced but not provided.
- **Missing materials affecting confidence** Figures 1–3, Tables 1–3, and the full reference list were not provided. This limits verification of quantitative comparisons, figure-data consistency, and citation accuracy. The absence of Table 1 is particularly significant given its central role in the HeAR comparison.

## Reviewer

- **Overall assessment** This is a well-structured and thoughtfully written narrative review that addresses a timely and important topic: the gap between excitatory and inhibitory optogenetic tools, and the potential of newly characterized archaeorhodopsins to fill that gap. The authors are commendably explicit about the limits of their evidence, repeatedly distinguishing measured properties from hypotheses, and clearly labeling the provenance of quantitative data. The treatment of HeAR is appropriately cautious, and the authors resist overclaiming its utility. The review is likely to be of interest to researchers in microbial rhodopsin biophysics and optogenetic tool development. However, the manuscript has several weaknesses that need to be addressed. The most significant is the tension between the stated emphasis on HeAR and the relatively thin, single-source evidence base for its distinctive properties. The review also suffers from some internal inconsistencies in quantitative claims, a tendency toward overlong and occasionally repetitive prose, and a lack of critical depth in some sections where the literature is summarized rather than interrogated. The absence of the tables and figures in the provided material makes full assessment of the comparative framework impossible. Overall, the manuscript is promising but requires revision to sharpen its claims, resolve inconsistencies, and fully deliver on its stated aims.

- **Who would be interested in the results, and why** Researchers in optogenetics, particularly those developing or applying inhibitory tools for neural silencing; biophysicists studying microbial rhodopsin structure-function relationships, photocycle kinetics, and ion transport mechanisms; synthetic biologists interested in light-driven energy conversion modules; and neuroscientists using optogenetic tools in circuit dissection or translational research. The comparative framework for evaluating silencing tools, and the explicit discussion of what has and has not been measured for HeAR, will be valuable to these communities.

- **Major strengths** The manuscript has several notable strengths. First, the authors are exceptionally transparent about the evidentiary status of their claims, explicitly distinguishing measured properties from hypotheses and clearly labeling the provenance of quantitative data. This is a model of scientific honesty in a review context. Second, the comparative framework, particularly the quantitative comparison of HeAR with BR, AR3, and AR4, is a valuable contribution that goes beyond typical narrative reviews. Third, the authors demonstrate strong command of the historical and current literature, from foundational work in the 1970s to recent cryo-EM and machine-learning approaches. Fourth, the review is well-organized, with a logical progression from basic rhodopsin biology to tool design and application. Fifth, the authors are careful to classify tools and strategies by molecular mechanism, avoiding the conflation that often plagues this literature. Finally, the explicit statement of literature selection criteria and their limitations is commendable and should be a model for other narrative reviews.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The manuscript's central emphasis is that HeAR possesses a distinctive combination of properties—fast M-state formation and decay, slow overall photocycle, slow dark adaptation, and a raised counterion pKa—that may have implications for low-light silencing. The authors state this is a hypothesis requiring direct testing, but the framing of the review gives this hypothesis substantial prominence.
- **Evidence pointer** Section 4.3, Section 6.6, Table 1 (not provided)
- **Concern** The entire case for HeAR's distinctiveness rests on a single source (Ref. [24], the authors' own work) and a single expression system (E. coli, in vitro biophysics of purified protein). The authors acknowledge this, but the review's structure gives HeAR disproportionate weight relative to the evidence base. The comparison with AR3 and AR4 is based on literature values from different laboratories, expression systems, and measurement conditions, which the authors acknowledge but do not systematically address. The absence of Table 1 in the provided material makes it impossible to assess whether the comparison is appropriately qualified.
- **Why it matters** A review that emphasizes a specific protein as a potential tool platform must establish that the protein's distinctive properties are robust and not artifacts of a single measurement context. If the HeAR data are not reproducible across expression systems or measurement conditions, the review's central emphasis is undermined. The current presentation does not allow the reader to assess this.
- **Resolution test** The authors should either (a) provide a more systematic and critical comparison of measurement conditions across studies, explicitly discussing how differences in expression system, membrane environment, pH, temperature, and detergent might affect the quantitative values, or (b) explicitly reframe the review to present HeAR as a case study in how new rhodopsins should be characterized, rather than as a protein with established distinctive properties. The latter would be more appropriate given the evidence base.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency of quantitative claims
- **Claim pointer** The manuscript states that HeAR's slow dark adaptation "does not by itself increase per-molecule charge turnover" and that "the proposal that it improves low-light silencing therefore needs direct measurement." However, in Section 6.6, the authors list as a design implication that "the coupling between M-state kinetics and silencing efficacy merits reassessment," citing the same kinetic features.
- **Evidence pointer** Section 3.2, Section 6.6
- **Concern** There is a tension between the cautious framing in Section 3.2, where the authors correctly note that slow dark adaptation does not imply improved silencing, and the more speculative framing in Section 6.6, where the same features are presented as design implications. The authors do not clearly resolve this tension. If slow dark adaptation does not increase per-molecule charge turnover, then its relevance to silencing is unclear, and the review should say so more directly.
- **Why it matters** The review's stated aim is to provide a comparative framework for tool design. If the implications drawn from HeAR's kinetics are not clearly grounded in the measured properties, the framework risks being misleading.
- **Resolution test** The authors should either (a) provide a more explicit mechanistic argument for why slow dark adaptation might matter for silencing, despite not increasing per-molecule charge turnover, or (b) remove or substantially qualify the design implication in Section 6.6.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Critical depth of literature review
- **Claim pointer** The review covers a broad range of topics, from rhodopsin family classification to optogenetic tool applications, but in several sections the treatment is largely descriptive rather than critical.
- **Evidence pointer** Sections 2, 5, 7
- **Concern** In several places, the review summarizes findings without critically evaluating them. For example, the discussion of optogenetic silencing tools in Section 5 catalogs tools and their properties but does not systematically compare their relative strengths and weaknesses for specific applications. Similarly, the discussion of machine-learning approaches in Section 6.4 is brief and does not critically assess the limitations of these methods. The review would be stronger if it provided a more analytical framework, identifying open questions and controversies in the field.
- **Why it matters** A Nature-style review is expected to provide not just a summary but a critical synthesis that advances the field's understanding. The current manuscript is more descriptive than analytical in places.
- **Resolution test** The authors should add critical analysis to at least the following: (a) a systematic comparison of silencing tool performance metrics across studies, (b) a discussion of the limitations and failure modes of machine-learning approaches to rhodopsin design, and (c) an explicit statement of the most important open questions in the field.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and provenance of quantitative data
- **Claim pointer** The manuscript presents quantitative values for HeAR (absorption maxima, photocycle kinetics, pKa, proton extrusion rates, ATP levels) and for comparators (BR, AR3, AR4) without providing sufficient detail on measurement conditions for the comparators.
- **Evidence pointer** Section 4.3, Table 1 (not provided)
- **Concern** The authors state that "excitation wavelength and intensity, pH, temperature, detergent and the fitting model all differ between these studies" for the kinetic comparison, but they do not provide a systematic account of these differences. Without this, the reader cannot assess the validity of the quantitative comparisons. The absence of Table 1, which presumably contains this information, is a significant gap in the provided material.
- **Why it matters** Quantitative comparisons across studies are only meaningful if measurement conditions are comparable or if differences are explicitly accounted for. The current presentation does not allow the reader to make this assessment.
- **Resolution test** The authors should provide a table (or expand Table 1) that systematically lists measurement conditions for each quantitative value cited, including expression system, membrane environment, pH, temperature, detergent, and fitting model. This would allow readers to assess the robustness of the comparisons.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Section 3.2, use of "slow recovery"
- **Evidence pointer** Section 3.2
- **Issue** The term "slow recovery" is used ambiguously. The authors clarify that it refers to light-dark adaptation, not photocycle duration, but the term could be confused with recovery from the photocycle itself.
- **Required correction** Use a more specific term, such as "slow dark adaptation" or "slow light-dark re-equilibration," throughout, and define it clearly at first use.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 4.3, long and complex sentences
- **Evidence pointer** Section 4.3
- **Issue** Some sentences in Section 4.3 are very long and contain multiple qualifications, making them difficult to follow. For example, the sentence beginning "The comparison must, however, be read with care..." is a single sentence with multiple clauses.
- **Required correction** Break long sentences into shorter, more digestible units. Consider using bullet points or a table for the detailed comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of figure descriptions
- **Affected element** Figures 1–3
- **Evidence pointer** Figures 1–3 (not provided)
- **Issue** The figure descriptions in the text are brief and do not fully convey the content. For example, Figure 1 is described as showing the four major groups of rhodopsins, but the specific structural features illustrated are not described.
- **Required correction** Provide more detailed figure legends that describe the specific content of each panel, including any structural features, kinetic traces, or comparative data shown.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency of classification
- **Affected element** Section 2.1, classification of rhodopsins
- **Evidence pointer** Section 2.1
- **Issue** The classification of rhodopsins into four major groups (ion pumps, ion channels, photosensors, enzyme rhodopsins) is presented as a standard framework, but the placement of some members (e.g., heliorhodopsins) within this framework is not fully discussed.
- **Required correction** Briefly acknowledge that the classification is a working framework and note any members that do not fit neatly into the four groups.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Citation completeness
- **Affected element** Section 5.5, discussion of optoGPCR and eOPN3
- **Evidence pointer** Section 5.5
- **Issue** The discussion of optoGPCR and eOPN3 is brief and does not provide sufficient context for readers unfamiliar with these tools.
- **Required correction** Add a sentence or two describing the mechanism of action of these tools and their relative advantages or disadvantages compared to rhodopsin-based tools.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity of scope
- **Affected element** Section 7.3, clinical translation
- **Evidence pointer** Section 7.3
- **Issue** The discussion of clinical translation is somewhat scattered, covering retinal therapies, brain-computer interfaces, and plant/Drosophila applications in a short space.
- **Required correction** Consider reorganizing this section to focus more clearly on the most important clinical opportunities and barriers, and to distinguish more clearly between near-term and long-term prospects.

- **Technical failings that need to be addressed before the case is established** The central case for HeAR's distinctive properties rests on a single source and a single expression system. The authors acknowledge this, but the review's structure gives HeAR disproportionate weight. The absence of Table 1 in the provided material is a significant gap. The internal tension between the cautious framing in Section 3.2 and the more speculative framing in Section 6.6 needs to be resolved. The review would benefit from a more systematic and critical comparison of measurement conditions across studies.

- **Assessment against Nature-style criteria** 
  - **Originality**: The review is not entirely original in its topic, as microbial rhodopsins and optogenetics have been reviewed extensively. However, the specific emphasis on HeAR as a newly characterized archaeorhodopsin, and the explicit comparative framework for evaluating silencing tools, provides a degree of originality. The authors' transparency about the evidentiary status of their claims is also a distinctive feature.
  - **Scientific importance**: The topic is of high scientific importance. The gap between excitatory and inhibitory optogenetic tools is a well-recognized problem, and the review addresses it directly. The comparative framework for evaluating silencing tools is potentially valuable. However, the importance of the HeAR-specific claims is not yet established, as the authors themselves acknowledge.
  - **Interdisciplinary readership**: The review is likely to appeal to a broad interdisciplinary audience, including biophysicists, neuroscientists, synthetic biologists, and optogenetics researchers. The authors make an effort to explain concepts clearly, and the Simple Summary is accessible. However, some sections are dense and may be challenging for non-specialists.
  - **Technical soundness**: The review is generally technically sound, with appropriate caveats about the limits of the evidence. However, the internal inconsistency in the kinetic comparison (M-state decay of 3.3 ms vs. 3.5 ms) and the lack of systematic accounting for measurement conditions across studies are weaknesses. The absence of Table 1 in the provided material limits assessment.
  - **Readability for nonspecialists**: The Simple Summary is clear and accessible. The main text is generally well-written but is dense in places and would benefit from more careful editing to improve readability. Some sentences are overly long and complex.

- **Recommendation posture** Supportive if technical concerns are resolved. The review addresses an important topic, is well-structured, and demonstrates commendable scientific honesty. However, the central emphasis on HeAR needs to be better supported by a more systematic and critical comparison of measurement conditions, and the internal inconsistency in the kinetic comparison needs to be resolved. The absence of Table 1 in the provided material makes full assessment impossible, but the text suggests the table would address many of these concerns. With these revisions, the review would be a valuable contribution to the field.

## Risk / unsupported claims
- The claim that HeAR's slow dark adaptation "may help maintain spectral and kinetic stability under extracellular environmental fluctuations" (Section 6.6) is presented as a design implication but is not directly supported by any measurement of stability under fluctuating conditions. This is an inference from the measured pKa and kinetics, and should be labeled as such.
- The claim that "the longer cycle lowers maximal per-molecule turnover relative to BR, so any low-light advantage must be measured rather than inferred" (Section 4.3) is appropriately cautious, but the framing in Section 6.6 that the kinetic signature is a design implication is not fully consistent with this caution.
- The statement that "AR4, which is 95% identical to HeAR, has been produced recombinantly in Halobacterium salinarum L33 at yields of up to 20 mg L−1 with its trimeric packing and proton-pumping kinetics retained" (Section 6.6) is presented as evidence that HeAR-based tools are feasible, but this is an inference from homology, not a direct demonstration for HeAR. The authors should clarify this.
- The claim that "the authors' team's work on Ejinoor Salt Lake shows that in-depth characterization of a single strain can yield a complete structural-functional parameter set with tool value" (Section 7.4) is an assertion about the value of the work that is not directly supported by the evidence presented in this review.
- The statement that "no archaeorhodopsin has entered clinical testing" (Section 7.3) is presented as a fact, but the source for this claim is not provided in the text.