---
language: es
tags:
- sagemaker
- ruperta
- TextClassification
- SentimentAnalysis
license: apache-2.0
datasets:
- IMDbreviews_es
model-index:
name: RuPERTa_base_sentiment_analysis_es
results:
  - task:
        name: Sentiment Analysis
        type: sentiment-analysis
  - dataset:
        name: "IMDb Reviews in Spanish" 
        type: IMDbreviews_es
  - metrics:
       - name: Accuracy,
         type: accuracy,
         value: 0.881866
       - name: F1 Score,
         type: f1,
         value: 0.008272
       - name: Precision,
         type: precision,
         value: 0.858605
       - name: Recall,
         type: recall,
         value: 0.920062
widget:
- text: "Se trata de una película interesante, con un solido argumento y un gran interpretación de su actor principal"
---

## Model `RuPERTa_base_sentiment_analysis_es`

### **A finetuned model for Sentiment analysis in Spanish**

This model was trained using Amazon SageMaker and the new Hugging Face Deep Learning container,
The base model is **RuPERTa-base (uncased)** which is a RoBERTa model trained on a uncased version of big Spanish corpus.
It was trained by mrm8488, Manuel Romero.[Link to base model](https://huggingface.co/mrm8488/RuPERTa-base) 

## Dataset
The dataset is a collection of movie reviews in Spanish, about 50,000 reviews. The dataset is balanced and provides every review in english, in spanish and the label in both languages. 

Sizes of datasets:
- Train dataset: 42,500
- Validation dataset: 3,750
- Test dataset: 3,750


## Hyperparameters
    {
    "epochs": "4",
    "train_batch_size": "32",    
    "eval_batch_size": "8",
    "fp16": "true",
    "learning_rate": "3e-05",
    "model_name": "\"mrm8488/RuPERTa-base\"",
    "sagemaker_container_log_level": "20",
    "sagemaker_program": "\"train.py\"",
    }

## Evaluation results
Accuracy = 0.8629333333333333
F1 Score = 0.8648790746582545
Precision = 0.8479381443298969
Recall = 0.8825107296137339

## Test results
Accuracy = 0.8066666666666666
F1 Score = 0.8057862309134743
Precision = 0.7928307854507116
Recall = 0.8191721132897604

## Model in action

### Usage for Sentiment Analysis

```python
import torch
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("edumunozsala/RuPERTa_base_sentiment_analysis_es")
model = AutoModelForSequenceClassification.from_pretrained("edumunozsala/RuPERTa_base_sentiment_analysis_es")

text ="Se trata de una película interesante, con un solido argumento y un gran interpretación de su actor principal"

input_ids = torch.tensor(tokenizer.encode(text)).unsqueeze(0)
outputs = model(input_ids)
output = outputs.logits.argmax(1)
```

Created by [Eduardo Muñoz/@edumunozsala](https://github.com/edumunozsala)
