## The Confessions of a Protein Language Model: Steering, Activations, and What Predicted Confidence Cannot Certify


## Abstract

Protein generate-and-screen pipelines use interventions and readouts to select candidates, but rarely test whether these track their intended targets. We audit published repetition steering, ESMFold confidence, and an activation readout. Steering preserves confidence at its operating point, but a fitted cliff follows at alpha_50 = 1.240x (sweep's own control: 64.0%). Direction matters at moderate matched-norm push, but not at saturation. Unsteered generator activations predict the confidence gate (ROC-AUC 0.786 +/- 0.004), supporting cost-aware, model-specific triage. We also replicate established length sensitivity, through which shortening can manufacture false nulls. Yet on composition- and length-matched design--scramble pairs, no balanced-accuracy interval excludes chance for experimental stability. Predicting the gate does not establish foldability. We should test what a readout measures before using it to select. Code and data: https://github.com/paninishah/plm-steering-audit


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://github.com/paninishah/plm-steering-audit

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area