## Protify: A Benchmarking Platform Revealing Task Dependence and Homology Leakage in Protein Language Model Evaluation


## Abstract

Protein Language Models (pLMs) have become essential tools for computational protein analysis, and the rapid proliferation of architectures, training objectives, and pretraining corpora has produced a diverse and expanding model landscape. Evaluation practices, however, remain fragmented: studies use different datasets, preprocessing pipelines, and reporting conventions, so results rarely transfer between publications. Here we introduce Protify, an open-source platform that standardizes pLM benchmarking across zero-shot, supervised, and transferlearning settings through a unified, low-code interface. Protify currently supports 35 pretrained models and 61 curated datasets and it is easy to add custom versions of each. Leveraging Protify's high throughput pipelines, we benchmarked 23 models on ProteinGym, discovering that DPLM3B is currently the top-performing self-supervised encoder. Another large-scale supervised evaluation across 32 diverse tasks, spanning enzyme classification, gene ontology annotation, protein-protein interaction, subcellular localization, and other functional properties, found that no single pLM dominated: 14 different models took the top score on at least one dataset, and the margins between the best and second-best models fell within run-to-run variability. On enzyme optimal pH prediction, a general-purpose probe pipeline matched or exceeded EpHod, a specialized model selected from 11,550 training runs, after 50 hyperparameter trials (R2 = 0.482 versus 0.425). Under a homology-controlled split of the same data, every pooled-embedding probe collapsed to near-zero R2, and only a transformer probe over full residue embeddings recovered appreciable signal (R2 = 0.248). Model rankings therefore depend as much on evaluation design as on the models themselves. Protify makes those design choices explicit, controlled, and replayable, and is freely available at https://github.com/Gleghorn-Lab/Protify.


## Competing Interest Statement

LH and JPG are co-founders of and have an equity stake in Synthyra, PBLLC.


## Footnotes

https://huggingface.co/collections/GleghornLab/protify-paper-6ae9f64088657c668a562853

https://github.com/Gleghorn-Lab/Protify


## Funder Information Declared

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area