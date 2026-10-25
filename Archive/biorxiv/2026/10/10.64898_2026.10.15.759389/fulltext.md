## DEEP: Extracting Latent Energetic Landscapes from Protein Structure Predictors


## Abstract

Modern protein structure predictors learn complex sequence-structure relationships, yet the extent to which their internal representations capture the energetic principles governing protein stability and conformational preferences remains unclear. Here, we introduce DEEP (Distogram Encoded Energetic Potential), a general framework that extracts effective statistical potentials directly from predicted residue-pair distance distributions, using the models own terminal distance state as an internal reference without training on experimental stability data. Applied to Boltz-2 (DEEP-Boltz) achieves a mean per-assay Spearman correlation of 0.720 across 64 ProteinGym stability assays, numerically outperforming all 97 published zero-shot methods in the matched comparison on level with the best performing predictors trained directly on experimental stability measurements. Beyond mutation effects, DEEP-Boltz accurately distinguishes native-like from non-native conformations across more than 180,000 Rosetta decoys. Applying DEEP to AlphaFold2 reveals nearly identical conformational discrimination but substantially weaker mutation-effect prediction, demonstrating that recognizing favorable conformations and capturing their energetic sensitivity to sequence changes are distinct properties of learned structural representations. Together, these findings establish that protein structure predictors encode accessible energetic information beyond their geometric predictions and that this information can be extracted. We release the framework and DEEP-Boltz as a freely available tool for extracting these latent energetic representations and for zero-shot prediction of mutation-induced protein stability changes.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

Updated method section and supplementary information

https://github.com/erdoslab-elte/DEEP-Boltz


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area