# BERT based temporal tagged 

Token classifier for temporal tagging of plain text using German Gelectra model. 
# Model description
GELECTRA is a transformer (ELECTRA) model pretrained on a large corpus of German data in a self-supervised fashion. We use GELECTRA for token classification to tag the tokens in text with classes (tags are from english timex3 format): 
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


# Intended uses & limitations
This model is best used accompanied with code from the [repository](https://github.com/satya77/Transformer_Temporal_Tagger). Especially for inference, the direct output might be noisy and hard to decipher, in the repository we provide alignment functions and voting strategies for the final output. The repo examples the english models, the german model can be used the same way.

# How to use
you can load the model as follows:
```
    tokenizer = AutoTokenizer.from_pretrained("satyaalmasian/temporal_tagger_German_GELECTRA", use_fast=False)
    model = BertForTokenClassification.from_pretrained("satyaalmasian/temporal_tagger_German_GELECTRA")

```
for inference use: 
```
processed_text = tokenizer(input_text, return_tensors="pt")
result = model(**processed_text)
classification= result[0]

```
for an example with post-processing, refer to the [repository](https://github.com/satya77/Transformer_Temporal_Tagger). 
We provide a function `merge_tokens` to decipher the output. 
to further fine-tune, use the `Trainer` from hugginface. An example of a similar fine-tuning can be found [here](https://github.com/satya77/Transformer_Temporal_Tagger/blob/master/run_token_classifier.py).

# Training data

For pre-training we use a large corpus of automatically annotated news articles with heideltime. 

We use 2 data sources for fine-tunning. : 
[Tempeval-3](https://www.cs.york.ac.uk/semeval-2013/task1/index.php%3Fid=data.html),automatically translated to gemran, 
[KRAUTS dataset](https://github.com/JannikStroetgen/KRAUTS). 

# Training procedure
The model is trained from publicly available checkpoints on huggingface (`deepset/gelectra-large`), with a batch size of 192. We use a learning rate of 1e-07 with an Adam optimizer and linear weight decay for pretraining. 
For fine-tuning we use a batch size of 16. We use a learning rate of 5e-05 with an Adam optimizer and linear weight decay.
We fine-tune with 3 different random seeds, this version of the model is the only seed=7.
For training, we use 2 NVIDIA A100 GPUs with 40GB of memory. 

 

