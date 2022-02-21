`LOREN` is an interpretable fact verification model trained on [FEVER](https://fever.ai), which aims to predict the veracity of a textual claim against a trustworthy knowledge source such as Wikipedia. 
`LOREN` also decomposes the verification and makes accurate and faithful phrase-level veracity predictions without any phrasal veracity supervision.

This repo hosts the following pre-trained models for `LOREN`:
- `fact_checking/`: the verification models based on BERT (large) and RoBERTa (large), respectively.
- `mrc_seq2seq/`: the generative machine reading comprehension model based on BART (base).
- `evidence_retrieval/`: the evidence sentence ranking models, which are copied directly from [KGAT](https://github.com/thunlp/KernelGAT).

More technical details can be found at [this GitHub Repo](https://github.com/jiangjiechen/LOREN).

Please check out our AAAI 2022 paper for more details: "[LOREN: Logic-Regularized Reasoning for Interpretable Fact Verification](https://arxiv.org/abs/2012.13577)".