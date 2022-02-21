# Model description
A Pretrained model on the Kinyarwanda language dataset using a masked language modeling (MLM) objective. RoBerta model was first introduced in [this paper](https://arxiv.org/abs/1907.11692). This KinyaRoBERTa model was pretrained with uncased tokens which means that no difference between for example ikinyarwanda and Ikinyarwanda.
 
# Training parameters

 #### Dataset 
 
 The data set used has both sources from the new articles in Rwanda extracted from different new web pages, dumped Wikipedia files, and the books in Kinyarwanda. The sizes of the sources of data are 72 thousand new articles, three thousand dumped Wikipedia articles, and six books with more than a thousand pages.
 
 #### Hyperparameters
 
The model was trained with the default configuration of RoBerta and Trainer from the Huggingface. However, due to some resource computation issues, we kept the number of transformer layers to 6.
 
# How to use:
The model can be used directly with the pipeline for masked language modeling as follows:
```
from transformers import pipeline
the_mask_pipe = pipeline(
    "fill-mask",
    model='jean-paul/kinyaRoberta-small',
    tokenizer='jean-paul/kinyaRoberta-small',
)

the_mask_pipe("Ejo ndikwiga nagize <mask> baje kunsura.")

[{'sequence': 'Ejo ndikwiga nagize amahirwe baje kunsura.', 'score': 0.3530674874782562, 'token': 1711, 'token_str': ' amahirwe'}, 
{'sequence': 'Ejo ndikwiga nagize ubwoba baje kunsura.', 'score': 0.2858319878578186, 'token': 2594, 'token_str': ' ubwoba'}, 
{'sequence': 'Ejo ndikwiga nagize ngo baje kunsura.', 'score': 0.032475441694259644, 'token': 396, 'token_str': ' ngo'}, 
{'sequence': 'Ejo ndikwiga nagize abana baje kunsura.', 'score': 0.029481062665581703, 'token': 739, 'token_str': ' abana'}, 
{'sequence': 'Ejo ndikwiga nagize abantu baje kunsura.', 'score': 0.016263306140899658, 'token': 500, 'token_str': ' abantu'}]
```
2) Direct use from the transformer library to get features using AutoModel

```
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("jean-paul/kinyaRoberta-small")

model = AutoModelForMaskedLM.from_pretrained("jean-paul/kinyaRoberta-small")

input_text = "Ejo ndikwiga nagize abashyitsi baje kunsura."
encoded_input = tokenizer(input_text, return_tensors='pt')
output = model(**encoded_input)

```
__Note__: We used the huggingface implementations for pretraining RoBerta from scratch, both the RoBerta model and the classes needed to do it.