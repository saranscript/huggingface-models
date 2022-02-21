# BERT based temporal tagged 

Token classifier for temporal tagging of plain text using BERT language model and CRFs. The model is introduced in the paper BERT got a Date: Introducing Transformers to Temporal Tagging and release in this [repository](https://github.com/satya77/Transformer_Temporal_Tagger).

# Model description
BERT is a transformers model pretrained on a large corpus of English data in a self-supervised fashion. We use BERT for token classification to tag the tokens in text with classes: 
```
O -- outside of a tag 
I-TIME -- inside tag of time 
B-TIME -- beginning tag of time
I-DATE -- inside tag of date 
B-DATE -- beginning tag of date
I-DURATION -- inside tag of duration 
B-DURATION -- beginning tag of duration
I-SET -- inside tag of the set 
B-SET -- beginning tag of the set
```
On top of the BERT classification layer, we add a custom CRF layer. This is a variant of `satyaalmasian/temporal_tagger_BERT_tokenclassifier` with slightly better 
performance but can not be used out of the box with huggingface models and needs the code from the accompanying [repository](https://github.com/satya77/Transformer_Temporal_Tagger).

# Intended uses & limitations
This model is best used accompanied with code from the [repository](https://github.com/satya77/Transformer_Temporal_Tagger). Especially for inference, the direct output might be noisy and hard to decipher, in the repository we provide alignment functions and voting strategies for the final output.

# How to use
you can load the model as follows:
```
    tokenizer = AutoTokenizer.from_pretrained("satyaalmasian/temporal_tagger_BERTCRF_tokenclassifier", use_fast=False)
    model = BertForTokenClassification.from_pretrained("satyaalmasian/temporal_tagger_BERTCRF_tokenclassifier")

```
for inference use: 
```
processed_text = tokenizer(input_text, return_tensors="pt")
processed_text["inference_mode"]=True
result = model(**processed_text)
classification= result[0]

```
for an example with post-processing, refer to the [repository](https://github.com/satya77/Transformer_Temporal_Tagger). 
We provide a function `merge_tokens` to decipher the output. 
to further fine-tune, use the `Trainer` from hugginface. An example of a similar fine-tuning can be found [here](https://github.com/satya77/Transformer_Temporal_Tagger/blob/master/run_token_classifier.py).

#Training data
We use 3 data sources: 
[Tempeval-3](https://www.cs.york.ac.uk/semeval-2013/task1/index.php%3Fid=data.html), Wikiwars, Tweets datasets. For the correct data versions please refer to our [repository](https://github.com/satya77/Transformer_Temporal_Tagger). 

#Training procedure
The model is trained from publicly available checkpoints on huggingface (`bert-base-uncased`), with a batch size of 34. We use a learning rate of 5e-05 with an Adam optimizer and linear weight decay.
We fine-tune with 5 different random seeds, this version of the model is the only seed=19.
For training, we use 2 NVIDIA A100 GPUs with 40GB of memory. 

 


