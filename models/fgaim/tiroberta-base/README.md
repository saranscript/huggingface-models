---
language: ti
widget:
- text: "ዓቕሚ መንእሰይ ኤርትራ <mask> ተራእዩ"
---

# RoBERTa Pretrained for Tigrinya Language

We pretrain a RoBERTa base model for Tigrinya on a dataset of 40 million tokens trained for 40 epochs.

Contained in this repo is the original pretrained Flax model that was trained on a TPU v3.8 and it's corresponding PyTorch version.


## Hyperparameters

The hyperparameters corresponding to model sizes mentioned above are as follows:

| Model Size | L  | AH | HS  | FFN  | P    | Seq  |
|------------|----|----|-----|------|------|------|
| BASE       | 12 | 12 | 768 | 3072 | 125M | 512  |

(L = number of layers; AH = number of attention heads; HS = hidden size; FFN = feedforward network dimension; P = number of parameters; Seq = maximum sequence length.)
