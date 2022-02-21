---
language: en
tags:
- bert
- qnli
- glue
- kd
- torchdistill
license: apache-2.0
datasets:
- qnli
metrics:
- accuracy
---

`bert-base-uncased` fine-tuned on QNLI dataset, using fine-tuned `bert-large-uncased` as a teacher model, [***torchdistill***](https://github.com/yoshitomo-matsubara/torchdistill) and [Google Colab](https://colab.research.google.com/github/yoshitomo-matsubara/torchdistill/blob/master/demo/glue_kd_and_submission.ipynb) for knowledge distillation.  
The training configuration (including hyperparameters) is available [here](https://github.com/yoshitomo-matsubara/torchdistill/blob/main/configs/sample/glue/qnli/kd/bert_base_uncased_from_bert_large_uncased.yaml).  
I submitted prediction files to [the GLUE leaderboard](https://gluebenchmark.com/leaderboard), and the overall GLUE score was **78.9**.
