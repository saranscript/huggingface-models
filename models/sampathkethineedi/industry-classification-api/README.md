---
language: "en"
thumbnail: "https://huggingface.co/sampathkethineedi"
widget:
 - text: "3rd Rock Multimedia Limited is an India-based event management company. The Company conducts film promotions, international events, corporate events and cultural events. The Company's entertainment properties include 3rd Rock Fashion Fiesta and 3rd Rock Calendar. The Company's association with various events in Mumbai includes Bryan Adam's Live in Concert, Michael Learns to Rock (MLTR) Eternity Concert, 3rd Rock's Calendar Launch 2011-2012, Airtel I Phone 4 Launch and ISPL Cricket Tournament 2012."
 - text: "Stellar Capital Services Limited is an India-based non-banking financial company. The Company is mainly engaged in the business of providing loans and advances and investing in shares, both quoted and unquoted. The Company's segments are trading in share and securities, and advancing of loans. The trading in share and securities segment includes trading in quoted equity shares, mutual funds, bonds, futures and options, and currency. The Company's financial services include inter corporate deposits, financial consultancy, retail initial public offering (IPO) funding, loan against property, management consultancy, personal loans and unsecured loans."
 - text: "Chemcrux Enterprises Ltd is a manufacturer of intermediates for bulk drugs, and dyes and pigments. The Company's products include 2 Chloro Benzoic Acid; 3 Chloro Benzoic Acid; 4 Chloro Benzoic Acid; 4 Nitro Benzoic Acid; 2,4 Dichloro Benzoic Acid; 4 Chloro 3 Nitro Benzoic Acid; 2 Chloro 5 Nitro Benzoic Acid; Meta Nitro Benzoic Acid; Lassamide, and Meta Chloro Per Benzoic Acid. The Company also offers various products on custom requirements, including Aceturic Acid; Meta Chloro Benzoyl Chloride; 3-Nitro-4-Methoxy Benzoic Acid; 2 Amino 5 Sulfonamide Benzoic Acid; 3,4 Dichloro Benzoic Acid; 5-Nitro Salycylic Acid, and 4-Chloro Benzoic Acid -3-Sulfonamide. The Company's plant has a capacity of 120 metric tons per month. The Company exports to Europe, Japan, the Middle East and East Africa. It is engaged in development and execution of various processes, such as High Pressure Oxidation, Nitration and Chloro Sulfonation."
tags:
- bert
- pytorch
- text-classification
- industry tags
- buisiness description
- multi-label 
- classification
- inference
liscence: "mit"
---

# industry-classification-api

## Model description

BERT Model to classify a business description into one of **62 industry tags**. 
Trained on 7000 samples of Business Descriptions and associated labels of companies in India.

## How to use

PyTorch only

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

tokenizer = AutoTokenizer.from_pretrained("sampathkethineedi/industry-classification")  
model = AutoModelForSequenceClassification.from_pretrained("industry-classification")

industry_tags = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)
industry_tags("Stellar Capital Services Limited is an India-based non-banking financial company ... loan against property, management consultancy, personal loans and unsecured loans.")

'''Ouput'''
[{'label': 'Consumer Finance', 'score': 0.9841355681419373}]
```

## Limitations and bias
Training data is only for Indian companies
