## Natural Don't Know Response Model

Fine-tuned on [Google's T5](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) using a combination of a dependency-rule based data and [Quora Question Pairs(QQP)](https://huggingface.co/nlp/viewer/?dataset=quora) dataset for **Don't Know Response Generation** task.

Additional information about this model:
- Paper : [Saying No is An Art: Contextualized Fallback Responses for
Unanswerable Dialogue Queries](https://arxiv.org/pdf/2012.01873.pdf)
- Github Repo: https://github.com/kaustubhdhole/natural-dont-know

#### How to use
```python
from transformers import T5ForConditionalGeneration, T5Tokenizer
model_name = "ashish-shrivastava/dont-know-response"
model = T5ForConditionalGeneration.from_pretrained(model_name)
tokenizer = T5Tokenizer.from_pretrained(model_name)

input = "Where can I find good Italian food ?"
input_ids = tokenizer.encode(input, return_tensors="pt")
outputs = model.generate(input_ids)
decoded_output = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(decoded_output) # I'm not sure where you can get good quality Italian food.

```

#### Hyperparameters

```
n_epochs = 2
base_LM_model = "T5-base"
max_seq_len = 256
learning_rate = 3e-4
adam_epsilon = 1e-8
train_batch_size = 6
``` 

#### BibTeX entry and citation info

```bibtex
@misc{shrivastava2020saying,
      title={Saying No is An Art: Contextualized Fallback Responses for Unanswerable Dialogue Queries}, 
      author={Ashish Shrivastava and Kaustubh Dhole and Abhinav Bhatt and Sharvani Raghunath},
      year={2020},
      eprint={2012.01873},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
