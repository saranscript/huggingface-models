---
language:
  - sv
  - multilingual
tags:
  - question-answering
  - xlm-roberta
  - roberta
  - squad
metrics:
  - squad_v2
widget:
  - text: Vilket datum är den svenska nationaldagen?
    context: >-
      Sveriges nationaldag och svenska flaggans dag firas den 6 juni varje år
      och är en helgdag i Sverige. Tidigare firades 6 juni enbart som "svenska
      flaggans dag" och det var först 1983 som dagen även fick status som
      nationaldag.
  - text: Vad innebär helgdag i Sverige?
    context: >-
      Sveriges nationaldag och svenska flaggans dag firas den 6 juni varje år
      och är en helgdag i Sverige. Tidigare firades 6 juni enbart som "svenska
      flaggans dag" och det var först 1983 som dagen även fick status som
      nationaldag.
  - text: Vilket år tillkom Sveriges nationaldag?
    context: >-
      Sveriges nationaldag och svenska flaggans dag firas den 6 juni varje år
      och är en helgdag i Sverige. Tidigare firades 6 juni enbart som "svenska
      flaggans dag" och det var först 1983 som dagen även fick status som
      nationaldag.
model-index:
  - name: "XLM-RoBERTa large for QA (SwedishQA - \U0001F1F8\U0001F1EA)"
    results:
      - task:
          type: question-answering
          name: Question Answering
        dataset:
          type: swedish_qa
          name: SwedishQA
          args: sv
        metrics:
          - type: squad_v2
            value: 87.97
            name: Eval F1
            args: max_order
          - type: squad_v2
            value: 78.79
            name: Eval Exact
            args: max_order

---

# XLM-RoBERTa large for QA (SwedishQA - 🇸🇪) 

This model is a fine-tuned version of [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) on the [SwedishQA](https://github.com/Vottivott/building-a-swedish-qa-model) dataset.



## Hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 2.0
- mixed_precision_training: Native AMP


## Performance

Evaluation results on the eval set with the official [eval script](https://worksheets.codalab.org/rest/bundles/0x6b567e1cf2e041ec80d7098f031c5c9e/contents/blob/).

### Evalset

```text
"exact": 78.79554655870446,
"f1": 87.97339064752278,
"total": 5928
```


## Usage

```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

model_name_or_path = "m3hrdadfi/xlmr-large-qa-sv"
nlp = pipeline('question-answering', model=model_name_or_path, tokenizer=model_name_or_path)

context = """
Sveriges nationaldag och svenska flaggans dag firas den 6 juni 
varje år och är en helgdag i Sverige. 
Tidigare firades 6 juni enbart som "svenska flaggans dag" och det 
var först 1983 som dagen även fick status som nationaldag. 
"""

questions = [
    "Vilket datum är den svenska nationaldagen?",
    "Vad innebär helgdag i Sverige?",
    "Vilket år tillkom Sveriges nationaldag?"
]
kwargs = {}

for question in questions:
    r = nlp(question=question, context=context, **kwargs)
    answer = " ".join([token.strip() for token in r["answer"].strip().split() if token.strip()])
    print(f"{question} {answer}")
```

**Output**

```text
Vilket datum är den svenska nationaldagen? 6 juni
Vad innebär helgdag i Sverige? svenska flaggans dag
Vilket år tillkom Sveriges nationaldag? 1983
```

## Authors
- [Mehrdad Farahani](https://github.com/m3hrdadfi)

### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
