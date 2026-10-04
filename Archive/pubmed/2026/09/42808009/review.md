## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability)
- **Assessment boundary** Scientific and technical evaluation of the ProNA3D tool, its demonstrated applications, and the claims made regarding its functionality and findings from large-scale analyses
- **Shared manuscript claim summary** The authors present ProNA3D, a UCSF ChimeraX plug-in and command-line tool for analyzing protein–nucleic acid and nucleic acid-only interfaces. The tool supports experimental and predicted structures, includes AlphaFold 3 confidence metrics, provides 2D interface visualization and secondary-structure topology plots, and enables cryo-EM density zoning. The authors demonstrate the tool on four diverse complexes and report a large-scale PDB analysis revealing distinct connectivity trends between nucleic acid-only and protein–nucleic acid interfaces, including specialized modes such as base flipping.
- **Visible evidence base** Full text including four application examples (hammerhead ribozyme, Fab–HIV-1 RNA, Cre recombinase–DNA, DHX36–G-quadruplex RNA), large-scale PDB analysis with connectivity distributions, methods section, and supplementary figure/table references
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S7, Tables S1–S14) not provided; no access to the software repository or code; no benchmark or validation data against existing tools; no runtime performance benchmarks for the plug-in version; no statistical test details beyond Mann–Whitney U test references

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software tool that addresses a genuine gap in the analysis of nucleic acid-containing complexes, particularly for predicted structures. The integration of interface detection, topology visualization, confidence metrics, and cryo-EM density zoning within a single ChimeraX plug-in is a sensible and practical contribution. However, the manuscript as presented has several weaknesses that prevent full assessment. The validation is largely anecdotal, with no systematic benchmarking against existing tools or quantitative assessment of the tool's accuracy. The large-scale analysis, while interesting, is presented at a descriptive level without clear hypotheses or deeper structural interpretation. The claim of novelty relative to existing tools such as DNAproDB and RNAproDB needs sharper articulation. The manuscript would benefit from clearer statements about what specific new capabilities ProNA3D offers beyond the sum of existing tools, and from more rigorous validation of the interface detection and clustering algorithms.

- **Who would be interested in the results, and why** Structural biologists studying protein–nucleic acid complexes, particularly those working with cryo-EM or AI-predicted structures, would find this tool useful. Researchers in RNA biology, gene regulation, and chromatin biology who need to analyze interaction interfaces in their complexes of interest would benefit. The large-scale connectivity analysis may interest bioinformaticians and computational biologists studying principles of molecular recognition. The tool's integration with ChimeraX makes it accessible to a broad structural biology community.

- **Major Strengths**
  1. Addresses a real need for tools that can handle both experimental and predicted nucleic acid-containing complexes in an integrated environment
  2. The combination of interface detection, topology plots, confidence metrics, and cryo-EM density zoning in a single plug-in is practical and potentially valuable
  3. The large-scale PDB analysis provides a useful resource and reveals interesting trends in interface connectivity
  4. The tool is freely available and open-source, supporting reproducibility and community adoption
  5. The application examples cover diverse complex types (RNA-only, protein–RNA, protein–DNA, cryo-EM) demonstrating versatility

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and benchmarking
- **Claim pointer** The authors claim ProNA3D provides a "unified platform for analyzing protein–nucleic acid and nucleic acid-only complexes" and that it "bridges the gap between structure prediction and functional interpretation"
- **Evidence pointer** Results sections for all four application examples; Methods section
- **Concern** The tool's performance is not systematically validated or benchmarked against existing tools. The four application examples are presented as demonstrations but lack quantitative assessment of the accuracy or reliability of the interface detection, sub-interface clustering, or topology generation. No comparison is made with DNAproDB, RNAproDB, or other existing tools for the same complexes. There is no assessment of sensitivity or specificity of interface detection, no comparison of detected interfaces with known interaction data, and no evaluation of how parameter choices (dHA, dC) affect results across different complex types beyond the single hammerhead ribozyme example.
- **Why it matters** Without systematic validation, users cannot assess whether ProNA3D's interface detection is reliable for their complexes of interest. The claim of providing a "unified platform" implies a level of robustness and accuracy that is not demonstrated. For a tool intended for community use, benchmarking against existing methods is essential to establish its value and to help users choose appropriate tools for their specific needs.
- **Resolution test** Provide a systematic benchmark comparing ProNA3D's interface detection and sub-interface clustering against existing tools (e.g., DNAproDB, RNAproDB, PLIP) on a diverse set of test cases with known or manually curated interfaces. Include quantitative metrics such as precision, recall, and F1-score for interface residue/nucleotide identification. Assess the impact of dHA and dC parameter choices across multiple complex types and provide guidance on parameter selection.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of large-scale analysis
- **Claim pointer** The authors claim "distinct interface connectivity trends" between nucleic acid-only and protein–nucleic acid interfaces, and that these differences are "statistically significant" (Mann–Whitney U test, Table S3)
- **Evidence pointer** Results section "Systematic analysis"; Figure 5; Tables S2, S3
- **Concern** The large-scale analysis is presented descriptively with limited statistical depth. While Mann–Whitney U tests are mentioned, the effect sizes, confidence intervals, and multiple testing corrections are not reported. The analysis does not account for potential confounding factors such as complex size, resolution, or structural class. The biological interpretation of the connectivity differences is superficial, and the claim that high-connectivity outliers "suggest" functional importance is speculative without functional validation or deeper structural analysis. The robustness analysis using different dHA/dC thresholds is mentioned but not shown in the main text.
- **Why it matters** The large-scale analysis is presented as a key contribution of the work. Without rigorous statistical treatment and consideration of confounders, the conclusions about connectivity differences between complex classes may not be reliable. The speculative interpretation of outliers as functionally important could mislead readers. For a study claiming to reveal "distinct trends," the statistical foundation must be solid.
- **Resolution test** Provide full statistical details including effect sizes, confidence intervals, and multiple testing corrections. Perform multivariate analysis to control for potential confounders. For the outlier analysis, provide structural context and, where possible, functional evidence or literature support for the proposed importance of specific high-connectivity nucleotides. Present the threshold robustness analysis in the main text or clearly summarize the findings.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and differentiation
- **Claim pointer** The authors state that "most current platforms are optimized for experimentally resolved structures, and their ability to analyze predicted complex models...remains limited" and that there is a "lack of unified workflows for mixed complexes"
- **Evidence pointer** Introduction; Table S1
- **Concern** The novelty of ProNA3D relative to existing tools is not clearly articulated. While the authors mention DNAproDB, RNAproDB, and other tools, the specific advantages of ProNA3D are not systematically compared. The claim that existing tools cannot handle predicted structures is not fully substantiated, as some tools may accept user-provided structures regardless of their origin. The unique combination of features (interface detection + topology + confidence metrics + cryo-EM zoning) is presented as the main novelty, but the value of this integration is not demonstrated beyond the individual examples.
- **Why it matters** For a new tool to be adopted, its advantages over existing options must be clear. If the individual features are available elsewhere, the integration alone may not justify the tool's existence. A clear statement of what ProNA3D offers that no other tool provides, with direct comparisons, is needed to establish its contribution to the field.
- **Resolution test** Provide a direct comparison table or figure showing ProNA3D's capabilities alongside those of existing tools (DNAproDB, RNAproDB, PLIP, etc.) for the same test cases. Clearly state which features are unique to ProNA3D and demonstrate the practical benefit of the integrated workflow with a concrete example where the integration provides insights that would not be obtainable by combining separate tools.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and limitations
- **Claim pointer** The authors claim ProNA3D "provides a unified approach for the analysis of protein and nucleic acid interactions" and supports "a wide range of downstream structural and functional studies"
- **Evidence pointer** Discussion section
- **Concern** The manuscript does not adequately address the limitations of the approach. The lack of support for modified nucleotides and amino acids is mentioned as a limitation, but other potential limitations are not discussed. These include: performance on very large complexes or assemblies, handling of symmetry or multimeric assemblies with many chains, computational efficiency for large-scale analyses, potential biases in the PDB dataset used for the large-scale analysis, and the generalizability of the connectivity findings to complexes not represented in the PDB. The authors also do not discuss how the tool handles structures with missing residues or nucleotides, or structures with multiple alternative conformations.
- **Why it matters** Users need to understand the scope and limitations of the tool to apply it appropriately. Overstating the tool's capabilities without acknowledging limitations could lead to inappropriate use and misinterpretation of results. A balanced discussion of limitations is essential for scientific credibility.
- **Resolution test** Add a dedicated limitations section discussing the tool's performance on different complex types, computational efficiency, handling of incomplete or ambiguous structures, and the representativeness of the PDB dataset. Provide guidance on when ProNA3D is and is not appropriate for use.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Interface detection algorithm
- **Evidence pointer** Methods section, Equation 1
- **Issue** The interface detection equation is presented without clear explanation of how the minimum distance criterion is applied in practice. The notation is ambiguous regarding whether the minimum is taken over all atom pairs or over specific atom types. The relationship between the interface definition and the sub-interface clustering algorithm is not fully explained.
- **Required correction** Clarify the notation in Equation 1 and provide a step-by-step description of the interface detection and sub-interface clustering algorithm. Include a pseudocode or flowchart if helpful.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Large-scale analysis dataset
- **Evidence pointer** Methods section "Dataset curation"
- **Issue** The dataset curation protocol is described but the exact version of the PDB used, the date of download, and the specific filtering criteria are not fully specified. The random selection of representatives from cluster–cluster interactions is mentioned but the random seed is not provided.
- **Required correction** Specify the PDB release date or version, provide the exact filtering criteria, and report the random seed used for representative selection to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Issue** The main text refers to Figure 5 for the large-scale connectivity analysis, but the figure is not described in sufficient detail in the text. The reader cannot assess the distributions without seeing the figure, and the text does not provide key summary statistics.
- **Required correction** Provide key summary statistics (medians, interquartile ranges) in the text for each interface class, and ensure the figure includes clear labels, legends, and statistical annotations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Software documentation
- **Affected element** Data availability
- **Evidence pointer** Data Availability section
- **Issue** The manuscript states the tool is available at a GitLab repository, but there is no mention of documentation, user guide, or example data. The installation requirements and dependencies are not described in the manuscript.
- **Required correction** Provide a brief description of the software documentation, installation instructions, and example data in the Data Availability section or supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Citation of related work
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction cites several tools but does not discuss recent developments in nucleic acid structure analysis tools comprehensively. Some relevant tools may be missing from the comparison.
- **Required correction** Ensure the comparison with existing tools is current and comprehensive. Add any missing relevant tools to Table S1 and discuss them in the introduction.

## Risk / unsupported claims
1. The claim that ProNA3D "identified a high-connectivity nucleotide with potential functional relevance" in the Fab–HIV-1 RNA complex is speculative. The functional relevance is inferred solely from connectivity without experimental validation or deeper structural analysis. This is presented as a finding but is only a hypothesis.
2. The claim that the large-scale analysis "revealed distinct interface connectivity trends" is supported by the data but the biological significance of these trends is not established. The interpretation that these trends reflect "specialized interaction modes" is speculative.
3. The claim that ProNA3D "bridges the gap between structure prediction and functional interpretation" is overstated. The tool provides structural analysis capabilities but does not directly connect to functional interpretation without additional experimental or computational analysis.
4. The statement that existing tools "are primarily tailored to experimentally resolved structures" is not fully supported. Some tools may accept predicted structures, and the authors do not provide evidence that existing tools fail on predicted models.
5. The claim that the cryo-EM density zoning feature "facilitates structure analysis" is demonstrated on one example but the general utility and limitations of this feature are not systematically assessed.
6. The performance metrics for the large-scale analysis (5 h 51 min for 10,806 complexes) are presented but no comparison with other tools or approaches is provided, making it difficult to assess the efficiency claim.