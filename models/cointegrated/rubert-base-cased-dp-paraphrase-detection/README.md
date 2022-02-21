This is a version of paraphrase detector by DeepPavlov ([details in the documentation](http://docs.deeppavlov.ai/en/master/features/overview.html#ranking-model-docs)) ported to the `Transformers` format. 

All credit goes to the authors of DeepPavlov.

The model has been trained on the dataset from http://paraphraser.ru/. 

It classifies texts as paraphrases (class 1) or non-paraphrases (class 0).

```python
import torch
from transformers import AutoModelForSequenceClassification, BertTokenizer
model_name = 'cointegrated/rubert-base-cased-dp-paraphrase-detection'
model = AutoModelForSequenceClassification.from_pretrained(model_name).cuda()
tokenizer = BertTokenizer.from_pretrained(model_name)

def compare_texts(text1, text2):
    batch = tokenizer(text1, text2, return_tensors='pt').to(model.device)
    with torch.inference_mode():
        proba = torch.softmax(model(**batch).logits, -1).cpu().numpy()
    return proba[0] # p(non-paraphrase), p(paraphrase)

print(compare_texts('Сегодня на улице хорошая погода', 'Сегодня на улице отвратительная погода'))
# [0.7056226 0.2943774]
print(compare_texts('Сегодня на улице хорошая погода', 'Отличная погодка сегодня выдалась'))
# [0.16524374 0.8347562 ]
```

P.S. In the DeepPavlov repository, the tokenizer uses `max_seq_length=64`. 
This model, however, uses `model_max_length=512`. 
Therefore, the results on long texts may be inadequate.