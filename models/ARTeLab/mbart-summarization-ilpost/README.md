---
tags:
- summarization
language:
- it
metrics:
- rouge
model-index:
- name: summarization_mbart_ilpost
  results: []
datasets:
- ARTeLab/ilpost
---

# mbart_summarization_ilpost

This model is a fine-tuned version of [facebook/mbart-large-cc25](https://huggingface.co/facebook/mbart-large-cc25) on IlPost dataset for Abstractive Summarization.

It achieves the following results:
- Loss: 2.3640
- Rouge1: 38.9101
- Rouge2: 21.384
- Rougel: 32.0517
- Rougelsum: 35.0743
- Gen Len: 39.8843

## Usage 

```python
from transformers import MBartTokenizer, MBartForConditionalGeneration
tokenizer = MBartTokenizer.from_pretrained("ARTeLab/mbart-summarization-ilpost")
model = MBartForConditionalGeneration.from_pretrained("ARTeLab/mbart-summarization-ilpost")
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4.0

### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3