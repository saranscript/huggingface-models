
---
language: en
widget:
- text: "I am really upset that I have to call up to three times to the number on the back of my insurance card for my call to be answer"
tags:
- sagemaker
- roberta-base
- text classification
license: apache-2.0
datasets:
- emotion
model-index:
- name: sagemaker-roberta-base-emotion
  results:
  - task: 
      name: Multi Class Text Classification
      type: text-classification
    dataset:
      name: "emotion" 
      type: emotion
    metrics:
       - name: Validation Accuracy
         type: accuracy
         value: 94.1
       - name: Validation F1
         type: f1
         value: 94.13
  
---
## roberta-base

This model is a fine-tuned model that was trained using Amazon SageMaker and the new Hugging Face Deep Learning container.
- Problem type: Multi Class Text Classification (emotion detection).

It achieves the following results on the evaluation set:
- Loss: 0.1613253802061081
- f1: 0.9413321705151999

## Hyperparameters
```json
{
    "epochs": 10,
    "train_batch_size": 16,
    "learning_rate": 3e-5, 
    "weight_decay":0.01,
    "load_best_model_at_end": true,
    "model_name":"roberta-base",
    "do_eval": True,
    "load_best_model_at_end":True
}
```
## Validation Metrics
| key | value |
| --- | ----- |
| eval_accuracy  | 0.941 |
| eval_f1 | 0.9413321705151999 |
| eval_loss | 0.1613253802061081|
| eval_recall | 0.941 |
| eval_precision | 0.9419519436781406 |

