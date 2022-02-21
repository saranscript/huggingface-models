---
language:
- en
- ar
tags:
- translation
- Arabic Abjad Characters
- Arabic
license: apache-2.0
datasets:
- marefa-mt
---


# Marefa-Mt-En-Ar 
# نموذج المعرفة للترجمة الآلية من الإنجليزية للعربية

## Model description

This is a model for translating English to Arabic. The special about this model that is take into considration the
using of additional Arabic characters like `پ` or `گ`.

## عن النموذج
هذا النموذج للترجمة الآلية من اللغة الإنجليزية إلى اللغة العربية, هو أول نماذج الترجمة الآلية التي تصدر تحت رعاية 
[موسوعة المعرفة](https://www.marefa.org)

يتميز هذا النموذج عن غيره من النماذج بدعمه لحروف الأبجدية العربية الإضافية لتمييز الصوتيات الخاصة في اللغة الإنجليزية مثل `پ` , `گ`.

يمكنك زيارة
[هذه الصفحة](https://www.marefa.org/%D8%A7%D9%84%D9%85%D8%B9%D8%B1%D9%81%D8%A9:%D8%AF%D9%84%D9%8A%D9%84_%D8%A7%D9%84%D8%A3%D8%B3%D9%84%D9%88%D8%A8#.D8.AD.D8.B1.D9.88.D9.81_.D8.A5.D8.B6.D8.A7.D9.81.D9.8A.D8.A9_.D9.84.D9.84.D9.86.D8.B7.D9.82_.D8.A7.D9.84.D8.B3.D9.84.D9.8A.D9.85)
لمعرفة أكثر عن أسلوب إستخدام هذه الحروف الأبجدية العربية


### How to use كيفية الإستخدام

Install transformers and sentencepiece (python >= 3.6)

`$ pip3 install transformers==4.3.0 sentencepiece==0.1.95 nltk==3.5 protobuf==3.15.3 torch==1.7.1`

> If you are using `Google Colab`, please restart your runtime after installing the packages.

-----------

```python
from transformers import MarianTokenizer, MarianMTModel
mname = "marefa-nlp/marefa-mt-en-ar"
tokenizer = MarianTokenizer.from_pretrained(mname)
model = MarianMTModel.from_pretrained(mname)

# English Sample Text
input = "President Putin went to the presidential palace in the capital, Kiev"

translated_tokens = model.generate(**tokenizer.prepare_seq2seq_batch([input], return_tensors="pt"))
translated_text = [tokenizer.decode(t, skip_special_tokens=True) for t in translated_tokens]

# translated Arabic Text
print(translated_text)
# ذهب الرئيس پوتن إلى القصر الرئاسي في العاصمة كييڤ
```