---
language: en
tags:
- tapas
license: apache-2.0
datasets:
- msr_sqa
---

# TAPAS mini model fine-tuned on Sequential Question Answering (SQA)

This model has 2 versions which can be used. The default version corresponds to the `tapas_sqa_inter_masklm_mini_reset` checkpoint of the [original Github repository](https://github.com/google-research/tapas).
This model was pre-trained on MLM and an additional step which the authors call intermediate pre-training, and then fine-tuned on [SQA](https://www.microsoft.com/en-us/download/details.aspx?id=54253). It uses relative position embeddings (i.e. resetting the position index at every cell of the table).

The other (non-default) version which can be used is: 
- `no_reset`, which corresponds to `tapas_sqa_inter_masklm_mini` (intermediate pre-training, absolute position embeddings). 

Disclaimer: The team releasing TAPAS did not write a model card for this model so this model card has been written by
the Hugging Face team and contributors.

## Results on SQA - Dev Accuracy

Size     |  Reset  | Dev Accuracy | Link
-------- | --------| -------- | ----
LARGE | noreset | 0.7223 | [tapas-large-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-large-finetuned-sqa/tree/no_reset)
LARGE | reset | 0.7289 | [tapas-large-finetuned-sqa](https://huggingface.co/google/tapas-large-finetuned-sqa/tree/main)
BASE | noreset | 0.6737 | [tapas-base-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-base-finetuned-sqa/tree/no_reset)
BASE | reset | 0.6874 | [tapas-base-finetuned-sqa](https://huggingface.co/google/tapas-base-finetuned-sqa/tree/main)
MEDIUM | noreset | 0.6464 | [tapas-medium-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-medium-finetuned-sqa/tree/no_reset)
MEDIUM | reset | 0.6561 | [tapas-medium-finetuned-sqa](https://huggingface.co/google/tapas-medium-finetuned-sqa/tree/main)
SMALL | noreset | 0.5876 | [tapas-small-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-small-finetuned-sqa/tree/no_reset)
SMALL | reset | 0.6155 | [tapas-small-finetuned-sqa](https://huggingface.co/google/tapas-small-finetuned-sqa/tree/main)
**MINI** | **noreset** | **0.4574** | [tapas-mini-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-mini-finetuned-sqa/tree/no_reset)
**MINI** | **reset** | **0.5148** | [tapas-mini-finetuned-sqa](https://huggingface.co/google/tapas-mini-finetuned-sqa/tree/main))
TINY | noreset | 0.2004 | [tapas-tiny-finetuned-sqa (absolute pos embeddings)](https://huggingface.co/google/tapas-tiny-finetuned-sqa/tree/no_reset)
TINY | reset | 0.2375 | [tapas-tiny-finetuned-sqa](https://huggingface.co/google/tapas-tiny-finetuned-sqa/tree/main)

## Model description

TAPAS is a BERT-like transformers model pretrained on a large corpus of English data from Wikipedia in a self-supervised fashion. 
This means it was pretrained on the raw tables and associated texts only, with no humans labelling them in any way (which is why it
can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it
was pretrained with two objectives:

- Masked language modeling (MLM): taking a (flattened) table and associated context, the model randomly masks 15% of the words in 
  the input, then runs the entire (partially masked) sequence through the model. The model then has to predict the masked words. 
  This is different from traditional recurrent neural networks (RNNs) that usually see the words one after the other, 
  or from autoregressive models like GPT which internally mask the future tokens. It allows the model to learn a bidirectional 
  representation of a table and associated text.
- Intermediate pre-training: to encourage numerical reasoning on tables, the authors additionally pre-trained the model by creating 
  a balanced dataset of millions of syntactically created training examples. Here, the model must predict (classify) whether a sentence 
  is supported or refuted by the contents of a table. The training examples are created based on synthetic as well as counterfactual statements.

This way, the model learns an inner representation of the English language used in tables and associated texts, which can then be used 
to extract features useful for downstream tasks such as answering questions about a table, or determining whether a sentence is entailed
or refuted by the contents of a table. Fine-tuning is done by adding a cell selection head on top of the pre-trained model, and then jointly
train this randomly initialized classification head with the base model on SQA. 


## Intended uses & limitations

You can use this model for answering questions related to a table in a conversational set-up.

For code examples, we refer to the documentation of TAPAS on the HuggingFace website. 


## Training procedure

### Preprocessing

The texts are lowercased and tokenized using WordPiece and a vocabulary size of 30,000. The inputs of the model are
then of the form:

```
[CLS] Question [SEP] Flattened table [SEP]
```

### Fine-tuning

The model was fine-tuned on 32 Cloud TPU v3 cores for 200,000 steps with maximum sequence length 512 and batch size of 128.
In this setup, fine-tuning takes around 20 hours. The optimizer used is Adam with a learning rate of 1.25e-5, and a warmup ratio 
of 0.2. An inductive bias is added such that the model only selects cells of the same column. This is reflected by the 
`select_one_column` parameter of `TapasConfig`. See also table 12 of the [original paper](https://arxiv.org/abs/2004.02349).


### BibTeX entry and citation info

```bibtex
@misc{herzig2020tapas,
      title={TAPAS: Weakly Supervised Table Parsing via Pre-training}, 
      author={Jonathan Herzig and PaweÃ…â€š Krzysztof Nowak and Thomas MÃƒÂ¼ller and Francesco Piccinno and Julian Martin Eisenschlos},
      year={2020},
      eprint={2004.02349},
      archivePrefix={arXiv},
      primaryClass={cs.IR}
}
```

```bibtex
@misc{eisenschlos2020understanding,
      title={Understanding tables with intermediate pre-training}, 
      author={Julian Martin Eisenschlos and Syrine Krichene and Thomas MÃƒÂ¼ller},
      year={2020},
      eprint={2010.00571},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

```bibtex
@InProceedings{iyyer2017search-based,
author = {Iyyer, Mohit and Yih, Scott Wen-tau and Chang, Ming-Wei},
title = {Search-based Neural Structured Learning for Sequential Question Answering},
booktitle = {Proceedings of the 55th Annual Meeting of the Association for Computational Linguistics},
year = {2017},
month = {July},
abstract = {Recent work in semantic parsing for question answering has focused on long and complicated questions, many of which would seem unnatural if asked in a normal conversation between two humans. In an effort to explore a conversational QA setting, we present a more realistic task: answering sequences of simple but inter-related questions. We collect a dataset of 6,066 question sequences that inquire about semi-structured tables from Wikipedia, with 17,553 question-answer pairs in total. To solve this sequential question answering task, we propose a novel dynamic neural semantic parsing framework trained using a weakly supervised reward-guided search. Our model effectively leverages the sequential context to outperform state-of-the-art QA systems that are designed to answer highly complex questions.},
publisher = {Association for Computational Linguistics},
url = {https://www.microsoft.com/en-us/research/publication/search-based-neural-structured-learning-sequential-question-answering/},
}
```