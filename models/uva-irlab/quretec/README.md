---
language:
- en
tags:
- conversational-search  # Example: audio
metrics:
- f1
datasets:
- uva-irlab/canard_quretec
model-index:  
- name: QuReTec
  results:
  - task: 
      name: Conversational search  # Example: Speech Recognition
      type: conversational  # Example: automatic-speech-recognition
    dataset:
      name: CANARD  # Example: Common Voice zh-CN
      type: canard  # Example: common_voice
    metrics:
      - name: Micro F1  # Example: Test WER
        type: f1  # Example: wer
        value: 68.7  # Example: 20.90
      - name: Micro Recall
        type: recall
        value: 66.1
      - name: Micro Precision
        type: precision
        value: 71.5
---

# QuReTec: query resolution model

QuReTeC is a query resolution model. It finds the relevant terms in a question history.
It is based on **bert-large-uncased** with a max sequence length of 300.

# Config details
Training and evaluation was done using the following BertConfig:

```json
BertConfig {
  "_name_or_path": "uva-irlab/quretec",
  "architectures": ["BertForMaskedLM"],
  "attention_probs_dropout_prob": 0.1,
  "finetuning_task": "ner",
  "gradient_checkpointing": false,
  "hidden_act": "gelu",
  "hidden_dropout_prob": 0.4,
  "hidden_size": 1024,
  "id2label": {
    "0": "[PAD]",
    "1": "O",
    "2": "REL",
    "3": "[CLS]",
    "4": "[SEP]"
  },
  "initializer_range": 0.02,
  "intermediate_size": 4096,
  "label2id": {
    "O": 1,
    "REL": 2,
    "[CLS]": 3,
    "[PAD]": 0,
    "[SEP]": 4
  },
  "layer_norm_eps": 1e-12,
  "max_position_embeddings": 512,
  "model_type": "bert",
  "num_attention_heads": 16,
  "num_hidden_layers": 24,
  "pad_token_id": 0,
  "position_embedding_type": "absolute",
  "transformers_version": "4.6.1",
  "type_vocab_size": 2,
  "use_cache": true,
  "vocab_size": 30522
}
```

# Original authors

QuReTeC model from the published SIGIR 2020 paper: Query Resolution for Conversational Search with Limited Supervision by N. Voskarides, D. Li, P. Ren, E. Kanoulas and M. de Rijke. [[pdf]](https://arxiv.org/abs/2005.11723). 

# Contributions

Uploaded by G. Scheuer ([website](https://giguruscheuer.com))