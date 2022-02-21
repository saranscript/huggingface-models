#### MathBERT model (custom vocab)

Pretrained model on pre-k to graduate math language (English) using a masked language modeling (MLM) objective. This model is uncased: it does not make a difference between english and English.


#### Model description
MathBERT is a transformers model pretrained on a large corpus of English math corpus data in a self-supervised fashion. This means it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it was pretrained with two objectives:

Masked language modeling (MLM): taking a sentence, the model randomly masks 15% of the words in the input then run the entire masked sentence through the model and has to predict the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the sentence.
Next sentence prediction (NSP): the models concatenates two masked sentences as inputs during pretraining. Sometimes they correspond to sentences that were next to each other in the original text, sometimes not. The model then has to predict if the two sentences were following each other or not.
This way, the model learns an inner representation of the math language that can then be used to extract features useful for downstream tasks: if you have a dataset of labeled sentences for instance, you can train a standard classifier using the features produced by the MathBERT model as inputs.

#### Intended uses & limitations
You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to be fine-tuned on a math-related downstream task.

Note that this model is primarily aimed at being fine-tuned on math-related tasks that use the whole sentence (potentially masked) to make decisions, such as sequence classification, token classification or question answering. For tasks such as math text generation you should look at model like GPT2.

#### How to use
<!---You can use this model directly with a pipeline for masked language modeling:

>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='bert-base-uncased')
>>> unmasker("Hello I'm a [MASK] model.")

[{'sequence': "[CLS] hello i'm a fashion model. [SEP]",
  'score': 0.1073106899857521,
  'token': 4827,
  'token_str': 'fashion'},
 {'sequence': "[CLS] hello i'm a role model. [SEP]",
  'score': 0.08774490654468536,
  'token': 2535,
  'token_str': 'role'},
 {'sequence': "[CLS] hello i'm a new model. [SEP]",
  'score': 0.05338378623127937,
  'token': 2047,
  'token_str': 'new'},
 {'sequence': "[CLS] hello i'm a super model. [SEP]",
  'score': 0.04667217284440994,
  'token': 3565,
  'token_str': 'super'},
 {'sequence': "[CLS] hello i'm a fine model. [SEP]",
  'score': 0.027095865458250046,
  'token': 2986,
  'token_str': 'fine'}]--->
  
Here is how to use this model to get the features of a given text in PyTorch:

```from transformers import BertTokenizer, BertModel
tokenizer = BertTokenizer.from_pretrained('tbs17/MathBERT-custom')
model = BertModel.from_pretrained("tbs17/MathBERT-custom")
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(encoded_input)
```
and in TensorFlow:

```
from transformers import BertTokenizer, TFBertModel
tokenizer = BertTokenizer.from_pretrained('tbs17/MathBERT-custom')
model = TFBertModel.from_pretrained("tbs17/MathBERT-custom")
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```

#### Warning

MathBERT is specifically designed for mathematics related tasks and works better with mathematical problem text fill-mask tasks instead of general purpose fill-mask tasks. See the below example:

```
  >>> from transformers import pipeline
 >>> unmasker = pipeline('fill-mask', model='tbs17/MathBERT')
 # Below is desired usage
  >>> unmasker("students apply these new understandings as they reason about and perform decimal [MASK] through the hundredths place.")
  
[{'score': 0.832804799079895,
  'sequence': 'students apply these new understandings as they reason about and perform decimal numbers through the hundredths place.',
  'token': 3616,
  'token_str': 'numbers'},
 {'score': 0.0865366980433464,
  'sequence': 'students apply these new understandings as they reason about and perform decimals through the hundredths place.',
  'token': 2015,
  'token_str': '##s'},
 {'score': 0.03134258836507797,
  'sequence': 'students apply these new understandings as they reason about and perform decimal operations through the hundredths place.',
  'token': 3136,
  'token_str': 'operations'},
 {'score': 0.01993160881102085,
  'sequence': 'students apply these new understandings as they reason about and perform decimal placement through the hundredths place.',
  'token': 11073,
  'token_str': 'placement'},
 {'score': 0.012547064572572708,
  'sequence': 'students apply these new understandings as they reason about and perform decimal places through the hundredths place.',
  'token': 3182,
  'token_str': 'places'}]
  
  #Below is not the desired usage
   >>> unmasker("The man worked as a [MASK].")
   
  [{'score': 0.6469377875328064,
  'sequence': 'the man worked as a book.',
  'token': 2338,
  'token_str': 'book'},
 {'score': 0.07073448598384857,
  'sequence': 'the man worked as a guide.',
  'token': 5009,
  'token_str': 'guide'},
 {'score': 0.031362924724817276,
  'sequence': 'the man worked as a text.',
  'token': 3793,
  'token_str': 'text'},
 {'score': 0.02306508645415306,
  'sequence': 'the man worked as a man.',
  'token': 2158,
  'token_str': 'man'},
 {'score': 0.020547250285744667,
  'sequence': 'the man worked as a distance.',
  'token': 3292,
  'token_str': 'distance'}]
```

### Training data
The BERT model was pretrained on pre-k to HS math curriculum (engageNY, Utah Math, Illustrative Math), college math books from openculture.com as well as graduate level math from arxiv math paper abstracts. There is about 100M tokens got pretrained on.

#### Training procedure

The texts are lowercased and tokenized using WordPiece and a customized vocabulary size of 30,522. We use the ```bert_tokenizer``` from huggingface tokenizers library to generate a custom vocab file from our training raw math texts. The inputs of the model are then of the form:

```
[CLS] Sentence A [SEP] Sentence B [SEP]
```
With probability 0.5, sentence A and sentence B correspond to two consecutive sentences in the original corpus and in the other cases, it's another random sentence in the corpus. Note that what is considered a sentence here is a consecutive span of text usually longer than a single sentence. The only constrain is that the result with the two "sentences" has a combined length of less than 512 tokens.

The details of the masking procedure for each sentence are the following:

+ 15% of the tokens are masked.
+ In 80% of the cases, the masked tokens are replaced by [MASK].
+ In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
+ In the 10% remaining cases, the masked tokens are left as is.

#### Pretraining
The model was trained on a 8-core cloud TPUs from Google Colab for 600k steps with a batch size of 128. The sequence length was limited to 512 for the entire time. The optimizer used is Adam with a learning rate of 5e-5, beta_{1} = 0.9 and beta_{2} =0.999, a weight decay of 0.01, learning rate warmup for 10,000 steps and linear decay of the learning rate after.