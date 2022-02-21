# MSRoBERTa

Fine-tuned RoBERTa MLM model for [`Miscrosoft Sentence Completion Challenge`](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/MSR_SCCD.pdf). This model case-sensitive following the `Roberta-base` model.

# Model description (taken from: [here](https://huggingface.co/roberta-base))

RoBERTa is a transformers model pretrained on a large corpus of English data in a self-supervised fashion. This means
it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of
publicly available data) with an automatic process to generate inputs and labels from those texts. 

More precisely, it was pretrained with the Masked language modeling (MLM) objective. Taking a sentence, the model
randomly masks 15% of the words in the input then run the entire masked sentence through the model and has to predict
the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one
after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to
learn a bidirectional representation of the sentence.

This way, the model learns an inner representation of the English language that can then be used to extract features
useful for downstream tasks: if you have a dataset of labeled sentences for instance, you can train a standard
classifier using the features produced by the BERT model as inputs.

### How to use
You can use this model directly with a pipeline for masked language modeling:


```python
from transformers import pipeline,AutoModelForMaskedLM,AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained("nkoh01/MSRoberta")
model = AutoModelForMaskedLM.from_pretrained("nkoh01/MSRoberta")

unmasker = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
unmasker("Hello, it is a <mask> to meet you.")

[{'score': 0.9508683085441589,
  'sequence': 'hello, it is a pleasure to meet you.',
  'token': 10483,
  'token_str': ' pleasure'},
 {'score': 0.015089659951627254,
  'sequence': 'hello, it is a privilege to meet you.',
  'token': 9951,
  'token_str': ' privilege'},
 {'score': 0.013942377641797066,
  'sequence': 'hello, it is a joy to meet you.',
  'token': 5823,
  'token_str': ' joy'},
 {'score': 0.006964420434087515,
  'sequence': 'hello, it is a delight to meet you.',
  'token': 13213,
  'token_str': ' delight'},
 {'score': 0.0024567877408117056,
  'sequence': 'hello, it is a honour to meet you.',
  'token': 6671,
  'token_str': ' honour'}]
```

## Installations 
Make sure you run `!pip install transformers` command to install the transformers library before running the commands above. 

## Bias and limitations 
Under construction.
