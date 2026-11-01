## Review setup
- **Input scope** Full manuscript text provided (abstract, introduction, all main sections, tables, figure captions, author contributions, acknowledgments). No supplementary materials, no line numbers.
- **Assessment boundary** Evaluation is limited to the supplied manuscript text and its embedded tables and figure captions. No independent verification of cited primary literature, no access to supplementary data, no line-level referencing possible.
- **Shared manuscript claim summary** The manuscript is a narrative review proposing a three-tiered framework for Cas protein engineering (directed evolution, structure-based rational design, integrated protein engineering) and argues that AI and protein language models act as cross-layer enabling tools that, together with a de novo design paradigm, will drive development of miniaturized, broad-spectrum, high-precision editors toward clinical and industrial translation.
- **Visible evidence base** Abstract; Introduction with Fig. 1 and Fig. 2 and Tables 1 and 2; section on high-throughput screening and directed evolution with Fig. 3; section on structure-based rational design with Fig. 4; section on comprehensive protein engineering; section on AI and protein language models with Table 3; section on synergies and future trends with Table 4; Applications and prospects; Conclusion; author contributions; competing interest statement; acknowledgments.
- **Missing materials affecting confidence** No line numbers; no supplementary tables or data; no search strategy, database list, inclusion or exclusion criteria, or time window for literature selection; no PRISMA-style flow or equivalent for a review; no quantitative synthesis methods; no primary data; no figure permissions or licensing statement; no explicit statement of how references were screened or how many were excluded.

## Reviewer
- **Overall assessment** The manuscript is a broad, well-organized narrative review that maps three established Cas protein engineering paradigms and positions AI-based tools as an integrative layer. The conceptual framing (discovery layer, optimization layer, integration layer) is coherent and the tables are informative. However, as submitted, the work reads primarily as a structured synthesis of already published findings rather than a critical or systematic analysis. Several specific factual and interpretive claims are stated with more confidence than the cited evidence appears to support, at least from the material visible here. The central assertion that the review "fills a gap in systematic analysis within the field" is not demonstrated, because no systematic methodology, coverage analysis, or comparison against existing reviews is presented. The AI section is the most distinctive contribution but is largely descriptive and does not critically evaluate model performance, benchmarking, or failure modes. The manuscript is potentially useful to the field if the technical and framing concerns below are resolved.

- **Who would be interested in the results, and why** Researchers in CRISPR tool development, protein engineering, and computational protein design; groups working on AAV-compatible miniaturized editors; translational gene therapy teams evaluating editor selection; and computational biologists interested in how protein language models are being applied to editor optimization. The comparative tables (Tables 3 and 4) may be of practical use to newcomers seeking an orientation map of the field.

- **Major strengths**
  - The three-tier framework (directed evolution, rational design, integrated engineering) is clearly articulated and consistently applied across sections, with a corresponding summary in Table 4.
  - Table 3 provides a reasonably structured inventory of AI tools with architecture, advantages, limitations, and applications, which is a useful reference element.
  - The manuscript correctly emphasizes that AI-generated candidates still require wet-lab validation and does not overstate AI as a replacement for experimental work in the Conclusion.
  - The miniaturization discussion, including Cas12f and TnpB/IscB, is a relevant and timely topic for in vivo delivery.
  - The limitations subsections at the end of each major section are a constructive structural choice.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Originality and gap claim
- **Claim pointer** The abstract states that the review "fills a gap in systematic analysis within the field" and provides a "theoretical framework for tiered, synergistic modification."
- **Evidence pointer** Abstract; Introduction; no methods or search-strategy section anywhere in the supplied text; location not provided.
- **Concern** The manuscript asserts a gap-filling and systematic contribution but provides no methodology to substantiate either. There is no described literature search strategy, no database list, no inclusion or exclusion criteria, no time window, no screening procedure, and no comparison with existing reviews on Cas engineering or AI-assisted protein design. Without these, the claim of systematic analysis is not evaluable and the novelty relative to prior reviews cannot be assessed.
- **Why it matters** The primary claimed contribution of the manuscript is its systematic and gap-filling character. If this cannot be verified, the central justification for publication as a review is weakened, and readers cannot judge coverage completeness or selection bias.
- **Resolution test** Provide an explicit search and selection methodology (databases, query strings, date range, inclusion and exclusion criteria, number screened and included), and a short positioning statement comparing the scope of this review against at least three to five recent reviews in the same area, indicating what is added.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of specific factual claims
- **Claim pointer** The manuscript states that engineered small Cas proteins "can achieve editing efficiencies of up to 90% in human cells without significant off-target effects or tissue toxicity," and that AsCas12f variants yham and hkra achieved "a tenfold increase in activity without increasing the risk of off-target effects."
- **Evidence pointer** Applications and prospects section; Miniaturized design subsection; location not provided.
- **Concern** These are strong quantitative and safety claims presented without accompanying qualification of the assay system, cell type, target locus, delivery format, or the specific study conditions under which the numbers were obtained. The "up to 90%" figure is not attributed to a specific variant, locus, or reference in the visible text, and "without significant off-target effects or tissue toxicity" is a safety assertion that requires defined detection methods and sensitivity limits. Similarly, the tenfold activity increase and the absence of increased off-target risk require specification of the assay and the comparison baseline.
- **Why it matters** Quantitative performance and safety claims are the most consequential statements in a translational review. Unqualified numbers can be propagated into downstream planning and grant or regulatory documents. If the underlying conditions are not stated, the claims are not verifiable and may mislead.
- **Resolution test** For each quantitative claim, state the specific variant, the cell type or organism, the target locus, the delivery method, the assay used to measure activity and off-target events, and the corresponding reference. Where the original study reported context-dependent values, report the range and conditions rather than a single maximum.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Accuracy of attribution and mechanism
- **Claim pointer** The manuscript attributes HiFiCas9 development to "Mark A. Behlke's team" using a dual positive and negative screening system in E. coli, and attributes SuperFi-Cas9 to "the University of Texas team," and the WED domain work to "the Doudna team."
- **Evidence pointer** Overcoming the activity-specificity trade-off subsection; Enhancing specificity subsection; Enhanced efficiency subsection; location not provided.
- **Concern** Attribution by team or institution rather than by the specific study and its findings is imprecise and difficult to verify. In several cases the described mechanism is compressed to the point where it may not match the primary report, for example the description of HypaCas9 mutations and the REC3 domain role, and the description of SuperFi-Cas9 as targeting "non-specific interactions at the DNA-binding interface and abnormal structural flexibility." These mechanistic summaries require direct correspondence with the cited primary literature.
- **Why it matters** Mechanistic misattribution in a review propagates errors into the field and undermines the review's value as a reference. Institutional attribution also obscures which specific study is being discussed when a group has multiple relevant publications.
- **Resolution test** Replace institutional attribution with specific study citations and verify each mechanistic statement against the primary source. Where the mechanism is contested or simplified, state so explicitly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Critical evaluation of AI tools
- **Claim pointer** Table 3 and the AI section present AI tools as providing "computational support for optimizing Cas editors across multiple dimensions" and describe advantages such as "accurate prediction," "high-precision prediction," and "broad-spectrum prediction."
- **Evidence pointer** AI-driven Cas editor optimizes core toolchain subsection; Table 3; location not provided.
- **Concern** The AI section is largely enumerative. It does not report benchmarking results, head-to-head comparisons, performance metrics on Cas-specific tasks, or known failure modes beyond generic statements. For example, AlphaFold2 and AlphaFold3 are described as resolving "atomic-resolution 3D conformations" of Cas-sgRNA-DNA ternary complexes, but the manuscript does not address the documented limitations of these models for large, multi-component nucleic acid-protein assemblies, nor does it indicate which Cas complexes have actually been predicted with validated accuracy. Similarly, EVOLVEpro and the ESM suite are described as quantitatively ranking variant performance without reporting reported correlation with experimental measurements.
- **Why it matters** The AI section is the most distinctive part of the review. Without critical evaluation, it functions as a catalogue rather than an analysis, and readers cannot judge which tools are actually usable for which Cas engineering tasks.
- **Resolution test** Add reported performance metrics where available (for example correlation coefficients, top-k enrichment, success rates in prospective validation), specify which Cas systems each tool has been applied to and with what outcome, and explicitly discuss documented failure modes and domains where predictions are unreliable.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency of the framework
- **Claim pointer** The manuscript states that rational design "does not require prior structural information of target proteins" in the technical workflow paragraph, while the same section and the limitations paragraph state that rational design "relies heavily on structural knowledge" and requires "high-resolution structures of protein-substrate complexes."
- **Evidence pointer** Structure-based rational design section, technical workflow paragraph and limitations paragraph; location not provided.
- **Concern** The statement that the remodeling strategy "does not require prior structural information of target proteins" appears to contradict the defining premise of structure-based rational design as presented throughout the manuscript. This may be a drafting error, but as written it creates an internal inconsistency in the core conceptual framework.
- **Why it matters** The three-tier framework depends on a clear distinction between methods that require structural knowledge and those that do not. An internal contradiction at this point undermines the framework's clarity.
- **Resolution test** Correct or clarify the statement so that the structural information requirement of rational design is stated consistently throughout.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Evidence for the de novo design paradigm
- **Claim pointer** The manuscript states that AI can "independently generate artificial editing scaffolds without natural evolutionary templates" and cites OpenCRISPR-1 as an example of overcoming performance bottlenecks via multi-site synergistic optimization.
- **Evidence pointer** Multidimensional advantages of AI-powered Cas protein engineering subsection; Overcoming the activity-specificity trade-off subsection; location not provided.
- **Concern** The claim of fully template-free generation of functional editors is a strong one and is presented without describing the extent of experimental validation, the performance relative to natural editors, or the current limitations of such generated scaffolds. OpenCRISPR-1 is cited in a list alongside screening-derived variants without distinguishing what was AI-generated versus what was experimentally optimized.
- **Why it matters** The de novo design paradigm is presented as a new avenue for creating editors with novel functions. If the actual validated performance and remaining gaps are not described, the reader cannot assess whether this is an established capability or an early-stage aspiration.
- **Resolution test** For each de novo designed editor cited, state the design method, the experimental validation performed, the measured performance relative to a natural comparator, and the current limitations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Classification of CRISPR systems
- **Evidence pointer** Introduction, second paragraph; location not provided.
- **Issue** The text states the system "can be classified into Type I and Type II systems based on the number of Cas proteins, and is further subdivided into seven classes (Types I-VII)," then refers to "Class I systems (Types I, III, IV, and VII)" and "Class II systems (Types II, V, and VI)." The terms Type and Class are used interchangeably in a way that is inconsistent with standard nomenclature, where Class 1 and Class 2 are the higher-level divisions and Types I through VII are the subclasses.
- **Required correction** Use the standard Class 1 and Class 2 terminology for the multi-subunit versus single-protein division, and reserve Type I through VII for the subclasses, consistently throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure caption accuracy
- **Affected element** Fig. 1 caption
- **Evidence pointer** Fig. 1 caption; location not provided.
- **Issue** The caption states that prime editing supports "small insertions (approximately 40 bp), small deletions (approximately 80 bp), and precise point mutations within approximately 30 bp flanking the Cas9 nicking site." These specific size limits require a supporting citation and should be qualified as typical rather than fixed limits, since reported capacities vary by system and study.
- **Required correction** Add a citation for the size ranges and state them as reported typical ranges with the conditions under which they were measured.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Table completeness and consistency
- **Affected element** Table 3
- **Evidence pointer** Table 3; location not provided.
- **Issue** Table 3 lists ProteinBERT, MSA Transformer, ProtTrans, and Evo within the sequence representation category, but the main text of the AI toolchain section describes only the ESM suite and EVOLVEpro in that category. The table and text are not aligned, and several table entries lack a clear statement of whether they have been applied specifically to Cas editors or only to general protein tasks.
- **Required correction** Align the table with the text, and for each entry indicate explicitly whether Cas-specific application has been demonstrated and cite the corresponding study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference formatting
- **Affected element** In-text citation
- **Evidence pointer** Introduction, first paragraph; location not provided.
- **Issue** The phrase "enabling precise gene knockout or knock-in Refs. [9,10]" contains an inconsistent citation format relative to the rest of the manuscript, which uses bracketed numerals.
- **Required correction** Standardize the citation format throughout.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure attribution
- **Affected element** Fig. 1 through Fig. 4 captions
- **Evidence pointer** Fig. 1, Fig. 2, Fig. 3, Fig. 4 captions; location not provided.
- **Issue** All four figure captions state "Created with BioGDP.com [13]." It is unclear whether this indicates the figures were generated using a commercial platform, which has implications for licensing, originality, and reproducibility of the schematics.
- **Required correction** Clarify the role of the platform in figure generation and confirm that all schematics are original and that any third-party content is appropriately licensed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Claim scope
- **Affected element** Applications and prospects section
- **Evidence pointer** Applications and prospects section; location not provided.
- **Issue** The statement that small Cas proteins "combine the advantages of high editing efficiency, low immunogenicity, and a broad targeting range" is presented as a general property of the class, whereas these properties are variant-specific and have been achieved only in particular engineered variants under particular conditions.
- **Required correction** Attribute these properties to specific engineered variants and conditions rather than to small Cas proteins as a class.

- **Technical failings that need to be addressed before the case is established** R1-M1 (absence of systematic methodology for a review claiming systematic gap-filling), R1-M2 (unqualified quantitative and safety claims), R1-M3 (imprecise attribution and mechanistic summaries), R1-M4 (absence of critical evaluation and benchmarking in the AI section), R1-M5 (internal contradiction regarding structural information requirements), R1-M6 (insufficient evidence for de novo design claims).

- **Assessment against Nature-style criteria**
  - **Originality** Limited as presented. The three-tier framework is a reasonable organizational device but overlaps substantially with existing reviews on Cas engineering. The AI section is the most potentially original element but is currently descriptive rather than analytical. The claimed gap-filling is not demonstrated.
  - **Scientific importance** The topic is important and timely, particularly the integration of AI tools with editor engineering and the miniaturization problem for in vivo delivery. However, the current treatment does not advance a new argument or synthesis beyond cataloguing.
  - **Interdisciplinary readership** The manuscript is potentially accessible to a broad readership across protein engineering, computational biology, and gene therapy. The tables support this. However, the density of unexplained jargon and the lack of critical framing reduce accessibility for nonspecialists.
  - **Technical soundness** Several specific claims are stated without sufficient qualification or supporting detail (R1-M2, R1-M3, R1-M6), and there is an internal contradiction in the framework (R1-M5). The AI section lacks benchmarking and failure-mode discussion (R1-M4).
  - **Readability for nonspecialists** The prose is generally clear but frequently dense, with long compound sentences and heavy use of field-specific abbreviations. Key concepts such as PAM, NHEJ, DBTL, and PLM are used with limited or no definition at first use. The figure captions are detailed and helpful.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires a defined review methodology, qualification or correction of quantitative and safety claims, precise attribution of mechanistic findings, critical evaluation of AI tool performance, resolution of the internal contradiction in the framework, and stronger support for the de novo design claims before the central contribution can be assessed.

## Risk / unsupported claims
- Claim that the review "fills a gap in systematic analysis within the field" is unsupported because no systematic methodology or comparison with existing reviews is provided (R1-M1).
- Claim that engineered small Cas proteins achieve "editing efficiencies of up to 90% in human cells without significant off-target effects or tissue toxicity" is not evaluable without specification of variant, locus, assay, and detection sensitivity (R1-M2).
- Claim that AsCas12f yham and hkra achieved "a tenfold increase in activity without increasing the risk of off-target effects" is not evaluable without assay conditions and baseline definition (R1-M2).
- Claim that AI can "independently generate artificial editing scaffolds without natural evolutionary templates" is weakly supported because validation extent and comparative performance are not described (R1-M6).
- Claim that AI-driven rational design cuts "screening cycles and experimental costs by orders of magnitude" is a quantitative assertion presented without supporting measurement or citation detail (R1-M4).
- Claim that AI tools "resolve atomic-resolution 3D conformations of Cas monomers and Cas-sgRNA-DNA ternary complexes" overstates current demonstrated capability for large multi-component assemblies without qualification (R1-M4).
- Claim that the integrated strategy "represents the mainstream strategy for developing high-performance Cas editing tools today" is asserted without survey or bibliometric support.
- Claim that small Cas proteins as a class "combine the advantages of high editing efficiency, low immunogenicity, and a broad targeting range" generalizes variant-specific properties to a protein class (R1-m6).
- Statement that rational design "does not require prior structural information of target proteins" contradicts the manuscript's own framework and is unsupported as written (R1-M5).