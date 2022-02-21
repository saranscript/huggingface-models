---
language: 
  - en
  
inference: false
license: apache-2.0
---
# Yuyuan-3.5B model (Medical)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
As we all know, the single direction language model based on decoder structure has strong generation ability, such as GPT model. 
The 3.5 billion parameter Yuyuan-3.5B large model, **using 50GB medical(pubmed) data, 32 A100 training for 7 days**, is the **largest open source GPT2 large model of medical.** 
Our model has nearly **90% accuracy in fact judgment in the medical field**.

We use the PPL(perplexity) output by Yuyuan-3.5B to realize fact judgment, and use the sentence pattern transformation from interrogative sentence to declarative sentence to realize medical question and answer. 
More possibilities are waiting for you to find out.

## Usage

### load model
```python 
from transformers import GPT2Tokenizer, GPT2Model
tokenizer = GPT2Tokenizer.from_pretrained('IDEA-CCNL/Yuyuan-3.5B')
model = GPT2Model.from_pretrained('IDEA-CCNL/Yuyuan-3.5B')
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```
### generation
```python
from transformers import pipeline, set_seed
set_seed(55)
generator = pipeline('text-generation', model='IDEA-CCNL/Yuyuan-3.5B')
generator("Diabetics should not eat", max_length=30, num_return_sequences=1)

```
## example
![avatar](https://huggingface.co/IDEA-CCNL/Yuyuan-3.5B/resolve/main/generation_example.jpg)

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
