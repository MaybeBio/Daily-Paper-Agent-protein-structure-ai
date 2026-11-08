## A protein language model for domain, functional site, and variant effect prediction


## Abstract

Protein sequence databases are growing far faster than experimentally curated annotations, limiting functional interpretation of newly identified proteins and coding variants. We developed PALM, a protein annotation language model that jointly predicts domain and functional-site occurrence, while preserving overlapping and nested annotations through a soft-target objective. PALM integrates ESM2 with low-rank adaptation (LoRA), learned layer aggregation, and a bidirectional long short-term memory (BiLSTM) encoder. PALM was trained on ~15 million InterPro-annotated UniRef50 sequences spanning 17,951 domain and 1,383 site classes. Across 2.3 million held-out proteins, PALM achieved domain- and site-occurrence F1 scores of 0.941 and 0.877, respectively, and retained substantial performance in proteins with <20% sequence identity to the training and validation data. PALM also substantially outperformed ESM3 annotation baseline. Without training on variant-pathogenicity labels, PALM embedding disruption distinguished 151,823 ClinVar missense variants more accurately than ESM2 embedding disruption (AUROC 0.835 versus 0.710), and combining PALM embedding disruption with the ESM2 likelihood-ratio signal reached an AUROC of 0.877. The same combined zero-shot score outperformed AlphaMissense on a benchmark dataset on 128,161 missense variants, that were derived from literature but not present in ClinVar database. At the protein level, PALM embeddings showed stronger CATH-Gene3D superfamily organization than frozen ESM2 and ESM3 embeddings, and improved prediction of experimental activation and repression effects when combined with ESM2. In a downstream case study, we demonstrated the ability to use PALM-derived embedding as proxy of deep mutational scanning (DMS), showcasing the broad application of PALM. Together, PALM converts curated residue-level knowledge into transferable and mechanistically interpretable representations that connect protein sequence, function, and variant consequence.


## Competing Interest Statement

The authors have declared no competing interest.


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area