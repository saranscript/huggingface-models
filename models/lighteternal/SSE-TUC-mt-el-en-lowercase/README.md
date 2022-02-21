---
language:
- en
- el
tags:
- translation

widget:
- text: "Η τύχη βοηθάει τους τολμηρούς."
license: apache-2.0
metrics:
- bleu
---


## Greek to English NMT (lower-case output)
## By the Hellenic Army Academy (SSE) and the Technical University of Crete (TUC)

* source languages: el
* target languages: en
* licence: apache-2.0 
* dataset: Opus, CCmatrix
* model: transformer(fairseq)
* pre-processing: tokenization + BPE segmentation
* metrics: bleu, chrf 
* output: lowercase only, for mixed-cased model use this: https://huggingface.co/lighteternal/SSE-TUC-mt-el-en-cased


### Model description

Trained using the Fairseq framework, transformer_iwslt_de_en architecture.\\
BPE segmentation (10k codes).\\
Lower-case model. 

### How to use

```
from transformers import FSMTTokenizer, FSMTForConditionalGeneration

mname = " <your_downloaded_model_folderpath_here> "

tokenizer = FSMTTokenizer.from_pretrained(mname)
model = FSMTForConditionalGeneration.from_pretrained(mname)

text = "Η τύχη βοηθάει τους τολμηρούς."

encoded = tokenizer.encode(text, return_tensors='pt')

outputs = model.generate(encoded, num_beams=5, num_return_sequences=5, early_stopping=True)
for i, output in enumerate(outputs):
    i += 1
    print(f"{i}: {output.tolist()}")
    
    decoded = tokenizer.decode(output, skip_special_tokens=True)
    print(f"{i}: {decoded}")
```


## Training data

Consolidated corpus from Opus and CC-Matrix (~6.6GB in total)


## Eval results


Results on Tatoeba testset (EL-EN): 

| BLEU | chrF  |
| ------ | ------ |
| 79.3 |  0.795 |


Results on XNLI parallel (EL-EN): 

| BLEU | chrF  |
| ------ | ------ |
| 66.2 |  0.623 |

### BibTeX entry and citation info

Dimitris Papadopoulos, et al. "PENELOPIE: Enabling Open Information Extraction for the Greek Language through Machine Translation." (2021). Accepted at EACL 2021 SRW
 

### Acknowledgement

The research work was supported by the Hellenic Foundation for Research and Innovation (HFRI) under the HFRI PhD Fellowship grant (Fellowship Number:50, 2nd call)
