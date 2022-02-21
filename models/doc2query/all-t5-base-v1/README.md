---
language: en
datasets:
- sentence-transformers/reddit-title-body
- sentence-transformers/embedding-training-data
widget:
- text: "Python is an interpreted, high-level and general-purpose programming language. Python's design philosophy emphasizes code readability with its notable use of significant whitespace. Its language constructs and object-oriented approach aim to help programmers write clear, logical code for small and large-scale projects."

license: apache-2.0
---

# doc2query/all-t5-base-v1

This is a [doc2query](https://arxiv.org/abs/1904.08375) model based on T5 (also known as [docT5query](https://cs.uwaterloo.ca/~jimmylin/publications/Nogueira_Lin_2019_docTTTTTquery-v2.pdf)).

It can be used for:
- **Document expansion**: You generate for your paragraphs 20-40 queries and index the paragraphs and the generates queries in a standard BM25 index like Elasticsearch, OpenSearch, or Lucene. The generated queries help to close the lexical gap of lexical search, as the generate queries contain synonyms. Further, it re-weights words giving important words a higher weight even if they appear seldomn in a paragraph. In our [BEIR](https://arxiv.org/abs/2104.08663) paper we showed that BM25+docT5query is a powerful search engine. In the [BEIR repository](https://github.com/UKPLab/beir) we have an example how to use docT5query with Pyserini.
- **Domain Specific Training Data Generation**: It can be used to generate training data to learn an embedding model. On [SBERT.net](https://www.sbert.net/examples/unsupervised_learning/query_generation/README.html) we have an example how to use the model to generate (query, text) pairs for a given collection of unlabeled texts. These pairs can then be used to train powerful dense embedding models.

## Usage
```python
from transformers import T5Tokenizer, T5ForConditionalGeneration

model_name = 'doc2query/all-t5-base-v1'
tokenizer = T5Tokenizer.from_pretrained(model_name)
model = T5ForConditionalGeneration.from_pretrained(model_name)

text = "Python is an interpreted, high-level and general-purpose programming language. Python's design philosophy emphasizes code readability with its notable use of significant whitespace. Its language constructs and object-oriented approach aim to help programmers write clear, logical code for small and large-scale projects."


input_ids = tokenizer.encode(text, max_length=384, truncation=True, return_tensors='pt')
outputs = model.generate(
    input_ids=input_ids,
    max_length=64,
    do_sample=True,
    top_p=0.95,
    num_return_sequences=5)

print("Text:")
print(text)

print("\nGenerated Queries:")
for i in range(len(outputs)):
    query = tokenizer.decode(outputs[i], skip_special_tokens=True)
    print(f'{i + 1}: {query}')
```

**Note:** `model.generate()` is non-deterministic. It produces different queries each time you run it.

## Training
This model fine-tuned [google/t5-v1_1-base](https://huggingface.co/google/t5-v1_1-base) for 570k training steps. For the  training script, see the `train_script.py` in this repository.

The input-text was truncated to 384 word pieces. Output text was generated up to 64 word pieces. 

This model was trained on a large collection of datasets. For the exact datasets names and weights see the `data_config.json` in this repository. Most of the datasets are available at [https://huggingface.co/sentence-transformers](https://huggingface.co/sentence-transformers).

The datasets include besides others:
- (title, body) pairs from [Reddit](https://huggingface.co/datasets/sentence-transformers/reddit-title-body)
- (title, body) pairs and (title, answer) pairs from StackExchange and Yahoo Answers!
- (title, review) pairs from Amazon reviews
- (query, paragraph) pairs from MS MARCO, NQ, and GooAQ 
- (question, duplicate_question) from Quora and WikiAnswers
- (title, abstract) pairs from S2ORC

## Prefix

This model was trained **without a prefix**. In contrast to [doc2query/all-with_prefix-t5-base-v1](https://huggingface.co/doc2query/all-with_prefix-t5-base-v1) you cannot specify what type of transformation (answer2question, review2title) etc. you will have. This can lead to a mixture of output values.


