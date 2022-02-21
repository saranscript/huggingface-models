---
language: it
tags:
- text-classification
- pytorch
- tensorflow
datasets:
- multi_nli
- glue
license: mit
pipeline_tag: zero-shot-classification
widget:
- text: "La seconda guerra mondiale vide contrapporsi, tra il 1939 e il 1945, le cosiddette potenze dell'Asse e gli Alleati che, come già accaduto ai belligeranti della prima guerra mondiale, si combatterono su gran parte del pianeta; il conflitto ebbe inizio il 1º settembre 1939 con l'attacco della Germania nazista alla Polonia e terminò, nel teatro europeo, l'8 maggio 1945 con la resa tedesca e, in quello asiatico, il successivo 2 settembre con la resa dell'Impero giapponese dopo i bombardamenti atomici di Hiroshima e Nagasaki."
  candidate_labels: "guerra, storia, moda, cibo"
  multi_class: true
---

# XLM-roBERTa-large-it-mnli

## Version 0.1
|                                                                                  | matched-it acc | mismatched-it acc |
| -------------------------------------------------------------------------------- |----------------|-------------------| 
| XLM-roBERTa-large-it-mnli     | 84.75          | 85.39             |

## Model Description
This model takes [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) and fine-tunes it on a subset of NLI data taken from a automatically translated version of the MNLI corpus. It is intended to be used for zero-shot text classification, such as with the Hugging Face [ZeroShotClassificationPipeline](https://huggingface.co/transformers/master/main_classes/pipelines.html#transformers.ZeroShotClassificationPipeline).
## Intended Usage
This model is intended to be used for zero-shot text classification of italian texts.
Since the base model was pre-trained trained on 100 different languages, the
model has shown some effectiveness in languages beyond those listed above as
well. See the full list of pre-trained languages in appendix A of the
[XLM Roberata paper](https://arxiv.org/abs/1911.02116)
For English-only classification, it is recommended to use
[bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli) or
[a distilled bart MNLI model](https://huggingface.co/models?filter=pipeline_tag%3Azero-shot-classification&search=valhalla).
#### With the zero-shot classification pipeline
The model can be loaded with the `zero-shot-classification` pipeline like so:
```python
from transformers import pipeline
classifier = pipeline("zero-shot-classification",
                      model="Jiva/xlm-roberta-large-it-mnli", device=0, use_fast=True, multi_label=True)              
```
You can then classify in any of the above languages. You can even pass the labels in one language and the sequence to
classify in another:
```python
# we will classify the following wikipedia entry about Sardinia"
sequence_to_classify = "La Sardegna è una regione italiana a statuto speciale di 1 592 730 abitanti con capoluogo Cagliari, la cui denominazione bilingue utilizzata nella comunicazione ufficiale è Regione Autonoma della Sardegna / Regione Autònoma de Sardigna."
# we can specify candidate labels in Italian:
candidate_labels = ["geografia", "politica", "macchine", "cibo", "moda"]
classifier(sequence_to_classify, candidate_labels)
# {'labels': ['geografia', 'moda', 'politica', 'macchine', 'cibo'],
# 'scores': [0.38871392607688904, 0.22633370757102966, 0.19398456811904907, 0.13735772669315338, 0.13708525896072388]}
```
The default hypothesis template is the English, `This text is {}`. With this model better results are achieving when providing a translated template:
```python
sequence_to_classify = "La Sardegna è una regione italiana a statuto speciale di 1 592 730 abitanti con capoluogo Cagliari, la cui denominazione bilingue utilizzata nella comunicazione ufficiale è Regione Autonoma della Sardegna / Regione Autònoma de Sardigna."
candidate_labels = ["geografia", "politica", "macchine", "cibo", "moda"]
hypothesis_template = "si parla di {}"
# classifier(sequence_to_classify, candidate_labels, hypothesis_template=hypothesis_template)
# 'scores': [0.6068345904350281, 0.34715887904167175, 0.32433947920799255, 0.3068877160549164, 0.18744681775569916]}
```
#### With manual PyTorch
```python
# pose sequence as a NLI premise and label as a hypothesis
from transformers import AutoModelForSequenceClassification, AutoTokenizer
nli_model = AutoModelForSequenceClassification.from_pretrained('Jiva/xlm-roberta-large-it-mnli')
tokenizer = AutoTokenizer.from_pretrained('Jiva/xlm-roberta-large-it-mnli')
premise = sequence
hypothesis = f'si parla di {}.'
# run through model pre-trained on MNLI
x = tokenizer.encode(premise, hypothesis, return_tensors='pt',
                     truncation_strategy='only_first')
logits = nli_model(x.to(device))[0]
# we throw away "neutral" (dim 1) and take the probability of
# "entailment" (2) as the probability of the label being true 
entail_contradiction_logits = logits[:,[0,2]]
probs = entail_contradiction_logits.softmax(dim=1)
prob_label_is_true = probs[:,1]
```
## Training

## Version 0.1
The model has been now retrained on the full training set. Around 1000 sentences pairs have been removed from the set because their translation was botched by the translation model.

| metric          	| value 	|
|-----------------	|-------	|
| learning_rate    	| 4e-6  	|
| optimizer       	| AdamW 	|
| batch_size      	| 80    	|
| mcc             	| 0.77  	|
| train_loss      	| 0.34  	|
| eval_loss       	| 0.40  	|
| stopped_at_step 	| 9754  	|

## Version 0.0
This model was pre-trained on set of 100 languages, as described in
[the original paper](https://arxiv.org/abs/1911.02116). It was then fine-tuned on the task of NLI on an Italian translation of the MNLI dataset (85% of the train set only so far). The model used for translating the texts is Helsinki-NLP/opus-mt-en-it, with a max output sequence lenght of 120. The model has been trained for 1 epoch with learning rate 4e-6 and batch size 80, currently it scores 82 acc. on the remaining 15% of the training.