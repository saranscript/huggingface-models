---
license: mit
tags:
- generated_from_trainer
datasets:
- ju-bezdek/conll2003-SK-NER
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: outputs
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: ju-bezdek/conll2003-SK-NER
      type: ju-bezdek/conll2003-SK-NER
      args: conll2003-SK-NER
    metrics:
    - name: Precision
      type: precision
      value: 0.8189727994593682
    - name: Recall
      type: recall
      value: 0.8389581169955002
    - name: F1
      type: f1
      value: 0.8288450029922203
    - name: Accuracy
      type: accuracy
      value: 0.9526157920337243
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# outputs

This model is a fine-tuned version of [gerulata/slovakbert](https://huggingface.co/gerulata/slovakbert) on the [ju-bezdek/conll2003-SK-NER](https://huggingface.co/datasets/ju-bezdek/conll2003-SK-NER) dataset.
It achieves the following results on the evaluation (validation) set:
- Loss: 0.1752
- Precision: 0.8190
- Recall: 0.8390
- F1: 0.8288
- Accuracy: 0.9526

## Model description

More information needed

## Code example

```python:
from transformers import pipeline, AutoModel, AutoTokenizer
from spacy import displacy
import os


model_path="ju-bezdek/slovakbert-conll2003-sk-ner"

aggregation_strategy="max"
ner_pipeline = pipeline(task='ner', model=model_path, aggregation_strategy=aggregation_strategy)

input_sentence= "Ruský premiér Viktor Černomyrdin v piatok povedal, že prezident Boris Jeľcin , ktorý je na dovolenke mimo Moskvy , podporil mierový plán šéfa bezpečnosti Alexandra Lebedu pre Čečensko, uviedla tlačová agentúra Interfax"
ner_ents = ner_pipeline(input_sentence)
print(ner_ents)

ent_group_labels = [ner_pipeline.model.config.id2label[i][2:] for i in ner_pipeline.model.config.id2label if i>0]

options = {"ents":ent_group_labels}

dicplacy_ents = [{"start":ent["start"], "end":ent["end"], "label":ent["entity_group"]} for ent in ner_ents]
displacy.render({"text":input_sentence, "ents":dicplacy_ents}, style="ent", options=options, jupyter=True, manual=True)
```

### Result: 
<div>
             <span class="tex2jax_ignore"><div class="entities" style="line-height: 2.5; direction: ltr">
       <mark class="entity" style="background: #ddd; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Ruský
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">MISC</span>
       </mark>
        premiér 
       <mark class="entity" style="background: #ddd; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Viktor Černomyrdin
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">PER</span>
       </mark>
        v piatok povedal, že prezident 
       <mark class="entity" style="background: #ddd; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Boris Jeľcin,
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">PER</span>
       </mark>
        , ktorý je na dovolenke mimo 
       <mark class="entity" style="background: #ff9561; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Moskvy
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">LOC</span>
       </mark>
        , podporil mierový plán šéfa bezpečnosti 
       <mark class="entity" style="background: #ddd; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Alexandra Lebedu
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">PER</span>
       </mark>
        pre 
       <mark class="entity" style="background: #ff9561; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Čečensko,
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">LOC</span>
       </mark>
        uviedla tlačová agentúra 
       <mark class="entity" style="background: #7aecec; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
           Interfax
           <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">ORG</span>
       </mark>
       </div></span>
       </div>




## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.3237        | 1.0   | 878   | 0.2541          | 0.7125    | 0.8059 | 0.7563 | 0.9283   |
| 0.1663        | 2.0   | 1756  | 0.2370          | 0.7775    | 0.8090 | 0.7929 | 0.9394   |
| 0.1251        | 3.0   | 2634  | 0.2289          | 0.7732    | 0.8029 | 0.7878 | 0.9385   |
| 0.0984        | 4.0   | 3512  | 0.2818          | 0.7294    | 0.8189 | 0.7715 | 0.9294   |
| 0.0808        | 5.0   | 4390  | 0.3138          | 0.7615    | 0.7900 | 0.7755 | 0.9326   |
| 0.0578        | 6.0   | 5268  | 0.3072          | 0.7548    | 0.8222 | 0.7871 | 0.9370   |
| 0.0481        | 7.0   | 6146  | 0.2778          | 0.7897    | 0.8156 | 0.8025 | 0.9408   |
| 0.0414        | 8.0   | 7024  | 0.3336          | 0.7695    | 0.8201 | 0.7940 | 0.9389   |
| 0.0268        | 9.0   | 7902  | 0.3294          | 0.7868    | 0.8140 | 0.8002 | 0.9409   |
| 0.0204        | 10.0  | 8780  | 0.3693          | 0.7657    | 0.8239 | 0.7938 | 0.9376   |
| 0.016         | 11.0  | 9658  | 0.3816          | 0.7932    | 0.8242 | 0.8084 | 0.9425   |
| 0.0108        | 12.0  | 10536 | 0.3607          | 0.7929    | 0.8256 | 0.8089 | 0.9431   |
| 0.0078        | 13.0  | 11414 | 0.3980          | 0.7915    | 0.8240 | 0.8074 | 0.9423   |
| 0.0062        | 14.0  | 12292 | 0.4096          | 0.7995    | 0.8247 | 0.8119 | 0.9436   |
| 0.0035        | 15.0  | 13170 | 0.4177          | 0.8006    | 0.8251 | 0.8127 | 0.9438   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.1+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
