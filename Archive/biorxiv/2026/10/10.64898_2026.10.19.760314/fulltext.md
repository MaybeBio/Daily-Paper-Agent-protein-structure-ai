## Sequence-only antigen context improves modeling of antibody hypervariable regions


## Abstract

The complementarity-determining regions (CDRs) of antibodies govern antigen specificity; consequently, CDR design should be performed conditional on the target antigen. Most published approaches depend on the availability of the antigen's three-dimensional (3D) structure, which is often difficult to obtain experimentally. In contrast, sequence-only models circumvent this requirement but are typically trained on antibodies without incorporating antigen context; exposure to antigen sequences alone does not necessarily entail learning the underlying interaction determinants. Here, we introduce LangAAI, a masked language model that conditions exclusively on antibody and antigen primary sequences and therefore does not require 3D structures, docking poses, or epitope annotations. To assess whether the model exhibits genuine antigen conditioning, we replace the cognate antigen with a non-binding decoy. Whereas antigen-agnostic models are largely insensitive to this substitution, LangAAI shows a marked reduction in sequence recovery that is specifically concentrated in the hypervariable CDR3 loop. Across benchmarks, LangAAI improves amino-acid recovery relative to existing antibody language models, matches the performance of structure-based methods when evaluated under their respective protocols, and ranks experimentally measured variants by affinity comparably to inverse-folding models that use backbone coordinates. Collectively, these results support LangAAI as a structure-independent approach for antigen-aware antibody optimization, enabling prioritization of candidate variants for targets lacking solved antigen-antibody complexes.


## Competing Interest Statement

The authors have declared no competing interest.

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area