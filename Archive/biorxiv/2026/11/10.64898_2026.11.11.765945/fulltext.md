## DynamicsPLM: A Dynamics-Enriched Small Protein Language Model for Protein Variant Effect Prediction


## Abstract

Predicting how mutations impact protein function and stability remains a key challenge in computational biology. Current state-of-the-art protein language models (PLMs) primarily scale parameter size on sequence corpora to capture evolutionary constraints but remain blind to the explicit physical dynamics of folded proteins. Conversely, models trained strictly on physical dynamics neglect critical evolutionary sequence statistics. In this paper, we bridge this gap by introducing DynamicsPLM, a highly parameter-efficient 35-million-parameter model that unifies evolutionary and biophysical representation learning. Utilizing a second-stage, multi-task continual pretraining strategy on over 60,000 proteins, we enrich a foundational sequence encoder with explicit residue-level and pairwise molecular dynamics heads while preserving its original evolutionary knowledge. At inference, DynamicsPLM computes zero-shot mutation effects from sequence alone by balancing an evolutionary plausibility score against a structural dynamics disruption score. Across the massive ProteinGym benchmark and natural variants of the Tsuboyama folding stability dataset, DynamicsPLM achieves state-of-the-art accuracy among all models under 100M parameters, and matches or outperforms several billion-scale sequence-based models of its size. Our findings demonstrate that explicit structural-dynamics supervision provides a parameter-efficient alternative to raw scale. Availability: All codes including data preparation scripts, training and validation recipes, and experimental configurations for LoMuS are available at: https://github.com/kabir-ai2bio-lab/DynamicsPLM.


## Competing Interest Statement

The authors have declared no competing interest.

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area