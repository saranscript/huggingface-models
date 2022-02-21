---
language:
- mn
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- mn
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-mongolian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: mn
    metrics:
       - name: Test WER
         type: wer
         value: 32.63
       - name: Test CER
         type: cer
         value: 9.26
---
# sammy786/wav2vec2-xlsr-mongolian
This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - mn dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 31.52
- Wer: 34.1522
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
| 200  | 4.906200      | 3.012986        | 1.000000 |
| 400  | 1.734600      | 0.704821        | 0.750497 |
| 600  | 1.132100      | 0.496223        | 0.531241 |
| 800  | 0.929300      | 0.468937        | 0.469043 |
| 1000 | 0.772300      | 0.425313        | 0.448168 |
| 1200 | 0.623900      | 0.394633        | 0.414229 |
| 1400 | 0.512400      | 0.369225        | 0.397614 |
| 1600 | 0.439900      | 0.346033        | 0.391650 |
| 1800 | 0.391300      | 0.358454        | 0.379296 |
| 2000 | 0.377000      | 0.346822        | 0.359415 |
| 2200 | 0.347500      | 0.325205        | 0.348481 |
| 2400 | 0.343600      | 0.315233        | 0.344078 |
| 2600 | 0.328000      | 0.308826        | 0.341522 |
| 2800 | 0.358200      | 0.331786        | 0.343084 |
| 3000 | 0.417200      | 0.370051        | 0.356433 |
| 3200 | 0.685300      | 0.595438        | 0.407413 |
| 3400 | 0.764100      | 0.643449        | 0.359983 |
| 3600 | 0.717100      | 0.505033        | 0.371911 |
| 3800 | 0.620900      | 0.464138        | 0.369071 |
| 4000 | 0.590700      | 0.445417        | 0.363249 |
| 4200 | 0.561000      | 0.440727        | 0.360267 |
| 4400 | 0.550600      | 0.447122        | 0.360267 |
| 4600 | 0.562100      | 0.457020        | 0.359841 |
| 4800 | 0.578800      | 0.470477        | 0.360551 |
| 5000 | 0.580400      | 0.481413        | 0.362539 |
| 5200 | 0.605500      | 0.485240        | 0.362823 |
| 5400 | 0.582900      | 0.486654        | 0.362965 |
| 5600 | 0.593900      | 0.486715        | 0.363107 |
| 5800 | 0.590900      | 0.486716        | 0.363107 |
| 6000 | 0.587200      | 0.486716        | 0.363107 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3
#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-mongolian --dataset mozilla-foundation/common_voice_8_0 --config mn --split test
```