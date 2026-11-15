## Binary Patterning as a Probe of Protein Language Model Representations


## Abstract

Do protein language models (pLMs) encode the physical rules that govern protein folding? The four-helix bundle provides a classic test case because binary patterning, the ordered placement of polar and nonpolar residues along an amphipathic α-helix, is sufficient to generate folded proteins with high probability. Here, we ask whether ESM2 captures the sequence grammar underlying this design strategy. Libraries of synthetic sequences constrained only by binary patterning were predicted by ESMFold to form four-helix bundles. Predicted helicity, compactness, and topological diversity changed with sequence length in the same direction as experimentally characterized libraries, although the model did not distinguish successful from unsuccessful individual designs. Principal component analysis of ESM2 embeddings revealed representations of hydrophobic patterning, helix-loop boundaries, and heptad register. Extending the analysis to all 128 heptad binary patterns produced a jellyfish-shaped manifold in which hydrophobic composition formed the dominant axis, while paired components encoded pattern phase. Manifold geometry depended on amino-acid chemistry, repeat number, and linker sequence, and collapsed when amino acids were assigned to arbitrary categories. ESM2 therefore combines general repeat recognition with protein-specific physicochemical information. More broadly, synthetic sequence libraries provide experimentally grounded probes of protein language model representations and their relationship to protein biophysics.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://github.com/Dylanklein1929/binpat_esm2_analysis


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats