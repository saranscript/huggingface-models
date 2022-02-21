## Acknowledgement
Google supported this work by providing Google Cloud credit. Thank you Google for supporting the open source! 🎉

## What is this?
This model is a finetuned version of [dbmdz/bert-base-turkish-cased](https://huggingface.co/dbmdz/bert-base-turkish-cased) to be used in zero-shot tasks in Turkish. It is finetuned with an NLI task by using `sentence-transformers` and uses `mean` of the token embeddings as the aggregation function. I also converted it to TensorFlow with the aggregation function rewritten in TF to use it in [my `ai-aas` repo on GitHub](https://github.com/monatis/ai-aas) for production-grade deployment, but a simple usage example is as follows:

## Usage
```python
import time
import tensorflow as tf
from transformers import TFAutoModel, AutoTokenizer

texts = ["Galatasaray, bu akşamki maçın ardından şampiyonluğunu ilan etmeye hazırlanıyor."]
labels = ["spor", "siyaset", "kültür"]
model_name = 'mys/bert-base-turkish-cased-nli-mean'

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = TFAutoModel.from_pretrained(model_name)


def label_text(model, tokenizer, texts, labels):
    texts_length = len(texts)
    tokens = tokenizer(texts + labels, padding=True, return_tensors='tf')
    embs = model(**tokens)[0]

    attention_masks = tf.cast(tokens['attention_mask'], tf.float32)
    sample_length = tf.reduce_sum(attention_masks, axis=-1, keepdims=True)
    masked_embs = embs * tf.expand_dims(attention_masks, axis=-1)
    masked_embs = tf.reduce_sum(masked_embs, axis=1) / tf.cast(sample_length, tf.float32)

    dists = tf.experimental.numpy.inner(masked_embs[:texts_length], masked_embs[texts_length:])
    scores = tf.nn.softmax(dists)
    results = list(zip(labels, scores.numpy().squeeze().tolist()))
    sorted_results = sorted(results, key=lambda x: x[1], reverse=True)
    sorted_results = [{"label": label, "score": f"{score:.4f}"} for label, score in sorted_results]
    return sorted_results


start = time.time()
sorted_results = label_text(model, tokenizer, texts, labels)
alapsed = time.time() - start

print(sorted_results)
print(f"Processed in {alapsed:.2f} secs")
```

Output:
```shell
[{'label': 'spor', 'score': '1.0000'}, {'label': 'siyaset', 'score': '0.0000'}, {'label': 'kültür', 'score': '0.0000'}]
Processed in 0.22 secs
```

## How it works
`label_text()`  function runs the BERT model with a concatenation of `texts` and `labels` as the input, and it agregates per-token hidden states outputted by the BERT model to produce a single vector per sequence. Then, the inner product of text embeddings and label embeddings is calculated as the similarity metric, and `softmax` is applied to convert these distance values to probabilities.

## Dataset
>[Emrah Budur](https://scholar.google.com/citations?user=zSNd03UAAAAJ), [Rıza Özçelik](https://www.cmpe.boun.edu.tr/~riza.ozcelik), [Tunga Güngör](https://www.cmpe.boun.edu.tr/~gungort/)  and [Christopher Potts](https://web.stanford.edu/~cgpotts). 2020. 
Data and Representation for Turkish Natural Language Inference. To appear in Proceedings of EMNLP. [[pdf]](https://arxiv.org/abs/2004.14963) [[bib]](https://tabilab.cmpe.boun.edu.tr/datasets/nli_datasets/nli-tr.bib)

```
@inproceedings{budur-etal-2020-data,
    title = "Data and Representation for Turkish Natural Language Inference",
    author = "Budur, Emrah and
      \"{O}z\c{c}elik, R{\i}za and
      G\"{u}ng\"{o}r, Tunga",
    booktitle = "Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics"
}
```