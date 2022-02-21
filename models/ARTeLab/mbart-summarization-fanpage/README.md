---
tags:
- summarization
language:
- it
metrics:
- rouge
model-index:
- name: summarization_mbart_fanpage4epoch
  results: []
datasets:
- ARTeLab/fanpage
---

# mbart-summarization-fanpage

This model is a fine-tuned version of [facebook/mbart-large-cc25](https://huggingface.co/facebook/mbart-large-cc25) on Fanpage dataset for Abstractive Summarization.

It achieves the following results:
- Loss: 2.1833
- Rouge1: 36.5027
- Rouge2: 17.4428
- Rougel: 26.1734
- Rougelsum: 30.2636
- Gen Len: 75.2413

## Usage 

```python
from transformers import MBartTokenizer, MBartForConditionalGeneration
tokenizer = MBartTokenizer.from_pretrained("ARTeLab/mbart-summarization-fanpage")
model = MBartForConditionalGeneration.from_pretrained("ARTeLab/mbart-summarization-fanpage")
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