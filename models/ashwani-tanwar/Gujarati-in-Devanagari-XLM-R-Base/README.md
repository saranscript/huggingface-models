---
language: gu
---

# Gujarati-in-Devanagari-XLM-R-Base


This model is finetuned over [XLM-RoBERTa](https://huggingface.co/xlm-roberta-base) (XLM-R) using its base variant with the Gujarati language using the [OSCAR](https://oscar-corpus.com/) monolingual dataset. We converted the Gujarati script to the Devanagari using [Indic-NLP](https://github.com/anoopkunchukuttan/indic_nlp_library) library. For example, the sentence 'અમદાવાદ એ ગુજરાતનું એક શહેર છે.' was converted to 'अमदावाद ए गुजरातनुं एक शहेर छे.'. This helped to get better contextualised representations for some words as the XLM-R was pre-trained with several languages written in Devanagari script such as Hindi, Marathi, Sanskrit, and so on. 

We used the same masked language modelling (MLM) objective which was used for pretraining the XLM-R. As it is built over the pretrained XLM-R, we leveraged *Transfer Learning* by exploiting the knowledge from its parent model.

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
   unmasker = pipeline('fill-mask', model='ashwani-tanwar/Gujarati-in-Devanagari-XLM-R-Base')
   pred_word = unmasker("अमदावाद ए गुजरातनुं एक <mask> छे.")
   print(pred_word) 
   ```
   ```
[{'sequence': '<s> अमदावाद ए गुजरातनुं एक नगर छे.</s>', 'score': 0.24843722581863403, 'token': 18576, 'token_str': '▁नगर'}, 
{'sequence': '<s> अमदावाद ए गुजरातनुं एक महानगर छे.</s>', 'score': 0.21455222368240356, 'token': 122519, 'token_str': '▁महानगर'}, 
{'sequence': '<s> अमदावाद ए गुजरातनुं एक राज्य छे.</s>', 'score': 0.16832049190998077, 'token': 10665, 'token_str': '▁राज्य'}, 
{'sequence': '<s> अमदावाद ए गुजरातनुं एक जिल्ला छे.</s>', 'score': 0.06764694303274155, 'token': 20396, 'token_str': '▁जिल्ला'}, 
{'sequence': '<s> अमदावाद ए गुजरातनुं एक शहर छे.</s>', 'score': 0.05364946648478508, 'token': 22770, 'token_str': '▁शहर'}]
   ```
 ### Using the model to generate contextualised word representations
  ```
  from transformers import AutoTokenizer, AutoModel
  tokenizer = AutoTokenizer.from_pretrained("ashwani-tanwar/Gujarati-in-Devanagari-XLM-R-Base")
  model = AutoModel.from_pretrained("ashwani-tanwar/Gujarati-in-Devanagari-XLM-R-Base")
  sentence = "अमदावाद ए गुजरातनुं एक शहेर छे."
  encoded_sentence = tokenizer(sentence, return_tensors='pt')
  context_word_rep = model(**encoded_sentence)
  ```
