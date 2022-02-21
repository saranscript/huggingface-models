---
language: 
- gu
- hi
- mr
- bn
---

# Indo-Aryan-XLM-R-Base


This model is finetuned over [XLM-RoBERTa](https://huggingface.co/xlm-roberta-base) (XLM-R) using its base variant with the Hindi, Gujarati, Marathi, and Bengali languages from the Indo-Aryan family using the [OSCAR](https://oscar-corpus.com/) monolingual datasets. As these languages had imbalanced datasets, we used resampling strategies as used in pretraining the XLM-R to balance the resulting dataset after combining these languages. We used the same masked language modelling (MLM) objective which was used for pretraining the XLM-R. As it is built over the pretrained XLM-R, we leveraged *Transfer Learning* by exploiting the knowledge from its parent model.

## Dataset
OSCAR corpus contains several diverse datasets for different languages. We followed the work of [CamemBERT](https://www.aclweb.org/anthology/2020.acl-main.645/) who reported better performance with this diverse dataset as compared to the other large homogenous datasets. 

## Preprocessing and Training Procedure
Please visit [this link](https://github.com/ashwanitanwar/nmt-transfer-learning-xlm-r#6-finetuning-xlm-r) for the detailed procedure.

## Usage
- This model can be used for further finetuning for different NLP tasks using the Hindi, Gujarati, Marathi, and Bengali languages.
- It can be used to generate contextualised word representations for the words from the above languages.
- It can be used for domain adaptation.
- It can be used to predict the missing words from their sentences.

## Demo
 ### Using the model to predict missing words
   ```
   from transformers import pipeline
   unmasker = pipeline('fill-mask', model='ashwani-tanwar/Indo-Aryan-XLM-R-Base')
   pred_word = unmasker("અમદાવાદ એ ગુજરાતનું એક <mask> છે.")
   print(pred_word) 
   ```
   ```
[{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક શહેર છે.</s>', 'score': 0.7811868786811829, 'token': 85227, 'token_str': '▁શહેર'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક ગામ છે.</s>', 'score': 0.055032357573509216, 'token': 66346, 'token_str': '▁ગામ'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક નામ છે.</s>', 'score': 0.0287721399217844, 'token': 29565, 'token_str': '▁નામ'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક રાજ્ય છે.</s>', 'score': 0.02565067447721958, 'token': 63678, 'token_str': '▁રાજ્ય'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એકનગર છે.</s>', 'score': 0.022877279669046402, 'token': 69702, 'token_str': 'નગર'}]
   ```
 ### Using the model to generate contextualised word representations
  ```
  from transformers import AutoTokenizer, AutoModel
  tokenizer = AutoTokenizer.from_pretrained("ashwani-tanwar/Indo-Aryan-XLM-R-Base")
  model = AutoModel.from_pretrained("ashwani-tanwar/Indo-Aryan-XLM-R-Base")
  sentence = "અમદાવાદ એ ગુજરાતનું એક શહેર છે."
  encoded_sentence = tokenizer(sentence, return_tensors='pt')
  context_word_rep = model(**encoded_sentence)
  ```
