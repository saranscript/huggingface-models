---
language:
- tt
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- tt
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-tatar
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: tt
    metrics:
       - name: Test WER
         type: wer
         value: 16.87
       - name: Test CER
         type: cer
         value: 3.64
---
# sammy786/wav2vec2-xlsr-tatar

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - tt dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 7.66
- Wer: 7.08

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


| Step  | Training Loss | Validation Loss | Wer      |
|-------|---------------|-----------------|----------|
| 200   | 4.849400      | 1.874908        | 0.995232 |
| 400   | 1.105700      | 0.257292        | 0.367658 |
| 600   | 0.723000      | 0.181150        | 0.250513 |
| 800   | 0.660600      | 0.167009        | 0.226078 |
| 1000  | 0.568000      | 0.135090        | 0.177339 |
| 1200  | 0.721200      | 0.117469        | 0.166413 |
| 1400  | 0.416300      | 0.115142        | 0.153765 |
| 1600  | 0.346000      | 0.105782        | 0.153963 |
| 1800  | 0.279700      | 0.102452        | 0.146149 |
| 2000  | 0.273800      | 0.095818        | 0.128468 |
| 2200  | 0.252900      | 0.102302        | 0.133766 |
| 2400  | 0.255100      | 0.096592        | 0.121316 |
| 2600  | 0.229600      | 0.091263        | 0.124561 |
| 2800  | 0.213900      | 0.097748        | 0.125687 |
| 3000  | 0.210700      | 0.091244        | 0.125422 |
| 3200  | 0.202600      | 0.084076        | 0.106284 |
| 3400  | 0.200900      | 0.093809        | 0.113238 |
| 3600  | 0.192700      | 0.082918        | 0.108139 |
| 3800  | 0.182000      | 0.084487        | 0.103371 |
| 4000  | 0.167700      | 0.091847        | 0.104960 |
| 4200  | 0.183700      | 0.085223        | 0.103040 |
| 4400  | 0.174400      | 0.083862        | 0.100589 |
| 4600  | 0.163100      | 0.086493        | 0.099728 |
| 4800  | 0.162000      | 0.081734        | 0.097543 |
| 5000  | 0.153600      | 0.077223        | 0.092974 |
| 5200  | 0.153700      | 0.086217        | 0.090789 |
| 5400  | 0.140200      | 0.093256        | 0.100457 |
| 5600  | 0.142900      | 0.086903        | 0.097742 |
| 5800  | 0.131400      | 0.083068        | 0.095225 |
| 6000  | 0.126000      | 0.086642        | 0.091252 |
| 6200  | 0.135300      | 0.083387        | 0.091186 |
| 6400  | 0.126100      | 0.076479        | 0.086352 |
| 6600  | 0.127100      | 0.077868        | 0.086153 |
| 6800  | 0.118000      | 0.083878        | 0.087676 |
| 7000  | 0.117600      | 0.085779        | 0.091054 |
| 7200  | 0.113600      | 0.084197        | 0.084233 |
| 7400  | 0.112000      | 0.078688        | 0.081319 |
| 7600  | 0.110200      | 0.082534        | 0.086087 |
| 7800  | 0.106400      | 0.077245        | 0.080988 |
| 8000  | 0.102300      | 0.077497        | 0.079332 |
| 8200  | 0.109500      | 0.079083        | 0.088339 |
| 8400  | 0.095900      | 0.079721        | 0.077809 |
| 8600  | 0.094700      | 0.079078        | 0.079730 |
| 8800  | 0.097400      | 0.078785        | 0.079200 |
| 9000  | 0.093200      | 0.077445        | 0.077015 |
| 9200  | 0.088700      | 0.078207        | 0.076617 |
| 9400  | 0.087200      | 0.078982        | 0.076485 |
| 9600  | 0.089900      | 0.081209        | 0.076021 |
| 9800  | 0.081900      | 0.078158        | 0.075757 |
| 10000 | 0.080200      | 0.078074        | 0.074498 |
| 10200 | 0.085000      | 0.078830        | 0.073373 |
| 10400 | 0.080400      | 0.078144        | 0.073373 |
| 10600 | 0.078200      | 0.077163        | 0.073902 |
| 10800 | 0.080900      | 0.076394        | 0.072446 |
| 11000 | 0.080700      | 0.075955        | 0.071585 |
| 11200 | 0.076800      | 0.077031        | 0.072313 |
| 11400 | 0.076300      | 0.077401        | 0.072777 |
| 11600 | 0.076700      | 0.076613        | 0.071916 |
| 11800 | 0.076000      | 0.076672        | 0.071916 |
| 12000 | 0.077200      | 0.076490        | 0.070989 |
| 12200 | 0.076200      | 0.076688        | 0.070856 |
| 12400 | 0.074400      | 0.076780        | 0.071055 |
| 12600 | 0.076300      | 0.076768        | 0.071320 |
| 12800 | 0.077600      | 0.076727        | 0.071055 |
| 13000 | 0.077700      | 0.076714        | 0.071254 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-tatar --dataset mozilla-foundation/common_voice_8_0 --config tt --split test
```