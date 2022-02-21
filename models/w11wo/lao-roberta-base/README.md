---
language: lo
tags:
  - lao-roberta-base
license: mit
datasets:
  - oscar-corpus/OSCAR-2109
---

## Lao RoBERTa Base

Lao RoBERTa Base is a masked language model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. It was trained on the [OSCAR-2109](https://huggingface.co/datasets/oscar-corpus/OSCAR-2109) dataset, specifically the `deduplicated_lo` subset. The model was trained from scratch and achieved an evaluation loss of 1.4556 and an evaluation perplexity of 4.287.

This model was trained using HuggingFace's PyTorch framework and the training script found [here](https://github.com/huggingface/transformers/blob/master/examples/pytorch/language-modeling/run_mlm.py). All training was done on a TPUv3-8, provided by the [TPU Research Cloud](https://sites.research.google/trc/about/) program. You can view the detailed training results in the [Training metrics](https://huggingface.co/w11wo/lao-roberta-base/tensorboard) tab, logged via Tensorboard.

## Model

| Model              | #params | Arch.   | Training/Validation data (text)      |
| ------------------ | ------- | ------- | ------------------------------------ |
| `lao-roberta-base` | 124M    | RoBERTa | OSCAR-2109 `deduplicated_lo` Dataset |

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 0.0002
- train_batch_size: 128
- eval_batch_size: 128
- seed: 42
- distributed_type: tpu
- num_devices: 8
- total_train_batch_size: 1024
- total_eval_batch_size: 1024
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 30.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
| :-----------: | :---: | :--: | :-------------: |
|    No log     |  1.0  | 216  |     5.8586      |
|    No log     |  2.0  | 432  |     5.5095      |
|     6.688     |  3.0  | 648  |     5.3976      |
|     6.688     |  4.0  | 864  |     5.3562      |
|    5.3629     |  5.0  | 1080 |     5.2912      |
|    5.3629     |  6.0  | 1296 |     5.2385      |
|     5.22      |  7.0  | 1512 |     5.1955      |
|     5.22      |  8.0  | 1728 |     5.1785      |
|     5.22      |  9.0  | 1944 |     5.1327      |
|    5.1248     | 10.0  | 2160 |     5.1243      |
|    5.1248     | 11.0  | 2376 |     5.0889      |
|    5.0591     | 12.0  | 2592 |     5.0732      |
|    5.0591     | 13.0  | 2808 |     5.0417      |
|    5.0094     | 14.0  | 3024 |     5.0388      |
|    5.0094     | 15.0  | 3240 |     4.9299      |
|    5.0094     | 16.0  | 3456 |     4.2991      |
|    4.7527     | 17.0  | 3672 |     3.6541      |
|    4.7527     | 18.0  | 3888 |     2.7826      |
|    3.4431     | 19.0  | 4104 |     2.2796      |
|    3.4431     | 20.0  | 4320 |     2.0213      |
|    2.2803     | 21.0  | 4536 |     1.8809      |
|    2.2803     | 22.0  | 4752 |     1.7615      |
|    2.2803     | 23.0  | 4968 |     1.6925      |
|    1.8601     | 24.0  | 5184 |     1.6205      |
|    1.8601     | 25.0  | 5400 |     1.5751      |
|    1.6697     | 26.0  | 5616 |     1.5391      |
|    1.6697     | 27.0  | 5832 |     1.5200      |
|    1.5655     | 28.0  | 6048 |     1.4866      |
|    1.5655     | 29.0  | 6264 |     1.4656      |
|    1.5655     | 30.0  | 6480 |     1.4627      |

## How to Use

### As Masked Language Model

```python
from transformers import pipeline

pretrained_name = "w11wo/lao-roberta-base"
prompt = "REPLACE WITH MASKED PROMPT"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask(prompt)
```

### Feature Extraction in PyTorch

```python
from transformers import RobertaModel, RobertaTokenizerFast

pretrained_name = "w11wo/lao-roberta-base"
model = RobertaModel.from_pretrained(pretrained_name)
tokenizer = RobertaTokenizerFast.from_pretrained(pretrained_name)

prompt = "ສະ​ບາຍ​ດີ​ຊາວ​ໂລກ."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer

Do consider the biases which came from pre-training datasets that may be carried over into the results of this model.

## Author

Lao RoBERTa Base was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google's TPU-RC.

## Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.9.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
