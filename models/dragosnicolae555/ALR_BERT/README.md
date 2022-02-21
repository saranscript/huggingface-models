---

language: ro

---

# ALBert 

The ALR-Bert , **cased** model for Romanian, trained on a 15GB corpus!
ALR-BERT is a multi-layer bidirectional Transformer encoder that shares ALBERT's factorized embedding parameterization and cross-layer sharing. ALR-BERT-base inherits ALBERT-base and features 12 parameter-sharing layers, a 128-dimension embedding size, 768 hidden units, 12 heads, and GELU non-linearities. Masked language modeling (MLM) and sentence order prediction (SOP) losses are the two objectives that ALBERT is pre-trained on. For ALR-BERT, we preserve both these objectives. 
The model was trained using 40 batches per GPU (for 128 sequence length) and then 20 batches per GPU (for 512 sequence length). Layer-wise Adaptive Moments optimizer for Batch (LAMB) training was utilized, with a warm-up over the first 1\% of steps up to a learning rate of 1e4, then a decay. Eight NVIDIA Tesla V100 SXM3 with 32GB memory were used, and the pre-training process took around 2 weeks per model.


Training methodology follows closely work previous done in Romanian Bert (https://huggingface.co/dumitrescustefan/bert-base-romanian-cased-v1)



### How to use

```python

from transformers import AutoTokenizer, AutoModel

import torch

# load tokenizer and model

tokenizer = AutoTokenizer.from_pretrained("dragosnicolae555/ALR_BERT")

model = AutoModel.from_pretrained("dragosnicolae555/ALR_BERT")

#Here add your magic

```

Remember to always sanitize your text! Replace ``s`` and ``t`` cedilla-letters to comma-letters with :
```
text = text.replace("ţ", "ț").replace("ş", "ș").replace("Ţ", "Ț").replace("Ş", "Ș")
```
because the model was **NOT** trained on cedilla ``s`` and ``t``s. If you don't, you will have decreased performance due to <UNK>s and increased number of tokens per word. 


### Evaluation

Here, we evaluate ALR-BERT on Simple Universal Dependencies task. One model for each task, evaluating labeling performance on the UPOS (Universal Part-of-Speech) and the XPOS (Extended Part-of-Speech) (eXtended Part-of-Speech). We compare our proposed ALR-BERT with Romanian BERT and multiligual BERT, using the cased version. To counteract the random seed effect, we repeat each experiment five times and simply provide the mean score. 




| Model                          |  UPOS |  XPOS  |  MLAS  |  AllTags  |
|--------------------------------|:-----:|:------:|:-----:|:-----:|
| M-BERT (cased)  | 93.87 | 89.89 | 90.01  | 87.04|
| Romanian BERT (cased)    |  95.56 |  95.35 |  92.78 |  93.22 | 
| ALR-BERT (cased)   |  **87.38** |  **84.05** |  **79.82** |  **78.82**| 

### Corpus 

The model is trained on the following corpora (stats in the table below are after cleaning):

| Corpus    	| Lines(M) 	| Words(M) 	| Chars(B) 	| Size(GB) 	|
|-----------	|:--------:	|:--------:	|:--------:	|:--------:	|
| OPUS      	|   55.05  	|  635.04  	|   4.045  	|    3.8   	|
| OSCAR     	|   33.56  	|  1725.82 	|  11.411  	|    11    	|
| Wikipedia 	|   1.54   	|   60.47  	|   0.411  	|    0.4   	|
| **Total**     	|   **90.15**  	|  **2421.33** 	|  **15.867**  	|   **15.2**   	|



