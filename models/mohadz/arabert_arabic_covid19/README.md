---
language: ar
widget:
 - text: "للوقايه من عدم انتشار [MASK]"
---
# arabert_c19: An Arabert model pretrained on 1.5 million COVID-19 multi-dialect Arabic tweets 
**ARABERT COVID-19** is a pretrained (fine-tuned) version of the AraBERT v2 model (https://huggingface.co/aubmindlab/bert-base-arabertv02). The pretraining was done using 1.5 million multi-dialect Arabic tweets regarding the COVID-19 pandemic from the “Large Arabic Twitter Dataset on COVID-19” (https://arxiv.org/abs/2004.04315).
The model can achieve better results for the tasks that deal with multi-dialect Arabic tweets in relation to the COVID-19 pandemic. 

# Classification results for multiple tasks including fake-news and hate speech detection when using arabert_c19 and mbert_ar_c19:
For more details refer to the paper (link)

|                                    | arabert  | mbert    | distilbert multi | arabert Covid-19 | mbert Covid-19 |
|------------------------------------|----------|----------|------------------|------------------|----------------|
| Contains hate (Binary)             |   0.8346 |   0.6675 |   0.7145         |   `0.8649`         |   0.8492       |
| Talk about a cure (Binary)         |   0.8193 |   0.7406 |   0.7127         |   0.9055         |   `0.9176`       |
| News or opinion (Binary)           |   0.8987 |   0.8332 |   0.8099         |   `0.9163`         |   0.9116       |
| Contains fake information (Binary) |   0.6415 |   0.5428 |   0.4743         |   `0.7739`         |   0.7228       |


# Preprocessing

```python
from arabert.preprocess import ArabertPreprocessor
model_name="moha/arabert_c19"
arabert_prep = ArabertPreprocessor(model_name=model_name)
text = "للوقايه من عدم انتشار كورونا عليك اولا غسل اليدين بالماء والصابون وتكون عملية الغسل دقيقه تشمل راحة اليد الأصابع التركيز على الإبهام"
arabert_prep.preprocess(text)
```


# Contacts
**Hadj Ameur**: [Github](https://github.com/MohamedHadjAmeur) | <mohamedhadjameur@gmail.com> | <mhadjameur@cerist.dz>

