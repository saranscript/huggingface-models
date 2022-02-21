---
tags:
- summarization
language:
- it
metrics:
- rouge
model-index:
- name: summarization_fanpage128
  results: []
datasets:
- ARTeLab/fanpage
---

# summarization_fanpage128

This model is a fine-tuned version of [gsarti/it5-base](https://huggingface.co/gsarti/it5-base) on Fanpage dataset for Abstractive Summarization.

It achieves the following results:
- Loss: 1.5348
- Rouge1: 34.1882
- Rouge2: 15.7866
- Rougel: 25.141
- Rougelsum: 28.4882
- Gen Len: 69.3041

## Usage 

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
tokenizer = T5Tokenizer.from_pretrained("ARTeLab/it5-summarization-fanpage-128")
model = T5ForConditionalGeneration.from_pretrained("ARTeLab/it5-summarization-fanpage-128")
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 3
- eval_batch_size: 3
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4.0

### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3