---
datasets:
- mnli
- xnli
tags:
- sentence-similarity
- transformers
- text-classification
- zero-shot-classification
- salesken
- hindi
- cross-lingual
inference: false
---

# XLM-R Base

A multilingual model is pre-trained on text coming from a mix of languages. We will look at a multilingual model called XLM-R from Facebook also called as Cross Lingual Model - Roberta. Unlike BERT which was pre-trained on English Wikipedia and BookCorpus, XLM-R was pre-trained on Wikipedia and Common Crawl data from 100 different languages. A single model trained on 100 different languages. 
* So, there is a single shared vocabulary with 250K tokens to cover all 100 languages.
* There is no special marker which suggests which language it is.
* It wasn't trained with parallel data (i.e. same sentence in multiple languages)

# Cross Lingual Transfer (Zero-shot transfer)

Say you are building a classifier which will classify Hindi comments toxic or non-toxic. But say you have a training dataset in English of 225 K labeled comments called "Wikipedia Toxic Comments". The Cross Lingual Transfer of XLM-R will let you fine-tune XLM-R on Wikipedia Toxic Comments dataset in English, and then apply it to Hindi comments. So, XLM-R is able to take it's task specific knowledge that it learned in English and apply it on Hindi, even though we never showed it any Hindi exmaples. It's concept of transfer learning applied from one language to another which is called Cross Lingual Transfer. The same could be done on any other low-resource languages

We will see that training XLM-R purely on ~400K English samples acutally yields better results than fine-tuning a monolingual Hindi model on a much smaller Hindi dataset. This is also referred to as Zero-Shot Learning or Cross-Lingual Transfer

# Our Approach -

We will use MNLI that provides us with a large number of English training examples to fine-tune XLM-R on the general task of NLI. XNLI will provide us with a small number of NLI test examples in different languages for us it will be Hindi. MNLI (Multi-genre NLI) has 392,000 training examples and 20,000 development examples and 20,000 test examples. On the other hand XNLI is a small subset of examples from MNLI dataset which have been human-translated to 14 different languages and yes Hindi is a part of it. For each language we have 5,000 test set sentence pairs and 2,500 development set sentence pairs

# Fine-tuning Hyperparameters -

learning rate : 5e-6 with linear learning rate scheduling over total steps
epochs = 2
batch_size = 32
GPU : Tesla T4

# Using this model
This model can be used using Huggingface Transformers. I have created a pipeline for a sentence pair classification. Hope it will be useful.

```python
!pip3 install transformers

import transformers
import torch

from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("salesken/xlm-roberta-base-finetuned-mnli-cross-lingual-transfer")

model = AutoModelForSequenceClassification.from_pretrained("salesken/xlm-roberta-base-finetuned-mnli-cross-lingual-transfer")

device = torch.device('cuda')
print('GPU: ', torch.cuda.get_device_name(0))

model.to(device)

# Here I am giving the sentence pairs and also the ground truth values (1 : Similar, 0 : NotSimilar)
# we have purposely used Hindi-Hindi , Hindi-English, Transliterated Hindi-Engish, Kannada and Spanish and also code-switching of languages
# You can try your own pairs and languages

u_premise = ['क्या आपका बेटा गणित में रूचि रखता है',
            'क्या आपका बेटा गणित में रूचि रखता है',
            'क्या आपका बेटा गणित में रूचि रखता है',
            'मैं त्योहार के दौरान घर जा रहा हूँ',
             'क्या आपका बेटा गणित में रूचि रखता है',
            'hum ek cross lingual model banane ka soch rahe hai',
            'we are planning to build a cross-lingual language model',
            'Hi. A very good morning to all of you. Lets get started. ',
            'शुभ प्रभात',
            'how are you doing today sir ?',
            'how are you doing today sir ?',
            'Argentina and Brazil will play Copa America finals this weekend',
             'I want to visit Spain and Portugal next year'
            ]

u_hypothesis = ['क्या आपकी बेटी को विज्ञान में दिलचस्पी है',
               'is your daughther interested in science',
               'is your son interested in stem subjects',
               'इस साल मैं त्योहार के दौरान घर नहीं जाऊंगा',
                'इस साल मैं त्योहार के दौरान घर नहीं जाऊंगा',
               'हम एक क्रॉस-लिंगुअल लैंग्वेज मॉडल बनाने की योजना बना रहे हैं',
               'hum ek क्रॉस-लिंगुअल model bana rahe hai',
               'शुभ प्रभात',
               'subh prabhat to all of you',
               'ಇಂದು ನೀವು ಹೇಗಿದ್ದೀರಿ ಸರ್?',
               'ನನ್ನ ಸ್ನಾತಕೋತ್ತರರಿಗಾಗಿ ನಾನು ಯಂತ್ರ ಕಲಿಕೆ ಮತ್ತು ಡೇಟಾ ವಿಜ್ಞಾನವನ್ನು ಮಾಡುತ್ತಿದ್ದೇನೆ',
               'Argentina y Brasil jugarán la final de la Copa América este fin de semana',
               'Puedes ver la aurora boreal desde Noruega']

ground_truth = [1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 0, 1, 0]

from torch.utils.data import TensorDataset, DataLoader
import numpy as np
import textwrap
import pandas as pd

labels_ar = []
input_ids_ar = []
attn_masks_ar = []
max_len = 128
batch_size = 32
label_names = ['entailment', 'neutral', 'contradiction']

for u_prem, u_hyp in zip(u_premise, u_hypothesis):
    encoded_dict = tokenizer.encode_plus(u_prem, u_hyp, 
                                              max_length=max_len, 
                                              padding='max_length',
                                              truncation=True, 
                                              return_tensors='pt')
    
    # Add this example to our lists.
    input_ids_ar.append(encoded_dict['input_ids'])
    attn_masks_ar.append(encoded_dict['attention_mask'])
    
# Convert each Python list of Tensors into a 2D Tensor matrix.
input_ids_ar = torch.cat(input_ids_ar, dim=0)
attn_masks_ar = torch.cat(attn_masks_ar, dim=0)

# Construct a TensorDataset from the encoded examples.
prediction_dataset = TensorDataset(input_ids_ar, attn_masks_ar)

# And a dataloader for handling batching.
prediction_dataloader = DataLoader(prediction_dataset, batch_size=batch_size)

# Put model in evaluation mode
model.eval()

# Tracking variables 
predictions , true_labels = [], []

count = 0

# Predict 
for batch in prediction_dataloader:
    batch = tuple(t.to(device) for t in batch)
    b_input_ids, b_input_mask = batch
    with torch.no_grad():
        # Forward pass, calculate logit predictions
        outputs = model(b_input_ids, 
                        attention_mask=b_input_mask)
    logits = outputs[0]
    # Move logits to CPU
    logits = logits.detach().cpu().numpy()
    # Store predictions and true labels
    predictions.append(logits)

# Combine the results across all batches. 
flat_predictions = np.concatenate(predictions, axis=0)

# For each sample, pick the label (0, 1, or 2) with the highest score.
predicted_labels = np.argmax(flat_predictions, axis=1).flatten()

wrapper = textwrap.TextWrapper(width = 80, initial_indent='   ',subsequent_indent='   ')

def softmax(logits):
    return np.exp(logits) / np.sum(np.exp(logits))

finalOut = []
for sentA, sentB, pred_logits, grnd_truth in zip(u_premise, u_hypothesis, flat_predictions, ground_truth):
    probScore = softmax(pred_logits)
    maxScore = {'idx': 0, 'score': 0}
    for idx, score in enumerate(probScore):
        if score > maxScore['score']:
            maxScore['score'] = score
            maxScore['idx'] = idx
    if maxScore['score'] > 0.4:
        if maxScore['idx'] == 0:
            label = 'Similar'
        else:
            label = 'NotSimilar'
        finalOut.append((sentA, sentB, label, grnd_truth, maxScore['score']))

pd.set_option("display.max_colwidth", -1)
pd.DataFrame(finalOut, columns = ['sentence-1', 'sentence-2', 'semantic_matching', 'ground_truth', 'probability_score'])

```
