---
language: en
license: mit
---

🦔 HEDGEhog 🦔: BERT-based multi-class uncertainty cues recognition
====================================================================

# Description
TBD

# Training Data
HEDGEhog is trained and evaluated on the [Szeged Uncertainty Corpus](https://rgai.inf.u-szeged.hu/node/160) (Szarvas et al. 2012<sup>1</sup>). The original sentence-level XML version of this dataset is available [here](https://rgai.inf.u-szeged.hu/node/160).

The token-level version that was used for the training can be downloaded from [here](https://1drv.ms/u/s!AvPkt_QxBozXk7BiazucDqZkVxLo6g?e=IisuM6) in a form of pickled pandas DataFrame's. You can download either the split sets (```train.pkl``` 137MB, ```test.pkl``` 17MB, ```dev.pkl``` 17MB) or the full dataset (```szeged_fixed.pkl``` 172MB).

Each row in the df contains a token, its features (these are not relevant for HEDGEhog; they were used to train the baseline CRF model, see [here](https://github.com/vanboefer/uncertainty_crf)), its sentence ID, and its label. The labels refer to different types of semantic uncertainty (Szarvas et al. 2012) -

- **E**pistemic: the proposition is possible, but its truth-value cannot be decided at the moment. Example: *She **may** be already asleep.*
- **I**nvestigation: the proposition is in the process of having its truth-value determined. Example: *She **examined** the role of NF-kappaB in protein activation.*
- **D**oxatic: the proposition expresses beliefs and hypotheses, which may be known as true or false by others. Example: *She **believes** that the Earth is flat*
- Co**N**dition: the proposition is true or false based on the truth-value of another proposition. Example: ***If** she gets the job, she will move to Utrecht.*
- **C**ertain: the token is not an uncertainty cue.


# Training Procedure
TBD

# Evaluation Results
class | precision | recall | F1-score | support
---|---|---|---|---
Epistemic | 0.90 | 0.85 | 0.88 | 624
Doxatic | 0.88 | 0.92 | 0.90 | 142
Investigation | 0.83 | 0.86 | 0.84 | 111
Condition | 0.85 | 0.87 | 0.86 | 86
Certain | 1.00 | 1.00 | 1.00 | 104,751
**macro average** | **0.89** | **0.90** | **0.89** | 105,714

# References
<sup>1</sup> Szarvas, G., Vincze, V., Farkas, R., Móra, G., & Gurevych, I. (2012). Cross-genre and cross-domain detection of semantic uncertainty. *Computational Linguistics, 38*(2), 335-367.