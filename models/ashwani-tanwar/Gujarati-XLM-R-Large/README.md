---
language: gu
---

# Gujarati-XLM-R-Large


This model is finetuned over [XLM-RoBERTa](https://huggingface.co/xlm-roberta-large) (XLM-R) using its large variant with the Gujarati language using the [OSCAR](https://oscar-corpus.com/) monolingual dataset. We used the same masked language modelling (MLM) objective which was used for pretraining the XLM-R. As it is built over the pretrained XLM-R, we leveraged *Transfer Learning* by exploiting the knowledge from its parent model.

## Dataset
OSCAR corpus contains several diverse datasets for different languages. We followed the work of [CamemBERT](https://www.aclweb.org/anthology/2020.acl-main.645/) who reported better performance with this diverse dataset as compared to the other large homogenous datasets. 

## Preprocessing and Training Procedure
Please visit [this link](https://github.com/ashwanitanwar/nmt-transfer-learning-xlm-r#6-finetuning-xlm-r) for the detailed procedure.

## Usage
- This model can be used for further finetuning for different NLP tasks using the Gujarati language.
- It can be used to generate contextualised word representations for the Gujarati words.
- It can be used for domain adaptation.
- It can be used to predict the missing words from the Gujarati sentences.

## Demo
 ### Using the model to predict missing words
   ```
   from transformers import pipeline
   unmasker = pipeline('fill-mask', model='ashwani-tanwar/Gujarati-XLM-R-Large')
   pred_word = unmasker("અમદાવાદ એ ગુજરાતનું એક <mask> છે.")
   print(pred_word) 
   ```
   ```
[{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક શહેર છે.</s>', 'score': 0.9790881276130676, 'token': 85227, 'token_str': '▁શહેર'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક રાજ્ય છે.</s>', 'score': 0.004246668424457312, 'token': 63678, 'token_str': '▁રાજ્ય'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક ગામ છે.</s>', 'score': 0.0038021174259483814, 'token': 66346, 'token_str': '▁ગામ'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક મહત્વ છે.</s>', 'score': 0.002798238070681691, 'token': 126763, 'token_str': '▁મહત્વ'}, 
{'sequence': '<s> અમદાવાદ એ ગુજરાતનું એક અમદાવાદ છે.</s>', 'score': 0.0021192911081016064, 'token': 69499, 'token_str': '▁અમદાવાદ'}]
   ```
 ### Using the model to generate contextualised word representations
  ```
  from transformers import AutoTokenizer, AutoModel
  tokenizer = AutoTokenizer.from_pretrained("ashwani-tanwar/Gujarati-XLM-R-Large")
  model = AutoModel.from_pretrained("ashwani-tanwar/Gujarati-XLM-R-Large")
  sentence = "અમદાવાદ એ ગુજરાતનું એક શહેર છે."
  encoded_sentence = tokenizer(sentence, return_tensors='pt')
  context_word_rep = model(**encoded_sentence)
  ```
