---
language: en
tags:
- bert
- cola
- glue
- torchdistill
license: apache-2.0
datasets:
- cola
metrics:
- matthew's correlation
---

`bert-large-uncased` fine-tuned on CoLA dataset, using [***torchdistill***](https://github.com/yoshitomo-matsubara/torchdistill) and [Google Colab](https://colab.research.google.com/github/yoshitomo-matsubara/torchdistill/blob/master/demo/glue_finetuning_and_submission.ipynb).  
The hyperparameters are the same as those in Hugging Face's example and/or the paper of BERT, and the training configuration (including hyperparameters) is available [here](https://github.com/yoshitomo-matsubara/torchdistill/blob/main/configs/sample/glue/cola/ce/bert_large_uncased.yaml).  
I submitted prediction files to [the GLUE leaderboard](https://gluebenchmark.com/leaderboard), and the overall GLUE score was **80.2**.
