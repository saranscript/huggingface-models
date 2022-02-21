# SVALabs - German Uncased Electra Cross-Encoder

In this repository, we present our german, uncased cross-encoder for Passage Retrieval.

This model was trained on the basis of the german electra uncased model from the [german-nlp-group](https://huggingface.co/german-nlp-group/electra-base-german-uncased) and finetuned as a cross-encoder for Passage Retrieval using the [sentence-transformers](https://github.com/UKPLab/sentence-transformers) package.
For this purpose, we translated the [MSMARCO-Passage-Ranking](https://github.com/microsoft/MSMARCO-Passage-Ranking) dataset using the [fairseq-wmt19-en-de](https://github.com/pytorch/fairseq/tree/master/examples/wmt19) translation model.

### Model Details

| | Description or Link  |
|---|---|
|**Base model**   | [```german-nlp-group/electra-base-german-uncased```](https://huggingface.co/german-nlp-group/electra-base-german-uncased)  |
|**Finetuning task**| Passage Retrieval / Semantic Search  |
|**Source dataset**| [```MSMARCO-Passage-Ranking```](https://github.com/microsoft/MSMARCO-Passage-Ranking)  |
|**Translation model**|  [```fairseq-wmt19-en-de```](https://github.com/pytorch/fairseq/tree/master/examples/wmt19)  |

### Performance

We evaluated our model on the [GermanDPR testset](https://deepset.ai/germanquad) and followed the benchmark framework of [BEIR](https://github.com/UKPLab/beir).
In order to compare our results, we conducted an evaluation on the same test data with BM25 and presented the results in the table below.
We took every paragraph with negative and positive context out of the testset and deduplicated them. The resulting corpus size is 2871 against 1025 queries.

| Model               | NDCG@1 | NDCG@5 | NDCG@10 | Recall@1 | Recall@5 | Recall@10 |
|:-------------------:|:------:|:------:|:-------:|:--------:|:--------:|:---------:|
| BM25                | 0.1463 | 0.3451 | 0.4097  | 0.1463   | 0.5424   | 0.7415    |
| BM25(Top 100) +Ours | 0.6410 | 0.7885 | 0.7943  | 0.6410   | 0.8576   | 0.9024    |

### How to Use

With ```sentence-transformers``` package (see [UKPLab/sentence-transformers](https://github.com/UKPLab/sentence-transformers) on GitHub for more details):
```python
from sentence_transformers.cross_encoder import CrossEncoder

cross_model = CrossEncoder("svalabs/cross-electra-ms-marco-german-uncased")
```

### Semantic Search Example
```python
import numpy as np
from sklearn.metrics.pairwise import cosine_similarity

K = 3 # number of top ranks to retrieve

docs = [
    "Auf Netflix gibt es endlich die neue Staffel meiner Lieblingsserie.",
    "Der Gepard jagt seine Beute.",
    "Wir haben in der Agentur ein neues System für Zeiterfassung.",
    "Mein Arzt sagt, dass mir dabei eher ein Orthopäde helfen könnte.",
    "Einen Impftermin kann mir der Arzt momentan noch nicht anbieten.",
    "Auf Kreta hat meine Tochter mit Muscheln eine schöne Sandburg gebaut.",
    "Das historische Zentrum (centro storico) liegt auf mehr als 100 Inseln in der Lagune von Venedig.",
    "Um in Zukunft sein Vermögen zu schützen, sollte man andere Investmentstrategien in Betracht ziehen.",
    "Die Ära der Dinosaurier wurde vermutlich durch den Einschlag eines gigantischen Meteoriten auf der Erde beendet.",
    "Bei ALDI sind die Bananen gerade im Angebot.",
    "Die Entstehung der Erde ist 4,5 milliarden jahre her.",
    "Finanzwerte treiben DAX um mehr als sechs Prozent nach oben Frankfurt/Main gegeben.",
    "DAX dreht ins Minus. Konjunkturdaten und Gewinnmitnahmen belasten Frankfurt/Main."
]

queries = [
    "dax steigt",
    "dax sinkt",
    "probleme mit knieschmerzen",
    "software für urlaubsstunden",
    "raubtier auf der jagd",
    "alter der erde",
    "wie alt ist unser planet?",
    "wie kapital sichern",
    "supermarkt lebensmittel reduziert",
    "wodurch ist der tyrannosaurus aussgestorben",
    "serien streamen"
]

# encode each query document pair
from itertools import product
combs = list(product(queries, docs))
outputs = cross_model.predict(combs).reshape((len(queries), len(docs)))

# print results
for i, query in enumerate(queries):
    ranks = np.argsort(-outputs[i])
    print("Query:", query)
    for j, r in enumerate(ranks[:3]):
        print(f"[{j}: {outputs[i, r]: .3f}]", docs[r])
    print("-"*96)

```

**Console Output**:
```
Query: dax steigt
[0:  7.676] Finanzwerte treiben DAX um mehr als sechs Prozent nach oben Frankfurt/Main gegeben.
[1:  0.821] DAX dreht ins Minus. Konjunkturdaten und Gewinnmitnahmen belasten Frankfurt/Main.
[2: -9.905] Um in Zukunft sein Vermögen zu schützen, sollte man andere Investmentstrategien in Betracht ziehen.
------------------------------------------------------------------------------------------------
Query: dax sinkt
[0:  8.079] DAX dreht ins Minus. Konjunkturdaten und Gewinnmitnahmen belasten Frankfurt/Main.
[1: -0.491] Finanzwerte treiben DAX um mehr als sechs Prozent nach oben Frankfurt/Main gegeben.
[2: -9.224] Um in Zukunft sein Vermögen zu schützen, sollte man andere Investmentstrategien in Betracht ziehen.
------------------------------------------------------------------------------------------------
Query: probleme mit knieschmerzen
[0:  6.753] Mein Arzt sagt, dass mir dabei eher ein Orthopäde helfen könnte.
[1: -5.866] Einen Impftermin kann mir der Arzt momentan noch nicht anbieten.
[2: -9.461] Auf Kreta hat meine Tochter mit Muscheln eine schöne Sandburg gebaut.
------------------------------------------------------------------------------------------------
Query: software für urlaubsstunden
[0:  1.707] Wir haben in der Agentur ein neues System für Zeiterfassung.
[1: -10.649] Mein Arzt sagt, dass mir dabei eher ein Orthopäde helfen könnte.
[2: -11.280] DAX dreht ins Minus. Konjunkturdaten und Gewinnmitnahmen belasten Frankfurt/Main.
------------------------------------------------------------------------------------------------
Query: raubtier auf der jagd
[0:  4.596] Der Gepard jagt seine Beute.
[1: -6.809] Auf Netflix gibt es endlich die neue Staffel meiner Lieblingsserie.
[2: -8.392] Das historische Zentrum (centro storico) liegt auf mehr als 100 Inseln in der Lagune von Venedig.
------------------------------------------------------------------------------------------------
Query: alter der erde
[0:  7.343] Die Entstehung der Erde ist 4,5 milliarden jahre her.
[1: -7.664] Die Ära der Dinosaurier wurde vermutlich durch den Einschlag eines gigantischen Meteoriten auf der Erde beendet.
[2: -8.020] Das historische Zentrum (centro storico) liegt auf mehr als 100 Inseln in der Lagune von Venedig.
------------------------------------------------------------------------------------------------
Query: wie alt ist unser planet?
[0:  7.672] Die Entstehung der Erde ist 4,5 milliarden jahre her.
[1: -9.638] Die Ära der Dinosaurier wurde vermutlich durch den Einschlag eines gigantischen Meteoriten auf der Erde beendet.
[2: -10.251] Auf Kreta hat meine Tochter mit Muscheln eine schöne Sandburg gebaut.
------------------------------------------------------------------------------------------------
Query: wie kapital sichern
[0:  3.927] Um in Zukunft sein Vermögen zu schützen, sollte man andere Investmentstrategien in Betracht ziehen.
[1: -8.733] Finanzwerte treiben DAX um mehr als sechs Prozent nach oben Frankfurt/Main gegeben.
[2: -10.090] Mein Arzt sagt, dass mir dabei eher ein Orthopäde helfen könnte.
------------------------------------------------------------------------------------------------
Query: supermarkt lebensmittel reduziert
[0:  3.508] Bei ALDI sind die Bananen gerade im Angebot.
[1: -10.057] Das historische Zentrum (centro storico) liegt auf mehr als 100 Inseln in der Lagune von Venedig.
[2: -10.470] DAX dreht ins Minus. Konjunkturdaten und Gewinnmitnahmen belasten Frankfurt/Main.
------------------------------------------------------------------------------------------------
Query: wodurch ist der tyrannosaurus aussgestorben
[0:  0.079] Die Ära der Dinosaurier wurde vermutlich durch den Einschlag eines gigantischen Meteoriten auf der Erde beendet.
[1: -10.701] Mein Arzt sagt, dass mir dabei eher ein Orthopäde helfen könnte.
[2: -11.200] Auf Netflix gibt es endlich die neue Staffel meiner Lieblingsserie.
------------------------------------------------------------------------------------------------
Query: serien streamen
[0:  3.392] Auf Netflix gibt es endlich die neue Staffel meiner Lieblingsserie.
[1: -5.725] Der Gepard jagt seine Beute.
[2: -8.378] Auf Kreta hat meine Tochter mit Muscheln eine schöne Sandburg gebaut.
------------------------------------------------------------------------------------------------
```

### Contact
- Baran Avinc, baran.avinc@sva.de
- Jonas Grebe, jonas.grebe@sva.de
- Lisa Stolz, lisa.stolz@sva.de
- Bonian Riebe, bonian.riebe@sva.de

### References
- N. Reimers and I. Gurevych (2019), ['Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks'](https://arxiv.org/abs/1908.10084).
- Payal Bajaj et al. (2018), ['MS MARCO: A Human Generated MAchine Reading COmprehension Dataset'](https://arxiv.org/abs/1611.09268).
- N. Thakur et al. (2021), ['BEIR: A Heterogenous Benchmark for Zero-shot Evaluation of Information Retrieval Models'](https://arxiv.org/abs/2104.08663).
-  T. Möller, J. Risch and M. Pietsch (2021), ['GermanQuAD and GermanDPR: Improving Non-English Question Answering and Passage Retrieval'](https://arxiv.org/abs/2104.12741).
- Hofstätter et al. (2021), ['Improving Efficient Neural Ranking Models with Cross-Architecture Knowledge Distillation'](https://arxiv.org/abs/2010.02666)
