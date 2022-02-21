---
license: apache-2.0
language:
- ja
tags:
- automatic-speech-recognition
- robust-speech-event
- common-voice
- ja
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec2-xls-r-1b
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7.0
      type: mozilla-foundation/common_voice_7_0
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 7.98
       - name: Test CER (with LM)
         type: cer
         value: 3.42
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8.0
      type: mozilla-foundation/common_voice_8_0
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 7.88
       - name: Test CER (with LM)
         type: cer
         value: 3.35
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 28.07
       - name: Test CER (with LM)
         type: cer
         value: 16.27 
---
## Model description

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on my collection of Public Japanese Voice datasets for research [Common Voice 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0), [JUST](https://sites.google.com/site/shinnosuketakamichi/publication/jsut) (Japanese speech corpus of Saruwatari-lab., University of Tokyo), [JSSS](https://sites.google.com/site/shinnosuketakamichi/research-topics/jsss_corpus) (Japanese speech corpus for summarization and simplification), [CSS10](https://paperswithcode.com/dataset/css10) (A collection of single speaker speech datasets). You can find in preprocessing dataset in here VUMICHIEN/COMMON_VOICE_LARGE_JSUT_JSSS_CSS10. 

### Total training data:
~60 hours

### Benchmark WER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 10.96 | 10.91 |
|with 4-grams LM| 7.98 | 7.88 |
### Benchmark CER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 4.28 | 4.22 |
|with 4-grams LM| 3.42 | 3.35 |
## Evaluation
Please use the eval.py file to run the evaluation:
```python
pip install mecab-python3 unidic-lite pykakasi
python eval.py --model_id vumichien/wav2vec2-xls-r-1b-japanese --dataset mozilla-foundation/common_voice_7_0 --config ja --split test --log_outputs
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 2.2896        | 3.37  | 1500  | 0.4748          | 0.4013 | 0.1767 |
| 1.1608        | 6.74  | 3000  | 0.3350          | 0.3159 | 0.1456 |
| 1.1042        | 10.11 | 4500  | 0.3119          | 0.2971 | 0.1400 |
| 1.0494        | 13.48 | 6000  | 0.2974          | 0.2867 | 0.1353 |
| 1.0061        | 16.85 | 7500  | 0.2802          | 0.2746 | 0.1300 |
| 0.9629        | 20.22 | 9000  | 0.2844          | 0.2776 | 0.1326 |
| 0.9267        | 23.59 | 10500 | 0.2577          | 0.2603 | 0.1255 |
| 0.8984        | 26.96 | 12000 | 0.2508          | 0.2531 | 0.1226 |
| 0.8729        | 30.34 | 13500 | 0.2629          | 0.2606 | 0.1254 |
| 0.8546        | 33.71 | 15000 | 0.2402          | 0.2447 | 0.1193 |
| 0.8304        | 37.08 | 16500 | 0.2532          | 0.2472 | 0.1209 |
| 0.8075        | 40.45 | 18000 | 0.2439          | 0.2469 | 0.1198 |
| 0.7827        | 43.82 | 19500 | 0.2387          | 0.2372 | 0.1167 |
| 0.7627        | 47.19 | 21000 | 0.2344          | 0.2331 | 0.1147 |
| 0.7402        | 50.56 | 22500 | 0.2314          | 0.2299 | 0.1135 |
| 0.718         | 53.93 | 24000 | 0.2257          | 0.2267 | 0.1114 |
| 0.7016        | 57.3  | 25500 | 0.2204          | 0.2184 | 0.1089 |
| 0.6804        | 60.67 | 27000 | 0.2227          | 0.2181 | 0.1085 |
| 0.6625        | 64.04 | 28500 | 0.2138          | 0.2112 | 0.1058 |
| 0.6465        | 67.42 | 30000 | 0.2141          | 0.2081 | 0.1044 |
| 0.6238        | 70.79 | 31500 | 0.2172          | 0.2082 | 0.1050 |
| 0.6062        | 74.16 | 33000 | 0.2174          | 0.2058 | 0.1043 |
| 0.588         | 77.53 | 34500 | 0.2156          | 0.2034 | 0.1027 |
| 0.5722        | 80.9  | 36000 | 0.2162          | 0.2032 | 0.1029 |
| 0.5585        | 84.27 | 37500 | 0.2156          | 0.2022 | 0.1021 |
| 0.5456        | 87.64 | 39000 | 0.2126          | 0.1993 | 0.1009 |
| 0.5325        | 91.01 | 40500 | 0.2121          | 0.1966 | 0.1003 |
| 0.5229        | 94.38 | 42000 | 0.2104          | 0.1941 | 0.0991 |
| 0.5134        | 97.75 | 43500 | 0.2108          | 0.1948 | 0.0992 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
