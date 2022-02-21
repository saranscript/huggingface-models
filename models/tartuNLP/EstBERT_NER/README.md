# EstBERT_NER

## Model description 

EstBERT_NER is a fine-tuned EstBERT model that can be used for Named Entity Recognition. This model was trained on the Estonian NER dataset created by [Tkachenko et al](https://www.aclweb.org/anthology/W13-2412.pdf). It can recognize three types of entities: locations (LOC), organizations (ORG) and persons (PER). 

## How to use 

You can use this model with Transformers pipeline for NER. Post-processing of results may be necessary as the model occasionally tags subword tokens as entities. 

```
from transformers import BertTokenizer, BertForTokenClassification
from transformers import pipeline

tokenizer = BertTokenizer.from_pretrained('tartuNLP/EstBERT_NER')
bertner = BertForTokenClassification.from_pretrained('tartuNLP/EstBERT_NER')

nlp = pipeline("ner", model=bertner, tokenizer=tokenizer)
sentence = 'Eesti Ekspressi teada on Eesti Pank uurinud Hansapanga tehinguid , mis toimusid kaks aastat tagasi suvel ja mille käigus voolas panka ligi miljardi krooni ulatuses kahtlast raha .'

ner_results = nlp(sentence)
print(ner_results)
```
```
[{'word': 'Eesti', 'score': 0.9964128136634827, 'entity': 'B-ORG', 'index': 1}, {'word': 'Ekspressi', 'score': 0.9978809356689453, 'entity': 'I-ORG', 'index': 2}, {'word': 'Eesti', 'score': 0.9988121390342712, 'entity': 'B-ORG', 'index': 5}, {'word': 'Pank', 'score': 0.9985784292221069, 'entity': 'I-ORG', 'index': 6}, {'word': 'Hansapanga', 'score': 0.9979034662246704, 'entity': 'B-ORG', 'index': 8}]

```



## BibTeX entry and citation info

```
@misc{tanvir2020estbert,
      title={EstBERT: A Pretrained Language-Specific BERT for Estonian}, 
      author={Hasan Tanvir and Claudia Kittask and Kairit Sirts},
      year={2020},
      eprint={2011.04784},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```