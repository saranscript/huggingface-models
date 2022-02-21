---
tags:
- generated_from_keras_callback
- dpr
license: apache-2.0
model-index:
- name: dpr-ctx_encoder_bert_uncased_L-12_H-128_A-2
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# dpr-ctx_encoder_bert_uncased_L-2_H-128_A-2

This model(google/bert_uncased_L-2_H-128_A-2) was trained from scratch on training data: data.retriever.nq-adv-hn-train(facebookresearch/DPR).
It achieves the following results on the evaluation set:


## Evaluation data

evaluation dataset: facebook-dpr-dev-dataset from official DPR github

|model_name|data_name|num of queries|num of passages|R@10|R@20|R@50|R@100|R@100|
|---|---|---|---|---|---|---|---|---|
|nlpconnect/dpr-ctx_encoder_bert_uncased_L-2_H-128_A-2(our)|nq-dev dataset|6445|199795|60.53%|68.28%|76.07%|80.98%|91.45%|
|nlpconnect/dpr-ctx_encoder_bert_uncased_L-12_H-128_A-2(our)|nq-dev dataset|6445|199795|65.43%|71.99%|79.03%|83.24%|92.11%|
|*facebook/dpr-ctx_encoder-single-nq-base(hf/fb)|nq-dev dataset|6445|199795|40.94%|49.27%|59.05%|66.00%|82.00%|

evaluation dataset: UKPLab/beir test data but we have used first 2lac passage only. 

|model_name|data_name|num of queries|num of passages|R@10|R@20|R@50|R@100|R@100|
|---|---|---|---|---|---|---|---|---|
|nlpconnect/dpr-ctx_encoder_bert_uncased_L-2_H-128_A-2(our)|nq-test dataset|3452|200001|49.68%|59.06%|69.40%|75.75%|89.28%|
|nlpconnect/dpr-ctx_encoder_bert_uncased_L-12_H-128_A-2(our)|nq-test dataset|3452|200001|51.62%|61.09%|70.10%|76.07%|88.70%|
|*facebook/dpr-ctx_encoder-single-nq-base(hf/fb)|nq-test dataset|3452|200001|32.93%|43.74%|56.95%|66.30%|83.92%|

Note: * means we have evaluated on same eval dataset.

### Usage (HuggingFace Transformers)

```python

passage_encoder = TFAutoModel.from_pretrained("nlpconnect/dpr-ctx_encoder_bert_uncased_L-12_H-128_A-2")
query_encoder = TFAutoModel.from_pretrained("nlpconnect/dpr-question_encoder_bert_uncased_L-12_H-128_A-2")

p_tokenizer = AutoTokenizer.from_pretrained("nlpconnect/dpr-ctx_encoder_bert_uncased_L-12_H-128_A-2")
q_tokenizer = AutoTokenizer.from_pretrained("nlpconnect/dpr-question_encoder_bert_uncased_L-12_H-128_A-2")

def get_title_text_combined(passage_dicts):
    res = []
    for p in passage_dicts:
        res.append(tuple((p['title'], p['text'])))
    return res
    
processed_passages = get_title_text_combined(passage_dicts)

def extracted_passage_embeddings(processed_passages, model_config):
    passage_inputs = tokenizer.batch_encode_plus(
                    processed_passages,
                    add_special_tokens=True,
                    truncation=True,
                    padding="max_length",
                    max_length=model_config.passage_max_seq_len,
                    return_token_type_ids=True
                )
    passage_embeddings = passage_encoder.predict([np.array(passage_inputs['input_ids']), 
                                                np.array(passage_inputs['attention_mask']), 
                                                np.array(passage_inputs['token_type_ids'])], 
                                                batch_size=512, 
                                                verbose=1)
    return passage_embeddings
    
passage_embeddings = extracted_passage_embeddings(processed_passages, model_config)


def extracted_query_embeddings(queries, model_config):
    query_inputs = tokenizer.batch_encode_plus(
                    queries,
                    add_special_tokens=True,
                    truncation=True,
                    padding="max_length",
                    max_length=model_config.query_max_seq_len,
                    return_token_type_ids=True
                )
    query_embeddings = query_encoder.predict([np.array(query_inputs['input_ids']), 
                                                np.array(query_inputs['attention_mask']), 
                                                np.array(query_inputs['token_type_ids'])], 
                                                batch_size=512, 
                                                verbose=1)
    return query_embeddings
    

query_embeddings = extracted_query_embeddings(queries, model_config)

```

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: None
- training_precision: float32

### Framework versions

- Transformers 4.15.0
- TensorFlow 2.7.0
- Tokenizers 0.10.3
