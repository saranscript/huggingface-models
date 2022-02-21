---
language:
- en
tags:
- summarization
- t&c
- tos
- distilbart
- distilbart-6-6
datasets:
- tosdr
metrics:
- rouge1
- rouge2
- rougel
inference:
  parameters:
    min_length: 5
    max_length: 512
    do_sample: False
widget:
- text: "In addition, certain portions of the Web Site may be subject to additional terms of use that we make available for your review or otherwise link to that portion of the Web Site to which such additional terms apply. By using such portions, or any part thereof, you agree to be bound by the additional terms of use applicable to such portions. Age Restrictions The Web Site may be accessed and used only by individuals who can form legally binding contracts under applicable laws, who are at least 18 years of age or the age of majority in their state or territory of residence (if higher than 18), and who are not barred from using the Web Site under applicable laws. Our Technology may not be copied, modified, reproduced, republished, posted, transmitted, sold, offered for sale, or redistributed in any way without our prior written permission and the prior written permission of our applicable licensors. Nothing in these Site Terms of Use grants you any right to receive delivery of a copy of Our Technology or to obtain access to Our Technology except as generally and ordinarily permitted through the Web Site according to these Site Terms of Use. Furthermore, nothing in these Site Terms of Use will be deemed to grant you, by implication, estoppel or otherwise, a license to Our Technology. Certain of the names, logos, and other materials displayed via the Web site constitute trademarks, tradenames, service marks or logos (“Marks”) of us or other entities. You are not authorized to use any such Marks. Ownership of all such Marks and the goodwill associated therewith remains with us or those other entities. Any use of third party software provided in connection with the Web Site will be governed by such third parties’ licenses and not by these Site Terms of Use. Information on this Web Site may contain technical inaccuracies or typographical errors. Lenovo provides no assurances that any reported problems may be resolved with the use of any information that Lenovo provides."
---

# T&C Summarization Model   

T&C Summarization Model based on [sshleifer/distilbart-cnn-6-6](https://huggingface.co/sshleifer/distilbart-cnn-6-6), 

This abstractive summarization model is a part of a bigger end-to-end T&C summarizer pipeline 
which is preceded by LSA (Latent Semantic Analysis) extractive summarization. The extractive 
summarization shortens the T&C to be further summarized by this model.

## Finetuning Corpus

We collaborated with [TOSDR](https://tosdr.org/) to work with their data, and the model is finetuned accordingly. The article and 
summarization text is reduced via extractive summarization before it is finetuned to the model.

## Contact Us

https://ml6.eu/ . 

This abstractive model finetuning is the continuation of the Christmas Project 2021 done in ML6: https://bit.ly/XmasProjects .

## Load Finetuned Model

```
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("ml6team/distilbart-tos-summarizer-tosdr")

model = AutoModelForSeq2SeqLM.from_pretrained("ml6team/distilbart-tos-summarizer-tosdr")
```

## Code Sample

This sample requires [sumy](https://pypi.org/project/sumy/), the LSA Extractive Summarization library, as additional package to 
run.

```
import re
import nltk
nltk.download('punkt')
from sumy.parsers.plaintext import PlaintextParser
from sumy.nlp.tokenizers import Tokenizer
from sumy.nlp.stemmers import Stemmer
from sumy.summarizers.lsa import LsaSummarizer
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

LANGUAGE = "english"
EXTRACTED_ARTICLE_SENTENCES_LEN = 12

stemmer = Stemmer(LANGUAGE)
lsa_summarizer = LsaSummarizer(stemmer)
tokenizer = AutoTokenizer.from_pretrained("ml6team/distilbart-tos-summarizer-tosdr")
model = AutoModelForSeq2SeqLM.from_pretrained("ml6team/distilbart-tos-summarizer-tosdr")

def get_extractive_summary(text, sentences_count):
  parser = PlaintextParser.from_string(text, Tokenizer(LANGUAGE))
  summarized_info = lsa_summarizer(parser.document, sentences_count)
  summarized_info = [element._text for element in summarized_info]
  return ' '.join(summarized_info)

def get_summary(dict_summarizer_model, dict_tokenizer, text_content):
  text_content = get_extractive_summary(text_content, EXTRACTED_ARTICLE_SENTENCES_LEN)
  tokenizer = dict_tokenizer['tokenizer']
  model = dict_summarizer_model['model']

  inputs = tokenizer(text_content, max_length=dict_tokenizer['max_length'], truncation=True, return_tensors="pt")
  outputs = model.generate(
      inputs["input_ids"], max_length=dict_summarizer_model['max_length'], min_length=dict_summarizer_model['min_length'], 
  )

  summarized_text = tokenizer.decode(outputs[0])
  match = re.search(r"<s>(.*)</s>", summarized_text)
  if match is not None: summarized_text = match.group(1)

  return summarized_text.replace('<s>', '').replace('</s>', '') 
  
test_tos = """
  In addition, certain portions of the Web Site may be subject to additional terms of use that we make available for your review or otherwise link to that portion of the Web Site to which such additional terms apply. By using such portions, or any part thereof, you agree to be bound by the additional terms of use applicable to such portions. 
  Age Restrictions The Web Site may be accessed and used only by individuals who can form legally binding contracts under applicable laws, who are at least 18 years of age or the age of majority in their state or territory of residence (if higher than 18), and who are not barred from using the Web Site under applicable laws. 
  Our Technology may not be copied, modified, reproduced, republished, posted, transmitted, sold, offered for sale, or redistributed in any way without our prior written permission and the prior written permission of our applicable licensors. Nothing in these Site Terms of Use grants you any right to receive delivery of a copy of Our Technology or to obtain access to Our Technology except as generally and ordinarily permitted through the Web Site according to these Site Terms of Use. 
  Furthermore, nothing in these Site Terms of Use will be deemed to grant you, by implication, estoppel or otherwise, a license to Our Technology. Certain of the names, logos, and other materials displayed via the Web site constitute trademarks, tradenames, service marks or logos (“Marks”) of us or other entities. You are not authorized to use any such Marks. Ownership of all such Marks and the goodwill associated therewith remains with us or those other entities. 
  Any use of third party software provided in connection with the Web Site will be governed by such third parties’ licenses and not by these Site Terms of Use. Information on this Web Site may contain technical inaccuracies or typographical errors. Lenovo provides no assurances that any reported problems may be resolved with the use of any information that Lenovo provides
"""

model_dict = {
  'model': model, 
  'max_length': 512,
  'min_length': 4
}

tokenizer_dict = {
  'tokenizer': tokenizer, 
  'max_length': 1024
}

print(get_summary(model_dict, tokenizer_dict, test_tos))
```
