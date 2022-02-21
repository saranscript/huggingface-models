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
      value: 1.352389
widget:
- text: "Com efeito, se tal fosse possível, o Poder [MASK] – que não dispõe de função legislativa – passaria a desempenhar atribuição que lhe é institucionalmente estranha (a de legislador positivo), usurpando, desse modo, no contexto de um sistema de poderes essencialmente limitados, competência que não lhe pertence, com evidente transgressão ao princípio constitucional da separação de poderes."
---

## (BERT base) Language modeling in the legal domain in Portuguese (LeNER-Br)

**bert-base-cased-pt-lenerbr** is a Language Model in the legal domain in Portuguese that was finetuned on 20/12/2021 in Google Colab from the model [BERTimbau base](https://huggingface.co/neuralmind/bert-base-portuguese-cased) on the dataset [LeNER-Br language modeling](https://huggingface.co/datasets/pierreguillou/lener_br_finetuning_language_model) by using a MASK objective.

You can check as well the [version large of this model](https://huggingface.co/pierreguillou/bert-large-cased-pt-lenerbr).
  
## Blog post

This language model is used to get a NER model on the Portuguese judicial domain. You can check the fine-tuned NER model at [pierreguillou/ner-bert-base-cased-pt-lenerbr](https://huggingface.co/pierreguillou/ner-bert-base-cased-pt-lenerbr).

All informations and links are in this blog post: [NLP | Modelos e Web App para Reconhecimento de Entidade Nomeada (NER) no domínio jurídico brasileiro](https://medium.com/@pierre_guillou/nlp-modelos-e-web-app-para-reconhecimento-de-entidade-nomeada-ner-no-dom%C3%ADnio-jur%C3%ADdico-b658db55edfb) (29/12/2021)

## Widget & APP

You can test this model into the widget of this page.

## Using the model for inference in production
````
# install pytorch: check https://pytorch.org/
# !pip install transformers 
from transformers import AutoTokenizer, AutoModelForMaskedLM

tokenizer = AutoTokenizer.from_pretrained("pierreguillou/bert-base-cased-pt-lenerbr")
model = AutoModelForMaskedLM.from_pretrained("pierreguillou/bert-base-cased-pt-lenerbr")
````

## Training procedure

## Notebook

The notebook of finetuning ([Finetuning_language_model_BERtimbau_LeNER_Br.ipynb](https://github.com/piegu/language-models/blob/master/Finetuning_language_model_BERtimbau_LeNER_Br.ipynb)) is in github.

### Training results

````
Num examples = 3227
Num Epochs = 5
Instantaneous batch size per device = 8
Total train batch size (w. parallel, distributed & accumulation) = 8
Gradient Accumulation steps = 1
Total optimization steps = 2020

Step	Training Loss	Validation Loss
100	 1.988700	     1.616412
200	 1.724900	     1.561100
300	 1.713400	     1.499991
400	 1.687400	     1.451414
500	 1.579700	     1.433665
600	 1.556900	     1.407338
700	 1.591400	     1.421942
800	 1.546000	     1.406395
900	 1.510100	     1.352389
1000	1.507100     	1.394799
1100	1.462200     	1.36809373471
````