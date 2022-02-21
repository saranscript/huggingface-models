---
language:
- en
inference: false
pipeline_tag: false
datasets:
- conll2003
- wnut_17
- jnlpba
- conll2012
- BTC
- dfki-nlp/few-nerd
tags:
- PyTorch
model-index:
- name: "bert-base-NER-reptile-5-datasets"
  results:
  - task: 
      name: few-shot-ner
      type: named-entity-recognition
    dataset:
      name: few-nerd-inter
      type: named-entity-recognition
    metrics:
       - name: 5 way 1~2 shot
         type: f1
         value: 56.12
       - name: 5-way 5~10-shot
         type: f1
         value: 62.7
       - name: 10-way 1~2-shot
         type: f1
         value: 50.3
       - name: 10-way 5~10-shot
         type: f1
         value: 58.82
---

# BERT base uncased model pre-trained on 5 NER datasets

Model was trained by _SberIDP_. The pretraining process and technical details are described [in this article](https://habr.com/ru/company/sberbank/blog/649609/).


* Task: Named Entity Recognition
* Base model: [bert-base-uncased](https://huggingface.co/bert-base-uncased)
* Training Data is 5 datasets: [CoNLL-2003](https://aclanthology.org/W03-0419.pdf), [WNUT17](http://noisy-text.github.io/2017/emerging-rare-entities.html), [JNLPBA](http://www.geniaproject.org/shared-tasks/bionlp-jnlpba-shared-task-2004), [CoNLL-2012 (OntoNotes)](https://aclanthology.org/W12-4501.pdf), [BTC](https://www.derczynski.com/papers/btc.pdf)
* Testing was made in Few-Shot scenario on [Few-NERD dataset](https://github.com/thunlp/Few-NERD) using the model as a backbone for [StructShot](https://arxiv.org/abs/2010.02405)



The model is pretrained for NER task using [Reptile](https://openai.com/blog/reptile/) and can be finetuned for new entities with only a small amount of samples.