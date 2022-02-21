---
language:
- ba
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ba
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-bashkir
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ba
    metrics:
       - name: Test WER
         type: wer
         value: 11.32
       - name: Test CER
         type: cer
         value: 2.34
---
# sammy786/wav2vec2-xlsr-bashkir
This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ba dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 
- Wer: 
## Model description
"facebook/wav2vec2-xls-r-1b" was finetuned.
## Intended uses & limitations
More information needed
## Training and evaluation data
Training data - 
Common voice Finnish train.tsv, dev.tsv and other.tsv
## Training procedure
For creating the train dataset, all possible datasets were appended and 90-10 split was used. 
### Training hyperparameters
The following hyperparameters were used during training:
- learning_rate: 0.000045637994662983496
- train_batch_size: 16
- eval_batch_size: 16
- seed: 13
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP
### Training results
| Step | Training Loss | Validation Loss | Wer      |
|:----:|:-------------:|:---------------:|:--------:|
| 200  | 5.387100      | 1.982867        | 1.000000 |
| 400  | 1.269800      | 0.369958        | 0.545755 |
| 600  | 0.903600      | 0.287705        | 0.465594 |
| 800  | 0.787300      | 0.235142        | 0.417091 |
| 1000 | 0.816300      | 0.206325        | 0.390534 |
| 1200 | 0.700500      | 0.197106        | 0.383987 |
| 1400 | 0.707100      | 0.179855        | 0.381368 |
| 1600 | 0.657800      | 0.181605        | 0.370593 |
| 1800 | 0.647800      | 0.168626        | 0.358767 |
| 2000 | 0.650700      | 0.164833        | 0.351483 |
| 2200 | 0.490900      | 0.168133        | 0.363309 |
| 2400 | 0.431000      | 0.161201        | 0.344350 |
| 2600 | 0.372100      | 0.160254        | 0.338280 |
| 2800 | 0.367500      | 0.150885        | 0.329687 |
| 3000 | 0.351300      | 0.154112        | 0.331392 |
| 3200 | 0.314800      | 0.147147        | 0.326700 |
| 3400 | 0.316800      | 0.142681        | 0.325090 |
| 3600 | 0.313000      | 0.138736        | 0.319553 |
| 3800 | 0.291800      | 0.138166        | 0.315570 |
| 4000 | 0.311300      | 0.135977        | 0.322894 |
| 4200 | 0.304900      | 0.128820        | 0.308627 |
| 4400 | 0.301600      | 0.129475        | 0.307440 |
| 4600 | 0.281800      | 0.131863        | 0.305967 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3
#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-bashkir --dataset mozilla-foundation/common_voice_8_0 --config ba --split test
```