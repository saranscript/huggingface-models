---
language:
- fi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- fi
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-finnish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: fi
    metrics:
       - name: Test WER
         type: wer
         value: 13.72
       - name: Test CER
         type: cer
         value: 2.35
---
# sammy786/wav2vec2-xlsr-finnish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - fi dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 8.7555
- Wer: 23.0231

## Model description
"facebook/wav2vec2-xls-r-1b" was finetuned.

## Intended uses & limitations
More information needed
## Training and evaluation data
Training data - 
Common voice Finnish train.tsv, dev.tsv, invalidated.tsv and other.tsv

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


| Step | Training Loss | Validation Loss | Wer      |
|:----:|:-------------:|:---------------:|:--------:|
| 200  | 4.253700      | 0.881733        | 0.967007 |
| 400  | 0.864800      | 0.226977        | 0.420836 |
| 600  | 0.607000      | 0.157473        | 0.343375 |
| 800  | 0.380200      | 0.145640        | 0.302672 |
| 1000 | 0.318400      | 0.128028        | 0.293886 |
| 1200 | 0.261100      | 0.121414        | 0.289941 |
| 1400 | 0.232300      | 0.113451        | 0.279182 |
| 1600 | 0.216600      | 0.113649        | 0.282948 |
| 1800 | 0.202500      | 0.112375        | 0.276134 |
| 2000 | 0.190000      | 0.105725        | 0.273803 |
| 2200 | 0.171000      | 0.109715        | 0.270755 |
| 2400 | 0.156500      | 0.105042        | 0.264300 |
| 2600 | 0.155600      | 0.108337        | 0.260714 |
| 2800 | 0.149100      | 0.112435        | 0.263583 |
| 3000 | 0.145100      | 0.106193        | 0.261969 |
| 3200 | 0.131700      | 0.102860        | 0.251210 |
| 3400 | 0.129100      | 0.096058        | 0.246907 |
| 3600 | 0.121600      | 0.099932        | 0.246369 |
| 3800 | 0.112000      | 0.099041        | 0.244397 |
| 4000 | 0.114100      | 0.101566        | 0.242604 |
| 4200 | 0.111500      | 0.089498        | 0.239197 |
| 4400 | 0.099800      | 0.092835        | 0.240990 |
| 4600 | 0.095300      | 0.093518        | 0.238121 |
| 4800 | 0.094300      | 0.090783        | 0.240631 |
| 5000 | 0.089000      | 0.094046        | 0.238479 |
| 5200 | 0.088000      | 0.089342        | 0.235252 |
| 5400 | 0.083600      | 0.087770        | 0.234535 |
| 5600 | 0.083600      | 0.088804        | 0.234355 |
| 5800 | 0.080300      | 0.090168        | 0.231307 |
| 6000 | 0.078100      | 0.090163        | 0.230949 |
| 6200 | 0.075600      | 0.088876        | 0.232383 |
| 6400 | 0.078700      | 0.087235        | 0.232024 |
| 6600 | 0.074800      | 0.086825        | 0.231486 |
| 6800 | 0.076400      | 0.087308        | 0.231845 |
| 7000 | 0.070700      | 0.087695        | 0.230769 |
| 7200 | 0.075500      | 0.087555        | 0.230231 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-finnish --dataset mozilla-foundation/common_voice_8_0 --config fi --split test
```