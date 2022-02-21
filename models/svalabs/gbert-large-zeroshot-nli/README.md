---

language: German

tags:

- text-classification

- pytorch

- nli

- de


pipeline_tag: zero-shot-classification

widget:

- text: "Ich habe ein Problem mit meinem Iphone das so schnell wie möglich gelöst werden muss."

  candidate_labels: "Computer, Handy, Tablet, dringend, nicht dringend"

  hypothesis_template: "In diesem Satz geht es um das Thema {}."

---


# SVALabs - Gbert Large Zeroshot Nli  

In this repository, we present our German zeroshot classification model. 

This model was trained on the basis of the German BERT large model from [deepset.ai](https://huggingface.co/deepset/gbert-large) and finetuned for natural language inference based on 847.862 machine-translated nli sentence pairs, using the [mnli](https://huggingface.co/datasets/multi_nli), [anli](https://huggingface.co/datasets/anli) and [snli](https://huggingface.co/datasets/snli) datasets. For this purpose, we translated the sentence pairs in these datasets to German.

If you are a German speaker you may also have a look at our [Blog post](https://focus.sva.de/zeroshot-klassifikation/) about this model and about Zeroshot Classification. 

### Model Details

| | Description or Link  |
|---|---|
|**Base model**   | [```gbert-large```](https://huggingface.co/deepset/gbert-large) |
|**Finetuning task**| Text Pair Classification / Natural Language Inference  |
|**Source datasets**| [```mnli```](https://huggingface.co/datasets/multi_nli); [```anli```](https://huggingface.co/datasets/anli); [```snli```](https://huggingface.co/datasets/snli)   |

### Performance

We evaluated our model for the nli task using the TEST set of the German part of the [xnli](https://huggingface.co/datasets/xnli) dataset.

XNLI TEST-Set Accuracy: 85.6% 


### Zeroshot Text Classification Task Benchmark 

We further tested our model for a zeroshot text classification task using a part of the [10kGNAD Dataset](https://tblock.github.io/10kGNAD/).
Specifically, we used all articles that were labeled "Kultur", "Sport", "Web", "Wirtschaft" and "Wissenschaft". 

The next table shows the results as well as a comparison with other German language and multilanguage zeroshot options performing the same task: 

| Model               | Accuracy |
|:-------------------:|:------:|
| Svalabs/gbert-large-zeroshot-nli     | 0.81 |
| Sahajtomar/German_Zeroshot | 0.76 |
| Symanto/xlm-roberta-base-snli-mnli-anli-xnli | 0.16 |
| Deepset/gbert-base | 0.65 |


### How to use 

The simplest way to use the model is the huggingface transformers pipeline tool. 
Just initialize the pipeline specifying the task as "zero-shot-classification" 
and select "svalabs/gbert-large-zeroshot-nli" as model. 

The model requires you to specify labels, 
a sequence (or list of sequences) to classify and a hypothesis template. 
In our tests, if the labels comprise only single words, 
"In diesem Satz geht es um das Thema {}" performed the best. 

However, for multiple words, especially when they combine nouns and verbs,
simple hypothesis such as "Weil {}" or "Daher {}" may work better. 

Here is an example of how to use the model:  

```python

from transformers import pipeline

zershot_pipeline = pipeline("zero-shot-classification",
                             model="svalabs/gbert-large-zeroshot-nli")

sequence = "Ich habe ein Problem mit meinem Iphone das so schnell wie möglich gelöst werden muss" 
labels = ["Computer", "Handy", "Tablet", "dringend", "nicht dringend"] 
hypothesis_template = "In diesem Satz geht es um das Thema {}."    


zershot_pipeline(sequence, labels, hypothesis_template=hypothesis_template)

```

### Contact
- Daniel Ehnes, daniel.ehnes@sva.de
- Baran Avinc, baran.avinc@sva.de
