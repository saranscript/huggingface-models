# Model description
A Pretrained model on the Kinyarwanda language dataset using a masked language modeling (MLM) objective. The BERT model was first introduced in [this paper](https://arxiv.org/abs/1810.04805). This KinyaBERT model was pretrained with uncased tokens which means that no difference between for example ikinyarwanda and Ikinyarwanda. 
# Training parameters
 #### Dataset 
 
 The data set used has both sources from the new articles in Rwanda extracted from different new web pages, dumped Wikipedia files, and the books in Kinyarwanda. The sizes of the sources of data are 72 thousand new articles, three thousand dumped Wikipedia articles, and six books with more than a thousand pages.
 
 #### Hyperparameters
 The model was trained with the default configuration of BERT and Trainer from the Huggingface. However, due to some resource computation issues, we kept the number of transformer layers to 6.
# How to use:
1) The model can be used directly with the pipeline for masked language modeling as follows:
```
from transformers import pipeline
the_mask_pipe = pipeline(
    "fill-mask",
    model='jean-paul/KinyaBERT-small',
    tokenizer='jean-paul/KinyaBERT-small',
)
the_mask_pipe("Ejo ndikwiga nagize [MASK] baje kunsura.")

[{'sequence': 'ejo ndikwiga nagize ubwoba baje kunsura.', 'score': 0.15674786269664764, 'token': 2387, 'token_str': 'ubwoba'}, 
{'sequence': 'ejo ndikwiga nagize ngo baje kunsura.', 'score': 0.13958698511123657, 'token': 196, 'token_str': 'ngo'}, 
{'sequence': 'ejo ndikwiga nagize inyota baje kunsura.', 'score': 0.07670339196920395, 'token': 8797, 'token_str': 'inyota'}, 
{'sequence': 'ejo ndikwiga nagize amahirwe baje kunsura.', 'score': 0.07234629988670349, 'token': 1501, 'token_str': 'amahirwe'}, 
{'sequence': 'ejo ndikwiga nagize abana baje kunsura.', 'score': 0.05717536434531212, 'token': 526, 'token_str': 'abana'}]
```

2) Direct use from the transformer library to get features using AutoModel

```
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("jean-paul/KinyaBERT-small")

model = AutoModelForMaskedLM.from_pretrained("jean-paul/KinyaBERT-small")

input_text = "Ejo ndikwiga nagize abashyitsi baje kunsura."
encoded_input = tokenizer(input_text, return_tensors='pt')
output = model(**encoded_input)

```
__Note__: We used the huggingface implementations for pretraining BERT from scratch, both the BERT model and the classes needed to do it.