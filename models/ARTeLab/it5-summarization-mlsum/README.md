---
tags:
- summarization
language:
- it
metrics:
- rouge
model-index:
- name: summarization_mlsum
  results: []
datasets:
- ARTeLab/mlsum-it
---

# summarization_mlsum

This model is a fine-tuned version of [gsarti/it5-base](https://huggingface.co/gsarti/it5-base) on MLSum-it for Abstractive Summarization.

It achieves the following results:
- Loss: 2.0190
- Rouge1: 19.3739
- Rouge2: 5.9753
- Rougel: 16.691
- Rougelsum: 16.7862
- Gen Len: 32.5268

## Usage 
```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
tokenizer = T5Tokenizer.from_pretrained("ARTeLab/it5-summarization-mlsum")
model = T5ForConditionalGeneration.from_pretrained("ARTeLab/it5-summarization-mlsum")
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 6
- eval_batch_size: 6
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4.0

### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3