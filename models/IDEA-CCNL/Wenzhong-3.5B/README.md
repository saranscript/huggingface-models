---
language: 
  - zh
license: apache-2.0
---
# Wenzhong-3.5B model (chinese)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
As we all know, the single direction language model based on decoder structure has strong generation ability, such as GPT model. **The 3.5 billion parameter Wenzhong-3.5B large model, using 100G chinese common data, 32 A100 training for 28 hours,** is the largest open source **GPT2 large model of chinese**. **Our model performs well in Chinese continuation generation.**

## Usage

### load model
```python 
from transformers import GPT2Tokenizer, GPT2Model
tokenizer = GPT2Tokenizer.from_pretrained('IDEA-CCNL/Wenzhong-3.5B')
model = GPT2Model.from_pretrained('IDEA-CCNL/Wenzhong-3.5B')
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```
### generation
```python
from transformers import pipeline, set_seed
set_seed(55)
generator = pipeline('text-generation', model='IDEA-CCNL/Wenzhong-3.5B')
generator("北京位于", max_length=30, num_return_sequences=1)

```

## Citation
If you find the resource is useful, please cite the following website in your paper.
```
@misc{Fengshenbang-LM,
  title={Fengshenbang-LM},
  author={IDEA-CCNL},
  year={2021},
  howpublished={\url{https://github.com/IDEA-CCNL/Fengshenbang-LM}},
}
```