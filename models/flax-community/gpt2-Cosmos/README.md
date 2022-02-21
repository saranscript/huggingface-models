# Cosmos QA (gpt2) 
> This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/train-a-gpt2-model-for-contextual-common-sense-reasoning-using-the-cosmos-qa-dataset/7463), organized by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

## Team Members
-Rohan V Kashyap ([Rohan](https://huggingface.co/Rohan))
-Vivek V Kashyap ([Vivek](https://huggingface.co/Vivek))

## Dataset

[Cosmos QA: Machine Reading Comprehension with Contextual Commonsense Reasoning](https://huggingface.co/datasets/cosmos_qa).This dataset contains a set of 35,600 problems that require commonsense-based reading comprehension, formulated as multiple-choice questions.Understanding narratives requires reading between the lines, which in turn, requires interpreting the likely causes and effects of events, even when they are not mentioned explicitly.The questions focus on factual and literal understanding of the context paragraph, our dataset focuses on reading between the lines over a diverse collection of people's everyday narratives.


### Example

```json
{"Context":["It's a very humbling experience when you need someone
to dress you every morning, tie your shoes, and put your hair
up. Every menial task takes an unprecedented amount of effort.
It made me appreciate Dan even more. But anyway I shan't
dwell on this (I'm not dying after all) and not let it detract from
my lovely 5 days with my friends visiting from Jersey."],

"Question":["What's a possible reason the writer needed someone to
dress him every morning?"],

"Multiple Choice":["A: The writer doesn't like putting effort into these tasks.",
"B: The writer has a physical disability.",
"C: The writer is bad at doing his own hair.",
"D: None of the above choices."]
"link":"https://arxiv.org/pdf/1909.00277.pdf"
}
```

## How to use

```bash
# Installing requirements
pip install transformers
pip install datasets 
```

```python
from model_file import FlaxGPT2ForMultipleChoice
from datasets import Dataset
model_path="flax-community/gpt2-Cosmos"
model = FlaxGPT2ForMultipleChoice.from_pretrained(model_path,input_shape=(1,4,1))

dataset=Dataset.from_csv('./')

def preprocess(example):
    example['context&question']=example['context']+example['question']
    example['first_sentence']=[example['context&question'],example['context&question'],example['context&question'],example['context&question']]
    example['second_sentence']=example['answer0'],example['answer1'],example['answer2'],example['answer3']
    return example
    
dataset=dataset.map(preprocess)

def tokenize(examples):
    a=tokenizer(examples['first_sentence'],examples['second_sentence'],padding='max_length',truncation=True,max_length=256,return_tensors='jax')
    a['labels']=examples['label']
    return a
    
dataset=dataset.map(tokenize)

input_id=jnp.array(dataset['input_ids'])
att_mask=jnp.array(dataset['attention_mask'])

outputs=model(input_id,att_mask)

final_output=jnp.argmax(outputs,axis=-1)

print(f"the predction of the dataset : {final_output}")
```

```
The Correct answer:-Option 1 
```

## Preprocessing

The texts are tokenized using the GPT2 tokenizer.To feed the inputs of multiple choice we concatenated context and question as first input and all the 4 possible choices as the second input to our tokenizer.

## Evaluation

The following tables summarize the scores obtained by the **GPT2-CosmosQA**.The ones  marked as (^) are the baseline models.

|      Model      |  Dev Acc | Test Acc  | 
|:---------------:|:-----:|:-----:|
| BERT-FT Multiway^| 68.3.| 68.4  |
|  GPT-FT   ^    |  54.0 | 54.4. |
| GPT2-CosmosQA  | 60.3 | 59.7 | 

## Inference

This project was mainly  to test the  common sense understanding of the  GPT2-model.We finetuned on a Dataset known as CosmosQ requires reasoning beyond the exact text spans in the context.The above results shows that GPT2 model is doing better than most of the base line models given that  it only used to predict the next word in the pre-training objective.


## Credits
  Huge thanks to Huggingface 🤗 & Google Jax/Flax team for such a wonderful community week. Especially for providing such massive computing resource. Big thanks to [@patil-suraj](https://github.com/patil-suraj) & [@patrickvonplaten](https://github.com/patrickvonplaten) for mentoring during whole week.
