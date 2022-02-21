---
language: ti
widget:
- text: "ዓቕሚ መንእሰይ ኤርትራ [MASK] ተራእዩ"
---

# Pre-trained ELECTRA small for Tigrinya Language

We pre-train ELECTRA small on the [TLMD](https://zenodo.org/record/5139094) dataset, with over 40 million tokens.

Contained are trained Flax and PyTorch models.


## Hyperparameters

The hyperparameters corresponding to model sizes mentioned above are as follows:

| Model Size | L  | AH | HS  | FFN  | P    | Seq  |
|------------|----|----|-----|------|------|------|
| SMALL      | 12 | 4  | 256 | 1024 | 14M  | 512  |

(L = number of layers; AH = number of attention heads; HS = hidden size; FFN = feedforward network dimension; P = number of parameters; Seq = maximum sequence length.)
