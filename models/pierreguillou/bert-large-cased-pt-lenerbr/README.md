---
language: 
- pt
tags:
- generated_from_trainer
datasets:
- pierreguillou/lener_br_finetuning_language_model
model-index:
- name: checkpoints
  results:
  - task:
      name: Fill Mask
      type: fill-mask
    dataset:
      name: pierreguillou/lener_br_finetuning_language_model
      type: pierreguillou/lener_br_finetuning_language_model
    metrics:
    - name: Loss
      type: loss
      value: 1.127950
widget:
- text: "Com efeito, se tal fosse possível, o Poder [MASK] – que não dispõe de função legislativa – passaria a desempenhar atribuição que lhe é institucionalmente estranha (a de legislador positivo), usurpando, desse modo, no contexto de um sistema de poderes essencialmente limitados, competência que não lhe pertence, com evidente transgressão ao princípio constitucional da separação de poderes."
---

## (BERT large) Language modeling in the legal domain in Portuguese (LeNER-Br)

**bert-large-cased-pt-lenerbr** is a Language Model in the legal domain in Portuguese that was finetuned on 20/12/2021 in Google Colab from the model [BERTimbau large](https://huggingface.co/neuralmind/bert-large-portuguese-cased) on the dataset [LeNER-Br language modeling](https://huggingface.co/datasets/pierreguillou/lener_br_finetuning_language_model) by using a MASK objective.

You can check as well the [version base of this model](https://huggingface.co/pierreguillou/bert-base-cased-pt-lenerbr).
  
## Widget & APP

You can test this model into the widget of this page.

## Blog post

This language model is used to get a NER model on the Portuguese judicial domain. You can check the fine-tuned NER model at [pierreguillou/ner-bert-large-cased-pt-lenerbr](https://huggingface.co/pierreguillou/ner-bert-large-cased-pt-lenerbr).

All informations and links are in this blog post: [NLP | Modelos e Web App para Reconhecimento de Entidade Nomeada (NER) no domínio jurídico brasileiro](https://medium.com/@pierre_guillou/nlp-modelos-e-web-app-para-reconhecimento-de-entidade-nomeada-ner-no-dom%C3%ADnio-jur%C3%ADdico-b658db55edfb) (29/12/2021)

## Using the model for inference in production
````
# install pytorch: check https://pytorch.org/
# !pip install transformers 
from transformers import AutoTokenizer, AutoModelForMaskedLM

tokenizer = AutoTokenizer.from_pretrained("pierreguillou/bert-large-cased-pt-lenerbr")
model = AutoModelForMaskedLM.from_pretrained("pierreguillou/bert-large-cased-pt-lenerbr")
````

## Training procedure

## Notebook

The notebook of finetuning ([Finetuning_language_model_BERtimbau_LeNER_Br.ipynb](https://github.com/piegu/language-models/blob/master/Finetuning_language_model_BERtimbau_LeNER_Br.ipynb)) is in github.

### Training results

````
Num examples = 3227
Num Epochs = 5
Instantaneous batch size per device = 2
Total train batch size (w. parallel, distributed & accumulation) = 8
Gradient Accumulation steps = 4
Total optimization steps = 2015

Step	Training Loss	Validation Loss
100   1.616700      1.366015
200   1.452000      1.312473
300   1.431100      1.253055
400   1.407500      1.264705
500   1.301900      1.243277
600   1.317800      1.233684
700   1.319100      1.211826
800   1.303800      1.190818
900   1.262800      1.171898
1000  1.235900      1.146275
1100  1.221900      1.149027
1200  1.226200      1.127950
1300  1.201700      1.172729
1400  1.198200      1.145363
````