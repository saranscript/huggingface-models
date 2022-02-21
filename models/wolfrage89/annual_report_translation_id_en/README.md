### Finetuned on annual report sentence pair
This marianMT has been further finetuned on annual report sentence pairs

## Test out at huggingface spaces!
https://huggingface.co/spaces/wolfrage89/finance_domain_translation_marianMT

## Sample colab notebook
https://colab.research.google.com/drive/1H57vwiah7n1JXvXYMqJ8dklrIuU6Cljb?usp=sharing

## How to use

```python
!pip install transformers
!pip install sentencepiece


from transformers import MarianMTModel, MarianTokenizer

tokenizer = MarianTokenizer.from_pretrained("wolfrage89/annual_report_translation_id_en")
model = MarianMTModel.from_pretrained("wolfrage89/annual_report_translation_id_en")

#tokenizing bahasa sentence
bahasa_sentence = "Interpretasi ini merupakan interpretasi atas PSAK 46: Pajak Penghasilan yang bertujuan untuk mengklarifikasi dan memberikan panduan dalam merefleksikan ketidakpastian perlakuan pajak penghasilan dalam laporan keuangan."
tokenized_bahasa_sentence = tokenizer([bahasa_sentence], return_tensors='pt', max_length=104, truncation=True)

#feeding tokenized sentence into model, the max_legnth have been set to 104 as the model was trained mostly on sentences with this length
translated_tokens = model.generate(**tokenized_bahasa_sentence, max_length=104)[0]

## decoding the tokens to get english sentence
english_sentence = tokenizer.decode(translated_tokens, skip_special_tokens=True)

print(english_sentence)
# This interpretation is an interpretation of PSAK 46: Income Tax that aims to clarify and provide guidance in reflecting the uncertainty of income tax treatments in the financial statements.


```




### opus-mt-id-en (original model)

* source languages: id
* target languages: en
*  OPUS readme: [id-en](https://github.com/Helsinki-NLP/OPUS-MT-train/blob/master/models/id-en/README.md)
