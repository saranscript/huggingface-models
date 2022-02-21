---
license: cc-by-4.0
widget:
- context: "DeBERTa improves the BERT and RoBERTa models using disentangled attention and enhanced mask decoder. With those two improvements, DeBERTa out perform RoBERTa on a majority of NLU tasks with 80GB training data. In DeBERTa V3, we further improved the efficiency of DeBERTa using ELECTRA-Style pre-training with Gradient Disentangled Embedding Sharing. Compared to DeBERTa, our V3 version significantly improves the model performance on downstream tasks. You can find more technique details about the new model from our paper. Please check the official repository for more implementation details and updates."
  example_title: "DeBERTa v3 Q1"
  text: "How is DeBERTa version 3 different than previous ones?"
- context: "DeBERTa improves the BERT and RoBERTa models using disentangled attention and enhanced mask decoder. With those two improvements, DeBERTa out perform RoBERTa on a majority of NLU tasks with 80GB training data. In DeBERTa V3, we further improved the efficiency of DeBERTa using ELECTRA-Style pre-training with Gradient Disentangled Embedding Sharing. Compared to DeBERTa, our V3 version significantly improves the model performance on downstream tasks. You can find more technique details about the new model from our paper. Please check the official repository for more implementation details and updates."
  example_title: "DeBERTa v3 Q2"
  text: "Where do I go to see new info about DeBERTa?"
datasets:
- squad_v2
metrics:
- f1
- exact
tags:
- question-answering
language: en
model-index:
- name: DeBERTa v3 xsmall squad2 
  results:
  - task: 
      name: Question Answering
      type: question-answering
    dataset:
      name: SQuAD2.0
      type: question-answering
    metrics:
       - name: f1
         type: f1
         value: 81.5
       - name: exact
         type: exact
         value: 78.3
---


# DeBERTa v3 xsmall SQuAD 2.0

[Microsoft reports that this model can get 84.8/82.0](https://huggingface.co/microsoft/deberta-v3-xsmall#fine-tuning-on-nlu-tasks) on f1/em on the dev set. 

I got 81.5/78.3 but I only did one run and I didn't use the official squad2 evaluation script. I will do some more runs and show the results on the official script soon.
