---
language: en
tags:
- exbert
license: apache-2.0
datasets:
- wikipedia
- quoref
- docred
- fever
- gap
- winograd_wsc
- winogender
- glue
---

# CorefRoBERTa base model 

Pretrained model on English language using Masked Language Modeling (MLM) and Mention Reference Prediction (MRP) objectives. It was introduced in
[this paper](https://arxiv.org/abs/2004.06870) and first released in
[this repository](https://github.com/thunlp/CorefBERT). 

Disclaimer: The team releasing CorefRoBERTa did not write a model card for this model so this model card has been written by me.

## Model description

CorefRoBERTa is a transformers model pretrained on a large corpus of English data in a self-supervised fashion. This means it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of
publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it was pretrained with two objectives:

- Masked language modeling (MLM): taking a sentence, the model randomly masks 15% of the words in the input then run
  the entire masked sentence through the model and has to predict the masked words. This is different from traditional
  recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like
  GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the
  sentence.
- Mention reference prediction (MRP): this is a novel training task which is proposed to enhance coreferential reasoning ability. MRP utilizes the
mention reference masking strategy to mask one of the repeated mentions and then employs a copybased training objective to predict the masked tokens by copying from other tokens in the sequence.

This way, the model learns an inner representation of the English language that can then be used to extract features useful for downstream tasks, especially those that involve coreference resolution. If you have a dataset of labeled sentences for instance, you can train a standard classifier using the features produced by the CorefRoBERTa model as inputs.


### BibTeX entry and citation info

```bibtex
@misc{ye2020coreferential,
      title={Coreferential Reasoning Learning for Language Representation}, 
      author={Deming Ye and Yankai Lin and Jiaju Du and Zhenghao Liu and Peng Li and Maosong Sun and Zhiyuan Liu},
      year={2020},
      eprint={2004.06870},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```


