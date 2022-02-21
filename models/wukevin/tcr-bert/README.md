# TCR transformer model

See our full [codebase](https://github.com/wukevin/tcr-bert) and our [preprint](https://www.biorxiv.org/content/10.1101/2021.11.18.469186v1) for more information.

This model is on:

- Masked language modeling (masked amino acid or MAA modeling)
- Classification across antigen labels from PIRD

If you are looking for a model trained only on MAA, please see our [other model](https://huggingface.co/wukevin/tcr-bert-mlm-only).

Example inputs:

* `C A S S P V T G G I Y G Y T F` (binds to NLVPMVATV CMV antigen)
* `C A T S G R A G V E Q F F` (binds to GILGFVFTL flu antigen)