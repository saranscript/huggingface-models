```python
from transformers import PreTrainedTokenizerFast, BartForConditionalGeneration

model = BartForConditionalGeneration.from_pretrained('honeyd3wy/kobart-titlenaming-v0.1')
tokenizer = PreTrainedTokenizerFast.from_pretrained('gogamza/kobart-base-v2')
```