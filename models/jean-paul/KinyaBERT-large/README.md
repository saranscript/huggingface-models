# Model description

A Pretrained model on the Kinyarwanda language dataset using a masked language modeling (MLM) objective. The BERT model was first introduced in [this paper](https://arxiv.org/abs/1810.04805). This KinyaBERT model was pretrained with uncased tokens which means that no difference between for example ikinyarwanda and Ikinyarwanda. 

# Training parameters

 #### Dataset 
 
 The data set used has both sources from the new articles in Rwanda extracted from different new web pages, dumped Wikipedia files, and the books in Kinyarwanda. The sizes of the sources of data are 72 thousand new articles, three thousand dumped Wikipedia articles, and six books with more than a thousand pages.
 
 #### Hyperparameters
 The model was trained with the default configuration of BERT and Trainer from the Huggingface. However, due to some resource computation issues, we kept the number of transformer layers to 12.

# How to use:

1) The model can be used directly with the pipeline for masked language modeling as follows:

```
from transformers import pipeline
the_mask_pipe = pipeline(
    "fill-mask",
    model='jean-paul/KinyaBERT-large',
    tokenizer='jean-paul/KinyaBERT-large',
)
the_mask_pipe("Ejo ndikwiga nagize [MASK] baje kunsura.")

[{'sequence': 'ejo ndikwiga nagize amahirwe baje kunsura.', 'score': 0.3704017996788025, 'token': 1501, 'token_str': 'amahirwe'}, 
{'sequence': 'ejo ndikwiga nagize ngo baje kunsura.', 'score': 0.30745452642440796, 'token': 196, 'token_str': 'ngo'},
{'sequence': 'ejo ndikwiga nagize agahinda baje kunsura.', 'score': 0.0638100653886795, 'token': 3917, 'token_str': 'agahinda'},
{'sequence': 'ejo ndikwiga nagize ubwoba baje kunsura.', 'score': 0.04934622719883919, 'token': 2387, 'token_str': 'ubwoba'}, 
{'sequence': 'ejo ndikwiga nagizengo baje kunsura.', 'score': 0.02243402972817421, 'token': 455, 'token_str': '##ngo'}]
```

2) Direct use from the transformer library to get features using AutoModel

```
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("jean-paul/KinyaBERT-large")

model = AutoModelForMaskedLM.from_pretrained("jean-paul/KinyaBERT-large")

input_text = "Ejo ndikwiga nagize abashyitsi baje kunsura."
encoded_input = tokenizer(input_text, return_tensors='pt')
output = model(**encoded_input)

```
__Note__: We used the huggingface implementations for pretraining BERT from scratch, both the BERT model and the classes needed to do it.