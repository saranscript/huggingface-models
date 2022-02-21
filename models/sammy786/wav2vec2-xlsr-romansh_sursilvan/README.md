---
language:
- rm-sursilv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- rm-sursilv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-romansh_sursilvan
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: rm-sursilv
    metrics:
       - name: Test WER
         type: wer
         value: 13.82
       - name: Test CER
         type: cer
         value: 3.02
---
# sammy786/wav2vec2-xlsr-romansh_sursilvan

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - rm-sursilv dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 16.38
- Wer: 21.25

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
- num_epochs: 40
- mixed_precision_training: Native AMP


### Training results


| Step | Training Loss | Validation Loss | Wer      |
|------|---------------|-----------------|----------|
| 200  | 4.825500      | 2.932350        | 1.000000 |
| 400  | 1.325600      | 0.292645        | 0.415436 |
| 600  | 0.709800      | 0.219167        | 0.324451 |
| 800  | 0.576800      | 0.174390        | 0.275477 |
| 1000 | 0.538100      | 0.183737        | 0.272116 |
| 1200 | 0.475200      | 0.159078        | 0.253871 |
| 1400 | 0.420400      | 0.167277        | 0.240907 |
| 1600 | 0.393500      | 0.167216        | 0.247269 |
| 1800 | 0.407500      | 0.178282        | 0.239827 |
| 2000 | 0.374400      | 0.184590        | 0.239467 |
| 2200 | 0.382600      | 0.164106        | 0.227824 |
| 2400 | 0.363100      | 0.162543        | 0.228544 |
| 2600 | 0.199000      | 0.172903        | 0.231665 |
| 2800 | 0.150800      | 0.160117        | 0.222662 |
| 3000 | 0.101100      | 0.169553        | 0.222662 |
| 3200 | 0.104200      | 0.161056        | 0.220622 |
| 3400 | 0.096900      | 0.161562        | 0.216781 |
| 3600 | 0.092200      | 0.163880        | 0.212580 |
| 3800 | 0.089200      | 0.162288        | 0.214140 |
| 4000 | 0.076200      | 0.160470        | 0.213540 |
| 4200 | 0.087900      | 0.162827        | 0.213060 |
| 4400 | 0.066200      | 0.161096        | 0.213300 |
| 4600 | 0.076000      | 0.162060        | 0.213660 |
| 4800 | 0.071400      | 0.162045        | 0.213300 |



### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-romansh_sursilvan --dataset mozilla-foundation/common_voice_8_0 --config rm-sursilv --split test
```