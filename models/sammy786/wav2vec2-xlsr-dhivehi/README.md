---
language:
- dv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- dv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-dhivehi
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: dv
    metrics:
       - name: Test WER
         type: wer
         value: 26.91
       - name: Test CER
         type: cer
         value: 4.02
  
---
# sammy786/wav2vec2-xlsr-dhivehi

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - dv dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 14.86
- Wer: 29.32

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
- train_batch_size: 8
- eval_batch_size: 16
- seed: 13
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP


### Training results

| Step  | Training Loss | Validation Loss | Wer      |
|-------|---------------|-----------------|----------|
| 200   | 4.883800      | 3.190218        | 1.000000 |
| 400   | 1.600100      | 0.497887        | 0.726159 |
| 600   | 0.928500      | 0.358781        | 0.603892 |
| 800   | 0.867900      | 0.309132        | 0.570786 |
| 1000  | 0.743100      | 0.309116        | 0.552954 |
| 1200  | 0.725100      | 0.266839        | 0.538378 |
| 1400  | 0.786200      | 0.259797        | 0.535897 |
| 1600  | 0.655700      | 0.245691        | 0.517290 |
| 1800  | 0.650500      | 0.246957        | 0.516204 |
| 2000  | 0.685500      | 0.234808        | 0.516204 |
| 2200  | 0.487100      | 0.228409        | 0.507753 |
| 2400  | 0.401300      | 0.221087        | 0.495968 |
| 2600  | 0.359300      | 0.212476        | 0.489301 |
| 2800  | 0.347300      | 0.204848        | 0.487750 |
| 3000  | 0.327000      | 0.203163        | 0.478756 |
| 3200  | 0.337100      | 0.210235        | 0.487595 |
| 3400  | 0.308900      | 0.201471        | 0.491316 |
| 3600  | 0.292600      | 0.192437        | 0.476120 |
| 3800  | 0.289600      | 0.198398        | 0.468445 |
| 4000  | 0.290200      | 0.193484        | 0.467204 |
| 4200  | 0.272600      | 0.193999        | 0.470150 |
| 4400  | 0.266700      | 0.187384        | 0.460769 |
| 4600  | 0.253800      | 0.187279        | 0.476663 |
| 4800  | 0.266400      | 0.197395        | 0.466817 |
| 5000  | 0.258000      | 0.188920        | 0.456660 |
| 5200  | 0.237200      | 0.180770        | 0.457358 |
| 5400  | 0.237900      | 0.178149        | 0.448287 |
| 5600  | 0.232600      | 0.179827        | 0.461002 |
| 5800  | 0.228500      | 0.182142        | 0.445185 |
| 6000  | 0.221000      | 0.173619        | 0.440688 |
| 6200  | 0.219500      | 0.172291        | 0.442859 |
| 6400  | 0.219400      | 0.173339        | 0.430609 |
| 6600  | 0.201900      | 0.177552        | 0.426423 |
| 6800  | 0.199000      | 0.173157        | 0.429834 |
| 7000  | 0.200000      | 0.166503        | 0.423709 |
| 7200  | 0.194600      | 0.171812        | 0.429834 |
| 7400  | 0.192100      | 0.164989        | 0.420530 |
| 7600  | 0.185000      | 0.168355        | 0.418825 |
| 7800  | 0.175100      | 0.168128        | 0.419290 |
| 8000  | 0.173500      | 0.167959        | 0.424950 |
| 8200  | 0.172200      | 0.173643        | 0.414793 |
| 8400  | 0.164200      | 0.167020        | 0.406342 |
| 8600  | 0.170800      | 0.168050        | 0.405334 |
| 8800  | 0.157900      | 0.164290        | 0.396573 |
| 9000  | 0.159900      | 0.163188        | 0.397426 |
| 9200  | 0.151700      | 0.164370        | 0.390991 |
| 9400  | 0.146600      | 0.165053        | 0.392852 |
| 9600  | 0.142200      | 0.164939        | 0.391844 |
| 9800  | 0.148300      | 0.164422        | 0.385719 |
| 10000 | 0.136200      | 0.166569        | 0.385951 |
| 10200 | 0.140700      | 0.161377        | 0.379594 |
| 10400 | 0.133300      | 0.165194        | 0.378276 |
| 10600 | 0.131300      | 0.164328        | 0.369205 |
| 10800 | 0.135500      | 0.160254        | 0.373236 |
| 11000 | 0.121100      | 0.163522        | 0.372693 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-dhivehi --dataset mozilla-foundation/common_voice_8_0 --config dv --split test
```